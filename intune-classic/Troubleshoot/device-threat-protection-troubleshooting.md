---
title: Resolução de problemas da Integração do Lookout
description: Este tópico descreve resoluções de problemas que ocorrem frequentemente com a Integração do Lookout
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6262fee0051827794c49ebe10361b1a3b280b140
ms.sourcegitcommit: f21287c66dd5559688f08bd98b6c976a0dea055d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/31/2018
ms.locfileid: "34470802"
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Resolução de Problemas da Integração do Lookout com o Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Este tópico descreve alguns problemas comuns que pode encontrar na configuração do Lookout Mobile Threat Protection (MTP).

**Erros de início de sessão**

## <a name="403-errors"></a>Erros 403
Quando inicia sessão na [consola do Lookout MTP](https://aad.lookout.com), vê um erro 403: **não tem autorização para aceder ao serviço** Isto pode acontecer quando o nome de utilizador especificado não é um membro do grupo do Azure Active Directory (Azure AD) que está configurado para aceder ao Lookout MTP.

O Lookout MTP só concede autorização para aceder ao serviço aos utilizadores de um grupo AD configurado. Para saber que grupo está configurado com acesso ao Lookout MTP, contacte o Suporte do Lookout:

* E-mail: enterprisesupport@lookout.com
* Inicie sessão na [Consola do MTP](http://aad.lookout.com) e navegue até ao módulo **Suporte**.
* Aceda a <https://enterprise.support.lookout.com/hc/requests> e efetue um pedido de suporte.

## <a name="unable-to-sign-in"></a>Não é possível iniciar sessão
Verá o seguinte erro se o utilizador de administração global do Azure AD não aceitar a configuração inicial do Lookout.

![captura de ecrã do ecrã de início de sessão do Lookout a mostrar um erro de início de sessão](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Para resolver este problema, o utilizador de administração global tem de iniciar sessão em https://aad.lookout.com/les?action=consent e aceitar o pedido para iniciar a configuração. Pode encontrar mais informações detalhadas no tópico [Configurar a sua subscrição com o Lookout MTP](../deploy-use/setup-your-lookout-mtd-subscription.md)

**Problemas relativos ao estado do dispositivo**

## <a name="device-missing-from-lookout-device-list"></a>Dispositivo em falta na lista de dispositivos do Lookout

Isto pode ocorrer em qualquer um dos seguintes cenários:
* O utilizador do dispositivo não está no **Grupo de Inscrição** especificado na **Consola do Lookout MTP**.  Na [consola do Lookout](http://aad.lookout.com), aceda a **Sistema** > **Conector do Intune** > **Gestão da Inscrição**.  Reveja os grupos do Azure AD que estão configurados para inscrição e verifique se o utilizador do dispositivo faz parte de um dos grupos do Azure AD.  Quando adicionar um utilizador ao grupo de inscrição, o dispositivo poderá demorar até ao intervalo de consulta configurado (a predefinição é 5 minutos) a aparecer no módulo **Dispositivos** da consola do Lookout MTP.
* Se o dispositivo não for suportado pelo Lookout MTP.  Os dispositivos que não são suportados irão aparecer na secção **Dispositivos Geridos** das definições do conector na Consola do Lookout MTP.

### <a name="device-reported-as-pending"></a>Dispositivo comunicado como **pendente**

Um dispositivo apresentado como **Pendente** significa que o utilizador final não abriu a aplicação Lookout for Work e não tocou no botão **Ativar**. Para obter mais detalhes sobre a ativação de dispositivos com a aplicação Lookout for Work, consulte [É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android) ou [É-lhe pedido que instale o Lookout for Work no seu dispositivo iOS](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios)

## <a name="device-whos-active-but-has-no-device-id"></a>O dispositivo está ativo, mas não tem ID de dispositivo
Na consola do Lookout MTP, se um dispositivo ativo não tiver ID de dispositivo, significa que o utilizador do dispositivo não está no grupo de inscrição. Um dispositivo pode ficar neste estado se o utilizador do dispositivo tiver sido removido do grupo de inscrição ou se o grupo de inscrição tiver sido removido.

Na [consola do Lookout](http://aad.lookout.com), aceda a **Sistema** > **Conector do Intune** > **Inscrição** e reveja as definições.  Reveja os grupos do Azure AD e verifique se o utilizador do dispositivo faz parte de um dos grupos do Azure AD.

Enquanto um dispositivo está neste estado, o Lookout irá continuar a notificar o utilizador de quaisquer ameaças detetadas, mas não irá enviar informações de ameaças ao Intune.

## <a name="device-reported-as-disconnected"></a>Dispositivo comunicado como **desligado**

A palavra **Desligado** significa que o dispositivo ainda não sincronizou com o Lookout MTP no intervalo configurado (a predefinição é 30 dias, sendo o mínimo 7 dias). A aplicação Portal da Empresa ou o Lookout for Work não se encontra no dispositivo. Reinstalar as aplicações deve resolver este problema. Quando o utilizador abre o Lookout for Work e ativa a aplicação, o dispositivo sincroniza novamente com o Lookout MTP e o Intune.

### <a name="forcing-a-device-sync"></a>Forçar uma sincronização do dispositivo
A partir do módulo **Dispositivos** da consola do Lookout MTP, o administrador pode selecionar o dispositivo e optar por eliminá-lo.   Da próxima vez que o proprietário do dispositivo abrir a aplicação Lookout for Work e tocar em **Ativar**, o estado do dispositivo fará uma ressincronização completa.

## <a name="device-has-a-new-user"></a>O dispositivo tem um novo utilizador
Deve apagar o dispositivo e pedir ao novo utilizador para se inscrever.  A partir da [consola do administrador do Intune](https://manage.microsoft.com), selecione o dispositivo, clique com o botão direito do rato e selecione **Extinguir/Limpar** para remover o dispositivo da gestão. Após extinguir o dispositivo pode eliminá-lo.

![captura de ecrã do módulo dispositivo na consola de administração do Intune com a opção extinguir/limpar apresentada](../media/mtp/mtp-retire-device-intune-console.png)

Também pode aceder ao módulo **Dispositivos** da [consola do Lookout](http://aad.lookout.com) e selecionar **Eliminar**.

Se o novo utilizador estiver num grupo de inscrição do Lookout MTP, o dispositivo irá aparecer assim que o Azure AD associar o dispositivo ao novo utilizador.

## <a name="compliance-remediation-workflows"></a>Fluxos de trabalho de remediação de conformidade
- [É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo Android](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo iOS](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>Consulte também
[Configurar a sua subscrição com o Lookout MTP](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)
