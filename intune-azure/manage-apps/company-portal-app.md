---
title: "Como configurar a aplicação do Portal da Empresa | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como pode aplicar a imagem corporativa específica da empresa à aplicação do Portal da Empresa do Intune. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 142b57f48c2950f6eecc228decfa06ce44c76319
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Como configurar a aplicação Portal da Empresa do Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O portal da empresa do Microsoft Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.

> [!Tip]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa.

Personalizar o Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para fazê-lo, na carga de trabalho **Gerir aplicações**, escolha **Configuração** > **Imagem Corporativa Portal da empresa** e, em seguida, configure as definições necessárias.

## <a name="company-contact-information-and-privacy-statement"></a>Informações de contacto e declaração de privacidade da empresa
O nome da empresa é apresentado como o título do Portal da Empresa. Os detalhes e as informações de contacto são apresentados aos utilizadores no ecrã **Contactar TI** do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.


|Nome do campo|Comprimento máximo|Mais informações|
|-|-|-|
|**Nome da empresa**|40|Este nome é apresentado como o título do Portal da Empresa.|
|**Nome do contacto do departamento de TI**|40|Este nome é apresentado na página **Contactar TI**.|
|**Número de telefone do departamento de TI**|20|Este número de contacto é apresentado na página **Contactar TI**.|
|Endereço de e-mail do departamento de TI|40|Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato **alias@domainname.com**.|
|**Informações adicionais**|120|Apresentado na página **Contactar TI**.|
|**URL da declaração de privacidade da empresa**|79|Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato **https://www.contoso.com**.|

## <a name="support-contacts"></a>Contactos de suporte
O site de suporte é apresentado para os utilizadores no Portal da Empresa para que possam aceder ao suporte online.



|Nome do campo|Comprimento máximo|Mais informações|
|-|-|-|
|**URL do site de suporte**|150|Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato **https://www.contoso.com**. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa.|
|**Nome do site de suporte**|40|Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação Aceder ao site de TI será apresentada na página **Contactar TI** no Portal da Empresa.

## <a name="company-branding-customization"></a>Personalização da imagem corporativa da empresa
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.



|Nome do campo|Mais informações|
|-|-|
|**Cor do tema**|Selecione a cor do tema que pretende aplicar ao Portal da Empresa.|
|**Mostrar o logótipo da empresa**|Quando ativa esta opção, pode carregar o logótipo da sua empresa que pretende que seja apresentado no Portal da Empresa. Pode carregar dois logótipos: um que é apresentado quando o fundo do Portal da Empresa é branco e outro que é apresentado quando o fundo do Portal da Empresa utiliza a cor do tema que selecionou. Cada logótipo tem de ser um tipo de ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 100 pixéis e ter um tamanho até 750 KB.<br>Também pode mostrar o nome da empresa que introduziu junto do logótipo carregado.|

Depois de guardar as alterações, pode escolher **Pré-visualizar as definições no Portal Web do Intune** para ver qual será o aspeto das configurações.

