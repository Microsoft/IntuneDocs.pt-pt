---
title: "Definições de políticas de proteção de aplicações iOS | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: este tópico descreve as definições de políticas de proteção de aplicações para dispositivos iOS."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 291c380b861d3ad7df2fc1af4274d9e8bb014846
ms.openlocfilehash: 55faaa918e309616c9b84eeb429f42d52796c1d9


---

#  <a name="ios-app-protection-policy-settings"></a>Definições de políticas de proteção de aplicações iOS 
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

As definições de políticas descritas neste tópico podem ser [configuradas](app-protection-policies.md) para uma política de proteção de aplicações no painel **Definições** no portal do Azure.

Existem duas categorias de definições de políticas: reposicionamento de dados e acesso. Neste tópico, o termo ***aplicações geridas por políticas*** menciona as aplicações configuradas com políticas de proteção de aplicações.

##  <a name="data-relocation-settings"></a>Definições de reposicionamento de dados

| Definição | Como utilizar | Valor(es) predefinido(s) |
|------|------|------|
| **Impedir cópias de segurança do iTunes e do iCloud** | Selecione **Sim** para impedir que esta aplicação crie uma cópia de segurança dos dados escolares ou profissionais para o iTunes e o iCloud. Selecione **Não** para permitir que esta aplicação crie uma cópia de segurança dos dados escolares ou profissionais para o iTunes e o iCloud.| Sim |
| **Permitir que a aplicação transfira dados para outras aplicações** | Especifique que aplicações podem receber dados desta aplicação: <ul><li> **Aplicações geridas por políticas**: permitir transferências apenas para outras aplicações geridas por políticas.</li> <li>**Todas as aplicações**: permitir a transferência para qualquer aplicação. </li> <li>**Nenhuma**: não permite a transferência de dados para nenhuma aplicação, incluindo outras aplicações geridas por políticas.</li></ul> Além disso, se definir esta opção como **Aplicações geridas por políticas** ou **Nenhuma**, a funcionalidade do iOS 9 que permite que a Pesquisa Spotlight procure dados dentro de aplicações será bloqueada. <br><br> | Todas as aplicações |
| **Permitir que a aplicação receba dados de outras aplicações** | Especifique que aplicações podem transferir dados para esta aplicação: <ul><li>**Aplicações geridas por políticas**: permitir transferências apenas a partir de outras aplicações geridas por políticas.</li><li>**Todas as aplicações**: permitir a transferência de dados a partir de qualquer aplicação.</li><li>**Nenhuma**: não permite transferências de dados a partir de nenhuma aplicação, incluindo outras aplicações geridas por políticas. | Todas as aplicações |
| **Impedir "Guardar Como"** | Selecione **Sim** para desativar a utilização da opção Guardar Como nesta aplicação. Selecione **Não** se quiser permitir a utilização da opção Guardar Como. | Não |
| **Restringir as operações de corte, cópia e colagem com outras aplicações** | Especifique quando as ações de corte, cópia e colagem podem ser utilizadas com esta aplicação. Escolha entre: <ul><li>**Bloqueado**: não permitir ações de corte, cópia e colagem entre esta aplicação e outras aplicações.</li><li>**Aplicações geridas por políticas**: permitir ações de corte, cópia e colagem entre esta aplicação e outras aplicações geridas por políticas.</li><li>**Aplicações geridas por políticas com colar em**: permitir ações de corte ou cópia entre esta aplicação e outras aplicações geridas por políticas. Permitir que os dados de qualquer aplicação sejam colados nesta aplicação.</li><li>**Qualquer aplicação**: sem restrições para ações de corte, cópia e colagem de e para esta aplicação. | Qualquer aplicação |
|**Restringir o conteúdo Web a apresentar no Managed Browser** | Selecione **Sim** para impor que as ligações Web na aplicação sejam abertas na aplicação Managed Browser. <br><br> Para os dispositivos não inscritos no Intune, as ligações Web em aplicações geridas por políticas só podem ser abertas na aplicação Managed Browser. <br><br> Se utiliza o Intune para gerir os dispositivos, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-internet-access-using-managed-browser-policies). | Não |
| **Encriptar dados da aplicação** | Para aplicações geridas por políticas, os dados inativos são encriptados através do esquema de encriptação ao nível do dispositivo fornecido pelo iOS. Quando for necessário um PIN, os dados são encriptados de acordo com as definições na política de proteção de aplicações. <br><br> Aceda à documentação oficial da Apple [aqui](https://support.apple.com/HT202739) para ver quais os módulos de encriptação iOS que têm a certificação FIPS 140-2 ou a certificação FIPS 140-2 pendente. <br><br> Especifique quando os dados escolares ou profissionais são encriptados nesta aplicação. Escolha entre: <ul><li>**Quando o dispositivo está bloqueado**: todos os dados de aplicação associados a esta política são encriptados quando o dispositivo está bloqueado.</li><li>**Quando o dispositivo está bloqueado e existem ficheiros abertos**: todos os dados de aplicação associados a esta política são encriptados quando o dispositivo está bloqueado, exceto para os dados dos ficheiros atualmente abertos na aplicação.</li><li>**Após o reinício do dispositivo:** todos os dados de aplicação associados a esta política são encriptados quando o dispositivo é reiniciado, até que o dispositivo seja desbloqueado pela primeira vez.</li><li>**Utilizar as definições do dispositivo:** os dados de aplicação são encriptados com base nas predefinições no dispositivo. <br><br> Quando ativa esta definição, o utilizador tem de configurar e utilizar um PIN para aceder ao respetivo dispositivo.  Se não existir um PIN, as aplicações não serão abertas e será pedido ao utilizador para definir um PIN com a mensagem "A sua organização requer que ative primeiro um PIN do dispositivo para aceder a esta aplicação". </li></ul> | Quando o dispositivo está bloqueado |
| **Desativar a sincronização de contactos** | Selecione **Sim** para impedir que a aplicação guarde os dados na aplicação nativa Contactos no dispositivo. Se selecionar **Não**, a aplicação pode guardar os dados na aplicação nativa Contactos no dispositivo. <br><br>Ao efetuar uma eliminação seletiva para remover dados escolares ou profissionais da aplicação, os contactos sincronizados diretamente a partir da aplicação para a aplicação nativa Contactos são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, só é aplicável à aplicação Microsoft Outlook. | Não |
| **Desativar a impressão** | Selecione **Sim** para impedir que a aplicação imprima dados escolares ou profissionais. | Não |


> [!NOTE]
> Nenhuma das definições de reposicionamento de dados controla a funcionalidade de gestão Open-in da Apple em dispositivos iOS. Para gerir a funcionalidade Open-in da Apple, veja [Gerir a transferência de dados entre aplicações iOS com o Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).


## <a name="access-settings"></a>Definições de acesso

| Definição | Como utilizar | Valor(es) predefinido(s) |
|------|------|------|
| **Exigir PIN para acesso** | Selecione **Sim** para exigir um PIN para utilizar esta aplicação. É pedido ao utilizador para configurar este PIN da primeira vez que executar a aplicação num contexto escolar ou profissional. Valor predefinido = **Sim**.<br><br> Configure as seguintes definições para a segurança do PIN: <ul><li>**Número de tentativas antes de redefinição do PIN**: especifique o número de tentativas que o utilizador tem para introduzir o PIN com êxito, após as quais será necessário repô-lo. Valor predefinido = **5**.</li><li> **Permitir PIN simples**: selecione **Sim** se pretende permitir que os utilizadores utilizem sequências de PIN simples, como 1234 ou 1111. Selecione **Não** para os impedir de utilizar sequências simples. Valor predefinido = **Sim**. </li><li> **Comprimento do PIN**: especifique o número mínimo de dígitos numa sequência de PIN. Valor predefinido = **4**. </li><li> **Permitir impressões digitais em vez do PIN (iOS 8.0+)**: selecione **Sim** para permitir que o utilizador utilize o [Touch ID](https://support.apple.com/en-us/HT201371) em vez de um PIN para aceder à aplicação. Valor predefinido = **Sim**.<br><br> Em dispositivos iOS, pode permitir que o utilizador prove a sua identidade através da utilização do [Touch ID](https://support.apple.com/en-us/HT201371) em vez de um PIN. Quando o utilizador tentar utilizar esta aplicação com a respetiva conta escolar ou profissional, é-lhe pedido para fornecer a identidade de impressão digital em vez de introduzir um PIN. </li></ul>| Exigir PIN: Sim <br><br> Tentativas de reposição do PIN: 5 <br><br> Permitir PIN simples: Sim <br><br> Comprimento do PIN: 4 <br><br> Permitir impressão digital: Sim |
| **Exigir credenciais da empresa para obter acesso** | Selecione **Sim** para exigir que o utilizador inicie sessão com a respetiva conta escolar ou profissional em vez de introduzir um PIN de acesso à aplicação. Se definir esta opção como **Sim**, substitui os requisitos para PIN ou Touch ID.  | Não |
| **Bloquear a execução de aplicações geridas em dispositivos com jailbreak ou root** |  Selecione **Sim** para bloquear a execução desta aplicação em dispositivos com jailbreak ou root. O utilizador continuará a poder utilizar esta aplicação para tarefas pessoais, mas terá de utilizar um dispositivo diferente para aceder aos dados escolares ou profissionais nesta aplicação. | Sim |
| **Verificar novamente os requisitos de acesso após (minutos)** | Configure as seguintes definições: <ul><li>**Tempo limite**: especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados. Valor predefinido = **30** minutos.</li><li>**Período de tolerância offline**: se o dispositivo estiver offline, especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados. Valor predefinido = **720** minutos (12 horas).</li></ul>| Tempo limite: 30 <br><br> Offline: 720 |
| **Intervalo offline antes de os dados da aplicação serem eliminados (dias)** | Os dados escolares ou profissionais nesta aplicação poderão ser eliminados se um dispositivo tiver estado offline durante um período de tempo superior a um determinado valor. Especifique o número de dias que um dispositivo pode ficar offline antes de os dados escolares ou profissionais serem removidos do dispositivo. <br><br> | 90 dias |

##  <a name="add-ins-for-outlook-app"></a>Suplementos para a aplicação Outlook

O Outlook incluiu recentemente suplementos no Outlook para iOS, que lhe permitem integrar aplicações populares no cliente de e-mail. Os suplementos para o Outlook estão disponíveis na Web, no Windows, no Mac e no Outlook para iOS. Uma vez que os suplementos são geridos através do Microsoft Exchange, os utilizadores serão capazes de partilhar dados e mensagens no Outlook e em aplicações de suplementos não geridas, exceto se os suplementos forem desativados para o utilizador pelo Exchange deles.

Se quiser impedir que os seus utilizadores finais acedam e instalem suplementos do Outlook (afeta todos os clientes do Outlook), confirme que tem as seguintes alterações das funções no Centro de administração do Exchange:

- Para impedir que os utilizadores instalem suplementos da Loja Office, remova a função O Meu Mercado desses utilizadores.
- Para impedir que os utilizadores realizem sideloading de suplementos, remova a função As Minhas Aplicações Personalizadas desses utilizadores.
- Para impedir que os utilizadores instalem todos os suplementos, remova as funções As Minhas Aplicações Personalizadas e O Meu Mercado.

Estas instruções aplicam-se ao Office 365, Exchange 2016, Exchange 2013 no Outlook na Web, Windows, Mac e em dispositivos móveis.

- Saiba mais sobre os [suplementos para o Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Saiba mais sobre os [como especificar os administradores e utilizadores que podem instalar e gerir suplementos para a aplicação Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).



<!--HONumber=Feb17_HO2-->


