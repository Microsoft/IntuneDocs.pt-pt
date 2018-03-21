---
title: "Como adicionar aplicações ao Microsoft Intune"
titlesuffix: 
description: "Saiba como adicionar aplicações ao Microsoft Intune para poder atribuir aplicações a utilizadores e dispositivos. O Intune suporta uma grande variedade de tipos de aplicações diferentes."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 407a332e170497dbb618a2915bba6b794c4a720f
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Como adicionar uma aplicação ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Microsoft Intune.

Os utilizadores de aplicações e dispositivos na sua empresa (força de trabalho da sua empresa) podem ter vários requisitos de aplicação. Antes de adicionar aplicações ao Intune e disponibilizá-las à sua força de trabalho, tem de avaliar e compreender algumas noções básicas sobre aplicações. Tem de compreender os diferentes tipos de aplicações disponíveis para o Intune. Terá de avaliar os requisitos de aplicação, tais como as plataformas e funcionalidades necessárias para a sua força de trabalho. Além disso, tem de determinar se irá utilizar o Intune para gerir os dispositivos (incluindo aplicações) ou se o Intune irá gerir as aplicações sem gerir os dispositivos. Tem de determinar quem é que na sua força de trabalho irá precisar de aplicações e funcionalidades diferentes. As informações fornecidas neste artigo irão ajudá-lo a começar.

## <a name="app-types-in-microsoft-intune"></a>Tipos de aplicações no Microsoft Intune

O Intune suporta uma grande variedade de tipos de aplicações diferentes. As opções disponíveis diferem para cada tipo de aplicação. O Intune permite-lhe adicionar e atribuir estes tipos de aplicação:

| **Tipos de Aplicações**                                     | **Instalação**                                                                  | **Atualizações**                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| Aplicações que estão na loja (aplicações da loja)          | O Intune instala a aplicação no dispositivo                                       | As atualizações das aplicações são automáticas     |
| Aplicações escritas internamente (linha de negócio)  | O Intune instala a aplicação no dispositivo (o ficheiro de instalação é fornecido por si)    | Tem de atualizar a aplicação       |
| Aplicações que estão incorporadas (aplicações incorporadas)    | O Intune instala a aplicação no dispositivo                                       | As atualizações das aplicações são automáticas     |
| Aplicações na Web (ligação Web)                | O Intune cria um atalho para a aplicação Web no ecrã principal do dispositivo          | As atualizações das aplicações são automáticas     |

### <a name="specific-app-type-details"></a>Detalhes específicos do tipo de aplicação
 
A tabela seguinte apresenta uma lista dos tipos de aplicação específicos e como pode adicioná-los a partir do painel **Adicionar aplicação** no Microsoft Intune:

| **Tipo de Aplicação Específico**                         | **Tipo Geral**             | **Procedimentos Específicos da Aplicação**                                                                                                                                                 |
|---------------------------------------------|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aplicações da loja Android                        | Aplicação da loja                  | Selecione **Android** como o **tipo de aplicação** e introduza o URL da loja Google Play para a aplicação.                                                                                       |
| Aplicações da loja iOS                            | Aplicação da loja                  | Selecione **iOS** como o **tipo de aplicação**, procure a aplicação e selecione a aplicação no Intune.                                                                                     |
| Aplicações da loja Windows Phone 8.1              | Aplicação da loja                  | Selecione **Windows Phone 8.1** como o **tipo de aplicação** e introduza o URL da loja Microsoft para a aplicação.                                                                               |
| Aplicações da loja Microsoft                      | Aplicação da loja                  | Selecione **Windows** como o **tipo de aplicação** e introduza o URL da loja Microsoft para a aplicação.                                                                                         |
| Aplicações Android for Work                     | Aplicação da loja                  | Localize e aprove a aplicação Android for Work da loja Google Play for Work.                                                                                        |
| Aplicações do Office 365 para Windows 10            | Aplicação da loja (Office 365)     | Selecione **Windows 10** em **Office 365 Suite** como o **tipo de aplicação** e, em seguida, selecione a aplicação do Office 365 que pretende instalar.                                                |
| Aplicações do Office 365 para macOS                 | Aplicação da loja (Office 365)     | Selecione **macOS** em **Office 365 Suite** como o **tipo de aplicação** e, em seguida, selecione o conjunto de aplicações do Office 365.                                                                     |
| Aplicações de linha de negócio (LOB) Android       | Aplicação de linha de negócio (LOB) | Selecione Aplicação de **linha de negócio** como o **tipo de aplicação**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação Android com a extensão **.apk**.                    |
| Aplicações de linha de negócio (LOB) iOS           | Aplicação de linha de negócio (LOB) | Selecione Aplicação de **linha de negócio** como o **tipo de aplicação**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação iOS com a extensão **.ipa**.                        |
| Aplicações de linha de negócio (LOB) Windows | Aplicação de linha de negócio (LOB) | Selecione Aplicação de **linha de negócio** como o **tipo de aplicação**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação iOS com a extensão **.xap**.                        |
| Aplicações de linha de negócio (LOB) Windows       | Aplicação de linha de negócio (LOB) | Selecione a Aplicação de linha de negócio como o tipo de aplicação, selecione o Ficheiro de pacote de aplicação e, em seguida, introduza um ficheiro de instalação iOS com a extensão **.msi**, **.appx** ou **.appxbundle**. |
| Aplicação iOS incorporada                          | Aplicação incorporada               | Selecione **Aplicação incorporada** como o **tipo de aplicação** e, em seguida, selecione a aplicação incorporada da lista de aplicações fornecidas.                                                                  |
| Aplicação Android incorporada                      | Aplicação incorporada               | Selecione **Aplicação incorporada** como o **tipo de aplicação** e, em seguida, selecione a aplicação incorporada da lista de aplicações fornecidas.                                                                  |
| Aplicações Web                                  | Aplicação Web                    | Selecione **Ligação Web** como o **tipo de aplicação** e introduza um URL válido que aponte para a aplicação Web.                                                                                        |

   
Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações móveis** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** será apresentado e permite-lhe selecionar o **Tipo de aplicação**. 

>[!TIP]
> Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona a partir de um ficheiro de instalação da aplicação. Por exemplo, para instalar uma aplicação LOB iOS, tem de adicionar a aplicação ao selecionar **Aplicação de linha de negócio** como o **Tipo de aplicação** a partir do painel **Adicionar aplicação**. Em seguida, selecione o ficheiro de pacote de aplicação (extensão .ipa). Normalmente, estes tipos de aplicações são escritos internamente.

## <a name="assess-app-requirements"></a>Avaliar requisitos da aplicação
Enquanto administrador de TI, tem de determinar as aplicações que o seu grupo tem de utilizar e as funcionalidades necessárias para cada grupo e subgrupo. Para cada aplicação, tem de determinar as plataformas necessárias, os grupos de utilizadores que precisam da aplicação, as políticas de configuração a aplicar a esses grupos e as políticas de proteção a aplicar.  

Além disso, tem de determinar se precisa de se focar na Gestão de Dispositivos Móveis (MDM) ou apenas na Gestão de Aplicações Móveis (MAM). Utilizar o Intune para gerir o dispositivo (Gestão de Dispositivos Móveis) é útil quando:
- Os utilizadores precisam de um perfil de conectividade empresarial VPN ou Wi-Fi para serem produtivos.
- Os utilizadores precisam que um conjunto de aplicações seja disponibilizado nos respetivos dispositivos.
- A sua organização tem de estar em conformidade com políticas de regulamentação ou outras políticas que necessitem de controlos de Gestão de Dispositivos Móveis (MDM) específicos, tal como segurança ou encriptação.

Utilizar o Intune para gerir aplicações (Gestão de Aplicações Móveis) sem gerir o dispositivo é útil quando:
- Quiser permitir que os utilizadores utilizem os seus próprios dispositivos (BYOD).
- Quiser fornecer um item de pop-up individual para informar os utilizadores de que as proteções de MAM estão aplicadas, em vez de enviar notificações contínuas ao nível do dispositivo.
- Quiser estar em conformidade com algumas políticas que exigem menos funcionalidades de gestão em dispositivos pessoais. Por exemplo, quer gerir os dados empresariais das aplicações, em vez de gerir os dados empresariais do dispositivo inteiro.

Para obter mais informações, [Comparar MDM e MAM](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Determinar quem irá utilizar a aplicação

Ao determinar as aplicações necessárias para a sua força de trabalho, considere os diferentes grupos de utilizadores que utilizam diferentes aplicações. Conhecer estes grupos também é útil depois de ter adicionado uma aplicação. Depois de adicionar uma aplicação, tem de designar um grupo de utilizadores que podem utilizar a aplicação. Em primeiro lugar, tem de determinar o grupo adequado que deve ter acesso à aplicação com base na confidencialidade dos dados que a aplicação contém. Poderá ter de incluir ou excluir determinados tipos de funções na sua organização. Por exemplo, podem ser necessárias apenas determinadas aplicações LOB para o seu grupo de vendas, enquanto as pessoas focadas em engenharia, finanças, RH ou aspetos jurídicos poderão não precisar de utilizar as aplicações LOB. Além disso, o seu grupo de vendas precisa de proteção de dados adicional e acesso a serviços empresariais internos nos respetivos dispositivos móveis. Tem de determinar a forma como este grupo se irá ligar aos recursos com a aplicação. Os dados aos quais a aplicação acede residem na cloud ou no local? Além disso, tem de determinar como é que os utilizadores se irão ligar aos recursos com a aplicação. O Intune também suporta permitir o acesso a aplicações móveis que exijam o acesso seguro a dados no local, como servidores de aplicações de linha de negócio. Normalmente, este tipo de acesso é feito através de [certificados geridos pelo Intune](certificates-configure.md) para controlo de acesso combinado com um proxy ou gateway de VPN padrão no perímetro, como o Proxy de Aplicações do Microsoft Azure Active Directory. A [Ferramenta de Encapsulamento de Aplicações e o SDK da Aplicação](apps-prepare-mobile-application-management.md) do Intune podem ajudar a conter os dados acedidos na sua aplicação de linha de negócio, para que não possa transmitir dados empresariais a aplicações ou serviços de consumidor.

Utilize o [Guia de planeamento, estruturação e implementação do Intune](planning-guide.md) para determinar como identificar os grupos organizacionais associados a cada cenário de aplicação de caso de utilização e caso de subutilização. Para obter detalhes sobre a atribuição de aplicações a grupos, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>Determinar o tipo de aplicação para a sua solução

Pode escolher entre os seguintes tipos de aplicação:
- **Aplicações da loja** – uma aplicação da loja é uma aplicação que foi carregada para a loja Microsoft, loja iOS ou loja Android. O fornecedor da aplicação da loja encarrega-se da manutenção e fornece atualizações à aplicação. Tem de selecionar a aplicação na lista da loja e adicioná-la com o Intune como uma aplicação disponível para os seus utilizadores.
- **Aplicações escritas internamente (linha de negócio)** – as aplicações criadas internamente são aplicações de linha de negócio (LOB). A funcionalidade deste tipo de aplicação foi criada para uma das plataformas suportadas do Intune, tal como Windows, iOS ou Android. A sua organização cria e fornece atualizações como um ficheiro separado. Tem de fornecer atualizações da aplicação aos utilizadores ao adicionar e implementar as atualizações com o Intune.
- **Aplicações na Web** – uma aplicação Web é uma aplicação de servidor de cliente. O servidor fornece a aplicação Web, que inclui a IU, conteúdos e funcionalidades. Além disso, normalmente as plataformas de alojamento na Web modernas oferecem segurança, balanceamento de carga e outras vantagens. A manutenção deste tipo de aplicação é feita separadamente na Web. Tem de utilizar o Intune para apontar para este tipo de aplicação. Também tem de designar que grupos de utilizadores podem aceder a esta aplicação. Tenha em atenção que o Android não suporta aplicações Web.

Ao determinar as aplicações necessárias para a sua organização, tenha em consideração a forma como estas aplicações se integram com serviços cloud, os dados aos quais as aplicações podem aceder, se as aplicações estão disponíveis para utilizadores BYOD e se as aplicações precisam de acesso à Internet.

Para obter mais informações sobre como determinar o tipo de aplicações que a sua organização necessita, veja **Aplicações** na secção **Requisitos de funcionalidades** em [Criar uma estrutura](planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Compreender as políticas de proteção e gestão de aplicações
O Intune permite-lhe modificar a funcionalidade das aplicações que implementa para ajudar a ajustá-las às políticas de conformidade e de segurança da sua empresa. Este controlo permite-lhe determinar como os dados da sua empresa são protegidos. As aplicações geridas pelo Intune têm um conjunto avançado de políticas de proteção de aplicações móveis, tal como:

- Restringir funções Copiar e colar e Guardar como
- Configurar ligações Web para serem abertas na aplicação Intune Managed Browser
- Ativar o acesso condicional ao nível da aplicação e a utilização de várias identidades

As aplicações geridas pelo Intune também permitem a proteção de aplicações sem exigir a inscrição, dando-lhe a opção de aplicar políticas de prevenção de perda de dados sem gerir o dispositivo do utilizador. Além disso, pode incorporar a gestão de aplicações móveis nas suas aplicações móveis e de linha de negócio com o Intune App Software Development Kit e a ferramenta de encapsulamento de aplicações. Para obter mais informações sobre estas ferramentas, veja [Descrição geral do SDK da Aplicação Intune](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Compreender as aplicações licenciadas
Para além das aplicações Web, aplicações da loja e aplicações LOB, também deve ter atenção o destino das aplicações licenciadas e aplicações de programa de compras em volume, tal como:     
- **Programa de Compras em Volume da Apple para Empresas (iOS e MacOS)** – a iOS App Store permite-lhe comprar múltiplas licenças para uma aplicação que pretende executar na sua empresa. A compra de várias cópias ajuda-o a gerir aplicações na sua empresa de forma eficiente. Para obter mais informações, veja [Gerir aplicações iOS compradas em volume](vpp-apps-ios.md).
- **Android for Work (Android)** – as aplicações em dispositivos Android for Work são atribuídas de forma diferente da atribuição em dispositivos Android padrão. Todas as aplicações que instala para o Android for Work provêm da Google Play for Work Store. Deve iniciar sessão na loja, procurar as aplicações desejadas e aprová-las. Em seguida, a aplicação aparece no nó Aplicações licenciadas do portal do Azure. A partir daqui, pode gerir a atribuição da aplicação da mesma forma que atribuiria qualquer outra aplicação.
- **Microsoft Store para Empresas (Windows 10)** – a Microsoft Store para Empresas dá-lhe um local para encontrar e comprar aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir do portal do Azure. Para obter mais informações, veja [Gerir aplicações a partir da Microsoft Store para Empresas](windows-store-for-business.md).

## <a name="before-you-add-apps"></a>Antes de adicionar aplicações
Considere os seguintes pontos antes de começar a adicionar e a atribuir as aplicações.

- Quando adicionar e atribuir uma aplicação a partir de uma loja, os utilizadores finais têm de ter uma conta nessa loja para conseguir instalar a aplicação.
- Algumas aplicações ou itens que atribuir poderão estar dependentes de aplicações iOS incorporadas. Por exemplo, se atribuir um livro a partir da loja iOS, a aplicação iBooks terá de estar presente no dispositivo. Se tiver removido a aplicação iBooks incorporada, não poderá utilizar o Intune para a restabelecer.

## <a name="cloud-storage-space"></a>Espaço de armazenamento na cloud
Todas as aplicações que criar com o tipo de instalação do instalador de software (por exemplo, uma aplicação de linha de negócio) são empacotadas e carregadas para o armazenamento na cloud do Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na cloud, o qual é utilizado para armazenar aplicações e atualizações geridas. Uma subscrição completa inclui 20 GB de espaço de armazenamento.

Pode comprar armazenamento adicional para o Intune com o seu método de compra original. Se tiver pago através de fatura ou cartão de crédito, visite o [Portal de Gestão de Subscrições](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions). Caso contrário, contacte o seu parceiro ou representante de vendas.

Requisitos de espaço de armazenamento na cloud:

-   Todos os ficheiros de instalação da aplicação têm de estar na mesma pasta.
-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Como criar e editar categorias para as aplicações

As categorias de aplicações podem ser utilizadas para o ajudar a ordenar as aplicações de modo a serem mais fáceis de encontrar por parte dos utilizadores no portal da empresa. Pode atribuir uma ou mais categorias a uma aplicação, por exemplo, **Aplicações de programador** ou **Aplicações de comunicação**.
Quando adiciona uma aplicação ao Intune, é-lhe dada a opção de selecionar a categoria que quiser. Utilize os tópicos das plataformas específicas para adicionar uma aplicação e atribuir categorias. Para criar e editar as suas próprias categorias, utilize o seguinte procedimento:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Categorias de aplicações** na secção **Configuração**. 
5. No painel **Categorias aplicações**, é apresentada uma lista das categorias atuais. Escolha uma das seguintes ações:
    - **Criar uma categoria** – selecione **Adicionar** para apresentar o painel **Criar categoria** e, em seguida, atribua um nome à nova categoria. Os nomes podem ser introduzidos em apenas um idioma e não são traduzidos pelo Intune. Quando terminar, clique em **Criar**.
    - **Editar uma categoria** – Para qualquer categoria na lista, escolha “**...**”. Esta opção apresenta um menu de contexto que lhe permite **Afixar ao dashboard** ou **Eliminar** a categoria.

## <a name="apps-added-automatically-by-intune"></a>Aplicações adicionadas automaticamente pelo Intune

Anteriormente, o Intune continha várias aplicações incorporadas que podia atribuir rapidamente. Com base no seu feedback, removemos esta lista e já não verá as aplicações incorporadas.
No entanto, se já tiver atribuído aplicações incorporadas, as mesmas continuarão visíveis na lista de aplicações. Pode continuar a atribuir estas aplicações conforme necessário.

## <a name="next-steps"></a>Próximos passos

Escolha um dos seguintes tópicos para saber como adicionar aplicações para cada plataforma ao Intune:

- [Aplicações da loja Android](store-apps-android.md)
- [Aplicações LOB Android](lob-apps-android.md)
- [Aplicações da loja iOS](store-apps-ios.md)
- [Aplicações LOB iOS](lob-apps-ios.md)
- [Aplicações Web (para todas as plataformas)](web-app.md)
- [Aplicações da loja Windows Phone 8.1](store-apps-windows-phone-8-1.md)
- [Aplicações LOB para Windows Phone](lob-apps-windows-phone.md)
- [Aplicações da loja Microsoft](store-apps-windows.md)
- [Aplicação LOB do Windows](lob-apps-windows.md)
- [Aplicações do Office 365 para Windows 10](apps-add-office365.md)
- [Aplicações do Office 365 para macOS](apps-add-office365-macos.md)
- [Aplicações incorporadas](apps-add-built-in.md)
