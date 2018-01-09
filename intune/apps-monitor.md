---
title: "Como monitorizar informações e atribuições da aplicação"
titlesuffix: Azure portal
description: "Depois de atribuir uma aplicação aos utilizadores ou dispositivos, utilize estas informações para o ajudar a monitorizar o estado da mesma."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cb95319d2574116d480de9bdf74ef36129d0970f
ms.sourcegitcommit: 9fabf1a8db53842f7b00762374de5b137158ee25
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Como monitorizar informações e atribuições da aplicação com o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune fornece várias formas através das quais pode monitorizar as propriedades das aplicações que gere, assim como os respetivos estados das atribuições.

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
3. Na carga de trabalho **Aplicações Móveis**, selecione **Aplicações** no grupo **Gerir**.
5. Na lista do painel de aplicações, selecione uma aplicação. Em seguida, verá o painel <*nome da aplicação*> **Estado de instalação do dispositivo**.

## <a name="app-overview-blade"></a>Painel Descrição geral da aplicação

Pode utilizar o painel **Estado de instalação do dispositivo** da aplicação *<nome da aplicação> * para rever os detalhes acerca do estado de uma aplicação no seu computador.

### <a name="essentials"></a>Essentials

A secção **Essentials** contém as seguintes informações sobre a aplicação:

 - **Publicador**  
Publicador da aplicação.
 - **Sistema operativo**  
O sistema operativo da aplicação (Windows, iOS, Android, entre outros)
 - **Criar**  
A hora em que esta revisão foi criada.
 - **Atribuído**  
**Sim** ou **Não**, consoante a aplicação tenha ou não sido atribuída.

### <a name="status"></a>Estado
Cada gráfico mostra os valores para os seguintes estados:

 - **Instalada**  
O número de aplicações instaladas.
 - **Não Instalado**  
O número de aplicações não instaladas.
 - **Instalação Pendente**  
O número de aplicações no processo de serem instaladas.
 - **Falhou**  
O número de instalações falhadas.
 - **Desconhecido**  
O número de aplicações com um estado desconhecido.

### <a name="device-status"></a>Estado do dispositivo

Estado do dispositivo. Um gráfico em anel que apresenta o estado da instalação das aplicações nos dispositivos. Clique no gráfico para abrir uma lista de detalhes sobre o estado do dispositivo. A tabela de detalhes inclui as seguintes colunas:

 - **Nome do dispositivo**  
Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos.
 - **Nome de utilizador**  
O nome do utilizador.
 - **Plataforma**  
O sistema operativo do dispositivo (Windows, iOS, Android, entre outros).
 - **Versão**  
O número da versão da aplicação. Para aplicações de linha de negócios, será apresentado o número da versão completo da aplicação. O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), por exemplo, 2.2(2.2.17560800).
 - **Estado**  
O estado da aplicação.
 - **Detalhes do estado**  
Os detalhes do estado.
 - **Último registo**  
A data da última sincronização do dispositivo com o Intune.


### <a name="user-status"></a>Estado de utilizador

O estado do utilizador. Um gráfico em anel que apresenta o estado da instalação das aplicações para os utilizadores. Clique no gráfico para abrir uma lista de detalhes sobre o estado do dispositivo. A tabela de detalhes inclui as seguintes colunas:
 - **Nome**  
O nome do utilizador no Azure AD.
 - **Nome de utilizador**  
O nome exclusivo do utilizador.
 - **Instalações**  
O número de instalações de aplicações usadas pelo utilizador.
 - **Falhas**  
O número de instalações falhadas pelo utilizador.
 - **Não instalado**  
O número de aplicações não instaladas pelo utilizador.


## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre como trabalhar com os dados do seu Intune, veja [Utilizar o Armazém de Dados do Intune](reports-nav-create-intune-reports.md).