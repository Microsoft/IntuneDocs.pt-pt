---
title: "Introdução às políticas"
titlesuffix: Azure portal
description: "Crie políticas para impedir que os utilizadores executem ações não autorizadas com os seus dispositivos."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7d100eeb177e2b47065f0688d9f94b2f4e5c06bc
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-policies"></a>Introdução às políticas

Um dos principais objetivos da introdução ao Intune é a inscrição de dispositivos para garantir que estão em conformidade com as políticas empresariais. As políticas de conformidade irão ajudá-lo a gerir tipos de dispositivos especializados, como quiosques pertencentes à empresa, mas também dispositivos pessoais (Bring Your Own Device), tablets e dispositivos sem utilizador.

![Dashboard de conformidade com poucos dados](/intune/media/generic-compliance-dashboard.png)

As políticas de conformidade fornecem as seguintes funcionalidades de gestão para dispositivos móveis:

* Regular o número de dispositivos que cada utilizador inscreve
* Gerir as definições dos dispositivos (por exemplo, a encriptação ao nível do dispositivo, o comprimento da palavra-passe, a utilização da câmara)
* Disponibilizar aplicações, perfis de e-mail, perfis da VPN, etc.
* Avaliar os critérios ao nível do dispositivo das políticas de conformidade de segurança

Cria políticas de conformidade para cada plataforma separadamente. Neste exercício, iremos utilizar o iOS. As seguintes políticas estão disponíveis para dispositivos iOS:

* Configuração do PIN ou da palavra-passe
* Encriptação do dispositivo
* Dispositivo desbloqueado por jailbreak
* Perfil de e-mail
* Versão mínima do SO
* Versão máxima do SO

__Como posso criar uma política?__

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Em **Procurar recursos**, procure o **Intune**.
3. Selecione **Conformidade do dispositivo**.
4. No painel **Conformidade do dispositivo**, selecione **Políticas**.
5. Selecione **Criar Política** e, em seguida, preencha os detalhes, como **Nome** e **Descrição**. Selecione **iOS** como a **Plataforma**.
6. Em **Definições**, selecione **Segurança do Sistema** e, em seguida, mude o botão de alternar **Exigir uma palavra-passe para desbloquear os dispositivos móveis** para **Exigir**. Também pode definir outras regras, tal como **Comprimento mínimo da palavra-passe**, **Tipo obrigatório de palavra-passe** e **Número de carateres não alfanuméricos na palavra-passe**. Quando terminar de configurar a sua política, selecione **OK**.
7. Regresse ao painel **Criar política** e, em seguida, selecione **Criar**.
8. Assim que a política for criada, selecione **Atribuições** para atribuí-la ao seu grupo de teste. Selecione o seu grupo de teste (que deve conter o seu utilizador de teste) e, em seguida, atribua a política a esse grupo ao clicar em **Guardar**.
9. Aguarde uns minutos e, em seguida, o seu dispositivo inscrito deverá indicar-lhe que precisa de uma palavra-passe atualizada para permanecer em conformidade com a política empresarial. Também pode verificar isto manualmente na **aplicação Portal da Empresa para iOS** ao tocar no nome do dispositivo e, em seguida, no botão **Sincronizar**.

## <a name="next-steps"></a>Próximos passos

[Introdução à inscrição de dispositivos](get-started-enroll.md) – conheça a experiência de inscrição ao efetuar uma experiência de inscrição completa de um dispositivo iOS.

## <a name="learn-more"></a>Saiba mais

* [Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
* [Formas comuns de utilizar as políticas de acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
