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
ms.openlocfilehash: 60244bb268f7becadc427c397d7c2d1562bcf6b5
ms.sourcegitcommit: ea81ad5f33f18d9fe43254e27e02de5eaef74a05
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75722611"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android Enterprise para marcar dispositivos como conformes ou não conformes com o Intune

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

- **Exigir que o dispositivo esteja no nível de ameaça do dispositivo ou abaixo**dele: selecione o nível máximo permitido de ameaça do dispositivo avaliado pelo seu [serviço de defesa contra ameaças móveis](mobile-threat-defense.md). Os dispositivos que excedem esse nível de ameaça são marcados como não compatíveis. Para utilizar esta definição, selecione o nível de ameaça permitido:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Seguro** – essa opção é a mais segura e significa que o dispositivo não pode ter nenhuma ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**:-o dispositivo será avaliado como em conformidade se apenas ameaças de nível baixo estiverem presentes. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** -o dispositivo será avaliado como em conformidade se as ameaças presentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** -essa opção é a menos segura, pois permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
> [!NOTE] 
> Todos os provedores de MTD (defesa contra ameaças móveis) têm suporte em implantações de proprietário do dispositivo Android Enterprise usando a configuração do aplicativo. Verifique com seu provedor MTD a configuração exata necessária para dar suporte a plataformas do proprietário do dispositivo Android Enterprise no Intune.

#### <a name="google-play-protect"></a>Google Play Protect

- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** (*padrão*)-a configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

### <a name="device-properties"></a>Propriedades do Dispositivo

#### <a name="operating-system-version"></a>Versão do Sistema Operativo

- **Versão mínima do so**: quando um dispositivo não atende ao requisito mínimo de versão do sistema operacional, ele é relatado como não compatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode atualizar a versão do dispositivo e, em seguida, aceder aos recursos da organização.

  *Por padrão, nenhuma versão é configurada*.

- **Versão máxima do sistema operacional**: quando um dispositivo estiver usando uma versão do sistema operacional posterior à versão na regra, o acesso aos recursos da organização será bloqueado. É pedido ao utilizador para contactar o administrador de TI. Enquanto a regra não for alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da organização.

  *Por padrão, nenhuma versão é configurada*.

- **Nível mínimo de patch de segurança**: selecione o nível de patch de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data deve ser inserida no formato AAAA-MM-DD.

  *Por padrão, nenhuma data é configurada*.


### <a name="system-security"></a>Segurança do sistema

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -os usuários devem inserir uma senha antes que possam acessar seu dispositivo. 

  Essa configuração se aplica ao nível do dispositivo. Se precisar apenas de exigir uma palavra-passe ao nível do perfil de trabalho, utilize uma política de configuração. Veja [Definições de configuração de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

  - **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
    - **Dispositivo padrão** – para avaliar a conformidade de senha, selecione uma senha que não seja o **padrão do dispositivo**.  
    - **Palavra-passe obrigatória, sem restrições**
    - **Biométricas fracas** - [forte e baixa biometria](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (abre o site do Android)
    - **Numeric** (*padrão*): a senha deve ser apenas números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Caracteres numéricos complexos** -números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - Letras **maiúsculas** no alfabeto são necessárias. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfanumérico** -inclui letras maiúsculas, letras minúsculas e caracteres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
    - **Alfanumérico com símbolos** -inclui letras maiúsculas, letras minúsculas, caracteres numéricos, sinais de Pontuação e símbolos. Introduza também:
    
    Dependendo do tipo de *senha* selecionado, as seguintes configurações estão disponíveis:  
    - **Comprimento mínimo da senha**: Insira o comprimento mínimo que a senha deve ter, entre 4 e 16 caracteres.  

    - **Número de caracteres necessários**: Insira o número de caracteres que a senha deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres minúsculos necessários**: Insira o número de caracteres minúsculos que a senha deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres maiúsculos necessários**: Insira o número de caracteres maiúsculos que a senha deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres que não são de letra necessários**: Insira o número de letras que não sejam maiúsculas (algo que não seja letras no alfabeto) que a senha deve ter, entre 0 e 16 caracteres.

    - **Número de caracteres numéricos necessários**: Insira o número de caracteres numéricos (`1`, `2`, `3`e assim por diante) que a senha deve ter, entre 0 e 16 caracteres.
    
    - **Número de caracteres de símbolo necessários**: Insira o número de caracteres de símbolo (`&`, `#`, `%`e assim por diante) que a senha deve ter, entre 0 e 16 caracteres.
 
- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. As opções incluem o padrão de *não configurado*e de *1 minuto* a *8 horas*.

- **Número de dias até a senha expirar**: Insira o número de dias, entre 1-365, até que a senha do dispositivo deva ser alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.

   *Por padrão, nenhum valor é configurado*.

- **Número de senhas necessárias antes que o usuário possa reutilizar uma senha**: Insira o número de senhas recentes que não podem ser reutilizadas, entre 1-24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.  

    *Por padrão, nenhuma versão é configurada*.

#### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -criptografar o armazenamento de dados em seus dispositivos.  

  Uma vez que os dispositivos Android Enterprise impõem a encriptação, não tem de configurar esta definição.

## <a name="work-profile"></a>Perfil profissional

### <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Dispositivos desbloqueados por rooting**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - Marca de **bloqueio** de dispositivos com raiz (jailbreak) como não compatível.  

- **Exigir que o dispositivo esteja no nível de ameaça do dispositivo ou abaixo**dele: selecione o nível máximo permitido de ameaça do dispositivo avaliado pelo seu [serviço de defesa contra ameaças móveis](mobile-threat-defense.md). Os dispositivos que excedem esse nível de ameaça são marcados como não compatíveis. Para utilizar esta definição, selecione o nível de ameaça permitido:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Seguro** – essa opção é a mais segura e significa que o dispositivo não pode ter nenhuma ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo** -o dispositivo será avaliado como compatível se apenas ameaças de nível baixo estiverem presentes. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** -o dispositivo será avaliado como em conformidade se as ameaças presentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** -essa opção é a menos segura, pois permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services configurado**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -requer que o aplicativo de serviços Google Play esteja instalado e habilitado. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. 
  
- **Fornecedor de segurança atualizado**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** – exigir que um provedor de segurança atualizado possa proteger um dispositivo contra vulnerabilidades conhecidas. 
  
- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** (*padrão*)-a configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Nos dispositivos Android Enterprise, a **Análise de ameaças nas aplicações** é uma política de configuração do dispositivo. Ao utilizar uma política de configuração, os administradores podem ativar a definição num dispositivo. Veja [Definições de restrição de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Propriedades do Dispositivo

#### <a name="operating-system-version"></a>Versão do Sistema Operativo

- **Versão mínima do so**: quando um dispositivo não atende ao requisito mínimo de versão do sistema operacional, ele é relatado como não compatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode atualizar a versão do dispositivo e, em seguida, aceder aos recursos da organização.

  *Por padrão, nenhuma versão é configurada*.

- **Versão máxima do sistema operacional**: quando um dispositivo estiver usando uma versão do sistema operacional posterior à versão na regra, o acesso aos recursos da organização será bloqueado. É pedido ao utilizador para contactar o administrador de TI. Enquanto a regra não for alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da organização.

  *Por padrão, nenhuma versão é configurada*.

### <a name="system-security"></a>Segurança do sistema

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade. 
  - **Exigir** -os usuários devem inserir uma senha antes que possam acessar seu dispositivo.  

  Essa configuração se aplica ao nível do dispositivo. Se precisar apenas de exigir uma palavra-passe ao nível do perfil de trabalho, utilize uma política de configuração. Veja [Definições de configuração de dispositivos Android Enterprise](../configuration/device-restrictions-android-for-work.md).

- **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos numeric** (*padrão*): Insira o **comprimento mínimo da senha** que um usuário deve inserir, entre 4 e 16 caracteres.
  - **Complexo numérico**: Insira o **comprimento mínimo da senha** que um usuário deve inserir, entre 4 e 16 caracteres.
  - **Pelo menos alfabético**: Insira o **comprimento mínimo da senha** que um usuário deve inserir, entre 4 e 16 caracteres.
  - **Pelo menos alfanumérico**: Insira o **comprimento mínimo da senha** que um usuário deve inserir, entre 4 e 16 caracteres.
  - **Pelo menos alfanumérico com símbolos**: Insira o **comprimento mínimo da senha** que um usuário deve inserir, entre 4 e 16 caracteres.

  Dependendo do tipo de *senha* selecionado, as seguintes configurações estão disponíveis:  
  - **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. As opções incluem o padrão de *não configurado*e de *1 minuto* a *8 horas*.

  - **Número de dias até a senha expirar**: Insira o número de dias, entre 1-365, até que a senha do dispositivo deva ser alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.

  - **Comprimento mínimo da senha**: Insira o comprimento mínimo que a senha deve ter, entre 4 e 16 caracteres. 
  
  - **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser utilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

#### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -criptografar o armazenamento de dados em seus dispositivos.  

  Uma vez que os dispositivos Android Enterprise impõem a encriptação, não tem de configurar esta definição.

#### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - Dispositivos de bloqueio **de bloco com** **segurança** > fontes habilitadas para **origens desconhecidas** (*com suporte no Android 4,0 até o Android 7. x. Sem suporte no Android 8,0 e posterior*).  

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade.

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

  Uma vez que os dispositivos Android Enterprise restringem sempre a instalação a partir de origens desconhecidas, não tem de configurar esta definição.

- **Integridade de tempo de execução de aplicações do portal da empresa**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -escolha *exigir* para confirmar se o aplicativo portal da empresa atende a todos os seguintes requisitos:
    - Tem o ambiente de tempo de execução predefinido instalado
    - Está corretamente assinada
    - Não está no modo de depuração
    - Foi instalada a partir de uma origem conhecida

- **Bloquear a depuração de USB no dispositivo**: 
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Bloquear** – impedir que os dispositivos usem o recurso de depuração de USB.  

  Uma vez que a depuração de USB já está desativada nos dispositivos Android Enterprise, não tem de configurar esta definição.

- **Nível mínimo de patch de segurança**: selecione o nível de patch de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data deve ser inserida no formato AAAA-MM-DD.

  *Por padrão, nenhuma data é configurada*.

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos Android](compliance-policy-create-android.md).
