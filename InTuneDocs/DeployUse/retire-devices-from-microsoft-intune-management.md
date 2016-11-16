---
title: Extinguir dispositivos | Microsoft Intune
description: "O Intune suporta uma eliminação seletiva e uma eliminação completa para remover o dispositivo da gestão do Intune, removendo as respetivas políticas e o portal da empresa."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b76e9e16ef1fa6870783326630ae74d07ae59cbb
ms.openlocfilehash: be3a30535fc9cebad5d4a167b75c484ddafd7f85


---

# <a name="retire-devices-from-intune-management"></a>Extinguir dispositivos da gestão do Intune

Independentemente de os dispositivos serem da empresa ou pessoais, chega uma altura em que os dispositivos geridos têm de ser removidos da gestão do Intune. Poderá ter de extinguir um dispositivo por vários motivos:

-   O utilizador sai da empresa de forma planeada (saída “gerida”)
-   O utilizador sai abruptamente (é despedido, despede-se, etc.).
-   Perda do dispositivo
-   Redefinição do objetivo de um dispositivo (passar para outro utilizador, reutilizar para uma finalidade diferente, etc.)

Pode efetuar uma eliminação seletiva ou uma eliminação completa nos dispositivos geridos como dispositivos móveis, ou pode bloquear um dispositivo e repor a respetiva palavra-passe. Ao limpar o dispositivo, liberta a subscrição do utilizador para adicionar um dispositivo diferente. Também pode extinguir PCs geridos com o software de cliente do Intune.

## <a name="wipe-data-and-apps-from-devices"></a>Eliminar dados e aplicações dos dispositivos
A eliminação seletiva e a eliminação completa removem o dispositivo da gestão do Intune, removendo as respetivas políticas e o portal da empresa. Como resultado, o dispositivo deixa de ter as credenciais necessárias para iniciar sessão nos recursos da empresa, como o Microsoft SharePoint, o e-mail ou o Office 365.

A [eliminação seletiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) é a ação preferencial para os empregados que inscreveram os dispositivos pessoais no Intune, porque não afeta as informações pessoais do dispositivo. Só são removidos os dados empresariais.

Para os dispositivos que têm de ser reaproveitados, também pode utilizar uma [eliminação completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), que repõe as definições de fábrica do dispositivo.

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Para eliminar dispositivos no portal do Azure Active Directory

1.  Inicie sessão com as credenciais da sua organização em [http://aka.ms/accessaad](http://aka.ms/accessaad) ou [https://portal.office.com](https://portal.office.com) e, em seguida, escolha **Centros de administração** &gt; **Azure AD**.

2.  Se não tiver uma subscrição do Azure, crie uma. Não deverá ser necessário um cartão de crédito nem efetuar o pagamento se tiver uma conta paga. Clique na ligação de subscrição **Registar o Azure Active Directory gratuitamente**.

4.  Selecione **Active Directory** e, em seguida, selecione a sua organização.

5.  Selecione o separador **Utilizadores** .

6.  Selecione o utilizador cujos dispositivos pretende eliminar.

7.  Escolha **Dispositivos**.

8.  Selecione os dispositivos conforme adequado e escolha **Eliminar dispositivo**. O dispositivo será eliminado da próxima vez que sincronizar com o Active Directory. Esta situação ocorre normalmente no prazo de quatro horas. Após a sincronização, o dispositivo é removido da gestão. Esta ação remove um dispositivo do limite do dispositivo para este utilizador.

## <a name="retire-managed-computers"></a>Extinguir computadores geridos
Os computadores geridos com o software de cliente Intune podem ser removidos da gestão a partir da consola de administração do Intune. Isto também desinstala o software de cliente e elimina a política do Intune do computador. Veja informações sobre como [extinguir computadores geridos com o software de cliente Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## <a name="block-access-a-device"></a>Bloquear o acesso a um dispositivo
No caso de um dispositivo perdido ou quando tem de extinguir um dispositivo porque um funcionário saiu da empresa sem devolver um hardware pertencente à empresa, também pode [repor o código de acesso e bloquear remotamente](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o dispositivo. Este procedimento impede que as informações sejam utilizadas indevidamente, embora possa ter de identificar o dispositivo como perdido.

Também deve revogar a licença da conta de utilizador do Intune do empregado. Esta ação liberta a licença e pode atribuí-la a uma nova conta de utilizador.

## <a name="retire-hardware"></a>Extinguir hardware
Por vezes, é o próprio dispositivo que atinge o respetivo fim de vida. Nestes casos, [repor as definições de fábrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) com uma limpeza completa remove todos os dados e retira o dispositivo do Intune. Em seguida, pode eliminar o hardware de acordo com a política da sua empresa.

### <a name="see-also"></a>Consulte também
[Ajudar a proteger os seus dados com a eliminação completa ou seletiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Nov16_HO3-->


