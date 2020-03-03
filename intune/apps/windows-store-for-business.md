---
title: Gerir aplicativos VPP da Microsoft Store para negócios
titleSuffix: Microsoft Intune
description: Saiba como pode sincronizar aplicações em Intune a partir da Microsoft Store for Business.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8782d18b1a16ffc9bc7e48b19a1b70fdfbe71b8
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216140"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Como gerir as aplicações adquiridas em volume na Microsoft Store para Negócios com a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Na [Loja Microsoft para Empresas](https://www.microsoft.com/business-store) pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir do portal do Azure. Por exemplo:
* Pode sincronizar a lista de aplicações que adquiriu (ou que são gratuitas) na loja com o Intune.
* As aplicações que são sincronizadas aparecem na consola de administração do Intune. Pode atribuí-las como todas as outras aplicações.
* As versões licenciadas online e offline de Apps são sincronizadas para Intune. Os nomes das aplicações serão anexados com "Online" ou "Offline" no portal.
* Pode controlar quantas licenças estão disponíveis e quantas estão a ser utilizadas na consola de administração do Intune.
* O Intune bloqueará a atribuição e instalação de aplicações se tiver um número insuficiente de licenças disponíveis.
* As aplicações geridas pela Microsoft Store para Empresas revogam as licenças automaticamente quando um utilizador sai da empresa ou quando o administrador remove o utilizador e os dispositivos do mesmo.

## <a name="before-you-start"></a>Antes de começar

Antes de iniciar a sincronização e a atribuição de aplicações da Loja Microsoft para Empresas, reveja as seguintes informações:

- Configure o Intune como a autoridade de gestão de dispositivos móveis da sua organização.
- Tem de se ter inscrito numa conta na Loja Microsoft para Empresas.
- Após associar uma conta da Microsoft Store para Empresas, não pode mudar para uma conta diferente no futuro.
- As aplicações compradas na loja não podem ser adicionadas ou eliminadas manualmente do Intune. Só podem ser sincronizadas com a Loja Microsoft para Empresas.
- As aplicações licenciadas online e offline que comprou na Microsoft Store para Empresas são sincronizadas no portal do Intune. Poderá então implementar essas aplicações em grupos de dispositivos ou grupos de utilizadores. 
- As instalações de aplicações online são geridas pela loja.
- As aplicações offline gratuitas também podem ser sincronizadas com o Intune. Estas aplicações são instaladas pelo Intune e não pela loja.
- Para utilizar esta capacidade, os dispositivos devem ser unidos aos Serviços de Domínio de Diretório Ativo, Azure AD aderido ou unidos no local de trabalho.
- Os dispositivos inscritos têm de utilizar a versão 1511 do Windows 10 ou posterior.

Além disso, as aplicações Licenciadas Offline e os conjuntos relacionados sincronizados a partir da Microsoft Store para Empresas serão consolidados numa única entrada de aplicação na IU. Todos os detalhes da implementação dos pacotes individuais serão migrados para uma única entrada. Para visualizar conjuntos relacionados no portal Azure, selecione **licenças** de App do painel **apps.**

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associar a sua conta da Loja Microsoft para Empresas ao Intune
Antes de ativar a sincronização na consola do Intune, tem de configurar a conta da loja para utilizar o Intune como ferramenta de gestão:
1. Certifique-se de que assina na [Microsoft Store for Business](https://www.microsoft.com/business-store) utilizando a mesma conta de inquilino que utiliza para iniciar sintonização.
2. Na Loja de Negócios, escolha o separador **Gerir,** selecione **Definições**e escolha o separador **Distribute.**
3. Se não tiver especificamente o **Microsoft Intune** disponível como uma ferramenta de gestão de dispositivos móveis, escolha adicionar **ferramenta de gestão Add** para adicionar Microsoft **Intune**. Se não tiver o **Microsoft Intune** ativado como ferramenta de gestão de dispositivos móveis, clique em **Ativar** ao lado do **Microsoft Intune**. Note que deve ativar o **Microsoft Intune** em vez de **Microsoft Intune Registration**.

> [!NOTE]
> Anteriormente, só podia associar uma ferramenta de gestão para atribuir aplicações com a Loja Microsoft para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager. 

Agora, pode continuar e configurar a sincronização na consola do Intune.

## <a name="configure-synchronization"></a>Configurar a sincronização

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **a administração** do Inquilino > **Conectores e fichas** > **Microsoft Store para negócios.**
3. Clique em **Ativar**.
4. Se ainda não o fez, clique na ligação para se inscrever na Loja Microsoft para Empresas e associe a sua conta conforme explicado anteriormente.
5. Na lista pendente **Idioma**, selecione o idioma no qual as aplicações da Microsoft Store para Empresas são apresentadas no portal do Azure. Independentemente do idioma em que são apresentadas, serão instaladas no idioma do utilizador final, se estiver disponível.
6. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicações

1. Selecione **a administração** do Inquilino > **Conectores e fichas** > **Microsoft Store para negócios.**
2. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

> [!NOTE]
> As aplicações com pacotes de aplicações encriptadas não são atualmente suportadas e não serão sincronizadas para intune.

## <a name="assign-apps"></a>Atribuir aplicações

As aplicações da loja são atribuídas da mesma forma que atribui qualquer outra aplicação Intune. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md). 

As aplicações offline podem ser direcionadas para grupos de utilizadores, grupos de dispositivos ou grupo com utilizadores e dispositivos.
As aplicações offline podem ser instaladas para um utilizador específico num dispositivo ou para todos os utilizadores num dispositivo. 


Quando atribui uma aplicação da Loja Microsoft para Empresas, é utilizada uma licença por cada utilizador que instalar a aplicação. Se utilizar todas as licenças disponíveis para uma aplicação atribuída, não poderá atribuir mais cópias. Efetue uma das seguintes ações:
* Desinstale a aplicação de dispositivos.
* Reduza o âmbito da atribuição atual, segmentando apenas os utilizadores para os quais tem licenças suficientes.
* Compre mais cópias da aplicação na Loja Microsoft para Empresas.

## <a name="remove-apps"></a>Remover aplicações

Para remover uma aplicação sincronizada a partir da Microsoft Store para Empresas, tem de iniciar sessão na Microsoft Store para Empresas e reembolsar a aplicação. O processo é o mesmo, quer a aplicação seja gratuita ou não. Para uma aplicação gratuita, a loja reembolsará $0. O exemplo abaixo mostra um reembolso para uma aplicação gratuita. 

![Captura de ecrã a mostrar os detalhes da remoção da aplicação](./media/windows-store-for-business/microsoft-store-for-business-01.png)

> [!NOTE]
> Remover a visibilidade de uma aplicação na loja privada não impedirá a Intune de sincronizar a aplicação. Tem de reembolsar a aplicação para remover totalmente a aplicação.

## <a name="next-steps"></a>Próximos passos

- [Gerir aplicações e livros comprados em grandes volumes com o Microsoft Intune](../vpp-apps.md)
