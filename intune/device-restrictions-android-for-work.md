---
title: "Definições de restrição de dispositivos no Intune para Android for Work"
titlesuffix: Azure portal
description: "Saiba quais são as definições do Intune que pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Android for Work.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c7c69bb3984ae4ffa81aa81ae24cfe17663bc191
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Android for Work no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Definições de perfil de trabalho
-   **Copiar e colar entre perfis pessoais e perfis de trabalho** – controla as ações de copiar e colar entre aplicações pessoais e aplicações de trabalho. Selecione **Bloquear** para ativar o bloqueio. Selecione **Não configurado** para desativar o bloqueio.
- **Partilha de dados entre perfis de trabalho e perfis pessoais** – utilize esta definição para controlar se as aplicações no perfil de trabalho podem partilhar dados com as aplicações no perfil pessoal. Esta definição controla ações de partilha nas aplicações (por exemplo, a opção **Partilha...** na aplicação do browser Chrome) e não se aplica ao comportamento copiar/colar na área de transferência. Ao contrário das [definições de política de proteção de aplicações](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), as definições de restrição de dispositivos são geridas no portal do Intune e utilizam a partição do perfil Android for Work para isolar as aplicações geridas. Escolha entre:
    - **Restrições de partilha predefinidas** – esta definição é o comportamento de partilha predefinido do dispositivo, que varia consoante a versão do Android que está em execução. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. A Google não proporciona uma forma de bloquear a partilha do perfil pessoal para o perfil de trabalho em dispositivos com versões 6.0 e posteriores.   
    - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal** – utilize esta opção para ativar a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
    - **Permitir partilha entre limites** – ativa a partilha entre limites do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Utilize esta definição com cuidado, uma vez que permite que aplicações geridas no perfil de trabalho sejam partilhadas com aplicações no lado não gerido do dispositivo.

-   **Notificações do perfil de trabalho quando o dispositivo está bloqueado** – controla se as aplicações no perfil de trabalho podem apresentar dados em notificações quando o dispositivo está bloqueado.
-   **Permissões de aplicações predefinidas** – define a política de permissões predefinida para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Esta política permite-lhe decidir se todas as permissões devem ser concedidas automaticamente sem um pedido de confirmação, se devem negadas automaticamente sem um pedido de confirmação ou se deve ser permitido ao utilizador final que decida. Escolha entre:
    -   **Predefinição do dispositivo**
    -   **Pedido de confirmação**
    -   **Conceder automaticamente**
    -   **Negar automaticamente**

    O estado de concessão de permissões pode ser definido posteriormente para aplicações específicas, ao definir uma política de Configuração de Aplicações para uma aplicação individual (em **Aplicações móveis** > **Políticas de configuração de aplicações**).

### <a name="work-profile-password"></a>Palavra-passe do perfil de trabalho
- **Exigir Palavra-passe do Perfil de Trabalho** – (Android 7.0 e superior com o perfil de trabalho ativado) Defina uma política de código de acesso que se aplique apenas às aplicações no perfil de trabalho. Por predefinição, o utilizador final tem a opção de utilizar os dois PINs definidos separadamente ou pode optar por os combinar segundo o mais forte.
- **Comprimento mínimo da palavra-passe:** introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter (**4**-**16**)
- **Máximo de minutos de inatividade até o perfil de trabalho ser bloqueado** – selecione a quantidade de tempo antes de o perfil de trabalho ser bloqueado. Em seguida, o utilizador tem de introduzir as credenciais para recuperar o acesso.
- **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de o perfil de trabalho do dispositivo ser eliminado.
- **Expiração da palavra-passe (dias)** – introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**).
- **Tipo de palavra-passe obrigatório** –selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
    - **Predefinição do dispositivo**
    - **Biométrica de segurança baixa**
    - **Necessário**
    - **Pelo menos numérica**
    - **Numérica complexa** – (números repetidos ou consecutivos, tais como “1111” ou “1234”, não são permitidos)
    - **Pelo menos alfabética**
    - **Pelo menos alfanumérica**
    - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores** –introduza o número de novas palavras-passe que têm de ter sido utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio por impressão digital** –impede um utilizador final de utilizar a deteção de impressão digital do dispositivo para o desbloquear.
- **Smart Lock e outros agentes de fidedignidade** – permite-lhe controlar a funcionalidade Smart Lock em dispositivos compatíveis. Esta funcionalidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe do perfil de trabalho se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.

## <a name="device-password"></a>Palavra-passe do dispositivo

- **Comprimento mínimo da palavra-passe:** introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter (**4**-**14**)
- **Máximo de minutos de inatividade até o ecrã ser bloqueado** –selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado.
- **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de todos os dados do dispositivo serem eliminados.
- **Expiração da palavra-passe (dias)** – introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**).
- **Tipo de palavra-passe obrigatório** –selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
    - **Predefinição do dispositivo**
    - **Biométrica de segurança baixa**
    - **Necessário**
    - **Pelo menos numérica**
    - **Numérica complexa** – (números repetidos ou consecutivos, tais como “1111” ou “1234”, não são permitidos)
    - **Pelo menos alfabética**
    - **Pelo menos alfanumérica**
    - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores** –introduza o número de novas palavras-passe que têm de ter sido utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio por impressão digital** –impede um utilizador final de utilizar a deteção de impressão digital do dispositivo para o desbloquear.
- **Smart Lock e outros agentes de fidedignidade** – permite-lhe controlar a funcionalidade Smart Lock em dispositivos compatíveis. Esta funcionalidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.

## <a name="system-security"></a>Segurança do sistema

 - **Análise de ameaças nas aplicações** – exija que a definição **Verificar Aplicações** esteja ativada para os perfis pessoais e de trabalho.

   > [!Note]  
   > Esta definição funcionará apenas em dispositivos que tenham o Android O e superior. 

## <a name="next-steps"></a>Próximos passos

Utilize as informações no tópico [Como configurar definições de restrições de dispositivos](device-restrictions-configure.md) para guardar e atribuir o perfil a utilizadores e dispositivos.
