---
title: Definições de conformidade do Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os dispositivos Android Enterprise no Microsoft Intune. Defina regras de palavra-passe, escolha uma versão mínima ou máxima do sistema operativo, restrinja aplicações específicas, impeça a reutilização de palavras-passe e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7d38d5c71b06587b593eef46eca46f3d32f1349
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729828"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android Enterprise para marcar dispositivos como conformes ou não conformes com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Android Enterprise no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes, defina um nível de ameaça permitido, ative o Google Play Protect e muito mais.

Esta funcionalidade aplica-se a:

- Android Enterprise

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

> [!IMPORTANT]
> As políticas de conformidade também se aplicam aos dispositivos Android Enterprise dedicados. Se uma política de conformidade for atribuída a um dispositivo dedicado, o dispositivo poderá ser apresentado como **Não conforme**. O acesso condicional e a imposição de conformidade não estão disponíveis em dispositivos dedicados. Realize algumas tarefas ou ações para que os dispositivos dedicados fiquem em conformidade com as políticas atribuídas.

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Android Enterprise**.

## <a name="device-owner"></a>Proprietário do dispositivo

### <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exigir que o dispositivo esteja ao nível ou abaixo do Nível de Ameaça de Dispositivos**: Selecione o nível máximo de ameaça de dispositivo permitido avaliado pelo seu [serviço de defesa contra ameaças móveis](mobile-threat-defense.md). Os dispositivos que excedem esse nível de ameaça são marcados como não compatíveis. Para utilizar esta definição, selecione o nível de ameaça permitido:

  - **Não configurado** (predefinição): Essa configuração não é avaliada quanto à conformidade ou não à conformidade.
  - **Protegido**: esta opção é a mais segura e significa que o dispositivo não pode ter ameaças. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo será avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo será avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alto**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
> [!NOTE] 
> Os seguintes provedores de defesa contra ameaças móveis (MTD) dão suporte a implantações de proprietário de dispositivo Android Enterprise usando a configuração de aplicativo:
> - Melhor mobilidade 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Verifique com seu provedor MTD a configuração exata necessária para dar suporte a plataformas do proprietário do dispositivo Android Enterprise no Intune. Essa lista é atualizada, pois o MTD parters dá suporte a cenários de proprietário do dispositivo Android Enterprise. 

#### <a name="google-play-protect"></a>Google Play Protect

- **Atestado do dispositivo SafetyNet**: introduza o nível do [Atestado SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** (predefinição): a definição não é avaliada quanto à conformidade ou não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

### <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do SO**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode atualizar a versão do dispositivo e, em seguida, aceder aos recursos da organização.
- **Versão máxima do SO**: quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Enquanto a regra não for alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da organização.

### <a name="system-security"></a>Segurança do sistema

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exija** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Esta definição é aplicada ao nível do dispositivo. Se precisar apenas de exigir uma palavra-passe ao nível do perfil de trabalho, utilize uma política de configuração. Veja [Definições de configuração de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

  - **Tipo obrigatório de palavra-passe**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
    - **Padrão do dispositivo**: Para avaliar a conformidade de senha, certifique-se de selecionar uma senha que não seja o **padrão do dispositivo**.  
    - **Palavra-passe obrigatória, sem restrições**
    - **Biometria fraca**: veja [Strong vs. weak biometrics](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (Biometria forte versus fraca) (abre o site do Android)
    - **Numérico** (padrão): a palavra-passe só pode ter números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Complexo numérico**: não são permitidos números repetidos ou consecutivos, como “1111” ou “1234”. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfabética**: são obrigatórias letras do alfabeto. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfanumérica**: inclui letras maiúsculas, letras minúsculas e carateres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfanumérica com símbolos**: inclui letras maiúsculas, letras minúsculas, carateres numéricos, sinais de pontuação e símbolos. Introduza também:

      - **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo da palavra-passe, entre 4 e 16 carateres.
      - **Número de carateres obrigatórios**: introduza o número de carateres que a palavra-passe deverá ter, entre 0 e 16 carateres.
      - **Número de carateres em minúsculas obrigatórios**: introduza o número de carateres em minúsculas que a palavra-passe deverá ter, entre 0 e 16 carateres.
      - **Número de carateres em maiúsculas obrigatórios**: introduza o número de carateres em maiúsculas que a palavra-passe deverá ter, entre 0 e 16 carateres.
      - **Número de carateres não alfabéticos obrigatórios**: introduza o número de carateres não alfabéticos (tudo o que não seja letras do alfabeto) que a palavra-passe deverá ter, entre 0 e 16 carateres.
      - **Número de carateres numéricos obrigatórios**: introduza o número de carateres numéricos (`1`, `2`, `3` e assim por diante) que a palavra-passe deverá ter, entre 0 e 16 carateres.
      - **Número de carateres de símbolos obrigatórios**: introduza o número de carateres de símbolos (`&`, `#`, `%` e assim por diante) que a palavra-passe deverá ter, entre 0 e 16 carateres.

- **Minutos de inatividade antes de a palavra-passe ser exigida**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Número de dias até expirar a palavra-passe**: introduza o número de dias, entre 1 e 365, antes de ser necessário alterar a palavra-passe do dispositivo. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.
- **Número de palavras-passe necessárias antes de o utilizador poder reutilizar uma palavra-passe**: introduza o número de palavras-passe recentes que não podem ser reutilizadas, entre 1 e 24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

- **Encriptação do armazenamento de dados no dispositivo**: escolha **Exigir** para encriptar o armazenamento de dados nos dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Uma vez que os dispositivos Android Enterprise impõem a encriptação, não tem de configurar esta definição.

## <a name="work-profile"></a>Perfil profissional

### <a name="device-health"></a>Device health

- **Dispositivos desbloqueados por rooting**: escolha **Bloquear** para marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir que o dispositivo esteja ao nível ou abaixo do Nível de Ameaça de Dispositivos**: Selecione o nível máximo de ameaça de dispositivo permitido avaliado pelo seu [serviço de defesa contra ameaças móveis](mobile-threat-defense.md). Os dispositivos que excedem esse nível de ameaça são marcados como não compatíveis. Para utilizar esta definição, selecione o nível de ameaça permitido:

  - **Não configurado** (predefinição): Essa configuração não é avaliada quanto à conformidade ou não à conformidade.
  - **Protegido**: esta opção é a mais segura e significa que o dispositivo não pode ter ameaças. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo será avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo será avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alto**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services configurado**: **exija** que a aplicação Google Play Services esteja instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Fornecedor de segurança atualizado**: **exija** que um fornecedor de segurança atualizado proteja um dispositivo contra vulnerabilidades conhecidas. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Atestado do dispositivo SafetyNet**: introduza o nível do [Atestado SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** (predefinição): a definição não é avaliada quanto à conformidade ou não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Nos dispositivos Android Enterprise, a **Análise de ameaças nas aplicações** é uma política de configuração do dispositivo. Ao utilizar uma política de configuração, os administradores podem ativar a definição num dispositivo. Veja [Definições de restrição de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do SO**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode atualizar a versão do dispositivo e, em seguida, aceder aos recursos da organização.
- **Versão máxima do SO**: quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Enquanto a regra não for alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da organização.

### <a name="system-security"></a>Segurança do sistema

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exija** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Esta definição é aplicada ao nível do dispositivo. Se precisar apenas de exigir uma palavra-passe ao nível do perfil de trabalho, utilize uma política de configuração. Veja [Definições de configuração de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).
- **Tipo obrigatório de palavra-passe**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos, numérico** (predefinição): introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Complexo numérico**: introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Pelo menos, alfabético**: introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Pelo menos, alfanumérico**: introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Pelo menos, alfanumérico com símbolos**: introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.

- **Minutos de inatividade antes de a palavra-passe ser exigida**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Número de dias até expirar a palavra-passe**: selecione o número de dias antes de a palavra-passe expirar e ser necessário que o utilizador final crie uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser reutilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

#### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo**: escolha **Exigir** para encriptar o armazenamento de dados nos dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. 

  Uma vez que os dispositivos Android Enterprise impõem a encriptação, não tem de configurar esta definição.

#### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: opte por **bloquear** os dispositivos que tenham a opção **Segurança** > **Origens Desconhecidas** ativada (suportado no Android 4.0 a Android 7.X. Não suportado no Android 8.0 e posterior). Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade.

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

  Uma vez que os dispositivos Android Enterprise restringem sempre a instalação a partir de origens desconhecidas, não tem de configurar esta definição.

- **Integridade de tempo de execução de aplicações do portal da empresa**: escolha **Exigir** para confirmar que a aplicação do Portal da Empresa cumpre os seguintes requisitos:

  - Tem o ambiente de tempo de execução predefinido instalado
  - Está corretamente assinada
  - Não está no modo de depuração
  - Foi instalada a partir de uma origem conhecida

  Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

- **Bloquear a depuração de USB no dispositivo**: escolha **Bloquear** para impedir que os dispositivos utilizem a funcionalidade de depuração de USB. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Uma vez que a depuração de USB já está desativada nos dispositivos Android Enterprise, não tem de configurar esta definição.

- **Nível mínimo da correção de segurança**: selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato *AAAA-MM-DD*.

## <a name="next-steps"></a>Passos seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos Android](compliance-policy-create-android.md).
