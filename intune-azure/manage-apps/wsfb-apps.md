---
title: "Gerir aplicações a partir da Loja Windows para Empresas | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como pode sincronizar aplicações no Intune a partir da Loja Windows para Empresas e, em seguida, atribuir e controlá-las."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a57ac0e6cb29dbfc87bb09c04bb372228a1d72be
ms.openlocfilehash: 2acb58a8fc71ae7f2e0bce127e709a678faa27cb

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business"></a>Como gerir aplicações compradas na Loja Windows para Empresas

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Na [Loja Windows para Empresas](https://www.microsoft.com/business-store), pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir do portal do Intune. Por exemplo:
* Pode sincronizar a lista de aplicações adquiridas na loja com o Intune.
* As aplicações que são sincronizadas aparecem na consola de administração do Intune e pode atribuí-las como todas as outras aplicações.
* Pode controlar quantas licenças estão disponíveis e quantas estão a ser utilizadas na consola de administração do Intune.
* O Intune bloqueia a implementação e instalação de aplicações se tiver um número insuficiente de licenças disponíveis.

## <a name="before-you-start"></a>Antes de começar
Antes de iniciar a sincronização e a implementação de aplicações da Loja Windows para Empresas, reveja as seguintes informações:
* Tem de configurar o Intune como a autoridade de gestão de dispositivos móveis da sua organização.
* Tem de se ter inscrito numa conta na Loja Windows para Empresas.
* Assim que tiver associado uma conta da Loja Windows para Empresas, não pode mudar para uma conta diferente no futuro.
* As aplicações compradas na loja não podem ser adicionadas ou eliminadas manualmente do Intune. Só podem ser sincronizadas com a Loja Windows para Empresas.
* O Intune só sincroniza as aplicações licenciadas online que comprou na Loja Windows para Empresas.
* Para utilizar esta funcionalidade, os dispositivos têm de ser associados aos Active Directory Domain Services ou à área de trabalho.
* Os dispositivos inscritos têm de utilizar a versão 1511 do Windows 10 ou posterior.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Associar a sua conta da Loja Windows para Empresas ao Intune
Antes de ativar a sincronização na consola do Intune, tem de configurar a conta da loja para utilizar o Intune como ferramenta de gestão:
1. Certifique-se de que se regista na Loja para Empresas com a mesma conta de inquilino que utiliza para iniciar sessão no Intune.
2. Na Loja para Empresas, escolha **Definições** > **Ferramentas de gestão**.
3. Na página Ferramentas de gestão, escolha **Adicionar uma ferramenta de gestão** e **Microsoft Intune**.

> [!NOTE]
> Se estiver a utilizar mais do que uma ferramenta de gestão para implementar aplicações da Loja Windows para Empresas, antes só podia associar uma destas com a Loja Windows para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager.

Agora, pode continuar e configurar a sincronização na consola do Intune.

## <a name="configure-synchronization"></a>Configurar a sincronização

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
1. No painel **Aplicações Móveis**, escolha **Configuração** > **Loja Windows para Empresas**.
2. Clique em **Ativar**.
3. Se ainda não o fez, clique na ligação para se inscrever na Loja Windows para Empresas e associe a sua conta conforme explicado anteriormente.
5. Na lista pendente **Idioma**, escolha o idioma em que as aplicações da Loja Windows para Empresas serão apresentadas no portal do Intune. Independentemente do idioma em que são apresentadas, serão instaladas no idioma do utilizador final, se estiver disponível.
6. Clique em **Sincronização** para obter as aplicações que comprou na Loja Windows para o Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicações

1. Na carga de trabalho **Gerir aplicações**, escolha **Configuração** > **Loja Windows para Empresas**.
2. Clique em **Sincronização** para obter as aplicações que comprou na Loja Windows para o Intune.

## <a name="assign-apps"></a>Atribuir aplicações

As aplicações da loja são atribuídas da mesma forma que implementa qualquer outra aplicação Intune. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](deploy-apps.md). No entanto, em vez de atribuir aplicações a partir da página **Todas as Aplicações**, deve atribuí-las a partir da página **Aplicações Licenciadas**.

Quando atribui uma aplicação da Loja Windows para Empresas, é utilizada uma licença por cada utilizador que instalar a aplicação. Se utilizar todas as licenças disponíveis para uma aplicação implementada, não poderá implementar mais cópias. Deve efetuar uma das seguintes ações:
* Desinstale a aplicação de dispositivos.
* Reduza o âmbito da implementação atual para segmentar apenas os utilizadores para os quais tem licenças suficientes.
* Compre mais cópias da aplicação na Loja Windows para Empresas.

> [!Important]
> As aplicações implementadas só estão disponíveis para o utilizador que inscreveu originalmente o dispositivo. Nenhum outro utilizador pode aceder à aplicação.



<!--HONumber=Feb17_HO1-->


