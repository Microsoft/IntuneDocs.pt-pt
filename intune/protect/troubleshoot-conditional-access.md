---
title: Resolver problemas de acesso condicional
titleSuffix: Microsoft Intune
description: O que fazer quando os usuários não conseguem acessar recursos por meio do acesso condicional do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c662de98ffa497c5fbc89ac1b78ed8537ff0d80c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729232"
---
# <a name="troubleshoot-conditional-access"></a>Resolver problemas de acesso condicional
Este artigo descreve o que fazer quando os usuários não conseguem acessar recursos protegidos com acesso condicional ou quando os usuários podem acessar recursos protegidos, mas devem ser bloqueados.

Com o Intune e o acesso condicional, você pode proteger o acesso a serviços como:
- Serviços do Office 365, como o Exchange Online, o SharePoint Online e o Skype for Business Online
- Exchange no local
- Vários outros serviços

Essa funcionalidade permite que você certifique-se de que apenas os dispositivos registrados no Intune e que estejam em conformidade com as regras de acesso condicional definidas no console de administração do Intune ou Azure Active Directory tenham acesso aos recursos da empresa. 

## <a name="requirements-for-conditional-access"></a>Requisitos para o acesso condicional

Os requisitos a seguir devem ser atendidos para que o acesso condicional funcione:

- O dispositivo deve ser registrado no MDM e gerenciado pelo Intune.

- O utilizador e o dispositivo têm de estar em conformidade com as políticas de conformidade do Intune atribuídas.

- Por predefinição, tem de ser atribuída ao utilizador uma política de conformidade de dispositivos. Isso pode depender da configuração da configuração **Marcar dispositivos sem nenhuma política de conformidade atribuída, pois** está em**configurações de política de conformidade** de conformidade > do **dispositivo**no portal de administração do Intune.

- O Exchange ActiveSync tem de estar ativado no dispositivo se o utilizador estiver a utilizar o cliente de correio nativo do dispositivo em vez do Outlook. Isso ocorre automaticamente para dispositivos iOS, Windows Phone e Android Knox.

- Para o Exchange local, seu Exchange Connector do Intune deve ser configurado corretamente. Para obter mais informações, consulte [Solucionando problemas do Exchange Connector no Microsoft Intune](troubleshoot-exchange-connector.md).

- Para o Skype local, você deve configurar a autenticação moderna híbrida. Consulte [visão geral da autenticação moderna híbrida](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview).

Estas condições podem ser visualizadas para cada dispositivo no portal do Azure e no relatório de inventário do dispositivo.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Os dispositivos aparecem como estando em conformidade, mas o acesso dos utilizadores continua a ser bloqueado

- Verifique se o usuário tem uma licença do Intune atribuída para a avaliação de conformidade adequada.

- Dispositivos Android não-Knox não receberão acesso até que o usuário clique no link de introdução **agora** no email de quarentena que eles recebem. Isto aplica-se mesmo que o utilizador já esteja inscrito no Intune. Se o usuário não receber o email com o link em seu telefone, ele poderá usar um computador para acessar seu email e encaminhá-lo a uma conta de email em seu dispositivo.

- Quando um dispositivo é inscrito pela primeira vez, pode demorar algum tempo até as informações de conformidade serem registadas num dispositivo. Aguarde alguns minutos e tente novamente.

- Para dispositivos iOS, um perfil de email existente pode bloquear a implantação de um perfil de email criado pelo administrador do Intune atribuído a esse usuário, tornando o dispositivo não compatível. Nesse cenário, o aplicativo Portal da Empresa notificará o usuário de que eles não estão em conformidade devido ao seu perfil de email configurado manualmente e solicitará que o usuário remova esse perfil. Depois que o usuário remove o perfil de email existente, o perfil de email do Intune pode ser implantado com êxito. Para evitar este problema, indique aos seus utilizadores para removerem qualquer perfil de e-mail existente no respetivo dispositivo antes de efetuarem a inscrição.

- Um dispositivo pode ficar preso em um estado de verificação de conformidade, impedindo o usuário de iniciar outro check-in. Se você tiver um dispositivo neste estado:
  - Certifique-se de que o dispositivo tem a versão mais recente da aplicação Portal da Empresa.
  - Reinicie o dispositivo.
  - Veja se o problema persiste em redes diferentes (por exemplo, celular, Wi-Fi, etc.).

  Se o problema persistir, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).

- Alguns dispositivos Android podem parecer estar criptografados, no entanto, o aplicativo Portal da Empresa reconhece esses dispositivos como não criptografados e os marca como não compatível. Neste cenário, o utilizador verá uma notificação na aplicação Portal da Empresa que lhe pede para definir um código de acesso para o dispositivo. Depois de tocar na notificação e confirmar a palavra-passe ou PIN existente, selecione a opção **Require PIN to start device**  (Exigir PIN para iniciar o dispositivo) no ecrã **Secure start-up** (Arranque seguro) e, em seguida, toque no botão **Check Compliance** (Verificar Conformidade) do dispositivo a partir da aplicação Portal da Empresa. O dispositivo deverá ser detetado como encriptado agora. 

  > [!NOTE]
  > Alguns fabricantes de dispositivos criptografam seus dispositivos bu usando um PIN padrão em vez de um PIN definido pelo usuário. O Intune exibe a criptografia que usa um PIN padrão como inseguro e marca esses dispositivos como não compatíveis até que o usuário crie um novo PIN não padrão.

- Um dispositivo Android que está registrado e em conformidade ainda pode ser bloqueado e receber um aviso de quarentena ao tentar acessar os recursos corporativos pela primeira vez. Se isso ocorrer, verifique se o aplicativo Portal da Empresa não está em execução e, em seguida, selecione o link **introdução agora** no email de quarentena para disparar a avaliação. Este passo só terá de ser seguido ao ativar o acesso condicional pela primeira vez.

- Um dispositivo Android registrado pode solicitar ao usuário "nenhum certificado encontrado" e não receber acesso aos recursos do O365. O usuário deve habilitar a opção *habilitar acesso do navegador* no dispositivo registrado da seguinte maneira:
  1. Abra a aplicação Portal da Empresa.
  2. Vá para a página configurações por meio dos três pontos (...) ou do botão de menu de hardware.
  3. Selecione o botão *habilitar acesso do navegador* .
  4. No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.  


## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Os dispositivos estão bloqueados e não foi recebido qualquer e-mail de quarentena

- Verifique se o dispositivo está presente na consola de administração do Intune como um dispositivo do Exchange ActiveSync. Se não estiver, a deteção de dispositivos pode estar a falhar, provavelmente devido a um problema do Exchange Connector. Para obter mais informações, consulte [solucionar problemas do Exchange Connector local do Intune](troubleshoot-exchange-connector.md).

- Antes do Exchange Connector bloquear um dispositivo, o mesmo envia um e-mail de ativação (quarentena). Se o dispositivo estiver offline, poderá não receber o e-mail de ativação. 

- Verifique se o cliente de e-mail no dispositivo está configurado para obter e-mails através de **Push** em vez de **Poll**. Se assim for, tal pode fazer com que o utilizador não receba o e-mail. Mude para **Poll** e verifique se o dispositivo recebe o e-mail.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Os dispositivos estão classificados como não conformes, mas os utilizadores não são bloqueados

- Para computadores Windows, o acesso condicional bloqueia apenas o aplicativo de email nativo, o Office 2013 com autenticação moderna ou o Office 2016. O bloqueio de versões anteriores do Outlook ou de todos os aplicativos de email em computadores Windows exige o registro de dispositivo do AAD e as configurações de Serviços de Federação do Active Directory (AD FS) (AD FS) de acordo com a [configuração do SharePoint Online e do Exchange Online para Azure Active Directory condicional Acesso](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication).

- Se o dispositivo for apagado seletivamente ou extinto do Intune, poderá continuar a ter acesso durante várias horas após a extinção. Isso ocorre porque o Exchange armazena em cache os direitos de acesso por seis horas. Considere outros meios de proteger dados em dispositivos extintos neste cenário.

- Surface Hub, os dispositivos Windows registrados em massa e o DEM inscrito podem dar suporte ao acesso condicional quando um usuário ao qual é atribuída uma licença para o Intune está conectado. No entanto, você deve implantar a política de conformidade em grupos de dispositivos (não grupos de usuários) para obter a avaliação correta.

- Verifique as atribuições das suas políticas de conformidade e de acesso condicional. Se um usuário não estiver no grupo que tem as políticas atribuídas ou estiver em um grupo que foi excluído, o usuário não será bloqueado. Apenas os dispositivos de utilizadores num grupo atribuído são verificados relativamente à conformidade.

## <a name="noncompliant-device-is-not-blocked"></a>O dispositivo não conforme não está bloqueado

Se um dispositivo não estiver em conformidade, mas continuar tendo acesso, execute as seguintes ações.

- Reveja os grupos de Destino e Exclusão. Se um utilizador não estiver no grupo de destino certo ou estiver no grupo de exclusão, não será bloqueado. Apenas os dispositivos de utilizadores num grupo de Destino são verificados relativamente à conformidade.

- Certifique-se de que o dispositivo está a ser detetado. O Exchange Connector está a apontar para um CAS do Exchange 2010 enquanto o utilizador está num servidor do Exchange 2013? Neste caso, se a regra do Exchange predefinida for Permitir, mesmo que o utilizador esteja no grupo de Destino, o Intune não pode ter conhecimento da ligação do dispositivo ao Exchange.

- Verifique o estado de Existência/Acesso do Dispositivo no Exchange:
  - Use este cmdlet do PowerShell para obter uma lista de todos os dispositivos móveis para uma caixa de correio: ' Get-ActiveSyncDeviceStatistics-Mailbox MBX '. Se o dispositivo não estiver listado, significa que não está a aceder ao Exchange.
  
  - Se o dispositivo estiver listado, use o ' Get-CASmailbox-Identity: ' UPN ' | FL ' para obter informações detalhadas sobre seu estado de acesso e fornecer essas informações para Suporte da Microsoft.

## <a name="next-steps"></a>Passos seguintes
Se estas informações não o ajudarem, também pode [obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
