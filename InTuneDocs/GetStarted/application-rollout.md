---
# required metadata

title: Implementação de aplicações | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Implementação de aplicações
Este tópico fornece recomendações específicas para uma implementação faseada de aplicações no Microsoft Intune. Para obter informações gerais sobre as fases de implementação, consulte [Fases de implementação do Microsoft Intune](rollout-phases-for-microsoft-intune-deployment.md)

### Fases de implementação de aplicações
As fases de implementação de aplicações são:

-   Âmbito do projeto

-   Prova de conceito

-   Piloto

-   Implementação empresarial

-   Operações e manutenção

## Âmbito do projeto
Tenha em consideração o seguinte:

-   A tarefa de utilizador que a aplicação se destina a ativar.

-   A adequação da aplicação aos seus utilizadores e respetivos dispositivos (todos os sistemas operativos que provavelmente serão utilizados).

-   Verifique se o instalador da aplicação que escolheu é suportado pela distribuição de aplicações do Intune, conforme descrito em [Adicionar aplicações com o Microsoft Intune](/intune/deploy-use/add-apps)

-   Certifique-se de que os pré-requisitos de distribuição de aplicações estão instalados. <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md--->Determine se o tipo de aplicação é suportado pelo Intune.

-   Verifique se tem espaço de armazenamento na nuvem suficiente disponível para carregar a aplicação.

-   São fornecidas instruções para comprar armazenamento adicional em [Adicionar aplicações com o Microsoft Intune](/intune/deploy-use/add-apps) Prova de conceito

## Na fase Prova de conceito, teste a implementação de aplicações num ambiente de laboratório em dispositivos e utilizadores que foram configurados estritamente para fins de teste.
Permita a participação do suporte técnico nesta fase para saber que problemas podem surgir durante a implementação piloto e de produção.

-   Estão disponíveis informações de resolução de problemas em [Resolver problemas de implementação de aplicações no Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune) Neste momento no processo, deve desenvolver planos de comunicação para utilizadores piloto e de produção.

-   No mínimo, o plano deve incluir a aplicação que está a ser implementada, como e quando os utilizadores a vão obter, o objetivo empresarial da implementação e o que fazer se encontrarem problemas, informações de ajuda autónoma e como contactar o suporte técnico. Piloto

## Durante o piloto, irá implementar a aplicação num pequeno grupo de utilizadores e dispositivos de teste.
Tenha em consideração o seguinte: Certifique-se de que o grupo de teste é representativo dos utilizadores e dispositivos que irão utilizar a aplicação após a implementação de produção.

-   Informe o suporte técnico sobre a implementação da aplicação e certifique-se de que estão preparados para ajudar os utilizadores no grupo de teste.

-   Selecione os utilizadores de teste que irão sujeitar a aplicação a uma utilização normal e reportar os problemas de forma fiável aos administradores do piloto.

-   Ative o plano de comunicação do utilizador piloto.

-   Implementação empresarial

## Utilize os resultados piloto para ajustar a implementação empresarial.

-   Notifique o suporte técnico do agendamento de implementação de aplicações.

-   Tenha mecanismos para responder aos pedidos de ajuda e ajustar a fase de implementação, conforme necessário. Esteja preparado para resolver problemas relacionados com a implementação.

-   Ative o plano de comunicação do utilizador de produção.

-   Utilize uma abordagem faseada para implementar a aplicação, adicionando grupos de forma incremental para assegurar que a implementação está a prosseguir sem problemas.

-   Operações e manutenção

## **Operações:** monitorize a consola do Intune para ver alertas e os problemas com utilizadores ou dispositivos, e assegurar que a distribuição de aplicações está a funcionar em conformidade com a sua estrutura.
**Suporte técnico:** certifique-se de que o suporte técnico tem conhecimento de quaisquer alterações à disponibilidade das aplicações que pode resultar em pedidos de suporte.

Consulte também

### Implementar aplicações
[Resolução de problemas de implementação de aplicações no Microsoft Intune](/intune/deploy-use/deploy-apps)

[Troubleshoot app deployment problems in Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)


<!--HONumber=May16_HO2-->


