---
title: "Controlar as definições do Microsoft Passport em dispositivos | Microsoft Intune"
description: "Saiba de que forma é que o Intune se integra com o Microsoft Passport for Work, que é um método de início de sessão alternativo que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 822264b7af87c0241e1d345544b8e9892f9e8c51
ms.openlocfilehash: c05929f3c4032bf8e252f4b2087b23dfdecf846b


---

# Controlar as definições do Microsoft Passport em dispositivos com o Microsoft Intune
O Microsoft Intune integra-se com o Microsoft Passport for Work, que é um método de início de sessão alternativo que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual.

Com o Passport, pode utilizar um *gesto de utilizador* para iniciar sessão, em vez de uma palavra-passe. Um gesto de utilizador pode ser um PIN simples, uma autenticação biométrica, como o Windows Hello, ou um dispositivo externo, como um leitor de impressões digitais.

>[!TIP]
>O Microsoft Passport for Work é agora conhecido como Windows Hello para Empresas. A consola do Intune ainda não reflete esta alteração.

O Intune integra-se com o Passport for Work de duas formas:

-   Pode utilizar uma política do Intune para controlar os gestos que os utilizadores podem e não podem utilizar para iniciar sessão.

-   Pode armazenar certificados de autenticação no fornecedor de armazenamento de chaves (KSP) do Passport for Work. Para mais informações, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md).

## Criar um Passport para a Política de trabalho

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Admin** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows** &gt; **Passport for Work** para abrir a página do Passport for Work.

    ![Página do Passport for Work](../media/passport.png)

2.  Escolha uma das seguintes definições:
    - **Desativar o Passport for Work nos dispositivos inscritos**. Se não pretender utilizar o Passport for Work em dispositivos Windows 10, selecione esta definição. Todas as outras definições no ecrã não estão disponíveis.
    - **Ativar o Passport for Work nos dispositivos inscritos**. Selecione esta definição se pretender configurar definições do Passport for Work em todos os dispositivos Windows 10.
    - **Não configurado**. Selecione esta definição se não pretender utilizar o Intune para controlar as definições do Passport for Work. Todas as definições do Passport for Work existentes em dispositivos Windows 10 não serão alteradas. Todas as outras definições no ecrã não estão disponíveis.
3.  Se tiver selecionado **Ativar Passport for Work em dispositivos inscritos**, configure as definições necessárias que serão aplicadas a todos os dispositivos Windows 10 e Windows 10 Mobile inscritos.
4.  Quando terminar, escolha **Guardar**.

## Passport for Work: definições de PIN


- **Pedir comprimento mínimo do PIN**/**Pedir comprimento máximo do PIN**. Configura os dispositivos para utilizar os comprimentos mínimo e máximo do PIN que especificar para ajudar a garantir o início de sessão seguro. O comprimento predefinido do PIN é de 6 carateres, mas pode impor um comprimento mínimo de 4 carateres. O comprimento máximo do PIN é de 127 carateres.
- **Pedir letras minúsculas no PIN**/**Pedir letras maiúsculas no PIN**/**Pedir carateres especiais no PIN**. Pode impor um PIN mais forte ao exigir a utilização de letras maiúsculas, letras minúsculas e carateres especiais no PIN. Escolha entre:
    - **Permitido**. Os utilizadores podem utilizar o tipo de caráter no PIN, mas não é obrigatório.
    - **Necessário**. Os utilizadores têm de incluir, pelo menos, um dos tipos de caráter no PIN. Por exemplo, é prática comum exigir pelo menos uma letra maiúscula e um caráter especial.
    - **Não permitido** (predefinição). Os utilizadores não devem utilizar estes tipos de carateres no seu PIN. (Este também será o comportamento se a definição não estiver configurada.)
    > [!TIP]
    > Os carateres especiais incluem: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **Expiração do PIN (dias)**. É recomendável especificar um período de expiração para um PIN, após o qual os utilizadores têm de alterá-lo. A predefinição é de 41 dias.
- **Memorizar histórico do PIN**. Restringe a reutilização de PINs utilizados anteriormente. Por predefinição, os últimos 5 PINs não podem ser reutilizados.


## Passport for Work: outras definições

- **Utilizar um Trusted Platform Module (TPM)**. Um chip TPM fornece uma camada adicional de segurança de dados.<br>Escolha um dos seguintes valores:
    - **Obrigatório** (predefinição). Apenas os dispositivos com um TPM acessível podem aprovisionar o Passport for Work.
    - **Preferencial**. Os dispositivos tentam utilizar primeiro um TPM. Se não estiver disponível, podem utilizar a encriptação de software.
- **Permitir autenticação biométrica**. Permite a autenticação biométrica, como reconhecimento facial ou impressão digital, como alternativa a um PIN, no Passport for Work. Os utilizadores continuam a ter de configurar um PIN, para a eventualidade de a autenticação biométrica falhar. Escolha entre:
    - **Sim**. O Passport for Work permite a autenticação biométrica.
    - **Não**. O Passport for Work impede a autenticação biométrica (para todos os tipos de conta).
- **Utilizar anti-spoofing avançado, quando disponível**. Configura se as funcionalidades de anti-spoofing do Windows Hello são utilizadas nos dispositivos que o suportam (por exemplo, detetar uma fotografia de um rosto em vez de um rosto real).<br>Se isto estiver definido como **Sim**, o Windows requer que todos os utilizadores utilizem anti-spoofing para funcionalidades faciais, quando suportado.
- **Utilizar Passaporte Remoto**. Se esta opção estiver definida como **Sim**, os utilizadores podem utilizar um passaporte remoto para servir de dispositivo complementar portátil para autenticação de computadores de secretária. O computador de secretária tem de estar associado ao Azure Active Directory e o dispositivo complementar tem de ser configurado com um PIN do Passport for Work.

## Informações adicionais
Para obter mais informações sobre o Microsoft Passport, consulte [o guia](https://technet.microsoft.com/library/mt589441.aspx) na documentação do Windows 10.



<!--HONumber=Aug16_HO1-->


