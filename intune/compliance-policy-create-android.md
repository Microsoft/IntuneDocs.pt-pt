---
title: Definições de conformidade de dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os dispositivos Android no Microsoft Intune. Defina regras de palavra-passe, escolha uma versão mínima ou máxima do sistema operativo, restrinja aplicações específicas, impeça a reutilização de palavras-passe e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7c6cec515bfda95fed922785705b0e0b5339983
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/25/2019
ms.locfileid: "71305084"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android para marcar dispositivos como conformes ou não conformes com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Android no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes, defina um nível de ameaça permitido, ative o Google Play Protect e muito mais.

Esta funcionalidade aplica-se a:

- Android

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Android**.

## <a name="device-health"></a>Device health

- **Dispositivos desbloqueados por rooting**: escolha **Bloquear** para marcar os dispositivos desbloqueados por rooting (jailbreak) como não conformes. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir que o dispositivo esteja ao nível ou abaixo do Nível de Ameaça de Dispositivos**: Use essa configuração para fazer a avaliação de risco da solução de segurança de ponto de extremidade móvel de consulta como uma condição para conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo será avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo será avaliado como estando em conformidade se as ameaças existentes forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alto**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services configurado**: **exija** que a aplicação Google Play Services esteja instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Fornecedor de segurança atualizado**: **exija** que um fornecedor de segurança atualizado proteja um dispositivo contra vulnerabilidades conhecidas. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Análise de ameaças nas aplicações**: **exija** que a funcionalidade **Verificar Aplicações** do Android esteja ativada. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  > [!NOTE]
  > Na plataforma Android legada, esta funcionalidade é uma definição de conformidade. O Intune só consegue verificar se esta definição está ativada ao nível do dispositivo.

- **Atestado do dispositivo SafetyNet**: introduza o nível do [Atestado SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** (predefinição): a definição não é avaliada quanto à conformidade ou não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Para configurar definições do Google Play Protect através de políticas de proteção de aplicações, veja [Definições de políticas de proteção de aplicações do Intune](app-protection-policy-settings-android.md#conditional-launch) no Android.

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **Versão mínima do SO**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão máxima do SO**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até uma regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exija** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de conter.
- **Tipo obrigatório de palavra-passe**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
  - **Padrão do dispositivo**: Para avaliar a conformidade de senha, certifique-se de selecionar uma senha que não seja o **padrão do dispositivo**.
  - **Biométrica de segurança baixa**
  - **Pelo menos, numérico** (predefinição)
  - **Complexo numérico**: os números repetidos ou consecutivos, tal como `1111` ou `1234`, não são permitidos.
  - **Pelo menos alfabética** 
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**

- **Minutos de inatividade antes de a palavra-passe ser exigida**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Expiração da palavra-passe (dias)** : selecione o número de dias antes de a palavra-passe expirar e ser necessário que o utilizador final crie uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser reutilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo** (Android 4.0 e superior ou KNOX 4.0 e superior): escolha **Exigir** para encriptar o armazenamento de dados nos dispositivos. Os dispositivos são encriptados quando seleciona a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: opte por **bloquear** os dispositivos que tenham a opção “Segurança > Origens Desconhecidas” ativada (suportado no Android 4.0 a Android 7.x. Não suportado no Android 8.0 e posterior). Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade. 

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Integridade de tempo de execução de aplicações do portal da empresa**: escolha **Exigir** para confirmar que a aplicação do Portal da Empresa cumpre os seguintes requisitos:

  - Tem o ambiente de tempo de execução predefinido instalado
  - Está corretamente assinada
  - Não está no modo de depuração
  - Foi instalada a partir de uma origem conhecida

  Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

- **Bloquear a depuração de USB no dispositivo** (Android 4.2 ou posterior): escolha **Bloquear** para impedir que os dispositivos utilizem a funcionalidade de depuração de USB. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Nível de correção de segurança mínimo** (Android 6.0 ou posterior): selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato `YYYY-MM-DD`.
- **Aplicações restritas**: introduza o **Nome da aplicação** e o **ID de pacote da aplicação** para aplicações que devem ser restringidas. Selecione **Adicionar**. Um dispositivo com pelo menos uma aplicação restrita instalada é marcado como não conforme.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="locations"></a>Localizações

Na sua política, pode forçar a conformidade com a localização do dispositivo. Escolha uma das localizações existentes. Ainda não tem uma localização? Veja [Utilizar Localizações (barreira de rede)](use-network-locations.md) no Intune para obter algumas orientações.

1. Escolha **Localizações** > **Selecionar localizações**.
2. Na lista, verifique a sua localização > **Selecionar**.
3. **Guarde** a política.

## <a name="next-steps"></a>Passos seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos Android Enterprise](compliance-policy-create-android-for-work.md).
