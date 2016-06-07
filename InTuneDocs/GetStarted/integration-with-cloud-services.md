---
# required metadata

title: Integração do Intune em serviços em nuvem e produtos da Microsoft | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Integração do Intune em serviços em nuvem e produtos da Microsoft

Antes de configurar o [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)], reveja este tópico e outros requisitos listados em [O que deve saber antes de iniciar o Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)
##Integração com outros serviços em nuvem da Microsoft


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] tem uma base em comum com outros serviços em nuvem da Microsoft. Quando utiliza a mesma conta para subscrever múltiplos serviços em nuvem, esses serviços utilizam a mesma infraestrutura do Microsoft Azure AD e são inquilinos do Azure AD. O Azure AD fornece as principais funcionalidades de gestão de identidades e diretórios nos serviços em nuvem da Microsoft.

Saiba mais sobre como [administrar o Azure AD ](http://technet.microsoft.com/library/hh967611.aspx) na Biblioteca TechNet.

## Integração com outros produtos Microsoft
Pode utilizar o [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] como um serviço autónomo em nuvem ou como um serviço em nuvem integrado com outros produtos. Atualmente, apenas o [!INCLUDE[cmshort](../includes/cmshort_md.md)] pode ser integrado diretamente com o

A decisão de integrar o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] com o [!INCLUDE[cmshort](../includes/cmshort_md.md)] é uma escolha permanente que requer que defina a autoridade de gestão de dispositivos móveis a partir da consola do [!INCLUDE[cmshort](../includes/cmshort_md.md)] e não a partir do [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]. Uma vez definida a autoridade de gestão de dispositivos móveis, não poderá alterar ou inverter esta configuração.

Quando utiliza o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] com o [!INCLUDE[cmshort](../includes/cmshort_md.md)], não utiliza a [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] para gerir o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]; em vez disso, utiliza a consola do [!INCLUDE[cmshort](../includes/cmshort_md.md)]. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] continua a utilizar o respetivo armazenamento em nuvem do Azure para alojar o software que implemente nos dispositivos que gere com o

Para obter mais informações, veja [Gerir Dispositivos Móveis com o Configuration Manager e o Microsoft Intune](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10), na documentação do [!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1.

### Consulte também
[What to know before you start Microsoft Intune (O que deve saber antes de iniciar o Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)

<!--HONumber=May16_HO2-->

