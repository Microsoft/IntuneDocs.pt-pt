---
title: Integrar MTD do Check Point SandBlast
titleSuffix: Microsoft Intune
description: Como configurar a Defesa Contra Ameaças para Dispositivos Móveis (MTD) do Check Point SandBlast com o Intune para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c3c19c927618cec4b5cb55eb08f097ea21ebc47
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729836"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Integrar o Check Point SandBlast Mobile com o Intune

## <a name="before-you-begin"></a>Antes de começar

> [!NOTE] 
> Os passos abaixo têm de ser efetuados na [consola MTD do Check Point SandBlast Mobile](https://intune-4.eu1.locsec.net/).

Antes de iniciar o processo de integração do Check Point SandBlast Mobile com o Intune, certifique-se de que tem o seguinte:

- Subscrição do Microsoft Intune

- Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:

  - Iniciar sessão e ler o perfil de utilizador

  - Aceder ao diretório como o utilizador com sessão iniciada

  - Ler dados do diretório

  - Enviar informações do dispositivo para o Intune

- Credenciais de administrador para aceder à consola MTD do Check Point SandBlast Mobile.

### <a name="check-point-sandblast-app-authorization"></a>Autorização da aplicação Check Point SandBlast

O processo de autorização da aplicação Check Point SandBlast consiste no seguinte:

- Permitir que o serviço Check Point SandBlast Mobile comunique informações relacionadas com o estado de funcionamento do dispositivo ao Intune.

- O Check Point SandBlast Mobile sincroniza com a associação do Grupo de Inscrição do Azure AD para povoar a respetiva base de dados do dispositivo.

- Permitir que a consola do administrador do Check Point SandBlast utilize o Início de Sessão Único (SSO) do Azure AD.

- Permitir que a aplicação Check Point SandBlast Mobile inicie sessão com o SSO do Azure AD.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>Para configurar a integração do Check Point SandBlast Mobile

1. Aceda à [consola MTD do Check Point SandBlast Mobile](https://intune-4.eu1.locsec.net/) e inicie sessão com as suas credenciais.

2. Clique no separador **Definições**.

3. Selecione **Gestão de dispositivos** e, em seguida, selecione **Definições**.

4. Selecione **Microsoft Intune** na lista pendente **Serviço MDM**.

5. Assim que definir o Microsoft Intune como o Serviço MDM, a janela **Configuração do Microsoft Intune** será apresentada. Selecione a opção **Adicionar à minha organização** para cada plataforma de dispositivos (iOS, Android e Windows) para autorizar que o Check Point SandBlast Mobile comunique com o Intune e o Azure AD.

    ![Imagem que mostra a configuração do Check Point MTD do Intune](./media/checkpoint-sandblast-mobile-mtd-connector-integration/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > Tem de adicionar todas as plataformas de dispositivos para avançar para o passo seguinte.

6. Selecione **Aceitar** para autorizar que a aplicação Check Point SandBlast Mobile comunique com o Intune e o Azure Active Directory.

7. Assim que ativar todas as plataformas de dispositivos, tem de introduzir o grupo de segurança do Azure AD.

8. Selecione **Verificar**. Assim que o grupo de segurança do Azure AD for verificado com êxito, selecione **Guardar**.

## <a name="next-steps"></a>Passos Seguintes

- [Set up Check Point SandBlast Mobile apps (Configurar aplicações do Check Point SandBlast Mobile)](mtd-apps-ios-app-configuration-policy-add-assign.md)
