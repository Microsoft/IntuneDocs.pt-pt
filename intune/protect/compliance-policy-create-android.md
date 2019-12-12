---
title: Definições de conformidade de dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os dispositivos Android no Microsoft Intune. Defina regras de palavra-passe, escolha uma versão mínima ou máxima do sistema operativo, restrinja aplicações específicas, impeça a reutilização de palavras-passe e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8efb9dcf9129375252b5d9a7d1e6255dce39625c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801399"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android para marcar dispositivos como conformes ou não conformes com o Intune

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Android no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes, defina um nível de ameaça permitido, ative o Google Play Protect e muito mais.

Esta funcionalidade aplica-se a:

- Administrador do dispositivo Android

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Para **plataforma**, selecione **administrador do dispositivo Android**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Dispositivos desbloqueados por rooting**:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - Marca de **bloqueio** de dispositivos com raiz (jailbreak) como não compatível.

- **Exigir que o dispositivo esteja ao nível ou abaixo do Nível de Ameaça de Dispositivos**:

  Use essa configuração para fazer a avaliação de risco de um serviço de defesa contra ameaças móveis conectado como uma condição para conformidade.
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade. 
  - **Seguro** – essa opção é a mais segura, pois o dispositivo não pode ter nenhuma ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo** -o dispositivo será avaliado como compatível se apenas ameaças de nível baixo estiverem presentes. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** -o dispositivo será avaliado como em conformidade se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** -essa opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services configurado**:

  Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados.

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.  
  - **Exigir** -requer que o aplicativo de serviços Google Play esteja instalado e habilitado.  

- **Fornecedor de segurança atualizado**:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** – exigir que um provedor de segurança atualizado possa proteger um dispositivo contra vulnerabilidades conhecidas.

- **Análise de ameaças nas aplicações**:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Require** -requer que o recurso Android **Verify apps** esteja habilitado.

  > [!NOTE]
  > Na plataforma Android legada, esta funcionalidade é uma definição de conformidade. O Intune só consegue verificar se esta definição está ativada ao nível do dispositivo.

- **Atestado do dispositivo SafetyNet**:

  Insira o nível de [atestado SafetyNET](https://developer.android.com/training/safetynet/attestation.html) que deve ser atendido. As opções são:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Para configurar definições do Google Play Protect através de políticas de proteção de aplicações, veja [Definições de políticas de proteção de aplicações do Intune](../apps/app-protection-policy-settings-android.md#conditional-launch) no Android.

## <a name="device-properties"></a>Propriedades do Dispositivo

### <a name="operating-system-version"></a>Versão do Sistema Operativo 

- **Versão mínima do SO**:

  quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.

  *Por padrão, nenhuma versão é configurada*.

- **Versão máxima do SO**:

  quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. O usuário é solicitado a entrar em contato com o administrador de ti. Até que uma regra seja alterada para permitir a versão do sistema operacional, esse dispositivo não poderá acessar os recursos da empresa.

  *Por padrão, nenhuma versão é configurada*.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

<!-- Removed
- **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -os usuários devem inserir uma senha antes que possam acessar seu dispositivo.

- **Tipo obrigatório de palavra-passe**:

  escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:

  - **Dispositivo padrão** – para avaliar a conformidade de senha, selecione uma senha que não seja o **padrão do dispositivo**.
  - **Biométrica de segurança baixa**
  - **Pelo menos numérica**
  - Numerais **numéricos complexos** repetidos ou consecutivos, como `1111` ou `1234`, não são permitidos.
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**:  
  *Com suporte no Android 4,0 e posterior, ou KNOX 4,0 e posterior.*

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -criptografar o armazenamento de dados em seus dispositivos. Os dispositivos são encriptados quando seleciona a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - Dispositivos de bloqueio **de bloco com** segurança > fontes habilitadas para **origens desconhecidas** (*com suporte no Android 4,0 até o Android 7. x. Sem suporte no Android 8,0 e posterior.* ).

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade.

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Integridade de tempo de execução de aplicações do portal da empresa**:

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -escolha *exigir* para confirmar se o aplicativo portal da empresa atende a todos os seguintes requisitos:

    - Tem o ambiente de tempo de execução predefinido instalado
    - Está corretamente assinada
    - Não está no modo de depuração
    - Foi instalada a partir de uma origem conhecida

- **Bloquear a depuração de USB no dispositivo** *(Android 4,2 ou posterior)* :

  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Bloquear** – impedir que os dispositivos usem o recurso de depuração de USB.

- **Nível mínimo de patch de segurança** *(Android 6,0 ou posterior)* :

  selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato `YYYY-MM-DD`.

  *Por padrão, nenhuma data é configurada*.

- **Aplicações restritas**:

  Insira o **nome do aplicativo** e a **ID do pacote de aplicativo** para aplicativos que devem ser restritos e, em seguida, selecione **Adicionar**. Um dispositivo com pelo menos uma aplicação restrita instalada é marcado como não conforme.

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos Android Enterprise](compliance-policy-create-android-for-work.md).
