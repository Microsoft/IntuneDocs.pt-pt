---
title: Personalizar o Portal da Empresa | Documentos da Microsoft
description: "O Portal da Empresa do Intune permite aos utilizadores realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações do departamento de TI."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 3794981387e73176152c212854a97b4333023f5d
ms.lasthandoff: 04/24/2017


---

# <a name="customize-the-company-portal"></a>Personalizar o Portal da Empresa

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico informa os administradores sobre como podem personalizar a aplicação Portal da Empresa do Intune e o site do Portal da Empresa.

O Portal da Empresa do Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.

O Portal da Empresa do Intune proporciona aos utilizadores acesso a aplicações e dados da empresa. O Portal da Empresa está disponível em dois formatos:

-   **A aplicação Portal da Empresa**: uma aplicação disponível nos dispositivos que gere com o Intune. Saiba mais sobre as aplicações Portal da Empresa para [Android](/Intune/EndUser/using-your-android-device-with-intune), [iOS](/Intune/EndUser/using-your-iOS-or-macOS-device-with-intune) e [Windows](/Intune/EndUser/using-your-windows-device-with-intune).


- **O site do Portal da Empresa**: um site que permite aos utilizadores finais realizar a maioria das tarefas executáveis a partir da aplicação Portal da Empresa. O URL do Portal da Empresa do Intune é [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com). Saiba mais sobre este site em [Utilizar o site do Portal da Empresa do Intune](/Intune/EndUser/using-the-intune-company-portal-website).

> [!TIP]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa.

Algumas das tarefas que os utilizadores podem fazer no Portal da Empresa são:

-   Inscrever dispositivos
-   Ver o estado dos respetivos dispositivos
-   Inscrever os respetivos dispositivos
-   Repor as palavras-passe
-   Bloquear remotamente os dispositivos
-   Transferir software implementado pela sua organização
-   Contactar o departamento de TI para obter suporte

## <a name="customize-company-portal-settings"></a>Personalizar as definições do Portal da Empresa
Personalizar o Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Inicie sessão na [consola de administrador do Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos ou de serviços, escolha **Administrador** &gt; **Portal da Empresa** e configure as definições do Portal da Empresa.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## <a name="company-contact-information-and-privacy-statement"></a>Informações de contacto e declaração de privacidade da empresa
O nome da empresa é apresentado como o título do Portal da Empresa. Os detalhes e as informações de contacto são apresentados aos utilizadores no ecrã Contactar TI do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |Nome da empresa|40|Este nome é apresentado como o título do Portal da Empresa.|
    |Nome do contacto do departamento de TI|40|Este nome é apresentado na página **Contactar TI**.|
    |Número de telefone do departamento de TI|20|Este número de contacto é apresentado na página **Contactar TI**.|
    |Endereço de e-mail do departamento de TI|40|Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato **alias@domainname.com**.|
    |Informações adicionais|120|Apresentado na página **Contactar TI**.|
    |URL da declaração de privacidade da empresa|79|Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato https://www.contoso.com.|

## <a name="support-contacts"></a>Contactos de suporte
O site de suporte é apresentado para os utilizadores no Portal da Empresa para que possam aceder ao suporte online.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |URL do site de suporte|150|Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato https://www.contoso.com. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa.|
    |Nome do site|40|Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação **Aceder ao site de TI** será apresentada na página **Contactar TI** no Portal da Empresa.|

## <a name="company-branding-customization"></a>Personalização da imagem corporativa da empresa
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.

|Nome do campo|Mais informações|
    |----------|----------------|
    |Cor do tema|Selecione a cor do tema que pretende aplicar ao Portal da Empresa.|
    |Incluir o logótipo da empresa|Quando ativa esta opção, pode carregar o logótipo da sua empresa que pretende que seja apresentado no Portal da Empresa. Pode carregar dois logótipos: um que é apresentado quando o fundo do Portal da Empresa é branco e outro que é apresentado quando o fundo do Portal da Empresa utiliza a cor do tema que selecionou. Cada logótipo tem de ser um tipo de ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 100 pixéis e ter um tamanho até 750 KB.|
    |Selecionar um fundo para a aplicação Portal da Empresa do [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]|Esta definição afeta apenas o fundo da aplicação Portal da Empresa do [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)].|


Depois de guardar as alterações, pode utilizar as ligações fornecidas na parte inferior da página **Portal da Empresa** da consola de administração para ver o site do Portal da Empresa. Estas ligações não podem ser alteradas. Quando um utilizador inicia sessão, estas ligações apresentam as suas subscrições no Portal da Empresa.

>[!div class="step-by-step"]

>[&larr; **Criar políticas e aplicações**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**Inscrever dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  

