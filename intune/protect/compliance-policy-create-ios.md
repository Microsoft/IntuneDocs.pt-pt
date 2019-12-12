---
title: Definições de conformidade de dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os dispositivos iOS no Microsoft Intune. Exigir uma mensagem de e-mail, verificar dispositivos desbloqueados por jailbreak ou rooting, definir o sistema de operativo mínimo e máximo permitido, definir restrições de palavra-passe, incluindo inatividade do dispositivo e o comprimento da palavra-passe, restringir aplicações e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b83b764af415349b287df2a09f9b4c355734c28
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810247"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do iOS para marcar dispositivos como conformes ou não conformes com o Intune

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos iOS no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para exigir uma mensagem de e-mail, marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes, definir um nível de ameaça permitido, definir a expiração de palavras-passe e muito mais.

Esta funcionalidade aplica-se a:

- iOS
- iPadOS

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Para **plataforma**, selecione **Ios/iPadOS**.

## <a name="email"></a>E-mail

- **Exigir que os dispositivos móveis tenham um perfil de e-mail gerido**:  
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -dispositivos que não têm um perfil de email gerenciado pelo Intune são considerados não compatíveis. Um dispositivo não pode ter um perfil de e-mail gerido quando não está corretamente direcionado ou se o utilizador tiver configurado manualmente a conta de e-mail no dispositivo.

  O dispositivo é considerado não conforme nas seguintes situações:  
  - O perfil de e-mail é atribuído a um grupo de utilizadores diferente do grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponde ao perfil de e-mail do Intune implementado no dispositivo. O Intune não é capaz de substituir o perfil de utilizador configurado e não o consegue gerir. Para estar conforme, o utilizador final tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.  

Para obter informações sobre os perfis de e-mail, veja [configurar o acesso ao e-mail organizacional através de perfis de e-mail com o Intune](../configuration/email-settings-configure.md).

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Dispositivos desbloqueados por jailbreak**:  
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - Marca de **bloqueio** de dispositivos com raiz (jailbreak) como não compatível.  

- **Exigir que o dispositivo esteja no nível de ameaça do dispositivo ou abaixo** dele *(Ios 8,0 e mais recente)* :  
  utilize esta definição para assumir a avaliação de riscos como uma condição para conformidade. Escolha o nível de ameaça permitido:  
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Seguro** – essa opção é a mais segura e significa que o dispositivo não pode ter nenhuma ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo** -o dispositivo será avaliado como compatível se apenas ameaças de nível baixo estiverem presentes. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** -o dispositivo será avaliado como em conformidade se as ameaças presentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** -essa opção é a menos segura, pois permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

## <a name="device-properties"></a>Propriedades do Dispositivo

### <a name="operating-system-version"></a>Versão do Sistema Operativo  

- **Sistema operacional mínimo necessário** *(Ios 8,0 e mais recente)* :  
  quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da organização.

- **Versão máxima do sistema operacional permitida** *(Ios 8,0 e mais recente)* :  
  quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador final para contactar o administrador de TI. O dispositivo não poderá aceder aos recursos da organização, enquanto a regra não for alterada para permitir a versão do SO.

- **Versão mínima de Build do so** *(Ios 8,0 e mais recente)* :  
  quando a Apple publica atualizações de segurança, o número da compilação é normalmente atualizado, não a versão do SO. Utilize esta funcionalidade para introduzir um número mínimo de compilação permitido no dispositivo.

- **Versão máxima de Build do so** *(Ios 8,0 e mais recente)* :  
  quando a Apple publica atualizações de segurança, o número da compilação é normalmente atualizado, não a versão do SO. Utilize esta funcionalidade para introduzir um número máximo de compilação permitido no dispositivo.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

> [!NOTE]
> Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, será pedido aos utilizadores que definam um código de acesso a cada 15 minutos. Os utilizadores continuam a receber o pedido até que seja definido um código de acesso. Quando uma senha é definida para o dispositivo iOS, o processo de criptografia é iniciado automaticamente. O dispositivo permanece criptografado até que a senha seja desabilitada.

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**:  
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.  
  - **Exigir** -os usuários devem inserir uma senha antes que possam acessar seu dispositivo. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.

- **Palavras-passe simples**:  
  - **Não configurado** (*padrão*)-os usuários podem criar senhas simples, como **1234** ou **1111**.
  - **Bloquear** -os usuários não podem criar senhas simples, como **1234** ou **1111**. 

- **Comprimento mínimo da palavra-passe**:  
  introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.  

- **Tipo obrigatório de palavra-passe**:  
  Escolha se uma senha deve ter apenas caracteres **numéricos** ou se deve haver uma combinação de números e outros caracteres (**alfanuméricos**).

- **Número de carateres não alfanuméricos na palavra-passe**:  
  Insira o número mínimo de caracteres especiais, como `&`, `#`, `%`, `!`e assim por diante, que deve estar na senha. 

  Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos após o bloqueio de tela antes da senha ser necessária** *(Ios 8,0 e mais recente)* :  
  Especifique o quanto logo após a tela ser bloqueada antes que um usuário precise digitar uma senha para acessar o dispositivo. As opções incluem o padrão de *não configurado*, *imediatamente*e de *1 minuto* a *4 horas*.

- **Máximo de minutos de inatividade até o ecrã ser bloqueado**:  
  Insira o tempo ocioso antes que o dispositivo bloqueie sua tela. As opções incluem o padrão de *não configurado*, *imediatamente*e de *1 minuto* a *15 minutos*.

- **Expiração da palavra-passe (dias)** :  
  selecione o número de dias antes de a palavra-passe expirar e ser necessário criar uma nova. 

- **Número de senhas anteriores para evitar a reutilização** *(Ios 8,0 e mais recente)* :   
  introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.

### <a name="device-security"></a>Segurança do Dispositivo

- **Aplicações restritas**:  
  Pode restringir aplicações ao adicionar os respetivos IDs do pacote à política. Se um dispositivo tiver a aplicação instalada, o dispositivo será marcado como não conforme.

  - **Nome do aplicativo** – Insira um nome amigável para o usuário para ajudá-lo a identificar a ID do pacote.
  - **ID do lote de aplicativos** – Insira o identificador exclusivo do pacote atribuído pelo provedor de aplicativos. Para localizar o ID do pacote, veja [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (Como localizar o ID do pacote de uma aplicação iOS) (abre outro site da Microsoft).  

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos macOS](compliance-policy-create-mac-os.md).
