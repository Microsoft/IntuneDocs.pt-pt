---
title: "Novidades na Pré-visualização do Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Saiba quais são as novidades da pré-visualização do Azure no Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 92bb81440b9374b2b0b433b32fc0a1301998ea80
ms.lasthandoff: 03/15/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novidades na pré-visualização do Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

À medida que a pré-visualização pública progride e mais funcionalidades são adicionadas, será informado aqui.

> [!Note]
> Estamos a implementar as alterações indicadas nesta página na pré-visualização do portal do Azure. No entanto, as alterações poderão não estar disponíveis imediatamente devido à forma como o serviço do Intune é atualizado.  Vários componentes do serviço têm de ser atualizados sequencialmente antes de as novas funcionalidades do portal estarem disponíveis. Procure estas alterações à medida que forem implementadas no fim deste mês.

## <a name="march-2017"></a>Março de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Suporte para o Modo Perdido no iOS <!--431695-->

Para os dispositivos iOS 9.3 e posteriores, o Intune adicionou o suporte para o **Modo Perdido**. Agora, pode bloquear um dispositivo para impedir toda a utilização e apresentar um número de telefone de contacto e uma mensagem no ecrã de bloqueio do dispositivo.

O utilizador final só poderá desbloquear o dispositivo quando um administrador desativar o Modo Perdido. Quando o Modo Perdido está ativado, pode utilizar a ação Localizar dispositivo para apresentar a localização geográfica do dispositivo num mapa na consola do Intune.

Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](/intune-azure/manage-devices/what-is)?

### <a name="improvements-to-device-actions-report---677150--"></a>Melhorias ao relatório de Ações de Dispositivos<!--677150-->

Melhoramos o relatório de Ações de Dispositivos para um melhor desempenho. Além disso, agora pode filtrar o relatório por estado. Por exemplo, pode filtrar o relatório para mostrar apenas as ações de dispositivo que foram concluídas.

### <a name="actions-for-non-compliance---730266--"></a>Ações de não conformidade <!--730266-->

**Ações de não conformidade** é uma nova funcionalidade de políticas de conformidade que lhe permite tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->

Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](/intune-azure/manage-apps/add-apps).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Atribuir aplicações de LOB a utilizadores com dispositivos não inscritos <!--748823-->

Pode agora atribuir aplicações de linha de negócio a partir da loja aos utilizadores quer os respetivos dispositivos estejam ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, o utilizador terá de aceder ao site do Portal da Empresa para o instalar, em vez da aplicação Portal da Empresa.

### <a name="new-compliance-reports---846671--"></a>Novos relatórios de conformidade <!--846671-->

Tem agora relatórios de conformidade que lhe dão a postura de conformidade dos dispositivos na sua empresa e lhe permitem rapidamente resolver problemas relacionados com a conformidade encontrados pelos utilizadores. Pode ver informações sobre o

- Estado de conformidade geral dos dispositivos
- Estado de conformidade de uma definição individual
- Estado de conformidade de uma política individual

Também pode utilizar estes relatórios para desagregar um dispositivo individual para ver definições e políticas específicas que afetam esse dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->

Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal de pré-visualização do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.


## <a name="february-2017"></a>Fevereiro de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747600, 795782-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.

* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.  
* Existe uma opção adicional para bloquear a inscrição de dispositivos pessoais apenas para iOS e Android.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas as ações em dispositivos geridos <!--677150-->
Um novo relatório __Ações de Dispositivos__ mostra quem efetuou ações remotas como a reposição de dados de fábrica em dispositivos e o estado dessas ações. Veja [O que é a gestão de dispositivos?](https://docs.microsoft.com/intune-azure/manage-devices/what-is)

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->
Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](/intune-azure/manage-apps/add-apps).

### <a name="display-device-categories---814654--"></a>Mostrar categorias dos dispositivos <!--814654-->
Agora pode ver a categoria do dispositivo como uma coluna na lista de dispositivos. Também pode editar a categoria a partir da secção de propriedades do painel de propriedades do dispositivo. Veja [Como adicionar uma aplicação ao Intune](/intune-azure/manage-apps/add-apps).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurar definições do Windows Update para Empresas <!--776716-->

O Windows como um Serviço é a nova forma de disponibilizar atualizações para o Windows 10. A partir do Windows 10, todas as novas Atualizações de Funcionalidades e Atualizações de Qualidade irão conter o conteúdo de todas as atualizações anteriores. Tal significa que, desde que instale a atualização mais recente, sabe que os dispositivos Windows 10 estão completamente atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações para não ter de aprovar atualizações individuais para grupos de dispositivos. Pode continuar a gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações e o Windows Update irá garantir que as atualizações são instaladas no momento certo. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem ao Windows Update diretamente para obterem as atualizações. Utilize o Intune para configurar e gerir **anéis de atualização do Windows 10**. Um anel de atualização contém um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Para obter detalhes, veja [Configure Windows Update for Business settings (Configurar definições do Windows Update para Empresas)](/intune-azure/configure-devices/how-to-configure-windows-update-for-business).

## <a name="january-2017"></a>Janeiro de 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Atribuir aplicações de linha de negócio se os dispositivos estiverem ou não inscritos <!--748823-->
Pode agora atribuir aplicações de linha de negócio a partir da loja aos utilizadores se os respetivos dispositivos estiverem ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, este tem de aceder ao site do Portal da Empresa para instalá-lo, em vez da aplicação Portal da Empresa. Veja [O que é a gestão de aplicações](/intune-azure/manage-apps/what-is-app-management).

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver o problema no qual os dispositivos iOS estão inativos ou a consola de administração não consegue comunicar com os mesmos
Quando os dispositivos dos utilizadores perdem o contacto com o Intune, pode dar-lhes novos passos de resolução de problemas que os ajudem a recuperar o acesso aos recursos da empresa. Consulte [Os dispositivos estão inativos ou a consola de administração não consegue comunicar com os mesmos](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Dezembro de 2016 (versão inicial)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integração da gestão de despesas de telecomunicações na pré-visualização pública do portal do Azure<!--747605-->
Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com). Para ativar esta funcionalidade no seu inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Implementar e gerir aplicações de uma loja para dispositivos iOS, Android e Windows
- Implementar e gerir aplicações de uma linha de negócio (LOB) para dispositivos iOS, Android e Windows
- Implementar e gerir aplicações compradas em volume para dispositivos iOS e Windows
- Implementar e gerir aplicações Web para dispositivos Android, iOS e Windows
- Perfis de configuração de aplicações geridas iOS
- Configurar políticas de proteção de aplicações e implementar aplicações de linha de negócio em dispositivos que não estão inscritos com o Intune
- Perfis de VPN, VPN por aplicação, Wi-Fi, e-mail e perfis de certificados
- Políticas de conformidade
- Acesso condicional para o Azure AD
- Acesso condicional para o Exchange no Local
- Inscrição de dispositivos
- Controlo de acesso baseado em funções

## <a name="deprecated-features-in-the-azure-portal"></a>Funcionalidades preteridas no portal do Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Suporte para revisão de linha por linha de identificadores de hardware
O portal do Azure não suporta a revisão de linha por linha de identificadores de hardware para números IMEI e números de série da Apple. Na consola clássica do Intune, pode importar os detalhes de um ficheiro valores separados por vírgulas (.csv) e substituir os detalhes existentes de identificadores de hardware individuais. O portal do Azure oferece uma opção única e simplificada que substitui automaticamente os detalhes de todos os identificadores de hardware ou ignora os detalhes novos para os identificadores existentes.

#### <a name="how-this-affects-you"></a>De que forma o afeta
No portal do Azure, não poderá decidir, linha por linha, os dispositivos de Identidade Internacional do Equipamento Móvel (IMEI) a atualizar. A consola clássica do Intune continuará a suportar esta funcionalidade.

#### <a name="how-to-get-ready-for-this-change"></a>Como se preparar para esta alteração
Estamos a disponibilizar estas informações com antecedência para que, se for afetado, possa avisar os seus administradores de suporte em relação a esta alteração. Esta alteração vai coincidir com a transição para o portal do Azure, antecipada para o primeiro semestre de 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Suporte para perfis predefinidos de Inscrição de Dispositivos da Empresa no DEP da Apple
O portal do Azure não suporta o perfil “predefinido” de Inscrição de Dispositivos de Empresa para números de série de dispositivos do Programa de Registo de Aparelho (DEP) da Apple. Esta funcionalidade, disponível na consola clássica do Intune, vai ser descontinuada para evitar atribuições inadvertidas de perfis. No portal do Azure, os números de série sincronizados a partir de uma conta de DEP da Apple não terão inicialmente nenhum perfil de Inscrição de Dispositivos de Empresa atribuído.

#### <a name="how-this-affects-you"></a>De que forma o afeta
No portal do Azure, não poderá definir uma política de perfil predefinida em todos os dispositivos da Apple. A consola clássica do Intune continuará a suportar esta funcionalidade.

#### <a name="how-to-get-ready-for-this-change"></a>Como se preparar para esta alteração
Estamos a disponibilizar estas informações com antecedência para que, se for afetado, possa avisar os seus administradores de suporte em relação a esta alteração. Esta situação vai coincidir com a transição para o portal do Azure, antecipada para o primeiro semestre de 2017.

