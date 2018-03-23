---
title: Como monitorizar informações e atribuições da aplicação
titlesuffix: Microsoft Intune
description: Depois de atribuir uma aplicação aos utilizadores ou dispositivos, utilize estas informações para o ajudar a monitorizar o estado da mesma.
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
ms.openlocfilehash: 2d1ca013b7000282316a17e02dcb38b3d4f27958
ms.sourcegitcommit: 820f950d1fc80b1eb5db1b0cf77f44d92a969951
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Como monitorizar informações e atribuições da aplicação com o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune fornece várias formas através das quais pode monitorizar as propriedades das aplicações que gere, assim como os respetivos estados das atribuições.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se no grupo **Monitorização + Gestão**.
3. Selecione **Aplicações Móveis** e, em seguida, selecione **Aplicações** no grupo **Gerir**.
5. Na lista de aplicações, selecione uma aplicação que pretenda monitorizar. Em seguida, verá o painel da aplicação com uma descrição geral do estado do dispositivo e do estado do utilizador.

## <a name="app-overview-blade"></a>Painel Descrição geral da aplicação

Pode utilizar o painel específico da aplicação para rever os detalhes acerca do estado de uma aplicação no seu ambiente.

### <a name="essentials"></a>Essentials
A secção **Essentials** contém as seguintes informações sobre a aplicação:

 | **Detalhes da Aplicação**            | **Descrição**                                                      |
|------------------------|------------------------------------------------------------------|
| **Publicador**          | Publicador da aplicação.                                            |
| **Sistema operativo**   | O sistema operativo da aplicação (Windows, iOS, Android, etc.) |
| **Criado**             | A data e hora em que esta revisão foi criada.                         |
| **Atribuído**           | **Sim** ou **Não**, consoante a aplicação tenha ou não sido atribuída.                  |

### <a name="device-and-user-status-graphs"></a>Gráficos de estado do utilizador e do dispositivo
Os gráficos mostram o número para os seguintes estados:

| **Estado do Dispositivo**       | **Descrição**                                       |
|-----------------------|-------------------------------------------------------|
| **Instalada**         | O número de aplicações instaladas.                         |
| **Não Instalado**     | O número de aplicações não instaladas.                     |
| **Falhou**            | O número de instalações falhadas.                   |
| **Instalação Pendente**   | O número de aplicações no processo de serem instaladas. |
| **Não Aplicável**           | O número de aplicações em que o estado não é aplicável.            |

### <a name="device-install-status"></a>Estado de instalação do dispositivo

Uma lista de estado do dispositivo é apresentada ao selecionar **Estado de instalação do dispositivo** na secção **Monitorizar**. A tabela de detalhes inclui as seguintes colunas:

| **Coluna do Dispositivo**      | **Descrição**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nome do dispositivo**      | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos.                                                                       |
| **Nome de utilizador**        | O nome do utilizador.                                                                                                                                                                                                                                      |
| **Plataforma**         | O sistema operativo do dispositivo (Windows, iOS, Android, entre outros).                                                                                                                                                                                           |
| **Versão**          | O número da versão da aplicação. Para aplicações de linha de negócios, será apresentado o número da versão completo da aplicação. O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), Por exemplo, 2.2 (2.2.17560800) |
| **Estado**           | O estado da aplicação.                                                                                                                                                                                                                                     |
| **Detalhes do estado**   | Os detalhes do estado.                                                                                                                                                                                                                                     |
| **Último registo**    | A data da última sincronização do dispositivo com o Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Estado de instalação do utilizador

Uma lista de estado do utilizador é apresentada ao selecionar **Estado de instalação do utilizador** na secção **Monitorizar**. A tabela de detalhes inclui as seguintes colunas:

| **Coluna do Utilizador**     | **Descrição**                           |
|---------------------|-------------------------------------------|
| **Nome**            | O nome do utilizador no Azure AD.         |
| **Nome de utilizador**       | O nome exclusivo do utilizador.              |
| **Instalações**   | O número de instalações de aplicações usadas pelo utilizador. |
| **Falhas**        | O número de instalações falhadas pelo utilizador.     |
| **Não instalado**   | O número de aplicações não instaladas pelo utilizador. |


## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como trabalhar com os dados do seu Intune, veja [Utilizar o Armazém de Dados do Intune](reports-nav-create-intune-reports.md).
- Para saber mais sobre as políticas de configuração de aplicações, veja [Políticas de configuração de aplicações do Intune](app-configuration-policies-overview.md).