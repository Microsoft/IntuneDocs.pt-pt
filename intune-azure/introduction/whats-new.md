---
title: "Novidades na Pré-visualização do Microsoft Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: conheça as novidades na pré-visualização do Azure no Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/02/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e405363f9d0a89b1589b01d18ee8d2861b07ec60
ms.openlocfilehash: 70007f5501fba37964a0a54807c0e0f565510a74


---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novidades na pré-visualização do Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


À medida que a pré-visualização pública progride e mais funcionalidades são adicionadas, será informado aqui.

<!--## February 2017-->

<!--### Custom app categories <!--748805
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](/intune-azure/manage-apps/add-apps).-->

<!--### Display device categories <!--814654
You can now view the device category as a column in the device list. You can also edit the category from the properties section of the device properties blade.-->

## <a name="january-2017"></a>Janeiro de 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Atribuir aplicações de linha de negócio se os dispositivos estiverem ou não inscritos <!--748823-->
Pode agora atribuir aplicações de linha de negócio a partir da loja aos utilizadores se os respetivos dispositivos estiverem ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, este tem de aceder ao site do Portal da Empresa para instalá-lo, em vez da aplicação Portal da Empresa. Veja [O que é a gestão de aplicações](/intune-azure/manage-apps/what-is-app-management).

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver o problema no qual os dispositivos iOS estão inativos ou a consola de administração não consegue comunicar com os mesmos
Quando os dispositivos dos utilizadores perdem o contacto com o Intune, pode dar-lhes novos passos de resolução de problemas que os ajudem a recuperar o acesso aos recursos da empresa. Consulte [Os dispositivos estão inativos ou a consola de administração não consegue comunicar com os mesmos](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Dezembro de 2016 (versão inicial)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integração da gestão de despesas de telecomunicações na pré-visualização pública do portal do Azure<!--747605-->
Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com). Para ativar esta funcionalidade no seu inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Implementar e gerir aplicações de uma loja para dispositivos iOS, Android e Windows
- Implementar e gerir aplicações de uma linha de negócio (LOB) para dispositivos iOS, Android e Windows
- Implementar e gerir aplicações compradas em volume para dispositivos iOS e Windows
- Implementar e gerir aplicações Web para dispositivos Android, iOS e Windows
- Perfis de configuração de aplicações geridas iOS
- Configurar políticas de proteção de aplicações e implementar aplicações de linha de negócio em dispositivos que não estão inscritos com o Intune
- Perfis de VPN, VPN por aplicação, Wi-Fi, e-mail e perfis de certificados
- Políticas de conformidade
- Acesso condicional para o Azure AD
- Acesso condicional para o Exchange no Local
- Inscrição de dispositivos
- Controlo de acesso baseado em funções

## <a name="deprecated-features-in-the-azure-portal"></a>Funcionalidades preteridas no portal do Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Suporte para revisão de linha por linha de identificadores de hardware
O portal do Azure não suporta a revisão de linha por linha de identificadores de hardware para números IMEI e números de série da Apple. Na consola clássica do Intune, pode importar os detalhes de um ficheiro valores separados por vírgulas (.csv) e substituir os detalhes existentes de identificadores de hardware individuais. O portal do Azure oferece uma opção única e simplificada que substitui automaticamente os detalhes de todos os identificadores de hardware ou ignora os detalhes novos para os identificadores existentes.

#### <a name="how-this-affects-you"></a>De que forma o afeta
No portal do Azure, não poderá decidir, linha por linha, os dispositivos de Identidade Internacional do Equipamento Móvel (IMEI) a atualizar. A consola clássica do Intune continuará a suportar esta funcionalidade.

#### <a name="how-to-get-ready-for-this-change"></a>Como se preparar para esta alteração
Estamos a disponibilizar estas informações com antecedência para que, se for afetado, possa avisar os seus administradores de suporte em relação a esta alteração. Esta alteração vai coincidir com a transição para o portal do Azure, antecipada para o primeiro semestre de 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Suporte para perfis predefinidos de Inscrição de Dispositivos da Empresa no DEP da Apple
O portal do Azure não suporta o perfil “predefinido” de Inscrição de Dispositivos de Empresa para números de série de dispositivos do Programa de Registo de Aparelho (DEP) da Apple. Esta funcionalidade, disponível na consola clássica do Intune, vai ser descontinuada para evitar atribuições inadvertidas de perfis. No portal do Azure, os números de série sincronizados a partir de uma conta de DEP da Apple não terão inicialmente nenhum perfil de Inscrição de Dispositivos de Empresa atribuído.

#### <a name="how-this-affects-you"></a>De que forma o afeta
No portal do Azure, não poderá definir uma política de perfil predefinida em todos os dispositivos da Apple. A consola clássica do Intune continuará a suportar esta funcionalidade.

#### <a name="how-to-get-ready-for-this-change"></a>Como se preparar para esta alteração
Estamos a disponibilizar estas informações com antecedência para que, se for afetado, possa avisar os seus administradores de suporte em relação a esta alteração. Esta situação vai coincidir com a transição para o portal do Azure, antecipada para o primeiro semestre de 2017.



<!--HONumber=Feb17_HO1-->


