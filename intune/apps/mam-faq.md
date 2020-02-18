---
title: Perguntas mais frequentes sobre a MAM e a proteção de aplicações
description: Este artigo apresenta respostas a algumas das perguntas mais frequentes acerca da gestão de aplicações móveis do Intune (MAM) e da proteção de aplicações do Intune.
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
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c40d9ef61493f084048ca277a6f54bdf5238f31a
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414391"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Perguntas mais frequentes sobre a MAM e a proteção de aplicações

Este artigo apresenta respostas a algumas das perguntas mais frequentes acerca da gestão de aplicações móveis do Intune (MAM) e da proteção de aplicações do Intune.

## <a name="mam-basics"></a>Noções básicas da MAM

**O que é a MAM?**<br></br>
A [gestão de aplicações móveis do Intune](app-lifecycle.md) refere-se ao conjunto de funcionalidades de gestão do Intune que lhe permite publicar, emitir via push, configurar, proteger, monitorizar e atualizar aplicações móveis para os seus utilizadores.

**Quais são as vantagens da proteção de aplicações da MAM?**<br></br>
A MAM protege os dados de uma empresa dentro da aplicação. Com a MAM sem inscrição (MAM-WE), pode gerir uma aplicação relacionada com o trabalho ou com a escola que contenha dados confidenciais na maioria dos dispositivos, incluindo os dispositivos pessoais, em cenários BYOD (Bring Your Own Device). Muitas aplicações de produtividade, como as aplicações do Microsoft Office, podem ser geridas pela MAM do Intune. Veja a lista oficial das [aplicações geridas pelo Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponíveis para utilização pública.

**Que configurações de dispositivos suporta a MAM?**<br></br>
A MAM do Intune suporta dois tipos de configurações:
- **Intune MDM + MAM**: os administradores de TI só podem gerir as aplicações através da MAM e das políticas de proteção de aplicações em dispositivos que estejam inscritos na gestão de dispositivos móveis do Intune (MDM). Para gerir aplicações com a MDM + MAM, os clientes devem utilizar a consola do Intune no portal do Azure em https://portal.azure.com.

- **MAM sem inscrição de dispositivos**: a MAM sem inscrição de dispositivos, ou MAM-WE, permite aos administradores de TI gerir as aplicações com a MAM e as políticas de proteção de aplicações nos dispositivos que não estejam inscritos na MDM do Intune. Isto significa que as aplicações podem ser geridas pelo Intune em dispositivos inscritos em fornecedores de EMM terceiros. Para gerir aplicações utilizando mAM-WE, os clientes devem utilizar a consola Intune no portal Azure em [https://portal.azure.com](https://portal.azure.com). Além disso, as aplicações podem ser geridas pelo Intune nos dispositivos inscritos em fornecedores de Gestão de Mobilidade da Empresa (EMM) de terceiros ou não inscritos numa MDM.


## <a name="app-protection-policies"></a>Políticas de proteção de aplicações

**O que são as políticas de proteção de aplicações?**<br></br>
As políticas de proteção de aplicações são regras que asseguram que os dados de uma organização continuam seguros ou protegidos numa aplicação gerida. Uma política pode ser uma regra que é aplicada quando o utilizador tenta aceder ou mover dados "empresariais" ou um conjunto de ações que são proibidas ou monitorizadas quando um utilizador utiliza a aplicação.

**Quais são os exemplos das políticas de proteção de aplicações?**<br></br>
Veja as [definições da política de proteção de aplicações para Android](app-protection-policy-settings-android.md) e as [definições da política de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) para obter informações detalhadas acerca de cada definição da política de proteção de aplicações.

**É possível ter as políticas de MDM e MAM aplicadas ao mesmo utilizador ao mesmo tempo, para diferentes dispositivos? Por exemplo, se um utilizador puder aceder aos seus recursos de trabalho a partir da sua própria máquina ativada por MAM, mas também venha trabalhar e utilizar um dispositivo gerido por MDM intune. Há alguma ressalva nesta ideia?**<br></br>
Se aplicar uma política MAM ao utilizador sem definir o estado do dispositivo, o utilizador obterá a política MAM tanto no dispositivo BYOD como no dispositivo gerido por Intune. Também pode aplicar uma política de MAM baseada no estado gerido. Por isso, quando criar uma política de proteção de aplicações, ao lado do Target para todos os tipos de aplicações, selecionaria O. Em seguida, faça qualquer um dos seguintes:
- Aplique uma política de MAM menos rigorosa aos dispositivos geridos intune e aplique uma política de MAM mais restritiva a dispositivos não inscritos em MDM.
- Aplicar uma política de MAM apenas a dispositivos não matriculados.

Para mais informações, consulte como monitorizar as políticas de [proteção de aplicações](app-protection-policies-monitor.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicações que pode gerir com as políticas de proteção de aplicações

**Que aplicações podem ser geridas pelas políticas de proteção de aplicações?**<br></br>
Qualquer aplicação que tenha sido integrada com o [SDK da Aplicação Intune](../developer/app-sdk.md) ou encapsulada pela [Ferramenta de Encapsulamento de Aplicações do Intune](../developer/apps-prepare-mobile-application-management.md) pode ser gerida com as políticas de proteção de aplicações do Intune. Veja a lista oficial das [aplicações geridas pelo Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponíveis para utilização pública.

**Quais são os requisitos base para utilizar as políticas de proteção de aplicações numa aplicação gerida pelo Intune?**

- O utilizador final tem de ter uma conta no Azure Active Directory (AAD). Veja [Adicionar utilizadores e conceder permissões administrativas no Intune](../fundamentals/users-add.md) para saber como criar utilizadores do Intune no Azure Active Directory.

- O utilizador final tem de ter uma licença para o Microsoft Intune atribuída à conta do Azure Active Directory dele. Veja [Gerir licenças do Intune](../fundamentals/licenses-assign.md) para saber como atribuir licenças do Intune aos utilizadores finais.

- O utilizador final tem de pertencer a um grupo de segurança visado por uma política de proteção de aplicações. A mesma política de proteção de aplicações tem de abranger a aplicação específica em utilização. As políticas de proteção de aplicações podem ser criadas e implementadas na consola do Intune, no [portal do Azure](https://portal.azure.com). Atualmente, os grupos de segurança podem ser criados no centro de administração da [Microsoft 365](https://admin.microsoft.com).

- O utilizador final tem de iniciar sessão na aplicação através da respetiva conta do AAD.

**E se eu quiser ativar uma aplicação com Intune App Protection mas não está a usar uma plataforma de desenvolvimento de aplicações suportada?**

A equipa de desenvolvimento intune SDK testa e mantém ativamente o suporte para aplicações construídas com as plataformas nativas do Android, iOS (Obj-C, Swift), Xamarin, Xamarin.Forms e Cordova. Embora alguns clientes tenham tido sucesso com a integração do Intune SDK com outras plataformas, como o React Native e o NativeScript, não fornecemos orientação explícita ou plugins para desenvolvedores de aplicações usando qualquer outra coisa que não as nossas plataformas suportadas.

**O SDK da APLICAÇÃO Intune suporta a Biblioteca de Autenticação da Microsoft (MSAL) ou contas de redes sociais?**<br></br>
O SDK da APLICAÇÃO do Intune utiliza algumas funcionalidades ADAL avançadas para as versões originais e de terceiros do SDK. Como tal, a MSAL não funciona corretamente com muitos dos nossos cenários principais, como a autenticação no serviço de Proteção de Aplicações do Intune e na iniciação condicional. Dado que a orientação geral da equipa de Identidade da Microsoft é mudar para MSAL para todas as aplicações do Microsoft Office, o Intune SDK acabará por ter de apoiá-lo, mas não existem planos hoje.

**Quais são os requisitos adicionais para utilizar a [aplicação Outlook para dispositivos móveis](https://products.office.com/outlook)?**

- O utilizador final tem de ter a aplicação Outlook para dispositivos móveis instalada no dispositivo dele.

- O utilizador final tem de ter uma licença e uma caixa de correio do [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) associadas à conta do Azure Active Directory dele.

  >[!NOTE]
  > Atualmente, a aplicação Outlook para dispositivos móveis só suporta a Proteção de Aplicações do Intune para o Microsoft Exchange Online e o [Exchange Server com autenticação moderna híbrida](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) e não suporta o Exchange no Office 365 Dedicated.

**Quais são os requisitos adicionais para utilizar as [aplicações Word, Excel e PowerPoint](https://products.office.com/business/office)?**

- O utilizador final tem de ter uma licença do [Office 365 Empresas ou Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) associada à respetiva conta do Azure Active Directory. A subscrição tem de incluir as aplicações do Office para dispositivos móveis e pode incluir uma conta de armazenamento na cloud com o [OneDrive para Empresas](https://onedrive.live.com/about/business/). As licenças do Office 365 podem ser atribuídas no centro de administração da [Microsoft 365](https://admin.microsoft.com) seguindo estas [instruções](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- O utilizador final deve ter uma localização gerida configurada utilizando o ecorânico save como funcionalidade no âmbito da definição da política de proteção de aplicações "Guardar cópias de dados org". Por exemplo, se a localização gerida for o OneDrive, a aplicação [OneDrive](https://onedrive.live.com/about/) deverá ser configurada na aplicação Word, Excel ou PowerPoint do utilizador final.

- Se a localização gerida for o OneDrive, a aplicação terá de ser visada pela política de proteção de aplicações implementada para o utilizador final.

  >[!NOTE]
  > Atualmente, as aplicações do Office para dispositivos móveis só suportam o SharePoint Online e não o SharePoint no local.

**Por que motivo é preciso uma localização gerida (como o OneDrive) para o Office?**<br></br>
O Intune marca todos os dados na aplicação como "empresariais" ou "pessoais". Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas).

**Quais são os requisitos adicionais para utilizar o Skype para Empresas?**<br></br>
Veja os requisitos de licença do [Skype para Empresas](https://products.office.com/skype-for-business/it-pros). Para as configurações híbridas e no local do Skype para Empresas (SfB), veja [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (Autenticação Híbrida Moderna para SfB e o Exchange está em disponibilidade geral) e [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (Autenticação Moderna para SfB Local com o AAD), respetivamente.

## <a name="app-protection-features"></a>Funcionalidades de proteção de aplicações

**O que é o suporte de identidades múltiplas?**<br></br>
O suporte de identidades múltiplas é a capacidade do SDK da Aplicação Intune de só aplicar as políticas de proteção de aplicações à conta profissional ou escolar que tenha sessão iniciada na aplicação. Se uma conta pessoal tiver sessão iniciada na aplicação, os dados permanecem inalterados.

**Qual é o objetivo do suporte de identidades múltiplas?**<br></br>
O suporte de identidades múltiplas permite que as aplicações com públicos "empresariais" e consumidores (por exemplo, as aplicações do Office) sejam lançadas publicamente com as funcionalidades de proteção de aplicações do Intune para as contas "empresariais".

**E o Outlook e as identidades múltiplas?**<br></br>
Uma vez que o Outlook tem uma vista combinada dos e-mails pessoais e "empresariais", a aplicação Outlook pede o PIN do Intune quando é iniciada.

**O que é o PIN da aplicação Intune?**<br></br>
O Número de Identificação Pessoal (PIN) é um código de acesso utilizado para verificar que o utilizador certo está a aceder aos dados da organização numa aplicação.

- **Quando é pedido ao utilizador para introduzir o PIN?**<br></br> O Intune só pede ao utilizador para introduzir o PIN da aplicação quando o mesmo quiser aceder aos dados "empresariais". Em aplicações de identidades múltiplas como o Word/Excel/PowerPoint, é pedido ao utilizador que introduza o PIN ao tentar abrir um documento ou ficheiro "empresarial". Em aplicações de identidade única, como as aplicações de linha de negócio geridas com a Ferramenta de Encapsulamento de Aplicações do Intune, o PIN é pedido no início, uma vez que o SDK da Aplicação Intune reconhece que a experiência do utilizador na aplicação é sempre "empresarial".

- **Com que frequência será pedido ao utilizador para introduzir o PIN do Intune?**<br></br> O administrador de TI pode configurar a definição“Reverificar os requisitos de acesso após (minutos)” da política de proteção de aplicações do Intune na consola de administração do Intune. Esta definição especifica o período de tempo antes da verificação dos requisitos de acesso no dispositivo e de uma nova apresentação do ecrã de PIN da aplicação. Contudo, os detalhes importantes sobre o PIN que afetam a frequência de solicitação do utilizador incluem: 

  - **O PIN é partilhado entre as aplicações do mesmo publicador para melhorar a facilidade de utilização:** no iOS, o PIN de uma aplicação é partilhado entre todas as aplicações **do mesmo publicador**. No Android, um PIN da aplicação é partilhado entre todas as aplicações.
  - **O comportamento "Reverificar os requisitos de acesso após (minutos)" depois de um reinício de dispositivo:** um "temporizador do PIN" controla o número de minutos de inatividade que determina quando mostrar novamente o PIN da aplicação do Intune. No iOS, o temporizador do PIN não é afetado pelo reinício do dispositivo. Desta forma, o reinício do dispositivo não afeta o número de minutos que o utilizador esteve inativo numa aplicação iOS que tenha a política de PIN do Intune. No Android, o temporizador do PIN é reposto ao reiniciar o dispositivo. Como tal, é provável que as aplicações Android com a política de PIN do Intune peçam um PIN da aplicação, independentemente do valor definido na opção "Reverificar os requisitos de acesso após (minutos)" **após reiniciar o dispositivo**.  
  - **A natureza flexível do temporizador associado ao PIN:** após introduzir um PIN para aceder a uma aplicação (aplicação A) e esta sair de primeiro plano (foco de introdução principal) no dispositivo, o temporizador deste PIN é reposto. Não será pedido nenhum PIN às aplicações (aplicação B) que partilhem este PIN, uma vez que o temporizador foi reposto. O pedido aparecerá novamente depois de o valor “Reverificar os requisitos de acesso após (minutos)” ter sido atingido.

No caso dos dispositivos iOS, mesmo que o PIN seja partilhado entre aplicações de diferentes publicadores, o pedido aparecerá novamente quando o valor **Reverificar os requisitos de acesso após (minutos)** for alcançado novamente para a aplicação que não é o foco de introdução principal. Por exemplo, um utilizador tem a aplicação _A_ do publicador _X_ e a aplicação _B_ do publicador _Y_ e essas duas aplicações partilham o mesmo PIN. O utilizador está concentrado na aplicação _A_ (primeiro plano) e a aplicação _B_ está minimizada. O PIN seria necessário depois de o valor **Reverificar os requisitos de acesso após (minutos)** ser alcançado e de o utilizador mudar para a aplicação _B_.

  >[!NOTE] 
  > Para verificar os requisitos de acesso do utilizador com mais frequência (ou seja, o pedido de PIN), especialmente para uma aplicação utilizada com frequência, é recomendado reduzir o valor da definição “Reverificar os requisitos de acesso após (minutos)”. 
      
- **Como é que o PIN do Intune funciona com PINs de aplicação incorporados para o Outlook e OneDrive?**<br></br>
O PIN Intune funciona com base num temporizador baseado na inatividade (o valor de 'Reverificar os requisitos de acesso após (minutos)'). Como tal, os pedidos de PIN do Intune são apresentados de forma independente dos pedidos de PIN de aplicação incorporados para o Outlook e OneDrive, que normalmente estão associados à inicialização da aplicação por predefinição. Se o utilizador receber ambos os pedidos de PIN ao mesmo tempo, o comportamento esperado deverá ser o de que o PIN do Intune tem precedência. 

- **O PIN é seguro?**<br></br> O PIN serve para garantir que só o utilizador correto consegue aceder aos dados da respetiva organização na aplicação. Por conseguinte, o utilizador final tem de iniciar sessão com a conta profissional ou escolar para poder definir ou repor o PIN da aplicação Intune. Esta autenticação é processada pelo Azure Active Directory através de uma troca de tokens segura e não é revelada ao SDK da Aplicação Intune. No que diz respeito à segurança, a melhor forma de proteger os seus dados profissionais ou escolares é encriptá-los. A encriptação não está relacionada com o PIN da aplicação, mas é a própria política de proteção da aplicação.

- **Como é que o Intune protege o PIN contra ataques de força bruta?**<br></br> Como parte da política de PIN da aplicação, o administrador de TI pode definir o número máximo de vezes que um utilizador pode tentar autenticar o respetivo PIN antes de bloquear a aplicação. Após esgotar o número de tentativas, o SDK da Aplicação Intune pode eliminar os dados "empresariais" na aplicação.
  
- **Por que motivo tenho de definir um PIN duas vezes em aplicações do mesmo publicador?**<br></br> O MAM (no iOS) permite atualmente pin de nível de aplicação com caracteres alfanuméricos e especiais (chamado 'código de acesso') que requer a participação de aplicações (isto é, WXP, Outlook, Managed Browser, Yammer) para integrar o Intune APP SDK para iOS/iPadOS. Caso contrário, as definições do código de acesso não são impostas corretamente nas aplicações visadas. Esta funcionalidade foi lançada com o SDK do Intune para iOS v. 7.1.12. <br><br> Para suportar esta funcionalidade e garantir a retrocompatibilidade com versões anteriores do SDK do Intune para iOS, todos os PINs (numéricos ou códigos de acesso) na versão 7.1.12 ou superior são processados em separado do PIN numérico em versões anteriores do SDK. Como tal, se um dispositivo tiver aplicações com o SDK do Intune para versões do iOS anteriores à 7.1.12 E posteriores à 7.1.12 do mesmo publicador, terá de configurar dois PINs. <br><br> Porém, os dois PINs (para cada aplicação) não estão relacionados de forma alguma, ou seja, têm de respeitar a política de proteção de aplicações que é aplicada à aplicação. Como tal, *só* se as aplicações A e B tiverem as mesmas políticas aplicadas (no que respeita ao PIN) é que o utilizador poderá configurar o mesmo PIN duas vezes. <br><br> Este comportamento é específico para o PIN em aplicações iOS com a Gestão de Aplicações Móveis do Intune ativada. Ao longo do tempo, como as aplicações adotam versões posteriores do SDK do Intune para iOS, ter de definir um PIN duas vezes em aplicações do mesmo publicador deixa de ser um problema. Veja a nota abaixo para obter um exemplo.

  >[!NOTE]
  > Por exemplo, se a aplicação A tiver sido concebida com uma versão anterior à 7.1.12 e a aplicação B tiver sido concebida com uma versão igual ou superior à 7.1.12 do mesmo publicador, o utilizador final terá de configurar PINs em separado para A e B se ambas estiverem instaladas num dispositivo iOS. <br><br> Se uma aplicação C que tem o SDK versão 7.1.9 estiver instalada no dispositivo, partilhará o mesmo PIN da aplicação A. <br><br> Uma aplicação D concebida com a versão 7.1.14 partilhará o mesmo PIN da aplicação B. <br><br> Se apenas as aplicações A e C estiverem instaladas num dispositivo, será preciso definir um PIN. O mesmo se aplica se apenas as aplicações B e D estiverem instaladas num dispositivo.

**E a encriptação?**<br></br>
Os administradores de TI podem implementar uma política de proteção de aplicações que exija a encriptação dos dados da aplicação. Como parte da política, o administrador de TI também pode especificar a altura em que os conteúdos são encriptados.

- **Como é que o Intune encripta os dados?**<br></br> Veja as [definições da política de proteção de aplicações para Android](app-protection-policy-settings-android.md) e as [definições da política de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) para obter informações detalhadas sobre a definição de encriptação da política de proteção de aplicações.

- **O que é encriptado?**<br></br> Só os dados marcados como "empresariais" são encriptados de acordo com a política de proteção de aplicações do administrador de TI. Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas). Para aplicações de linha de negócio geridas com a Ferramenta de Encapsulamento de Aplicações do Intune, todos os dados da aplicação são considerados "empresariais".

**Como é que o Intune elimina os dados remotamente?**<br></br>
O Intune pode eliminar os dados da aplicação de três formas diferentes: eliminação total do dispositivo, eliminação seletiva para MDM e eliminação seletiva MAM. Para obter mais informações sobre a limpeza remota da MDM, veja [Remove devices by using wipe or retire](../remote-actions/devices-wipe.md) (Remover dispositivos através da limpeza ou extinção). Para obter mais informações sobre a limpeza seletiva através da MAM, veja [a ação Extinguir](../remote-actions/devices-wipe.md#retire) e [Como eliminar apenas dados empresariais de aplicações](apps-selective-wipe.md).

- **O que é a limpeza?**<br></br> A [limpeza](../remote-actions/devices-wipe.md) elimina todas as definições e dados dos utilizadores do **dispositivo** ao restaurar o dispositivo para as predefinições de fábrica. O dispositivo é removido do Intune.
  >[!NOTE]
  > A limpeza só pode ser realizada em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune.

- **O que é uma eliminação seletiva para MDM?**<br></br> Veja a secção [Remover dispositivos – extinguir](../remote-actions/devices-wipe.md#retire) para ler mais sobre a remoção dos dados da empresa.

- **O que é uma eliminação seletiva para MAM?**<br></br> A eliminação seletiva para MAM simplesmente remove os dados da aplicação da empresa de uma aplicação. O pedido é iniciado através do portal do Intune Azure. Para saber como iniciar um pedido de eliminação, veja o artigo [Como eliminar apenas os dados empresariais das aplicações](apps-selective-wipe.md).

- **Qual é a velocidade da eliminação seletiva para MAM?**<br></br> Se o utilizador estiver a utilizar a aplicação quando a eliminação seletiva for iniciada, o SDK da Aplicação Intune verifica a existência de pedidos de eliminação seletiva a cada 30 minutos a partir do serviço MAM do Intune. Também verifica a existência de pedidos de eliminação seletiva quando o utilizador inicia a aplicação pela primeira vez e inicia sessão com a conta profissional ou escolar.

**Por que razão os serviços no local não funcionam com as aplicações protegidas pelo Intune?**<br></br>
A proteção de aplicações do Intune depende da identidade do utilizador para ser consistente entre a aplicação e o SDK da Aplicação Intune. A única forma de o garantir é através da autenticação moderna. Existem cenários onde aplicações podem funcionar com uma configuração no local, mas não é garantido e nem consistente.

**Existe uma forma segura de abrir ligações Web a partir de aplicações geridas?**<br></br>
Sim! O administrador de TI pode implementar e definir a política de proteção de aplicações para a [aplicação Intune Managed Browser](../apps/app-configuration-managed-browser.md), um browser desenvolvido pelo Microsoft Intune que pode ser gerido facilmente com o Intune. O administrador de TI pode exigir que todas as ligações Web nas aplicações geridas pelo Intune sejam abertas através da aplicação Managed Browser.

## <a name="app-experience-on-android"></a>Experiência de aplicação em Android

**Por que razão é que a aplicação Portal da Empresa precisa da proteção de aplicações do Intune para funcionar em dispositivos Android?**<br></br>
Uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. Embora a aplicação Portal da Empresa seja sempre necessária, a inscrição de dispositivos _não é obrigatória_. Para a MAM-WE, o utilizador final apenas precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

**Como é que múltiplas definições de acesso de proteção de aplicações do Intune configuradas para o mesmo conjunto de aplicações e utilizadores funcionam no Android?**<br></br>
As políticas de proteção de aplicações do Intune para acesso serão aplicadas numa ordem específica nos dispositivos dos utilizadores finais à medida que tentam aceder a uma aplicação direcionada a partir da respetiva conta empresarial. Em geral, um bloqueio teria precedência, seguido de um aviso que pode ser dispensado. Por exemplo, se aplicável ao utilizador/aplicação específico, uma definição mínima de versão de patch do Android que avisa um utilizador para atualizar o patch será aplicada após a definição mínima de versão de patch do Android bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura a versão mínima de patch do Android para 2018-03-01 e a versão mínima de patch do Android (apenas Aviso) para 2018-02-01, embora o dispositivo que tentava aceder à aplicação tivesse a versão de patch 2018-01-01, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de patch do Android que resulta num bloqueio do acesso. 

Ao lidar com diferentes tipos de definições, um requisito de versão de aplicação teria precedência, seguido do requisito de versão de sistema operativo Android e do requisito de versão de patch do Android. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem.

**As Políticas de Proteção de Aplicações Intune fornecem a capacidade para os administradores exigirem que os dispositivos de utilizador final passem o Atestado SafetyNet da Google para dispositivos Android. Quantas vezes é enviado um novo resultado da SafetyNet Attestation para o serviço?** <br><br> Uma nova determinação do serviço Google Play será reportada ao administrador de TI num intervalo determinado pelo serviço Intune. A frequência com que a chamada de serviço é feita é acelerada devido à carga, pelo que este valor é mantido internamente e não é configurável. Qualquer ação configurada por TI para a definição de Attestation Google SafetyNet será tomada com base no último resultado reportado ao serviço Intune no momento do lançamento condicional. Caso não existam dados, o acesso será permitido dependendo de nenhuma outra verificação de lançamento condicional falhando, e o Google Play Service "trip" para determinar os resultados da atesta começará no backend e solicitará ao utilizador assincronicamente se o dispositivo tiver falhado. Se houver dados antigos, o acesso será bloqueado ou permitido dependendo do último resultado reportado, e da mesma forma, uma "ida e volta" do Serviço Google Play para determinar os resultados da atesta começará e solicitará ao utilizador assincronicamente se o dispositivo tiver falhado.

**As Políticas de Proteção de Aplicações Intune fornecem a capacidade para os administradores exigirem que os dispositivos de utilizador final enviem sinais através da API de Aplicações de Verificação da Google para dispositivos Android. Como é que um utilizador final pode ligar a aplicação para que não seja bloqueada do acesso devido a isto?**<br><br> As instruções sobre como fazê-lo variam ligeiramente por dispositivo. O processo geral envolve ir à Google Play Store, clicando depois nas **minhas aplicações e jogos,** clicando no resultado da última pesquisa de aplicações que o levará ao menu Play Protect. Certifique-se de que o **dispositivo Desativação para ameaças** de segurança está ligado.

**O que é que a API safetyNet attestation da Google verifica realmente em dispositivos Android? Qual é a diferença entre os valores configuráveis de 'Verificar integridade básica' e 'Verificar integridade básica e dispositivos certificados'?** <br><br>
Intune aproveita as APIs do Google Play Protect SafetyNet para adicionar aos nossos controlos de deteção de raízes existentes para dispositivos não matriculados. A Google desenvolveu e manteve este conjunto de API para as aplicações Android adotarem se não quiserem que as suas aplicações sejam executadas em dispositivos enraizados. A aplicação Android Pay incorporou isto, por exemplo. Embora a Google não partilhe publicamente a totalidade das verificações de deteção de raízes que ocorrem, esperamos que estas APIs detetem utilizadores que tenham enraizado os seus dispositivos. Estes utilizadores podem então ser impedidos de aceder, ou as suas contas corporativas eliminadas das suas aplicações ativadas pela política. 'Verifique a integridade básica' diz-lhe sobre a integridade geral do dispositivo. Dispositivos enraizados, emuladores, dispositivos virtuais e dispositivos com sinais de adulteração falham a integridade básica. 'Verifique a integridade básica e os dispositivos certificados' diz-lhe sobre a compatibilidade do dispositivo com os serviços da Google. Apenas dispositivos não modificados certificados pela Google podem passar este cheque. Os dispositivos que falharão incluem o seguinte:

- Dispositivos que falham na integridade básica
- Dispositivos com um bootloader desbloqueado
- Dispositivos com uma imagem/ROM do sistema personalizado
- Dispositivos para os quais o fabricante não se candidatou, ou passou, certificação da Google 
- Dispositivos com uma imagem de sistema construída diretamente a partir dos ficheiros de origem do Android Open Source Program
- Dispositivos com uma imagem do sistema de pré-visualização beta/desenvolvedor

Consulte [a documentação da Google sobre o Atestado SafetyNet](https://developer.android.com/training/safetynet/attestation) para obter detalhes técnicos.

**Existem dois controlos semelhantes na secção de Lançamento Condicional ao criar uma Política de Proteção de Aplicações Intune para dispositivos Android. Devo exigir a definição do dispositivo SafetyNet ou a definição de dispositivos "jailbroken/rooted devices"?** <br><br>
As verificações da API SafetyNet da Google Play Protect exigem que o utilizador final esteja online, pelo menos durante o tempo em que a "viagem de ida e volta" para determinar os resultados da atesta executa. Se o utilizador final estiver offline, a administração de TI ainda pode esperar que um resultado seja aplicado a partir da definição de "dispositivos encarcerados/enraizados". Dito isto, se o utilizador final estiver offline há demasiado tempo, entra em vigor o valor do "período de carência offline", e todo o acesso ao trabalho ou aos dados escolares é bloqueado assim que esse valor do temporizador for atingido, até que o acesso à rede esteja disponível. Ligar ambas as definições permite uma abordagem em camadas para manter os dispositivos de utilizador final saudáveis, o que é importante quando os utilizadores finais acedem ao trabalho ou aos dados escolares no telemóvel. 

**As definições de política de proteção de aplicações que alavancam as APIs do Google Play Protect exigem que os Serviços de Reprodução do Google funcionem. E se os Serviços de Reprodução do Google não forem permitidos no local onde o utilizador final pode estar?**<br><br>
Tanto o 'dispositivo SafetyNet' como as definições de 'Threat scan on apps' exigem que a versão determinada do Google Play Services funcione corretamente. Uma vez que estas são configurações que caem na área de segurança, o utilizador final será bloqueado se tiver sido alvo destas definições e não estiver a cumprir a versão adequada dos Serviços Google Play ou não tiver acesso aos Serviços de Reprodução do Google. 

## <a name="app-experience-on-ios"></a>Experiência de aplicação em iOS
**O que acontece se adicionar ou remover uma impressão digital ou um rosto do meu dispositivo?**<br></br>
As políticas de proteção de aplicações do Intune permitem o controlo sobre o acesso da aplicação apenas ao utilizador licenciado do Intune. Uma das formas de controlar o acesso à aplicação é exigir o Touch ID ou o Face ID da Apple nos dispositivos suportados. O Intune implementa um comportamento em que se houver qualquer alteração à base de dados biométricos do dispositivo, o Intune pede ao utilizador um PIN quando atingir o valor do tempo limite de inatividade seguinte. As alterações a dados biométricos incluem a adição ou remoção de uma impressão digital ou de um rosto. Se o utilizador do Intune não tiver um PIN definido, este é direcionado para configurar um PIN do Intune.

A intenção é continuar a manter os dados da sua organização na aplicação em segurança e protegidos ao nível da aplicação. Esta funcionalidade só está disponível para iOS e requer a participação de aplicações que integrem o SDK da aplicação Intune para iOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.
  
**Posso usar a extensão da partilha do iOS para abrir o trabalho ou dados escolares em aplicações não geridas, mesmo com a política de transferência de dados definida para "apenas aplicações geridas" ou "sem apps". Estes dados não são de fugas?**<br></br>
A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por isso, o _**Intune encripta os dados "empresariais" antes de estes serem partilhados fora da aplicação**_ . Para o confirmar, pode tentar abrir o ficheiro "empresarial" fora da aplicação gerida. O ficheiro deverá estar encriptado, e não deverá ser possível abri-lo fora da aplicação gerida.

**Como é que múltiplas definições de acesso de proteção de aplicações do Intune configuradas para o mesmo conjunto de aplicações e utilizadores funcionam no iOS?**<br></br>
As políticas de proteção de aplicações do Intune para acesso serão aplicadas numa ordem específica nos dispositivos dos utilizadores finais à medida que tentam aceder a uma aplicação direcionada a partir da respetiva conta empresarial. Em geral, uma limpeza teria precedência, seguida de um bloqueio e de um aviso que pode ser dispensado. Por exemplo, se for aplicável ao utilizador/aplicação específico, uma definição de sistema operativo iOS mínimo que avisa um utilizador para atualizar a respetiva versão do iOS será aplicada após a definição de sistema operativo iOS mínimo bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura o sistema operativo iOS mínimo para 11.0.0.0 e o sistema operativo iOS mínimo (apenas Aviso) para 11.1.0.0, embora o dispositivo que tentava aceder à aplicação tivesse o iOS 10, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de sistema operativo iOS que resulta num bloqueio do acesso.

Ao lidar com diferentes tipos de definições, um requisito de versão de SDK da Aplicação Intune teria precedência, seguido do requisito de versão da aplicação e do requisito de versão de sistema operativo iOS. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem. Recomendamos que o requisito de versão do SDK da Aplicação Intune só seja configurado após receber orientações sobre cenários de bloqueio essenciais por parte da equipa de produto do Intune.


## <a name="see-also"></a>Veja também
- [Implementar o plano do Intune](../fundamentals/planning-guide-onboarding.md)
- [Teste e validação do Intune](../fundamentals/planning-guide-test-validation.md)
- [Definições de políticas de gestão de aplicações móveis para Android no Microsoft Intune](../apps/app-protection-policy-settings-android.md)
- [Definições de políticas de gestão de aplicações móveis para iOS](../apps/app-protection-policy-settings-ios.md)
- [Atualização da política de políticas de proteção de aplicações](../apps/app-protection-policy-delivery.md)
- [Validar as políticas de proteção de aplicações](../apps/app-protection-policy-delivery.md)
- [Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos](../apps/app-configuration-policies-managed-app.md)
- [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md)
