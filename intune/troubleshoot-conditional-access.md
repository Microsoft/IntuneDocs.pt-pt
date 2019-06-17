---
title: Resolver problemas de acesso condicional
titleSuffix: Microsoft Intune
description: O que fazer quando os utilizadores não conseguem obter acesso aos recursos através de acesso condicional do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
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
ms.openlocfilehash: f286ec4928ad4bb026c95d10562d9b339b2ca5f3
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043912"
---
# <a name="troubleshoot-conditional-access"></a>Resolver problemas de acesso condicional

Pode proteger o acesso aos serviços do Office 365 como o Exchange Online, SharePoint Online, Skype para empresas Online, no local e outros serviços do Exchange com o Intune e acesso condicional. Esta capacidade permite-lhe certificar-se de que o acesso aos recursos da empresa é restringido aos dispositivos que estão inscritos no Intune e em conformidade com as regras de acesso condicional que definiu, seja na consola de administração do Intune ou do Azure Active Directory. Este artigo descreve o que fazer quando os utilizadores não conseguem obter acesso a recursos protegidos com o acesso condicional, ou quando os utilizadores podem aceder a recursos protegidos, mas devem ser bloqueados.

## <a name="requirements-for-conditional-access"></a>Requisitos para o acesso condicional

Os seguintes requisitos devem ser cumpridos para acesso condicional funcionar:

- O dispositivo tem de estar inscrito no e de ser gerido pelo Intune.
- O utilizador e o dispositivo têm de estar em conformidade com as políticas de conformidade do Intune atribuídas.
- Por predefinição, tem de ser atribuída ao utilizador uma política de conformidade de dispositivos. Isso pode variar consoante a configuração da definição **Marcar os dispositivos sem política de conformidade atribuída como** em **Conformidade do Dispositivo** > **Definições de Política de Conformidade** no portal de administração do Intune.
-   O Exchange ActiveSync tem de estar ativado no dispositivo se o utilizador estiver a utilizar o cliente de correio nativo do dispositivo em vez do Outlook. Isto ocorre automaticamente para dispositivos iOS, Windows Phone e Android.
-   O Intune Exchange Connector tem de estar configurado corretamente. Veja [Resolução de Problemas do Exchange Connector no Microsoft Intune](troubleshoot-exchange-connector.md) para obter mais informações.

Estas condições podem ser visualizadas para cada dispositivo no portal do Azure e no relatório de inventário do dispositivo.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Os dispositivos aparecem como estando em conformidade, mas o acesso dos utilizadores continua a ser bloqueado

- O acesso a dispositivos Android que não forem Knox não será concedido até que o utilizador clique na ligação **Começar Agora Mesmo** no e-mail de quarentena recebido pelo mesmo. Isto aplica-se mesmo que o utilizador já esteja inscrito no Intune. Se o utilizador não receber o e-mail com a ligação no respetivo telemóvel, poderá utilizar um PC para aceder ao e-mail e reencaminhá-lo para uma conta de e-mail no respetivo dispositivo.
- Quando um dispositivo é inscrito pela primeira vez, pode demorar algum tempo até as informações de conformidade serem registadas num dispositivo. Aguarde alguns minutos e tente novamente.
- Nos dispositivos iOS, é possível que um perfil de e-mail existente impeça a implementação de um perfil de e-mail criado pelo administrador do Intune atribuído a esse utilizador, o que torna o dispositivo não conforme. Neste cenário, a aplicação Portal da Empresa irá notificar o utilizador de que não está em conformidade devido ao respetivo perfil de e-mail configurado manualmente e irá indicar-lhe para remover esse perfil. Quando o utilizador remover o perfil de e-mail existente, o perfil de e-mail do Intune será implementado com êxito. Para evitar este problema, indique aos seus utilizadores para removerem qualquer perfil de e-mail existente no respetivo dispositivo antes de efetuarem a inscrição.
- Um dispositivo pode ficar bloqueado num estado de verificação de conformidade, impedindo que o utilizador inicie outra verificação. Se tiver um dispositivo que se encontre neste estado, experimente o seguinte:
  - Certifique-se de que o dispositivo tem a versão mais recente da aplicação Portal da Empresa.
  - Reinicie o dispositivo.
  - Verifique se o problema persiste em redes diferentes (por exemplo, rede móvel, Wi-Fi, etc.).

  Se o problema persistir, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](get-support.md).
- É possível que determinados dispositivos Android pareçam estar encriptados, embora a aplicação Portal da Empresa reconheça estes dispositivos como não encriptados e, como tal, classifica-os como estando não conformes. Neste cenário, o utilizador verá uma notificação na aplicação Portal da Empresa que lhe pede para definir um código de acesso para o dispositivo. Depois de tocar na notificação e confirmar a palavra-passe ou PIN existente, selecione a opção **Require PIN to start device**  (Exigir PIN para iniciar o dispositivo) no ecrã **Secure start-up** (Arranque seguro) e, em seguida, toque no botão **Check Compliance** (Verificar Conformidade) do dispositivo a partir da aplicação Portal da Empresa. O dispositivo deverá ser detetado como encriptado agora. 
  > [!NOTE]
  > Alguns fabricantes de dispositivos encriptam os seus dispositivos através de um PIN predefinido em vez do PIN definido pelo utilizador. O Intune considera a encriptação através do PIN predefinido insegura e irá classificar esses dispositivos como não conformes até que o utilizador crie um PIN novo e personalizado.
- Um dispositivo Android inscrito e conforme ainda poderá ser bloqueado e receber um aviso de quarentena ao tentar aceder a recursos empresariais pela primeira vez. Se isto ocorrer, certifique-se de que a aplicação Portal da Empresa não está em execução e, em seguida, clique na ligação **Começar Agora Mesmo** no e-mail de quarentena para acionar a avaliação. Isso só deve ser feito quando o acesso condicional estiver ativado pela primeira vez.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Os dispositivos estão bloqueados e não foi recebido qualquer e-mail de quarentena

- Verifique se o dispositivo está presente na consola de administração do Intune como um dispositivo do Exchange ActiveSync. Se não estiver, a deteção de dispositivos pode estar a falhar, provavelmente devido a um problema do Exchange Connector. Para obter mais informações, veja [Resolução de problemas do conector do Exchange no local do Intune](troubleshoot-exchange-connector.md).
- Antes do Exchange Connector bloquear um dispositivo, o mesmo envia um e-mail de ativação (quarentena). Se o dispositivo estiver offline, poderá não receber o e-mail de ativação. 
- Verifique se o cliente de e-mail no dispositivo está configurado para obter e-mails através de **Push** em vez de **Poll**. Se assim for, tal pode fazer com que o utilizador não receba o e-mail. Mude para **Poll** e verifique se o dispositivo recebe o e-mail.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Os dispositivos estão classificados como não conformes, mas os utilizadores não são bloqueados

- Para Windows PCs, o acesso condicional bloqueia apenas a aplicação de e-mail nativa, o Office 2013 com autenticação moderna ou o Office 2016. Bloquear versões anteriores do Outlook ou todas as aplicações de correio em Windows PCs requerem o registo de dispositivos do AAD e configurações de serviços de Federação do Active Directory (AD FS), de acordo [configurar o SharePoint Online e Exchange Online para o Azure Active Directory Acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication). 
- Se o dispositivo for apagado seletivamente ou extinto do Intune, poderá continuar a ter acesso durante várias horas após a extinção. Isto acontece porque o Exchange coloca os direitos de acesso à memória cache a cada 6 horas. Considere outros meios de proteger dados em dispositivos extintos neste cenário.
- Os dispositivos surfaces Hub suportam o acesso condicional; No entanto, tem de implementar a política de conformidade para grupos de dispositivos (não a grupos de utilizadores) para avaliação correta.
- Verifique as atribuições de políticas de conformidade e as políticas de acesso condicional. Se um utilizador não estiver no grupo ao qual as políticas foram atribuídas ou estiver num grupo que está a ser excluído, o utilizador não será bloqueado. Apenas os dispositivos de utilizadores num grupo atribuído são verificados relativamente à conformidade.

## <a name="noncompliant-device-is-not-blocked"></a>O dispositivo não conforme não está bloqueado

Se tiver um dispositivo que não esteja em conformidade mas continue a ter acesso, siga os passos seguintes.
- Reveja os grupos de Destino e Exclusão. Se um utilizador não estiver no grupo de destino certo ou estiver no grupo de exclusão, não será bloqueado. Apenas os dispositivos de utilizadores num grupo de Destino são verificados relativamente à conformidade.
- Certifique-se de que o dispositivo está a ser detetado. O Exchange Connector está a apontar para um CAS do Exchange 2010 enquanto o utilizador está num servidor do Exchange 2013? Neste caso, se a regra do Exchange predefinida for Permitir, mesmo que o utilizador esteja no grupo de Destino, o Intune não pode ter conhecimento da ligação do dispositivo ao Exchange.
- Verifique o estado de Existência/Acesso do Dispositivo no Exchange:
  - Utilize este cmdlet do PowerShell para obter uma lista de todos os dispositivos móveis para uma caixa de correio: "Get-ActiveSyncDeviceStatistics-mailbox mbx'. Se o dispositivo não estiver listado, significa que não está a aceder ao Exchange.
  - Se o dispositivo estiver listado, utilize o cmdlet Get-CASmailbox -identity:’upn’ | fl para obter informações detalhadas sobre o respetivo estado de acesso e fornecer essas informações ao Suporte da Microsoft.

## <a name="next-steps"></a>Passos Seguintes
Se estas informações não o ajudarem, também pode [obter suporte para o Microsoft Intune](get-support.md).
