---
title: Perguntas mais frequentes sobre a MAM e a proteção de aplicações
description: Este artigo apresenta respostas a algumas das perguntas mais frequentes acerca da gestão de aplicações móveis do Intune (MAM) e da proteção de aplicações do Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3c28f7cea87a58f7a01ef2fc427dd3c6d2176f8c
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Perguntas mais frequentes sobre a MAM e a proteção de aplicações

Este artigo apresenta respostas a algumas das perguntas mais frequentes acerca da gestão de aplicações móveis do Intune (MAM) e da proteção de aplicações do Intune.

## <a name="mam-basics"></a>Noções básicas da MAM


**O que é a MAM?** A [gestão de aplicações móveis do Intune](/intune/app-lifecycle) refere-se ao conjunto de funcionalidades de gestão do Intune que lhe permite publicar, emitir via push, configurar, proteger, monitorizar e atualizar aplicações móveis para os seus utilizadores.

**Quais são as vantagens da proteção de aplicações da MAM?** A MAM protege os dados de uma empresa dentro da aplicação. Com a MAM sem inscrição (MAM-WE), pode gerir uma aplicação relacionada com o trabalho ou com a escola que contenha dados confidenciais na maioria dos dispositivos, incluindo os dispositivos pessoais, em cenários BYOD (Bring Your Own Device). Muitas aplicações de produtividade, como as aplicações do Microsoft Office, podem ser geridas pela MAM do Intune. Veja a lista oficial das [aplicações geridas pelo Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponíveis para utilização pública.

**Que configurações de dispositivos suporta a MAM?** A MAM do Intune suporta dois tipos de configurações:
- **Intune MDM + MAM**: os administradores de TI só podem gerir as aplicações através da MAM e das políticas de proteção de aplicações em dispositivos que estejam inscritos na gestão de dispositivos móveis do Intune (MDM). Para gerir aplicações com a MDM + MAM, os clientes devem utilizar a consola do Intune no portal do Azure em https://portal.azure.com.

- **MAM sem inscrição de dispositivos**: a MAM sem inscrição de dispositivos, ou MAM-WE, permite aos administradores de TI gerir as aplicações com a MAM e as políticas de proteção de aplicações nos dispositivos que não estejam inscritos na MDM do Intune. Isto significa que as aplicações podem ser geridas pelo Intune em dispositivos inscritos em fornecedores de EMM terceiros. Para gerir aplicações com a MAM-WE, os clientes devem utilizar a consola do Intune no portal do Azure em http://portal.azure.com. Além disso, as aplicações podem ser geridas pelo Intune nos dispositivos inscritos em fornecedores de Gestão de Mobilidade da Empresa (EMM) de terceiros ou não inscritos numa MDM.


## <a name="app-protection-policies"></a>Políticas de proteção de aplicações

**O que são as políticas de proteção de aplicações?** As políticas de proteção de aplicações são regras que asseguram que os dados de uma organização continuam seguros ou protegidos numa aplicação gerida. Uma política pode ser uma regra que é aplicada quando o utilizador tenta aceder ou mover dados "empresariais" ou um conjunto de ações que são proibidas ou monitorizadas quando um utilizador utiliza a aplicação.

**Quais são os exemplos das políticas de proteção de aplicações?** Veja as [definições da política de proteção de aplicações para Android](app-protection-policy-settings-android.md) e as [definições da política de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) para obter informações detalhadas acerca de cada definição da política de proteção de aplicações.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicações que pode gerir com as políticas de proteção de aplicações

**Que aplicações podem ser geridas pelas políticas de proteção de aplicações?** Qualquer aplicação que tenha sido integrada com o [SDK da Aplicação Intune](/intune/app-sdk) ou encapsulada pela [Ferramenta de Encapsulamento de Aplicações do Intune](/intune/apps-prepare-mobile-application-management) pode ser gerida com as políticas de proteção de aplicações do Intune. Veja a lista oficial das [aplicações geridas pelo Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponíveis para utilização pública.

**Quais são os requisitos base para utilizar as políticas de proteção de aplicações numa aplicação gerida pelo Intune?**
- O utilizador final tem de ter uma conta no Azure Active Directory (AAD). Veja [Adicionar utilizadores e conceder permissões administrativas no Intune](/intune/users-permissions-add) para saber como criar utilizadores do Intune no Azure Active Directory.

- O utilizador final tem de ter uma licença para o Microsoft Intune atribuída à conta do Azure Active Directory dele. Veja [Gerir licenças do Intune](/intune/licenses-assign) para saber como atribuir licenças do Intune aos utilizadores finais.

- O utilizador final tem de pertencer a um grupo de segurança visado por uma política de proteção de aplicações. A mesma política de proteção de aplicações tem de abranger a aplicação específica em utilização. As políticas de proteção de aplicações podem ser criadas e implementadas na consola do Intune, no [portal do Azure](http://portal.azure.com). Atualmente, os grupos de segurança podem ser criados no [portal do Office](http://portal.office.com).

- O utilizador final tem de iniciar sessão na aplicação através da respetiva conta do AAD.

**Quais são os requisitos adicionais para utilizar a [aplicação Outlook para dispositivos móveis](https://products.office.com/outlook)?**

- O utilizador final tem de ter a aplicação Outlook para dispositivos móveis instalada no dispositivo dele.

- O utilizador final tem de ter uma licença e uma caixa de correio do [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) associadas à conta do Azure Active Directory dele.

  >[!NOTE]
  > Atualmente, a aplicação Outlook para dispositivos móveis só suporta a Proteção de Aplicações do Intune para o Microsoft Exchange Online e o [Exchange Server com autenticação moderna híbrida](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx) e não suporta o Exchange no Office 365 Dedicated.

**Quais são os requisitos adicionais para utilizar as [aplicações Word, Excel e PowerPoint](https://products.office.com/business/office)?**

- O utilizador final tem de ter uma licença do [Office 365 Empresas ou Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) associada à respetiva conta do Azure Active Directory. A subscrição tem de incluir as aplicações do Office para dispositivos móveis e pode incluir uma conta de armazenamento na cloud com o [OneDrive para Empresas](https://onedrive.live.com/about/business/). As licenças do Office 365 podem ser atribuídas no [portal do Office](http://portal.office.com) ao seguir estas [instruções](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- O utilizador final tem de ter uma localização gerida, configurada através da funcionalidade granular Guardar como, na definição da política de proteção de aplicações "Impedir Guardar Como". Por exemplo, se a localização gerida for o OneDrive, a aplicação [OneDrive](https://onedrive.live.com/about/) deverá ser configurada na aplicação Word, Excel ou PowerPoint do utilizador final.

- Se a localização gerida for o OneDrive, a aplicação terá de ser visada pela política de proteção de aplicações implementada para o utilizador final.

  >[!NOTE]
  > Atualmente, as aplicações do Office para dispositivos móveis só suportam o SharePoint Online e não o SharePoint no local.

**Por que motivo é preciso uma localização gerida (como o OneDrive) para o Office?** O Intune marca todos os dados na aplicação como "empresariais" ou "pessoais". Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas).

**Quais são os requisitos adicionais para utilizar o Skype para Empresas?** Veja os requisitos de licença do [Skype para Empresas](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > Atualmente, a aplicação Skype para Empresas para dispositivos móveis só suporta o Skype para Empresas Online.

## <a name="app-protection-features"></a>Funcionalidades da proteção de aplicações

**O que é o suporte de identidades múltiplas?** O suporte de identidades múltiplas é a capacidade do SDK da Aplicação Intune de só aplicar as políticas de proteção de aplicações à conta profissional ou escolar que tenha sessão iniciada na aplicação. Se uma conta pessoal tiver sessão iniciada na aplicação, os dados permanecem inalterados.

**Qual é o objetivo do suporte de identidades múltiplas?** O suporte de identidades múltiplas permite que as aplicações com públicos "empresariais" e consumidores (por exemplo, as aplicações do Office) sejam lançadas publicamente com as funcionalidades de proteção de aplicações do Intune para as contas "empresariais".

**E o Outlook e as identidades múltiplas?** Uma vez que o Outlook tem uma vista combinada dos e-mails pessoais e "empresariais", a aplicação Outlook pede o PIN do Intune quando é iniciada.

**O que é o PIN da aplicação Intune?** O Número de Identificação Pessoal (PIN) é um código de acesso utilizado para verificar que o utilizador certo está a aceder aos dados da organização numa aplicação.

- **Quando é pedido ao utilizador para introduzir o PIN?** O Intune só pede ao utilizador para introduzir o PIN da aplicação quando o mesmo quiser aceder aos dados "empresariais". Em aplicações de identidades múltiplas como o Word/Excel/PowerPoint, é pedido ao utilizador que introduza o PIN ao tentar abrir um documento ou ficheiro "empresarial". Em aplicações de identidade única, como as aplicações de linha de negócio geridas com a Ferramenta de Encapsulamento de Aplicações do Intune, o PIN é pedido no início, uma vez que o SDK da Aplicação Intune reconhece que a experiência do utilizador na aplicação é sempre "empresarial".

- **Com que frequência será pedido ao utilizador para introduzir o PIN do Intune?**
  O administrador de TI pode configurar a definição“Reverificar os requisitos de acesso após (minutos)” da política de proteção de aplicações do Intune na consola de administração do Intune. Esta definição especifica o período de tempo antes da verificação dos requisitos de acesso no dispositivo e de uma nova apresentação do ecrã de PIN da aplicação. Contudo, os detalhes importantes sobre o PIN que afetam a frequência de solicitação do utilizador incluem: 

    - **O PIN é partilhado entre aplicações do mesmo publicador para melhorar a facilidade de utilização:** no iOS, um PIN da aplicação é partilhado entre todas as aplicações **do mesmo publicador**. No Android, um PIN da aplicação é partilhado entre todas as aplicações.
    - **A natureza flexível do temporizador associado ao PIN:** após introduzir um PIN para aceder a uma aplicação (aplicação A) e esta sair de primeiro plano (foco de introdução principal) no dispositivo, o temporizador deste PIN é reposto. Não será pedido nenhum PIN às aplicações (aplicação B) que partilhem este PIN, uma vez que o temporizador foi reposto. O pedido aparecerá novamente depois de o valor “Reverificar os requisitos de acesso após (minutos)” ter sido atingido. 

      >[!NOTE] 
      > Para verificar os requisitos de acesso do utilizador com mais frequência (ou seja, o pedido de PIN), especialmente para uma aplicação utilizada com frequência, é recomendado reduzir o valor da definição “Reverificar os requisitos de acesso após (minutos)”. 

- **O PIN é seguro?** O PIN serve para garantir que só o utilizador correto consegue aceder aos dados da respetiva organização na aplicação. Por conseguinte, o utilizador final tem de iniciar sessão com a conta profissional ou escolar para poder definir ou repor o PIN da aplicação Intune. Esta autenticação é processada pelo Azure Active Directory através de uma troca de tokens segura e não é revelada ao SDK da Aplicação Intune. No que diz respeito à segurança, a melhor forma de proteger os seus dados profissionais ou escolares é encriptá-los. A encriptação não está relacionada com o PIN da aplicação, mas é a sua própria política de proteção da aplicação.

- **Como é que o Intune protege o PIN contra ataques de força bruta?** Como parte da política de PIN da aplicação, o administrador de TI pode definir o número máximo de vezes que um utilizador pode tentar autenticar o respetivo PIN antes de bloquear a aplicação. Após esgotar o número de tentativas, o SDK da Aplicação Intune pode eliminar os dados "empresariais" na aplicação.
  
- **Por que motivo tenho de definir um PIN duas vezes em aplicações do mesmo publicador?**
  Atualmente, a MAM (no iOS) permite PINs ao nível da aplicação com carateres alfanuméricos e especiais (denominados “código de acesso”), que precisam da participação de aplicações (como WXP, Outlook, Managed Browser, Yammer) para integrar o SDK da Aplicação Intune para iOS. Caso contrário, as definições do código de acesso não são impostas corretamente nas aplicações visadas. Esta funcionalidade foi lançada com o SDK do Intune para iOS v. 7.1.12. <br><br> Para suportar esta funcionalidade e garantir a retrocompatibilidade com versões anteriores do SDK do Intune para iOS, todos os PINs (numéricos ou códigos de acesso) na versão 7.1.12 ou superior são processados em separado do PIN numérico em versões anteriores do SDK. Como tal, se um dispositivo tiver aplicações com o SDK do Intune para versões do iOS anteriores à 7.1.12 E posteriores à 7.1.12 do mesmo publicador, terá de configurar dois PINs. <br><br> Porém, os dois PINs (para cada aplicação) não estão relacionados de forma alguma, ou seja, têm de respeitar a política de proteção de aplicações que é aplicada à aplicação. Como tal, *só* se as aplicações A e B tiverem as mesmas políticas aplicadas (no que respeita ao PIN) é que o utilizador poderá configurar o mesmo PIN duas vezes. <br><br> Este comportamento é específico para o PIN em aplicações iOS com a Gestão de Aplicações Móveis do Intune ativada. Ao longo do tempo, como as aplicações adotam versões posteriores do SDK do Intune para iOS, ter de definir um PIN duas vezes em aplicações do mesmo publicador deixa de ser um problema. Veja a nota abaixo para obter um exemplo.

  >[!NOTE]
  > Por exemplo, se a aplicação A tiver sido concebida com uma versão anterior à 7.1.12 e a aplicação B tiver sido concebida com uma versão igual ou superior à 7.1.12 do mesmo publicador, o utilizador final terá de configurar PINs em separado para A e B se ambas estiverem instaladas num dispositivo iOS. <br><br> Se uma aplicação C que tem o SDK versão 7.1.9 estiver instalada no dispositivo, partilhará o mesmo PIN da aplicação A. <br><br> Uma aplicação D concebida com a versão 7.1.14 partilhará o mesmo PIN da aplicação B. <br><br> Se apenas as aplicações A e C estiverem instaladas num dispositivo, será preciso definir um PIN. O mesmo se aplica se apenas as aplicações B e D estiverem instaladas num dispositivo.

**E a encriptação?** Os administradores de TI podem implementar uma política de proteção de aplicações que exija a encriptação dos dados da aplicação. Como parte da política, o administrador de TI também pode especificar a altura em que os conteúdos são encriptados.

- **Como é que o Intune encripta os dados?** Veja as [definições da política de proteção de aplicações para Android](app-protection-policy-settings-android.md) e as [definições da política de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) para obter informações detalhadas sobre a definição de encriptação da política de proteção de aplicações.

- **O que é encriptado?** Só os dados marcados como "empresariais" são encriptados de acordo com a política de proteção de aplicações do administrador de TI. Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas). Para aplicações de linha de negócio geridas com a Ferramenta de Encapsulamento de Aplicações do Intune, todos os dados da aplicação são considerados "empresariais".

**Como é que o Intune elimina os dados remotamente?** O Intune pode eliminar os dados da aplicação de três formas diferentes: eliminação total do dispositivo, eliminação seletiva para MDM e eliminação seletiva MAM. Para obter mais informações sobre a eliminação remota para a MDM, veja [Remover dispositivos através da reposição de fábrica ou da remoção de dados da empresa](devices-wipe.md#factory-reset). Para obter mais informações sobre a eliminação seletiva através da MAM, veja [Remover dados da empresa](devices-wipe.md#remove-company-data) e [Como eliminar apenas os dados empresariais das aplicações](apps-selective-wipe.md).

- **O que é a reposição de fábrica?** A [Reposição de fábrica](devices-wipe.md) elimina todos os dados e definições do utilizador do respetivo **dispositivo**, ao restaurar o dispositivo com as predefinições de fábrica. O dispositivo é removido do Intune.
  >[!NOTE]
  > A Reposição de fábrica só pode ser realizada em dispositivos inscritos na gestão de dispositivos móveis do Intune (MDM).

- **O que é uma eliminação seletiva para MDM?** Veja [Remover dispositivos – Remover dados da empresa](devices-wipe.md#remove-company-data) para ler mais sobre a remoção dos dados da empresa.

- **O que é uma eliminação seletiva para MAM?** A eliminação seletiva para MAM simplesmente remove os dados da aplicação da empresa de uma aplicação. O pedido é iniciado através do portal do Intune Azure. Para saber como iniciar um pedido de eliminação, veja o artigo [Como eliminar apenas os dados empresariais das aplicações](apps-selective-wipe.md).

- **Qual é a velocidade da eliminação seletiva para MAM?** Se o utilizador estiver a utilizar a aplicação quando a eliminação seletiva for iniciada, o SDK da Aplicação Intune verifica a existência de pedidos de eliminação seletiva a cada 30 minutos a partir do serviço MAM do Intune. Também verifica a existência de pedidos de eliminação seletiva quando o utilizador inicia a aplicação pela primeira vez e inicia sessão com a conta profissional ou escolar.

**Por que razão os serviços no local não funcionam com as aplicações protegidas pelo Intune?** A proteção de aplicações do Intune depende da identidade do utilizador para ser consistente entre a aplicação e o SDK da Aplicação Intune. A única forma de o garantir é através da autenticação moderna. Existem cenários onde aplicações podem funcionar com uma configuração no local, mas não é garantido e nem consistente.

**Existe uma forma segura de abrir ligações Web a partir de aplicações geridas?** Sim! O administrador de TI pode implementar e definir a política de proteção de aplicações para a [aplicação Intune Managed Browser](app-configuration-managed-browser.md), um browser desenvolvido pelo Microsoft Intune que pode ser gerido facilmente com o Intune. O administrador de TI pode exigir que todas as ligações Web nas aplicações geridas pelo Intune sejam abertas através da aplicação Managed Browser.

## <a name="app-experience-on-android"></a>Experiência de aplicação em Android

**Por que razão é que a aplicação Portal da Empresa precisa da proteção de aplicações do Intune para funcionar em dispositivos Android?** Uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. Embora a aplicação Portal da Empresa seja sempre necessária, a inscrição de dispositivos _não é obrigatória_. Para a MAM-WE, o utilizador final apenas precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

**Como é que múltiplas definições de acesso de proteção de aplicações do Intune configuradas para o mesmo conjunto de aplicações e utilizadores funcionam no Android?** As políticas de proteção de aplicações do Intune para acesso serão aplicadas numa ordem específica nos dispositivos dos utilizadores finais à medida que tentam aceder a uma aplicação direcionada a partir da respetiva conta empresarial. Em geral, um bloqueio teria precedência, seguido de um aviso que pode ser dispensado. Por exemplo, se aplicável ao utilizador/aplicação específico, uma definição mínima de versão de patch do Android que avisa um utilizador para atualizar o patch será aplicada após a definição mínima de versão de patch do Android bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura a versão mínima de patch do Android para 2018-03-01 e a versão mínima de patch do Android (apenas Aviso) para 2018-02-01, embora o dispositivo que tentava aceder à aplicação tivesse a versão de patch 2018-01-01, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de patch do Android que resulta num bloqueio do acesso. 

Ao lidar com diferentes tipos de definições, um requisito de versão de aplicação teria precedência, seguido do requisito de versão de sistema operativo Android e do requisito de versão de patch do Android. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem.

## <a name="app-experience-on-ios"></a>Experiência de aplicação em iOS

**Posso utilizar a extensão de partilha do iOS para abrir dados escolares ou profissionais em aplicações não geridas, mesmo com a política de transferência de dados definida para "apenas aplicações geridas" ou "nenhuma aplicação". Isto não resulta numa fuga de dados?** A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por isso, o _**Intune encripta os dados "empresariais" antes de estes serem partilhados fora da aplicação**_. Para comprovar, pode tentar abrir o ficheiro "empresarial" fora da aplicação gerida. O ficheiro deverá estar encriptado, e não deverá ser possível abri-lo fora da aplicação gerida.

**Como é que múltiplas definições de acesso de proteção de aplicações do Intune configuradas para o mesmo conjunto de aplicações e utilizadores funcionam no iOS?** As políticas de proteção de aplicações do Intune para acesso serão aplicadas numa ordem específica nos dispositivos dos utilizadores finais à medida que tentam aceder a uma aplicação direcionada a partir da respetiva conta empresarial. Em geral, uma eliminação teria precedência, seguida de um bloqueio e de um aviso que pode ser dispensado. Por exemplo, se for aplicável ao utilizador/aplicação específico, uma definição de sistema operativo iOS mínimo que avisa um utilizador para atualizar a respetiva versão do iOS será aplicada após a definição de sistema operativo iOS mínimo bloquear o acesso do utilizador. Portanto, no cenário em que o administrador de TI configura o sistema operativo iOS mínimo para 11.0.0.0 e o sistema operativo iOS mínimo (apenas Aviso) para 11.1.0.0, embora o dispositivo que tentava aceder à aplicação tivesse o iOS 10, o utilizador final seria bloqueado com base na definição mais restrita de versão mínima de sistema operativo iOS que resulta num bloqueio do acesso.

Ao lidar com diferentes tipos de definições, um requisito de versão de SDK da Aplicação Intune teria precedência, seguido do requisito de versão da aplicação e do requisito de versão de sistema operativo iOS. Em seguida, são verificados os avisos de todos os tipos de definições na mesma ordem. Recomendamos que o requisito de versão do SDK da Aplicação Intune só seja configurado após receber orientações sobre cenários de bloqueio essenciais por parte da equipa de produto do Intune.

## <a name="see-also"></a>Consulte também
- [Implementar o plano do Intune](planning-guide-onboarding.md)
- [Teste e validação do Intune](planning-guide-test-validation.md)
- [Definições de políticas de gestão de aplicações móveis para Android no Microsoft Intune](app-protection-policy-settings-android.md)
- [Definições de políticas de gestão de aplicações móveis para iOS](app-protection-policy-settings-ios.md)
- [Validar as políticas de proteção de aplicações](app-protection-policies-validate.md)
- [Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos](app-configuration-policies-managed-app.md)
- [Como obter suporte para o Microsoft Intune](get-support.md)
