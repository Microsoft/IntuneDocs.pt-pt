---
title: Solucionar problemas de ações de dispositivo no Microsoft Intune-Azure | Microsoft Docs
description: Obtenha ajuda para solucionar problemas de ação do dispositivo.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 239dd8630eb361da8609e3a34eb2c9346a64dab0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907190"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Solucionar problemas de ações de dispositivo no Intune

Microsoft Intune tem muitas ações que ajudam você a gerenciar dispositivos. Este artigo fornece respostas para algumas perguntas comuns que podem ajudá-lo a solucionar problemas de ações do dispositivo.

## <a name="bypass-activation-lock-action"></a>Ignorar ação de Bloqueio de Ativação

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Cliquei na ação "ignorar Bloqueio de Ativação" no portal, mas nada aconteceu no dispositivo.
Isto era esperado. Depois de iniciar a ação ignorar Bloqueio de Ativação, o Intune solicitará um código atualizado da Apple. Você inserirá manualmente o código no campo senha depois que o dispositivo estiver na tela de Bloqueio de Ativação. Esse código só é válido por 15 dias, portanto, certifique-se de clicar na ação e copiar o código antes de emitir o apagamento.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Por que não vejo o código de Bloqueio de Ativação de bypass na folha de visão geral de hardware do meu dispositivo iOS?
Os motivos mais prováveis incluem:
- O código expirou e foi limpo do serviço.
- O dispositivo não é supervisionado com a política de restrição de dispositivo para permitir Bloqueio de Ativação.

Você pode verificar o código no explorador do Graph com a seguinte consulta:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>Por que o bypass Bloqueio de Ativação ação esmaecida para meu dispositivo iOS?
Os motivos mais prováveis incluem: 
- O código expirou e foi limpo do serviço.
- O dispositivo não é supervisionado com a política de restrição de dispositivo para permitir Bloqueio de Ativação.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>O bypass Bloqueio de Ativação diferencia maiúsculas de minúsculas?
Não. E você não precisa inserir os traços.

## <a name="remove-devices-action"></a>Ação remover dispositivos

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Como fazer dizer quem iniciou uma desativação/apagamento?
No centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), acesse **Administração de locatários** > **logs de auditoria** > marque a coluna **iniciado por** .
Se você não vir uma entrada, a pessoa mais provável de iniciar a ação é o usuário do dispositivo. Eles provavelmente usaram o Portal da Empresa aplicativo ou o portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Por que meu aplicativo não foi desinstalado depois de usar a desativação?
Porque não era considerado um aplicativo gerenciado. Nesse contexto, um aplicativo gerenciado é um aplicativo que foi instalado usando o serviço do Intune. Isto inclui:
- O aplicativo foi implantado conforme necessário
- O aplicativo foi implantado como disponível e, em seguida, instalado pelo usuário final de dentro do aplicativo Portal da Empresa.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Por que o apagamento fica esmaecido para dispositivos Android Enterprise de perfil de trabalho?
Este comportamento está previsto. O Google não permite a redefinição de fábrica de dispositivos de perfil de trabalho do provedor de MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Por que posso entrar nos meus aplicativos do Office depois que meu dispositivo fosse desativado?
Como desativar um dispositivo não revoga tokens de acesso. Você pode usar políticas de acesso condicional para atenuar essa condição.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Como posso monitorar uma ação de desativar/apagar após sua emissão?
No centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), acesse **Administração de locatários** > **logs de auditoria**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Por que as limpezas às vezes são mostradas como pendentes de forma indefinida?
Os dispositivos nem sempre relatam seu status de volta para o serviço do Intune antes que a redefinição seja iniciada. Assim, a ação é mostrada como pendente. Se você confirmou que a ação foi bem-sucedida, exclua o dispositivo do serviço.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>O que acontece se eu iniciar uma desativação/apagamento em um dispositivo offline ou um dispositivo que não se comunicava com o serviço há algum tempo?
O dispositivo permanecerá no estado de **desativação/apagamento pendente** até que o certificado MDM expire. O certificado MDM dura por um ano do registro e renova automaticamente todos os anos. Se o dispositivo fizer check-in antes que o certificado MDM expire, ele será desativado/apagado. Se o dispositivo não fizer check-in antes de o certificado MDM expirar, ele não poderá fazer check-in no serviço. 180 dias após o certificado MDM expirar, o dispositivo será removido automaticamente da portal do Azure.


## <a name="reset-passcode-action"></a>Redefinir ação de senha

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Por que a ação Redefinir senha está esmaecida no dispositivo de administrador do meu dispositivo Android registrado?
Para combater o ransomware Ware, o Google removeu o recurso de redefinição de senha na API de administração do dispositivo (aplica-se ao Android versão 7,0 ou dispositivos superiores).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Por que recebo uma mensagem "sem suporte" ao emitir uma redefinição de senha para meu dispositivo de perfil de trabalho do Android 8,0 ou posterior?
Porque o token de redefinição não foi ativado no dispositivo. Para ativar o token de redefinição:
1. Você deve exigir uma senha de perfil de trabalho em sua política de configuração.
2. O usuário final deve definir uma senha de perfil de trabalho apropriada.
3. O usuário final deve aceitar o prompt secundário para permitir a redefinição de senha.
Depois que essas etapas forem concluídas, você não deverá mais receber essa resposta.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Por que sou solicitado a definir uma nova senha no meu dispositivo iOS quando eu emitir a ação remover senha?
Porque uma de suas políticas de conformidade requer uma senha.

## <a name="next-steps"></a>Próximos passos

Obtenha [ajuda de suporte da Microsoft](../fundamentals/get-support.md)ou use os [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
