---
title: Definições de conformidade do Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os dispositivos Android Enterprise no Microsoft Intune. Defina regras de palavra-passe, escolha uma versão mínima ou máxima do sistema operativo, restrinja aplicações específicas, impeça a reutilização de palavras-passe e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/07/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 163f5dd246fb17e7d67a8baffbae9926f2f4bc79
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256446"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android Enterprise para marcar dispositivos como conformes ou não conformes com o Intune

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Android Enterprise no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes, defina um nível de ameaça permitido, ative o Google Play Protect e muito mais.

Esta funcionalidade aplica-se a:

- Android Enterprise

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

> [!IMPORTANT]
> As políticas de conformidade também se aplicam aos dispositivos Android Enterprise dedicados. Se uma política de conformidade for atribuída a um dispositivo dedicado, o dispositivo poderá ser apresentado como **Não conforme**. O Acesso Condicional e a aplicação da conformidade não estão disponíveis em dispositivos dedicados. Realize algumas tarefas ou ações para que os dispositivos dedicados fiquem em conformidade com as políticas atribuídas.

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Android Enterprise**.

## <a name="device-owner"></a>Proprietário do dispositivo

### <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exija que o dispositivo esteja no nível de ameaça**do dispositivo : Selecione o nível máximo de ameaça permitido para dispositivos avaliado pelo seu serviço de defesa de [ameaças móveis](mobile-threat-defense.md). Os dispositivos que excedam este nível de ameaça são marcados sem conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:

  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Secured** - Esta opção é a mais segura, e significa que o dispositivo não pode ter ameaças. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: - O dispositivo é avaliado como conforme se apenas houver ameaças de baixo nível. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** - O dispositivo é avaliado como conforme se as ameaças presentes no dispositivo forem de baixo ou médio nível. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** - Esta opção é a menos segura, pois permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
> [!NOTE] 
> Todos os fornecedores de Mobile Threat Defense (MTD) são suportados nas implementações do proprietário do dispositivo Android Enterprise utilizando a configuração da aplicação. Consulte o seu fornecedor MTD para saber se é necessária a configuração exata necessária para suportar as plataformas Android Enterprise Device Owner em Intune.

#### <a name="google-play-protect"></a>Google Play Protect

- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** *(predefinido)* - A definição não é avaliada para conformidade ou incumprimento.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

### <a name="device-properties"></a>Propriedades do Dispositivo

#### <a name="operating-system-version"></a>Versão do Sistema Operativo

- **Versão mínima do SISTEMA**: Quando um dispositivo não cumpre o requisito mínimo de versão de OS, é reportado como incompatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode atualizar a versão do dispositivo e, em seguida, aceder aos recursos da organização.

  *Por defeito, nenhuma versão está configurada.*

- **Versão máxima do SISTEMA**: Quando um dispositivo está a utilizar uma versão S mais tarde do que a versão da regra, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Enquanto a regra não for alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da organização.

  *Por defeito, nenhuma versão está configurada.*

- **Nível mínimo de correção**de segurança: Selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data deve ser inserida no formato YYYY-MM-DD.

  *Por predefinição, nenhuma data está configurada.*


### <a name="system-security"></a>Segurança do sistema

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Exigir** - Os utilizadores devem introduzir uma palavra-passe antes de poderem aceder ao seu dispositivo.
  - **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
    - **Predefinição do dispositivo** - Para avaliar a conformidade com a palavra-passe, certifique-se de selecionar uma força de senha diferente da **predefinição do Dispositivo**.  
    - **Palavra-passe obrigatória, sem restrições**
    - ** - biométrico fraco** [Forte vs. biométrico fraco](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (abre o site do Android)
    - **Numérico** *(predefinição):* A palavra-passe só deve ser números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Complexo numérico** - Números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfabética** - São necessárias letras no alfabeto. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfanumérico** - Inclui letras maiúsculas, letras minúsculas e caracteres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfanumérico com símbolos** - Inclui letras maiúsculas, letras minúsculas, caracteres numéricos, marcas de pontuação e símbolos. Introduza também:
    
    Dependendo do tipo de *palavra-passe* que selecionar, estão disponíveis as seguintes definições:  
    - Comprimento mínimo da **palavra-passe**: Introduza o comprimento mínimo que a palavra-passe deve ter, entre 4 e 16 caracteres.  

    - **Número de caracteres necessários**: Introduza o número de caracteres que a palavra-passe deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres minúsculos necessários**: Introduza o número de caracteres minúsculos que a palavra-passe deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres maiúsculos necessários**: Introduza o número de caracteres maiúsculos que a palavra-passe deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres não-letra necessários**: Introduza o número de não-letras (qualquer outra coisa que não seja letras no alfabeto) a palavra-passe deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres numéricos necessários**: Introduza o número de caracteres numéricos (`1`, `2`, `3`, e assim por diante) a palavra-passe deve ter, entre 0 e 16 caracteres.
    
    - **Número de caracteres de símbolo necessários**: Introduza o número de caracteres de símbolos (`&`, `#`, `%`, e assim por diante) a palavra-passe deve ter, entre 0 e 16 caracteres.
 
- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. As opções incluem o padrão de *Não configurado*, e de *1 Minuto* a 8 *horas*.

- Número de dias até que a **palavra-passe expire**: Introduza o número de dias, entre 1-365, até que a palavra-passe do dispositivo seja alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.

   *Por defeito, nenhum valor está configurado.*

- **Número de palavras-passe necessárias antes de o utilizador poder reutilizar uma palavra-passe**: Introduza o número de senhas recentes que não podem ser reutilizadas, entre 1 e 24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.  

    *Por defeito, nenhuma versão está configurada.*

#### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Require** - Criptografe o armazenamento de dados nos seus dispositivos.  

  Uma vez que os dispositivos Android Enterprise impõem a encriptação, não tem de configurar esta definição.

## <a name="work-profile"></a>Perfil profissional

### <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Dispositivos desbloqueados por rooting**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Bloco** - Mark dispositivos enraizados (jailbroken) como não conformes.  

- **Exija que o dispositivo esteja no nível de ameaça**do dispositivo : Selecione o nível máximo de ameaça permitido para dispositivos avaliado pelo seu serviço de defesa de [ameaças móveis](mobile-threat-defense.md). Os dispositivos que excedam este nível de ameaça são marcados sem conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:

  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Secured** - Esta opção é a mais segura, e significa que o dispositivo não pode ter ameaças. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo** - O dispositivo é avaliado como conforme se apenas houver ameaças de baixo nível. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** - O dispositivo é avaliado como conforme se as ameaças presentes no dispositivo forem de baixo ou médio nível. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** - Esta opção é a menos segura, pois permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services configurado**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Require** - Require that the Google Play services app is installand and enabled. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. 
  
- **Fornecedor de segurança atualizado**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Require** - Exigir que um fornecedor de segurança atualizado possa proteger um dispositivo de vulnerabilidades conhecidas. 
  
- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** *(predefinido)* - A definição não é avaliada para conformidade ou incumprimento.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Nos dispositivos Android Enterprise, a **Análise de ameaças nas aplicações** é uma política de configuração do dispositivo. Ao utilizar uma política de configuração, os administradores podem ativar a definição num dispositivo. Veja [Definições de restrição de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Propriedades do Dispositivo

#### <a name="operating-system-version"></a>Versão do Sistema Operativo

- **Versão mínima do SISTEMA**: Quando um dispositivo não cumpre o requisito mínimo de versão de OS, é reportado como incompatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode atualizar a versão do dispositivo e, em seguida, aceder aos recursos da organização.

  *Por defeito, nenhuma versão está configurada.*

- **Versão máxima do SISTEMA**: Quando um dispositivo está a utilizar uma versão S mais tarde do que a versão da regra, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Enquanto a regra não for alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da organização.

  *Por defeito, nenhuma versão está configurada.*

### <a name="system-security"></a>Segurança do sistema

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento. 
  - **Exigir** - Os utilizadores devem introduzir uma palavra-passe antes de poderem aceder ao seu dispositivo.  

  Esta definição aplica-se ao nível do dispositivo. Se precisar apenas de exigir uma palavra-passe ao nível do perfil de trabalho, utilize uma política de configuração. Veja [Definições de configuração de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

- **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos numérico** *(predefinição*): Introduza o comprimento mínimo da **palavra-passe** que um utilizador deve introduzir, entre 4 e 16 caracteres.
  - **Complexo numérico**: Introduza o comprimento mínimo da **palavra-passe** que um utilizador deve introduzir, entre 4 e 16 caracteres.
  - **Pelo menos alfabético**: Introduza o comprimento mínimo da **palavra-passe** que um utilizador deve introduzir, entre 4 e 16 caracteres.
  - **Pelo menos alfanumérico:** Introduza o comprimento mínimo da **palavra-passe** que um utilizador deve introduzir, entre 4 e 16 caracteres.
  - **Pelo menos alfanumérico com símbolos**: Introduza o comprimento mínimo da **palavra-passe** que um utilizador deve introduzir, entre 4 e 16 caracteres.

  Dependendo do tipo de *palavra-passe* que selecionar, estão disponíveis as seguintes definições:  
  - **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. As opções incluem o padrão de *Não configurado*, e de *1 Minuto* a 8 *horas*.

  - Número de dias até que a **palavra-passe expire**: Introduza o número de dias, entre 1-365, até que a palavra-passe do dispositivo seja alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.

  - Comprimento mínimo da **palavra-passe**: Introduza o comprimento mínimo que a palavra-passe deve ter, entre 4 e 16 caracteres. 
  
  - **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser utilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

#### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Require** - Criptografe o armazenamento de dados nos seus dispositivos.  

  Uma vez que os dispositivos Android Enterprise impõem a encriptação, não tem de configurar esta definição.

#### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Block** - Block devices with **Security** > **Unknown Sources** enabled sources (*suportado no Android 4.0 através do Android 7.x. Não suportado pelo Android 8.0 e mais tarde).*  

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade.

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

  Uma vez que os dispositivos Android Enterprise restringem sempre a instalação a partir de origens desconhecidas, não tem de configurar esta definição.

- **Integridade de tempo de execução de aplicações do portal da empresa**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Exigir** - Escolha *Exigir* confirmar que a aplicação Portal da Empresa satisfaz todos os seguintes requisitos:
    - Tem o ambiente de tempo de execução predefinido instalado
    - Está corretamente assinada
    - Não está no modo de depuração
    - Foi instalada a partir de uma origem conhecida

- **Bloquear a depuração de USB no dispositivo**: 
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Bloquear** - Evitar que os dispositivos utilizem a função de depuração USB.  

  Uma vez que a depuração de USB já está desativada nos dispositivos Android Enterprise, não tem de configurar esta definição.

- **Nível mínimo de correção**de segurança: Selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data deve ser inserida no formato YYYY-MM-DD.

  *Por predefinição, nenhuma data está configurada.*

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos Android](compliance-policy-create-android.md).
