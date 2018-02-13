---
title: "O que é a gestão de aplicações"
titlesuffix: Azure portal
description: "Utilize este tópico para conhecer as noções básicas sobre a gestão de aplicações com o Microsoft Intune\""
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/08/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 00e6b9f05f967da9066639dbf1b25bc76a49541b
ms.sourcegitcommit: 0a5f424a8f683daa919b13b5c363173040d561c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/13/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>O que é a gestão de aplicações do Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Como administrador de TI, é responsável por garantir que os utilizadores finais têm acesso às aplicações de que precisam para trabalhar. Esta tarefa pode ser um desafio porque:
- Existe uma grande variedade de plataformas de dispositivos e de tipos de aplicações.
- Poderá ter de gerir as aplicações nos dispositivos da empresa e nos próprios dispositivos dos utilizadores.
- Tem de verificar se a sua rede e os seus dados permanecem seguros.

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
|Aplicações internas (linha de negócios)|Sim|Sim|Não|Sim|
|Aplicações de uma loja|Sim|Sim|Sim|Sim|
|Atualizar aplicações|Sim|Sim|Sim|Sim|

<sup>1</sup> Considere a utilização do [Windows Information Protection](windows-information-protection-configure.md) para proteger aplicações em dispositivos com o Windows 10.

<sup>2</sup>Aplica-se apenas a dispositivos geridos pelo Intune.

## <a name="how-to-get-started"></a>Como começar

Pode encontrar a maior parte das informações relacionadas com aplicações na carga de trabalho **Aplicações Móveis**, à qual pode aceder da seguinte forma:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.

    ![A carga de trabalho Aplicações Móveis](./media/apps-workload.png)

### <a name="manage"></a>Gerir o Endpoint Protection do
- **Aplicações** – Este nó é o local onde adiciona, atribui e monitoriza a maior parte das suas aplicações.
    - [Adicionar aplicações](apps-add.md)
    - [Atribuir aplicações](apps-deploy.md)
    - [Monitorizar aplicações](apps-monitor.md)
- **Políticas de configuração de aplicações** – as políticas de configuração de aplicações permitem-lhe disponibilizar definições que poderão ser exigidas quando um utilizador executar uma aplicação.
    - [Políticas de configuração de aplicações iOS](app-configuration-policies-use-ios.md)
    - [Políticas de configuração de aplicações Android](app-configuration-policies-use-android.md)
- **Políticas de proteção de aplicações** – permitem-lhe associar definições a uma aplicação para o ajudar a proteger os dados da empresa que utiliza. Por exemplo, pode restringir as capacidades de uma aplicação para comunicar com outras aplicações ou exigir que o utilizador introduza um PIN para aceder a uma aplicação da empresa.
    - [Políticas de proteção de aplicações](app-protection-policies.md)
- **Eliminação seletiva de aplicações** – remova apenas os dados empresariais do dispositivo de um utilizador selecionado por si.
    - [Eliminação seletiva de aplicações](apps-selective-wipe.md)
- **Perfis de aprovisionamento do iOS** – as aplicações iOS incluem um perfil de aprovisionamento e um código assinado por um certificado. Quando o certificado expirar, a aplicação já não poderá ser executada. O Intune proporciona-lhe as ferramentas para atribuir pró-ativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
    - [Perfis de aprovisionamento de aplicações iOS](app-provisioning-profile-ios.md)

Para obter mais detalhes, veja [Gerir aplicações](app-management.md).

### <a name="monitor"></a>Monitor
- **Licenças de aplicações** – veja, atribua e monitorize as aplicações compradas em volume nas lojas de aplicações.
    - [Aplicações compradas em volume na Loja Microsoft para Empresas](windows-store-for-business.md)
- **Aplicações Detetadas** – mostra todas as aplicações que foram atribuídas pelo Intune e instaladas num dispositivo.
- **Estado da Instalação da Aplicação** – Mostra o estado da atribuição de uma aplicação que criou.
- **Estado da proteção da aplicação** – mostra o estado da política de proteção de uma aplicação de um utilizador selecionado.
- **Registos de auditoria** – mostra a atividade relacionada com a aplicação do Intune realizada por todos os administradores de TI.

Para obter mais detalhes, veja [Monitorizar aplicações](apps-monitor.md).

### <a name="setup"></a>Setup
- **Tokens VPP do iOS** – aplique e veja as suas licenças de Volume Purchase Program (VPP) iOS.
    - [Aplicações iOS compradas em volume](vpp-apps-ios.md)
- **Certificado empresarial do Windows** – aplique ou veja o estado de um certificado de assinatura de código que serve para distribuir aplicações de linha de negócio nos dispositivos Windows geridos. 
- **Certificado da Symantec do Windows** – aplique ou veja o estado de um certificado de assinatura de código da Symantec, que é preciso para distribuir ficheiros appx de XAP e WP8.x aos dispositivos Windows 10 Mobile. 
- **Loja Microsoft para Empresas** – configure a integração na Loja Microsoft para Empresas. Em seguida, pode sincronizar com o Intune as aplicações compradas, atribuí-las e controlar a utilização das suas licenças.
    - [Aplicações compradas em volume na Loja Microsoft para Empresas](windows-store-for-business.md)
- **Chaves de sideloading do Windows** – pode adicionar uma chave de sideloading do Windows que pode utilizar para instalar uma aplicação diretamente nos dispositivos, em vez de publicar e transferir a aplicação da Loja Windows.
    - [Fazer sideload de uma aplicação Windows](app-sideload-windows.md) 
- **Imagem corporativa do Portal da Empresa** – personalize o Portal da Empresa de modo a dar-lhe a imagem corporativa da sua empresa.
    - [Configuração do portal da empresa](company-portal-app.md)
- **Categorias de aplicações** – adicione, afixe e elimine nomes de categorias de aplicações.
- **Android for Work** – aprove e sincronize as aplicações aprovou para a sua empresa.
    - [Aplicações Android for Work](apps-add-android-for-work.md) 

### <a name="help-and-support"></a>Ajuda e Suporte
- **Ajuda e suporte** – resolva problemas, peça suporte ou veja o estado do Intune.
    - [Resolver problemas](help-desk-operators.md)
