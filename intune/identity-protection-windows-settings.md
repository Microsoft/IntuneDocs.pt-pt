---
title: Windows Hello para empresas no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todos os PIN, biométrica e antisspoofing configurações num perfil de proteção de identidade para utilizar e configurar o Windows Hello para empresas em dispositivos Windows 10 no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5eb4097ab2bedf032270b1d4230d81f7b326fbf1
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228583"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Definições de dispositivo 10 (e versões posteriores) do Windows para ativar o Windows Hello para empresas no Intune

Este artigo apresenta e descreve o Windows Hello para empresas que pode controlar em dispositivos Windows 10 no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para utilizar um PIN ou impressão digital para iniciar sessão e muito mais.

Enquanto administrador do Intune, pode criar e atribuir estas definições para Windows 10 e dispositivos posteriores.

Para saber mais sobre o Windows Hello para perfis de empresas no Intune, consulte [configurar a proteção de identidade](identity-protection-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas

- **Configurar o Windows Hello para empresas**: Para utilizar esta funcionalidade e configurar as definições, escolha **ativar**.
- **Comprimento mínimo do PIN**: Introduza o comprimento mínimo do PIN, que deseja permitir nos dispositivos. O comprimento do PIN predefinido é seis carateres. O comprimento mínimo do PIN é de quatro (4) carateres.
- **Comprimento máximo do PIN**: Introduza o comprimento máximo do PIN, que deseja permitir nos dispositivos. O comprimento predefinido do PIN é de seis (6) carateres. O comprimento máximo do PIN é de 127 carateres.  
- **Letras minúsculas no PIN**: Pode impor um PIN mais forte ao exigir que os utilizadores finais incluir letras minúsculas. As opções são:

  - **Não permitido** (predefinição): Impedir que os utilizadores da utilização de letras em minúsculas no PIN. Este comportamento ocorre também se a definição não está configurada.
  - **Permitido**: Permitir aos utilizadores utilizar letras minúsculas no PIN, mas não seja necessário.
  - **Necessário**: Os utilizadores têm de incluir pelo menos uma letra em minúsculas no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

- **Letras maiúsculas no PIN**: Pode impor um PIN mais forte ao exigir que os utilizadores finais incluem letras maiúsculas. As opções são:

  - **Não permitido** (predefinição): Impedir que os utilizadores da utilização de letras maiúsculas no PIN. Este comportamento ocorre também se a definição não está configurada.
  - **Permitido**: Permitir aos utilizadores utilizar letras maiúsculas no PIN, mas não seja necessário.
  - **Necessário**: Os utilizadores têm de incluir, pelo menos, uma letra em maiúsculas no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

- **Carateres especiais no PIN**: Pode impor um PIN mais forte ao exigir que os utilizadores finais incluir caracteres especiais. As opções são:

  - **Não permitido** (predefinição): Impedir que os utilizadores com carateres especiais no PIN. Este comportamento ocorre também se a definição não está configurada.
    Carateres especiais incluem: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Permitido**: Permitir aos utilizadores utilizar letras maiúsculas no PIN, mas não seja necessário.
  - **Necessário**: Os utilizadores têm de incluir, pelo menos, uma letra em maiúsculas no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

- **Expiração do PIN (dias)**: É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. A predefinição é de 41 dias.

- **Memorizar histórico de PINS**: Restringe a reutilização de PINs utilizados anteriormente. Por predefinição, os últimos 5 PINs não podem ser reutilizados.  
- **Ativar a recuperação PIN**: Permite ao utilizador de alterar o PIN ao utilizar o Windows Hello para o serviço de recuperação de PIN de negócios.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Utilizar um Trusted Platform Module (TPM)**: Um chip TPM fornece uma camada adicional de segurança de dados. Escolha um dos seguintes valores:  
  - **Ativar**: Apenas os dispositivos com um TPM acessível podem aprovisionar o Windows Hello para Empresas.
  - **Não configurado**: Todos os dispositivos podem aprovisionar o Windows Hello para Empresas, mesmo quando não houver nenhum TPM utilizável. Os dispositivos começarão por tentar utilizar um TPM, mas se este estiver indisponível, os dispositivos podem utilizar a encriptação de software.  

- **Permitir autenticação biométrica**: Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Windows Hello para Empresas. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:

  - **Ativar**: O Windows Hello para Empresas permite a autenticação biométrica.
  - **Não configurado** (predefinição): O Windows Hello para Empresas impede a autenticação biométrica (para todos os tipos de conta).

- **Utilizar anti-spoofing avançado, quando disponível**: Escolha se antisspoofing funcionalidades do Windows Hello são utilizadas nos dispositivos que o suportam. Por exemplo, detete uma fotografia de um rosto em vez de um rosto real.

  - **Ativar**: O Windows requer que todos os utilizadores utilizem anti-spoofing para funcionalidades faciais, quando tal for suportado.  
  - **Não configurado** (predefinição): O Windows respeita as configurações anti-spoofing do dispositivo.

- **Certificado para recursos no local**: 

  - **Ativar**: Permite que o Windows Hello para Empresas utilize certificados para autenticar recursos no local.
  - **Não configurado** (predefinição): Impede que o Windows Hello para Empresas utilize certificados para autenticar recursos no local.  

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
