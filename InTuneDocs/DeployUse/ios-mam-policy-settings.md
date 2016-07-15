---
# required metadata

title: Definições de políticas de MAM para iOS | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: andcerat
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

#  Definições de políticas de gestão de aplicações móveis para iOS
As definições de políticas descritas abaixo podem ser [configuradas](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para uma política de MAM no painel **Definições** no portal do Azure.

Existem duas categorias de definições de políticas: Reposicionamento de dados e Acesso:

##  Definições de reposicionamento de dados
O termo **Aplicações geridas por políticas** é utilizado para fazer referência a aplicações que estão configuradas com políticas de MAM.

- **Impedir cópias de segurança do iTunes e iCloud:** escolha **Sim** para desativar ou **Não** para permitir a cópia de segurança de dados da empresa de aplicações geridas por políticas.

  **Valor predefinido = Sim**

- **Permitir que a aplicação transfira dados para outras aplicações:**   Escolha uma das opções para indicar as aplicações que podem receber dados de aplicações geridas por políticas:
  - **Aplicações geridas por políticas**: permitir a transferência apenas para aplicações com a política de MAM.
  - **Todas as aplicações**: permitir a transferência para qualquer aplicação
  - **Nenhuma**: não permite a transferência de dados para nenhuma aplicação, incluindo outras aplicações geridas por políticas.

  Além disso, se definir esta opção como **Aplicações Geridas por Políticas** ou **Nenhuma**, a funcionalidade do iOS 9 que permite que o Spotlight Search procure dados dentro de aplicações será bloqueada.

  **Valor predefinido = Aplicações geridas por políticas**

- **Permitir que a aplicação receba dados de outras aplicações:**  Especificar aplicações que têm permissão para transferir dados para aplicações geridas por políticas:
  -  **Aplicações geridas por políticas**: permitir transferências de dados apenas a partir de outras aplicações geridas por políticas.
  -  **Todas as aplicações**: permitir a transferência de dados a partir de qualquer aplicação
  -  **Nenhuma**: não permitir a transferência de dados a partir de nenhuma aplicação.

  **Valor predefinido = Todas as aplicações**

- **Impedir operações "Guardar Como":** escolha **Sim** para desativar a utilização da opção Guardar Como em qualquer aplicação que utiliza esta política. Escolha **Não** se pretender permitir a utilização da opção Guardar Como.

  **Valor predefinido = Sim**

- **Restringir cortar, copiar e colar com outras aplicações:** especificar quando as operações cortar, copiar e colar devem ser restringidas. Escolha entre:
  -   **Bloqueado**: não permitir operações cortar, copiar e colar entre aplicações geridas por políticas.
  -   **Aplicações Geridas por Políticas**: permitir apenas operações cortar, copiar e colar entre aplicações geridas por políticas.
  -   **Aplicações Geridas por Políticas com Colar Em**: permitir operações cortar ou copiar entre aplicações geridas por políticas. Permitir que os dados cortados ou copiados de qualquer aplicação sejam colados nesta aplicação.
  - **Qualquer Aplicação**: sem restrições para operações cortar, copiar e colar entre quaisquer aplicações.

  **Valor predefinido = Aplicações geridas por políticas com colar em**

- **Restringir conteúdo Web a apresentar no Managed Browser:** quando esta definição está ativada, todas as ligações na aplicação serão abertas no Managed Browser.

  Para os dispositivos que não estejam inscritos no Intune, as ligações Web em aplicações geridas por políticas apenas podem ser abertas na aplicação Managed Browser através da política de gestão de aplicações móveis.

  Se utilizar o Intune para gerir os dispositivos, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Valor predefinido = Sim**

- **Encriptar dados da aplicação:** para aplicações associadas à política de gestão de aplicações móveis do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], os dados são encriptados em descanso ao utilizar a encriptação no nível do dispositivo fornecida pelo sistema operativo. Quando for necessário um PIN, os dados são encriptados de acordo com as definições na política de gestão de aplicações móveis. Conforme indicado na documentação da Apple, [os módulos utilizados pelo iOS 7 têm a certificação FIPS 140-2](http://support.apple.com/en-us/HT202739).

  Nas definições de política, pode especificar os valores de encriptação do PIN.  Estes valores determinam quando os dados são encriptados. As opções são:
  - **Quando o dispositivo está bloqueado:** todos os dados de aplicação associados a esta política são encriptados quando o dispositivo está bloqueado.
  -   **Quando o dispositivo está bloqueado (exceto para abrir ficheiros):** todos os dados de aplicação associados a esta política são encriptados quando o dispositivo está bloqueado, exceto para os dados dos ficheiros atualmente abertos na aplicação.
  -   **Após o reinício do dispositivo:** todos os dados de aplicação associados a esta política são encriptados quando o dispositivo é reiniciado, até que o dispositivo seja desbloqueado pela primeira vez.
  -   **Utilizar as definições do dispositivo:** os dados de aplicação são encriptados com base nas predefinições no dispositivo.
  Quando ativa esta definição, o utilizador final tem de configurar e utilizar um PIN para aceder ao respetivo dispositivo.  Se não existir PIN, as aplicações não serão iniciadas e será pedido ao utilizador final para definir um PIN com uma mensagem "A sua empresa requer que ative primeiro um PIN do dispositivo para aceder a esta aplicação".

  **Valor predefinido = A opção de encriptação não está selecionada.**
- **ContactSyncDisabled:**  Escolha **Sim** para impedir que as informações de contacto sejam sincronizadas com a aplicação do livro de endereços nativo no dispositivo. Se escolher **Não**, a aplicação guardará as informações de contacto na aplicação do livro de endereços nativo no dispositivo.

  Quando efetuar uma eliminação seletiva para remover os dados da empresa, os contactos sincronizados diretamente a partir da aplicação com o livro de endereços nativo são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, apenas é aplicável à aplicação **Microsoft Outlook**.

  **Valor predefinido = Sim**
##  Definições de política de acesso para iOS
O termo **Aplicações geridas por políticas** é utilizado para fazer referência a aplicações que estão configuradas com políticas de MAM.
- **Exigir PIN para o acesso:** escolha **Sim** para exigir um PIN para utilizar aplicações geridas por políticas. É pedido ao utilizador para configurar esta opção da primeira vez que executar a aplicação num contexto profissional.

  **Valor predefinido = Sim**
    -  **Permitir PIN simples:** especifique se pretende permitir que os utilizadores utilizem sequências de PIN simples, como 1234 ou 1111. **Valor predefinido = Sim**.
    - **Comprimento do PIN**: especifique o número mínimo de dígitos num PIN. **Valor predefinido = 4**
    - **Número de tentativas antes da reposição do PIN:** especifique o número de tentativas de introdução do PIN que podem ser efetuadas antes de o utilizador ter de repor o PIN.
  **Não existe valor predefinido para esta definição**.

  - **Requer impressão digital em vez de PIN (iOS 8.0+):** escolha **Sim** para requerer uma identidade de impressão digital em vez de um PIN numerado para acesso à aplicação.
Em dispositivos iOS, pode permitir ao utilizador identificar-se a si próprio através de impressão digital em dispositivos iOS em vez de um PIN numerado. Quando o utilizador final tentar aceder a esta aplicação utilizando a respetiva conta profissional, é-lhe pedido para fornecer a identidade de impressão digital em vez de introduzir um número PIN.

    **Valor predefinido = Sim**
- **Exigir credenciais da empresa para obter acesso:** escolha **Sim** para requerer credenciais empresariais em vez de um PIN de acesso à aplicação. **Se definir esta opção para Sim, isto substitui os requisitos para PIN ou Touch ID.** Será pedido ao utilizador para fornecer as respetivas credenciais empresariais.

  **Valor predefinido = Não**
- **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting:** escolha **Sim** para impedir que as aplicações sejam executadas em dispositivos desbloqueados por jailbreak ou rooting. O utilizador continuará a poder utilizar as aplicações para tarefas pessoais, mas terá de utilizar um dispositivo diferente para o trabalho.

  **Valor predefinido = Sim**
- **Verificar novamente os requisitos de acesso após (minutos)**|-   **Tempo limite:** tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados.
  -   **Período de tolerância offline:** se o dispositivo estiver offline, especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados.

  **Valor predefinido = Tempo limite de 30 minutos e período de tolerância offline de 720 minutos**
  - **Intervalo offline antes de os dados da aplicação serem eliminados (dias):** pode optar por eliminar os dados da empresa se um dispositivo estiver offline durante um determinado período.  Especificar o número de dias que um dispositivo pode ficar offline antes de os dados empresariais serem removidos do dispositivo. **A introdução de um valor de 0 desativará esta definição**.

  **Valor predefinido = 90 dias**


<!--HONumber=Jun16_HO2-->


