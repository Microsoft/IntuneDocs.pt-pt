---
title: Edição antecipada – Microsoft Intune
titlesuffix: ''
description: Edição antecipada do Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1ff65e1b48815cd5964aa7498fa6ba54df50e09
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742300"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>A edição antecipada do Microsoft Intune – Fevereiro de 2019

> [!Note]
> Notificação de contrato de confidencialidade: As seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, que estarão disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure
<!-- 1902 start-->


<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Implementação de online licenciado Microsoft Store para aplicações de negócio <!-- 1672660  -->
Será capaz de atribuir necessário online licenciada Microsoft Store para aplicações de negócio no contexto do dispositivo. Implementar um Microsoft Store para a aplicação de negócios desta forma permitirá que a aplicação ser instalada para todos os utilizadores no dispositivo. Isto só é aplicável no Windows 10 RS4 + dispositivos de ambiente de trabalho. A opção para instalar no contexto do dispositivo está disponível na página de atribuição de aplicações de cliente para aplicações licenciadas Online do MSFB.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Aplicação do Android Enterprise-implementação de aplicações, <!-- 1171203 -->
Para dispositivos Android num não inscritos proteção política sem inscrição de aplicações (APP-PODEMOS) cenário de implementação, poderá usar o Google Play gerido para implementar aplicações da loja e aplicações aos utilizadores LOB. Especificamente, o departamento de TI pode fornecer aos utilizadores finais uma experiência de instalação e de catálogo de aplicações que já não necessita que os utilizadores finais flexibilize as a postura de segurança dos seus dispositivos ao permitir que as instalações de origens desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>As políticas do Intune atualizar o método de autenticação e a instalação da aplicação Portal da empresa  <!-- 1927359 -->
Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, o Intune suportará já não é o Portal da empresa quando é instalado manualmente pelos usuários finais da loja de aplicações. Esta alteração é relevante apenas quando se autenticar com o Assistente de configuração da Apple durante a inscrição. Esta alteração afeta também apenas dispositivos iOS inscritos através de:  
* Do Apple configurator
* Gerente de negócios da Apple
* Gestor Escolar da Apple
* Programa de inscrição de dispositivos Apple (DEP)

Se os utilizadores instalarem a aplicação Portal da empresa a partir da App store e, em seguida, tentar inscrever estes dispositivos através do mesmo, receberá um erro. Estes dispositivos serão esperados para utilizar o Portal da empresa apenas quando ele é foi emitido, automaticamente, pelo Intune durante a inscrição. Perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Se pretender que os utilizadores de dispositivos do DEP para o portal da empresa, terá de especificar as suas preferências num perfil de inscrição. Além disso, o **identificar o seu dispositivo** ecrã na aplicação Portal da empresa em breve se tornarão obsoleta.  
Para instalar o Portal da empresa em dispositivos DEP já inscrito, terá de ir para o Intune > aplicações de cliente e enviá-los como uma aplicação gerida com as políticas de configuração de aplicações. Detalhes sobre como efetuar estes passos irão ser descritos nos documentos futuros.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Modelos administrativos estão em pré-visualização pública e movido para o seu próprio perfil de configuração <!-- 3322847 -->
Modelos administrativos no Intune (**configuração do dispositivo** > **modelos administrativos**) estão atualmente em pré-visualização privada. Com esta atualização: Modelos administrativos inclui aproximadamente 300 configurações que podem ser geridas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
Modelos administrativos estão disponíveis em pré-visualização pública, administração estiver a mover de modelos **configuração do dispositivo** > **modelos administrativos** para **dispositivo configuração** > **perfis** >**criar perfil** > no **plataforma**, escolha  **Windows 10 e posterior**, na **tipo de perfil**, escolha **modelos administrativos**.
O relatório está ativado aplica-se a: Windows 10 e posterior

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>No modo escuro do Portal da empresa do Intune macOS <!-- 3300524 -->
O Portal da empresa do macOS do Intune agora suporta o modo escuro para macOS. Quando ativar o modo escuro num dispositivo macOS 10.14 +, o Portal da empresa irá ajustar sua aparência para as cores que refletem esse modo.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Definições da Política de Proteção de Aplicações (APP) para dados da Web <!-- 2662995 -->
As definições da política APP para conteúdos da Web em dispositivos Android e iOS serão atualizadas para processar melhor ligações Web HTTP e HTTPS, bem como a transferência de dados através de Ligações Universais do iOS e Ligações de Aplicações do Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token Apple VPP utilizado por outra MDM <!-- 1488946 -->
O Intune irá detetar e mostrar detalhes se um token de programa de compras em volume (VPP) da Apple estiver a ser utilizado pelo Intune e outra MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos extintos no dashboard de conformidade do dispositivo <!-- 1981119 -->
Numa atualização futura, os dispositivos extintos serão removidos do dashboard de conformidade do dispositivo. Tal irá alterar os seus números de conformidade.

## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
