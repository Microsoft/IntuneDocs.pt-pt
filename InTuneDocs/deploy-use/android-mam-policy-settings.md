---
title: "Definições de políticas de MAM para Android | Microsoft Intune"
description: "Este tópico descreve as definições da política de gestão de aplicações móveis para dispositivos Android."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d0a1a2b3f4e5dbac8b333db3a5cc4bb32c0d61ef


---

# <a name="android-mobile-app-management-policy-settings-in-microsoft-intune"></a>Definições de políticas de gestão de aplicações móveis para Android no Microsoft Intune
As definições de políticas descritas neste tópico podem ser [configuradas](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para uma política de gestão de aplicações móveis (MAM) no painel **Definições** no portal do Azure.
Existem duas categorias de definições de políticas: reposicionamento de dados e acesso. Neste tópico, o termo *aplicações geridas por políticas* é utilizado para fazer referência a aplicações configuradas com políticas de MAM.

##  <a name="data-relocation-settings"></a>Definições de reposicionamento de dados

- **Impedir cópias de segurança de Android:** selecione **Sim** para desativar ou **Não** para permitir a cópia de segurança de dados da empresa de aplicações geridas por políticas.

  Valor predefinido = **Sim**
- **Permitir que a aplicação transfira dados para outras aplicações**: selecione uma das opções para indicar que tipo de aplicações podem receber dados da empresa de aplicações geridas por políticas:
  -   **Aplicações geridas por políticas**: permite a transferência apenas para aplicações com a política de MAM.
  -   **Todas as aplicações**: permite a transferência para qualquer aplicação.
  -   **Nenhuma**: não permite a transferência de dados para nenhuma aplicação.

 Valor predefinido = **Aplicações geridas por políticas**.
- **Permitir que a aplicação receba dados de outras aplicações**: especifique as aplicações que podem transferir dados para aplicações geridas por políticas:
  -   **Aplicações geridas por políticas**: permite transferências de dados apenas a partir de outras aplicações geridas por políticas.
  -   **Todas as aplicações**: permite a transferência de dados a partir de qualquer aplicação.
  -   **Nenhuma**: não permite a transferência de dados a partir de nenhuma aplicação.

  Valor predefinido = **Todas as aplicações**

-   **Impedir Guardar Como**: selecione **Sim** para desativar a utilização da opção Guardar Como em qualquer aplicação que utilize esta política. Selecione **Não** se quiser permitir a utilização da opção Guardar Como.

  Valor predefinido = **Sim**
- **Restringir cortar, copiar e colar com outras aplicações**: especifique quando as ações cortar, copiar e colar devem ser restringidas. Escolha entre:
  -   **Bloqueado**: não permite as ações cortar, copiar e colar entre aplicações geridas por políticas.
  -   **Aplicações Geridas por Políticas**: permite as ações cortar, copiar e colar apenas entre aplicações geridas por políticas.
  -   **Aplicações Geridas por Políticas com colar em**: permite as ações cortar ou copiar entre aplicações geridas por políticas. Permite que os dados cortados ou copiados de qualquer aplicação sejam colados nesta aplicação.
  -   **Qualquer aplicação**: sem restrições para as ações cortar, copiar e colar entre todas as aplicações.

  Valor predefinido = **Aplicações geridas por políticas com colar em**
-   **Restringir conteúdo Web a apresentar no Managed Browser**: selecione **sim** para especificar quer todas as ligações na aplicação serão abertas na aplicação Managed Browser.

  Para os dispositivos que não estejam inscritos no Intune, as ligações em aplicações geridas por políticas só podem ser abertas na aplicação Managed Browser se utilizar a política de MAM.

  Se utiliza o Intune para gerir os dispositivos, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Valor predefinido = **Sim**
- **Encriptar dados da aplicação**: selecione **Sim** para ativar a encriptação. Quando esta definição está ativada, a Microsoft fornece encriptação para as aplicações que estão associadas a uma política de MAM. Os dados são encriptados de modo síncrono durante as tarefas de E/S de ficheiros. Os conteúdos no armazenamento do dispositivo são sempre encriptados.
  >[!NOTE]
  >O método de encriptação não tem certificação FIPS 140-2.

  Valor predefinido = **Sim**

- **Desativar a sincronização de contactos**: selecione **Sim** para impedir que as informações de contacto sejam sincronizadas com a aplicação de livro de endereços nativa no dispositivo. Se selecionar **Não**, a aplicação guarda as informações de contacto na aplicação de livro de endereços nativa no dispositivo.

  Quando efetuar uma eliminação seletiva para remover os dados da empresa, os contactos sincronizados diretamente entre a aplicação e o livro de endereços nativo são removidos. Não é possível limpar contactos sincronizados entre o livro de endereços nativo e outra origem externa. Atualmente, só é aplicável à aplicação Microsoft Outlook.

  Valor predefinido = **Sim**
- **Desativar a impressão**: selecione **Sim** para impedir a impressão dos dados da empresa a partir de aplicações associadas à política de MAM.

  Valor predefinido = **Sim**

##  <a name="access-settings"></a>Definições de acesso

- **Exigir PIN para o acesso**: selecione **Sim** para exigir um PIN para utilizar aplicações geridas por políticas. É pedido ao utilizador para configurar esta opção da primeira vez que executar a aplicação num contexto profissional.

 Valor predefinido = **Sim**

 -  **Permitir PIN simples**: especifique se quer permitir que os utilizadores utilizem sequências de PIN simples, como 1234 ou 1111. Valor predefinido = **Sim**.
 - **Comprimento do PIN**: especifique o número mínimo de dígitos num PIN. Valor predefinido = **4**.
 - **Número de tentativas antes da reposição do PIN**: especifique o número de tentativas de introdução do PIN que podem ser efetuadas antes de o utilizador ter de repor o PIN. Não existe um valor predefinido para esta definição.
 - **Requer impressão digital em vez de PIN (Android 6.0+):** selecione **Sim** para requerer uma identidade de impressão digital em vez de um PIN numerado para acesso à aplicação.
 Em dispositivos Android, pode permitir ao utilizador identificar-se a si próprio através de impressão digital em vez de um PIN numerado. Quando o utilizador tentar aceder a esta aplicação ao utilizar a respetiva conta profissional, é-lhe pedido para fornecer a identidade de impressão digital em vez de introduzir um PIN.
 - **Exigir credenciais da empresa para obter acesso**: selecione **Sim** para exigir credenciais empresariais em vez de um PIN ou impressão digital de acesso à aplicação. Se definir esta opção como **Sim**, os requisitos para um PIN ou um Touch ID são substituídos. Será pedido ao utilizador para fornecer as respetivas credenciais empresariais. Valor predefinido = **Não**.


- **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**: selecione **Sim** para impedir que as aplicações sejam executadas em dispositivos desbloqueados por jailbreak ou rooting. O utilizador pode continuar a utilizar as aplicações para tarefas pessoais, mas tem de utilizar um dispositivo diferente para o trabalho.

  Valor predefinido = **Sim**
- **Verificar novamente os requisitos de acesso após (minutos)**
  -   **Tempo limite**: especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados.
  -   **Período de tolerância offline**: se o dispositivo estiver offline, especifique o tempo (em minutos) antes de os requisitos de acesso da aplicação serem novamente verificados.

  Valores predefinidos = Tempo limite de **30** minutos e período de tolerância offline de **720** minutos

-   **Intervalo offline antes de os dados da aplicação serem eliminados (dias)**: opte por eliminar os dados da empresa se um dispositivo estiver offline durante um determinado período.  Especificar o número de dias que um dispositivo pode ficar offline antes de os dados empresariais serem removidos do dispositivo.

    >[!TIP]
    >Introduzir o valor **0** desativa esta definição.

  Valor predefinido = **90** dias
- **Bloquear captura de ecrã e Assistente do Android (Android 6 Marshmallow ou posterior)**: selecione **Sim** para bloquear as capacidades de captura de ecrã e de **Assistente do Android** do dispositivo quando utilizar esta aplicação.



<!--HONumber=Dec16_HO2-->


