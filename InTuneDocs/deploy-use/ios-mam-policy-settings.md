---
title: "Definições de políticas de MAM para iOS | Documentos da Microsoft"
description: "Este tópico descreve as definições da política de gestão de aplicações móveis para dispositivos iOS."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d80f548f0c1382e1bd024bd31078d2a4e6366656
ms.openlocfilehash: a2130fa76f66528f6e77c720bc93286e0d01aba2


---

#  <a name="ios-mobile-app-management-policy-settings"></a>Definições de políticas de gestão de aplicações móveis para iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As definições de políticas descritas neste tópico podem ser [configuradas](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para uma política de gestão de aplicações móveis (MAM) no painel **Definições** no portal do Azure.

Existem duas categorias de definições de políticas: reposicionamento de dados e acesso. Neste tópico, o termo _**aplicações geridas por políticas**_ é utilizado para fazer referência a aplicações configuradas com políticas de MAM.

##  <a name="data-relocation-settings"></a>Definições de reposicionamento de dados

| Definição | Como utilizar | Valor predefinido |
|------|------|------|
| **Impedir cópias de segurança do iTunes e do iCloud** | Selecione **Sim** para impedir que esta aplicação crie uma cópia de segurança dos dados escolares ou profissionais para o iTunes e o iCloud. Selecione **Não** para permitir que esta aplicação crie uma cópia de segurança dos dados escolares ou profissionais para o iTunes e o iCloud.| Sim |
| **Permitir que a aplicação transfira dados para outras aplicações** | Especifique que aplicações podem receber dados desta aplicação: <ul><li> **Aplicações geridas por políticas**: permitir transferências apenas para outras aplicações geridas por políticas.</li> <li>**Todas as aplicações**: permitir a transferência para qualquer aplicação. </li> <li>**Nenhuma**: não permite a transferência de dados para nenhuma aplicação, incluindo outras aplicações geridas por políticas.</li></ul> Além disso, se definir esta opção como **Aplicações geridas por políticas** ou **Nenhuma**, a funcionalidade do iOS 9 que permite que a Pesquisa Spotlight procure dados dentro de aplicações será bloqueada. <br><br> | Todas as aplicações |
| **Permitir que a aplicação receba dados de outras aplicações** | Especifique que aplicações podem transferir dados para esta aplicação: <ul><li>**Aplicações geridas por políticas**: permitir transferências apenas a partir de outras aplicações geridas por políticas.</li><li>**Todas as aplicações**: permitir a transferência de dados a partir de qualquer aplicação.</li><li>**Nenhuma**: não permite transferências de dados a partir de nenhuma aplicação, incluindo outras aplicações geridas por políticas. | Todas as aplicações |
| **Impedir "Guardar Como"** | Selecione **Sim** para desativar a utilização da opção Guardar Como nesta aplicação. Selecione **Não** se quiser permitir a utilização da opção Guardar Como. | Não |
| **Restringir as operações de corte, cópia e colagem com outras aplicações** | Especifique quando as ações de corte, cópia e colagem podem ser utilizadas com esta aplicação. Escolha entre: <ul><li>**Bloqueado**: não permitir ações de corte, cópia e colagem entre esta aplicação e outras aplicações.</li><li>**Aplicações geridas por políticas**: permitir ações de corte, cópia e colagem entre esta aplicação e outras aplicações geridas por políticas.</li><li>**Aplicações geridas por políticas com colar em**: permitir ações de corte ou cópia entre esta aplicação e outras aplicações geridas por políticas. Permitir que os dados de qualquer aplicação sejam colados nesta aplicação.</li><li>**Qualquer aplicação**: sem restrições para ações de corte, cópia e colagem de e para esta aplicação. | Qualquer aplicação |
|**Restringir o conteúdo Web a apresentar no Managed Browser** | Selecione **Sim** para impor que as ligações Web na aplicação sejam abertas na aplicação Managed Browser. <br><br> Para os dispositivos não inscritos no Intune, as ligações Web em aplicações geridas por políticas só podem ser abertas na aplicação Managed Browser. <br><br> Se utiliza o Intune para gerir os dispositivos, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | Não |
| **Encriptar dados da aplicação** | Para aplicações geridas por políticas, os dados inativos são encriptados através do esquema de encriptação ao nível do dispositivo fornecido pelo iOS. Quando for necessário um PIN, os dados são encriptados de acordo com as definições na política de proteção de aplicações. <br><br> Aceda à documentação oficial da Apple [aqui](https://support.apple.com/HT202739) para ver quais os módulos de encriptação iOS que têm a certificação FIPS 140-2 ou a certificação FIPS 140-2 pendente. <br><br> Especifique quando os dados escolares ou profissionais são encriptados nesta aplicação. Escolha entre: <ul><li>**Quando o dispositivo está bloqueado**: todos os dados de aplicação associados a esta política são encriptados quando o dispositivo está bloqueado.</li><li>**Quando o dispositivo está bloqueado e existem ficheiros abertos**: todos os dados de aplicação associados a esta política são encriptados quando o dispositivo está bloqueado, exceto para os dados dos ficheiros atualmente abertos na aplicação.</li><li>**Após o reinício do dispositivo**: todos os dados de aplicação associados a esta política são encriptados quando o dispositivo é reiniciado, até que o dispositivo seja desbloqueado pela primeira vez.</li><li>**Utilizar as definições do dispositivo:** os dados de aplicação são encriptados com base nas predefinições no dispositivo. <br><br> Quando ativa esta definição, o utilizador tem de configurar e utilizar um PIN para aceder ao respetivo dispositivo.  Se não existir um PIN, as aplicações não serão abertas e será pedido ao utilizador para definir um PIN com a mensagem "A sua organização requer que ative primeiro um PIN do dispositivo para aceder a esta aplicação". </li></ul> | Quando o dispositivo está bloqueado |
| **Desativar a sincronização de contactos** | Selecione **Sim** para impedir que a aplicação guarde os dados na aplicação nativa Contactos no dispositivo. Se selecionar **Não**, a aplicação pode guardar os dados na aplicação nativa Contactos no dispositivo. <br><br>Ao efetuar uma eliminação seletiva para remover dados escolares ou profissionais da aplicação, os contactos sincronizados diretamente a partir da aplicação para a aplicação nativa Contactos são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, só é aplicável à aplicação Microsoft Outlook. | Não |
| **Desativar a impressão** | Selecione **Sim** para impedir que a aplicação imprima dados escolares ou profissionais. | Não |


> [!NOTE]
> Nenhuma das definições de reposicionamento de dados controla a funcionalidade de gestão Open-in da Apple em dispositivos iOS. Para gerir a funcionalidade Open-in da Apple, veja [Gerir a transferência de dados entre aplicações iOS com o Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).


## <a name="access-settings"></a>Definições de acesso

| Definição | Como utilizar | Valor predefinido |
|------|------|------|
| **Exigir PIN para acesso** | Selecione **Sim** para exigir um PIN para utilizar esta aplicação. É pedido ao utilizador para configurar este PIN da primeira vez que executar a aplicação num contexto escolar ou profissional. Valor predefinido = **Sim**.<br><br> Configure as seguintes definições para a segurança do PIN: <ul><li>**Número de tentativas antes de redefinição do PIN**: especifique o número de tentativas que o utilizador tem para introduzir o PIN com êxito, após as quais será necessário repô-lo. Valor predefinido = **5**.</li><li> **Permitir PIN simples**: selecione **Sim** se pretende permitir que os utilizadores utilizem sequências de PIN simples, como 1234 ou 1111. Selecione **Não** para os impedir de utilizar sequências simples. Valor predefinido = **Sim**. </li><li> **Comprimento do PIN**: especifique o número mínimo de dígitos numa sequência de PIN. Valor predefinido = **4**. </li><li> **Permitir impressões digitais em vez do PIN (iOS 8.0+)**: selecione **Sim** para permitir que o utilizador utilize o [Touch ID](https://support.apple.com/en-us/HT201371) em vez de um PIN para aceder à aplicação. Valor predefinido = **Sim**.<br><br> Em dispositivos iOS, pode permitir que o utilizador prove a sua identidade através da utilização do [Touch ID](https://support.apple.com/en-us/HT201371) em vez de um PIN. Quando o utilizador tentar utilizar esta aplicação com a respetiva conta escolar ou profissional, é-lhe pedido para fornecer a identidade de impressão digital em vez de introduzir um PIN. </li></ul>| Exigir PIN: Sim <br><br> Tentativas de reposição do PIN: 5 <br><br> Permitir PIN simples: Sim <br><br> Comprimento do PIN: 4 <br><br> Permitir impressão digital: Sim |
| **Exigir credenciais da empresa para obter acesso** | Selecione **Sim** para exigir que o utilizador inicie sessão com a respetiva conta escolar ou profissional em vez de introduzir um PIN de acesso à aplicação. Se definir esta opção como **Sim**, substitui os requisitos para PIN ou Touch ID.  | Não |
| **Bloquear a execução de aplicações geridas em dispositivos com jailbreak ou root** |  Selecione **Sim** para bloquear a execução desta aplicação em dispositivos com jailbreak ou root. O utilizador continuará a poder utilizar esta aplicação para tarefas pessoais, mas terá de utilizar um dispositivo diferente para aceder aos dados escolares ou profissionais nesta aplicação. | Sim |
| **Verificar novamente os requisitos de acesso após (minutos)** | Configure as seguintes definições: <ul><li>**Tempo limite**: especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados. Valor predefinido = **30** minutos.</li><li>**Período de tolerância offline**: se o dispositivo estiver offline, especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados. Valor predefinido = **720** minutos (12 horas).</li></ul>| Tempo limite: 30 <br><br> Offline: 720 |
| **Intervalo offline antes de os dados da aplicação serem eliminados (dias)** | Os dados escolares ou profissionais nesta aplicação poderão ser eliminados se um dispositivo tiver estado offline durante um período de tempo superior a um determinado valor. Especifique o número de dias que um dispositivo pode ficar offline antes de os dados escolares ou profissionais serem removidos do dispositivo. <br><br> | 90 dias |



<!--HONumber=Dec16_HO3-->


