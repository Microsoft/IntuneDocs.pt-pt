---
# required metadata

title: Definições de políticas de MAM para Android | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Definições de políticas de gestão de aplicações móveis para Android no Microsoft Intune
As definições de políticas descritas abaixo podem ser [configuradas](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para uma política de MAM no painel **Definições** no portal do Azure.
Existem duas categorias de definições de políticas: Reposicionamento de dados e Acesso:

##  Definições de reposicionamento de dados
O termo **Aplicações geridas por políticas** é utilizado para fazer referência a aplicações que estão configuradas com políticas de MAM.
- **Impedir cópias de segurança de Android:** escolha **Sim** para desativar ou **Não** para permitir a cópia de segurança de dados da empresa de aplicações geridas por políticas.

  **Valor predefinido = Sim**
- **Permitir que a aplicação transfira dados para outras aplicações:** selecione uma das opções para indicar as aplicações que podem receber dados da empresa de aplicações geridas por políticas:
  -   **Aplicações geridas por políticas**: permitir a transferência apenas para aplicações com a política de MAM
  -   **Todas as aplicações**: permitir a transferência para qualquer aplicação
  -   **Nenhuma**: não permitir a transferência de dados para nenhuma aplicação

  **Valor predefinido = Aplicações geridas por políticas**
- **Permitir que a aplicação receba dados de outras aplicações:** especificar aplicações que têm permissão para transferir dados para as aplicações geridas por políticas:
  -   **Aplicações geridas por políticas**: permitir transferências de dados apenas a partir de outras aplicações geridas por políticas
  -   **Todas as aplicações**: permitir a transferência de dados a partir de qualquer aplicação
  -   **Nenhuma**: não permitir a transferência de dados a partir de qualquer aplicação

      **Valor predefinido = Todas as aplicações**

-   **Impedir operações "Guardar Como":** escolha **Sim** para desativar a utilização da opção Guardar Como em qualquer aplicação que utiliza esta política. Escolha **Não** se pretender permitir a utilização da opção Guardar Como.

  **Valor predefinido = Sim**
- **Restringir cortar, copiar e colar com outras aplicações:** especificar quando as operações cortar, copiar e colar devem ser restringidas. Escolha entre:
  -   **Bloqueado**: não permitir operações cortar, copiar e colar entre aplicações geridas por políticas.
  -   **Aplicações Geridas por Políticas**: permitir apenas operações cortar, copiar e colar entre aplicações geridas por políticas.
  -   **Aplicações Geridas por Políticas com Colar Em**: permitir operações cortar ou copiar entre aplicações geridas por políticas. Permitir que os dados cortados ou copiados de qualquer aplicação sejam colados nesta aplicação.
  -   **Qualquer Aplicação**: sem restrições para operações cortar, copiar e colar entre quaisquer aplicações.

    **Valor predefinido = Aplicações geridas por políticas com colar em**
-   **Restringir conteúdo Web a apresentar no Managed Browser:** quando esta definição está ativada, todas as ligações na aplicação serão abertas no Managed Browser.

  Para os dispositivos que não estejam inscritos no Intune, as ligações Web em aplicações geridas por políticas apenas serão abertas na aplicação Managed Browser através da política de gestão de aplicações móveis.

  Se utilizar o Intune para gerir os dispositivos, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Valor predefinido = Sim**
- **Encriptar dados da aplicação:** escolha **Sim** para ativar a encriptação. Quando esta definição está ativada, para as aplicações que estão associadas a uma política de gestão de aplicações móveis, a encriptação é fornecida pela Microsoft. Os dados são encriptados de modo síncrono durante as operações de E/S de ficheiros. O conteúdo no armazenamento do dispositivo é sempre encriptado.
  >[!NOTE] O método de encriptação não tem certificação FIPS 140-2

  **Valor predefinido = Sim**

- **ContactSyncDisabled:** escolha **Sim** para impedir que as informações de contacto sejam sincronizadas com a aplicação do livro de endereços nativo no dispositivo. Se escolher **Não**, a aplicação guardará as informações de contacto na aplicação do livro de endereços nativo no dispositivo.<br/>Quando efetuar uma eliminação seletiva para remover os dados da empresa, os contactos sincronizados diretamente a partir da aplicação com o livro de endereços nativo são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, apenas é aplicável à aplicação **Microsoft Outlook**.

  **Valor predefinido = Sim**

##  Definições de política de acesso para Android
O termo **Aplicações geridas por políticas** é utilizado para fazer referência a aplicações que estão configuradas com políticas de MAM

- **Exigir PIN para o acesso:** escolha **Sim** para exigir um PIN para utilizar aplicações geridas por políticas. É pedido ao utilizador para configurar esta opção da primeira vez que executar a aplicação num contexto profissional.

 **Valor predefinido = Sim**

 -  **Permitir PIN simples:** especifique se pretende permitir que os utilizadores utilizem sequências de PIN simples, como 1234 ou 1111. **Valor predefinido = Sim**.
 - **Comprimento do PIN**: especifique o número mínimo de dígitos num PIN. **Valor predefinido = 4**
 - **Número de tentativas antes da reposição do PIN:** especifique o número de tentativas de introdução do PIN que podem ser efetuadas antes de o utilizador ter de repor o PIN. **Não existe um valor predefinido para esta definição.**
- **Exigir credenciais de empresa para o acesso:** escolha **Sim** para exigir credenciais de empresa em vez de um PIN para acesso a aplicações.  Se definir esta opção como **Sim**, substitui os requisitos para PIN ou Touch ID.  Será pedido ao utilizador para fornecer as respetivas credenciais empresariais.

  **Valor predefinido = Não**
- **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting:** escolha **Sim** para impedir que as aplicações sejam executadas em dispositivos desbloqueados por jailbreak ou rooting. O utilizador continuará a poder utilizar as aplicações para tarefas pessoais, mas terá de utilizar um dispositivo diferente para o trabalho.

  **Valor predefinido = Sim**
- **Reverificar os requisitos de acesso após (minutos)**-   **Tempo limite:** tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados.
  -   **Período de tolerância offline:** se o dispositivo estiver offline, especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados.

    **Valores predefinidos = Tempo limite de 30 minutos e período de tolerância offline de 720 minutos**

-   **Intervalo offline (dias) antes do apagamento dos dados da aplicação:** pode optar por eliminar os dados da empresa se um dispositivo estiver offline durante um determinado período.  Especificar o número de dias que um dispositivo pode ficar offline antes de os dados empresariais serem removidos do dispositivo. **Dica:** A introdução de um valor de 0 desativará esta definição.

  **Valor predefinido = 90 dias**
- **Bloquear captura de ecrã e Assistente do Android (Android 6 Marshmallow ou posterior):** escolha **Sim** para bloquear as capacidades de captura de ecrã e de **Assistente do Android** do dispositivo quando utilizar esta aplicação.


<!--HONumber=May16_HO3-->


