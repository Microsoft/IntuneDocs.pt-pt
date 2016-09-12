---
title: "Implementação de políticas | Microsoft Intune"
description: "Recomendações para uma implementação faseada de política no Microsoft Intune."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 0c23fdd5f5e6bc1b50dda56fe2135e8cc24b5e26


---

# Implementação de políticas
Este tópico fornece recomendações específicas para uma implementação faseada de políticas no Microsoft Intune. Esta abordagem aplica-se às primeiras políticas aplicadas numa nova implementação do Intune ou às políticas adicionadas a uma implementação existente.

Para obter informações gerais sobre as fases de implementação, veja [Fases de implementação do Microsoft Intune](rollout-phases-for-microsoft-intune-deployment.md).

### Fases de implementação de políticas
As fases de implementação de políticas são:

-   Âmbito do projeto

-   Prova de conceito

-   Piloto

-   Implementação empresarial

-   Operações e manutenção

## Âmbito do projeto
Defina o âmbito da implementação de políticas do Intune:

-   Para uma nova implementação, será necessário definir todos os comportamentos de dispositivo pretendidos e os requisitos de segurança que pretende criar com o conjunto de políticas.

-   Decida quais os utilizadores e dispositivos que pretende afetar com estas políticas.

-   Crie os grupos de utilizadores e dispositivos para permitir a aplicação correta das novas políticas.

-   Determine se existem limitações ou requisitos associados a cada sistema operativo que afetem as intenções da sua política.

-   Considere especificações de estrutura da política, como o tipo e o modelo de política a utilizar.

-   Quer esteja a iniciar o primeiro conjunto de políticas ou a adicionar novas políticas a um conjunto de políticas existente, considere como várias políticas interagem entre si e qual será o comportamento de dispositivo provável. Podem ocorrer problemas com as interações de políticas e conflitos na fase Piloto, mas a deteção de conflitos de políticas no planeamento antecipado simplificará a execução do Piloto.

## Prova de conceito
Na fase Prova de conceito, teste a implementação de políticas num ambiente de laboratório em dispositivos e utilizadores que tenha configurado estritamente para fins de teste.

-   Permita a participação do suporte técnico nesta fase para saber que problemas podem surgir durante a implementação piloto e de produção. Estão disponíveis informações de resolução de problemas em [Resolver problemas de políticas no Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).

-   Neste momento no processo, deve desenvolver planos de comunicação para utilizadores piloto e de produção. No mínimo, o plano deve incluir o que os comportamentos de dispositivo irão alterar e quando, o objetivo empresarial da alteração, o que fazer se os utilizadores ou o pessoal de TI encontrarem problemas, informações de ajuda autónoma e como contactar o suporte técnico.

## Piloto
Durante o piloto, irá implementar a política num pequeno grupo de utilizadores e dispositivos de teste. Existem considerações específicas de política piloto no Intune:

-   O grupo de teste deve ser representativo do grupo ao qual será aplicada a política para implementação de produção.

-   Informe o suporte técnico sobre as alterações na política e certifique-se de que estão preparados para ajudar os utilizadores no grupo de teste.

-   Ative o plano de comunicação do utilizador piloto.

-   O piloto pode ser efetuado primeiro no modo isolado, no qual o dispositivo não está sujeito a outras políticas que possam causar conflitos e comportamentos indesejados.

-   O teste final tem de considerar a nova política e todas as políticas existentes que serão aplicadas ao mesmo dispositivo.

## Implementação empresarial

-   Com base nos resultados do piloto, ajuste a sua política planeada para corrigir os conflitos de políticas e comportamentos inesperados.

-   Notifique o suporte técnico do agendamento da implementação empresarial. Implemente mecanismos para responder aos pedidos de ajuda e para ajustar a fase de implementação, conforme necessário.

-   Esteja preparado para resolver problemas relacionados com a política.

-   Ative o plano de comunicação do utilizador de produção.

-   Aplique as políticas de forma incremental a grupos adicionais, monitorizando o estado de política para os dispositivos afetados e controlando os pedidos de suporte técnico que possam estar relacionados com a nova política.

## Operações e manutenção
**Operações:** Monitorize a consola do Intune para ver alertas e problemas com utilizadores ou dispositivos, e verifique se as políticas estão a ser aplicadas em conformidade com a sua estrutura.

**Suporte técnico:** Certifique-se de que o suporte técnico tem conhecimento de quaisquer alterações às políticas que irão afetar a experiência de utilizador, uma vez que podem resultar em pedidos de suporte.


### Consulte também
[Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Resolver problemas de políticas no Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)



<!--HONumber=Jul16_HO4-->


