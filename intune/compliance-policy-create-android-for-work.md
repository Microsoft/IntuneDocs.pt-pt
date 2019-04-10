---
title: As definições de conformidade do Android Enterprise no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições que pode utilizar quando a definição de conformidade para os seus dispositivos Android Enterprise no Microsoft Intune. Definir regras de palavra-passe, escolher uma versão de sistema operativo mínimo ou máximo, restringir aplicações específicas, impedir a reutilização palavra-passe e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16db0acab84a1095c40e9a92648c75c2581187cd
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423565"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Android Enterprise para marcar dispositivos como compatíveis ou não compatíveis com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Android Enterprise no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para marcar os dispositivos com root (jailbreak) como não conforme, definir um nível de ameaça permitido, ativar o Google Play Protect e muito mais.

Esta funcionalidade aplica-se a:

- Android Enterprise

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger recursos da sua organização. Para saber mais sobre as políticas de conformidade e o que fazer, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Para **plataforma**, selecione **Android Enterprise**.

## <a name="device-health"></a>Device health

- **Dispositivos com jailbreak**: Escolher **bloco** para marcar os dispositivos com root (com jailbreak) como não conforme. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir o dispositivo esteja ao nível ou abaixo do nível de ameaça do dispositivo**: Utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: Esta opção é a mais segura e significa que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças que estão presentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta**: Esta opção é menos segura, já que permite a todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

### <a name="google-play-protect"></a>Proteger o Google Play

- **Serviços do Google Play está configurado**: **Exigir** que o Google Play dos serviços de aplicação é instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Fornecedor de segurança atualizado**: **Exigir** que um fornecedor de segurança atualizado Proteja um dispositivo contra vulnerabilidades conhecidas. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Dispositivo safetynet**: Introduza o nível de [atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que têm de ser cumpridos. As opções são:
  - **Não configurado** (predefinição): Não é avaliada a definição de conformidade ou de não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

> [!NOTE]
> Em dispositivos Android Enterprise, **análise de ameaças nas aplicações** é uma política de configuração do dispositivo. Utilizar uma política de configuração, os administradores podem ativar a definição de um dispositivo. Veja [Definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Definições de propriedades do dispositivo

- **Versão mínima do SO**: Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para, em seguida, poder aceder aos recursos da empresa.
- **Versão do SO máxima**: Quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da empresa é bloqueado. Além disso, é pedido ao utilizador para contactar o administrador de TI. Até uma regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Esta definição é aplicada ao nível do dispositivo. Se só precisa de exigir uma palavra-passe no nível de perfil de trabalho, em seguida, utilize uma política de configuração. Ver [definições de configuração de dispositivos Android Enterprise](device-restrictions-android-for-work.md).
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres de que palavra-passe do utilizador tem de ter.
- **Tipo de palavra-passe obrigatório**: Escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e outros caracteres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos, numérico** (predefinição)
  - **Complexo numérico**
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe recentes que não podem ser reutilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo de**: Escolher **requerem** para encriptar o armazenamento de dados nos seus dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. 

  Não tem de configurar esta definição, porque os dispositivos empresariais Android impõem a encriptação.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: Optar por **bloco** dispositivos com o "Segurança > origens desconhecidas" ativada origens (suportadas no Android 4.0 – Android 7.x; não suportadas pelo Android 8.0 e posteriores). Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade. 

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

  Não tem de configurar esta definição como dispositivos Android Enterprise restringem sempre a instalação de origens desconhecidas.

- **Integridade de tempo de execução da aplicação do portal da empresa**: Escolher **requerem** para confirmar o Portal da empresa a aplicação cumpre os seguintes requisitos:

  - Tem o ambiente de tempo de execução predefinido instalado
  - Está corretamente assinada
  - Não está no modo de depuração
  - Foi instalada a partir de uma origem conhecida

  Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

- **Depuração de USB de bloco no dispositivo**: Escolher **bloco** para impedir que os dispositivos a utilizar a funcionalidade de depuração de USB. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Não tem de configurar esta definição, porque a depuração USB já se encontra desativada em dispositivos Android Enterprise.

- **Nível de patch de segurança mínimo**: Selecione o nível de patch de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato *AAAA-MM-DD*.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).
- [Monitorizar as suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte a [definições de política de conformidade para Android](compliance-policy-create-android.md) dispositivos.
