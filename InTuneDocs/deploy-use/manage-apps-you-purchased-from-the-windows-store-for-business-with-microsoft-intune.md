---
title: "Gerir aplicações da Loja Windows para Empresas | Microsoft Intune"
description: "Ligue o Microsoft Intune à Loja Windows para Empresas se quiser gerir e implementar aplicações compradas em volume a partir da consola do Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 37044da4c7a58749c7b3423b1872b07d1673603d


---

# <a name="manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Manage apps you purchased from the Windows Store for Business with Microsoft Intune (Gerir aplicações compradas na Loja Windows para Empresas com o Microsoft Intune)
Na [Loja Windows para Empresas](https://www.microsoft.com/business-store), pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir da consola do Intune. Por exemplo:
* Pode sincronizar a lista de aplicações adquiridas na loja com o Intune.
* As aplicações que são sincronizadas aparecem na consola de administração do Intune e pode implementá-las como todas as outras aplicações.
* Pode controlar quantas licenças estão disponíveis e quantas estão a ser utilizadas na consola de administração do Intune.
* O Intune bloqueia a implementação e instalação de aplicações se tiver um número insuficiente de licenças disponíveis.

## <a name="before-you-start"></a>Antes de começar
Antes de iniciar a sincronização e a implementação de aplicações da Loja Windows para Empresas, reveja as seguintes informações:
* Tem de configurar o Intune como a autoridade de gestão de dispositivos móveis da sua organização. Para mais informações, consulte o artigo [Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md).
* Tem de se ter inscrito numa conta na Loja Windows para Empresas.
* Assim que tiver associado uma conta da Loja Windows para Empresas, não pode mudar para uma conta diferente no futuro.
* As aplicações compradas na loja não podem ser adicionadas ou eliminadas manualmente do Intune. Só podem ser sincronizadas com a Loja Windows para Empresas.
* O Intune só sincroniza as aplicações licenciadas online que comprou na Loja Windows para Empresas.
* Os dispositivos têm de ser associados aos Serviços de Domínio do Active Directory ou à área de Trabalho para utilizar esta capacidade.
* Os dispositivos inscritos têm de utilizar a versão 1511 do Windows 10.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Associar a sua conta da Loja Windows para Empresas ao Intune
Antes de ativar a sincronização na consola do Intune, tem de configurar a conta da loja para utilizar o Intune como ferramenta de gestão:
1. Certifique-se de que se regista na Loja para Empresas com a mesma conta de inquilino que utiliza para iniciar sessão no Intune.
2. Na Loja para Empresas, escolha **Definições** > **Ferramentas de gestão**.
3. Na página Ferramentas de gestão, escolha **Adicionar uma ferramenta de gestão** e **Microsoft Intune**.

Agora, pode continuar e configurar a sincronização na consola do Intune.

## <a name="configure-synchronization"></a>Configurar a sincronização

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Admin**.
2. Na área de trabalho **Admin**, expanda **Mobile Device Management** > **Windows** e selecione **Store for Business**.
3. Na página **Loja Windows para Empresas**, faça o seguinte:
 * Se ainda não o fez, clique na ligação para se inscrever na Loja Windows para Empresas.
 * Assim que concluir a inscrição, escolha em **Configurar Sincronização**.
4. Na caixa de diálogo **Configurar sincronização de aplicações da Loja Windows para Empresas**, selecione **Ativar sincronização da Loja Windows para Empresas**.
5. Na lista pendente **Idioma**, escolha o idioma em que as aplicações da Loja Windows para Empresas serão apresentadas na consola do Intune. Independentemente do idioma em que são apresentadas, serão instaladas no idioma do utilizador final, se estiver disponível.
6. Clique em **OK**.

## <a name="synchronize-apps"></a>Sincronizar aplicações

1. Na página **Loja Windows para Empresas**, escolha **Sincronizar agora** para sincronizar as aplicações que comprou na loja com o Intune.
2. Na área de trabalho **Aplicações**, escolha **Aplicações** > **Aplicações Compradas em Volume** para ver as aplicações que pode implementar e para confirmar se aquelas que comprou foram importadas corretamente. As aplicações neste nó são apresentadas com o número total de licenças que tiver e o número de licenças que tem disponíveis.
Por exemplo, pode comprar a aplicação do Portal da Empresa (licenciamento online) na loja Windows para Empresas, sincronizá-la com a consola do Intune e, em seguida, implementá-la como uma aplicação necessária nos dispositivos Windows 10 necessários. 


## <a name="deploy-apps"></a>Implementar aplicações

As aplicações da loja são implementadas da mesma forma que implementa qualquer outra aplicação do Intune. Para mais informações, consulte [Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Quando implementa uma aplicação da Loja Windows para Empresas, é utilizada uma licença por cada utilizador que instalar a aplicação. Se utilizar todas as licenças disponíveis para uma aplicação implementada, não poderá implementar mais cópias. Deve efetuar uma das seguintes ações:
* Desinstale a aplicação de dispositivos.
* Reduza o âmbito da implementação atual para segmentar apenas os utilizadores para os quais tem licenças suficientes.
* Compre mais cópias da aplicação na Loja Windows para Empresas.

> [!Important]
> As aplicações implementadas só estão disponíveis para o utilizador que inscreveu originalmente o dispositivo. Nenhum outro utilizador pode aceder à aplicação.


### <a name="see-also"></a>Consulte também
[Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


