---
title: Como configurar a aplicação do Portal da Empresa
titleSuffix: Microsoft Intune
description: Saiba como você pode aplicar a identidade visual específica da empresa ao aplicativo Portal da Empresa do Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 7a4d6db4f61dea1b073ccce7c4c3f727a91402c1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563644"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Como configurar a aplicação Portal da Empresa do Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O portal da empresa do Microsoft Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI. Além disso, o aplicativo portal da empresa permite que o usuário acesse os recursos da empresa com segurança. O aplicativo do portal da empresa fornece várias páginas diferentes, como página inicial, aplicativos, detalhes do aplicativo, dispositivos e detalhes do dispositivo. Para localizar rapidamente os aplicativos no Portal da Empresa, você pode filtrar os aplicativos na página de aplicativos.

> [!IMPORTANT]
> Para dar suporte ao FCM (firebase Cloud Messaging) do Google, você deve atualizar seu aplicativo Android Portal da Empresa para a versão mais recente.  

> [!Tip]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa. Tenha em atenção que os utilizadores têm de ter uma licença do Intune atribuída para poderem aceder ao site do Portal da Empresa.

A personalização do Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para fazer isso, no portal do Intune, selecione **aplicativos** > **identidade visual e personalização**e, em seguida, defina as configurações necessárias.

Quando um usuário estiver instalando um aplicativo iOS do Portal da Empresa ele receberá um prompt. Isso ocorre quando o aplicativo iOS está vinculado à loja de aplicativos, vinculado a um VPP (programa de compra por volume) ou vinculado a um aplicativo de linha de negócios (LOB). O prompt permite que os usuários aceitem a ação ou permitam o gerenciamento do aplicativo. O prompt exibirá o nome da empresa ou, quando o nome da sua empresa estiver indisponível, **portal da empresa** será exibido. 

> [!Note]
> Se estiver a utilizar o Azure Government, os registos de aplicações estão disponíveis para o utilizador final decidir como pretende partilhar ao iniciar o processo para obter ajuda com um problema. No entanto, se não estiver a utilizar o Azure Government, o Portal da Empresa para Windows 10 irá enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o processo para obter ajuda com um problema. O envio dos registos de aplicações para a Microsoft irá facilitar a resolução dos problemas. 

## <a name="company-information-and-privacy-statement"></a>Informações e declaração de privacidade da empresa
O nome da empresa é apresentado como o título do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

| Nome do campo | Comprimento máximo | Mais informações |
|---|---|---|
|**Nome da empresa**| 40 | Este nome é apresentado como o título do Portal da Empresa e é apresentado como texto em toda a experiência de utilizador do Intune. |
| **URL de declaração de privacidade** |     79     | Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato `<https://www.contoso.com>`. |

> [!NOTE]
> Consistente com a Microsoft e a política da Apple, não vendemos nenhum dado coletado por nosso serviço a terceiros por qualquer motivo.

## <a name="support-information"></a>Informações de suporte
Introduza as informações de suporte da sua empresa para que o colaborador tenha um contacto para questões relacionadas com o Intune.

|Nome do campo|Comprimento máximo|Mais informações|
|---|---|---|
|**Nome do contacto** | 40 | Esse nome é exibido na página **ajuda e suporte** . |
|**Número de telefone** | 20 | Este número de contato é exibido na página **ajuda e suporte** para permitir que os funcionários entrem em contato com você para obter suporte. |
|**Endereço de e-mail**| 40 | Este endereço de contato é exibido na página **ajuda e suporte** . Tem de inserir um endereço de e-mail válido no formato `alias@domainname.com`. |
|**Nome do site**| 40 | Este é o nome amigável apresentado no URL do site de suporte. Se você especificar uma URL do site de suporte e nenhum nome amigável, vá para o site de ti é exibido na página **ajuda e suporte** no portal da empresa. |
|**URL do Site**| 150 | Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato `https://www.contoso.com`. Se você não especificar uma URL, nada será exibido para o site de suporte na página **ajuda e suporte** na portal da empresa. |
| **Informações adicionais**| 120 | Exibido na página **ajuda e suporte** . |


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

Apresente uma imagem de marca que reflita a marca da sua empresa. Depois de salvar as alterações, você pode escolher **Visualizar suas configurações** no portal da Web do Intune na parte superior do painel para ver como as configurações serão exibidas. Tenha em atenção que só poderá pré-visualizar a imagem de marca num dispositivo iOS e não no Portal Web do Intune. 

|Nome do campo|Mais informações|
|---|---|
|**Carregar a imagem de marca**| Esta opção permite-lhe apresentar uma imagem de marca. No Portal da Empresa do iOS, é apresentada como uma imagem de fundo na página de perfil do utilizador.<p><ul><li>Largura de imagem recomendada: maior que 1125px (necessário para ser pelo menos 650 px)</li><li>Tamanho máximo da imagem: 1,3 MB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

A imagem de marca correta pode melhorar a confiança do utilizador no Portal da Empresa ao apresentar uma imagem sólida da marca da sua empresa. Aqui estão algumas sugestões que poderá considerar para comprar, escolher e otimizar a imagem do Portal da Empresa. 

- Entre em contacto com o Departamento de Marketing ou de Artes Gráficas. Estes departamentos podem já ter um conjunto de imagens de marca aprovado. Também poderão ajudá-lo a otimizar as imagens conforme necessário. 

- Considere tanto a composição horizontal como a vertical. A imagem deve ter um fundo suficiente, de forma a envolver o ponto focal. A imagem pode ser recortada de forma diferente com base na orientação, no tamanho e na plataforma do dispositivo. 

- Evite utilizar uma imagem de stock genérica. A imagem deve refletir a marca da sua empresa e ser familiar aos utilizadores. Se não tiver uma, é melhor não utilizar uma imagem genérica que não faça sentido para o seu utilizador. 

- Remova os metadados desnecessários. O ficheiro de imagem pode vir com metadados, tais como o perfil da câmara, a geolocalização, o título, a legenda, etc. Utilize uma ferramenta de otimização de imagens para retirar estas informações para manter a qualidade e cumprir o limite de tamanho do ficheiro. 

Depois de uma imagem de marca ter sido adicionada ou alterada no Intune, o utilizador final poderá não ver a alteração nos dispositivos iOS, até que o Portal da Empresa reconheça a alteração no arranque e tenha sido reiniciado para apresentar a imagem de marca. 

### <a name="brand-image-examples"></a>Exemplos de imagem de marca

A imagem seguinte mostra um exemplo de imagem corporativa no iPad:

![Captura de ecrã de exemplo de imagem corporativa no iPhone](./media/company-portal-app/company-portal-app-03.png)

A imagem seguinte mostra um exemplo de imagem corporativa no iPhone:

![Captura de ecrã de exemplo de imagem corporativa no iPad](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Personalização da política de privacidade

Você pode personalizar a declaração de privacidade que aparece para sua organização em dispositivos iOS gerenciados. Esta mensagem lista os itens que sua organização não pode ver ou fazer em dispositivos iOS gerenciados.

Em **portal da empresa personalização** > o **Gerenciamento de dispositivos e a mensagem de privacidade**, você pode:

- Aceite o **padrão** para usar a lista, conforme mostrado, ou
- Escolha **personalizado** para personalizar a lista de itens que sua organização não pode ver ou fazer em dispositivos IOS gerenciados. Você pode usar a [redução](https://daringfireball.net/projects/markdown/) para adicionar marcadores, negrito, itálico e links.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Portal da Empresa credenciais derivadas para dispositivos iOS
O Intune dá suporte às credenciais derivadas de PIV (verificação de identidade pessoal) e de cartão de acesso comum (CAC) em parceria com os provedores de credenciais DISA purebred, Entrust Datacard e intercedam. Os usuários finais passarão por etapas adicionais após o registro de seu dispositivo iOS para verificar sua identidade no aplicativo Portal da Empresa. As credenciais derivadas serão habilitadas para os usuários primeiro Configurando um provedor de credenciais para seu locatário e, em seguida, direcionando um perfil que usa credenciais derivadas para usuários ou dispositivos.

> [!NOTE]
> O usuário verá instruções sobre as credenciais derivadas com base no link que você especificou por meio do Intune.

Para obter mais informações sobre credenciais derivadas para dispositivos iOS, consulte [usar credenciais derivadas no Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Modo escuro para iOS Portal da Empresa

O modo escuro está disponível para o Portal da Empresa do iOS. Os usuários podem baixar aplicativos da empresa, gerenciar seus dispositivos e obter suporte de ti no esquema de cores de sua escolha com base nas configurações do dispositivo. O Portal da Empresa do iOS corresponderá automaticamente às configurações do dispositivo do usuário final para o modo escuro ou leve. 

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

## <a name="user-self-service-device-actions-from-the-company-portal"></a>Ações de dispositivo de autoatendimento do usuário da Portal da Empresa

Os usuários podem executar ações em seus dispositivos locais ou remotos por meio do aplicativo Portal da Empresa ou site. As ações que um usuário pode executar variam de acordo com a plataforma e a configuração do dispositivo. Em todos os casos, as ações de dispositivo remoto só podem ser executadas pelo usuário primário do dispositivo.
- **Desativar** – remove o dispositivo do gerenciamento do Intune. No aplicativo do portal da empresa e no site, isso é mostrado como **remover**.
- **Apagar** – esta ação inicia uma redefinição de dispositivo. No site do portal da empresa, isso é mostrado como **redefinição**ou **redefinição de fábrica** no aplicativo portal da empresa do Ios.
- **Renomear** – essa ação altera o nome do dispositivo que o usuário pode ver no portal da empresa. Ele não altera o nome do dispositivo local, apenas a listagem no Portal da Empresa.
- **Sincronização** – essa ação inicia um check-in de dispositivo com o serviço do Intune. Isso mostra como **verificar o status** na portal da empresa.
- **Bloqueio remoto** – bloqueia o dispositivo, exigindo um PIN para desbloqueá-lo.
- **Redefinir senha** – esta ação é usada para redefinir a senha do dispositivo. Em dispositivos iOS, a senha será removida e o usuário final será solicitado a inserir um novo código em configurações. Em dispositivos Android com suporte, uma nova senha é gerada pelo Intune e exibida temporariamente no Portal da Empresa.
- **Recuperação de chave** – essa ação é usada para recuperar uma chave de recuperação pessoal para dispositivos MacOS criptografados do site Portal da empresa. 

### <a name="self-service-actions"></a>Ações de autoatendimento

Algumas plataformas e configurações não permitem ações de dispositivo de autoatendimento. Esta tabela abaixo fornece mais detalhes sobre as ações de autoatendimento:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Extinguir | Disponível<sup>(1)</sup> | Disponível | Disponível | Disponível<sup>(7)</sup> |
| Eliminação | Disponível | Disponível<sup>(5)</sup> | ND | Disponível<sup>(7)</sup> |
| Renomear<sup>(4)</sup> | Disponível | Disponível | Disponível | Disponível |
| Sincronizar | Disponível | Disponível | Disponível | Disponível |
| Bloqueio Remoto | Somente Windows Phone | Disponível | Disponível | Disponível |
| Repor Código de Acesso | Somente Windows Phone | Disponível<sup>(8)</sup> | ND | Disponível<sup>(6)</sup> |
| Recuperação de Chaves | ND | ND | Disponível<sup>(2)</sup> | ND |

<sup>(1)</sup> a **desativação** é sempre bloqueada em dispositivos Windows ingressados no Azure AD.<br>
<sup>(2)</sup> a **recuperação de chave** para MacOS só está disponível por meio do portal da Web.<br>
<sup>(3)</sup> todas as ações remotas serão desabilitadas se você usar um registro do Gerenciador de registro de dispositivo.<br>
<sup>(4)</sup> **renomear** apenas altera o nome do dispositivo no aplicativo portal da empresa ou no portal da Web, não no dispositivo.<br>
<sup>(5)</sup> o **apagamento** não está disponível em dispositivos IOS registrados pelo usuário.<br>
<sup>(6)</sup> não há suporte para **Redefinir senha** em algumas configurações corporativas do Android e Android. Para obter mais informações, consulte [redefinir ou remover uma senha de dispositivo no Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> a **desativação** e o **apagamento** não estão disponíveis nos cenários do proprietário do dispositivo Android Enterprise (Cobo, COSU).<br> 
<sup>(8)</sup> não há suporte para **Redefinir senha** em dispositivos IOS registrados pelo usuário.

## <a name="next-steps"></a>Próximos passos

- [Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](company-portal-app.md)
