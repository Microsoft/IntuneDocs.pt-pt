---
title: Integrar o Windows Hello para Empresas com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba como criar uma política para controlar a utilização do Windows Hello para Empresas em dispositivos geridos."
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 7ce6def40c6c0fff3a28f884c458220283979234
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465769"
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Integrar o Windows Hello para Empresas com o Microsoft Intune  

Pode integrar o Microsoft Hello para Empresas (anteriormente conhecido como Microsoft Passport for Work) com o Microsoft Intune.

 O Hello para Empresas é um método de início de sessão alternativo que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual. Pode utilizar um *gesto de utilizador* para iniciar sessão, em vez de uma palavra-passe. A user gesture might be a PIN, biometric authentication such as Windows Hello, or an external device such as a fingerprint reader.

O Intune integra o Hello para Empresas de duas formas:

- Pode ser criada uma política do Intune em **Inscrição de dispositivos**. Esta política destina-se a toda a organização (ao nível dos inquilinos). Suporta a experiência de configuração inicial (OOBE) do Windows AutoPilot e é aplicada quando um dispositivo é inscrito. 
- Pode ser criado um perfil de proteção de identidade em **Configuração do dispositivo**. Este perfil destina-se aos utilizadores e dispositivos atribuídos e é aplicado durante a entrada. 

Utilize este artigo para criar uma política do Windows Hello para Empresas predefinida destinada a toda a organização. Para criar um perfil de proteção de identidade utilizado para selecionar grupos de utilizadores e dispositivos, veja [Configurar um perfil de proteção de identidade](identity-protection-configure.md).  

<!--- - You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Nas versões do Windows 10 para computadores e dispositivos móveis antes da Atualização de Aniversário, podia definir dois PINs diferentes que podiam ser utilizados para autenticar recursos:
> - O **PIN do dispositivo** podia ser utilizado para desbloquear o dispositivo e estabelecer ligação a recursos na cloud.
> - O **PIN de trabalho** foi utilizado para aceder aos recursos do Azure AD nos dispositivos pessoais do utilizador (BYOD).
> 
> Na Atualização de Aniversário, estes dois PINs foram unidos num único PIN do dispositivo.
> Agora, tanto as políticas de configuração do Intune que definiu para controlar o PIN do dispositivo, e adicionalmente, quaisquer políticas do Windows Hello para Empresas que tenha configurado, definem este novo valor PIN.
> Se tiver definido ambos os tipos de política para controlar o PIN, a política do Windows Hello para Empresas será aplicada tanto em computadores como em dispositivos móveis com Windows 10.
> Para garantir que os conflitos de políticas são resolvidos e que a política de PIN é aplicada corretamente, atualize a sua Política do Windows Hello para Empresas para corresponder às definições na sua política de configuração e peça aos seus utilizadores para sincronizarem os seus dispositivos na aplicação Portal da Empresa.



## <a name="create-a-windows-hello-for-business-policy"></a>Criar uma política do Windows Hello para Empresas

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431.

2. Go to **Devices** >  enrollment** > **Enroll devices** > **Windows enrollment** > **Windows Hello for Business**. The Windows Hello for Business pane opens.

3. Select from the following options for **Configure Windows Hello for Business**:

    - **Desativado**. Se não pretender utilizar o Windows Hello para Empresas, selecione esta definição. If disabled, users can't provision Windows Hello for Business except on Azure Active Directory joined mobile phones where provisioning may be required.
    - **Ativado**. Selecione esta definição se pretender configurar as definições do Windows Hello para Empresas.  When you select *Enabled*, additional settings for WIndows Hello become visible.
    - **Não configurado**. Selecione esta definição se não pretender utilizar o Intune para controlar as definições do Windows Hello para Empresas. Any existing Windows Hello for Business settings on Windows 10 devices isn't changed. Todas as outras definições no painel não estão disponíveis.

4. Se tiver selecionado **Ativado** no passo anterior, configure as definições obrigatórias que são aplicadas a todos os dispositivos Windows 10 e Windows 10 Mobile inscritos. After  you configure these settings, select **Save**.

   - **Use a Trusted Platform Module (TPM)** :

     Um chip TPM fornece uma camada adicional de segurança de dados. Escolha um dos seguintes valores:

     - **Obrigatório** (predefinição). Apenas os dispositivos com um TPM acessível podem aprovisionar o Windows Hello para Empresas.
     - **Preferencial**. Os dispositivos tentam utilizar primeiro um TPM. If this option isn't available, they can use software encryption.

   - **Minimum PIN length** and **Maximum PIN length**:

     Configura os dispositivos para utilizar os comprimentos mínimo e máximo do PIN que especificar para ajudar a garantir o início de sessão seguro. O comprimento predefinido do PIN é de seis carateres, mas pode impor um comprimento mínimo de quatro carateres. O comprimento máximo do PIN é de 127 carateres.

   - **Lowercase letters in PIN**, **Uppercase letters in PIN**, and **Special characters in PIN**.

     Pode impor um PIN mais forte ao exigir a utilização de letras maiúsculas, letras minúsculas e carateres especiais no PIN. For each, select from:

     - **Permitido**. Users can use the character type in their PIN, but it isn't mandatory.

     - **Necessário**. Os utilizadores têm de incluir, pelo menos, um dos tipos de caráter no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

     - **Não permitido** (predefinição). Os utilizadores não devem utilizar estes tipos de carateres no seu PIN. (This is also the behavior if the setting isn't configured.)

       Os carateres especiais incluem: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN expiration (days)** :

     É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. A predefinição é de 41 dias.

   - **Remember PIN history**:

     Restringe a reutilização de PINs utilizados anteriormente. By default, the last 5 PINs can't be reused.

   - **Allow biometric authentication**:

     Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Windows Hello para Empresas. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:

     - **Sim**. O Windows Hello para Empresas permite a autenticação biométrica.
     - **Não**. O Windows Hello para Empresas impede a autenticação biométrica (para todos os tipos de conta).

   - **Use enhanced anti-spoofing, when available**:

     Configures whether the anti-spoofing features of Windows Hello are used on devices that support it. For example, detecting a photograph of a face instead of a real face.

     When set to **Yes**, Windows requires all users to use anti-spoofing for facial features when that is supported.

   - **Allow phone sign-in**:

     Se esta opção estiver definida como **Sim**, os utilizadores podem utilizar um passaporte remoto para servir de dispositivo complementar portátil para autenticação de computadores de secretária. O computador de secretária tem de estar associado ao Azure Active Directory e o dispositivo complementar tem de ser configurado com um PIN do Windows Hello para Empresas.

## <a name="windows-holographic-for-business-support"></a>Suporte do Windows Holographic for Business

Windows Holographic for Business supports the following settings for Windows Hello for Business:

- Utilizar um Trusted Platform Module (TPM)
- Comprimento mínimo do PIN
- Comprimento máximo do PIN
- Letras em minúsculas no PIN
- Letras em maiúsculas no PIN
- Carateres especiais no PIN
- Expiração do PIN (dias)
- Memorizar histórico de PIN

## <a name="next-steps"></a>Próximos passos

For more information about Windows Hello for Business, see [the guide](https://technet.microsoft.com/library/mt589441.aspx) in the Windows 10 documentation.
