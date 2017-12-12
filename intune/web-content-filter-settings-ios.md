---
title: "Definições de filtros de conteúdo Web do Intune para dispositivos iOS"
titlesuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar para permitir e bloquear o acesso a sites a partir de dispositivos iOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 7/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16aa0f3c-8977-4495-9fbe-ca30ad278c9e
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 89641cee439d7da9f73d56c2ab3d6d8299164700
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2017
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Definições de filtros de conteúdo Web para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize estas definições para configurar URLs que os utilizadores finais dos browsers em dispositivos iOS podem ou não visitar. Existem dois métodos que pode utilizar para configurar URLs:

- **Configurar URLs** – utilize o filtro Web incorporado da Apple que procura termos para adultos, tais como linguagem inapropriada ou sexualmente explícita. Esta função avalia cada página Web à medida que é carregada e tenta identificar e bloquear conteúdo inadequado. Também pode configurar os URLs que não são verificados pelo filtro ou aqueles que são bloqueados independentemente das definições do filtro.

- **Apenas sites específicos** (apenas para o browser Safari) – estes URLs são adicionados aos marcadores do browser Safari. O utilizador **apenas** tem permissão para visitar estes sites; não pode aceder a mais nenhum site. Utilize esta opção apenas se souber a lista exata de URLs aos quais os utilizadores podem aceder.
Se não especificar nenhum URL, os utilizadores finais não poderão aceder a sites que não contenham os domínios microsoft.com, microsoft.net e apple.com.



## <a name="get-started"></a>Introdução

1. No painel Funcionalidades do dispositivo, selecione **Filtro de Conteúdo da Web (controlado apenas)**.
2. No painel **Filtro de Conteúdo Web**, escolha o **Tipo de filtro** que pretende configurar em:
    - **Não Configurado** – nenhuma filtragem é executada.
    - **Configurar URLs**
    - **Apenas sites específicos**
3. Em seguida, consoante o tipo de filtro que estiver a utilizar, efetue um dos seguintes procedimentos:


## <a name="configure-urls"></a>Configurar URLs

1. No painel **Filtro de Conteúdo da Web**, selecione uma das seguintes definições conforme necessário:
    - **URLs Permitidos** – no painel **URLs Permitidos**, introduza os URLs que pretende autorizar (ignorando o filtro Web da Apple) e escolha Introduzir após cada um.
    - **URLs Bloqueados** – no painel **URLs Bloqueados**, introduza os URLs que pretende bloquear (independentemente do filtro Web da Apple) e escolha Introduzir após cada um.
2. Quando concluir o procedimento, clique em **OK**.


## <a name="specific-websites-only"></a>Apenas sites específicos

1. No painel **Filtro de Conteúdo da Web**, configure as seguintes definições para todos os sites que pretende permitir:
    - **URL** – introduza o URL do site que pretende permitir, por exemplo, **http://www.contoso.com**.
    - **Caminho do Marcador** –introduza o caminho onde pretende armazenar o marcador, por exemplo **/Contoso/Business Apps**. Se não incluir um caminho, o marcador será adicionado à pasta de marcadores predefinida no dispositivo.
    - **Título** – introduza um título descritivo para o marcador.
2. Clique em **Adicionar** depois de introduzir as informações de cada site.
3. Quando concluir o procedimento, clique em **OK**.

>[!IMPORTANT] 
> Os seguintes URLs são automaticamente permitidos pelo Intune.
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>Concluir

Escolha **OK** para voltar ao painel **Criar Perfil** e, em seguida, selecione **Criar**.

## <a name="next-steps"></a>Passos seguintes

Agora pode atribuir o perfil do dispositivo aos grupos que selecionar. Para obter detalhes, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
