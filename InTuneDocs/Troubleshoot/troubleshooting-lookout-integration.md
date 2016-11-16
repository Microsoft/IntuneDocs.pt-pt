---
title: "Resolução de Problemas da Integração do Lookout | Microsoft Intune"
description: "Este tópico descreve resoluções de problemas que ocorrem frequentemente com a Integração do Lookout"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: aa29f702803d657f783ff0dfc6ea66981484c569


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Resolução de Problemas da Integração do Lookout com o Intune
Este tópico descreve alguns problemas comuns que pode encontrar na configuração do Lookout Mobile Threat Protection (MTP).
## <a name="troubleshoot-login-errors"></a>Resolução de problemas de erros de início de sessão
### <a name="403-errors"></a>Erros 403
Pode ver um erro 403 quando inicia sessão na [consola do Lookout MTP](https://aad.lookout.com): **não tem autorização para aceder ao serviço** Isto pode acontecer quando o nome de utilizador que especificou não é um membro do grupo do Azure Active Directory (Azure AD) que está configurado para aceder ao Lookout MTP.

O Lookout MTP está configurado para permitir que apenas utilizadores de um grupo do Azure AD configurado tenham acesso. Se não tiver a certeza que grupo está configurado com acesso ao Lookout MTP, contacte o Suporte do Lookout.

Pode contactar o Suporte do Lookout através dos seguintes métodos:

* E-mail: enterprisesupport@lookout.com
* Inicie sessão na [Consola do MTP](http://aad.lookout.com) e navegue até ao módulo **Suporte**.
* Aceda a https://enterprise.support.lookout.com/hc/en-us/requests e efetue um pedido de suporte.

### <a name="unable-to-sign-in"></a>Não é possível iniciar sessão
Poderá ver o seguinte erro se o utilizador de administração global do Azure AD não aceitar a configuração inicial do Lookout.

![captura de ecrã do ecrã de início de sessão do Lookout a mostrar um erro de início de sessão](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Para resolver este problema, o utilizador de administração global tem de iniciar sessão em https://aad.lookout.com/les?action=consent e aceitar o pedido para iniciar a configuração. Pode encontrar mais informações detalhadas no tópico [Configurar a sua subscrição com o Lookout MTP](set-up-your-subscription-with-lookout-mtp.md)

## <a name="troubleshoot-device-status-issues"></a>Resolução de problemas do estado do dispositivo

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>O dispositivo não está a ser apresentado na lista de dispositivos da consola do Lookout MTP

Isto pode ocorrer em qualquer um dos seguintes cenários:
* Quando o utilizador que é proprietário deste dispositivo não está no **Grupo de Inscrição** especificado na **Consola do Lookout MTP**.  A partir do módulo **Sistema**, aceda ao separador **Conector do Intune** e observe as definições **Gestão de Inscrições**.  Deverá ver um ou mais grupos do Azure AD configurados para inscrição.  Verifique que o utilizador que é proprietário do dispositivo em falta faz parte de um dos grupos do Azure AD especificados.  Assim que for adicionado um utilizador novo ao grupo de inscrição, irá demorar até ao intervalo de consulta configurado (a predefinição é 5 minutos) para ver o dispositivo a aparecer no módulo **Dispositivos** da Consola do Lookout MTP.

* Se o dispositivo não for suportado pelo Lookout MTP.  Os dispositivos que não são suportados irão aparecer na secção **Dispositivos Geridos** das definições do conector na Consola do Lookout MTP.

### <a name="device-continues-to-be-reported-as-pending"></a>O dispositivo continua a ser comunicado como **pendente**

Um dispositivo a mostrar **Pendente** significa que o utilizador final não abriu a aplicação Lookout for Work e não tocou no botão **Ativar**. Para obter mais detalhes sobre a ativação do dispositivo com a aplicação Lookout for Work, leia o seguinte tópico:

[É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>Na consola do Lookout MTP, um dispositivo está a aparecer como ativo, mas não tem um ID de dispositivo.  
Isto significa que o utilizador que é proprietário deste dispositivo não está no grupo de inscrição especificado na Consola do Lookout MTP.   Um dispositivo pode ficar neste estado se o utilizador que é proprietário do dispositivo tiver sido removido do grupo de inscrição ou se o grupo de inscrição a que o utilizador pertence tiver sido removido.

A partir do módulo **Sistema** na consola do Lookout MTP, aceda ao separador **Conector do Intune** e analise as definições **Inscrição**.  Deverá ver um ou mais grupos do Azure AD configurados para inscrição.  Confirme que o utilizador que é proprietário do dispositivo faz parte de um dos grupos do Azure AD especificados.  

Enquanto um dispositivo está neste estado, o Lookout irá continuar a notificar o utilizador de quaisquer ameaças detetadas, mas não irá enviar informações de ameaças ao Intune.

### <a name="device-shows-disconnected-state"></a>O dispositivo mostra um estado desligado

Desligado significa que o Lookout MTP não teve notícias do dispositivo durante um intervalo de tempo pré-configurado (a predefinição é 30 dias com um mínimo de 7 dias). Isto significa que a aplicação Portal da Empresa ou a aplicação Lookout for Work não está instalada no dispositivo ou foi desinstalada. Reinstalar as aplicações deve resolver este problema. Quando o utilizador abre o Lookout for Work e ativa a aplicação, o dispositivo sincroniza novamente com o Lookout MTP e o Intune.    

### <a name="forcing-a-resync-on-the-device"></a>Forçar a ressincronização no dispositivo
A partir do módulo **Dispositivos** da consola do Lookout MTP, o administrador pode selecionar o dispositivo e optar por eliminá-lo.   Da próxima vez que o proprietário do dispositivo abrir a aplicação Lookout for Work e tocar em **Ativar**, o estado do dispositivo fará uma ressincronização completa.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>O proprietário do dispositivo já não utiliza este dispositivo
Tem de apagar o dispositivo e pedir ao novo utilizador para se inscrever.  A partir da [consola do administrador do Intune](https://manage.microsoft.com), selecione o dispositivo, clique com o botão direito do rato e selecione **Extinguir/Limpar** para remover o dispositivo da gestão. Após extinguir o dispositivo pode eliminá-lo.

![captura de ecrã do módulo dispositivo na consola de administração do Intune com a opção extinguir/limpar apresentada](../media/mtp/mtp-retire-device-intune-console.png)

Também pode aceder ao módulo **Dispositivos** da Consola do Lookout MTP e selecionar **Eliminar**.  

Desde que o utilizador novo esteja num dos grupos de inscrição especificados na consola do Lookout MTP, o dispositivo irá aparecer assim que o Azure AD associar o dispositivo ao novo utilizador.

## <a name="compliance-remediation-workflows"></a>Fluxos de trabalho de remediação de conformidade
[É-lhe pedido que instale o Lookout for Work no seu dispositivo Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### <a name="see-also"></a>Consulte também
[Configurar a sua subscrição com o Lookout MTP](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)



<!--HONumber=Nov16_HO2-->


