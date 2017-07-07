---
title: "Onde está a minha funcionalidade do Intune no Azure?"
titleSuffix: Intune on Azure
description: Ajuda para encontrar funcionalidades do Intune na consola do Azure."
keywords: 
author: dagerrit
ms.author: dagerrit
manager: angrobe
ms.date: 03/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b9d1ac3930e29bc024ece7e6b9b11c91a4e14c1
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Onde está a minha funcionalidade do Intune no Azure?
Organizámos algumas tarefas por ordem mais lógica ao mover o Intune para o portal do Azure. Cada melhoria significa ter de conhecer a nova localização das funcionalidades. Criámos este guia de referência para os utilizadores que estejam familiarizados com o Intune na consola clássica e que pretendam saber como efetuar tarefas no Intune no Azure. Se este artigo não abranger uma funcionalidade que procura, deixe um comentário no final do mesmo para o atualizarmos.
## <a name="quick-reference-guide"></a>Guia de referência rápida
|Funcionalidade |Caminho da consola clássica|Caminho do Intune no Azure| |------------||---------------|---------------| |Programa de Inscrição de Dispositivos (DEP) |Admin > Gestão de Dispositivos Móveis > iOS e Mac OS X > Programa de Inscrição de Dispositivos|[Inscrição de dispositivos > Inscrição da Apple > Token do Programa de Inscrição](#where-did-apple-dep-go) | |Programa de Inscrição de Dispositivos (DEP)| Admin > Gestão de Dispositivos Móveis > iOS e Mac OS X > Programa de Inscrição de Dispositivos |[Inscrição de dispositivos > Inscrição da Apple > Números de Série do Programa de Inscrição](#where-did-apple-dep-go) | |Regras de Inscrição |Admin > Gestão de Dispositivos Móveis > Regras de Inscrição|[Inscrição de dispositivos > Restrições de Inscrição](#where-did-enrollment-rules-go) | |Grupos por Número de Série iOS |Grupos > Todos os Dispositivos > Dispositivos Pré-inscritos da Empresa > Por Número de Série iOS|[Inscrição de dispositivos > Inscrição da Apple > Números de Série do Programa de Inscrição](#where-did-corporate-pre-enrolled-devices-go) | |Grupos por Número de Série iOS |Grupos > Todos os Dispositivos > Dispositivos Pré-inscritos da Empresa > Por Número de Série iOS| [Inscrição de dispositivos > Inscrição da Apple > Números de Série AC](#where-did-corporate-pre-enrolled-devices-go)| |Grupos por IMEI (todas as plataformas)| Grupos > Todos os Dispositivos > Dispositivos Pré-inscritos da Empresa > Por IMEI (Todas as plataformas) | [Inscrição de dispositivos > Identificadores de Dispositivos da Empresa](#by-imei-all-platforms)| | Perfil de Inscrição de Dispositivos da Empresa| Política > Inscrição de Dispositivos da Empresa | [Inscrição de dispositivos > Inscrição da Apple > Perfis do Programa de Inscrição](#where-did-corporate-pre-enrolled-devices-go) | | Perfil de Inscrição de Dispositivos da Empresa | Política > Inscrição de Dispositivos da Empresa | [Inscrição de dispositivos > Inscrição da Apple > Perfis AC](#where-did-corporate-pre-enrolled-devices-go) | | Android for Work | Admin > Gestão de Dispositivos Móveis > Android for Work | Inscrição de dispositivos > Inscrição do Android for Work | | Termos e Condições | Política > Termos e Condições | Inscrição de dispositivos > Termos e Condições |


## <a name="where-do-i-manage-groups"></a>Onde posso gerir os grupos?
O Intune no Azure utiliza o [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) para gerir grupos.

## <a name="where-did-enrollment-rules-go"></a>Onde estão as regras de inscrição?
Na consola clássica, pode definir regras para a inscrição MDM de dispositivos móveis e modernos Windows e macOS:

![Imagem das regras clássicas de inscrição de dispositivos móveis](./media/01-classic-rules.png)

Estas regras aplicam-se a todos os utilizadores na sua conta do Intune, sem exceção. No portal do Azure, estas regras são agora apresentadas como dois tipos de políticas distintos – Restrições de Tipos de Dispositivos e Restrições de Limite de Dispositivos:

![Imagem das restrições de inscrição de dispositivos móveis no Azure](./media/02-azure-enroll-restrictions.png)

As Restrições de Limite de Dispositivos predefinidas correspondem ao Limite de Inscrição de Dispositivos na consola clássica:

![Imagem das restrições de limite de dispositivos no Azure](./media/03-azure-device-limit.png)

As Restrições de Tipos de Dispositivos predefinidas correspondem às Restrições de Plataformas na consola clássica:

![Imagem das restrições de tipo de dispositivos no Azure](./media/04-azure-platform-restrictions.png)

A capacidade de permitir ou bloquear dispositivos pessoais é agora gerida na secção Configurações de Plataformas das Restrições de Tipos de Dispositivos:

![Imagem das definições de bloqueio de dispositivos pessoais no Azure](./media/05-azure-personal-block.png)

Serão adicionadas novas funcionalidades de restrição apenas ao Portal do Azure.

## <a name="where-did-apple-dep-go"></a>Onde está o DEP da Apple?
Na consola clássica, pode configurar o Intune para se integrar com o Programa de Registo de Aparelho da Apple e pedir a sincronização com o serviço da Apple manualmente:

![Imagem de token DEP clássico](./media/06-classic-dep-token.png)

No portal do Azure, pode configurar o Programa de Registo de Aparelho através dos mesmos passos que executaria no Intune clássico:

![Imagem de token DEP no Azure](./media/07-azure-dep-token.png)

Contudo, a opção **Sincronizar** na consola clássica foi movida para o fluxo de trabalho de gestão de números de série, uma vez que os resultados da sincronização manual serão apresentados nessa localização:

![Imagem da funcionalidade Sincronizar no DEP no Azure](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>Onde estão os dispositivos pré-inscritos da empresa?
### <a name="by-ios-serial-number"></a>Por número de série iOS
Na consola clássica, pode inscrever dispositivos iOS através do Programa de Registo de Aparelho (DEP) da Apple e da ferramenta Apple Configurator. Ambos os métodos disponibilizam a pré-inscrição de dispositivos por número de série e incluem a atribuição de perfis de Inscrição de Dispositivo da Empresa especiais. Antes da inscrição, a atribuição do perfil da inscrição pode ser gerida através do grupo de dispositivos **Dispositivos Pré-inscritos da Empresa por Número de Série iOS**:

![Imagem dos números de série da Apple clássicos](./media/09-classic-apple-serials.png)

São indicados números de série para inscrição através do DEP da Apple e do Apple Configurator numa única lista. Para reduzir a probabilidade de erros de atribuição (perfil de DEP atribuído a um número de série do AC e vice-versa), separámos os números de série em duas listas no portal do Azure:

**Números de série do DEP**
![Imagem dos números de série do DEP no Azure](./media/10-azure-dep-serials.png)

**Números de série do Apple Configurator**
![Imagem dos números de série do Apple Configurator no Azure](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>Por IMEI (todas as plataformas)

Na consola clássica, pode preparar uma lista dos números IMEI dos dispositivos para marcá-los como propriedade da empresa quando forem inscritos no Intune:

![Imagem da lista clássica dos números IMEI](./media/12-classic-corp-imei.png)

Na consola do Azure, tem de carregar o mesmo IMEI para a lista Identificadores de Dispositivo da Empresa com um ficheiro de valores separados por vírgulas (CSV). O novo portal não irá suportar a introdução manual de números IMEI:

![Imagem da lista de números IMEI no Azure](./media/13-azure-corp-imei.png)

O Intune no portal do Azure foi planeado para suportar outros tipos de identificadores para além de IMEI no futuro, mas atualmente só permite a lista já preenchida de números IMEI.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>Onde estão os perfis da Inscrição de Dispositivo da Empresa?
Para inscrever dispositivos iOS através do Programa de Registo de Aparelho ou da ferramenta Apple Configurator, tem de fornecer um perfil de Inscrição de Dispositivo da Empresa para atribuir ao dispositivo. Na consola clássica, a criação e gestão destes perfis encontrava-se numa única lista:

![Imagem da lista clássica dos perfis de inscrição de dispositivos](./media/14-classic-corp-profiles.png)

Esta lista apresenta os perfis para utilização com o Programa de Registo de Aparelho (**DEP – Ativado**) e para utilização apenas com a ferramenta Apple Configurator (**DEP – Desativado**).

Para facilitar a distinção entre os dois tipos de perfil e reduzir potenciais erros de atribuição (perfil de DEP atribuído a dispositivos do Configurator e vice-versa), separámos a criação e gestão dos perfis do Programa de Registo (suportam o Programa de Registo de Aparelho da Apple e o Gestor de Escola da Apple) e os perfis do Apple Configurator:

**Perfis de DEP**
![Imagem dos perfis de DEP no Azure](./media/15-azure-dep-profiles.png)

**Perfis do Apple Configurator**
![Imagem dos perfis do Apple Configurator no Azure](./media/16-azure-ac-profiles.png)
