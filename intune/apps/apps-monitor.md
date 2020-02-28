---
title: Monitorizar informações e atribuições da aplicação
titleSuffix: Microsoft Intune
description: Depois de atribuir uma aplicação aos utilizadores ou dispositivos, utilize estas informações para o ajudar a monitorizar o estado da aplicação.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d044357ffe15a0f621636cf2a8524851d72595d2
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781313"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Monitorizar informações e atribuições da aplicação com o Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune fornece várias formas de monitorizar as propriedades de aplicações que gere e de gerir o estado de atribuição da aplicação.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações.**
3. Na lista de aplicações, selecione uma aplicação a monitorizar. Em seguida, verá o painel de aplicações, que inclui uma descrição geral do estado dos dispositivos e dos utilizadores.

> [!NOTE]
> As aplicações da Loja Android que são implementadas como **Disponíveis** não comunicam o respetivo estado de instalação.
>
> Para aplicações geridas do Google Play implementadas para dispositivos de perfil de trabalho Android Enterprise, pode ver o estado e o número de versão da aplicação instalada num dispositivo utilizando o Intune. 

## <a name="app-overview-pane"></a>Painel Descrição geral da aplicação

No painel da aplicação, pode rever os detalhes acerca do estado de uma aplicação no seu ambiente.

### <a name="essentials"></a>Essentials
A secção **Essentials** contém as seguintes informações sobre a aplicação:

 | **Detalhes da aplicação**            | **Descrição**                                                      |
|------------------------|------------------------------------------------------------------|
| **Publicador**          | O publicador da aplicação.                                            |
| **Sistema operativo**   | O sistema operativo da aplicação (Windows, iOS/iPadOS, Android, e assim por diante). |
| **Criado**             | A data e hora em que esta revisão foi criada. <b>**Nota**: Este valor de data é atualizado quando um administrador de TI altera os metadados da aplicação, tais como alterar a categoria de aplicação ou descrição da aplicação.                        |
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

> [!NOTE]
> Esteja ciente de que as aplicações Android LOB (. APK) implementado como **disponível com ou sem inscrição** apenas reporte o estado de instalação da aplicação para dispositivos matriculados. O estado de instalação das aplicações não está disponível para dispositivos que não estão inscritos no Intune.

### <a name="device-install-status"></a>Estado de instalação do dispositivo

Uma lista de estados do dispositivo é apresentada ao selecionar **Estado de instalação do dispositivo** na secção **Monitorizar** do menu. A tabela de detalhes inclui as seguintes colunas:

| **Coluna do dispositivo**      | **Descrição**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nome do dispositivo**      | O nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. Este atributo não está disponível em mais nenhum dispositivo.                                                                       |
| **Nome de utilizador**        | O nome do utilizador.                                                                                                                                                                                                                                      |
| **Plataforma**         | O sistema operativo do dispositivo (Windows, iOS/iPadOS, Android, e assim por diante).                                                                                                                                                                                           |
| **Versão**          | O número da versão da aplicação. Para aplicações de linha de negócios (LOB) e aplicações da Microsoft Store para Empresas, será apresentado o número completo da versão da aplicação. O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), Por exemplo, 2.2 (2.2.17560800). Para aplicações da Loja padrão, não são apresentadas as versões. |
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

- Para obter mais informações sobre como trabalhar com os dados do seu Intune, veja [Utilizar o Armazém de Dados do Intune](../reports-nav-create-intune-reports.md).
- Para saber mais sobre as políticas de configuração de aplicações, veja [Políticas de configuração de aplicações do Intune](app-configuration-policies-overview.md).
