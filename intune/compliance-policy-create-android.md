---
title: Definições de conformidade do dispositivo Android no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições que pode utilizar ao definir a conformidade dos seus dispositivos Android no Microsoft Intune. Definir regras de palavra-passe, escolher uma versão de sistema operativo mínimo ou máximo, restringir aplicações específicas, impedir a reutilização palavra-passe e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7670af46657fed048bfe10b8659eae6d45db7620
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423582"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android para marcar dispositivos como compatíveis ou não compatíveis com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta uma lista e descreve as definições de conformidade diferentes que pode configurar em dispositivos Android no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para marcar os dispositivos com root (jailbreak) como não conforme, definir um nível de ameaça permitido, ativar o Google Play Protect e muito mais.

Esta funcionalidade aplica-se a:

- Android

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger recursos da sua organização. Para saber mais sobre as políticas de conformidade e o que fazer, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Android**.

## <a name="device-health"></a>Device health

- **Dispositivos com jailbreak**: Escolher **bloco** para marcar os dispositivos com root (com jailbreak) como não conforme. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir o dispositivo esteja ao nível ou abaixo do nível de ameaça do dispositivo**: Utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: Esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta**: Esta opção é menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

### <a name="google-play-protect"></a>Proteger o Google Play

- **Serviços do Google Play está configurado**: **Exigir** que o Google Play dos serviços de aplicação é instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Fornecedor de segurança atualizado**: **Exigir** que um fornecedor de segurança atualizado Proteja um dispositivo contra vulnerabilidades conhecidas. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Análise de ameaças nas aplicações**: **Exigir** que o Android **verificar aplicações** funcionalidade está ativada. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  > [!NOTE]
  > Na plataforma Android legada, esta funcionalidade é uma definição de conformidade. O Intune só consegue verificar se esta definição está ativada ao nível do dispositivo.

- **Dispositivo safetynet**: Introduza o nível de [atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que têm de ser cumpridos. As opções são:
  - **Não configurado** (predefinição): Não é avaliada a definição de conformidade ou de não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Para configurar definições do Google Play Protect através de políticas de proteção de aplicações, consulte [definições de política de proteção de aplicações do Intune](app-protection-policy-settings-android.md#conditional-launch) no Android.

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **Versão mínima do SO**: Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima**: Quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até uma regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Tipo de palavra-passe obrigatório**: Escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e outros caracteres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos, numérico** (predefinição)
  - **Complexo numérico**: Números repetidos ou consecutivos, tais como `1111` ou `1234`, não são permitidos.
  - **Pelo menos alfabética** 
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e o utilizador tem de criar uma nova palavra-passe.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe recentes que não podem ser reutilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo de** (Android 4.0 e superior ou KNOX 4.0 e superior): Escolher **requerem** para encriptar o armazenamento de dados nos seus dispositivos. Os dispositivos são encriptados quando seleciona a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: Optar por **bloco** dispositivos com o "Segurança > origens desconhecidas" ativada origens (suportadas no Android 4.0 – Android 7.x; não suportadas pelo Android 8.0 e posteriores). Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade. 

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Integridade de tempo de execução da aplicação do portal da empresa**: Escolher **requerem** para confirmar o Portal da empresa a aplicação cumpre os seguintes requisitos:

  - Tem o ambiente de tempo de execução predefinido instalado
  - Está corretamente assinada
  - Não está no modo de depuração
  - Foi instalada a partir de uma origem conhecida

  Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

- **Depuração de USB de bloco no dispositivo** (Android 4.2 ou posterior): Escolher **bloco** para impedir que os dispositivos a utilizar a funcionalidade de depuração de USB. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Nível de patch de segurança mínimo** (Android 6.0 ou posterior): Selecione o nível de patch de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato `YYYY-MM-DD`.
- **Aplicações restritas**: Introduza o **nome da aplicação** e **ID do pacote de aplicação** para aplicações que devem ser restringidas. Selecione **Adicionar**. Um dispositivo com pelo menos uma aplicação restrita instalada é marcado como não conforme.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="locations"></a>Localizações

Na sua política, pode forçar a conformidade com a localização do dispositivo. Escolha a partir de localizações existentes. Ainda não tem uma localização? [Utilize localizações (cerca de rede)](use-network-locations.md) no Intune fornece algumas diretrizes.

1. Escolher **localizações** > **selecionar localizações**.
2. Na lista, verifique a sua localização > **selecione**.
3. **Guarde** a política.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).
- [Monitorizar as suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte a [definições de política de conformidade para Android Enterprise](compliance-policy-create-android-for-work.md) dispositivos.
