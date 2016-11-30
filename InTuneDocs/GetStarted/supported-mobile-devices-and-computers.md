---
title: "Dispositivos móveis e browsers suportados | Microsoft Intune"
description: "Dispositivos móveis e computadores que o Intune suporta"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>Dispositivos móveis e computadores suportados

Pode inscrever-se e, em seguida, gerir os seguintes tipos de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

A inscrição de dispositivos fornece [estas funcionalidades](/Intune/get-started/choose-how-to-manage-devices).

Em alternativa, pode gerir PCs com Windows com o software de cliente para PC do Intune. O software de cliente de PC do Intune suporta o Windows 7 e posterior, exceto o Windows 10 Home. A gestão de PCs com o software de cliente fornece [estas funcionalidades](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

Os clientes com o Enterprise Management Suite também podem utilizar o Azure Active Directory (Azure AD) para registar dispositivos com Windows 10.

## <a name="microsoft-intune-supported-web-browsers"></a>Browsers suportados do Microsoft Intune

As diferentes tarefas administrativas necessitam que utilize um dos seguintes sites administrativos.

- [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Consola do administrador do Microsoft Intune](https://admin.manage.microsoft.com/)

> [!Note]
> O Microsoft Edge e os browsers para dispositivos móveis não são suportados na consola de administração porque não suportam o [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). A consola do Intune está a abandonar a experiência do Silverlight ao longo de um período de tempo; eventualmente, todas as funcionalidades de gestão de aplicações e dispositivos móveis do Intune serão [disponibilizadas no novo portal do Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

|Funcionalidade do Intune |Browsers suportados|
|---------|---------|
|Consola de Administração do Intune     |  Internet Explorer 10 ou posterior<br /><br />Google Chrome (versões anteriores à versão 42)<br /><br />Mozilla Firefox com o Silverlight ativado<br /><br />**Nota:** o Microsoft Edge e o browsers para dispositivos móveis não são suportados pela consola de Administração.                      
|Portal de Administração do Office 365     |Todos os browsers, incluindo browsers para dispositivos móveis e browsers geridos  |
|Site do Portal da Empresa     |**Em dispositivos móveis:** utilize o browser predefinido de cada plataforma suportada   <br /><br />**Em PCs com Windows:** Internet Explorer 10 ou posterior ou o Microsoft Edge<br /><br />**Em Mac OS X 10.9 ou posterior:** Apple Safari    |

> [!Note]
> O Microsoft Edge e os browsers para dispositivos móveis não são suportados na consola de administração porque não suportam o [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). A consola do Intune está a abandonar a experiência do Silverlight ao longo de um período de tempo; eventualmente, todas as funcionalidades de gestão de aplicações e dispositivos móveis do Intune serão [disponibilizadas no novo portal do Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Enquanto administrador inquilino, utilize este portal para gerir a sua subscrição**, incluindo as seguintes tarefas, se a sua função de administrador o permitir:

- Gerir as contas de utilizador da subscrição e configurar a sincronização de diretórios a partir do seu Active Directory no local.
- Gerir grupos de utilizadores denominados grupos de segurança.
- Atribuir licenças aos utilizadores para utilizar o Intune.
- Configurar o nome de domínio que utiliza com a sua subscrição. O nome de domínio define a conta com a qual os utilizadores iniciam sessão.
- Gerir os detalhes de compra e faturação da sua subscrição, incluindo o número de licenças que possui ou a quantidade de espaço de armazenamento em nuvem que pode utilizar.
- Localizar ligações para ver o estado de funcionamento do serviço do Intune.
- Enquanto administrador inquilino, pode iniciar sessão no portal do Office 365 para gerir a subscrição, mesmo que a sua conta não tenha licenças atribuídas para utilizar o Intune.
- Qualquer utilizador que tenha uma licença do Intune, mas que não seja administrador, pode utilizar este portal para repor a palavra-passe da conta e editar o respetivo perfil.
- Para aceder ao portal do Office 365, a sua conta tem de ter o estado de início de sessão definido como **Permitido**. Este estado é diferente de ter uma licença para a subscrição. Por predefinição, todas as contas de utilizador têm o estado **Permitido**.


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Consola do administrador do Microsoft Intune](https://manage.microsoft.com/)

**Enquanto administrador de serviços, utilize este portal para gerir operações diárias,** incluindo:

- Definir políticas para computadores e dispositivos móveis.
- Carregar e implementar software, tal como atualizações de software e aplicações.
- Gerir o Endpoint Protection nos computadores.
- Ver o estado dos dispositivos e executar relatórios.
- Inicie sessão neste portal. Tem de ter permissões de administrador de serviços ou ser um administrador inquilino com a função de administrador global para iniciar sessão neste portal.


Apenas os utilizadores com permissões de administrador de serviços ou administradores inquilinos com a função de administrador global podem iniciar sessão neste portal. Para aceder à consola de administração, a sua conta tem de ter uma licença para utilizar o Intune e o estado de início de sessão definido como **Permitido**.



<!--HONumber=Nov16_HO4-->


