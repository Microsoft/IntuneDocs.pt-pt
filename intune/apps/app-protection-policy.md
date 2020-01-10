---
title: Descrição geral das políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como as políticas de proteção de aplicações do Microsoft Intune ajudam a proteger os dados da sua empresa e evitar perdas de dados.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: f11ccb51e08e96595dfcb9118c1f479f1b0fc3de
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692127"
---
# <a name="app-protection-policies-overview"></a>Descrição geral das políticas de proteção de aplicações

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As políticas de proteção de aplicativo (aplicativo) são regras que garantem que os dados de uma organização permaneçam seguros ou contidos em um aplicativo gerenciado. Uma política pode ser uma regra que é aplicada quando o utilizador tenta aceder ou mover dados "empresariais" ou um conjunto de ações que são proibidas ou monitorizadas quando um utilizador utiliza a aplicação. Uma aplicação gerida é uma aplicação que tem políticas de proteção de aplicações aplicadas à mesma e pode ser gerida pelo Intune.

Políticas de proteção de aplicativo de MAM (gerenciamento de aplicativo móvel) permitem que você gerencie e proteja os dados de sua organização em um aplicativo. Com o **Mam sem registro** (MAM-We), um aplicativo relacionado ao trabalho ou à escola que contém dados confidenciais pode ser gerenciado em quase qualquer [dispositivo](app-management.md#app-management-capabilities-by-platform), incluindo dispositivos pessoais em cenários BYOD ( **traga seu próprio dispositivo** ). Muitas aplicações de produtividade, como as aplicações do Microsoft Office, podem ser geridas pela MAM do Intune. Consulte a lista oficial de [aplicativos protegidos do Microsoft Intune](apps-supported-intune-apps.md) disponíveis para uso público.

## <a name="how-you-can-protect-app-data"></a>Como pode proteger dados de aplicações
Os seus empregados utilizam dispositivos móveis para tarefas pessoais e profissionais. Se, por um lado, quer garantir que os seus funcionários são produtivos, por outro, quer evitar a perda de dados, intencional e não intencional. Também irá querer proteger os dados da empresa que são acedidos a partir de dispositivos que não são geridos por si.

Pode utilizar as políticas de proteção de aplicações do Intune **independentemente de qualquer solução de gestão de dispositivos móveis (MDM)** . Esta independência ajuda-o a proteger dados da sua empresa com ou sem inscrição de dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

### <a name="app-protection-policies-on-devices"></a>Políticas de proteção de aplicativo em dispositivos

As políticas de proteção de aplicações podem ser configuradas para aplicações executadas em dispositivos que estão:

- **Inscritos no Microsoft Intune:** estes dispositivos pertencem, normalmente, à empresa.

- **Inscritos numa solução de gestão de dispositivos móveis (MDM) de terceiros:** estes dispositivos pertencem, normalmente, à empresa.

  > [!NOTE]
  > As políticas de gestão de aplicações móveis não devem ser utilizadas com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

- **Não registrado em nenhuma solução de gerenciamento de dispositivo móvel:** Normalmente, esses dispositivos são dispositivos de Propriedade do funcionário que não são gerenciados ou registrados no Intune ou outras soluções de MDM.

> [!IMPORTANT]
> Pode criar políticas de gestão de aplicações móveis para as aplicações móveis do Office que se ligam aos serviços do Office 365. Também pode proteger o acesso a caixas de correio do Exchange no local ao criar políticas de proteção de aplicações do Intune para o Outlook para iOS e Android com Autenticação Moderna híbrida. Antes de utilizar esta funcionalidade, certifique-se de que cumpre os [requisitos do Outlook para iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). As políticas de proteção de aplicações não são suportadas para outras aplicações que se ligam aos serviços do SharePoint ou do Exchange no local.

## <a name="benefits-of-using-app-protection-policies"></a>Benefícios do uso de políticas de proteção de aplicativo

Os benefícios importantes do uso de políticas de proteção de aplicativo são os seguintes:

- **Proteger os dados da empresa no nível do aplicativo.** Como a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

- **A produtividade do usuário final não é afetada e as políticas não se aplicam ao usar o aplicativo em um contexto pessoal.** As políticas são aplicadas apenas num contexto profissional, o que lhe permite proteger os dados da empresa sem afetar os dados pessoais.

- **As políticas de proteção de aplicativo garantem que as proteções de camada de aplicativo estejam em vigor.** Por exemplo, pode:
  - Exigir um PIN para abrir uma aplicação num contexto de trabalho 
  - Controlar a partilha de dados entre aplicações 
  - Impedir a gravação de dados empresariais da aplicação numa localização de armazenamento pessoal

- **O MDM, além do MAM, garante que o dispositivo esteja protegido**. Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

A utilização da MDM com políticas de proteção de aplicações tem outras vantagens e as empresas podem utilizar as políticas de proteção de aplicações com ou sem MDM ao mesmo tempo. Por exemplo, considere um funcionário que utiliza os um telemóvel atribuído pela empresa e o seu próprio tablet pessoal. O telemóvel da empresa está inscrito na MDM e protegido por políticas de proteção de aplicações, ao passo que o dispositivo pessoal está protegido apenas por políticas de proteção de aplicações.

Se você aplicar uma política de MAM ao usuário sem definir o estado do dispositivo, o usuário receberá a política de MAM no dispositivo BYOD e no dispositivo gerenciado pelo Intune. Você também pode aplicar uma política de MAM com base no estado gerenciado. Portanto, quando você cria uma política de proteção de aplicativo, ao lado de **destino para todos os tipos de aplicativo**, você seleciona **não**. Em seguida, faça o seguinte:
- Aplique uma política de MAM menos estrita aos dispositivos gerenciados do Intune e aplique uma política de MAM mais restritiva a dispositivos não registrados no MDM.
- Aplique uma política de MAM somente a dispositivos não registrados.

## <a name="supported-platforms-for-app-protection-policies"></a>Plataformas suportadas das políticas de proteção de aplicações

O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos nos quais quer executá-las. Para obter mais informações, consulte [recursos de gerenciamento de aplicativo por plataforma](app-management.md#app-management-capabilities-by-platform).

O suporte para plataformas de políticas de proteção de aplicações do Intune está alinhado com o suporte para plataformas de aplicações móveis do Office para os dispositivos Android e iOS. Para obter detalhes, veja a secção **Aplicações móveis** de [Requisitos de Sistema do Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> O Portal da Empresa do Intune é necessário no dispositivo para receber as Políticas de Proteção de Aplicações do Android. Para obter mais informações, veja os [Requisitos das aplicações de acesso ao Portal da Empresa do Intune](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Como as políticas de proteção de aplicações protegem os dados das aplicações

### <a name="apps-without-app-protection-policies"></a>Aplicações sem políticas de proteção de aplicações

Quando as aplicações são utilizadas sem restrições, os dados pessoais e da empresa podem confundir-se. Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou ser transferidos para aplicações fora da sua competência e que resulta em perda de dados. As setas no diagrama a seguir mostram a movimentação de dados irrestrito entre os aplicativos corporativos e pessoais e os locais de armazenamento.

![Imagem conceptual do movimento de dados entre aplicações sem políticas em vigor](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Proteção de dados com políticas de proteção de aplicativo (aplicativo)

Você pode usar as políticas de proteção de aplicativo para impedir que os dados da empresa sejam salvos no armazenamento local do dispositivo (consulte a imagem abaixo). Também pode restringir o movimento de dados para outras aplicações que não estão protegidas pelas Políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de realocação **de dados como salvar cópias de dados da organização**e **restringir recortar, copiar e colar**.
- Definições de política de acesso, como **Exigir PIN simples para o acesso** e **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

![Imagem conceptual que mostra os dados da empresa a serem protegidos por políticas](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Proteção de dados com o aplicativo em dispositivos gerenciados por uma solução de MDM

A ilustração abaixo mostra as camadas de proteção que as políticas de MDM e proteção de aplicativo oferecem juntas.

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos BYOD](./media/app-protection-policy/app-protection-policies-with-mdm.png)

A solução MDM agrega valor fornecendo o seguinte:

- Inscreve o dispositivo
- Implementa as aplicações no dispositivo
- Fornece gestão e conformidade dos dispositivos contínuas

As políticas de proteção de aplicativo adicionam valor, fornecendo o seguinte:

- Ajudar a proteger os dados da empresa contra vazar para serviços e aplicativos de consumidor
- Aplicar restrições como *salvar como*, *área de transferência*ou *PIN*, aos aplicativos cliente
- Apagar dados da empresa quando necessário em aplicativos sem remover esses aplicativos do dispositivo

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Proteção de dados com o aplicativo para dispositivos sem registro

O diagrama a seguir ilustra como as políticas de proteção de dados funcionam no nível do aplicativo sem MDM.

![Imagem que mostra como as políticas de proteção de aplicativo funcionam em dispositivos sem registro (dispositivos não gerenciados)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

Nos dispositivos BYOD não inscritos em nenhuma solução de MDM, as políticas de proteção de aplicações podem ajudar a proteger os dados da empresa ao nível da aplicação.
No entanto, há algumas limitações a serem consideradas, como:

- Não pode implementar aplicações no dispositivo. O utilizador final tem de obter as aplicações na loja.
- Não pode aprovisionar perfis de certificado nestes dispositivos.
- Não pode aprovisionar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicações que pode gerir com as políticas de proteção de aplicações

Qualquer aplicação que tenha sido integrada com o [SDK da Aplicação Intune](../developer/app-sdk.md) ou encapsulada pela [Ferramenta de Encapsulamento de Aplicações do Intune](../developer/apps-prepare-mobile-application-management.md) pode ser gerida com as políticas de proteção de aplicações do Intune. Consulte a lista oficial de [Microsoft Intune aplicativos protegidos](apps-supported-intune-apps.md) que foram criados usando essas ferramentas e estão disponíveis para uso público.

A equipe de desenvolvimento do SDK do Intune testa e mantém ativamente o suporte para aplicativos criados com as plataformas nativas do Android, iOS (obj-C, Swift), Xamarin, Xamarin. Forms e Cordova. Embora alguns clientes tenham tido êxito com a integração do SDK do Intune com outras plataformas, como reagir nativo e NativeScript, não fornecemos orientações explícitas ou plug-ins para desenvolvedores de aplicativos usando algo diferente de nossas plataformas com suporte.

O [SDK de aplicativos do Intune](../developer/app-sdk.md) usa alguns recursos avançados de autenticação moderna das Adal ([bibliotecas de autenticação de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) ) para as versões de terceiros e de terceiros do SDK. Assim, a MSAL ( [biblioteca de autenticação da Microsoft](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) ) não funciona bem com muitos dos nossos principais cenários, como a autenticação no serviço de proteção de aplicativo do Intune e a inicialização condicional. Considerando que as diretrizes gerais da equipe de identidade da Microsoft é mudar para MSAL para todos os aplicativos de Microsoft Office, o [SDK de aplicativos do Intune](../developer/app-sdk.md) eventualmente precisará dar suporte a ele, mas não há planos atualmente.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Requisitos do usuário final para usar políticas de proteção de aplicativo

A lista a seguir fornece os requisitos do usuário final para usar políticas de proteção de aplicativo em um aplicativo gerenciado pelo Intune:

- O utilizador final tem de ter uma conta no Azure Active Directory (AAD). Veja [Adicionar utilizadores e conceder permissões administrativas no Intune](../fundamentals/users-add.md) para saber como criar utilizadores do Intune no Azure Active Directory.

- O utilizador final tem de ter uma licença para o Microsoft Intune atribuída à conta do Azure Active Directory dele. Veja [Gerir licenças do Intune](../fundamentals/licenses-assign.md) para saber como atribuir licenças do Intune aos utilizadores finais.

- O utilizador final tem de pertencer a um grupo de segurança visado por uma política de proteção de aplicações. A mesma política de proteção de aplicações tem de abranger a aplicação específica em utilização. As políticas de proteção de aplicações podem ser criadas e implementadas na consola do Intune, no [portal do Azure](https://portal.azure.com). No momento, os grupos de segurança podem ser criados no [centro de administração do Microsoft 365](https://admin.microsoft.com).

- O utilizador final tem de iniciar sessão na aplicação através da respetiva conta do AAD.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Políticas de proteção de aplicativo para aplicativos Microsoft Office

Há alguns requisitos adicionais que você deseja conhecer ao usar políticas de proteção de aplicativo com Microsoft Office aplicativos.

### <a name="outlook-mobile-app"></a>Aplicativo móvel do Outlook
Os requisitos adicionais para usar o [aplicativo móvel do Outlook](https://products.office.com/outlook) incluem o seguinte:

- O utilizador final tem de ter a aplicação Outlook para dispositivos móveis instalada no dispositivo dele.
- O utilizador final tem de ter uma licença e uma caixa de correio do [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) associadas à conta do Azure Active Directory dele.

  >[!NOTE]
  > Atualmente, a aplicação Outlook para dispositivos móveis só suporta a Proteção de Aplicações do Intune para o Microsoft Exchange Online e o [Exchange Server com autenticação moderna híbrida](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) e não suporta o Exchange no Office 365 Dedicated.

### <a name="word-excel-and-powerpoint"></a>Word, Excel e PowerPoint
Os requisitos adicionais para usar os aplicativos [Word, Excel e PowerPoint](https://products.office.com/business/office) incluem o seguinte:

- O utilizador final tem de ter uma licença do [Office 365 Empresas ou Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) associada à respetiva conta do Azure Active Directory. A subscrição tem de incluir as aplicações do Office para dispositivos móveis e pode incluir uma conta de armazenamento na cloud com o [OneDrive para Empresas](https://onedrive.live.com/about/business/). As licenças do Office 365 podem ser atribuídas no [centro de administração do Microsoft 365](https://admin.microsoft.com) seguindo estas [instruções](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- O usuário final deve ter um local gerenciado configurado usando a funcionalidade de salvar como granular na configuração de política "salvar cópias de dados da organização". Por exemplo, se a localização gerida for o OneDrive, a aplicação [OneDrive](https://onedrive.live.com/about/) deverá ser configurada na aplicação Word, Excel ou PowerPoint do utilizador final.

- Se a localização gerida for o OneDrive, a aplicação terá de ser visada pela política de proteção de aplicações implementada para o utilizador final.

  >[!NOTE]
  > Atualmente, as aplicações do Office para dispositivos móveis só suportam o SharePoint Online e não o SharePoint no local.

### <a name="managed-location-needed-for-office"></a>Local gerenciado necessário para o Office
Um local gerenciado (ou seja, OneDrive) é necessário para o Office. O Intune marca todos os dados no aplicativo como "corporativo" ou "pessoal". Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas).

### <a name="skype-for-business"></a>Skype para Empresas
Há requisitos adicionais para usar o Skype for Business. Veja os requisitos de licença do [Skype para Empresas](https://products.office.com/skype-for-business/it-pros). Para as configurações híbridas e no local do Skype para Empresas (SfB), veja [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (Autenticação Híbrida Moderna para SfB e o Exchange está em disponibilidade geral) e [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (Autenticação Moderna para SfB Local com o AAD), respetivamente.

## <a name="app-protection-global-policy"></a>Política Global de proteção de aplicações

Se um administrador do OneDrive navegar até **admin.office.com** e selecionar acesso por **Dispositivo**, poderá definir os controlos da **Gestão de aplicações móveis** para as aplicações cliente OneDrive e SharePoint. 

As definições, disponibilizadas para a consola de administração do OneDrive, configuram uma política de proteção de aplicações do Intune especial denominada política **Global**. Esta política global aplica-se a todos os utilizadores no seu inquilino e não existe nenhuma forma de controlar a segmentação da política. 

Uma vez ativada, as aplicações OneDrive e SharePoint para iOS e Android estão protegidas com as definições selecionadas por predefinição. Um profissional de TI pode editar esta política na consola do Intune para adicionar mais aplicações segmentadas e para modificar qualquer definição de política. 

Por predefinição, só pode existir uma política **Global** por inquilino. No entanto, pode utilizar [Graph APIs do Intune](../developer/intune-graph-apis.md) para criar políticas globais adicionais por inquilino, mas não é recomendado. A criação de políticas globais adicionais não é recomendada, uma vez que resolver problemas relacionados com a implementação destas políticas pode tornar-se complicado.

Embora a política **Global** se aplique a todos os utilizadores no seu inquilino, qualquer política de proteção de aplicações padrão do Intune substituirá estas definições.

## <a name="app-protection-features"></a>Funcionalidades de proteção de aplicações

### <a name="multi-identity"></a>Várias identidades

O suporte a várias identidades permite que um aplicativo dê suporte a vários públicos. Esses públicos são usuários "corporativos" e "pessoais". As contas corporativas e de estudante são usadas por públicos "corporativos", enquanto as contas pessoais seriam usadas para as audiências do consumidor, como Microsoft Office usuários. Um aplicativo que dá suporte a várias identidades pode ser lançado publicamente, em que as políticas de proteção de aplicativo se aplicam somente quando o aplicativo é usado no contexto de trabalho e escola ("corporativo"). O suporte a várias identidades usa o [SDK de aplicativo do Intune](../developer/app-sdk.md) para aplicar somente as políticas de proteção de aplicativo à conta corporativa ou de estudante conectada ao aplicativo. Se uma conta pessoal tiver sessão iniciada na aplicação, os dados permanecem inalterados.

Para obter um exemplo de contexto "pessoal", considere um usuário que inicia um novo documento no Word, isso é considerado contexto pessoal para que as políticas de Proteção de Aplicativo do Intune não sejam aplicadas. Depois que o documento for salvo na conta "corporativa" do OneDrive, ele será considerado contexto "corporativo" e as políticas de Proteção de Aplicativo do Intune serão aplicadas.

Para obter um exemplo de contexto de trabalho ou "corporativo", considere um usuário que inicia o aplicativo do OneDrive usando sua conta corporativa. No contexto de trabalho, não pode mover ficheiros para uma localização de armazenamento pessoal. Posteriormente, quando utiliza o OneDrive com a sua conta pessoal, pode copiar e mover dados dos seus OneDrive pessoais, sem restrições.

O Outlook tem uma exibição de email combinada de emails "pessoais" e "corporativos". Nessa situação, o aplicativo Outlook solicita o PIN do Intune na inicialização.

Para obter mais informações sobre várias identidades no Intune, consulte [MAM e várias identidades](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>PIN do aplicativo do Intune

O Número de Identificação Pessoal (PIN) é um código de acesso utilizado para verificar que o utilizador certo está a aceder aos dados da organização numa aplicação.

**Aviso de PIN**<br>
O Intune só pede ao utilizador para introduzir o PIN da aplicação quando o mesmo quiser aceder aos dados "empresariais". Em aplicativos de várias identidades, como Word, Excel ou PowerPoint, o usuário recebe um prompt para o PIN quando tenta abrir um documento ou arquivo "corporativo". Em aplicativos de identidade única, como aplicativos de linha de negócios gerenciados usando a [ferramenta de disposição do aplicativo do Intune](../developer/apps-prepare-mobile-application-management.md), o PIN é solicitado na inicialização, pois o SDK do aplicativo do [Intune](../developer/app-sdk.md) sabe que a experiência do usuário no aplicativo é sempre "corporativa".

**Prompt de PIN, prompt de credencial corporativa, frequência**<br>
O administrador de ti pode definir a configuração de política de proteção de aplicativo do Intune **verificar novamente os requisitos de acesso após (minutos)** no console de administração do Intune. Essa configuração especifica a quantidade de tempo antes que os requisitos de acesso sejam verificados no dispositivo e a tela PIN do aplicativo, ou prompt de credencial corporativa, é mostrado novamente. Contudo, os detalhes importantes sobre o PIN que afetam a frequência de solicitação do utilizador incluem:

- **O PIN é compartilhado entre aplicativos do mesmo editor para melhorar a usabilidade:**<br> No iOS, um PIN de aplicativo é compartilhado entre todos os aplicativos **do mesmo editor de aplicativos**. Por exemplo, todos os aplicativos da Microsoft compartilham o mesmo PIN. No Android, um PIN da aplicação é partilhado entre todas as aplicações.
- **O comportamento *verificar novamente os requisitos de acesso após (minutos)* após a reinicialização do dispositivo:**<br> Um temporizador acompanha o número de minutos de inatividade que determinam quando mostrar o PIN do aplicativo do Intune ou a solicitação de credencial corporativa em seguida. No iOS, o temporizador não é afetado pela reinicialização do dispositivo. Assim, a reinicialização do dispositivo não tem nenhum efeito sobre o número de minutos que o usuário esteve inativo de um aplicativo iOS com a política de PIN do Intune (ou credencial corporativa) direcionada. No Android, o temporizador é redefinido na reinicialização do dispositivo. Assim, os aplicativos Android com a política de PIN (ou credencial corporativa) do Intune provavelmente solicitarão um PIN do aplicativo ou uma solicitação de credencial corporativa, independentemente do valor da configuração ' verificar novamente os requisitos de acesso após (minutos) ' **após a reinicialização do dispositivo**.  
- **A natureza de sobreversão do temporizador associado ao PIN:**<br> Depois que um PIN é inserido para acessar um aplicativo (aplicativo A) e o aplicativo deixa o primeiro plano (foco de entrada principal) no dispositivo, o temporizador é redefinido para esse PIN. Não será pedido nenhum PIN às aplicações (aplicação B) que partilhem este PIN, uma vez que o temporizador foi reposto. O pedido aparecerá novamente depois de o valor “Reverificar os requisitos de acesso após (minutos)” ter sido atingido.

No caso dos dispositivos iOS, mesmo que o PIN seja partilhado entre aplicações de diferentes publicadores, o pedido aparecerá novamente quando o valor **Reverificar os requisitos de acesso após (minutos)** for alcançado novamente para a aplicação que não é o foco de introdução principal. Por exemplo, um utilizador tem a aplicação _A_ do publicador _X_ e a aplicação _B_ do publicador _Y_ e essas duas aplicações partilham o mesmo PIN. O utilizador está concentrado na aplicação _A_ (primeiro plano) e a aplicação _B_ está minimizada. O PIN seria necessário depois de o valor **Reverificar os requisitos de acesso após (minutos)** ser alcançado e de o utilizador mudar para a aplicação _B_.

  >[!NOTE]
  > Para verificar os requisitos de acesso do utilizador com mais frequência (ou seja, o pedido de PIN), especialmente para uma aplicação utilizada com frequência, é recomendado reduzir o valor da definição “Reverificar os requisitos de acesso após (minutos)”.

**PINs de aplicativo internos para Outlook e OneDrive**<br>
O PIN do Intune funciona com base em um temporizador baseado em inatividade (o valor de **verificar novamente os requisitos de acesso após (minutos)** ). Como tal, os pedidos de PIN do Intune são apresentados de forma independente dos pedidos de PIN de aplicação incorporados para o Outlook e OneDrive, que normalmente estão associados à inicialização da aplicação por predefinição. Se o utilizador receber ambos os pedidos de PIN ao mesmo tempo, o comportamento esperado deverá ser o de que o PIN do Intune tem precedência.

**Segurança de PIN do Intune**<br>
O PIN serve para garantir que só o utilizador correto consegue aceder aos dados da respetiva organização na aplicação. Por conseguinte, o utilizador final tem de iniciar sessão com a conta profissional ou escolar para poder definir ou repor o PIN da aplicação Intune. Essa autenticação é tratada por Azure Active Directory por meio do Secure token Exchange e não é transparente para o [SDK do aplicativo do Intune](../developer/app-sdk.md). No que diz respeito à segurança, a melhor forma de proteger os seus dados profissionais ou escolares é encriptá-los. A encriptação não está relacionada com o PIN da aplicação, mas é a própria política de proteção da aplicação.

**PIN do Intune-proteção contra ataques de força bruta**<br>
Como parte da política de PIN da aplicação, o administrador de TI pode definir o número máximo de vezes que um utilizador pode tentar autenticar o respetivo PIN antes de bloquear a aplicação. Depois que o número de tentativas for atingido, o [SDK de aplicativos do Intune](../developer/app-sdk.md) poderá apagar os dados "corporativos" no aplicativo.
  
**Definir um PIN duas vezes em aplicativos do mesmo editor?**<br>
No momento, o MAM (no iOS) permite o PIN de nível de aplicativo com caracteres alfanuméricos e especiais (chamados de ' senha '), o que exige a participação de aplicativos (ou seja, WXP, Outlook, Managed Browser, Yammer) para integrar o [SDK de aplicativo do Intune para IOS](../developer/app-sdk-ios.md). Caso contrário, as definições do código de acesso não são impostas corretamente nas aplicações visadas. Esta funcionalidade foi lançada com o SDK do Intune para iOS v. 7.1.12.

Para suportar esta funcionalidade e garantir a retrocompatibilidade com versões anteriores do SDK do Intune para iOS, todos os PINs (numéricos ou códigos de acesso) na versão 7.1.12 ou superior são processados em separado do PIN numérico em versões anteriores do SDK. Como tal, se um dispositivo tiver aplicações com o SDK do Intune para versões do iOS anteriores à 7.1.12 E posteriores à 7.1.12 do mesmo publicador, terá de configurar dois PINs. Os dois PINs (para cada aplicativo) não estão relacionados de nenhuma maneira (ou seja, eles devem aderir à política de proteção do aplicativo aplicada ao aplicativo). Como tal, *somente* se os aplicativos a e B tiverem as mesmas políticas aplicadas (em relação ao PIN), o usuário poderá configurar o mesmo PIN duas vezes. 

Este comportamento é específico para o PIN em aplicações iOS com a Gestão de Aplicações Móveis do Intune ativada. Ao longo do tempo, como as aplicações adotam versões posteriores do SDK do Intune para iOS, ter de definir um PIN duas vezes em aplicações do mesmo publicador deixa de ser um problema. Veja a nota abaixo para obter um exemplo.

  >[!NOTE]
  > Por exemplo, se a aplicação A tiver sido concebida com uma versão anterior à 7.1.12 e a aplicação B tiver sido concebida com uma versão igual ou superior à 7.1.12 do mesmo publicador, o utilizador final terá de configurar PINs em separado para A e B se ambas estiverem instaladas num dispositivo iOS.
  > Se um aplicativo C que tem a versão 7.1.9 do SDK estiver instalado no dispositivo, ele compartilhará o mesmo PIN que o aplicativo A. Um aplicativo D criado com 7.1.14 compartilhará o mesmo PIN que o aplicativo B.  
  > Se apenas as aplicações A e C estiverem instaladas num dispositivo, será preciso definir um PIN. O mesmo se aplica se apenas as aplicações B e D estiverem instaladas num dispositivo.

### <a name="app-data-encryption"></a>Criptografia de dados de aplicativo
Os administradores de TI podem implementar uma política de proteção de aplicações que exija a encriptação dos dados da aplicação. Como parte da política, o administrador de TI também pode especificar a altura em que os conteúdos são encriptados.

**Como o processo de criptografia de dados do Intune**<br> Veja as [definições da política de proteção de aplicações para Android](app-protection-policy-settings-android.md) e as [definições da política de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) para obter informações detalhadas sobre a definição de encriptação da política de proteção de aplicações.

**Dados criptografados**<br>
Só os dados marcados como "empresariais" são encriptados de acordo com a política de proteção de aplicações do administrador de TI. Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para os aplicativos do Office, o Intune considera o seguinte como locais de negócios:

- Email (Exchange) 
- Armazenamento em nuvem (aplicativo OneDrive com uma conta do OneDrive for Business)

Para aplicativos de linha de negócios gerenciados pela [ferramenta de disposição do aplicativo do Intune](../developer/apps-prepare-mobile-application-management.md), todos os dados do aplicativo são considerados "corporativos".

**Apagar dados remotamente**<br>
O Intune pode apagar dados de aplicativos de três maneiras diferentes: 
- Apagamento completo de dispositivo
- Apagamento seletivo para MDM 
- Apagamento seletivo de MAM

Para obter mais informações sobre a limpeza remota da MDM, veja [Remove devices by using wipe or retire](../remote-actions/devices-wipe.md) (Remover dispositivos através da limpeza ou extinção). Para obter mais informações sobre a limpeza seletiva através da MAM, veja [a ação Extinguir](../remote-actions/devices-wipe.md#retire) e [Como eliminar apenas dados empresariais de aplicações](apps-selective-wipe.md).

A [limpeza](../remote-actions/devices-wipe.md) elimina todas as definições e dados dos utilizadores do **dispositivo** ao restaurar o dispositivo para as predefinições de fábrica. O dispositivo é removido do Intune.

  >[!NOTE]
  > A limpeza só pode ser realizada em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune.

**Apagamento seletivo para MDM**<br>
Veja a secção [Remover dispositivos – extinguir](../remote-actions/devices-wipe.md#retire) para ler mais sobre a remoção dos dados da empresa.

**Apagamento seletivo para MAM**<br>
A eliminação seletiva para MAM simplesmente remove os dados da aplicação da empresa de uma aplicação. O pedido é iniciado através do portal do Intune Azure. Para saber como iniciar um pedido de eliminação, veja o artigo [Como eliminar apenas os dados empresariais das aplicações](apps-selective-wipe.md).

Se o usuário estiver usando o aplicativo quando o apagamento seletivo for iniciado, o [SDK de aplicativo do Intune](../developer/app-sdk.md) verificará a cada 30 minutos uma solicitação de apagamento seletivo do serviço de Mam do Intune. Também verifica a existência de pedidos de eliminação seletiva quando o utilizador inicia a aplicação pela primeira vez e inicia sessão com a conta profissional ou escolar.

**Quando os serviços locais (local) não funcionam com os aplicativos protegidos do Intune**<br>
A proteção de aplicativo do Intune depende da identidade do usuário para ser consistente entre o aplicativo e o [SDK do aplicativo do Intune](../developer/app-sdk.md). A única forma de o garantir é através da autenticação moderna. Existem cenários onde aplicações podem funcionar com uma configuração no local, mas não é garantido e nem consistente.

**Maneira segura de abrir links da Web de aplicativos gerenciados**<br>
O administrador de TI pode implementar e definir a política de proteção de aplicações para a [aplicação Intune Managed Browser](app-configuration-managed-browser.md), um browser desenvolvido pelo Microsoft Intune que pode ser gerido facilmente com o Intune. O administrador de TI pode exigir que todas as ligações Web nas aplicações geridas pelo Intune sejam abertas através da aplicação Managed Browser.

## <a name="examples-of-app-protection-policies"></a>Exemplos de políticas de proteção de aplicativo

Para saber mais sobre exemplos de políticas de proteção de aplicativo e ver informações detalhadas sobre cada configuração de política de proteção de aplicativo, consulte as configurações de política de proteção de aplicativo [Android](app-protection-policy-settings-android.md) e [configurações de política de proteção de aplicativo IOS](app-protection-policy-settings-ios.md).

## <a name="app-protection-experience-for-ios-devices"></a>Experiência de proteção de aplicativo para dispositivos iOS

### <a name="device-fingerprint-or-face-ids"></a>Impressão digital do dispositivo ou IDs facial 
As políticas de proteção de aplicações do Intune permitem o controlo sobre o acesso da aplicação apenas ao utilizador licenciado do Intune. Uma das formas de controlar o acesso à aplicação é exigir o Touch ID ou o Face ID da Apple nos dispositivos suportados. O Intune implementa um comportamento em que se houver qualquer alteração à base de dados biométricos do dispositivo, o Intune pede ao utilizador um PIN quando atingir o valor do tempo limite de inatividade seguinte. As alterações a dados biométricos incluem a adição ou remoção de uma impressão digital ou de um rosto. Se o utilizador do Intune não tiver um PIN definido, este é direcionado para configurar um PIN do Intune.
 
A intenção desse processo é continuar a manter os dados da sua organização no aplicativo protegidos e protegidos no nível do aplicativo. Esta funcionalidade só está disponível para iOS e requer a participação de aplicações que integrem o SDK da aplicação Intune para iOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.
  
### <a name="ios-share-extension"></a>extensão de compartilhamento do iOS
Você pode usar a extensão de compartilhamento do iOS para abrir dados corporativos ou de estudante em aplicativos não gerenciados, mesmo com a política de transferência de dados definida **somente para aplicativos gerenciados** ou **nenhum aplicativo**. A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por isso, o _**Intune encripta os dados "empresariais" antes de estes serem partilhados fora da aplicação**_ . Você pode validar esse comportamento de criptografia ao tentar abrir um arquivo "corporativo" fora do aplicativo gerenciado. O ficheiro deve estar encriptado e não deve ser possível abri-lo fora da aplicação gerida.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Várias configurações de acesso de proteção de aplicativo do Intune para o mesmo conjunto de aplicativos e usuários
As políticas de proteção de aplicativo do Intune para acesso serão aplicadas em uma ordem específica em dispositivos de usuário final à medida que tentarem acessar um aplicativo de destino de sua conta corporativa. Em geral, uma limpeza teria precedência, seguida de um bloqueio e de um aviso que pode ser dispensado. Por exemplo, se for aplicável ao utilizador/aplicação específico, uma definição de sistema operativo iOS mínimo que avisa um utilizador para atualizar a respetiva versão do iOS será aplicada após a definição de sistema operativo iOS mínimo bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura o sistema operativo iOS mínimo para 11.0.0.0 e o sistema operativo iOS mínimo (apenas Aviso) para 11.1.0.0, embora o dispositivo que tentava aceder à aplicação tivesse o iOS 10, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de sistema operativo iOS que resulta num bloqueio do acesso.

Ao lidar com diferentes tipos de definições, um requisito de versão de SDK da Aplicação Intune teria precedência, seguido do requisito de versão da aplicação e do requisito de versão de sistema operativo iOS. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem. Recomendamos que o requisito de versão do SDK da Aplicação Intune só seja configurado após receber orientações sobre cenários de bloqueio essenciais por parte da equipa de produto do Intune.

## <a name="app-protection-experience-for-android-devices"></a>Experiência de proteção de aplicativo para dispositivos Android

### <a name="company-portal-app-and-intune-app-protection"></a>Portal da Empresa aplicativo e proteção de aplicativo do Intune
Uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. Embora a aplicação Portal da Empresa seja sempre necessária, a inscrição de dispositivos _não é obrigatória_. Para o gerenciamento de aplicativos móveis sem registro (MAM-WE), o usuário final precisa apenas ter o aplicativo Portal da Empresa instalado no dispositivo.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Várias configurações de acesso de proteção de aplicativo do Intune para o mesmo conjunto de aplicativos e usuários
As políticas de proteção de aplicativo do Intune para acesso serão aplicadas em uma ordem específica em dispositivos de usuário final à medida que tentarem acessar um aplicativo de destino de sua conta corporativa. Em geral, um bloqueio teria precedência, seguido de um aviso que pode ser dispensado. Por exemplo, se aplicável ao utilizador/aplicação específico, uma definição mínima de versão de patch do Android que avisa um utilizador para atualizar o patch será aplicada após a definição mínima de versão de patch do Android bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura a versão mínima de patch do Android para 2018-03-01 e a versão mínima de patch do Android (apenas Aviso) para 2018-02-01, embora o dispositivo que tentava aceder à aplicação tivesse a versão de patch 2018-01-01, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de patch do Android que resulta num bloqueio do acesso. 

Ao lidar com diferentes tipos de definições, um requisito de versão de aplicação teria precedência, seguido do requisito de versão de sistema operativo Android e do requisito de versão de patch do Android. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Políticas de proteção de aplicativo do Intune e atestado de SafetyNet do Google para dispositivos Android 
As políticas de proteção de aplicativo do Intune fornecem a capacidade para os administradores exigirem que os dispositivos do usuário final passem o atestado SafetyNet do Google para dispositivos Android. Uma nova determinação de serviço Google Play será relatada ao administrador de ti em um intervalo determinado pelo serviço do Intune. A frequência com que a chamada de serviço é feita é limitada devido ao carregamento, portanto, esse valor é mantido internamente e não é configurável. Qualquer ação configurada pelo administrador de ti para a configuração de atestado do Google SafetyNet será executada com base no último resultado relatado para o serviço do Intune no momento da inicialização condicional. Se não houver dados, o acesso será permitido dependendo de nenhuma outra verificação de inicialização condicional falhar, e Google Play serviço "de ida e volta" para determinar os resultados de atestado começarão no back-end e solicitará o usuário assincronamente se o dispositivo tiver falhado. Se houver dados obsoletos, o acesso será bloqueado ou permitido dependendo do último resultado relatado e, da mesma forma, um serviço de Google Play "ida e volta" para determinar os resultados do atestado começará e avisará o usuário de forma assíncrona se o dispositivo tiver falhado.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Políticas de proteção de aplicativo do Intune e API de verificação de aplicativos do Google para dispositivos Android
As políticas de Proteção de Aplicativo do Intune fornecem a capacidade para os administradores exigirem que os dispositivos do usuário final enviem sinais por meio da API de aplicativos de verificação do Google para dispositivos Android. As instruções sobre como fazer isso variam um pouco pelo dispositivo. O processo geral envolve ir para a Google Play Store e, em seguida, clicar em **meus aplicativos & jogos**, clicando no resultado da última verificação do aplicativo, que o levará para o menu executar proteção. Certifique-se de que a alternância para o **dispositivo de verificação para ameaças à segurança** esteja ativada.

### <a name="googles-safetynet-attestation-api"></a>API de atestado do SafetyNet do Google 
O Intune utiliza Google Play proteger as APIs SafetyNet para adicionar às nossas verificações de detecção de raiz existentes para dispositivos não registrados. O Google desenvolveu e manteve essa API definida para aplicativos Android a adotarem se não quiserem que seus aplicativos sejam executados em dispositivos com raiz. O aplicativo de pagamento do Android incorporou isso, por exemplo. Embora o Google não compartilhe publicamente as verificações de detecção de raiz que ocorrem, esperamos que essas APIs detectem usuários que fizeram a raiz de seus dispositivos. Esses usuários podem então ser impedidos de acessar ou suas contas corporativas apagadas de seus aplicativos habilitados para políticas. **Verificar a integridade básica** informa sobre a integridade geral do dispositivo. Dispositivos com raiz, emuladores, dispositivos virtuais e dispositivos com sinais de falha de violação de integridade básica. **Verificar a integridade básica & dispositivos certificados** informa sobre a compatibilidade do dispositivo com os serviços do Google. Somente dispositivos não modificados que foram certificados pelo Google podem passar por essa verificação. Os dispositivos que falharão incluem o seguinte:

- Dispositivos que falham na integridade básica
- Dispositivos com um carregador de erro desbloqueado
- Dispositivos com uma imagem de sistema personalizada/ROM
- Dispositivos para os quais o fabricante não se aplica, ou passar, certificação do Google
- Dispositivos com uma imagem do sistema criada diretamente dos arquivos de origem do programa de software livre do Android
- Dispositivos com uma imagem do sistema Beta/Developer Preview

Consulte [a documentação do Google sobre o atestado SafetyNET](https://developer.android.com/training/safetynet/attestation) para obter detalhes técnicos.

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Configuração de atestado de dispositivo SafetyNet e a configuração ' dispositivos com jailbreak/raiz '
Google Play proteger as verificações de API do SafetyNet exigem que o usuário final esteja online, pelo menos durante o tempo em que o "ida e volta" para determinar os resultados do atestado é executado. Se o usuário final estiver offline, o administrador de ti ainda poderá esperar que um resultado seja imposto a partir da configuração de **dispositivos com jailbreak/raiz** . Dito isso, se o usuário final esteve offline demais, o valor do **período de carência offline** entra em cena e todo o acesso a dados corporativos ou de estudante é bloqueado quando o valor do temporizador é atingido, até que o acesso à rede esteja disponível. A ativação de ambas as configurações permite que uma abordagem em camadas Mantenha os dispositivos do usuário final íntegros, o que é importante quando os usuários finais acessam dados corporativos ou de estudante em dispositivos móveis.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play proteger APIs e Google Play Services
As configurações de política de proteção de aplicativo que aproveitam Google Play proteger APIs exigem Google Play Services para funcionar. As configurações de **atestado de dispositivo SafetyNET**e **verificação de ameaças em aplicativos** exigem a versão do Google determinada do Google Play Services para funcionar corretamente. Como essas são configurações que se enquadram na área de segurança, o usuário final será bloqueado se eles tiverem sido direcionados a essas configurações e não atenderem à versão apropriada do Google Play Services ou não tiverem acesso a Google Play Services.

## <a name="next-steps"></a>Próximos passos

[Como criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Consulte também
As aplicações de terceiros como a aplicação móvel do Salesforce funcionam com o Intune de formas específicas para proteger os dados empresariais. Para obter mais informações sobre como a aplicação Salesforce em particular funciona com o Intune (incluindo configurações de aplicações de MDM), veja [Aplicação Salesforce e Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
