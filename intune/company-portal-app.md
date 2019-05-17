---
title: Como configurar a aplicação do Portal da Empresa
titleSuffix: Microsoft Intune
description: Saiba como pode aplicar a imagem corporativa específica da empresa à aplicação Portal da Empresa do Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33f24a3d7b30973855bb303bb97bf703cd4dc5fa
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59895418"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Como configurar a aplicação Portal da Empresa do Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O portal da empresa do Microsoft Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.        

> [!Tip]        
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa. Tenha em atenção que os utilizadores têm de ter uma licença do Intune atribuída para poderem aceder ao site do Portal da Empresa.

A personalização do Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para tal, no portal do Intune, selecione **Aplicações cliente** > **Marca e personalização** e, em seguida, configure as definições necessárias. 

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
Introduza as informações de suporte da sua empresa para que o colaborador tenha um contacto para questões relacionadas com o Intune.          

|Nome do campo|Comprimento máximo|Mais informações|
|---|---|---|
|**Nome do contacto** | 40 | Este nome é apresentado na página **Contactar TI**. |
|**Número de telefone** | 20 | Este número de contacto é apresentado na página **Contactar TI** para permitir que os colaboradores o contactem para obter suporte. |
|**Endereço de e-mail**| 40 | Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato `alias@domainname.com`. |
|**Nome do site**| 40 | Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação Aceder ao site de TI será apresentada na página **Contactar TI** no Portal da Empresa. |
|**URL do Site**| 150 | Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato `https://www.contoso.com`. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa. |
| **Informações adicionais**| 120 | Apresentado na página **Contactar TI**. |


## <a name="company-identity-branding-customization"></a>Personalização da imagem corporativa da identidade da empresa      
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.     

### <a name="theme-color-and-logo-in-the-company-portal"></a>Logótipo e cor do tema no Portal da Empresa
Aplique a cor do tema ao Portal da Empresa. Selecione uma cor padrão ou introduza um código hexadecimal de seis dígitos para obter uma cor personalizada.

|Nome do campo|Mais informações|
|---|---|
|**Selecionar uma cor padrão ou introduzir um código hexadecimal de seis dígitos**| Escolha **Padrão** para selecionar visualmente uma cor. Escolha **Personalizada** para selecionar uma cor específica com base num valor de código hexadecimal.|
|**Escolher a cor do tema**| Selecione a cor do tema que pretende aplicar ao Portal da Empresa. Pode escolher uma cor padrão ou introduzir um código hexadecimal específico. |
|**Apresentar**| Selecione se pretende apresentar o **Logótipo e o nome da empresa**, **Apenas o logótipo da empresa** ou **Apenas o nome da empresa**. |
|**Carregar o logótipo da empresa**|Pode carregar o logótipo da empresa para mostrar no Portal da Empresa. Tenha em atenção que a cor do texto será automaticamente escolhida para proporcionar o maior nível de contraste. Para obter o melhor aspeto, carregue um logótipo com um fundo transparente.<p><ul><li>Tamanho máximo da imagem: 400 px x 400 px</li><li>Tamanho máximo do ficheiro: 750 KB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

Depois de carregar o logótipo, a área de pré-visualização mostrará o logótipo com a cor do tema. Se optar por apresentar o nome da sua empresa, este será mostrado em preto ou branco no Portal da Empresa e será automaticamente escolhido para proporcionar o maior nível de contraste com base na cor do seu tema. A área de pré-visualização no ecrã não apresentará o nome da sua empresa. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logótipo para utilizar em fundos brancos ou claros
Escolha o logótipo que ficará melhor em fundos brancos ou claros.

|Nome do campo|Mais informações|
|---|---|
|**Carregar o logótipo**| Esta opção está disponível se tiver optado por mostrar o logótipo da empresa. Para obter o melhor aspeto, carregue um logótipo com um fundo transparente.<p><ul><li>Tamanho máximo da imagem: 400 px x 400 px</li><li>Tamanho máximo do ficheiro: 750 KB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Imagem de marca do Portal da Empresa

Apresente uma imagem de marca que reflita a marca da sua empresa. Depois de guardar as alterações, pode optar por **Pré-visualizar as definições** no Portal Web do Intune na parte superior do painel para ver qual será o aspeto das configurações. Tenha em atenção que só poderá pré-visualizar a imagem de marca num dispositivo iOS e não no Portal Web do Intune. 

|Nome do campo|Mais informações|
|---|---|
|**Carregar a imagem de marca**| Esta opção permite-lhe apresentar uma imagem de marca. No Portal da Empresa do iOS, é apresentada como uma imagem de fundo na página de perfil do utilizador.<p><ul><li>Largura recomendada da imagem: menos de 1125 px, mas não menos de 640 px</li><li>Tamanho máximo da imagem: 1,3 MB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

A imagem de marca correta pode melhorar a confiança do utilizador no Portal da Empresa ao apresentar uma imagem sólida da marca da sua empresa. Aqui estão algumas sugestões que poderá considerar para comprar, escolher e otimizar a imagem do Portal da Empresa. 

- Entre em contacto com o Departamento de Marketing ou de Artes Gráficas. Estes departamentos podem já ter um conjunto de imagens de marca aprovado. Também poderão ajudá-lo a otimizar as imagens conforme necessário. 

- Considere tanto a composição horizontal como a vertical. A imagem deve ter um fundo suficiente, de forma a envolver o ponto focal. A imagem pode ser recortada de forma diferente com base na orientação, no tamanho e na plataforma do dispositivo. 

- Evite utilizar uma imagem de stock genérica. A imagem deve refletir a marca da sua empresa e ser familiar aos utilizadores. Se não tiver uma, é melhor não utilizar uma imagem genérica que não faça sentido para o seu utilizador. 

- Remova os metadados desnecessários. O ficheiro de imagem pode vir com metadados, tais como o perfil da câmara, a geolocalização, o título, a legenda, etc. Utilize uma ferramenta de otimização de imagens para retirar estas informações para manter a qualidade e cumprir o limite de tamanho do ficheiro. 

Depois de uma imagem de marca ter sido adicionada ou alterada no Intune, o utilizador final poderá não ver a alteração nos dispositivos iOS, até que o Portal da Empresa reconheça a alteração no arranque e tenha sido reiniciado para apresentar a imagem de marca. 

### <a name="brand-image-examples"></a>Exemplos de imagem de marca

A imagem seguinte mostra um exemplo de imagem corporativa no iPad:

![Captura de ecrã de exemplo de imagem corporativa no iPhone](media/company-portal-app/company-portal-app-03.png)

A imagem seguinte mostra um exemplo de imagem corporativa no iPhone:

![Captura de ecrã de exemplo de imagem corporativa no iPad](media/company-portal-app/company-portal-app-02.png)

## <a name="windows-company-portal-keyboard-shortcuts"></a>Atalhos de teclado do Portal da Empresa do Windows

Os utilizadores finais podem ativar ações de navegação, de aplicação e de dispositivo no Portal da Empresa do Windows com atalhos de teclado.

Os atalhos de teclado seguintes estão disponíveis na aplicação Portal da Empresa do Windows.

| Área | Descrição | Atalho de teclado |
|:------------------:|:--------------:|:-----------------:|
| Menu de navegação | Navegação | Alt+M |
|  | Casa | Alt+H |
|  | Todas as aplicações | Alt+A |
|  | Aplicações instaladas | Alt+I |
|  | Enviar feedback | Alt+F |
|  | O meu perfil | Alt+U |
|  | Definições | Alt+T |
| Base – Mosaico Dispositivo | Mudar o nome | F2 |
|  | Remove | Ctrl+D ou Delete |
|  | Verificar o acesso | Ctrl+M ou F9 |
| Detalhes do dispositivo | Mudar o nome | F2 |
|  | Remove | Ctrl+D ou Delete |
|  | Verificar o acesso | Ctrl+M ou F9 |
| Detalhes da aplicação | Instalar | Ctrl+I |

Os utilizadores finais também poderão ver os atalhos disponíveis na aplicação Portal da Empresa no Windows.

![Captura de ecrã dos atalhos disponíveis no Portal da Empresa do Windows](media/company-portal-app/company-portal-app-01.png)

## <a name="next-steps"></a>Próximos passos

- [Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](store-apps-company-portal-app.md)
