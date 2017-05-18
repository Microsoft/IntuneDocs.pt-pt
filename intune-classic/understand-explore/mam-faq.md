---
title: "Perguntas mais frequentes sobre a MAM e a proteção de aplicações"
description: "Este artigo apresenta respostas a algumas das perguntas mais frequentes acerca da gestão de aplicações móveis do Intune (MAM) e da proteção de aplicações do Intune."
keywords: 
author: oydang
ms.author: oydang
manager: mtillman
ms.date: 01/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 32446d9a6f9383b5449dbabf288b0eac0b483ebb
ms.lasthandoff: 04/24/2017


---

# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Perguntas mais frequentes sobre a MAM e a proteção de aplicações

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este artigo apresenta respostas a algumas das perguntas mais frequentes acerca da gestão de aplicações móveis do Intune (MAM) e da proteção de aplicações do Intune.

## <a name="mam-basics"></a>Noções básicas da MAM


**O que é a MAM?** A [gestão de aplicações móveis do Intune](../deploy-use/overview-of-app-lifecycle-in-microsoft-intune.md) refere-se ao conjunto de funcionalidades de gestão do Intune que lhe permite publicar, emitir via push, configurar, proteger, monitorizar e atualizar aplicações móveis para os seus utilizadores.

**Quais são as vantagens da proteção de aplicações da MAM?** A MAM protege os dados de uma empresa dentro da aplicação. Com a MAM-WE, pode gerir uma aplicação relacionada com o trabalho ou com a escola que contenha informações confidenciais na maioria dos dispositivos, incluindo os dispositivos pessoais, em cenários BYOD (Bring Your Own Device). Muitas aplicações de produtividade, como as aplicações do Microsoft Office, podem ser geridas pela MAM do Intune. Veja a lista oficial das [aplicações otimizadas pelo Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponíveis para utilização pública.

**Que configurações de dispositivos suporta a MAM?** A MAM do Intune suporta dois tipos de configurações:
  1. **MDM + MAM do Intune**: esta foi a primeira configuração suportada pela MAM quando esta foi lançada. Os administradores de TI só podem gerir as aplicações através da MAM e das políticas de proteção de aplicações em dispositivos que estejam inscritos na gestão de dispositivos móveis do Intune (MDM). Para gerir aplicações com a MDM + MAM, os clientes devem utilizar a consola autónoma do Intune em https://manage.microsoft.com.

  2. **MAM sem inscrição de dispositivos**: a MAM sem inscrição de dispositivos, ou MAM-WE, permite aos administradores de TI gerir as aplicações com a MAM e as políticas de proteção de aplicações nos dispositivos que não estejam inscritos na MDM do Intune. Isto significa que as aplicações podem ser geridas pelo Intune em dispositivos inscritos em fornecedores de EMM terceiros. Para gerir aplicações com a MAM-WE, os clientes podem utilizar a consola do Intune no portal do Azure em http://portal.azure.com.


## <a name="app-protection-policies"></a>Políticas de proteção de aplicações

**O que são as políticas de proteção de aplicações?** As políticas de proteção de aplicações são regras que asseguram que os dados de uma organização continuam seguros ou protegidos numa aplicação gerida. Uma política pode ser uma regra que é aplicada quando o utilizador tenta aceder ou mover dados "empresariais" ou um conjunto de ações que são proibidas ou monitorizadas quando um utilizador utiliza a aplicação.

**Quais são os exemplos das políticas de proteção de aplicações?** Veja as [definições da política de proteção de aplicações para Android](../deploy-use/android-mam-policy-settings.md) e as [definições da política de proteção de aplicações para iOS](../deploy-use/ios-mam-policy-settings.md) para obter informações detalhadas acerca de cada definição da política de proteção de aplicações.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicações que pode gerir com as políticas de proteção de aplicações

**Que aplicações podem ser geridas pelas políticas de proteção de aplicações?** Qualquer aplicação que tenha sido otimizada pelo [SDK da Aplicação Intune](../develop/intune-app-sdk.md) ou encapsulada pela [Ferramenta de Encapsulamento de Aplicações do Intune](../deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) pode ser gerida com as políticas de proteção de aplicações do Intune. Veja a lista oficial das [aplicações otimizadas pelo Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponíveis para utilização pública.

**Quais são os requisitos base para utilizar as políticas de proteção de aplicações numa aplicação otimizada pelo Intune?**
  1. O utilizador final tem de ter uma conta no Azure Active Directory (AAD). Veja [Adicionar utilizadores e conceder permissões administrativas no Intune](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md) para saber como criar utilizadores do Intune no Azure Active Directory.

  2. O utilizador final tem de ter uma licença para o Microsoft Intune atribuída à conta do Azure Active Directory dele. Veja [Gerir licenças do Intune](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4.md) para saber como atribuir licenças do Intune aos utilizadores finais.

  3. O utilizador final tem de pertencer a um grupo de segurança visado por uma política de proteção de aplicações. A mesma política de proteção de aplicações tem de abranger a aplicação específica em utilização. As políticas de proteção de aplicações podem ser criadas e implementadas na consola do Intune, no [portal do Azure](http://portal.azure.com). Atualmente, os grupos de segurança podem ser criados no [portal do Office](http://portal.office.com).

  4. O utilizador final tem de iniciar sessão na aplicação através da respetiva conta do AAD.

**Quais são os requisitos adicionais para utilizar a [aplicação Outlook para dispositivos móveis](https://www.microsoft.com/outlook-com/mobile/)?**

  1. O utilizador final tem de ter a aplicação Outlook para dispositivos móveis instalada no dispositivo dele.

  2. O utilizador final tem de ter uma licença e uma caixa de correio do [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) associadas à conta do Azure Active Directory dele.

  >[!NOTE]
  > Atualmente, a aplicação Outlook para dispositivos móveis só suporta o Microsoft Exchange Online e não suporta o Exchange no local ou o Exchange no Office 365 Dedicated.

**Quais são os requisitos adicionais para utilizar as [aplicações Word, Excel e PowerPoint](https://products.office.com/business/office)?**

  1. O utilizador final tem de ter uma licença do [Office 365 Empresas ou do Office 365 Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) associada à conta do Azure Active Directory. A subscrição tem de incluir as aplicações do Office para dispositivos móveis e uma conta de armazenamento na cloud com o [OneDrive para Empresas](https://onedrive.live.com/about/business/). As licenças do Office 365 podem ser atribuídas no [portal do Office](http://portal.office.com) ao seguir estas [instruções](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

  2. O utilizador final tem de ter a aplicação [OneDrive](https://onedrive.live.com/about/) instalada no dispositivo e tem de iniciar sessão com a conta do AAD dele.

  3. A aplicação do OneDrive tem de ser visada pela política de proteção de aplicações implementada no utilizador final.

  >[!NOTE]
  > Atualmente, as aplicações do Office para dispositivos móveis só suportam o SharePoint Online e não o SharePoint no local.

**Por que razão é necessário o OneDrive para o Office?** O Intune marca todos os dados na aplicação como "empresariais" ou "pessoais". Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas).

**Quais são os requisitos adicionais para utilizar o Skype para Empresas?** Veja os requisitos de licença do [Skype para Empresas](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > Atualmente, a aplicação Skype para Empresas para dispositivos móveis só suporta o Skype para Empresas Online.

## <a name="app-protection-features"></a>Funcionalidades da proteção de aplicações

**O que é o suporte de identidades múltiplas?** O suporte de identidades múltiplas é a capacidade do SDK da Aplicação Intune de só aplicar as políticas de proteção de aplicações à conta profissional ou escolar que tenha sessão iniciada na aplicação. Se uma conta pessoal tiver sessão iniciada na aplicação, os dados permanecem inalterados.

**Qual é o objetivo do suporte de identidades múltiplas?** O suporte de identidades múltiplas permite que as aplicações com públicos "empresariais" e consumidores (por exemplo, as aplicações do Office) sejam lançadas publicamente com as funcionalidades de proteção de aplicações do Intune para as contas "empresariais".

**Quando é que o ecrã de PIN é apresentado?** O ecrã de PIN do Intune só é apresentado quando o utilizador tenta aceder aos dados "empresariais" na aplicação. Por exemplo, nas aplicações Word/Excel/PowerPoint, o ecrã será apresentado quando o utilizador tentar abrir um documento a partir do OneDrive para Empresas (partindo do princípio de que implementa com êxito uma política de proteção de aplicações que exige PIN).

**E o Outlook e as identidades múltiplas?** Uma vez que o Outlook tem uma vista combinada dos e-mails pessoais e "empresariais", a aplicação Outlook pede o PIN do Intune quando é iniciada.

**O que é o PIN da aplicação Intune?** O Número de Identificação Pessoal (PIN) é um código de acesso utilizado para verificar que o utilizador certo está a aceder aos dados da organização numa aplicação.

  1. **Quando é pedido ao utilizador para introduzir o PIN?** O Intune só pede ao utilizador para introduzir o PIN da aplicação quando o mesmo quiser aceder aos dados "empresariais". Em aplicações de identidades múltiplas como o Word/Excel/PowerPoint, é pedido ao utilizador que introduza o PIN ao tentar abrir um documento ou ficheiro "empresarial". Em aplicações de identidade única, como as aplicações de linha de negócio otimizadas com a Ferramenta de Encapsulamento de Aplicações do Intune, o PIN é pedido no início, uma vez que o SDK da Aplicação Intune reconhece que a experiência do utilizador na aplicação é sempre "empresarial".

  2. **O PIN é seguro?** O PIN serve para garantir que só o utilizador correto consegue aceder aos dados da respetiva organização na aplicação. Por conseguinte, o utilizador final tem de iniciar sessão com a conta profissional ou escolar para poder definir ou repor o PIN da aplicação Intune. Esta autenticação é processada pelo Azure Active Directory através de uma troca de tokens segura e não é revelada ao SDK da Aplicação Intune. No que diz respeito à segurança, a melhor forma de proteger os seus dados profissionais ou escolares é encriptá-los. A encriptação não está relacionada com o PIN da aplicação, mas é a sua própria política de proteção da aplicação.

  3. **Como é que o Intune protege o PIN contra ataques de força bruta?** Como parte da política de PIN da aplicação, o administrador de TI pode definir o número máximo de vezes que um utilizador pode tentar autenticar o respetivo PIN antes de bloquear a aplicação. Após esgotar o número de tentativas, o SDK da Aplicação Intune pode eliminar os dados "empresariais" na aplicação.

**E a encriptação?** Os administradores de TI podem implementar uma política de proteção de aplicações que exija a encriptação dos dados da aplicação. Como parte da política, o administrador de TI também pode especificar a altura em que os conteúdos são encriptados.

  1. **Como é que o Intune encripta os dados?** Veja as [definições da política de proteção de aplicações para Android](../deploy-use/android-mam-policy-settings.md) e as [definições da política de proteção de aplicações para iOS](../deploy-use/ios-mam-policy-settings.md) para obter informações detalhadas sobre a definição de encriptação da política de proteção de aplicações.

  2. **O que é encriptado?** Só os dados marcados como "empresariais" são encriptados de acordo com a política de proteção de aplicações do administrador de TI. Os dados são considerados "empresariais" quando provêm de uma localização empresarial. Para as aplicações do Office, o Intune considera as seguintes localizações como localizações empresariais: e-mail (Exchange) ou armazenamento da cloud (aplicação OneDrive com uma conta do OneDrive para Empresas). Para aplicações de linha de negócio otimizadas com a Ferramenta de Encapsulamento de Aplicações do Intune, todos os dados da aplicação são considerados "empresariais".

**Como é que o Intune elimina os dados remotamente?** O Intune pode eliminar os dados da aplicação de três formas diferentes: eliminação total do dispositivo, eliminação seletiva para MDM e eliminação seletiva MAM. Para obter mais informações sobre a eliminação remota para MDM, veja [Ajudar a proteger os dados com a eliminação completa ou seletiva através do Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md). Para obter mais informações sobre a eliminação seletiva através do MAM, veja [Eliminar dados de aplicações geridas pela empresa com o Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  1. **O que é uma eliminação completa?** A [eliminação completa](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) elimina todos os dados e definições do utilizador do respetivo**dispositivo**, ao restaurar o dispositivo com as predefinições de fábrica. O dispositivo é removido do Intune.
  >[!NOTE]
  > A eliminação completa só pode ser realizada em dispositivos inscritos na gestão de dispositivos móveis do Intune (MDM).

  2. **O que é uma eliminação seletiva para MDM?** Veja [Ajudar a proteger os dados com a eliminação completa ou seletiva no Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) para saber mais sobre a eliminação seletiva.

  3. **O que é uma eliminação seletiva para MAM?** A eliminação seletiva para MAM simplesmente remove os dados da aplicação da empresa de uma aplicação. O pedido é iniciado através do portal do Intune Azure. Para obter mais informações sobre como iniciar um pedido de eliminação, veja [Eliminar dados de aplicações geridas pela empresa com o Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  4. **Qual é a velocidade da eliminação seletiva para MAM?** Se o utilizador estiver a utilizar a aplicação quando a eliminação seletiva for iniciada, o SDK da Aplicação Intune verifica a existência de pedidos de eliminação seletiva a cada 30 minutos a partir do serviço MAM do Intune. Também verifica a existência de pedidos de eliminação seletiva quando o utilizador inicia a aplicação pela primeira vez e inicia sessão com a conta profissional ou escolar.

**Por que razão os serviços no local não funcionam com as aplicações protegidas pelo Intune?** A proteção de aplicações do Intune depende da identidade do utilizador para ser consistente entre a aplicação e o SDK da Aplicação Intune. A única forma de o garantir é através da autenticação moderna. Existem cenários onde aplicações podem funcionar com uma configuração no local, mas não é garantido e nem consistente.

**Existe uma forma segura de abrir ligações Web a partir de aplicações geridas?** Sim! O administrador de TI pode implementar e definir a política de proteção de aplicações para a [aplicação Intune Managed Browser](../deploy-use/manage-internet-access-using-managed-browser-policies.md), um browser desenvolvido pelo Microsoft Intune que pode ser gerido facilmente com o Intune. O administrador de TI pode exigir que todas ligações Web nas aplicações otimizadas pelo Intune sejam abertas através da aplicação Managed Browser.


## <a name="app-experience-on-android"></a>Experiência de aplicação em Android

**Por que razão é que a aplicação Portal da Empresa precisa da proteção de aplicações do Intune para funcionar em dispositivos Android?** Uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. Embora a aplicação Portal da Empresa seja sempre necessária, a inscrição de dispositivos _não é obrigatória_. Para a MAM-WE, o utilizador final apenas precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

## <a name="app-experience-on-ios"></a>Experiência de aplicação em iOS

**Posso utilizar a extensão de partilha do iOS para abrir dados escolares ou profissionais em aplicações não geridas, mesmo com a política de transferência de dados definida para "apenas aplicações geridas" ou "nenhuma aplicação". Isto não resulta numa fuga de dados?** A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por isso, o _**Intune encripta os dados "empresariais" antes de estes serem partilhados fora da aplicação**_. Para comprovar, pode tentar abrir o ficheiro "empresarial" fora da aplicação gerida. O ficheiro deve estar encriptado e não deve ser possível abri-lo fora da aplicação gerida.

### <a name="see-also"></a>Consulte também
- [Definições de políticas de gestão de aplicações móveis para Android no Microsoft Intune](../deploy-use/android-mam-policy-settings.md)
- [Definições de políticas de gestão de aplicações móveis para iOS](../deploy-use/ios-mam-policy-settings.md)
- [Validar a configuração de gestão de aplicações móveis](../deploy-use/validate-mobile-application-management.md)
- [Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Como obter suporte para o Microsoft Intune](../troubleshoot/how-to-get-support-for-microsoft-intune.md)

