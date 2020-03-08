---
title: Quadro de proteção de dados utilizando políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como as Políticas de Proteção de Aplicações (APP) garantem que os dados de uma organização permanecem seguros ou contidos numa aplicação gerida, independentemente de o dispositivo estar matriculado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: smithre4
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 075f4bdd52bfa72e2eaed051c765d77d7b80e6fd
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856250"
---
# <a name="data-protection-framework-using-app-protection-policies"></a>Quadro de proteção de dados utilizando políticas de proteção de aplicações 

À medida que mais organizações implementam estratégias de dispositivos móveis para aceder a dados de trabalho ou escolares, a proteção contra fugas de dados torna-se primordial. A solução de gestão de aplicações móveis da Intune para proteger contra fugas de dados é políticas de proteção de aplicações (APP). A APP são regras que garantem que os dados de uma organização permanecem seguros ou contidos numa aplicação gerida, independentemente de o dispositivo estar matriculado. Para mais informações, consulte a visão geral das políticas de proteção de [aplicações](~/apps/app-protection-policy.md). 

Ao configurar políticas de proteção de aplicações, o número de várias configurações e opções permite que as organizações adaptem a proteção às suas necessidades específicas. Devido a esta flexibilidade, pode não ser óbvio qual a permutação das definições políticas necessárias para implementar um cenário completo. Para ajudar as organizações a priorizar os esforços de endurecimento do ponto final do cliente, a Microsoft introduziu uma nova taxonomia para configurações de [segurança no Windows 10](https://aka.ms/secconframework), e a Intune está a aproveitar uma taxonomia semelhante para o seu quadro de proteção de dados APP para gestão de aplicações móveis.  

O quadro de configuração de proteção de dados da APP é organizado em três cenários distintos de configuração: 

- Proteção de dados básica seleto de nível 1 – a Microsoft recomenda esta configuração como a configuração mínima de proteção de dados para um dispositivo empresarial. 

- Proteção de dados melhorada pela empresa nível 2 – a Microsoft recomenda esta configuração para dispositivos onde os utilizadores acedem a informações confidenciais ou confidenciais. Esta configuração é aplicável à maioria dos utilizadores móveis que acedem a dados do trabalho ou da escola. Alguns dos controlos podem ter impacto na experiência do utilizador. 

- Nivete de alta proteção de dados da empresa de nível 3 – a Microsoft recomenda esta configuração para dispositivos geridos por uma organização com uma equipa de segurança maior ou mais sofisticada, ou para utilizadores ou grupos específicos que estão em risco único (como um exemplo, uma organização identificaram os utilizadores que lidam com dados cujo roubo teria impacto direto e grave no seu preço de stock). Uma organização suscetível de ser alvo de adversários bem financiados e sofisticados deve aspirar a esta configuração. 

## <a name="app-data-protection-framework-deployment-methodology"></a>Metodologia de implementação do quadro de proteção de dados da APP 

Tal como acontece com qualquer implementação de novos softwares, funcionalidades ou configurações, a Microsoft recomenda investir numa metodologia de anel para testar a validação antes de implementar o quadro de proteção de dados da APP. A definição de anéis de implantação é geralmente um evento único (ou pelo menos pouco frequente), mas a TI deve revisitar estes grupos para garantir que a sequenciação ainda está correta. 

A Microsoft recomenda a seguinte abordagem do anel de implementação para a estrutura de proteção de dados da APP: 

| Anel de implantação  | Inquilino  | Equipas de avaliação  | Saída  | Linha do tempo  |
|--------------------|------------------------|-------------------------------------------------------------------|----------------------------------------------------------|----------------------------------------|
| Garantia da Qualidade  | Inquilino de pré-produção  | Proprietários de capacidademóvel, Segurança, Avaliação de Risco, Privacidade, UX  | Validação do cenário funcional, projeto de documentação  | 0-30 dias  |
| Pré-visualização  | Inquilino de produção  | Proprietários de capacidademóvel, UX  | Validação do cenário do utilizador final, documentação virada para o utilizador  | 7-14 dias, pós Garantia de Qualidade  |
| Produção  | Inquilino de produção  | Proprietários de capacidade móvel, balcão de ajuda de TI  | N/D  | 7 dias a várias semanas, pós Pré-visualização  |

Como indica o quadro acima indicado, todas as alterações às Políticas de Proteção de Aplicações devem ser realizadas primeiro num ambiente de pré-produção para compreender as implicações da definição de políticas. Uma vez concluídos os testes, as alterações podem ser transferidas para a produção e aplicadas a um subconjunto de utilizadores de produção, geralmente, ao departamento de TI e a outros grupos aplicáveis. E, finalmente, o lançamento pode ser concluído para o resto da comunidade de utilizadores móveis. O lançamento para a produção pode demorar mais tempo, dependendo da escala de impacto no que diz respeito à alteração. Se não houver impacto do utilizador, a alteração deve ser lançada rapidamente, enquanto que, se a alteração resultar no impacto do utilizador, o lançamento poderá ter de ser mais lento devido à necessidade de comunicar alterações à população utilizadora. 

Ao testar alterações numa APP, esteja ciente do tempo de [entrega](~/apps/app-protection-policy-delivery.md). O estado da entrega de APP para um determinado utilizador pode ser monitorizado. Para mais informações, consulte como monitorizar as políticas de [proteção de aplicações](~/apps/app-protection-policies-monitor.md). 

As definições individuais de APP para cada aplicação podem ser validadas em dispositivos que utilizem o Edge e o URL *sobre:Intunehelp*. Para mais informações, consulte os registos de proteção de [aplicações do cliente E](~/apps/app-protection-policy-settings-log.md) [gerencie o acesso à Web utilizando](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs)o Microsoft Edge com o Microsoft Intune . 

## <a name="app-data-protection-framework-settings"></a>Definições do quadro de proteção de dados da APP 

As seguintes definições de Política de Proteção de Aplicações devem ser ativadas para as aplicações aplicáveis e atribuídas a todos os utilizadores móveis. Para obter mais informações sobre cada definição de política, consulte as definições de políticas de proteção de [aplicações iOS](~/apps/app-protection-policy-settings-ios.md) e as definições de políticas de proteção de [aplicações Android](~/apps/app-protection-policy-settings-android.md). 

A Microsoft recomenda rever e categorizar cenários de utilização e, em seguida, configurar os utilizadores usando a orientação prescritiva para esse nível. Como em qualquer quadro, as configurações dentro de um nível correspondente podem ter de ser ajustadas com base nas necessidades da organização, uma vez que a proteção de dados deve avaliar o ambiente de ameaça, o apetite de risco e o impacto na usabilidade.  

### <a name="apps-to-include-in-the-app-protection-policies"></a>Apps a incluir nas Políticas de Proteção de Aplicações  

Para cada Política de Proteção de Aplicações, devem ser incluídas as seguintes aplicações principais da Microsoft: 

- Microsoft Edge 
- Excel 
- Escritório 
- OneDrive 
- OneNote 
- Outlook 
- PowerPoint 
- Microsoft Teams 
- Microsoft To-Do
- Word 
- Microsoft SharePoint 

As políticas devem incluir outras aplicações da Microsoft baseadas nas necessidades empresariais, aplicações públicas adicionais de terceiros que integraram o Intune SDK utilizado na organização, bem como aplicações de linha de negócio que integraram o [Intune SDK](~/developer/app-sdk.md) (ou foram embrulhados). 

### <a name="level-1-enterprise-basic-data-protection"></a>Proteção de dados básicos da empresa de nível 1 

O nível 1 é a configuração mínima de proteção de dados para um dispositivo móvel empresarial. Esta configuração substitui a necessidade de políticas básicas de acesso ao dispositivo Exchange Online, exigindo que um PIN aceda a dados de trabalho ou de escola, encriptando os dados do trabalho ou da conta escolar, e fornecendo a capacidade de limpar seletivamente os dados escolares ou de trabalho. No entanto, ao contrário das políticas de acesso ao dispositivo Exchange Online, as definições abaixo da Política de Proteção de Aplicações aplicam-se a todas as aplicações selecionadas na política, garantindo assim que o acesso de dados está protegido para além dos cenários de mensagens móveis. 

As políticas no nível 1 impõem um nível razoável de acesso a dados, minimizando o impacto para os utilizadores e espelham as definições de proteção de dados padrão e requisitos de acesso ao criar uma Política de Proteção de Aplicações dentro do Microsoft Endpoint Manager.  

#### <a name="data-protection"></a>Proteção de dados 

| Definição | Descrição da definição |             Valor  |             Platform        |
|-----------------|--------------------------------------------------------|-----------------------|----------------------------------------|
| Transferência de Dados |             Dados de backup org para...  |             Permitir  |             iOS/iPadOS, Android        |
| Transferência de Dados |       Envie dados org para outras aplicações  |             Todas as aplicações  |             iOS/iPadOS, Android        |
| Transferência de Dados |       Receber dados de outras apps  |             Todas as aplicações  |             iOS/iPadOS, Android        |
| Transferência de Dados |       Restringir corte, cópia e pasta entre apps  |             Qualquer aplicação  |             iOS/iPadOS, Android        |
| Transferência de Dados |       Teclados de terceiros  |             Permitir  |             iOS/iPadOS        |
| Transferência de Dados |       Teclados aprovados  |             Não é necessário  |             Android        |
| Transferência de Dados |       Captura de ecrã e Google Assistant  |             Permitir  |             Android        |
| Encriptação |             Criptografe dados org  |             Exigir  |             iOS/iPadOS, Android        |
| Encriptação |       Criptografe dados org em dispositivos matriculados  |             Exigir  |             Android        |
| Funcionalidade  |             Sync app com app de contactos nativos  |             Permitir  |             iOS/iPadOS, Android        |
| Funcionalidade  |       Imprimir dados org  |             Permitir  |             iOS/iPadOS, Android        |
| Funcionalidade  |       Restringir a transferência de conteúdos web com outras aplicações  |             Qualquer aplicação  |             iOS/iPadOS, Android        |
| Funcionalidade  |       Notificações de dados org  |             Permitir  |             iOS/iPadOS, Android        |

#### <a name="access-requirements"></a>Requisitos de acesso 

| Definição  | Valor  | Platform  | Notas  |
|----------------------------------------------------------------|---------------|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PIN para acesso  | Exigir  | iOS/iPadOS, Android  |   |
| Tipo PIN  | Numérica  | iOS/iPadOS, Android  |   |
| PIN simples  | Permitir  | iOS/iPadOS, Android  |   |
| Selecione comprimento pin mínimo  | 4  | iOS/iPadOS, Android  |   |
| Biométrico em vez de PIN para acesso  | Permitir  | iOS/iPadOS, Android  |   |
| Sobrepor biométrico em vez de PIN para acesso  | Exigir  | iOS/iPadOS, Android  |   |
| Tempo limite (minutos de atividade)  | 720  | iOS/iPadOS, Android  |   |
| Id do rosto em vez de PIN para acesso  | Permitir  | iOS/iPadOS  |   |
| PIN reset após o número de dias  | Não  | iOS/iPadOS, Android  |   |
| Pin de aplicativo quando o PIN do dispositivo é definido  | Exigir  | iOS/iPadOS, Android  | Se o dispositivo estiver matriculado no Intune, os administradores podem considerar a definição deste para "Não necessário" se estiverem a impor um PIN de dispositivo forte através de uma política de conformidade do dispositivo.  |
| Credenciais de conta de trabalho ou de escola para acesso  | Não é necessário  | iOS/iPadOS, Android  |   |
| Volte a verificar os requisitos de acesso após (minutos de inatividade)  | 30  | iOS/iPadOS, Android  |   |

#### <a name="conditional-launch"></a>Iniciação condicional 

| Definição | Descrição da definição |          Valor / Ação  |          Platform        | Notas |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Condições da aplicação |       Tentativas max PIN  |          5 / Pin de reset  |          iOS/iPadOS, Android  |                  |
| Condições da aplicação |       Período de graça offline  |          720 / Acesso ao bloco (minutos)  |          iOS/iPadOS, Android  |                  |
| Condições da aplicação |       Período de graça offline  |          90 / Dados de limpeza (dias)  |          iOS/iPadOS, Android  |                  |
| Condições do dispositivo  |       Dispositivos encarcerados/enraizados  |        Acesso n/A / Bloco  |          iOS/iPadOS, Android  |                  |
| Condições do dispositivo  |       Atestação do dispositivo SafetyNet  |          Integridade básica e dispositivos certificados / Acesso ao bloco  |          Android  |          <p>Esta definição configura o Attestation SafetyNet da Google em dispositivos de utilizador final. A integridade básica valida a integridade do dispositivo. Dispositivos enraizados, emuladores, dispositivos virtuais e dispositivos com sinais de adulteração falham a integridade básica. </p><p> A integridade básica e os dispositivos certificados validam a compatibilidade do dispositivo com os serviços da Google. Apenas dispositivos não modificados certificados pela Google podem passar este cheque.</p>  |
| Condições do dispositivo  |       Exigir uma varredura de ameaças em apps  |        Acesso n/A / Bloco  |          Android  |          Esta definição garante que a verificação de Apps de Verificação da Google é ligada para dispositivos de utilizador final. Se configurado, o utilizador final será bloqueado do acesso até ativar a aplicação da Google no seu dispositivo Android.        |

#### <a name="level-2-enterprise-enhanced-data-protection"></a>Empresa de nível 2 melhorou a proteção de dados 

O nível 2 é a configuração de proteção de dados recomendada como padrão para dispositivos onde os utilizadores acedem a informações mais sensíveis. Estes dispositivos são um alvo natural nas empresas de hoje. Estas recomendações não assumem um grande pessoal de profissionais de segurança altamente qualificados, pelo que devem ser acessíveis à maioria das organizações empresariais. Esta configuração expande-se sobre a configuração no Nível 1, restringindo cenários de transferência de dados e exigindo uma versão mínima do sistema operativo. 

As definições de política aplicadas no nível 2 incluem todas as definições de política recomendadas para o nível 1 e apenas adiciona ou atualiza as definições de política abaixo para implementar mais controlos e uma configuração mais sofisticada do que o nível 1. Embora estas definições possam ter um impacto ligeiramente maior para os utilizadores ou para as aplicações, impõem um nível de proteção de dados mais proporcional aos riscos que os utilizadores enfrentam com acesso a informações sensíveis em dispositivos móveis. 

#### <a name="data-protection"></a>Proteção de dados 

| Definição | Descrição da definição |             Valor  |             Platform        | Notas |
|---------------|----------------------------------------------------------|-----------------------------------------------|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Transferência de Dados |       Dados de backup org para...  |          Bloqueio  |          iOS/iPadOS, Android  |                  |
| Transferência de Dados |       Envie dados org para outras aplicações  |          Aplicativos geridos por políticas  |          iOS/iPadOS, Android  |          <p>Com o iOS/iPadOS, os administradores podem configurar este valor como "Aplicações geridas por políticas", "Aplicações geridas por políticas com partilha de OS", ou "Aplicações geridas por políticas com filtragem Open-In/Share". </p><p>As aplicações geridas pela política com partilha de OS estão disponíveis quando o dispositivo também está matriculado no Intune. Esta definição permite a transferência de dados para outras aplicações geridas por políticas, bem como transferências de ficheiros para outras aplicações que tenham sido geridas pela Intune. </p><p>Aplicações geridas por políticas com filtros de filtragem Open-In/Share os diálogos OS Open-in/Share para apenas exibir aplicações geridas pela política. </p><p> Para mais informações, consulte as definições da política de proteção de [aplicações iOS](~/apps/app-protection-policy-settings-ios.md).</p> |
| Transferência de Dados |       Guardar cópias dos dados org  |          Bloqueio  |          iOS/iPadOS, Android  |                  |
| Transferência de Dados |       Permitir que os utilizadores guardem cópias para serviços selecionados  |          OneDrive para negócios, SharePoint Online |          iOS/iPadOS, Android  |                  |
| Transferência de Dados |       Restringir corte, cópia e pasta entre apps  |          Aplicativos geridos pela política com pasta em  |          iOS/iPadOS, Android  |                  |
| Transferência de Dados |       Captura de ecrã e Google Assistant  |          Bloqueio  |          Android  |                  |
| Funcionalidade |       Restringir a transferência de conteúdos web com outras aplicações  |          Microsoft Edge  |          iOS/iPadOS, Android  |                  |
| Funcionalidade |       Notificações de dados org  |          Bloquear dados org  |          iOS/iPadOS, Android  |          Para obter uma lista de aplicações que suportem esta definição, consulte as definições de políticas de proteção de [aplicações iOS](~/apps/app-protection-policy-settings-ios.md) e as definições de políticas de proteção de [aplicações Android.](~/apps/app-protection-policy-settings-android.md)       |


#### <a name="conditional-launch"></a>Iniciação condicional

| Definição | Descrição da definição |          Valor / Ação  |          Platform        | Notas |
|--------------------|----------------------------|-----------------------------------------------------------|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Condições do dispositivo  |       Versão Min OS  |          *Formato: Major.Minor.Construa <br>Exemplo: 12.4.4* / Acesso ao bloco |          iOS/iPadOS        | A Microsoft recomenda configurar a versão principal do iOS mínimo para combinar com as versões suportadas para iOS para aplicações da Microsoft.   As aplicações da Microsoft suportam uma abordagem N-1 onde n é a versão atual do iOS. Para valores de versão menor estonteantes e de construção, a Microsoft recomenda garantir que os dispositivos estão atualizados com as respetivas atualizações de segurança. Consulte [as atualizações](https://support.apple.com/en-us/HT201222) de segurança da Apple para as mais recentes recomendações da Apple |
| Condições do dispositivo  |       Versão Min OS  |          *Formato: Major.Minor<br> Exemplo: 8.0* / Acesso ao bloco   |          Android        | A Microsoft recomenda configurar a versão principal do Android mínima para combinar com as versões Android suportadas para aplicações da Microsoft. Os OEMs e dispositivos que aderem ao Android Enterprise recomendam que os requisitos devem suportar o lançamento de envio atual + uma atualização de letra.   Atualmente, o Android recomenda o Android 8.0 e mais tarde para os trabalhadores do conhecimento.   Consulte [os requisitos recomendados](https://www.android.com/enterprise/recommended/requirements/) para android enterprise para as mais recentes recomendações do Android |
| Condições do dispositivo  |       Versão de patch de min  |          *Formato: YYYY-MM-DD <br> Exemplo: 2020-01-01* / Acesso ao bloco  |          Android        | Os dispositivos Android podem receber patches de segurança mensais, mas o lançamento depende de OEMs e/ou transportadoras. As organizações devem garantir que os dispositivos Android implantados recebem atualizações de segurança antes de implementar esta definição. Consulte os [Boletims](https://source.android.com/security/bulletin/) de Segurança Android para ver os mais recentes lançamentos de patch.  |

#### <a name="level-3-enterprise-high-data-protection"></a>Alta proteção de dados da empresa de nível 3 

O nível 3 é a configuração de proteção de dados recomendada como padrão para organizações com grandes e sofisticadas organizações de segurança, ou para utilizadores e grupos específicos que serão exclusivamente visados por adversários. Tais organizações são tipicamente alvo de adversários bem financiados e sofisticados, e como tal merecem os constrangimentos e controlos adicionais descritos. Esta configuração expande-se sobre a configuração no Nível 2, restringindo cenários adicionais de transferência de dados, aumentando a complexidade da configuração PIN e adicionando a deteção de ameaças móveis.  

As definições de política aplicadas no nível 3 incluem todas as definições de política recomendadas para os níveis 2 e 1 e apenas adiciona ou atualiza as definições de política abaixo para implementar configuração e controlos rigorosos de proteção de dados. Estas definições políticas podem ter um impacto potencialmente significativo para os utilizadores ou para as aplicações, aplicando um nível de segurança proporcional aos riscos que as organizações-alvo enfrentam.  

#### <a name="data-protection"></a>Proteção de dados

| Definição | Descrição da definição |             Valor  |             Platform        | Notas |
|---------------|---------------------------------------|----------------------------------------|--------------------------------------|---------------------------------------------------------------------------------------------------------|
| Transferência de dados |       Receber dados de outras apps  |          Aplicativos geridos por políticas  |          iOS/iPadOS, Android         |  |
| Transferência de dados |       Teclados de terceiros  |          Bloqueio  |          iOS/iPadOS        | No iOS, isto bloqueia que todos os teclados de terceiros funcionem dentro da aplicação.  |
| Transferência de dados |       Teclados aprovados  |          Exigir  |          Android        | Com o Android, os teclados devem ser selecionados para serem utilizados com base nos seus dispositivos Android implantados.  |
| Transferência de dados |       Selecione teclados para aprovar  |          *adicionar/remover teclados*  |          Android        | Com o Android, os teclados devem ser selecionados para serem utilizados com base nos seus dispositivos Android implantados.  |
| Funcionalidade |       Imprimir dados org  |          Bloqueio  |          iOS/iPadOS, Android         |  |

#### <a name="access-requirements"></a>Requisitos de acesso

|       Definição  |          Valor  |          Platform  |
|-----------------------------------------------------------|--------------------|---------------------------------|
|       PIN simples  |          Bloqueio  |          iOS/iPadOS, Android  |
|       Selecione comprimento pin mínimo  |          6  |          iOS/iPadOS, Android  |
|       PIN reset após o número de dias  |          Sim  |          iOS/iPadOS, Android  |
|       Número de dias  |          365  |          iOS/iPadOS, Android  |

#### <a name="conditional-launch"></a>Iniciação condicional

| Definição | Descrição da definição |          Valor / Ação  |          Platform        | Notas |
|----------------------------|--------------------------------------|-------------------|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Condições do dispositivo  |          Dispositivos com jailbreak/rooting  |        Dados de N/A / Limpeza  |          iOS/iPadOS, Android        |  |
|       Condições do dispositivo  |          Max permitiu o nível de ameaça  |          Acesso seguro / Bloco  |          iOS/iPadOS, Android        | <p>Dispositivos não matriculados podem ser inspecionados para obter ameaças usando a Defesa de Ameaças Móveis. Para mais informações, consulte [mobile threat defense para dispositivos não matriculados](https://aka.ms/mtdmamdocs).      </p><p>     Se o dispositivo estiver matriculado, esta definição pode ser ignorada a favor da implementação da Defesa de Ameaças Móveis para dispositivos matriculados. Para mais informações, consulte [mobile threat defense para dispositivos matriculados](~/protect/mtd-device-compliance-policy-create.md).</p> |

## <a name="next-steps"></a>Próximos passos

Os administradores podem incorporar os níveis de configuração acima indicados na sua metodologia de implantação de anéis para testes e utilização da produção, importando os [modelos json](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) de configuração da política de proteção de aplicações [Intune Intune com os scripts PowerShell da Intune](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="see-also"></a>Veja também

- [Como criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)
- [Definições de política de proteção de aplicativos Android disponíveis com microsoft Intune](app-protection-policy-settings-android.md)
- [Definições de política de proteção de aplicações iOS/iPadOS disponíveis com microsoft Intune](app-protection-policy-settings-ios.md)
- As aplicações de terceiros como a aplicação móvel do Salesforce funcionam com o Intune de formas específicas para proteger os dados empresariais. Para obter mais informações sobre como a aplicação Salesforce em particular funciona com o Intune (incluindo configurações de aplicações de MDM), veja [Aplicação Salesforce e Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
