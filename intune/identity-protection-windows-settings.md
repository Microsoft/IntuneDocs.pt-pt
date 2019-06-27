---
title: Windows Hello para empresas no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todos os PIN, biométrica e antisspoofing configurações num perfil de proteção de identidade para utilizar e configurar o Windows Hello para empresas em dispositivos Windows 10 no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 1cbf45fc337cbe7d7a45081a3b9e05002ca126d8
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402929"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Definições do dispositivo Windows 10 para ativar o Windows Hello para empresas no Intune

Este artigo apresenta e descreve o Windows Hello para empresas que pode controlar em dispositivos Windows 10 no Intune. Enquanto administrador do Intune, pode configurar e atribuir estas definições para dispositivos Windows 10 como parte da sua solução de gestão (MDM) de dispositivos móveis. 

Pode encontrar informações adicionais sobre estas definições na [configurar o Windows Hello para definições de política de negócios](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings), na documentação Hello do Windows.


Para saber mais sobre o Windows Hello para perfis de empresas no Intune, consulte [configurar a proteção de identidade](identity-protection-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas
- **Configurar o Windows Hello para empresas**:
  - **Não configurado** -Selecione esta definição se não quiser utilizar o Intune para controlar Windows Hello para empresas. Nenhuma das definições do Windows Hello para Empresas existentes em dispositivos Windows 10 será alterada. Todas as outras definições no painel não estão disponíveis.

  - **Desativado** - se de que não pretende utilizar o Windows Hello para empresas, selecione esta definição. Todas as outras definições no ecrã não estão disponíveis.
  - **Ativado** -Selecione esta definição se quiser configurar o Windows Hello para empresas.  
  
  **Predefinido**: Não configurado

  Quando definido como *ativado*, estão disponíveis as seguintes definições:

    - **Comprimento mínimo do PIN**  
     Especifica um comprimento mínimo do PIN para dispositivos, para ajudar o início de sessão seguro. Padrões de dispositivo do Windows são seis carateres, mas esta definição pode impor um mínimo de quatro e 127 carateres. 
  
      **Predefinido**: *Não configurado*

    - **Comprimento máximo do PIN**  
    Especifica um comprimento máximo do PIN para dispositivos, para ajudar o início de sessão seguro. Padrões de dispositivo do Windows são seis carateres, mas esta definição pode impor um mínimo de quatro e 127 carateres.  

      **Predefinido**: *Não configurado*  

    - **Letras minúsculas no PIN**  
      Pode impor um PIN mais forte ao exigir que os utilizadores finais incluir letras minúsculas. As opções são:

      - **Não permitido** -bloquear os utilizadores de utilizarem letras minúsculas no PIN. Este comportamento ocorre também se a definição não está configurada.
      - **Permitido** - permitir aos utilizadores utilizar letras minúsculas no PIN, mas que não seja necessário.
      - **Necessário** -os utilizadores têm de incluir pelo menos uma letra em minúsculas no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

    - **Letras em maiúsculas no PIN**  
    Pode impor um PIN mais forte ao exigir que os utilizadores finais incluem letras maiúsculas. As opções são:

      - **Não permitido** -bloquear os utilizadores de utilizarem letras maiúsculas no PIN. Este comportamento ocorre também se a definição não está configurada.
      - **Permitido** - permitir aos utilizadores utilizar letras maiúsculas no PIN, mas que não seja necessário.
      - **Necessário** -os utilizadores têm de incluir, pelo menos, uma letra em maiúsculas no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

    - **Carateres especiais no PIN**  
    Pode impor um PIN mais forte ao exigir que os utilizadores finais incluir caracteres especiais. Carateres especiais incluem: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  
 
      As opções são:
      - **Não permitido** -impedir que os utilizadores com carateres especiais no PIN. Este comportamento ocorre também se a definição não está configurada.
      - **Permitido** - permitir aos utilizadores utilizar letras maiúsculas no PIN, mas que não seja necessário.
      - **Necessário** -os utilizadores têm de incluir, pelo menos, uma letra em maiúsculas no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

      **Predefinido**: Não permitido

  - **Expiração do PIN (dias)**  
      É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. Predefinições de dispositivo do Windows são 41 dias.

    **Predefinido**: Não Configurado

  - **Memorizar histórico de PINS**  
    Restringe a reutilização de PINs utilizados anteriormente. Padrão de dispositivos do Windows para impedir a reutilização dos últimos cinco PINs.  

    **Predefinido**: Não Configurado  

  - **Ativar a recuperação PIN**   
    Permite ao utilizador utilizar o Windows Hello para o serviço de recuperação de PIN de negócios. 
    
    - **Ativado** - segredo de recuperação do PIN é armazenada no dispositivo e o utilizador pode alterar o PIN, se necessário.  
    - **Desativado** -o segredo de recuperação não é criado ou armazenado.

    **Predefinido**: Não configurado

  - **Utilizar um Trusted Platform Module (TPM)**    
    Um chip TPM fornece uma camada adicional de segurança de dados.  

    - **Ativado** – apenas dispositivos com um TPM acessível podem aprovisionar o Windows Hello para empresas.
    - **Não configurado** -dispositivos tentam utilizar primeiro um TPM. Se não estiver disponível, podem utilizar a encriptação de software.
    
    **Predefinido**: Não configurado

  - **Permitir autenticação biométrica**  
     Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Windows Hello para Empresas. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:

    - **Ativar** -Windows Hello para empresas permite a autenticação biométrica.
    - **Não configurado** -Windows Hello para empresas impede a autenticação biométrica (para todos os tipos de conta).

    **Predefinido**: Não configurado

  - **Utilizar anti-spoofing avançado, quando disponível**  
    Configura se as funcionalidades de anti-spoofing do Windows Hello são utilizadas nos dispositivos que o suportam (por exemplo, detetar uma fotografia de um rosto em vez de um rosto real).  
    - **Ativar** -Windows requer que todos os utilizadores utilizem anti-spoofing para funcionalidades faciais, quando suportado.
    - **Não configurado** -Windows respeita as configurações antisspoofing no dispositivo.

    **Predefinido**: Não configurado

  - **Certificado para recursos no local**  

    - **Ativar** -permite Windows Hello para empresas utilizar certificados para se autenticar em recursos no local.
    - **Não configurado** -impede o Windows Hello para empresas da utilização de certificados para se autenticar em recursos no local. Em vez disso, os dispositivos utilizam o comportamento padrão do *confiança de chave de autenticação no local*. Para obter mais informações, consulte [certificado de utilizador para autenticação no local](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) na documentação Hello do Windows.  

  **Predefinido**: Não configurado

- **Utilizar chaves de segurança para o início de sessão**  
  Esta definição está disponível para dispositivos que executam o Windows 10 versão 1903 ou posterior. Usá-lo para gerir o suporte para utilizar chaves de segurança Windows Hello para iniciar sessão.  

  - **Ativado** -os utilizadores podem utilizar uma chave de Windows Hello segurança como uma credencial de início de sessão para PCs segmentados com esta política. 
  - **Desativada** - chaves de segurança estão desativadas e os utilizadores não é possível usá-los para iniciar sessão em PCs.   

  **Predefinido**: Não configurado

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
