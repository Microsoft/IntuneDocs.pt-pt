---
title: Personalizar o Portal da Empresa | Microsoft Intune
description: "Explica como personalizar o Portal da Empresa na sua subscrição do Intune"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c1e08cc49d75303f6793894e3c8a040f6e7a8b1
ms.openlocfilehash: 1578ebcc6d4d01a6e9bee2f40cfcc07b3ae54cb2


---


# personalizar o Portal da Empresa
O [!INCLUDE[wit_iwportal_1](../includes/wit_iwportal_1_md.md)] é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.

> [!TIP]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa.

Personalizar o Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para tal, basta iniciar sessão na [consola de administrador do Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos ou de serviços, escolher **Administrador** &gt; **Portal da Empresa** e configurar as definições do Portal da Empresa.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## Informações de contacto e declaração de privacidade da empresa
O nome da empresa é apresentado como o título do Portal da Empresa. Os detalhes e as informações de contacto são apresentados aos utilizadores no ecrã Contactar TI do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |Nome da empresa|40|Este nome é apresentado como o título do Portal da Empresa.|
    |Nome do contacto do departamento de TI|40|Este nome é apresentado na página **Contactar TI**.|
    |Número de telefone do departamento de TI|20|Este número de contacto é apresentado na página **Contactar TI**.|
    |Endereço de e-mail do departamento de TI|40|Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato **alias@nomedodominio.com**.|
    |Informações adicionais|120|Apresentado na página **Contactar TI**.|
    |URL da declaração de privacidade da empresa|79|Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato https://www.contoso.com.|

## Contactos de suporte
O site de suporte é apresentado para os utilizadores no Portal da Empresa para que possam aceder ao suporte online.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |URL do site de suporte|150|Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato https://www.contoso.com. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa.|
    |Nome do site|40|Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação **Aceder ao site de TI** será apresentada na página **Contactar TI** no Portal da Empresa.|

## Personalização da imagem corporativa da empresa
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.

|Nome do campo|Mais informações|
    |----------|----------------|
    |Cor do tema|Selecione a cor do tema que pretende aplicar ao Portal da Empresa.|
    |Incluir o logótipo da empresa|Quando ativa esta opção, pode carregar o logótipo da sua empresa que pretende que seja apresentado no Portal da Empresa. Pode carregar dois logótipos: um que é apresentado quando o fundo do Portal da Empresa é branco, e outro que é apresentado quando o fundo do Portal da Empresa utiliza a cor do tema que selecionou. Cada logótipo tem de ser um tipo de ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 100 pixéis e ter um tamanho até 750 KB.|
    |Selecionar um fundo para a aplicação Portal da Empresa do [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]|Esta definição afeta apenas o fundo da aplicação Portal da Empresa do [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)].|


Depois de guardar as alterações, pode utilizar as ligações fornecidas na parte inferior da página **Portal da Empresa** da consola de administração para ver o site do Portal da Empresa. Estas ligações não podem ser alteradas. Quando um utilizador inicia sessão, estas ligações apresentam as suas subscrições no Portal da Empresa.

### Passos seguintes
Parabéns! Acabou de concluir o passo 7 do *Guia de introdução do Intune*.
>[!div class="step-by-step"]

>[&larr; **Criar políticas e aplicações**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**Inscrever dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Aug16_HO5-->


