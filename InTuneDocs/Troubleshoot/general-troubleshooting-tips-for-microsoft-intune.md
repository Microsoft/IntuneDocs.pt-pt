---
# required metadata

title: Sugestões de resolução de problemas genéricos | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Sugestões de resolução de problemas genéricos do Microsoft Intune
Depois de implementar o Microsoft Intune, poderá deparar-se com problemas relacionados com a sua configuração ou com os clientes. Os recursos abaixo podem ajudá-lo a identificar a causa do problema para que o possa resolver.

> [!NOTE]
> Para criar um pedido de suporte ou para ver um pedido existente, clique [aqui](https://portal.office.com/admin/default.aspx) para visitar o centro de administração do Office 365. Para obter mais informações sobre as opções de suporte, veja [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
## Definir o problema

-   Qual é o comportamento?

-   Quem se depara com este comportamento e em que plataformas e dispositivos?

-   O dispositivo funcionava bem anteriormente?

-   Que alterações fez à configuração do Intune ou do dispositivo?

-   Considere se foram feitas outras alterações ao ambiente em que trabalha, além das alterações de configuração.

-   Com que frequência ocorre este problema e é esporádico ou consistente?

-   O utilizador poderá estar a deparar-se com um problema de autenticação? Se esta for uma possibilidade, verifique se o utilizador pode iniciar sessão noutros serviços que utilizam o Azure Active Directory. Além disso, veja se o utilizador pode iniciar sessão a partir de um dispositivo diferente.

## Recolher dados disponíveis

-   Registos de dispositivos. Saiba como recolher registos do dispositivo em:
  - [Enviar registos de dados de diagnóstico de dispositivos Android ao administrador de TI com um cabo USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Enviar registos de dados de diagnóstico de dispositivos Android ao administrador de TI por e-mail](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Enviar erros de inscrição de dispositivos Android ao administrador de TI](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Enviar erros de inscrição de dispositivos iOS ao administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios.md)

-   Dados da consola de administração, por exemplo, relativamente a problemas de implementação de políticas, deve examinar a política em causa e o estado da mesma, conforme descrito em [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](/indune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## Pesquisar soluções

-   Procure uma solução na Web. Por exemplo, se receber o erro 0x80073CF0, pode procurar **technet intune 0x80073cf0** na Web e localizar o artigo [Resolução de problemas de implementação de aplicações no Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md), que oferece sugestões para resolver este problema.

-   Pode procurar uma resposta no [Fórum TechNet do Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Se o problema não tiver sido resolvido anteriormente, publique-o para ver as sugestões que a Comunidade pode dar.

-   Pode abrir um pedido de suporte. O suporte do Intune conseguirá ajudá-lo a resolver problemas de melhor forma, quando os tiver definido e recolhido os dados disponíveis.

    Para criar um pedido de suporte clique [aqui](https://portal.office.com/admin/default.aspx) para visitar o centro de administração do Office 365. Para obter mais informações sobre as opções de suporte, veja [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## Recursos comunitários
Pode encontrar outras informações úteis nestes recursos comunitários:

-   O [Microsoft Intune Survival Guide (Guia de Sobrevivência do Microsoft Intune)](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) contém ligações para muitos recursos que o podem ajudar a configurar, a manter e a resolver problemas do Intune.

-   [O blogue do Intune](http://blogs.technet.com/b/windowsintune/)

-   [Siga o Intune no Twitter](https://twitter.com/MSIntune)

-   [Os fóruns do Intune](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

## Passos seguintes
Os tópicos indicados abaixo incluem ajuda para a resolução de problemas específicos. Se estas informações de resolução de problemas não o ajudarem, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Resolução de problemas de acesso aos recursos da empresa com o Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Resolução de problemas de implementação de aplicações no Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Resolver problemas de inscrição de dispositivos no Intune](troubleshoot-device-enrollment-in-intune.md)

[Resolver problemas de políticas no Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Resolver problemas de configuração do cliente no Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Resolver problemas de atualizações de software no Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)
g


<!--HONumber=May16_HO1-->


