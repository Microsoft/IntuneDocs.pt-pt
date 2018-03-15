---
title: "Adicionar políticas de configuração da aplicação para dispositivos Android geridos"
titlesuffix: Microsoft Intune
description: "Utilize políticas de configuração da aplicação no Microsoft Intune para disponibilizar definições quando os utilizadores executarem uma aplicação do Android for Work."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 206e229e95633ce553637bcedef708ee5630864c
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Adicionar políticas de configuração da aplicação para dispositivos Android geridos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize políticas de configuração da aplicação no Microsoft Intune para disponibilizar definições quando os utilizadores executarem uma aplicação do Android for Work. Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, atribua a aplicação. As definições de política são utilizadas quando a aplicação as verificar, normalmente a primeira vez em que for executada.

> [!Note]  
> Nem todas as aplicações suportam a configuração de aplicações. Verifique junto do programador da aplicação para saber se este criou a aplicação de forma a suportar políticas de configuração da aplicação.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione a carga de trabalho **Aplicações Móveis**.
4. Selecione **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, selecione **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome**  
      O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**  
      A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**  
      Selecione **Dispositivos geridos**.
6. Selecione **Android for Work** em **Plataforma**.
7. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração da aplicação. Selecione na lista de aplicações Android for Work que aprovou e sincronizou com o Intune.
8. Selecione **Definições de configuração**. Pode definir configurações com:
    - [Estruturador de configuração](#Use-the-configuration-designer)
    - [Editor de JSON](#Enter-the-JSON-editor)
9. Selecione **OK** e, em seguida, **Adicionar**.

## <a name="use-the-configuration-designer"></a>Utilizar o estruturador de configuração

Pode utilizar o estruturador de configuração para as aplicações em dispositivos inscritos ou não inscritos no Intune. O estruturador permite-lhe configurar chaves e valores de configuração específicos. Também tem de especificar o tipo de dados para cada valor.

Para cada chave e valor na configuração, defina:

  - **Chave de configuração**  
     A chave que identifica exclusivamente a configuração de definição específica.
  - **Tipo de valor**  
    O tipo de dados do valor de configuração. Os tipos incluem Número Inteiro, Real, Cadeia ou Booleano.
  - **Valor de configuração**  
    O valor da configuração. 

## <a name="enter-the-json-editor"></a>Entrar no editor de JSON

Algumas definições de configuração em aplicações (tais como aquelas com tipos de Pacote) não podem ser configuradas com o estruturador de configuração. Tem de utilizar o editor de JSON para esses valores. As definições são fornecidas para aplicações automaticamente quando a aplicação é instalada.

1. Para o **Formato das definições de configuração**, selecione **Entrar no editor de JSON**.
2. No editor, pode definir valores JSON para as definições de configuração. Pode escolher **Transferir modelo JSON** para transferir um ficheiro de exemplo que pode configurar.
3. Selecione **OK** e, em seguida, **Adicionar**.

A política é criada e apresentada no painel da lista de políticas.

Quando a aplicação atribuída é executada num dispositivo, a mesma é executada com as definições que configurou na política de configuração de aplicações.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Pré-configurar o estado de concessão de permissões para aplicações

Também pode pré-configurar uma permissão para que as aplicações acedam às funcionalidades do dispositivo Android. Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, pedem aos utilizadores que aceitem ou neguem as permissões. Por exemplo, se uma aplicação utilizar o microfone do dispositivo, é pedido ao utilizador que conceda à aplicação permissão para utilizar o microfone.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **Aplicações Móveis**.
3. Em **Gerir**, selecione **Políticas de configuração da aplicação** e, em seguida, selecione **Adicionar**.
4. Defina os seguintes detalhes:
    - **Nome**. O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**. A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**. Selecione **Dispositivos geridos**.
    - **Plataforma**. Selecione **Android for Work**.
5. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração. Selecione na lista de aplicações Android for Work que aprovou e sincronizou com o Intune.
6. Selecione **Permissões** e, em seguida, escolha **Adicionar**.
7. Selecione na lista de permissões de aplicações disponíveis e, em seguida, escolha **OK**.
8. Selecione uma opção para cada permissão a conceder com esta política:
    - **Pedido de confirmação**. Solicitar o utilizador a aceitar ou recusar.
    - **Conceder automaticamente**. Aprovar automaticamente sem notificar o utilizador.
    - **Negar automaticamente**. Negar automaticamente sem notificar o utilizador.
9. Para atribuir a política de configuração de aplicações, selecione a política de configuração de aplicações, **Atribuição** e, em seguida, **Selecionar grupos**.
10. Selecione os grupos de utilizadores a atribuir e, em seguida, escolha **Selecionar**.
11. Escolha **Guardar** para atribuir a política.

## <a name="next-steps"></a>Passos seguintes

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação.

