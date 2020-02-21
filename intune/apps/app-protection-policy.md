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
ms.openlocfilehash: d2d8d50f7ac5d79d4d0081e7eee2169e9ff45d49
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512080"
---
# <a name="app-protection-policies-overview"></a>Descrição geral das políticas de proteção de aplicações

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As políticas de proteção de aplicações (APP) são regras que garantem que os dados de uma organização permanecem seguros ou contidos numa aplicação gerida. Uma política pode ser uma regra que é aplicada quando o utilizador tenta aceder ou mover dados "empresariais" ou um conjunto de ações que são proibidas ou monitorizadas quando um utilizador utiliza a aplicação. Uma aplicação gerida é uma aplicação que tem políticas de proteção de aplicações aplicadas à mesma e pode ser gerida pelo Intune.

As políticas de proteção de aplicações mobile Application Management (MAM) permitem-lhe gerir e proteger os dados da sua organização dentro de uma aplicação. Com a **MAM sem matrícula** (MAM-WE), uma aplicação relacionada com trabalho ou escola que contenha dados sensíveis pode ser gerida em quase todos os [dispositivos](app-management.md#app-management-capabilities-by-platform), incluindo dispositivos pessoais em cenários de **bring-your-own-device** (BYOD). Muitas aplicações de produtividade, como as aplicações do Microsoft Office, podem ser geridas pela MAM do Intune. Consulte a lista oficial de [aplicações protegidas](apps-supported-intune-apps.md) microsoft Intune disponíveis para uso público.

## <a name="how-you-can-protect-app-data"></a>Como pode proteger dados de aplicações
Os seus funcionários utilizam dispositivos móveis para tarefas pessoais e profissionais. Se, por um lado, quer garantir que os seus funcionários são produtivos, por outro, quer evitar a perda de dados, intencional e não intencional. Também irá querer proteger os dados da empresa que são acedidos a partir de dispositivos que não são geridos por si.

Pode utilizar as políticas de proteção de aplicações do Intune **independentemente de qualquer solução de gestão de dispositivos móveis (MDM)** . Esta independência ajuda-o a proteger dados da sua empresa com ou sem inscrição de dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

### <a name="app-protection-policies-on-devices"></a>Políticas de proteção de aplicações em dispositivos

As políticas de proteção de aplicações podem ser configuradas para aplicações executadas em dispositivos que estão:

- **Inscritos no Microsoft Intune:** estes dispositivos pertencem, normalmente, à empresa.

- **Inscritos numa solução de gestão de dispositivos móveis (MDM) de terceiros:** estes dispositivos pertencem, normalmente, à empresa.

  > [!NOTE]
  > As políticas de gestão de aplicações móveis não devem ser utilizadas com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

- Não inscrito em nenhuma solução de gestão de **dispositivos móveis:** Estes dispositivos são normalmente dispositivos de propriedade de funcionários que não são geridos ou matriculados em Intune ou outras soluções de MDM.

> [!IMPORTANT]
> Pode criar políticas de gestão de aplicações móveis para as aplicações móveis do Office que se ligam aos serviços do Office 365. Também pode proteger o acesso às caixas de correio no local através da criação de políticas de proteção de aplicações Intune para Outlook para iOS/iPadOS e Android habilitadas com autenticação moderna híbrida. Antes de utilizar esta funcionalidade, certifique-se de que cumpre o [Outlook para os requisitos iOS/iPadOS e Android.](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) As políticas de proteção de aplicações não são suportadas para outras aplicações que se ligam aos serviços do SharePoint ou do Exchange no local.

## <a name="benefits-of-using-app-protection-policies"></a>Benefícios da utilização de políticas de proteção de Aplicações

Os benefícios importantes da utilização das políticas de proteção da App são os seguintes:

- **Proteger os dados da sua empresa ao nível da aplicação.** Como a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

- **A produtividade dos utilizadores finais não é afetada e as políticas não se aplicam quando se utiliza a aplicação num contexto pessoal.** As políticas são aplicadas apenas num contexto profissional, o que lhe permite proteger os dados da empresa sem afetar os dados pessoais.

- **As políticas de proteção de aplicações asseguram-se de que as proteções da camada de aplicações estão em vigor.** Por exemplo, pode:
  - Exigir um PIN para abrir uma aplicação num contexto de trabalho 
  - Controlar a partilha de dados entre aplicações 
  - Impedir a gravação de dados empresariais da aplicação numa localização de armazenamento pessoal

- **O MDM, além do MAM, certifica-se**de que o dispositivo está protegido . Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

A utilização da MDM com políticas de proteção de aplicações tem outras vantagens e as empresas podem utilizar as políticas de proteção de aplicações com ou sem MDM ao mesmo tempo. Por exemplo, considere um funcionário que utiliza os um telemóvel atribuído pela empresa e o seu próprio tablet pessoal. O telemóvel da empresa está inscrito na MDM e protegido por políticas de proteção de aplicações, ao passo que o dispositivo pessoal está protegido apenas por políticas de proteção de aplicações.

Se aplicar uma política MAM ao utilizador sem definir o estado do dispositivo, o utilizador obterá a política MAM tanto no dispositivo BYOD como no dispositivo gerido por Intune. Também pode aplicar uma política de MAM baseada no estado gerido. Assim, quando criar uma política de proteção de aplicações, ao lado do Target para todos os tipos de **aplicações,** selecionaria **No**. Em seguida, faça qualquer um dos seguintes:
- Aplique uma política de MAM menos rigorosa aos dispositivos geridos intune e aplique uma política de MAM mais restritiva a dispositivos não inscritos em MDM.
- Aplicar uma política de MAM apenas a dispositivos não matriculados.

## <a name="supported-platforms-for-app-protection-policies"></a>Plataformas suportadas das políticas de proteção de aplicações

O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos nos quais quer executá-las. Para mais informações, consulte [as capacidades](app-management.md#app-management-capabilities-by-platform)de gestão da App por plataforma .

O suporte da plataforma de políticas de proteção de aplicações intune alinha-se com o suporte da plataforma de aplicações móveis office para dispositivos Android e iOS/iPadOS. Para obter detalhes, veja a secção **Aplicações móveis** de [Requisitos de Sistema do Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> O Portal da Empresa Intune é necessário no dispositivo para receber Políticas de Proteção de Aplicações no Android. Para obter mais informações, veja os [Requisitos das aplicações de acesso ao Portal da Empresa do Intune](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Como as políticas de proteção de aplicações protegem os dados das aplicações

### <a name="apps-without-app-protection-policies"></a>Aplicações sem políticas de proteção de aplicações

Quando as aplicações são utilizadas sem restrições, os dados pessoais e da empresa podem confundir-se. Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou ser transferidos para aplicações fora da sua competência e que resulta em perda de dados. As setas no diagrama seguinte mostram um movimento de dados ilimitado entre aplicações corporativas e pessoais, e para locais de armazenamento.

![Imagem conceptual do movimento de dados entre aplicações sem políticas em vigor](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Proteção de dados com políticas de proteção de aplicações (APP)

Pode utilizar políticas de proteção de Aplicações para evitar que os dados da empresa guardem para o armazenamento local do dispositivo (ver imagem abaixo). Também pode restringir o movimento de dados para outras aplicações que não estão protegidas pelas Políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de deslocalização de dados como **Guardar cópias de dados org**, e restringir **corte, cópia e pasta**.
- Definições de política de acesso, como **Exigir PIN simples para o acesso** e **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

![Imagem conceptual que mostra os dados da empresa a serem protegidos por políticas](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Proteção de dados com APP em dispositivos geridos por uma solução MDM

A ilustração abaixo mostra as camadas de proteção que as políticas de proteção de MDM e App oferecem em conjunto.

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos BYOD](./media/app-protection-policy/app-protection-policies-with-mdm.png)

A solução MDM acrescenta valor fornecendo o seguinte:

- Inscreve o dispositivo
- Implementa as aplicações no dispositivo
- Fornece gestão e conformidade dos dispositivos contínuas

As políticas de proteção da App acrescentam valor fornecendo o seguinte:

- Ajude a proteger os dados da empresa de fugas para aplicações e serviços de consumo
- Aplicar restrições como *save-as*, *clipboard,* ou *PIN*, a aplicações de clientes
- Limpe os dados da empresa quando necessário de apps sem remover essas aplicações do dispositivo

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Proteção de dados com APP para dispositivos sem matrícula

O diagrama que se segue ilustra como as políticas de proteção de dados funcionam ao nível da aplicação sem MDM.

![Imagem que mostra como as políticas de proteção de Aplicações funcionam em dispositivos sem inscrição (dispositivos não geridos)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

Nos dispositivos BYOD não inscritos em nenhuma solução de MDM, as políticas de proteção de aplicações podem ajudar a proteger os dados da empresa ao nível da aplicação.
No entanto, existem algumas limitações a ter em conta, tais como:

- Não pode implementar aplicações no dispositivo. O utilizador final tem de obter as aplicações na loja.
- Não pode aprovisionar perfis de certificado nestes dispositivos.
- Não pode aprovisionar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicações que pode gerir com as políticas de proteção de aplicações

Qualquer aplicação que tenha sido integrada com o [Intune SDK](../developer/app-sdk.md) ou embrulhada pela Ferramenta de Embrulho de [Aplicações Intune](../developer/apps-prepare-mobile-application-management.md) pode ser gerida usando políticas de proteção de aplicações Intune. Consulte a lista oficial de [aplicações protegidas](apps-supported-intune-apps.md) microsoft Intune que foram construídas usando estas ferramentas e estão disponíveis para uso público.

A equipa de desenvolvimento intune SDK testa e mantém ativamente o suporte para aplicações construídas com as plataformas nativas android, iOS/iPadOS (Obj-C, Swift), Xamarin, Xamarin.Forms e Cordova. Embora alguns clientes tenham tido sucesso com a integração do Intune SDK com outras plataformas, como o React Native e o NativeScript, não fornecemos orientação explícita ou plugins para desenvolvedores de aplicações usando qualquer outra coisa que não as nossas plataformas suportadas.

O [Intune SDK](../developer/app-sdk.md) utiliza algumas capacidades avançadas de autenticação moderna das Bibliotecas de[Autenticação de Diretórios Ativos Azure](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) tanto para a 1ª parte como para as versões 3ª do SDK. Como tal, a [Microsoft Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) não funciona bem com muitos dos nossos cenários fundamentais, como a autenticação no serviço de Proteção de Aplicações Intune e lançamento condicional. Dado que a orientação geral da equipa de Identidade da Microsoft é mudar para MSAL para todas as aplicações do Microsoft Office, o [Intune SDK](../developer/app-sdk.md) acabará por ter de apoiá-lo, mas não existem planos hoje.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Requisitos de utilizador final para usar políticas de proteção de aplicações

A lista que se segue fornece os requisitos do utilizador final para utilizar as políticas de proteção de aplicações numa aplicação gerida pelo Intune:

- O utilizador final tem de ter uma conta no Azure Active Directory (AAD). Veja [Adicionar utilizadores e conceder permissões administrativas no Intune](../fundamentals/users-add.md) para saber como criar utilizadores do Intune no Azure Active Directory.

- O utilizador final tem de ter uma licença para o Microsoft Intune atribuída à conta do Azure Active Directory dele. Veja [Gerir licenças do Intune](../fundamentals/licenses-assign.md) para saber como atribuir licenças do Intune aos utilizadores finais.

- O utilizador final tem de pertencer a um grupo de segurança visado por uma política de proteção de aplicações. A mesma política de proteção de aplicações tem de abranger a aplicação específica em utilização. As políticas de proteção de aplicações podem ser criadas e implementadas na consola do Intune, no [portal do Azure](https://portal.azure.com). Atualmente, os grupos de segurança podem ser criados no centro de administração da [Microsoft 365](https://admin.microsoft.com).

- O utilizador final tem de iniciar sessão na aplicação através da respetiva conta do AAD.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Políticas de proteção de aplicativos para aplicações do Microsoft Office

Existem alguns requisitos adicionais que pretende ter em conta ao utilizar políticas de proteção de Aplicações com aplicações do Microsoft Office.

### <a name="outlook-mobile-app"></a>Aplicação móvel Outlook
Os requisitos adicionais para utilizar a [aplicação móvel Outlook](https://products.office.com/outlook) incluem o seguinte:

- O utilizador final tem de ter a aplicação Outlook para dispositivos móveis instalada no dispositivo dele.
- O utilizador final tem de ter uma licença e uma caixa de correio do [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) associadas à conta do Azure Active Directory dele.

  >[!NOTE]
  > Atualmente, a aplicação Outlook para dispositivos móveis só suporta a Proteção de Aplicações do Intune para o Microsoft Exchange Online e o [Exchange Server com autenticação moderna híbrida](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) e não suporta o Exchange no Office 365 Dedicated.

### <a name="word-excel-and-powerpoint"></a>Palavra, Excel e PowerPoint
Os requisitos adicionais para utilizar as aplicações [Word, Excel e PowerPoint](https://products.office.com/business/office) incluem os seguintes:

- O utilizador final tem de ter uma licença do [Office 365 Empresas ou Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) associada à respetiva conta do Azure Active Directory. A subscrição tem de incluir as aplicações do Office para dispositivos móveis e pode incluir uma conta de armazenamento na cloud com o [OneDrive para Empresas](https://onedrive.live.com/about/business/). As licenças do Office 365 podem ser atribuídas no centro de administração da [Microsoft 365](https://admin.microsoft.com) seguindo estas [instruções](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- O utilizador final deve ter uma localização gerida configurada utilizando o ecorânico save como funcionalidade no âmbito da definição da política de proteção de aplicações "Guardar cópias de dados org". Por exemplo, se a localização gerida for o OneDrive, a aplicação [OneDrive](https://onedrive.live.com/about/) deverá ser configurada na aplicação Word, Excel ou PowerPoint do utilizador final.

- Se a localização gerida for o OneDrive, a aplicação terá de ser visada pela política de proteção de aplicações implementada para o utilizador final.

  >[!NOTE]
  > Atualmente, as aplicações do Office para dispositivos móveis só suportam o SharePoint Online e não o SharePoint no local.

### <a name="managed-location-needed-for-office"></a>Localização gerida necessária para o Office
É necessária uma localização gerida (ou seja, OneDrive) para o Office. Intune marca todos os dados da app como "corporativo" ou "pessoal". Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas).

### <a name="skype-for-business"></a>Skype para Empresas
Existem requisitos adicionais para usar o Skype para o Negócios. Veja os requisitos de licença do [Skype para Empresas](https://products.office.com/skype-for-business/it-pros). Para as configurações híbridas e no local do Skype para Empresas (SfB), veja [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (Autenticação Híbrida Moderna para SfB e o Exchange está em disponibilidade geral) e [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (Autenticação Moderna para SfB Local com o AAD), respetivamente.

## <a name="app-protection-global-policy"></a>Política Global de proteção de aplicações

Se um administrador da OneDrive procurar **admin.onedrive.com** e selecionar o acesso ao **Dispositivo,** pode definir os controlos de gestão de **aplicações móveis** para as aplicações de clientes OneDrive e SharePoint. 

As definições, disponibilizadas para a consola de administração do OneDrive, configuram uma política de proteção de aplicações do Intune especial denominada política **Global**. Esta política global aplica-se a todos os utilizadores no seu inquilino e não existe nenhuma forma de controlar a segmentação da política. 

Uma vez ativadas, as aplicações OneDrive e SharePoint para iOS/iPadOS e Android estão protegidas com as definições selecionadas por padrão. Um profissional de TI pode editar esta política na consola do Intune para adicionar mais aplicações segmentadas e para modificar qualquer definição de política. 

Por predefinição, só pode existir uma política **Global** por inquilino. No entanto, pode utilizar [Graph APIs do Intune](../developer/intune-graph-apis.md) para criar políticas globais adicionais por inquilino, mas não é recomendado. A criação de políticas globais adicionais não é recomendada, uma vez que resolver problemas relacionados com a implementação destas políticas pode tornar-se complicado.

Embora a política **Global** se aplique a todos os utilizadores no seu inquilino, qualquer política de proteção de aplicações padrão do Intune substituirá estas definições.

## <a name="app-protection-features"></a>Funcionalidades de proteção de aplicações

### <a name="multi-identity"></a>Várias identidades

O suporte multi-identidade permite que uma aplicação suporte a vários públicos. Estes públicos são utilizadores "corporativos" e utilizadores "pessoais". As contas de trabalho e escola são utilizadas por audiências "corporativas", enquanto as contas pessoais seriam utilizadas para o público dos consumidores, como os utilizadores do Microsoft Office. Uma aplicação que suporta multiidentidade pode ser divulgada publicamente, onde as políticas de proteção de aplicações só se aplicam quando a app é usada no contexto de trabalho e escola ("corporate") O suporte multi-identidade utiliza o [Intune SDK](../developer/app-sdk.md) para aplicar apenas políticas de proteção de aplicações no trabalho ou na conta escolar assinada saem na app. Se uma conta pessoal tiver sessão iniciada na aplicação, os dados permanecem inalterados.

Para um exemplo de contexto "pessoal", considere um utilizador que inicie um novo documento no Word, este é considerado contexto pessoal para que as políticas de Proteção de Aplicações Intune não sejam aplicadas. Assim que o documento for guardado na conta OneDrive "corporativa", então será considerado contexto "corporativo" e as políticas de Proteção de Aplicações Intune serão aplicadas.

Para um exemplo de trabalho ou contexto "corporativo", considere um utilizador que inicie a aplicação OneDrive utilizando a sua conta de trabalho. No contexto de trabalho, não pode mover ficheiros para uma localização de armazenamento pessoal. Posteriormente, quando utiliza o OneDrive com a sua conta pessoal, pode copiar e mover dados dos seus OneDrive pessoais, sem restrições.

O Outlook tem uma visão combinada de e-mail seletiva mente e-mail. Nesta situação, a aplicação Outlook solicita o Intune PIN no lançamento.

Para obter mais informações sobre multi-identidade em Intune, consulte [MAM e multi-identidade.](apps-supported-intune-apps.md)

### <a name="intune-app-pin"></a>Intune app PIN

O Número de Identificação Pessoal (PIN) é um código de acesso utilizado para verificar que o utilizador certo está a aceder aos dados da organização numa aplicação.

**Pedido PIN**<br>
O Intune só pede ao utilizador para introduzir o PIN da aplicação quando o mesmo quiser aceder aos dados "empresariais". Em aplicações multi-identidades como word, Excel ou PowerPoint, o utilizador é solicitado para o seu PIN quando tenta abrir um documento ou ficheiro "corporativo". Em aplicações de identidade única, como aplicações de linha de negócio geridas através da Ferramenta de Embrulho de [Aplicações Intune,](../developer/apps-prepare-mobile-application-management.md)o PIN é solicitado no lançamento, porque o [Intune SDK](../developer/app-sdk.md) sabe que a experiência do utilizador na app é sempre "corporativa".

**Pin prompt, ou aviso de credencial corporativa, frequência**<br>
O administrador de TI pode definir a definição da política de proteção de aplicações **Intune, reverificar os requisitos de acesso após (minutos)** na consola de administração Intune. Esta definição especifica o tempo até que os requisitos de acesso sejam verificados no dispositivo, e o ecrã PIN da aplicação, ou pedido de credencial corporativo, é novamente mostrado. Contudo, os detalhes importantes sobre o PIN que afetam a frequência de solicitação do utilizador incluem:

- **O PIN é partilhado entre apps da mesma editora para melhorar a usabilidade:**<br> No iOS/iPadOS, uma aplicação PIN é partilhada entre todas as aplicações **da mesma editora de aplicações.** Por exemplo, todas as aplicações da Microsoft partilham o mesmo PIN. No Android, um PIN da aplicação é partilhado entre todas as aplicações.
- **Verifique *os requisitos* de acesso após o comportamento após o reboot de um dispositivo:**<br> Um temporizador rastreia o número de minutos de inatividade que determinam quando mostrar o PIN da aplicação Intune, ou o pedido de credencial corporativo a seguir. No iOS/iPadOS, o temporizador não é afetado pelo reboot do dispositivo. Assim, o reboot do dispositivo não tem qualquer efeito no número de minutos em que o utilizador esteve inativo a partir de uma aplicação iOS/iPadOS com a política intune PIN (ou credencial corporativa) direcionada. No Android, o temporizador é reiniciado no reboot do dispositivo. Como tal, as aplicações Android com a política Intune PIN (ou credencial corporativa) provavelmente irão solicitar um PIN de aplicação, ou uma solicitação credencial corporativa, independentemente do 'Reverificar os requisitos de acesso após (minutos)' de definir o valor **após o reboot do dispositivo.**  
- **A natureza rolante do temporizador associado ao PIN:**<br> Uma vez introduzido um PIN para aceder a uma aplicação (app A), e a aplicação deixa o primeiro plano (foco principal de entrada) no dispositivo, o temporizador é reposto para esse PIN. Não será pedido nenhum PIN às aplicações (aplicação B) que partilhem este PIN, uma vez que o temporizador foi reposto. O pedido aparecerá novamente depois de o valor “Reverificar os requisitos de acesso após (minutos)” ter sido atingido.

Para dispositivos iOS/iPadOS, mesmo que o PIN seja partilhado entre aplicações de diferentes editoras, o pedido voltará a aparecer quando o **Recheck os requisitos de acesso após (minutos)** o valor for novamente satisfeito para a app que não é o principal foco de entrada. Por exemplo, um utilizador tem a aplicação _A_ do publicador _X_ e a aplicação _B_ do publicador _Y_ e essas duas aplicações partilham o mesmo PIN. O utilizador está concentrado na aplicação _A_ (primeiro plano) e a aplicação _B_ está minimizada. O PIN seria necessário depois de o valor **Reverificar os requisitos de acesso após (minutos)** ser alcançado e de o utilizador mudar para a aplicação _B_.

  >[!NOTE]
  > Para verificar os requisitos de acesso do utilizador com mais frequência (ou seja, o pedido de PIN), especialmente para uma aplicação utilizada com frequência, é recomendado reduzir o valor da definição “Reverificar os requisitos de acesso após (minutos)”.

**Aplicativo incorporado PINs para Outlook e OneDrive**<br>
O PIN Intune funciona com base num temporizador baseado em inatividade (o valor de **Reverificar os requisitos de acesso após (minutos)** ). Como tal, os pedidos de PIN do Intune são apresentados de forma independente dos pedidos de PIN de aplicação incorporados para o Outlook e OneDrive, que normalmente estão associados à inicialização da aplicação por predefinição. Se o utilizador receber ambos os pedidos de PIN ao mesmo tempo, o comportamento esperado deverá ser o de que o PIN do Intune tem precedência.

**Segurança PIN Intune**<br>
O PIN serve para garantir que só o utilizador correto consegue aceder aos dados da respetiva organização na aplicação. Por conseguinte, o utilizador final tem de iniciar sessão com a conta profissional ou escolar para poder definir ou repor o PIN da aplicação Intune. Esta autenticação é tratada pelo Azure Ative Directory através de uma troca segura de tokene e não é transparente para o [Intune SDK](../developer/app-sdk.md). No que diz respeito à segurança, a melhor forma de proteger os seus dados profissionais ou escolares é encriptá-los. A encriptação não está relacionada com o PIN da aplicação, mas é a própria política de proteção da aplicação.

**Proteger contra ataques de força bruta e o PIN Intune**<br>
Como parte da política de PIN da aplicação, o administrador de TI pode definir o número máximo de vezes que um utilizador pode tentar autenticar o respetivo PIN antes de bloquear a aplicação. Depois de o número de tentativas ter sido cumprido, o [Intune SDK](../developer/app-sdk.md) pode eliminar os dados "corporativos" da aplicação.

**PIN intonina e uma limpeza seletiva**<br>
No iOS/iPadOS, a informação pin de nível de aplicação é armazenada no porta-chaves que é partilhado entre apps com a mesma editora, como todas as aplicações da Microsoft de primeira parte. Esta informação PIN também está ligada a uma conta de utilizador final. Uma limpeza seletiva de uma aplicação não deve afetar uma aplicação diferente. 

Por exemplo, um conjunto PIN para o Outlook para o utilizador assinado é armazenado num porta-chaves partilhado. Quando o utilizador entrar no OneDrive (também publicado pela Microsoft), verá o mesmo PIN que o Outlook, uma vez que utiliza o mesmo porta-chaves partilhado. Ao assinar fora do Outlook ou limpar os dados do utilizador no Outlook, o Intune SDK não limpa esse porta-chaves porque o OneDrive ainda pode estar a utilizar esse PIN. Por isso, as toalhetes seletivas não limpam o porta-chaves partilhado, incluindo o PIN. Este comportamento permanece o mesmo mesmo, mesmo que exista apenas uma aplicação por uma editora no dispositivo. 

Uma vez que o PIN é partilhado entre aplicações com a mesma editora, se a limpeza for para uma única aplicação, o Intune SDK não sabe se existem outras aplicações no dispositivo com a mesma editora. Assim, o Intune SDK não limpa o PIN, uma vez que ainda pode ser utilizado para outras aplicações. A expectativa é que o PIN da aplicação seja apagado quando a última aplicação dessa editora for removida eventualmente como parte de alguma limpeza de OS.
 
Se observar o PIN a ser apagado em alguns dispositivos, é provável que o PIN esteja ligado a uma identidade, se o utilizador tiver assinado com uma conta diferente após uma limpeza, serão solicitados a introduzir um novo PIN. No entanto, se assinarem com uma conta anteriormente existente, um PIN armazenado no porta-chaves já pode ser utilizado para iniciar sessão.

**Definir um PIN duas vezes em aplicações da mesma editora?**<br>
O MAM (no iOS/iPadOS) permite atualmente pin de nível de aplicação com caracteres alfanuméricos e especiais (chamado 'código de acesso') que requer a participação de aplicações (isto é, WXP, Outlook, Managed Browser, Yammer) para integrar o [Intune SDK para iOS](../developer/app-sdk-ios.md). Caso contrário, as definições do código de acesso não são impostas corretamente nas aplicações visadas. Esta funcionalidade foi lançada com o SDK do Intune para iOS v. 7.1.12.

De forma a suportar esta funcionalidade e garantir a retrocompatibilidade com as versões anteriores do Intune SDK para iOS/iPadOS, todos os PINs (numérico ou código de acesso) em 7.1.12+ são manuseados separadamente do PIN numérico em versões anteriores do SDK. Como tal, se um dispositivo tiver aplicações com o SDK do Intune para versões do iOS anteriores à 7.1.12 E posteriores à 7.1.12 do mesmo publicador, terá de configurar dois PINs. Os dois PINs (para cada aplicação) não estão de forma alguma relacionados (ou seja, devem aderir à política de proteção de aplicações que é aplicada à aplicação). Como tal, *apenas* se as aplicações A e B tiverem as mesmas políticas aplicadas (no que diz respeito ao PIN), o utilizador pode configurar o mesmo PIN duas vezes. 

Este comportamento é específico do PIN nas aplicações iOS/iPadOS que estão ativadas com a Intune Mobile App Management. Com o passar do tempo, à medida que as aplicações adotam versões posteriores do Intune SDK para iOS/iPadOS, ter de definir um PIN duas vezes em aplicações da mesma editora torna-se menos um problema. Veja a nota abaixo para obter um exemplo.

  >[!NOTE]
  > Por exemplo, se a aplicação A for construída com uma versão anterior a 7.1.12 e a aplicação B for construída com uma versão maior ou igual a 7.1.12 da mesma editora, o utilizador final terá de configurar PINs separadamente para A e B se ambos estiverem instalados num dispositivo iOS/iPadOS.
  > Se uma aplicação C que tenha a versão SDK 7.1.9 estiver instalada no dispositivo, partilhará o mesmo PIN que a aplicação A. Uma aplicação D construída com 7.1.14 partilhará o mesmo PIN que a app B.  
  > Se apenas as aplicações A e C estiverem instaladas num dispositivo, será preciso definir um PIN. O mesmo se aplica se apenas as aplicações B e D estiverem instaladas num dispositivo.

### <a name="app-data-encryption"></a>Encriptação de dados de aplicativos
Os administradores de TI podem implementar uma política de proteção de aplicações que exija a encriptação dos dados da aplicação. Como parte da política, o administrador de TI também pode especificar a altura em que os conteúdos são encriptados.

**Como é que o processo de encriptação de dados intune**<br> Consulte as definições da política de proteção de [aplicações Android](app-protection-policy-settings-android.md) e as definições de políticas de proteção de [aplicações iOS/iPadOS](app-protection-policy-settings-ios.md) para obter informações detalhadas sobre a definição da política de proteção de aplicações de encriptação.

**Dados encriptados**<br>
Só os dados marcados como "empresariais" são encriptados de acordo com a política de proteção de aplicações do administrador de TI. Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, intune considera o seguinte como locais de negócio:

- E-mail (Troca) 
- Armazenamento em nuvem (aplicação OneDrive com uma conta OneDrive para negócios)

Para aplicações de linha de negócio geridas pela [Intune App Wrapping Tool,](../developer/apps-prepare-mobile-application-management.md)todos os dados da aplicação são considerados "corporativos".

### <a name="selective-wipe"></a>Eliminação seletiva

**Limpar remotamente os dados**<br>
Intune pode limpar os dados da aplicação de três maneiras diferentes: 
- Limpeza completa do dispositivo
- Limpeza seletiva para MDM 
- Limpeza seletiva MAM

Para obter mais informações sobre a limpeza remota da MDM, veja [Remove devices by using wipe or retire](../remote-actions/devices-wipe.md) (Remover dispositivos através da limpeza ou extinção). Para obter mais informações sobre a limpeza seletiva através da MAM, veja [a ação Extinguir](../remote-actions/devices-wipe.md#retire) e [Como eliminar apenas dados empresariais de aplicações](apps-selective-wipe.md).

[A limpeza total](../remote-actions/devices-wipe.md) do dispositivo remove todos os dados e definições do **utilizador do dispositivo,** restaurando o dispositivo às suas definições predefinidas de fábrica. O dispositivo é removido do Intune.

  >[!NOTE]
  > A limpeza completa do dispositivo e a limpeza seletiva para ODM só podem ser alcançadas em dispositivos matriculados na gestão de dispositivos móveis Intune (MDM).

**Limpeza seletiva para MDM**<br>
Veja a secção [Remover dispositivos – extinguir](../remote-actions/devices-wipe.md#retire) para ler mais sobre a remoção dos dados da empresa.

**Limpeza seletiva para MAM**<br>
A eliminação seletiva para MAM simplesmente remove os dados da aplicação da empresa de uma aplicação. O pedido é iniciado através do portal do Intune Azure. Para saber como iniciar um pedido de eliminação, veja o artigo [Como eliminar apenas os dados empresariais das aplicações](apps-selective-wipe.md).

Se o utilizador estiver a utilizar a aplicação quando for iniciada uma limpeza seletiva, o [Intune SDK](../developer/app-sdk.md) verifica a cada 30 minutos um pedido de limpeza seletivo do serviço Intune MAM. Também verifica a existência de pedidos de eliminação seletiva quando o utilizador inicia a aplicação pela primeira vez e inicia sessão com a conta profissional ou escolar.

**Quando os serviços On-Premises (on-prem) não funcionam com aplicações protegidas intune**<br>
A proteção de aplicações intonizada depende da identidade do utilizador para ser consistente entre a aplicação e o [Intune SDK](../developer/app-sdk.md). A única forma de o garantir é através da autenticação moderna. Existem cenários onde aplicações podem funcionar com uma configuração no local, mas não é garantido e nem consistente.

**Forma segura de abrir links web a partir de aplicações geridas**<br>
O administrador de TI pode implementar e definir a política de proteção de aplicações para a [aplicação Intune Managed Browser](app-configuration-managed-browser.md), um browser desenvolvido pelo Microsoft Intune que pode ser gerido facilmente com o Intune. O administrador de TI pode exigir que todas as ligações Web nas aplicações geridas pelo Intune sejam abertas através da aplicação Managed Browser.

## <a name="app-protection-experience-for-ios-devices"></a>Experiência de proteção de aplicativos para dispositivos iOS

### <a name="device-fingerprint-or-face-ids"></a>Impressões digitais do dispositivo ou iDs faciais 
As políticas de proteção de aplicações do Intune permitem o controlo sobre o acesso da aplicação apenas ao utilizador licenciado do Intune. Uma das formas de controlar o acesso à aplicação é exigir o Touch ID ou o Face ID da Apple nos dispositivos suportados. O Intune implementa um comportamento em que se houver qualquer alteração à base de dados biométricos do dispositivo, o Intune pede ao utilizador um PIN quando atingir o valor do tempo limite de inatividade seguinte. As alterações a dados biométricos incluem a adição ou remoção de uma impressão digital ou de um rosto. Se o utilizador do Intune não tiver um PIN definido, este é direcionado para configurar um PIN do Intune.
 
A intenção deste processo é continuar a manter os dados da sua organização dentro da app seguros e protegidos ao nível da aplicação. Esta funcionalidade só está disponível para iOS/iPadOS, e requer a participação de aplicações que integram o Intune SDK para iOS/iPadOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.
  
### <a name="ios-share-extension"></a>extensão de partilha iOS
Pode utilizar a extensão de partilha iOS/iPadOS para abrir o trabalho ou dados escolares em aplicações não geridas, mesmo com a política de transferência de dados definida apenas para **aplicações geridas** ou **sem aplicações.** A política de proteção de aplicações intonizada não pode controlar a extensão de partilha iOS/iPadOS sem gerir o dispositivo. Por isso, o _**Intune encripta os dados "empresariais" antes de estes serem partilhados fora da aplicação**_ . Pode validar este comportamento de encriptação tentando abrir um ficheiro "corporativo" fora da aplicação gerida. O ficheiro deverá estar encriptado, e não deverá ser possível abri-lo fora da aplicação gerida.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Múltiplas definições de acesso à proteção de aplicativos Intune para o mesmo conjunto de apps e utilizadores
As políticas de proteção de aplicações intonantes para acesso serão aplicadas numa ordem específica sobre dispositivos de utilizador final, uma vez que tentam aceder a uma aplicação direcionada a partir da sua conta corporativa. Em geral, uma limpeza teria precedência, seguida de um bloqueio e de um aviso que pode ser dispensado. Por exemplo, se aplicável ao utilizador/app específico, será aplicada uma definição mínima do sistema operativo iOS/iPadOS que avisa um utilizador para atualizar a sua versão iOS/iPadOS após a definição mínima do sistema operativo iOS/iPadOS que bloqueia o acesso ao utilizador. Portanto, no cenário em que o administrador de TI configura o sistema operativo iOS mínimo para 11.0.0.0 e o sistema operativo iOS mínimo (apenas Aviso) para 11.1.0.0, embora o dispositivo que tentava aceder à aplicação tivesse o iOS 10, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de sistema operativo iOS que resulta num bloqueio do acesso.

Ao lidar com diferentes tipos de configurações, um requisito de versão Intune SDK teria precedência, então um requisito de versão de aplicação, seguido pelo requisito da versão do sistema operativo iOS/iPadOS. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem. Recomendamos que o requisito da versão Intune SDK seja configurado apenas mediante orientação da equipa de produtos Intune para cenários essenciais de bloqueio.

## <a name="app-protection-experience-for-android-devices"></a>Experiência de proteção de aplicativos para dispositivos Android

### <a name="company-portal-app-and-intune-app-protection"></a>App Portal da Empresa e proteção de aplicativos Intune
Uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. Embora a aplicação Portal da Empresa seja sempre necessária, a inscrição de dispositivos _não é obrigatória_. Para a gestão de aplicações móveis sem matrícula (MAM-WE), o utilizador final apenas precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Múltiplas definições de acesso à proteção de aplicativos Intune para o mesmo conjunto de apps e utilizadores
As políticas de proteção de aplicações intonantes para acesso serão aplicadas numa ordem específica sobre dispositivos de utilizador final, uma vez que tentam aceder a uma aplicação direcionada a partir da sua conta corporativa. Em geral, um bloqueio teria precedência, seguido de um aviso que pode ser dispensado. Por exemplo, se aplicável ao utilizador/aplicação específico, uma definição mínima de versão de patch do Android que avisa um utilizador para atualizar o patch será aplicada após a definição mínima de versão de patch do Android bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura a versão mínima de patch do Android para 2018-03-01 e a versão mínima de patch do Android (apenas Aviso) para 2018-02-01, embora o dispositivo que tentava aceder à aplicação tivesse a versão de patch 2018-01-01, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de patch do Android que resulta num bloqueio do acesso. 

Ao lidar com diferentes tipos de definições, um requisito de versão de aplicação teria precedência, seguido do requisito de versão de sistema operativo Android e do requisito de versão de patch do Android. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Intune apps protection policies e A Natstation SafetyNet da Google para dispositivos Android 
As políticas de proteção de aplicações intune fornecem a capacidade para os administradores exigirem dispositivos de utilizador final para passar em Dispositivos Android SafetyNet da Google. Uma nova determinação do serviço Google Play será reportada ao administrador de TI num intervalo determinado pelo serviço Intune. A frequência com que a chamada de serviço é feita é acelerada devido à carga, pelo que este valor é mantido internamente e não é configurável. Qualquer ação configurada por TI para a definição de Attestation Google SafetyNet será tomada com base no último resultado reportado ao serviço Intune no momento do lançamento condicional. Caso não existam dados, o acesso será permitido dependendo de nenhuma outra verificação de lançamento condicional falhando, e o Google Play Service "trip" para determinar os resultados da atesta começará no backend e solicitará ao utilizador assincronicamente se o dispositivo tiver falhado. Se houver dados antigos, o acesso será bloqueado ou permitido dependendo do último resultado reportado, e da mesma forma, uma "ida e volta" do Serviço Google Play para determinar os resultados da atesta começará e solicitará ao utilizador assincronicamente se o dispositivo tiver falhado.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Intune apps protection policies e Google's Check Apps API para dispositivos Android
As Políticas de Proteção de Aplicações Intune fornecem a capacidade para os administradores exigirem que dispositivos de utilizador final enviem sinais através da API de Aplicações de Verificação da Google para dispositivos Android. As instruções sobre como fazê-lo variam ligeiramente por dispositivo. O processo geral envolve ir à Google Play Store, clicando depois nas **minhas aplicações e jogos,** clicando no resultado da última pesquisa de aplicações que o levará ao menu Play Protect. Certifique-se de que o **dispositivo Desativação para ameaças** de segurança está ligado.

### <a name="googles-safetynet-attestation-api"></a>API de Attestation SafetyNet da Google 
Intune aproveita as APIs do Google Play Protect SafetyNet para adicionar aos nossos controlos de deteção de raízes existentes para dispositivos não matriculados. A Google desenvolveu e manteve este conjunto de API para as aplicações Android adotarem se não quiserem que as suas aplicações sejam executadas em dispositivos enraizados. A aplicação Android Pay incorporou isto, por exemplo. Embora a Google não partilhe publicamente a totalidade das verificações de deteção de raízes que ocorrem, esperamos que estas APIs detetem utilizadores que tenham enraizado os seus dispositivos. Estes utilizadores podem então ser impedidos de aceder, ou as suas contas corporativas eliminadas das suas aplicações ativadas pela política. **Verifique a integridade básica** que lhe diz sobre a integridade geral do dispositivo. Dispositivos enraizados, emuladores, dispositivos virtuais e dispositivos com sinais de adulteração falham a integridade básica. Verifique a **integridade básica e os dispositivos certificados** contam-lhe sobre a compatibilidade do dispositivo com os serviços da Google. Apenas dispositivos não modificados certificados pela Google podem passar este cheque. Os dispositivos que falharão incluem o seguinte:

- Dispositivos que falham na integridade básica
- Dispositivos com um bootloader desbloqueado
- Dispositivos com uma imagem/ROM do sistema personalizado
- Dispositivos para os quais o fabricante não se candidatou, ou passou, certificação da Google
- Dispositivos com uma imagem de sistema construída diretamente a partir dos ficheiros de origem do Android Open Source Program
- Dispositivos com uma imagem do sistema de pré-visualização beta/desenvolvedor

Consulte [a documentação da Google sobre o Atestado SafetyNet](https://developer.android.com/training/safetynet/attestation) para obter detalhes técnicos.

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Definição de atestado do dispositivo SafetyNet e a definição de "dispositivos encadeçados/enraizados"
As verificações da API SafetyNet da Google Play Protect exigem que o utilizador final esteja online, pelo menos durante o tempo em que a "viagem de ida e volta" para determinar os resultados da atesta executa. Se o utilizador final estiver offline, a administração de TI ainda pode esperar que um resultado seja aplicado a partir da definição de **dispositivos encadedados/enraizados.** Dito isto, se o utilizador final estiver offline há demasiado tempo, o valor do período de **carência offline** entra em vigor, e todo o acesso ao trabalho ou aos dados escolares é bloqueado assim que esse valor do temporizador for atingido, até que o acesso à rede esteja disponível. Ligar ambas as definições permite uma abordagem em camadas para manter os dispositivos de utilizador final saudáveis, o que é importante quando os utilizadores finais acedem ao trabalho ou aos dados escolares no telemóvel.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play Protect APIs e Google Play Services
As definições de política de proteção de aplicações que alavancam as APIs do Google Play Protect exigem que os Serviços de Reprodução do Google funcionem. Tanto o **atestado safetyNet**como a **análise de ameaças nas** definições de apps exigem que a versão determinada do Google Play Services funcione corretamente. Uma vez que estas são configurações que caem na área de segurança, o utilizador final será bloqueado se tiver sido alvo destas definições e não estiver a cumprir a versão adequada dos Serviços Google Play ou não tiver acesso aos Serviços de Reprodução do Google.

## <a name="next-steps"></a>Próximos passos

[Como criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)

[Definições de política de proteção de aplicativos Android disponíveis com microsoft Intune](app-protection-policy-settings-android.md)

[Definições de política de proteção de aplicações iOS/iPadOS disponíveis com microsoft Intune](app-protection-policy-settings-ios.md)

## <a name="see-also"></a>Veja também
As aplicações de terceiros como a aplicação móvel do Salesforce funcionam com o Intune de formas específicas para proteger os dados empresariais. Para obter mais informações sobre como a aplicação Salesforce em particular funciona com o Intune (incluindo configurações de aplicações de MDM), veja [Aplicação Salesforce e Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
