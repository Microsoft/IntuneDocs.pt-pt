---
title: Definições de conformidade de dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os dispositivos iOS no Microsoft Intune. Exigir uma mensagem de e-mail, verificar dispositivos desbloqueados por jailbreak ou rooting, definir o sistema de operativo mínimo e máximo permitido, definir restrições de palavra-passe, incluindo inatividade do dispositivo e o comprimento da palavra-passe, restringir aplicações e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f473e376278b454ca2d173c7c147137226a9fc9
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601516"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do iOS para marcar dispositivos como conformes ou não conformes com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos iOS no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para exigir uma mensagem de e-mail, marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes, definir um nível de ameaça permitido, definir a expiração de palavras-passe e muito mais.

Esta funcionalidade aplica-se a:

- iOS

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **iOS**.

## <a name="email"></a>E-mail

- **Exigir que os dispositivos móveis tenham um perfil de email gerenciado**: quando definido como **exigir**, os dispositivos que não têm um perfil de email gerenciado pelo Intune são considerados não compatíveis. Um dispositivo não pode ter um perfil de e-mail gerido quando não está corretamente direcionado ou se o utilizador tiver configurado manualmente a conta de e-mail no dispositivo. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  O dispositivo é considerado não conforme nas seguintes situações:

  - O perfil de e-mail é atribuído a um grupo de utilizadores diferente do grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponde ao perfil de e-mail do Intune implementado no dispositivo. O Intune não é capaz de substituir o perfil de utilizador configurado e não o consegue gerir. Para estar conforme, o utilizador final tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.

- **Selecione o perfil de email que deve ser gerenciado pelo Intune**: se a configuração a **conta de email deve ser gerenciada pelo Intune** estiver selecionada, escolha **selecionar** para inserir o perfil de email do Intune. O perfil de e-mail tem de existir no dispositivo.

Para obter informações sobre os perfis de e-mail, veja [configurar o acesso ao e-mail organizacional através de perfis de e-mail com o Intune](../configuration/email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Dispositivos com jailbreak**: escolha **Bloquear** para marcar dispositivos com raiz (jailbreak) como sem conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir que o dispositivo esteja no nível de ameaça do dispositivo ou abaixo** dele (Ios 8,0 e mais recente): Use essa configuração para fazer a avaliação de risco como uma condição para conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: esta opção é a mais segura e significa que o dispositivo não pode ter ameaças. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo é avaliado como em conformidade se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Elevado**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

## <a name="device-properties"></a>Propriedades do dispositivo

- **Sistema operacional mínimo necessário** (Ios 8,0 e mais recente): quando um dispositivo não atende ao requisito mínimo de versão do sistema operacional, ele é relatado como não compatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da organização.
- **Versão máxima do sistema operacional permitida** (Ios 8,0 e mais recente): quando um dispositivo usa uma versão do sistema operacional posterior à versão na regra, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador final para contactar o administrador de TI. O dispositivo não poderá aceder aos recursos da organização, enquanto a regra não for alterada para permitir a versão do SO.
- **Versão mínima de Build do so** (Ios 8,0 e mais recente): quando a Apple publica atualizações de segurança, o número da compilação é normalmente atualizado, não a versão do sistema operacional. Utilize esta funcionalidade para introduzir um número mínimo de compilação permitido no dispositivo.
- **Versão máxima de Build do sistema operacional** (Ios 8,0 e mais recente): quando a Apple publica atualizações de segurança, o número de Build é normalmente atualizado, não a versão do sistema operacional. Utilize esta funcionalidade para introduzir um número máximo de compilação permitido no dispositivo.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

> [!NOTE]
> Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, será pedido aos utilizadores que definam um código de acesso a cada 15 minutos. Os utilizadores continuam a receber o pedido até que seja definido um código de acesso. Quando uma senha é definida para o dispositivo iOS, o processo de criptografia é iniciado automaticamente. O dispositivo permanece criptografado até que a senha seja desabilitada.

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.
- **Palavras-passe simples**: defina como **Bloquear** para que os utilizadores não possam criar palavras-passe simples, como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).
- **Número de caracteres não alfanuméricos na senha**: Insira o número mínimo de caracteres especiais, como `&`, `#`, `%`, `!` e assim por diante, que deve estar na senha.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)** : selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de senhas anteriores para evitar a reutilização**: Insira o número de senhas usadas anteriormente que não podem ser usadas.

### <a name="device-security"></a>Segurança do dispositivo

- **Aplicações restritas**: pode restringir aplicações ao adicionar os respetivos IDs do pacote à política. Se um dispositivo tiver a aplicação instalada, o dispositivo será marcado como não conforme.

  - **Nome da aplicação**: introduza um nome simples para o ajudar a identificar o ID do pacote.
  - **ID do pacote de aplicação**: introduza o identificador exclusivo do pacote atribuído pelo fornecedor da aplicação. Para localizar o ID do pacote, veja [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (Como localizar o ID do pacote de uma aplicação iOS) (abre outro site da Microsoft).  

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos macOS](compliance-policy-create-mac-os.md).
