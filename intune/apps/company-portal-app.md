---
title: Como configurar a aplicação do Portal da Empresa
titleSuffix: Microsoft Intune
description: Saiba como pode aplicar a marca específica da empresa à aplicação Intune Company Portal.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c938aba7fde84536af2452f13f6ed030fa1d823
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576428"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Como configurar a aplicação Portal da Empresa do Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O portal da empresa do Microsoft Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI. Além disso, a aplicação portal da empresa permite ao utilizador aceder de forma segura aos recursos da empresa. A aplicação portal da empresa fornece várias páginas diferentes, tais como Detalhes home, Apps, App, Dispositivos e Dispositivos. Para encontrar rapidamente aplicações dentro do Portal da Empresa, pode filtrar as aplicações na página apps.

> [!IMPORTANT]
> Para suportar a Firebase Cloud Messaging (FCM) da Google, tem de atualizar a sua aplicação Portal da Empresa Android para a versão mais recente.  

> [!Tip]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa. Tenha em atenção que os utilizadores têm de ter uma licença do Intune atribuída para poderem aceder ao site do Portal da Empresa.

A personalização do Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para isso, navegue para o centro de [administração do Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Tenant Administration** > Branding **e personalização,** e, em seguida, configure as definições necessárias.

Quando um utilizador estiver a instalar uma aplicação iOS/iPadOS a partir do Portal da Empresa, receberá uma solicitação. Isto ocorre quando a aplicação iOS/iPadOS está ligada à loja de aplicações, ligada a um programa de compra de volume (VPP), ou ligada a uma aplicação de linha de negócios (LOB). O pedido permite que os utilizadores aceitem a ação ou permitam a gestão da app. O pedido mostrará o nome da sua empresa, ou quando o nome da sua empresa não estiver disponível, o **Portal da Empresa** será exibido. 

> [!Note]
> Se estiver a utilizar o Azure Government, os registos de aplicações estão disponíveis para o utilizador final decidir como pretende partilhar ao iniciar o processo para obter ajuda com um problema. No entanto, se não estiver a utilizar o Azure Government, o Portal da Empresa para Windows 10 irá enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o processo para obter ajuda com um problema. O envio dos registos de aplicações para a Microsoft irá facilitar a resolução dos problemas. 

## <a name="company-information-and-privacy-statement"></a>Informações e declaração de privacidade da empresa
O nome da empresa é apresentado como o título do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

| Nome do campo | Comprimento máximo | Mais informações |
|---|---|---|
|**Nome da empresa**| 40 | Este nome é apresentado como o título do Portal da Empresa e é apresentado como texto em toda a experiência de utilizador do Intune. |
| **URL de declaração de privacidade** |     79     | Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato `<https://www.contoso.com>`. |

> [!NOTE]
> De acordo com a política da Microsoft e da Apple, não vendemos quaisquer dados recolhidos pelo nosso serviço a terceiros por qualquer motivo.

## <a name="support-information"></a>Informações de suporte
Introduza as informações de suporte da sua empresa para que o colaborador tenha um contacto para questões relacionadas com o Intune.

|Nome do campo|Comprimento máximo|Mais informações|
|---|---|---|
|**Nome do contacto** | 40 | Este nome é apresentado na página **de Ajuda e Suporte.** |
|**Número de telefone** | 20 | Este número de contacto é apresentado na página **de Ajuda e Suporte** para permitir que os colaboradores o contactem para obter apoio. |
|**Endereço de e-mail**| 40 | Este endereço de contacto é apresentado na página **de Ajuda e Suporte.** Tem de inserir um endereço de e-mail válido no formato `alias@domainname.com`. |
|**Nome do site**| 40 | Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte e nenhum nome amigável, então o site de TI é exibido na página **de Ajuda e Suporte** no Portal da Empresa. |
|**URL do Site**| 150 | Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato `https://www.contoso.com`. Se não especificar um URL, nada é apresentado para o site de suporte na página **de Ajuda e Suporte** no Portal da Empresa. |
| **Informações adicionais**| 120 | Apresentado na página **de Ajuda e Suporte.** |


## <a name="company-identity-branding-customization"></a>Personalização da imagem corporativa da identidade da empresa
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Logótipo e cor do tema no Portal da Empresa
Aplique a cor do tema ao Portal da Empresa. Selecione uma cor padrão ou introduza um código hexadecimal de seis dígitos para obter uma cor personalizada.

|Nome do campo|Mais informações|
|---|---|
|**Selecionar uma cor padrão ou introduzir um código hexadecimal de seis dígitos**| Escolha **Padrão** para selecionar visualmente uma cor. Escolha **Personalizada** para selecionar uma cor específica com base num valor de código hexadecimal.|
|**Escolher a cor do tema**| Selecione a cor do tema que pretende aplicar ao Portal da Empresa. Pode escolher uma cor padrão ou introduzir um código hexadecimal específico. |
|**Apresentar**| Selecione se pretende apresentar o **Logótipo e o nome da empresa**, **Apenas o logótipo da empresa** ou **Apenas o nome da empresa**. |
|**Carregar o logótipo da empresa**|Pode carregar o logótipo da empresa para mostrar no Portal da Empresa. Tenha em atenção que a cor do texto será automaticamente escolhida para proporcionar o maior nível de contraste. Para obter o melhor aspeto, carregue um logótipo com um fundo transparente.<p><ul><li>Tamanho máximo da imagem: 400 x 400 px</li><li>Tamanho máximo do ficheiro: 750 KB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

Depois de carregar o logótipo, a área de pré-visualização mostrará o logótipo com a cor do tema. Se optar por apresentar o nome da sua empresa, este será mostrado em preto ou branco no Portal da Empresa e será automaticamente escolhido para proporcionar o maior nível de contraste com base na cor do seu tema. A área de pré-visualização no ecrã não apresentará o nome da sua empresa. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logótipo para utilizar em fundos brancos ou claros
Escolha o logótipo que ficará melhor em fundos brancos ou claros.

|Nome do campo|Mais informações|
|---|---|
|**Carregar o logótipo**| Esta opção está disponível se tiver optado por mostrar o logótipo da empresa. Para obter o melhor aspeto, carregue um logótipo com um fundo transparente.<p><ul><li>Tamanho máximo da imagem: 400 x 400 px</li><li>Tamanho máximo do ficheiro: 750 KB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Imagem de marca do Portal da Empresa

Apresente uma imagem de marca que reflita a marca da sua empresa. Depois de guardar as suas alterações, pode escolher **pré-visualizar** as suas definições no Portal Web Intune na parte superior do painel para ver como serão as suas configurações. Note que só será possível pré-visualizar a imagem da marca num dispositivo iOS/iPadOS e não no Intune Web Portal. 

|Nome do campo|Mais informações|
|---|---|
|**Carregar a imagem de marca**| Esta opção permite-lhe apresentar uma imagem de marca. No portal da empresa iOS/iPadOS, mostra como uma imagem de fundo na página de perfil do utilizador.<p><ul><li>Largura de imagem recomendada: Superior a 1125px (necessário para ser pelo menos 650 px)</li><li>Tamanho máximo da imagem: 1,3 MB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

A imagem de marca correta pode melhorar a confiança do utilizador no Portal da Empresa ao apresentar uma imagem sólida da marca da sua empresa. Aqui estão algumas sugestões que poderá considerar para comprar, escolher e otimizar a imagem do Portal da Empresa. 

- Entre em contacto com o Departamento de Marketing ou de Artes Gráficas. Estes departamentos podem já ter um conjunto de imagens de marca aprovado. Também poderão ajudá-lo a otimizar as imagens conforme necessário. 

- Considere tanto a composição horizontal como a vertical. A imagem deve ter um fundo suficiente, de forma a envolver o ponto focal. A imagem pode ser recortada de forma diferente com base na orientação, no tamanho e na plataforma do dispositivo. 

- Evite utilizar uma imagem de stock genérica. A imagem deve refletir a marca da sua empresa e ser familiar aos utilizadores. Se não tiver uma, é melhor não utilizar uma imagem genérica que não faça sentido para o seu utilizador. 

- Remova os metadados desnecessários. O ficheiro de imagem pode vir com metadados, tais como o perfil da câmara, a geolocalização, o título, a legenda, etc. Utilize uma ferramenta de otimização de imagens para retirar estas informações para manter a qualidade e cumprir o limite de tamanho do ficheiro. 

Depois de uma imagem da marca ser adicionada ou alterada em Intune, o utilizador final pode não ver a alteração nos dispositivos iOS/iPadOS até que o Portal da Empresa reconheça a mudança no arranque e depois tenha sido reiniciado para exibir a imagem da marca. 

### <a name="brand-image-examples"></a>Exemplos de imagem de marca

A imagem seguinte mostra um exemplo de imagem corporativa no iPad:

![Captura de ecrã de exemplo de imagem corporativa no iPhone](./media/company-portal-app/company-portal-app-03.png)

A imagem seguinte mostra um exemplo de imagem corporativa no iPhone:

![Captura de ecrã de exemplo de imagem corporativa no iPad](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Personalização da declaração de privacidade

Pode personalizar a declaração de privacidade que aparece para a sua organização em dispositivos geridos iOS/iPadOS. Esta mensagem lista os itens que a sua organização não consegue ver ou fazer em dispositivos geridos iOS/iPadOS.

Sob **a personalização** do Portal da Empresa > **gestão de dispositivos e mensagem**de privacidade, pode:

- Aceitar o **Padrão** para utilizar a lista como mostrado, ou
- Escolha o **Custom** para personalizar a lista de itens que a sua organização não consegue ver ou fazer em dispositivos geridos iOS/iPadOS. Pode usar [o markdown](https://daringfireball.net/projects/markdown/) para adicionar balas, arrojados, itálicos e ligações.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Credenciais derivadas do Portal da Empresa para dispositivos iOS
Intune apoia a Verificação de Identidade Pessoal (PIV) e o Cartão de Acesso Comum (CAC) Credenciais derivadas em parceria com fornecedores credenciais DISA Purebred, Entrust Datacard e Intercede. Os utilizadores finais passarão por etapas adicionais após a inscrição do seu dispositivo iOS/iPadOS para verificar a sua identidade na aplicação Portal da Empresa. As Credenciais derivadas serão ativadas para os utilizadores, criando primeiro um fornecedor de credenciais para o seu inquilino, direcionando depois um perfil que utiliza credenciais derivadas para utilizadores ou dispositivos.

> [!NOTE]
> O utilizador verá instruções sobre credenciais derivadas com base no link que especificou via Intune.

Para obter mais informações sobre credenciais derivadas para dispositivos iOS/iPadOS, consulte [Utilize credenciais derivadas no Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Modo Escuro para portal da empresa iOS

O Modo Escuro está disponível para o portal da empresa iOS. Os utilizadores podem descarregar aplicações da empresa, gerir os seus dispositivos e obter suporte de TI no esquema de cores da sua escolha com base nas configurações do dispositivo. O portal da empresa iOS irá corresponder automaticamente às definições do dispositivo do utilizador final para o modo escuro ou leve. 

## <a name="windows-company-portal-keyboard-shortcuts"></a>Atalhos de teclado do Portal da Empresa do Windows

Os utilizadores finais podem ativar ações de navegação, de aplicação e de dispositivo no Portal da Empresa do Windows com atalhos de teclado.

Os atalhos de teclado seguintes estão disponíveis na aplicação Portal da Empresa do Windows.

| Área | Description | Atalho de teclado |
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
| Dispositivos | Disponível | Ctrl+D |

Os utilizadores finais também poderão ver os atalhos disponíveis na aplicação Portal da Empresa no Windows.

![Captura de ecrã dos atalhos disponíveis no Portal da Empresa do Windows](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>Ações de dispositivo de self-service do utilizador a partir do Portal da Empresa

Os utilizadores podem realizar ações nos seus dispositivos locais ou remotos através da aplicação ou website do Portal da Empresa. As ações que um utilizador pode executar variam em função da plataforma e configuração do dispositivo. Em todos os casos, as ações do dispositivo remoto só podem ser executadas pelo Utilizador Primário do dispositivo.
- **Aposentador** – Remove o dispositivo da Intune Management. Na aplicação e website do portal da empresa, isto mostra como **Remover**.
- **Limpeza** – Esta ação inicia um reset do dispositivo. No portal da empresa este é mostrado como **Reset**, ou **Reset de Fábrica** na Aplicação portal da empresa iOS.
- **Renomear** – Esta ação altera o nome do dispositivo que o utilizador pode ver no Portal da Empresa. Não altera o nome do dispositivo local, apenas a listagem no Portal da Empresa.
- **Sync** – Esta ação inicia um check-in do dispositivo com o serviço Intune. Isto mostra como **Check Status** no Portal da Empresa.
- **Bloqueio remoto** – Este bloqueia o dispositivo, exigindo um PIN para desbloqueá-lo.
- **Redefinir a código de acesso** – Esta ação é utilizada para redefinir a senha do dispositivo. Nos dispositivos iOS/iPadOS, a senha será removida e o utilizador final será obrigado a introduzir um novo código nas definições. Em dispositivos Android suportados, uma nova senha é gerada pela Intune e exibida temporariamente no Portal da Empresa.
- **Recuperação chave** – Esta ação é usada para recuperar uma chave de recuperação pessoal para dispositivos macOS encriptados a partir do website do Portal da Empresa. 

### <a name="self-service-actions"></a>Ações de Self Service

Algumas plataformas e configurações não permitem ações de dispositivos self-service. Este quadro abaixo fornece mais detalhes sobre as ações de self service:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Extinguir | Disponível<sup>(1)</sup> | Disponível | Disponível | Disponível<sup>(7)</sup> |
| Eliminação | Disponível | Disponível<sup>(5)</sup> | ND | Disponível<sup>(7)</sup> |
| Renome<sup>(4)</sup> | Disponível | Disponível | Disponível | Disponível |
| Sincronizar | Disponível | Disponível | Disponível | Disponível |
| Bloqueio Remoto | Apenas windows Phone | Disponível | Disponível | Disponível |
| Repor Código de Acesso | Apenas windows Phone | Disponível<sup>(8)</sup> | ND | Disponível<sup>(6)</sup> |
| Recuperação da chave | ND | ND | Disponível<sup>(2)</sup> | ND |

<sup>(1)</sup> **A reforma** está sempre bloqueada nos dispositivos Azure AD Joined Windows.<br>
<sup>(2)</sup> **A recuperação da chave** para o MacOS só está disponível através do Portal Web.<br>
<sup>(3)</sup> Todas as ações remotas são desativadas se utilizarem uma inscrição do Gestor de Inscrição do Dispositivo.<br>
<sup>(4)</sup> **O nome de novo** altera apenas o nome do dispositivo na aplicação portal da empresa ou no Portal web, não no dispositivo.<br>
<sup>(5)</sup> **A limpeza** não está disponível nos dispositivos iOS inscritos pelo utilizador.<br>
<sup>(6)</sup> **O Reset Passcode** não é suportado em algumas configurações do Android e Android Enterprise. Para mais informações, consulte [Reset ou remova uma senha do dispositivo no Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> **A reforma** e a **limpeza** não estão disponíveis nos cenários do Proprietário do Dispositivo Empresarial Android (COPE, COBO, COSU).<br> 
(8) O código de acesso de **reset** <sup>(8)</sup> não é suportado nos dispositivos iOS inscritos pelo utilizador.

## <a name="next-steps"></a>Próximos passos

- [Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](company-portal-app.md)
