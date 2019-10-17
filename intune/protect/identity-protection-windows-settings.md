---
title: Configurações do Windows Hello para empresas no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as configurações de PIN, biométrica e anti-falsificação em um perfil de proteção de identidade para usar e configurar o Windows Hello para empresas em dispositivos Windows 10 no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: f49ea9e1e59fadcb90a773e362ec3ef41e25ab63
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502237"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Configurações do dispositivo Windows 10 para habilitar o Windows Hello para empresas no Intune

Este artigo lista e descreve as configurações do Windows Hello para empresas que você pode controlar em dispositivos Windows 10 no Intune. Como administrador do Intune, você pode configurar e atribuir essas configurações a dispositivos Windows 10 como parte da sua solução de MDM (gerenciamento de dispositivo móvel). 

Você pode encontrar informações adicionais sobre essas configurações em [definir configurações de política do Windows Hello para empresas](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings), na documentação do Windows Hello.


Para saber mais sobre os perfis do Windows Hello para empresas no Intune, consulte [Configurar a proteção de identidade](identity-protection-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas
- **Configurar o Windows Hello para empresas**:
  - **Não configurado** – Selecione essa configuração se não quiser usar o Intune para controlar as configurações do Windows Hello para empresas. Nenhuma das definições do Windows Hello para Empresas existentes em dispositivos Windows 10 será alterada. Todas as outras definições no painel não estão disponíveis.

  - **Desabilitado** -se você não quiser usar o Windows Hello para empresas, selecione essa configuração. Todas as outras definições no ecrã não estão disponíveis.
  - **Habilitado** – Selecione essa configuração se desejar definir as configurações do Windows Hello para empresas.  
  
  **Padrão**: não configurado

  Quando definido como *habilitado*, as seguintes configurações estão disponíveis:

  - **Comprimento mínimo do PIN**  
    Especifique um comprimento mínimo de PIN para dispositivos, para ajudar a proteger a entrada. Os padrões de dispositivo do Windows têm seis caracteres, mas essa configuração pode impor um mínimo de quatro a 127 caracteres. 

    **Padrão**: *não configurado*

  - **Comprimento máximo do PIN**  
  Especifique um comprimento máximo de PIN para dispositivos, para ajudar a proteger a entrada. Os padrões de dispositivo do Windows têm seis caracteres, mas essa configuração pode impor um mínimo de quatro a 127 caracteres.  

    **Padrão**: *não configurado*  

  - **Letras minúsculas no PIN**  
    Você pode impor um PIN mais forte exigindo que os usuários finais incluam letras minúsculas. As opções são:

    - **Não permitido** – bloquear usuários de usar letras minúsculas no PIN. Esse comportamento também ocorrerá se a configuração não estiver configurada.
    - **Permitido** – permitir que os usuários usem letras minúsculas no PIN, mas isso não é necessário.
    - **Obrigatório** -os usuários devem incluir pelo menos uma letra minúscula no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

  - **Letras maiúsculas no PIN**  
    Você pode impor um PIN mais forte exigindo que os usuários finais incluam letras maiúsculas. As opções são:

    - **Não permitido** – bloquear usuários de usar letras maiúsculas no PIN. Esse comportamento também ocorrerá se a configuração não estiver configurada.
    - **Permitido** – permitir que os usuários usem letras maiúsculas no PIN, mas isso não é necessário.
    - **Obrigatório** -os usuários devem incluir pelo menos uma letra maiúscula no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

  - **Caracteres especiais no PIN**  
    Você pode impor um PIN mais forte exigindo que os usuários finais incluam caracteres especiais. Os caracteres especiais incluem: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  

    As opções são:
    - **Não permitido** – bloquear usuários de usar caracteres especiais no PIN. Esse comportamento também ocorrerá se a configuração não estiver configurada.
    - **Permitido** – permitir que os usuários usem letras maiúsculas no PIN, mas isso não é necessário.
    - **Obrigatório** -os usuários devem incluir pelo menos uma letra maiúscula no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.

    **Padrão**: não permitido

  - **Expiração do PIN (dias)**  
    É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. Os padrões de dispositivo do Windows são de 41 dias.

    **Padrão**: não configurado

  - **Lembrar histórico de PIN**  
    Restringe a reutilização de PINs utilizados anteriormente. Os dispositivos Windows são padrão para impedir a reutilização dos últimos cinco PINs.  

    **Padrão**: não configurado  

  - **Habilitar**@no__t de recuperação de PIN-1  
    Permite que o usuário use o serviço de recuperação de PIN do Windows Hello para empresas. 
    
    - **Habilitado** -o segredo de recuperação do PIN é armazenado no dispositivo e o usuário pode alterar seu PIN, se necessário.  
    - **Desabilitado** -o segredo de recuperação não é criado ou armazenado.

    **Padrão**: não configurado

  - **Usar um Trusted Platform Module (TPM)**    
    Um chip TPM fornece uma camada adicional de segurança de dados.  

    - **Habilitado** -somente dispositivos com um TPM acessível podem provisionar o Windows Hello para empresas.
    - **Não configurado** -os dispositivos primeiro tentam usar um TPM. Se não estiver disponível, podem utilizar a encriptação de software.
    
    **Padrão**: não configurado

  - **Permitir autenticação biométrica**  
     Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Windows Hello para Empresas. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:

    - **Habilitar** -o Windows Hello para empresas permite a autenticação biométrica.
    - **Não configurado** -o Windows Hello para empresas impede a autenticação biométrica (para todos os tipos de conta).

    **Padrão**: não configurado

  - **Usar antifalsificação avançada, quando disponível**  
    Configura se as funcionalidades de anti-spoofing do Windows Hello são utilizadas nos dispositivos que o suportam (por exemplo, detetar uma fotografia de um rosto em vez de um rosto real).  
    - **Habilitar** -o Windows exige que todos os usuários usem a antifalsificação para recursos faciais quando houver suporte.
    - **Não configurado** -o Windows honra as configurações anti-falsificação no dispositivo.

    **Padrão**: não configurado

  - **Certificado para recursos locais**  

    - **Habilitar** – permite que o Windows Hello para empresas Use certificados para autenticar para recursos locais.
    - **Não configurado** – impede que o Windows Hello para empresas Use certificados para autenticar para recursos locais. Em vez disso, os dispositivos usam o comportamento padrão de *autenticação de chave confiável no local*. Para obter mais informações, consulte [certificado de usuário para autenticação local](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) na documentação do Windows Hello.  

  **Padrão**: não configurado

- **Usar chaves de segurança para entrar**  
  Essa configuração está disponível para dispositivos que executam o Windows 10 versão 1903 ou posterior. Use-o para gerenciar o suporte ao uso de chaves de segurança do Windows Hello para entrada.  

  - **Habilitado** -os usuários podem usar uma chave de segurança do Windows Hello como uma credencial de logon para PCs com essa política. 
  - **Desabilitado** -as chaves de segurança estão desabilitadas e os usuários não podem usá-las para entrar em PCs.   

  **Padrão**: não configurado

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../configuration/device-profile-assign.md) e [monitorize o respetivo estado](../configuration/device-profile-monitor.md).
