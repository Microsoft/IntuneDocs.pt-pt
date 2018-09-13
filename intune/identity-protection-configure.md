---
title: Configurar definições de proteção de identidade no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar um perfil de dispositivo para configurar as definições do Windows Hello para Empresas em dispositivos com o Windows 10 no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7012479023ece83ef475431c5cefe150ab2ef342
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317996"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Configurar definições de proteção de identidade no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Os perfis de proteção de identidade controlam a forma como o Windows Hello para Empresas é aprovisionado e configurado em dispositivos com o Windows 10 geridos. Crie este perfil para configurar:  
* A disponibilidade do Windows Hello para Empresas para dispositivos e utilizadores.
* Os requisitos de PIN do dispositivo.
* Os gestos que os utilizadores podem e não podem utilizar para iniciar sessão nos respetivos dispositivos.  

 Pode atribuir este perfil a grupos de utilizadores e dispositivos específicos ou a todos os utilizadores e todos os dispositivos. Os grupos recebem o perfil de proteção de identidade quando dão entrada no Intune.    

Utilize as informações que constam neste artigo para criar um perfil de proteção de identidade. Em seguida, [atribua o seu perfil](device-profile-assign.md) a grupos de utilizadores e dispositivos.

Esta funcionalidade aplica-se a dispositivos que executem:  
- Windows 10 e posterior
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de identidade

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de identidade.
5. Na lista pendente **Plataforma**, selecione **Windows 10 e posterior**. O Windows Hello para Empresas só é suportado em dispositivos com o Windows 10 e versões posteriores.
6. Na lista pendente **Tipo de perfil**, selecione **Identity protection**.
7. No painel Windows Hello para Empresas, selecione uma das seguintes opções para Configurar o Windows Hello para Empresas:
    * Desativado. Se não pretender utilizar o Windows Hello para Empresas, selecione esta definição. Todas as outras definições no ecrã não estão disponíveis.
    * Ativada. Selecione esta definição se pretender configurar as definições do Windows Hello para Empresas.  

8. Se tiver selecionado **Ativado** no passo anterior, configure as definições obrigatórias que são aplicadas aos utilizadores e dispositivos com Windows 10 e Windows 10 Mobile visados e inscritos.

> [!NOTE]
> Quando atribuir perfis de proteção de identidade apenas a utilizadores, o contexto do dispositivo assume a predefinição **Não configurado**.  

   - **Comprimento mínimo do PIN**/**Comprimento máximo do PIN**. Configura os dispositivos para utilizar os comprimentos mínimo e máximo do PIN que especificar para ajudar a garantir o início de sessão seguro. O comprimento predefinido do PIN é de seis carateres, mas pode impor um comprimento mínimo de quatro carateres. O comprimento máximo do PIN é de 127 carateres.  

   - **Letras minúsculas no PIN**/**Letras maiúsculas no PIN**/**Carateres especiais no PIN**. Pode impor um PIN mais forte ao exigir a utilização de letras maiúsculas, letras minúsculas e carateres especiais no PIN. Escolha entre:

     - **Permitido**. Os utilizadores podem utilizar o tipo de caráter no PIN, mas não é obrigatório.

     - **Necessário**. Os utilizadores têm de incluir, pelo menos, um dos tipos de caráter no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

     - **Não permitido** (predefinição). Os utilizadores não devem utilizar estes tipos de carateres no seu PIN. (Este comportamento também ocorre se a definição não estiver configurada.)<br>Os carateres especiais incluem: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **Expiração do PIN (dias)**. É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. A predefinição é de 41 dias.

   - **Memorizar histórico do PIN**. Restringe a reutilização de PINs utilizados anteriormente. Por predefinição, os últimos 5 PINs não podem ser reutilizados.  
   - **Ativar a recuperação de PIN**: permite que o utilizador altere o respetivo PIN através do serviço de recuperação de PIN do Windows Hello para Empresas. 
       - **Ativar**. O serviço cloud encripta um segredo de recuperação de PIN que será armazenado no dispositivo. O utilizador pode alterar o PIN caso seja necessário.  
       - **Não configurado** (predefinição). Não é criado nem armazenado nenhum segredo de recuperação de PIN. Se o PIN do utilizador for esquecido, a única forma de obter um PIN novo é através da eliminação do PIN existente e da criação de um novo. O utilizador terá de voltar a registar-se com qualquer serviço ao qual o PIN antigo concedia acesso.  
   
   - **Utilizar um Trusted Platform Module (TPM)**. Um chip TPM fornece uma camada adicional de segurança de dados. Escolha um dos seguintes valores:  
     - **Ativar**. Apenas os dispositivos com um TPM acessível podem aprovisionar o Windows Hello para Empresas.
     - **Não configurado**. Todos os dispositivos podem aprovisionar o Windows Hello para Empresas, mesmo quando não houver nenhum TPM utilizável. Os dispositivos começarão por tentar utilizar um TPM, mas se este estiver indisponível, os dispositivos podem utilizar a encriptação de software.  

   - **Permitir autenticação biométrica**. Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Windows Hello para Empresas. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:

     - **Ativar**. O Windows Hello para Empresas permite a autenticação biométrica.
     - **Não configurado** (predefinição). O Windows Hello para Empresas impede a autenticação biométrica (para todos os tipos de conta).

   - **Utilizar anti-spoofing avançado, quando disponível**. Configura se as funcionalidades de anti-spoofing do Windows Hello são utilizadas nos dispositivos que o suportam (por exemplo, detetar uma fotografia de um rosto em vez de um rosto real).
       - **Ativar**. O Windows requer que todos os utilizadores utilizem anti-spoofing para funcionalidades faciais, quando tal for suportado.  
       - **Não configurado** (predefinição). O Windows respeita as configurações anti-spoofing do dispositivo.

   - **Certificado para os recursos no local**. 
       - **Ativar**. Permite que o Windows Hello para Empresas utilize certificados para autenticar recursos no local.
       - **Não configurado** (predefinição). Impede que o Windows Hello para Empresas utilize certificados para autenticar recursos no local.  
9. Clique em **OK** para guardar o seu perfil.  

O perfil é criado e apresentado na lista **Configuração do dispositivo – Perfis**. Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
