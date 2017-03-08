---
title: "Sugestões de resolução de problemas genéricos | Documentos da Microsoft"
description: Recursos gerais para ajudar a resolver problemas com o Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: ef6c482a45a7c759cec1062b129d2644562d0da2
ms.lasthandoff: 01/10/2017


---

# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Sugestões de resolução de problemas genéricos do Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Depois de implementar o Microsoft Intune, poderá deparar-se com problemas relacionados com a sua configuração ou com os dispositivos clientes. Utilize os seguintes recursos para ajudar a detetar o que está a causar o problema para que possa resolvê-lo.

> [!NOTE]
> Para criar um pedido de suporte ou para ver um pedido existente, visite o [centro de administração do Office 365](https://portal.office.com/admin/default.aspx). Para mais informações sobre as opções de suporte, consulte [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="define-the-problem"></a>Definir o problema

-   Qual é o comportamento?

-   Quem se depara com este comportamento e em que plataformas e dispositivos?

-   O dispositivo funcionava bem anteriormente?

-   Que alterações fez à configuração do Intune ou do dispositivo?

-   Foram feitas outras alterações ao ambiente em que trabalha, além das alterações de configuração?

-   Com que frequência ocorre este problema e é esporádico ou consistente?

-   O utilizador poderá estar a deparar-se com um problema de autenticação? Se esta for uma possibilidade, veja se o utilizador pode iniciar sessão noutros serviços que utilizam o Azure Active Directory. Além disso, veja se o utilizador pode iniciar sessão a partir de um dispositivo diferente.

-   Verificou o estado do serviço? Pode monitorizar o estado de funcionamento do serviço do Intune no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx). Escolha **Estado de Funcionamento do Serviço** no painel esquerdo.

## <a name="collect-available-data"></a>Recolher dados disponíveis

-   Os seguintes recursos podem ajudá-lo a aprender a recolher registos de dispositivo:
  - [Enviar registos de dados de diagnóstico de dispositivos Android para o seu administrador de TI através de um cabo USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Enviar registos de dados de diagnóstico para o seu administrador de TI através de e-mail](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Enviar erros de inscrição de dispositivos Android para o seu administrador de TI](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Enviar erros de inscrição de dispositivos iOS para o seu administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios)

-   No que respeita aos dados da consola de administração (por exemplo, problemas de implementação de políticas) examine a política em causa e o estado da mesma, conforme descrito em [Utilizar grupos para gerir utilizadores e dispositivos no Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="research-the-solution"></a>Pesquisar soluções

-   Procure uma solução na Web. Por exemplo, se receber o erro 0x80073CF0, procure **technet intune 0x80073cf0** na Web e encontrará o artigo [Resolução de problemas de implementação de aplicações no Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md). Este artigo disponibiliza sugestões para lidar com este erro.

-   Procure uma resposta no [Fórum TechNet do Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Se o problema não tiver sido resolvido anteriormente, publique-o para ver as sugestões que a Comunidade pode dar.

-   Abra um pedido de suporte. O Suporte do Intune conseguirá ajudá-lo a resolver problemas de melhor forma depois de ter definido e recolhido os dados disponíveis.

    Para criar um pedido de suporte, [visite o centro de administração do Office 365](https://portal.office.com/admin/default.aspx). Para mais informações sobre as opções de suporte, consulte [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="find-community-resources"></a>Pesquisar recursos de comunidade
Pode encontrar outras informações úteis nestes recursos comunitários:

-   O [Microsoft Intune Survival Guide (Guia de Sobrevivência do Microsoft Intune)](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) contém ligações para muitos recursos que o podem ajudar a configurar, a manter e a resolver problemas do Intune.

-   [O blogue do Intune](http://blogs.technet.com/b/windowsintune/)

-   [Seguir o Intune no Twitter](https://twitter.com/MSIntune)

-   [Os fóruns do Intune](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>Passos seguintes
Os seguintes tópicos incluem ajuda para a resolução de problemas específicos. Se estas informações de resolução de problemas não o ajudarem, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Resolução de problemas do Endpoint Protection no Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Resolução de problemas de acesso a recursos da empresa com o Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Resolução de problemas de implementação da aplicação no Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Resolução de problemas de inscrição de dispositivos no Intune](troubleshoot-device-enrollment-in-intune.md)

[Resolução de problemas de políticas no Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Resolução de problemas de configuração de cliente no Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Resolução de problemas de atualizações de software no Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)

