---
title: Configurar a inscrição de dispositivos dedicados do Android Enterprise no Intune
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos dedicados do Android Enterprise no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e07952b6e7147ffa9b84cfbd1988ebb927b411dd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730072"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Configurar a inscrição de dispositivos dedicados do Android Enterprise no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Android Enterprise suporta dispositivos que são propriedade da empresa, de utilização única e de estilo de quiosque com o conjunto de soluções de dispositivos dedicados. Estes dispositivos são utilizados para um único objetivo, como sinalética digital, impressão de bilhetes, gestão de inventário, entre outros. Os administradores bloqueiam a utilização de um conjunto limitado de aplicações e ligações Web num dispositivo. Além disso, também impede os utilizadores de adicionarem outras aplicações ou de efetuarem outras ações no dispositivo.

O Intune ajuda-o a implementar aplicações e definições em dispositivos dedicados do Android Enterprise. Para obter detalhes específicos sobre o Android Enterprise, veja [Android enterprise requirements ](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisitos empresariais do Android).

Os dispositivos que gerir desta forma são inscritos no Intune sem uma conta de utilizador e não estão associados a nenhum utilizador final. Estes dispositivos não são para utilização pessoal nem para aplicações que tenham um requisito forte para dados de conta específicos do utilizador, como o Outlook ou o Gmail.

## <a name="device-requirements"></a>Requisitos dos dispositivos

Os dispositivos têm de cumprir estes requisitos para serem geridos como um dispositivo dedicado do Android Enterprise:

- Versão do SO Android 5.1 e posterior.
- Os dispositivos têm de executar uma distribuição do Android com conectividade aos GMS (Serviços Google Mobile). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Configurar a gestão dos dispositivos dedicados do Android Enterprise

Para configurar a gestão dos dispositivos dedicados do Android Enterprise, siga estes passos:

1. Para se preparar para gerir dispositivos móveis, tem de [definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**](../fundamentals/mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. [Ligue a conta do inquilino do Intune à conta do Managed Google Play ](connect-intune-android-enterprise.md).
3. [Crie um perfil de inscrição](#create-an-enrollment-profile).
4. [Crie um grupo de dispositivos](#create-a-device-group).
5. [Inscreva os dispositivos dedicados](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Criar um perfil de inscrição

> [!NOTE]
> Se um token tiver expirado, o perfil associado a ele não será exibido no **registro** > do dispositivo registro do**Android** > **dispositivos dedicados de propriedade corporativa**. Para ver todos os perfis associados a tokens ativos e inativos, clique em **Filtrar** e marque as caixas dos Estados de política "ativo" e "inativo". 

Tem de criar um perfil de inscrição para poder inscrever os dispositivos dedicados. Depois de criar o perfil, o mesmo fornece-lhe um token de inscrição (cadeia aleatória) e um código QR. Consoante o SO Android e a versão do dispositivo, pode utilizar o token ou o código QR para [inscrever o dispositivo dedicado](#enroll-the-dedicated-devices).

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e escolha **registro** > de dispositivo registros**Android** > **dispositivos dedicados de propriedade corporativa**.
2. Selecione **Criar** e preencha os campos obrigatórios.
    - **Nome**: introduza o nome que irá utilizar quando atribuir o perfil ao grupo de dispositivos dinâmicos.
    - **Data de expiração do token**: a data em que o token expira. A Google impõe um máximo de 90 dias.
3. Escolha **Criar** para guardar o perfil.

### <a name="create-a-device-group"></a>Criar um grupo de dispositivos

Pode direcionar aplicações e políticas para grupos de dispositivos dinâmicos ou atribuídos. Pode configurar grupos de dispositivos do AAD dinâmicos para povoar automaticamente os dispositivos inscritos com um perfil de inscrição específico ao seguir estes passos:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e escolha **grupos** > **todos os grupos** > **novo grupo**.
2. No painel **Grupo**, preencha os campos obrigatórios da seguinte forma:
    - **Tipo de grupo**: Segurança
    - **Nome do grupo**: introduza um nome intuitivo (como Dispositivos da fábrica 1)
    - **Tipo de associação**: dispositivo dinâmico
3. Selecione **Adicionar consulta dinâmica**.
4. No painel **Regras de associação de grupo dinâmica**, preencha os campos da seguinte forma:
    - **Adicionar regra de associação dinâmica**: regra simples
    - **Adicionar dispositivos onde**: enrollmentProfileName
    - Na caixa do meio, selecione **Correspondência**.
    - No último campo, introduza o nome do perfil de inscrição que criou anteriormente.
    Para obter mais informações sobre regras de associação dinâmica, veja [Regras de associação dinâmica para grupos no AAD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Selecione **Adicionar consulta** > **Criar**.

### <a name="replace-or-remove-tokens"></a>Substituir ou remover tokens

- **Substituir token**: pode gerar um novo token/código QR quando o antigo estiver prestes a expirar.
- **Revogar token**: pode definir a expiração imediata do token/código QR. Quando o fizer, o token/código QR deixa de ser utilizável. Pode utilizar esta opção se:
  - partilhar acidentalmente o token/código QR com um terceiro não autorizado
  - concluir todas as inscrições e deixar de precisar do token/código QR

Substituir ou revogar um token/código QR não terá efeito em dispositivos que já tenham sido inscritos.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e escolha **registro de dispositivo registros** > do**Android** > **corporativo dispositivos dedicados de propriedade**.
2. Selecione o perfil com o qual pretende trabalhar.
3. Selecione **Token**.
4. Para substituir o token, selecione **Substituir token**.
5. Para revogar o token, selecione **Revogar token**.

## <a name="enroll-the-dedicated-devices"></a>Inscrever os dispositivos dedicados

Agora, pode [inscrever os dispositivos dedicados](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Gerir aplicações em dispositivos dedicados do Android Enterprise

Apenas as aplicações com o Tipo de atribuição [definido como Obrigatório](../apps/apps-deploy.md#assign-an-app) podem ser instaladas em dispositivos dedicados do Android Enterprise. As aplicações são instaladas a partir da loja do Managed Google Play da mesma forma que os dispositivos com perfil de trabalho do Android Enterprise.

As aplicações são atualizadas automaticamente em dispositivos geridos quando o programador da aplicação publica uma atualização na Google Play Store.

Para remover uma aplicação dos dispositivos dedicados do Android Enterprise, pode seguir um dos seguintes passos:
- Elimine a implementação da aplicação obrigatória.
- Crie uma implementação de desinstalação para a aplicação.

## <a name="next-steps"></a>Passos seguintes
- [Implementar aplicações Android](../apps/apps-deploy.md)
- [Adicionar políticas de configuração para Android](../configuration/device-profiles.md)
