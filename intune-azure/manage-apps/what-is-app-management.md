---
title: "O que é a gestão de aplicações | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: utilizar este tópico para conhecer as noções básicas sobre a gestão de aplicações com o Microsoft Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: a9748a0ad6b9bbe10e36ba133ba74edb6aa6e09a
ms.openlocfilehash: 34970d6adcfe41a6de9636a5605a17f9f5ef2d82
ms.contentlocale: pt-pt
ms.lasthandoff: 05/05/2017


---

# <a name="what-is-microsoft-intune-app-management"></a>O que é a gestão de aplicações do Microsoft Intune?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Como administrador de TI, é provável que tenha a tarefa de garantir que os utilizadores finais têm acesso às aplicações de que precisam para trabalhar. Esta tarefa pode ser um desafio porque:
- Existe uma grande variedade de plataformas de dispositivos e de tipos de aplicações.
- Poderá ter de gerir as aplicações em dispositivos da empresa, bem como os dispositivos próprios dos utilizadores.
- É preciso fazer tudo isto e, ao mesmo tempo, garantir que a sua rede e os dados permanecem seguros. 

Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune.

O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos à sua escolha.

## <a name="app-management-capabilities-by-platform"></a>Capacidades de gestão de aplicações por plataforma

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|Adicionar e atribuir aplicações a dispositivos e utilizadores|Sim|Sim|Sim|Sim|
|Atribuir aplicações a dispositivos não inscritos no Intune|Sim|Sim|Não|Não|
|Utilizar políticas de configuração de aplicações para controlar o comportamento de arranque das aplicações|Não|Sim|Não|Não|
|Utilizar políticas de aprovisionamento de aplicações móveis para renovar aplicações expiradas|Não|Sim|Não|Não|
|Proteger dados da empresa em aplicações com políticas de proteção|Sim|Sim|Não|Não<sup>1</sup>|
|Remover apenas dados empresariais a partir de uma aplicação instalada (eliminação seletiva de aplicações)|Sim|Sim|Sim|Sim|
|Monitorizar atribuições de aplicações|Sim|Sim|Sim|Sim|
|Atribuir e controlar aplicações compradas em volume a partir de uma loja de aplicações|Não|Não|Não|Sim|
|Instalação obrigatória de aplicações em dispositivos (obrigatório)<sup>2</sup>|Sim|Sim|Sim|Sim|
|Instalação opcional em dispositivos a partir do Portal da Empresa (instalação disponível)|Sim|Sim|Sim|Sim|
|Instalar atalho para uma aplicação na Web (clip da Web)|Sim|Sim|Sim|Sim|
|Aplicações internas (linha de negócios)|Sim|Sim|Não|Não|
|Aplicações de uma loja|Sim|Sim|Sim|Sim|
|Atualizar aplicações|Sim|Sim|Sim|Sim|

<sup>1</sup> Considere a utilização do [Windows Information Protection](/intune-azure/configure-devices/how-to-configure-windows-information-protection) para proteger aplicações em dispositivos com o Windows 10.

<sup>2</sup>Aplica-se apenas a dispositivos geridos pelo Intune.


## <a name="how-to-get-started"></a>Como começar

Pode encontrar a maior parte das informações relacionadas com aplicações na carga de trabalho **Aplicações Móveis**, à qual pode aceder da seguinte forma:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.

    ![A carga de trabalho Aplicações Móveis](./media/apps-workload.png)

### <a name="manage"></a>Gerir o Endpoint Protection do
- **Aplicações** – Este é o local onde vai adicionar, atribuir e monitorizar a maior parte das suas aplicações. 
    - [Adicionar aplicações](add-apps.md)
    - [Atribuir aplicações](deploy-apps.md)
    - [Monitorizar aplicações](monitor-apps.md)
- **Políticas de configuração de aplicações** – as políticas de configuração de aplicações permitem-lhe disponibilizar definições que poderão ser exigidas quando um utilizador executar uma aplicação. Para mais detalhes, consulte:
    - [Políticas de configuração de aplicações](app-configuration-policies.md)
- **Políticas de proteção de aplicações** – permitem-lhe associar definições a uma aplicação para o ajudar a proteger os dados da empresa que utiliza. Por exemplo, pode restringir as capacidades de uma aplicação para comunicar com outras aplicações ou exigir que o utilizador introduza um PIN para aceder a uma aplicação da empresa.
    - [Políticas de proteção de aplicações](app-protection-policies.md)
- **Eliminação seletiva de aplicações** – remova apenas os dados empresariais do dispositivo de um utilizador selecionado por si.
    - [Eliminação seletiva de aplicações](app-selective-wipe.md)
- **Perfis de aprovisionamento do iOS** – as aplicações iOS incluem um perfil de aprovisionamento e um código assinado por um certificado. Quando o certificado expirar, a aplicação já não poderá ser executada. O Intune proporciona-lhe as ferramentas para atribuir pró-ativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
    - [Perfis de aprovisionamento de aplicações iOS](ios-app-provisioning-profile.md)

### <a name="monitor"></a>Monitor
- **Aplicações Licenciadas** – veja, atribua e monitorize as aplicações compradas em volume nas lojas de aplicações.
    - [Aplicações compradas em volume na Loja Windows para Empresas](wsfb-apps.md)
- **Aplicações Detetadas** – Mostra todas as aplicações que foram atribuídas pelo Intune e instaladas num dispositivo.
- **Estado da Instalação da Aplicação** – Mostra o estado da atribuição de uma aplicação que criou.
- **Estado da proteção da aplicação** – mostra o estado da política de proteção de uma aplicação de um utilizador selecionado.

Para obter mais detalhes, veja [Monitorizar aplicações](monitor-apps.md)

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](ios-vpp-apps.md) --->
- **Loja Windows para Empresas** – Configure a integração na Loja Windows para Empresas. Depois de fazê-lo, pode sincronizar com o Intune as aplicações compradas, atribuí-las e controlar a utilização da suas licenças. 
    - [Aplicações compradas em volume na Loja Windows para Empresas](wsfb-apps.md)
- **Imagem corporativa do Portal da Empresa** – personalize o Portal da Empresa de modo a dar-lhe a imagem corporativa da sua empresa. 
    - [Configuração do portal da empresa](company-portal-app.md)

