---
title: Como integrar o Windows Hello para Empresas com o Microsoft Intune
titleSuffix: 
description: "Saiba como criar uma política para controlar a utilização do Windows Hello para Empresas em dispositivos geridos.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46bb82fd49fa58e87c22c8bf0abb57e1587b8b40
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Integrar o Windows Hello para Empresas com o Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode integrar o Microsoft Hello para Empresas (anteriormente conhecido como Microsoft Passport for Work) com o Microsoft Intune.

 O Hello para Empresas é um método de início de sessão alternativo que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual. Pode utilizar um *gesto de utilizador* para iniciar sessão, em vez de uma palavra-passe. Um gesto de utilizador pode ser um PIN simples, uma autenticação biométrica, como o Windows Hello, ou um dispositivo externo, como um leitor de impressões digitais.

O Intune integra o Hello para Empresas de duas formas:

-   Pode utilizar uma política do Intune para controlar os gestos que os utilizadores podem e não podem utilizar para iniciar sessão.

<!--- -   You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Nas versões do Windows 10 para computadores e dispositivos móveis antes da Atualização de Aniversário, podia definir dois PINs diferentes que podiam ser utilizados para autenticar recursos:
- O **PIN do dispositivo** podia ser utilizado para desbloquear o dispositivo e estabelecer ligação a recursos na cloud.
- O **PIN de trabalho** foi utilizado para aceder aos recursos do Azure AD nos dispositivos pessoais do utilizador (BYOD).

>Na Atualização de Aniversário, estes dois PINs foram unidos num único PIN do dispositivo.
Agora, tanto as políticas de configuração do Intune que definiu para controlar o PIN do dispositivo, e adicionalmente, quaisquer políticas do Windows Hello para Empresas que tenha configurado, definem este novo valor PIN.
Se tiver definido ambos os tipos de política para controlar o PIN, a política do Windows Hello para Empresas será aplicada tanto em computadores como em dispositivos móveis com Windows 10.
Para garantir que os conflitos de políticas são resolvidos e que a política de PIN é aplicada corretamente, atualize a sua Política do Windows Hello para Empresas para corresponder às definições na sua política de configuração e peça aos seus utilizadores para sincronizarem os seus dispositivos na aplicação Portal da Empresa.



## <a name="create-a-windows-hello-for-business-policy"></a>Criar uma política do Windows Hello para Empresas

1.  No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2.  Na página Intune, selecione **Inscrição de dispositivos** e, em seguida, selecione **Inscrição no Windows** > **Windows Hello para Empresas**.

3.  Na página que é aberta, selecione **Predefinição**.

4.  Na página **Todos os Utilizadores**, clique em **Propriedades** e, em seguida, introduza um **Nome** e uma **Descrição** opcional para as definições do Windows Hello para Empresas.

5. Na página **Todos os Utilizadores**, clique em **Definições** e, em seguida, escolha entre as seguintes opções para **Configurar o Windows Hello para Empresas**:

    - **Desativado**. Se não pretender utilizar o Windows Hello para Empresas, selecione esta definição. Todas as outras definições no ecrã não estão disponíveis.
    - **Ativado**. Selecione esta definição se pretender configurar as definições do Windows Hello para Empresas.
    - **Não configurado**. Selecione esta definição se não pretender utilizar o Intune para controlar as definições do Windows Hello para Empresas. Nenhuma das definições do Windows Hello para Empresas existentes em dispositivos Windows 10 será alterada. Todas as outras definições na página não estão disponíveis.

6.  Se tiver selecionado **Ativado** no passo anterior, configure as definições obrigatórias que são aplicadas a todos os dispositivos Windows 10 e Windows 10 Mobile inscritos.

 - **Utilizar um Trusted Platform Module (TPM)**. Um chip TPM fornece uma camada adicional de segurança de dados.<br>Escolha um dos seguintes valores:

     - **Obrigatório** (predefinição). Apenas os dispositivos com um TPM acessível podem aprovisionar o Windows Hello para Empresas.
     - **Preferencial**. Os dispositivos tentam utilizar primeiro um TPM. Se não estiver disponível, podem utilizar a encriptação de software.

 - **Pedir comprimento mínimo do PIN**/**Pedir comprimento máximo do PIN**. Configura os dispositivos para utilizar os comprimentos mínimo e máximo do PIN que especificar para ajudar a garantir o início de sessão seguro. O comprimento predefinido do PIN é de seis carateres, mas pode impor um comprimento mínimo de quatro carateres. O comprimento máximo do PIN é de 127 carateres.

 - **Pedir letras minúsculas no PIN**/**Pedir letras maiúsculas no PIN**/**Pedir carateres especiais no PIN**. Pode impor um PIN mais forte ao exigir a utilização de letras maiúsculas, letras minúsculas e carateres especiais no PIN. Escolha entre:

     - **Permitido**. Os utilizadores podem utilizar o tipo de caráter no PIN, mas não é obrigatório.

     - **Necessário**. Os utilizadores têm de incluir, pelo menos, um dos tipos de caráter no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

     - **Não permitido** (predefinição). Os utilizadores não devem utilizar estes tipos de carateres no seu PIN. (Este também será o comportamento se a definição não estiver configurada.)<br>Os carateres especiais incluem: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

 - **Expiração do PIN (dias)**. É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. A predefinição é de 41 dias.

 - **Memorizar histórico do PIN**. Restringe a reutilização de PINs utilizados anteriormente. Por predefinição, os últimos 5 PINs não podem ser reutilizados.

 - **Permitir autenticação biométrica**. Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Windows Hello para Empresas. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:

     - **Sim**. O Windows Hello para Empresas permite a autenticação biométrica.
     - **Não**. O Windows Hello para Empresas impede a autenticação biométrica (para todos os tipos de conta).

 - **Utilizar anti-spoofing avançado, quando disponível**. Configura se as funcionalidades de anti-spoofing do Windows Hello são utilizadas nos dispositivos que o suportam (por exemplo, detetar uma fotografia de um rosto em vez de um rosto real).<br>Se isto estiver definido como **Sim**, o Windows requer que todos os utilizadores utilizem anti-spoofing para funcionalidades faciais, quando suportado.

 - **Utilizar o início de sessão no telefone**. Se esta opção estiver definida como **Sim**, os utilizadores podem utilizar um passaporte remoto para servir de dispositivo complementar portátil para autenticação de computadores de secretária. O computador de secretária tem de estar associado ao Azure Active Directory e o dispositivo complementar tem de ser configurado com um PIN do Windows Hello para Empresas.

## <a name="windows-holographic-for-business-support"></a>Suporte do Windows Holographic for Business

O Windows Holographic for Business suporta as seguintes definições do Windows Hello para Empresas:

- Utilizar um Trusted Platform Module (TPM)
- Comprimento mínimo do PIN
- Comprimento máximo do PIN
- Letras em minúsculas no PIN
- Letras em maiúsculas no PIN
- Carateres especiais no PIN
- Expiração do PIN (dias)
- Memorizar histórico de PIN

## <a name="further-information"></a>Informações adicionais
Para obter mais informações sobre o Microsoft Passport, veja [o guia](https://technet.microsoft.com/library/mt589441.aspx) na documentação do Windows 10.
