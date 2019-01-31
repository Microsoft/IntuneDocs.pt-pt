---
title: Configurar a inscrição no Intune para dispositivos Android enterprise dedicado
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android enterprise dedicado no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b3ced7e52de05e98c2f4a7ec9a828972ab60cf71
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290728"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Configurar a inscrição do Intune de dispositivos empresariais Android dedicado

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android suporta dispositivos de local público-estilo de empresa e de utilização única, com o respetivo conjunto de solução de dispositivos dedicados. Estes dispositivos são utilizados para um único objetivo, como sinalética digital, impressão de bilhetes, gestão de inventário, entre outros. Os administradores bloqueiam a utilização de um conjunto limitado de aplicações e ligações Web num dispositivo. Além disso, também impede os utilizadores de adicionarem outras aplicações ou de efetuarem outras ações no dispositivo.

O Intune ajuda-o a implementar aplicações e definições para dispositivos Android de dedicado. Para obter detalhes específicos sobre o Android Enterprise, veja [Android enterprise requirements (Requisitos empresariais do Android)](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Os dispositivos que gerir desta forma são inscritos no Intune sem uma conta de utilizador e não estão associados a nenhum utilizador final. Estes dispositivos não são para utilização pessoal nem para aplicações que tenham um requisito forte para dados de conta específicos do utilizador, como o Outlook ou o Gmail.

## <a name="device-requirements"></a>Requisitos de dispositivos

Dispositivos têm de cumprir estes requisitos para ser gerido como um dispositivo de dedicado do Android enterprise:

- Versão do SO Android 5.1 e posterior.
- Os dispositivos têm de executar uma distribuição do Android com conectividade aos GMS (Serviços Google Mobile). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

## <a name="set-up-android-dedicated-device-management"></a>Configurar a gestão de dispositivos dedicados Android

Para configurar a gestão de dispositivos Android de dedicado, siga estes passos:

1. Para se preparar para gerir dispositivos móveis, tem de [definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**](mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
3. [Crie um perfil de inscrição](#create-an-enrollment-profile).
4. [Crie um grupo de dispositivos](#create-a-device-group).
5. [Inscrever os dispositivos dedicados](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Criar um perfil de inscrição

Tem de criar um perfil de inscrição, de modo a que pode inscrever os seus dispositivos dedicados. Depois de criar o perfil, o mesmo fornece-lhe um token de inscrição (cadeia aleatória) e um código QR. Consoante o SO Android e a versão do dispositivo, pode utilizar o token ou código QR para [inscrever o dispositivo dedicado](#enroll-the-dedicated-devices).

1. Aceda ao [Portal do Intune](https://portal.azure.com) e selecione **Inscrição de dispositivos** > **Inscrição Android** > **Inscrição de quiosque e dispositivos de tarefas**.
2. Selecione **Criar** e preencha os campos obrigatórios.
    - **Nome**: Escreva um nome que irá utilizar quando o perfil a atribuir ao grupo de dispositivos dinâmicos.
    - **Data de expiração do token**: A data em que o token expira. A Google impõe um máximo de 90 dias.
3. Escolha **Criar** para guardar o perfil.

### <a name="create-a-device-group"></a>Criar um grupo de dispositivos

Pode direcionar aplicações e políticas para grupos de dispositivos dinâmicos ou atribuídos. Pode configurar grupos de dispositivos do AAD dinâmicos para povoar automaticamente os dispositivos inscritos com um perfil de inscrição específico ao seguir estes passos:

1. Aceda ao [Portal do Intune](https://portal.azure.com) e selecione **Grupos** > **Todos os grupos** > **Novo grupo**.
2. No painel **Grupo**, preencha os campos obrigatórios da seguinte forma:
    - **Tipo de grupo**: Segurança
    - **Nome do grupo**: Escreva um nome intuitivo (como dispositivos de 1 de fábrica)
    - **Tipo de associação**: Dispositivo dinâmico
3. Selecione **Adicionar consulta dinâmica**.
4. No painel **Regras de associação de grupo dinâmica**, preencha os campos da seguinte forma:
    - **Adicionar regra de associação dinâmica**: Regra simples
    - **Adicionar dispositivos onde**: enrollmentProfileName
    - Na caixa do meio, selecione **Correspondência**.
    - No último campo, introduza o nome do perfil de inscrição que criou anteriormente.
    Para obter mais informações sobre regras de associação dinâmica, veja [Regras de associação dinâmica para grupos no AAD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Selecione **Adicionar consulta** > **Criar**.

### <a name="replace-or-remove-tokens"></a>Substituir ou remover tokens

Pode substituir ou remover tokens e códigos QR.

- **Substituir token**: Pode gerar um novo código token/QR quando um está prestes a expirar, utilizando substituir Token.
- **Revogar token**: O código token/QR imediatamente pode expirar. Quando o fizer, o token/código QR deixa de ser utilizável. Pode utilizar esta opção se:
    - partilhar acidentalmente o token/código QR com um terceiro não autorizado
    - concluir todas as inscrições e deixar de precisar do token/código QR

Substituir ou revogar um token/código QR não terá efeito em dispositivos que já tenham sido inscritos.

1. Aceda ao [Portal do Intune](https://portal.azure.com) e selecione **Inscrição de dispositivos** > **Inscrição Android** > **Inscrição de quiosque e dispositivos de tarefas**.
2. Selecione o perfil com o qual pretende trabalhar.
3. Selecione **Token**.
4. Para substituir o token, selecione **Substituir token**.
5. Para revogar o token, selecione **Revogar token**.

## <a name="enroll-the-dedicated-devices"></a>Inscrever os dispositivos dedicados

Agora, pode [inscrever os dispositivos dedicados](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-dedicated-devices"></a>Gestão de aplicações em dispositivos Android de dedicado

Apenas as aplicações que têm o tipo de atribuição [definido em necessário](apps-deploy.md#assign-an-app) pode ser instalado em dispositivos Android de dedicado. As aplicações são instaladas a partir da Google Play Store Gerida da mesma forma que os dispositivos com perfil de trabalho do Android.

As aplicações são atualizadas automaticamente em dispositivos geridos quando o programador da aplicação publica uma atualização na Google Play Store.

Para remover uma aplicação do Android dispositivos dedicados, pode efetuar um dos seguintes procedimentos:
-   Elimine a implementação da aplicação obrigatória.
-   Crie uma implementação de desinstalação para a aplicação.

## <a name="next-steps"></a>Passos Seguintes
- [Implementar aplicações Android](apps-deploy.md)
- [Adicionar políticas de configuração para Android](device-profiles.md)
