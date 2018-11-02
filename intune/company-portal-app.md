---
title: Como configurar a aplicação do Portal da Empresa
titleSuffix: Microsoft Intune
description: Saiba como pode aplicar a imagem corporativa específica da empresa à aplicação Portal da Empresa do Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2defc433ef39562750c4579f302a9c5367c6464a
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828249"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Como configurar a aplicação Portal da Empresa do Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O portal da empresa do Microsoft Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.        

> [!Tip]        
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa.       

Personalizar o Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para o fazer, na carga de trabalho **Aplicações do cliente**, escolha **Configuração** > **Imagem Corporativa do Portal da Empresa** e, em seguida, configure as definições necessárias.  

> [!Note]       
> Se estiver a utilizar o Azure Government, os registos de aplicações estão disponíveis para o utilizador final decidir como pretende partilhar ao iniciar o processo para obter ajuda com um problema. No entanto, se não estiver a utilizar o Azure Government, o Portal da Empresa para Windows 10 irá enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o processo para obter ajuda com um problema. O envio dos registos de aplicações para a Microsoft irá facilitar a resolução dos problemas. 

## <a name="company-information-and-privacy-statement"></a>Informações e declaração de privacidade da empresa        
O nome da empresa é apresentado como o título do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

Os campos marcados com um asterisco (*) são obrigatórios.       


| Nome do campo | Comprimento máximo | Mais informações |
|---|---|---|
|**Nome da empresa**| 40 | Este nome é apresentado como o título do Portal da Empresa e é apresentado como texto em toda a experiência de utilizador do Intune. |
| **URL de declaração de privacidade** |     79     | Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato `<https://www.contoso.com>`. |

## <a name="support-information"></a>Informações de suporte      
Introduza as informações de suporte da sua empresa para fornecer ao seu colaborador um contacto para perguntas relacionadas com o Intune.       

|Nome do campo|Comprimento máximo|Mais informações|
|---|---|---|
|**Nome do contacto** | 40 | Este nome é apresentado na página **Contactar TI**. |
|**Número de telefone** | 20 | Este número de contacto é apresentado na página **Contactar TI** para permitir que os colaboradores o contactem para obter suporte. |
|**Endereço de e-mail**| 40 | Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato `alias@domainname.com`. |
|**Nome do site**| 40 | Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação Aceder ao site de TI será apresentada na página **Contactar TI** no Portal da Empresa. |
|**URL do Site**| 150 | Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato `https://www.contoso.com`. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa. |
| **Informações adicionais**| 120 | Apresentado na página **Contactar TI**. |


## <a name="company-branding-customization"></a>Personalização da imagem corporativa da empresa       
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.     

### <a name="theme-color"></a>Cor do tema
Aplique a cor do tema ao Portal da Empresa. Selecione uma cor padrão ou introduza um código hexadecimal de seis dígitos para obter uma cor personalizada.

|Nome do campo|Mais informações|
|---|---|
|**Tipo de cor**| Selecione a cor do tema que pretende aplicar ao Portal da Empresa. Pode escolher uma cor padrão ou introduzir um código hexadecimal específico. |
|**Escolher código** ou **Código de cor hexadecimal**| Selecione a cor do tema que pretende aplicar ao Portal da Empresa. Pode escolher uma cor padrão ou introduzir um código hexadecimal específico. Estas opções são fornecidas com base no **Tipo de cor** que seleciona.  |

### <a name="company-logo"></a>Logótipo da empresa
Carregue o logótipo da empresa para o tornar visível em toda a experiência de utilizador do Intune.

|Nome do campo|Mais informações|
|---|---|
|**Mostrar o logótipo da empresa**|Quando ativa esta opção, pode carregar o logótipo da sua empresa que pretende que seja apresentado no Portal da Empresa. Pode carregar dois logótipos: um que é apresentado quando o fundo do Portal da Empresa é branco e outro que é apresentado quando o fundo do Portal da Empresa utiliza a cor do tema que selecionou. |
|**Carregar um logótipo para utilizar em fundos de temas com cor**| Esta opção está disponível se tiver optado por mostrar o logótipo da empresa. O logótipo tem de ser um ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 400 pixéis e ter um tamanho igual ou inferior a 750 KB. |
|**Carregar logótipo para utilizar em fundos claros**| Esta opção está disponível se tiver optado por mostrar o logótipo da empresa. O logótipo tem de ser um ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 400 pixéis e ter um tamanho igual ou inferior a 750 KB. |
|**Mostrar o nome da empresa ao lado do logótipo**| Selecione esta opção para mostrar o nome da empresa que introduziu junto ao logótipo carregado. |

Depois de guardar as alterações, pode escolher **Pré-visualizar as suas definições no Portal Web do Intune** na parte superior do painel para ver qual será o aspeto das configurações.
