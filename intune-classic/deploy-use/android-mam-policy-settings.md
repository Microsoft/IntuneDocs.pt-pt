---
title: "Definições de políticas de MAM para Android | Documentos da Microsoft"
description: "Este tópico descreve as definições da política de gestão de aplicações móveis para dispositivos Android."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 017c316ce102b71b3ef9552d8fe69181b79473de
ms.contentlocale: pt-pt
ms.lasthandoff: 05/31/2017


---

# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Definições de políticas de proteção de aplicações Android no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As definições da política de aplicação descritas neste tópico podem ser [configuradas](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) no painel **Definições** no portal do Azure.
Existem duas categorias de definições de políticas: reposicionamento de dados e acesso. Neste tópico, o termo _**aplicações geridas por políticas**_ menciona as aplicações configuradas com políticas de proteção de aplicações.

##  <a name="data-relocation-settings"></a>Definições de reposicionamento de dados

| Definição | Como utilizar | Valor(es) predefinido(s) |
|------|------|------|
| **Impedir cópias de segurança Android** | Selecione **Sim** para impedir que esta aplicação crie uma cópia de segurança dos dados escolares ou profissionais no [Serviço de Cópia de Segurança do Android](https://developer.android.com/google/backup/index.html). Selecione **Não** para permitir que esta aplicação crie uma cópia de segurança dos dados escolares ou profissionais.| Sim |
| **Permitir que a aplicação transfira dados para outras aplicações** | Especifique que aplicações podem receber dados desta aplicação: <ul><li> **Aplicações geridas por políticas**: permitir transferências apenas para outras aplicações geridas por políticas.</li> <li>**Todas as aplicações**: permitir a transferência para qualquer aplicação. </li> <li>**Nenhuma**: não permite a transferência de dados para nenhuma aplicação, incluindo outras aplicações geridas por políticas.</li></ul> <p>Existem algumas aplicações e serviços isentos aos quais o Intune poderá permitir a transferência de dados. Veja [Isenções de transferência de dados](#Data-transfer-exemptions) para obter uma lista completa das aplicações e dos serviços.| Todas as aplicações |
| **Permitir que a aplicação receba dados de outras aplicações** | Especifique que aplicações podem transferir dados para esta aplicação: <ul><li>**Aplicações geridas por políticas**: permitir transferências apenas a partir de outras aplicações geridas por políticas.</li><li>**Todas as aplicações**: permitir a transferência de dados a partir de qualquer aplicação.</li><li>**Nenhuma**: não permite transferências de dados a partir de nenhuma aplicação, incluindo outras aplicações geridas por políticas. </li></ul> <p>Existem algumas aplicações e serviços isentos a partir dos quais o Intune poderá permitir a transferência de dados. Veja [Isenções de transferência de dados](#Data-transfer-exemptions) para obter uma lista completa das aplicações e dos serviços. | Todas as aplicações |
| **Impedir "Guardar Como"** | Selecione **Sim** para desativar a utilização da opção Guardar Como nesta aplicação. Selecione **Não** se quiser permitir a utilização da opção Guardar Como. <p><br>**Selecionar os serviços de armazenamento nos quais os dados empresariais podem ser guardados** <br>Os utilizadores são capazes de guardar nos serviços selecionados (OneDrive para Empresas, SharePoint e Armazenamento Local). Todos os outros serviços serão bloqueados.</p> | Não <br><br> 0 selecionados |
| **Restringir as operações de corte, cópia e colagem com outras aplicações** | Especifique quando as ações de corte, cópia e colagem podem ser utilizadas com esta aplicação. Escolha entre: <ul><li>**Bloqueado**: não permitir ações de corte, cópia e colagem entre esta aplicação e outras aplicações.</li><li>**Aplicações geridas por políticas**: permitir ações de corte, cópia e colagem entre esta aplicação e outras aplicações geridas por políticas.</li><li>**Aplicações geridas por políticas com colar em**: permitir ações de corte ou cópia entre esta aplicação e outras aplicações geridas por políticas. Permitir que os dados de qualquer aplicação sejam colados nesta aplicação.</li><li>**Qualquer aplicação**: sem restrições para ações de corte, cópia e colagem de e para esta aplicação. | Qualquer aplicação |
|**Restringir o conteúdo Web a apresentar no Managed Browser** | Selecione **Sim** para impor que as ligações Web na aplicação sejam abertas na aplicação Managed Browser. <br><br> Para os dispositivos não inscritos no Intune, as ligações Web em aplicações geridas por políticas só podem ser abertas na aplicação Managed Browser. <br><br> Se utiliza o Intune para gerir os dispositivos, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | Não |
| **Encriptar dados da aplicação** | Selecione **Sim** para ativar a encriptação de dados escolares ou profissionais nesta aplicação. O Intune utiliza um esquema de encriptação OpenSSL, AES de 128 bits juntamente com o sistema Android Keystore para encriptar dados da aplicação em segurança. Os dados são encriptados de modo síncrono durante as tarefas de E/S de ficheiros. Os conteúdos no armazenamento do dispositivo são sempre encriptados. <br><br> O método de encriptação **não** tem certificação FIPS 140-2.  | Sim |
| **Desativar a sincronização de contactos** | Selecione **Sim** para impedir que a aplicação guarde os dados na aplicação nativa Contactos no dispositivo. Se selecionar **Não**, a aplicação pode guardar os dados na aplicação nativa Contactos no dispositivo. <br><br>Ao efetuar uma eliminação seletiva para remover dados escolares ou profissionais da aplicação, os contactos sincronizados diretamente a partir da aplicação para a aplicação nativa Contactos são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, só é aplicável à aplicação Microsoft Outlook. | Não |
| **Desativar a impressão** | Selecione **Sim** para impedir que a aplicação imprima dados escolares ou profissionais. | Não |

  >[!NOTE]
  >O método de encriptação para a definição **Encriptar dados da aplicação** **não** tem certificação FIPS 140-2.


  ## <a name="data-transfer-exemptions"></a>Isenções de transferência de dados

  Existem algumas aplicações e serviços de plataforma isentos aos quais a política de proteção de aplicações do Intune poderá permitir a transferência de dados. Por exemplo, todas as aplicações otimizadas pelo Intune no Android têm de conseguir transferir dados de e para a Síntese de Voz Google, para que o texto do ecrã do seu dispositivo móvel possa ser lido em voz alta. Esta lista está sujeita a alterações e reflete as aplicações e serviços considerados úteis para produtividade segura.

  ### <a name="full-exemptions"></a>Isenções completas

  Estas aplicações e serviços têm permissão total para transferir dados de e para aplicações geridas pelo Intune.

  |Nome da aplicação/serviço | Descrição |
  | ------ | ---- |
  | com.android.phone | Aplicação de telefone nativa
  | com.android.vending | Google Play Store |
  | com.android.documentsui | Seletor de Documentos do Android|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html), que é necessário para muitas aplicações, incluindo o Outlook. |
  | com.android.webview |[WebView](https://developer.android.com/reference/android/webkit/WebView.html), que é necessário para muitas aplicações, incluindo o Outlook.|
  | com.google.android.tts | Síntese de Voz Google |
  | com.android.providers.settings | Definições de sistema do Android |
  | com.azure.authenticator | Aplicação Azure Authenticator, que é necessária para uma autenticação com êxito em muitos cenários. |
  | com.microsoft.windowsintune.companyportal | Intune Portal da Empresa|

  ### <a name="conditional-exemptions"></a>Isenções condicionais
  Estas aplicações e serviços só têm permissão para transferir dados de e para aplicações geridas pelo Intune em determinadas condições.

  |Nome da aplicação/serviço | Descrição | Condição de isenção|
  | ------ | ---- | --- |
  | com.android.chrome | Browser Google Chrome | O Chrome é utilizado para alguns componentes WebView no Android 7.0+ e nunca é ocultado da vista. No entanto, o fluxo de dados de e para a aplicação será sempre restringido.
  | com.skype.raider | Skype | A aplicação Skype é permitida apenas em determinadas ações que resultam numa chamada telefónica. |
  | com.android.providers.media | Fornecedor de conteúdos multimédia do Android | O fornecedor de conteúdos multimédia só tem permissão para a ação de seleção de toque. |
  | com.google.android.gms; com.google.android.gsf | Pacotes dos Serviços do Google Play | Estes pacotes têm permissão para ações do Google Cloud Messaging, tal como notificações push. |



##  <a name="access-settings"></a>Definições de acesso

| Definição | Como utilizar | Valor(es) predefinido(s) |
|------|------|------|
| **Exigir PIN para acesso** | Selecione **Sim** para exigir um PIN para utilizar esta aplicação. É pedido ao utilizador para configurar este PIN da primeira vez que executar a aplicação num contexto escolar ou profissional. Valor predefinido = **Sim**.<br><br> Configure as seguintes definições para a segurança do PIN: <ul><li>**Número de tentativas antes de redefinição do PIN**: especifique o número de tentativas que o utilizador tem para introduzir o PIN com êxito, após as quais será necessário repô-lo. Valor predefinido = **5**.</li><li> **Permitir PIN simples**: selecione **Sim** se pretende permitir que os utilizadores utilizem sequências de PIN simples, como 1234 ou 1111. Selecione **Não** para os impedir de utilizar sequências simples. Valor predefinido = **Sim**. </li><li> **Comprimento do PIN**: especifique o número mínimo de dígitos numa sequência de PIN. Valor predefinido = **4**. </li><li> **Permitir impressões digitais em vez do PIN (Android 6.0+)**: selecione **Sim** para permitir que o utilizador utilize a [autenticação por impressão digital](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) em vez de um PIN para acesso à aplicação. Valor predefinido = **Sim**.</li></ul> Em dispositivos Android, pode permitir que o utilizador prove a sua identidade através da [autenticação por impressão digital Android](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) em vez de um PIN. Quando o utilizador tentar utilizar esta aplicação com a respetiva conta escolar ou profissional, é-lhe pedido para fornecer a identidade de impressão digital em vez de introduzir um PIN. </li></ul>| Exigir PIN: Sim <br><br> Tentativas de reposição do PIN: 5 <br><br> Permitir PIN simples: Sim <br><br> Comprimento do PIN: 4 <br><br> Permitir impressão digital: Sim |
| **Exigir credenciais da empresa para obter acesso** | Selecione **Sim** para exigir que o utilizador inicie sessão com a respetiva conta escolar ou profissional em vez de introduzir um PIN de acesso à aplicação. Se definir esta opção como **Sim**, substitui os requisitos para PIN ou Touch ID.  | Não |
| **Bloquear a execução de aplicações geridas em dispositivos com jailbreak ou root** |Selecione **Sim** para bloquear a execução desta aplicação em dispositivos com jailbreak ou root. O utilizador continuará a poder utilizar esta aplicação para tarefas pessoais, mas terá de utilizar um dispositivo diferente para aceder aos dados escolares ou profissionais nesta aplicação. | Sim |
| **Verificar novamente os requisitos de acesso após (minutos)** | Configure as seguintes definições: <ul><li>**Tempo Limite**: este é o número de minutos que passam até os requisitos de acesso (definidos anteriormente na política) serem verificados novamente. Por exemplo, um administrador ativa o PIN na política, um utilizador abre uma aplicação de MAM e tem de introduzir um PIN. Quando utiliza esta definição, o utilizador não tem de introduzir um PIN numa aplicação de MAM durante **30 minutos** (valor predefinido).</li><li>**Período de tolerância offline**: este é o número de minutos em que as aplicações de MAM podem ser executadas offline, especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem verificados novamente. Valor predefinido = **720** minutos (12 horas). Após este período expirar, a aplicação pedirá uma autenticação de utilizador para o AAD, para que a mesma possa continuar em execução.</li></ul>| Tempo limite: 30 <br><br> Offline: 720 |
| **Intervalo offline antes de os dados da aplicação serem eliminados (dias)** | Após vários dias (definidos pelo administrador) de execução offline, a aplicação irá fazer uma eliminação seletiva. Esta eliminação seletiva é a mesma eliminação que aquela que pode ser iniciada pelo administrador no fluxo de trabalho de eliminação de MAM. <br><br> | 90 dias |
| **Bloquear captura de ecrã e Android Assistant (Android 6.0+)** | Selecione **Sim** para bloquear a captura de ecrã e as capacidades do **Android Assistant** do dispositivo quando utilizar esta aplicação. Selecionar **Sim** também desfocará a imagem de pré-visualização do comutador da aplicação quando utilizar esta aplicação com uma conta escolar ou profissional. | Não |
| **Desativar o PIN da aplicação quando o PIN do dispositivo for gerido** | Escolha **Sim** para desativar o PIN da aplicação quando for detetado um bloqueio do dispositivo num dispositivo inscrito. | Não |

