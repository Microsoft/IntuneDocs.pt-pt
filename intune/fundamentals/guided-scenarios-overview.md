---
title: Visão geral dos cenários orientados
titleSuffix: Microsoft Intune
description: Saiba mais sobre os cenários guiados do Intune disponíveis no portal de gerenciamento de dispositivos Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ebb17324355fff9631ef74a76388ef0ab797d437
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899132"
---
# <a name="intune-guided-scenarios-overview"></a>Visão geral dos cenários guiados do Intune 

Um cenário guiado é uma série personalizada de etapas centradas em um caso de uso de ponta a ponta. Cenários comuns são baseados na função que um administrador, um usuário ou um dispositivo desempenha em sua organização. Essas funções normalmente exigem uma coleção de perfis, configurações, aplicativos e controles de segurança com cuidado, para fornecer a melhor experiência de usuário e segurança.    

Se você não estiver familiarizado com todas as etapas e os recursos necessários para implementar um cenário específico do Intune, cenários orientados podem ser usados como ponto de partida. O cenário guiado montará políticas, aplicativos, atribuições e outras configurações de gerenciamento automaticamente. Além disso, os cenários orientados podem omitir deliberadamente determinadas opções que não são aplicáveis ou incomuns para o cenário fornecido. 

Cenários guiados não são um espaço de gerenciamento diferente dos fluxos de trabalho normais do Intune. Esses fluxos de trabalho devem ser usados em conjunto com os fluxos de trabalho existentes do Intune para perfis, aplicativos e políticas. Após a conclusão de um cenário guiado, todo o gerenciamento futuro do cenário deve ocorrer nos menus existentes para políticas, aplicativos e perfis. Um cenário guiado não salva um tipo de recurso "cenário guiado" ou rastreia alterações futuras feitas nos recursos. Cada recurso criado por um cenário guiado aparecerá em sua respectiva carga de trabalho. Todas as opções, até mesmo as opções omitidas no cenário guiado, estarão disponíveis para edição nos menus existentes.  

## <a name="types-of-guided-scenarios"></a>Tipos de cenários orientados 

Para simplificar, todos os cenários guiados omitem recursos de escopo complexos, tais como marcas de escopo, grupos de exclusão e atribuições de grupo virtual. Todos os recursos criados por um cenário guiado herdarão cada marca de escopo do administrador que conclui o cenário. Determinados cenários oferecem algum nível de personalização para configuração comum para abranger cenários bem relacionados. Esses cenários oferecem suporte à atribuição de grupo apenas para grupos de inclusão. Para outros cenários orientados, todo o cenário garante uma experiência consistente ao não oferecer nenhuma personalização e gera automaticamente um novo grupo para receber todas as atribuições. Depois que o cenário guiado for concluído, você poderá usar atribuições mais sofisticadas diretamente por meio de políticas existentes, cargas de trabalho de aplicativo e perfil.  

Os cenários a seguir são guiados: 
- Implantar o Microsoft Edge para dispositivos móveis 
- Experimente um PC gerenciado em nuvem
- Proteger Microsoft Office para dispositivos móveis 

## <a name="guided-scenario-functionality"></a>Funcionalidade de cenário guiado 

Cenários orientados oferecem funcionalidade específica. Os detalhes a seguir ajudam a explicar o que você pode e não pode fazer ao seguir um cenário guiado.

### <a name="launching"></a>Launching  

Todos os cenários guiados estão disponíveis no **[portal de gerenciamento de dispositivos](https://devicemanagement.microsoft.com)**  > solução de **problemas + suporte** > **cenários orientados**. 

O cenário guiado começa com uma introdução explicando a finalidade do cenário e todos os pré-requisitos necessários para concluir a configuração. Neste ponto, as permissões de administrador são verificadas para verificar se você tem todos os privilégios necessários para concluir o cenário.  

Depois que todas as verificações de pré-requisitos forem aprovadas, o cenário oferecerá as configurações apropriadas para personalização. Cenários orientados visam apenas exigir entrada para o número mínimo de configurações e ocultar configurações não comuns ou avançadas até que sejam necessárias, ou com base em circunstâncias especiais. Cada cenário guiado é vinculado à documentação que fornece detalhes adicionais. 

Depois que todas as configurações obrigatórias são inseridas, o cenário guiado apresenta um resumo das configurações inseridas e os recursos exigidos pelo cenário. Neste ponto, nada foi salvo, a menos que explicitamente indicado.

A próxima etapa é implantar o cenário. A implantação de um cenário cria e salva todos os recursos necessários e as configurações selecionadas. O tempo necessário para concluir uma implantação varia de acordo com o cenário. Após a conclusão da implantação, o cenário guiado apresenta uma lista dos recursos criados com links para a exibição de gerenciamento de cada recurso, a carga de trabalho normal do recurso e a documentação. 

> [!IMPORTANT]
> A lista apresentada no final do cenário guiado não é salva e só é visível enquanto o cenário guiado está aberto.  
Se houver um erro ao implantar o cenário, todas as alterações serão revertidas. 

### <a name="editing"></a>Edição 

Cenários orientados não podem ser usados para editar recursos existentes. Uma vez criado, todos os recursos, grupos e atribuições devem ser editados usando as cargas de trabalho existentes.

### <a name="monitoring"></a>Monitorização 

Cenários orientados não podem ser usados para monitorar recursos existentes além do processo de criação inicial. Uma vez criado, todos os recursos, grupos e atribuições devem ser monitorados usando as cargas de trabalho existentes. 

### <a name="retiring"></a>Desativar 

Cenários orientados não podem ser usados para desativar recursos existentes, além da limpeza automatizada durante um erro na implantação inicial. Uma vez criado, todos os recursos, grupos e atribuições devem ser desativados usando as cargas de trabalho existentes. 

### <a name="updating"></a>Atualização

À medida que a tecnologia evolui, o Intune pode, de tempos em tempos, atualizar um cenário guiado para melhorar a experiência do usuário, a segurança ou outros aspectos do cenário. Essa atualização afetará apenas as novas implantações feitas pelo cenário guiado. O Intune não atualizará os recursos existentes gerados anteriormente pelo cenário guiado para fazer a correspondência de novas práticas recomendadas ou recomendações.  

## <a name="next-steps"></a>Próximos passos

Para ser executado rapidamente em Microsoft Intune, percorra os cenários guiados pelo Intune. Se você for novo no Intune, configure seu locatário do Intune seguindo o guia de [início rápido da avaliação gratuita](free-trial-sign-up.md).
