---
title: Monitorizar informações e atribuições da aplicação
titlesuffix: Microsoft Intune
description: Depois de atribuir uma aplicação aos utilizadores ou dispositivos, utilize estas informações para o ajudar a monitorizar o estado da aplicação.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0408ce3a4c2d4224780b4b23b0fb1b7d690471fe
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2018
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Monitorizar informações e atribuições da aplicação com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune disponibiliza várias formas para monitorizar as propriedades das aplicações que gere e gerir o estado da atribuição das aplicações.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No menu **Intune**, selecione **Aplicações móveis**.
4. Na secção **Gerir** do menu, selecione **Aplicações**.
5. Na lista de aplicações, selecione uma aplicação a monitorizar. Em seguida, verá o painel da aplicação com uma descrição geral do estado do dispositivo e do estado do utilizador.

## <a name="app-overview-pane"></a>Painel Descrição geral da aplicação

No painel da aplicação, pode rever os detalhes acerca do estado de uma aplicação no seu ambiente.

### <a name="essentials"></a>Essentials
A secção **Essentials** contém as seguintes informações sobre a aplicação:

 | **Detalhes da aplicação**            | **Descrição**                                                      |
|------------------------|------------------------------------------------------------------|
| **Publicador**          | O publicador da aplicação.                                            |
| **Sistema operativo**   | O sistema operativo da aplicação (Windows, iOS, Android, etc.). |
| **Criado**             | A data e hora em que esta revisão foi criada.                         |
| **Atribuído**           | Se a aplicação foi atribuída (**Sim** ou **Não**).                  |

### <a name="device-and-user-status-graphs"></a>Gráficos de estado do utilizador e do dispositivo
Os gráficos mostram o número de aplicações para os seguintes estados:

| **Estado do dispositivo**       | **Descrição**                                       |
|-----------------------|-------------------------------------------------------|
| **Instalada**         | O número de aplicações instaladas.                         |
| **Não Instalado**     | O número de aplicações não instaladas.                     |
| **Falhou**            | O número de instalações falhadas.                   |
| **Instalação Pendente**   | O número de aplicações no processo de serem instaladas. |
| **Não Aplicável**           | O número de aplicações em que o estado não é aplicável.            |

### <a name="device-install-status"></a>Estado de instalação do dispositivo

Uma lista de estados do dispositivo é apresentada ao selecionar **Estado de instalação do dispositivo** na secção **Monitorizar** do menu. A tabela de detalhes inclui as seguintes colunas:

| **Coluna do dispositivo**      | **Descrição**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nome do dispositivo**      | O nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. Este atributo não está disponível em mais nenhum dispositivo.                                                                       |
| **Nome de utilizador**        | O nome do utilizador.                                                                                                                                                                                                                                      |
| **Plataforma**         | O sistema operativo do dispositivo (Windows, iOS, Android, entre outros).                                                                                                                                                                                           |
| **Versão**          | O número da versão da aplicação. Para aplicações de linha de negócios, será apresentado o número completo da versão da aplicação. O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), Por exemplo, 2.2 (2.2.17560800). |
| **Estado**           | O estado da aplicação.                                                                                                                                                                                                                                     |
| **Detalhes do estado**   | Os detalhes do estado.                                                                                                                                                                                                                                     |
| **Último registo**    | A data da última sincronização do dispositivo com o Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Estado de instalação do utilizador

Uma lista de estados do utilizador é apresentada ao selecionar **Estado de instalação do utilizador** na secção **Monitorizar** do menu. A tabela de detalhes inclui as seguintes colunas:

| **Coluna do utilizador**     | **Descrição**                           |
|---------------------|-------------------------------------------|
| **Nome**            | O nome do utilizador no Azure Active Directory.         |
| **Nome de utilizador**       | O nome exclusivo do utilizador.              |
| **Instalações**   | O número de aplicações instaladas pelo utilizador. |
| **Falhas**        | O número de falhas nas instalações das aplicações para o utilizador.     |
| **Não instalado**   | O número de aplicações não instaladas pelo utilizador. |


## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como trabalhar com os dados do seu Intune, veja [Utilizar o Armazém de Dados do Intune](reports-nav-create-intune-reports.md).
- Para saber mais sobre as políticas de configuração de aplicações, veja [Políticas de configuração de aplicações do Intune](app-configuration-policies-overview.md).
