---
title: "Edição antecipada | Documentos da Microsoft"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 0ba6695b595849f72eb44d8e6f095e8b1aae39eb
ms.lasthandoff: 03/10/2017


---


# <a name="the-early-edition-for-microsoft-intune---march-2017"></a>A edição antecipada do Microsoft Intune – março de 2017

O **Edição Antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
> As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nova experiência de utilizador da aplicação Portal da Empresa para Android<!--621622-->

A aplicação Portal da Empresa para Android irá atualizar a respetiva interface de utilizador para obter um aspeto mais moderno e a melhor experiência de utilizador. As atualizações relevantes são:

- Cores: os cabeçalhos dos separadores do Portal da Empresa têm as cores da imagem corporativa definida pelas TI.
- Aplicações: no separador **Aplicações**, os botões **Aplicações em Destaque** e **Todas as Aplicações** são atualizados.
- Pesquisar: no separador **Aplicações**, o botão **Pesquisar** é um botão de ação flutuante.
- Navegar em Aplicações: a vista **Todas as Aplicações** mostra uma vista com os separadores **Em Destaque**, **Todas** e **Categorias** para uma navegação mais fácil.
- Suporte: os separadores **Os Meus Dispositivos** e **Contactar TI** são atualizados para melhorar a legibilidade.

Pode encontrar mais detalhes sobre estas alterações na [página de atualizações da IU de aplicações] (whats-new-in-intune-app-ui.md].

## <a name="notices"></a>Avisos

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Suporte melhorado para os utilizadores do Android sediados na China<!--720444-->

Devido à ausência da Google Play Store na China, os dispositivos Android têm de obter aplicações a partir de mercados chineses. O Portal da Empresa suportará este fluxo de trabalho ao redirecionar os utilizadores do Android na China para transferirem as aplicações Portal da Empresa e Outlook a partir de lojas de aplicações locais. Deste modo, irá melhorar a experiência do utilizador quando as políticas de Acesso Condicional são ativadas, tanto para a Gestão de Dispositivos Móveis como para a Gestão de Aplicações Móveis. As aplicações Portal da Empresa e Outlook para Android estão disponíveis nas seguintes lojas de aplicações chinesas: 

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->

A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS/macOS. Veja o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure <!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Se tiver dúvidas sobre a linha cronológica para a migração do inquilino, contacte a nossa equipa de migração através do e-mail [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->

Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="improvements-to-device-actions-report---677150--"></a>Melhorias ao relatório de Ações de Dispositivos<!--677150-->

Melhoramos o relatório de Ações de Dispositivos para um melhor desempenho. Além disso, agora pode filtrar o relatório por estado. Por exemplo, pode filtrar o relatório para mostrar apenas as ações de dispositivo que foram concluídas.

### <a name="actions-for-non-compliance---730266--"></a>Ações de não conformidade <!--730266-->

**Ações de não conformidade** é uma nova funcionalidade de políticas de conformidade que lhe permite tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->

Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](/intune-azure/manage-apps/add-apps).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Atribuir aplicações de LOB a utilizadores com dispositivos não inscritos <!--748823-->

Pode agora atribuir aplicações de linha de negócio a partir da loja aos utilizadores quer os respetivos dispositivos estejam ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, este tem de aceder ao site do Portal da Empresa para instalá-lo, em vez da aplicação Portal da Empresa.

### <a name="new-compliance-reports---846671--"></a>Novos relatórios de conformidade <!--846671-->

Tem agora relatórios de conformidade que lhe dão a postura de conformidade dos dispositivos na sua empresa e lhe permitem rapidamente resolver problemas relacionados com a conformidade encontrados pelos utilizadores. Pode ver informações sobre o

- Estado de conformidade geral dos dispositivos
- Estado de conformidade de uma definição individual
- Estado de conformidade de uma política individual

Também pode utilizar estes relatórios para desagregar um dispositivo individual para ver definições e políticas específicas que afetam esse dispositivo.

### <a name="additional-windows-10-upgrade-paths---903672--"></a>Caminhos de atualização do Windows 10 adicionais<!--903672-->

Agora, pode criar uma política de atualização de edição para atualizar os dispositivos para as seguintes edições do Windows 10 adicionais:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->

Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal de pré-visualização do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.

