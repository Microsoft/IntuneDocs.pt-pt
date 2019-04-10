---
title: definições de conformidade do dispositivo iOS no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições que pode utilizar quando a definição de conformidade para os seus dispositivos iOS no Microsoft Intune. Exigir uma mensagem de e-mail, verificar desbloqueados por jailbreak ou Root dispositivos, definir o sistema de operativo mínimo e máximo permitido, definir quaisquer restrições de palavra-passe, incluindo inatividade de dispositivos e de comprimento de palavra-passe, restringir as aplicações e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ec071622a2e0d49068864f8bfb47954f54c8ba4
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423616"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>definições do iOS para marcar dispositivos como compatíveis ou não compatíveis com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos iOS no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para exigir uma mensagem de e-mail, marcar os dispositivos com root (jailbreak) como não conforme, defina uma ameaça permitido nível, definidas as palavras-passe a expirar e muito mais.

Esta funcionalidade aplica-se a:

- iOS

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger recursos da sua organização. Para saber mais sobre as políticas de conformidade e o que fazer, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **iOS**.

## <a name="email"></a>Email

- **Exigir que os dispositivos móveis tenham um perfil de e-mail gerido**: Quando definido como **requerem**, dispositivos que não têm um perfil de e-mail gerido pelo Intune são considerados não conformes. Um dispositivo não pode ter um perfil de e-mail gerido quando ele não está corretamente direcionado ou se o utilizador configurado manualmente a conta de e-mail no dispositivo. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  O dispositivo é considerado não conforme nas seguintes situações:

  - O perfil de e-mail é atribuído a um grupo de utilizadores diferentes que o grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponda ao perfil de e-mail do Intune implementado no dispositivo. Intune não é possível substituir o perfil de utilizador configurado e o Intune não o consegue gerir. Para estar em conformidade, o utilizador final tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.

- **Selecione o perfil de e-mail que tem de ser gerido pelo Intune**: Se o **conta de E-Mail tem de ser gerenciada pelo Intune** definição está selecionada, escolha **selecione** para introduzir o perfil de e-mail do Intune. O perfil de e-mail tem de existir no dispositivo.

Para obter detalhes sobre perfis de e-mail, consulte [configurar o acesso ao e-mail da organização através de perfis de e-mail com o Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Os dispositivos com Jailbreak**: Escolher **bloco** para marcar os dispositivos com root (com jailbreak) como não conforme. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir o dispositivo esteja ao nível ou abaixo do nível de ameaça do dispositivo** (iOS 8.0 e mais recente): Utilize esta definição para assumir a avaliação de risco como uma condição para conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: Esta opção é a mais segura e significa que o dispositivo não pode ter qualquer ameaça. Se o dispositivo é detetado com qualquer nível de ameaças, é avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças que estão presentes no dispositivo forem de nível baixo ou médio. Se o dispositivo forem detectado ameaças de nível alto, este tem determinado como não conforme.
  - **Alta**: Esta opção é menos segura, já que permite a todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

## <a name="device-properties"></a>Propriedades do dispositivo

- **SO mínimo obrigatório** (iOS 8.0 e mais recente): Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Depois disso, podem aceder a recursos da organização.
- **Versão do SO máxima permitida** (iOS 8.0 e mais recente): Quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da organização é bloqueado. O utilizador final é pedido que contacte o administrador de TI. O dispositivo não é possível aceder aos recursos de organização, enquanto uma regra ser alterada para permitir a versão do SO.
- **Versão de compilação de SO mínimo** (iOS 8.0 e mais recente): Quando a Apple publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido mínimo no dispositivo.
- **Versão de compilação do SO máximo** (iOS 8.0 e mais recente): Quando a Apple publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido máximo no dispositivo.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

> [!NOTE]
> Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, será pedido aos utilizadores que definam um código de acesso a cada 15 minutos. Os utilizadores continuam a receber o pedido até que seja definido um código de acesso.

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.
- **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe obrigatório**: Escolha se uma palavra-passe deve ter apenas **numérico** carateres, ou se deve existir uma combinação de números e outros carateres (**alfanumérico**).
- **Número de carateres não alfanuméricos na palavra-passe**: Introduza o número mínimo de carateres especiais, como `&`, `#`, `%`, `!`e assim por diante, que tem de ser a palavra-passe.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizado.

### <a name="device-security"></a>Segurança do dispositivo

- **Aplicações restritas**: Pode restringir aplicações ao adicionar os respetivos IDs do pacote à política. Se um dispositivo tiver a aplicação instalada, o dispositivo é marcado como não conforme.

  - **Nome da aplicação**: Introduza um nome amigável para ajudar a identificar o ID de pacote.
  - **ID do pacote de aplicação**: Introduza o identificador do pacote exclusivo atribuído pelo fornecedor da aplicação. Para obter o ID do pacote, veja [como localizar o ID do pacote para uma aplicação iOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (abre-se outro web site da Microsoft).  

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).
- [Monitorizar as suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte a [definições de política de conformidade para macOS](compliance-policy-create-mac-os.md) dispositivos.
