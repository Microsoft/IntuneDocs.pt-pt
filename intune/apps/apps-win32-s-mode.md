---
title: Habilitar aplicativos Win32 em dispositivos de modo S
titleSuffix: Microsoft Intune
description: Saiba como habilitar aplicativos Win32 em dispositivos de modo S usando Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a0f9a4cdee992914dfebd9552778c882313718
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182902"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Habilitar aplicativos Win32 em dispositivos de modo S

O [modo Windows 10 S](https://docs.microsoft.com/windows/deployment/s-mode) é um sistema operacional bloqueado que só executa aplicativos da Store. Por padrão, os dispositivos de modo S do Windows não permitem a instalação e a execução de aplicativos Win32. Esses dispositivos incluem uma única *política de base 10s do Win*, que bloqueia o dispositivo de modo S de executar qualquer aplicativo Win32 nele. No entanto, ao criar e usar uma **política complementar de modo S** no Intune, você pode instalar e executar aplicativos Win32 em dispositivos gerenciados do modo Windows 10 S. Usando as ferramentas do PowerShell do [Windows Defender Application Control (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) , você pode criar uma ou mais políticas complementares para o modo S do Windows. Você deve assinar as políticas complementares com o [serviço de assinatura do Device Guard (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) ou com [SignTool. exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) e, em seguida, carregar e distribuir as políticas por meio do Intune. Como alternativa, você pode assinar as políticas complementares com um certificado de codesignação de sua organização, no entanto, o método preferencial é usar DGSS. Na instância em que você usa o certificado de codesignação de sua organização, o certificado raiz ao qual o certificado de codesign se encadeia, deve estar presente no dispositivo.

Ao atribuir a política complementar do modo S no Intune, você permite que o dispositivo faça uma exceção à política de modo S existente do dispositivo, que permite o catálogo de aplicativos assinados carregado correspondente. A política define uma lista de permissões de aplicativos (o catálogo de aplicativos) que pode ser usada no dispositivo de modo S.

<!-- Add WDAC tooling diagram  -->

As etapas para permitir que os aplicativos Win32 sejam executados em um dispositivo Windows 10 no modo S são as seguintes:

1. Habilite dispositivos de modo S por meio do Intune como parte do processo de registro do Windows 10 S.
2. Crie uma política complementar para permitir aplicativos Win32:
   - Você pode usar as ferramentas [do controle de aplicativos do Windows Defender (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) para criar uma política complementar. A ID da política de base na política deve corresponder à ID da política base do modo S (que é embutida no cliente). Além disso, certifique-se de que a versão da política seja maior do que a versão anterior.
   - Você usa o DGSS para assinar sua política complementar. Para obter mais informações, consulte [assinar política de integridade de código com assinatura do Device Guard](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - Você carrega a política complementar assinada no Intune criando uma política complementar do modo Windows 10 S (veja abaixo).
3. Você permite catálogos de aplicativos Win32 por meio do Intune:
   - Você cria arquivos de catálogo (1 para cada aplicativo) e os assina usando DGSS ou outra infraestrutura de certificado.
   - Você empacota o catálogo assinado no arquivo *. intunewin* usando a [ferramenta de preparação de conteúdo do Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730). Para obter mais informações, consulte [Win32 app Management-Prepare The Win32 app Content for upload](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - O Intune aplica o catálogo de aplicativos assinado para instalar o aplicativo Win32 no dispositivo de modo S usando a [extensão de gerenciamento do Intune](~/apps/intune-management-extension.md).

> [!NOTE]
> Os pacotes de `.appx` de linha de negócios (LOB) e `.appx` no modo do Windows 10 S terão suporte por meio da assinatura do Microsoft Store for Business (MSFB).
>
> A **política complementar de modo S** para aplicativos deve ser fornecida por meio da extensão de gerenciamento do Intune.
>
> As políticas de modo S são impostas no nível do dispositivo. Várias políticas de destino serão mescladas no dispositivo. A política mesclada será imposta no dispositivo.

Para criar uma política complementar do modo do Windows 10 S, use as seguintes etapas:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No painel **Intune** , selecione **aplicativos cliente** > **políticas complementares de modo S** > **criar política**.
3. Antes de adicionar o **arquivo de política**, você deve criá-lo e conectá-lo. Para obter mais informações, consulte:
    - [Criar uma política WDAC usando as ferramentas do PowerShell e convertê-la em um formato binário](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Assinar usando o serviço de assinatura do Device Guard](https://go.microsoft.com/fwlink/?linkid=2095629) **(recomendado)**

4. Na página **noções básicas** , adicione os seguintes valores:

    | Valor | Description |
    |--------------|------------------------------------------------|
    | Arquivo de política | O arquivo que contém a política WDAC. |
    | Nome | O nome desta política. |
    | Description | Adicional A descrição desta política. |

5. Clique em **Avançar: marcas de escopo**.<br>
   Na página **marcas de escopo** , você pode opcionalmente configurar marcas de escopo para determinar quem pode ver a política de aplicativo no Intune. Para obter mais informações sobre marcas de escopo, consulte [usar o controle de acesso baseado em função e marcas de escopo para distribuí-lo](~/fundamentals/scope-tags.md).

6. Clique em **Avançar: atribuições**.<br>
   A página **atribuições** permite que você atribua a política a usuários e dispositivos. É importante observar que você pode atribuir uma política a um dispositivo, independentemente de o dispositivo ser gerenciado pelo Intune ou não.
7. Clique em **Avançar: examinar + criar** para examinar os valores inseridos para o perfil.
8. Quando terminar, clique em **criar** para criar a política complementar do modo S no Intune. 

Depois que a política for criada, você a verá adicionada à lista de políticas complementares de modo S no Intune. Depois que a política é atribuída, a política é implantada nos dispositivos. Observe que você deve implantar o aplicativo no mesmo grupo de segurança que a política complementar. Você pode começar a direcionar e atribuir aplicativos a esses dispositivos. Isso permitirá que os usuários finais instalem e executem os aplicativos nos dispositivos do modo S.

## <a name="removal-of-s-mode-policy"></a>Remoção da política de modo S

No momento, para remover a política suplementar do modo S do dispositivo, você deve atribuir e implantar uma política vazia para substituir a política complementar do modo S existente.

## <a name="policy-reporting"></a>Relatórios de política

A política complementar do modo S, que é imposta no nível do dispositivo, tem apenas relatórios no nível do dispositivo. Os relatórios no nível do dispositivo estão disponíveis para sucesss e condições de erro. 

Valores de relatório que são mostrados no console do Intune para as políticas de relatório do modo S:
- **Êxito**: a política complementar do modo S está em vigor.
- **Desconhecido**: o status da política suplementar do modo S não é conhecido.
- **TokenError**: a política complementar de modo S é estruturalmente Ok, mas há um erro com a autorização do token.
- **NotAuthorizedByToken**: o token não autoriza essa política complementar de modo S.
- **PolicyNotFound**: a política complementar de modo S não foi encontrada.

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como adicionar aplicações ao Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).
- Para obter mais informações sobre aplicativos Win32, consulte [Gerenciamento de aplicativos Win32 do Intune](~/apps/apps-win32-app-management.md).
