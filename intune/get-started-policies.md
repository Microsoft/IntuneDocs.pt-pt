---
title: Introdução às políticas no Microsoft Intune – Azure | Microsoft Docs
description: Crie políticas para ajudar a proteger dados empresariais e gerir os dispositivos que os utilizadores finais utilizam para aceder aos recursos da empresa. Em seguida, atribua as políticas aos grupos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271529"
---
# <a name="get-started-with-creating-policies"></a>Introdução à criação de políticas

As políticas do Intune são uma ótima forma de inscrever dispositivos e certificar-se de que estão em conformidade com as suas políticas empresariais. As políticas de conformidade ajudam-no a gerir tipos de dispositivos especializados e quiosques pertencentes à empresa e dispositivos pessoais (Bring Your Own Device), tablets e dispositivos sem utilizador.

![Dashboard de conformidade com poucos dados](/intune/media/generic-compliance-dashboard.png)

Os dispositivos móveis podem ser geridos através de políticas de conformidade, incluindo:

* Regular o número de dispositivos que um utilizador pode inscrever no Intune
* Gerir as definições dos dispositivos, como a encriptação ao nível do dispositivo, o comprimento da palavra-passe e a utilização da câmara
* Disponibilizar aplicações, perfis de e-mail, perfis da VPN, entre outros
* Avaliar os critérios ao nível do dispositivo das políticas de conformidade de segurança

As políticas de conformidade são criadas para cada plataforma, como o iOS, Android, Windows e mais. Para este exercício, utilize o iOS. As seguintes políticas estão disponíveis para dispositivos iOS:

* Configuração do PIN ou da palavra-passe
* Encriptação do dispositivo
* Dispositivo desbloqueado por jailbreak
* Perfil de e-mail
* Versão mínima do SO
* Versão máxima do SO

## <a name="create-a-policy"></a>Criar uma política

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
4. Introduza um **Nome** e uma **Descrição**. 
5. Para a **Plataforma**, selecione **iOS**.
6. Em **Definições**, selecione **Segurança do Sistema** e, em seguida, defina **Exigir uma palavra-passe para desbloquear os dispositivos móveis** para **Exigir**. 

    Também pode definir outras regras, como: 
    - **Comprimento mínimo da palavra-passe**
    - **Tipo obrigatório de palavra-passe**
    - **Número de carateres não alfanuméricos na palavra-passe**
    
    Quando terminar de configurar a sua política, selecione **OK**.
  
7. Clique em **Criar política** e selecione **Criar**. Este passo cria a política e indica a sua política em **Conformidade do dispositivo** > **Políticas**.
8. Selecione a nova política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
Escolha Grupos selecionados para ver os seus grupos de segurança do Azure Active Directory existentes. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política aos utilizadores.

Para estar em conformidade com a nova política empresarial, após alguns minutos, o seu dispositivo inscrito pede uma palavra-passe atualizada. Pode procurar a atualização manualmente na **aplicação Portal da Empresa para iOS**. Abra a aplicação Portal da Empresa, selecione o nome do dispositivo e selecione **Sincronizar**.

> [!NOTE]
> As novas políticas aplicadas a um grupo de dispositivos dinâmico poderão demorar até oito horas a serem aplicadas a todos os dispositivos no grupo.

## <a name="next-steps"></a>Próximos passos

[Introdução à inscrição de dispositivos](get-started-enroll.md) – conheça a experiência de inscrição ao efetuar uma experiência de inscrição completa de um dispositivo iOS.

## <a name="learn-more"></a>Saiba mais

* [Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
* [Formas comuns de utilizar as políticas de acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
