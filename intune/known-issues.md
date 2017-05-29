---
title: "Problemas conhecidos na Pré-visualização do Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: leia sobre os problemas conhecidos na pré-visualização"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 36b35e5311f6262c545a266003fb72b2febb277c
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemas conhecidos na pré-visualização do Microsoft Intune


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Utilize este tópico para saber mais sobre os problemas conhecidos na pré-visualização do Intune.

Se quiser comunicar um erro que não se encontra listado aqui, [abra um pedido de suporte](https://docs.microsoft.com/intune-classic/troubleshoot/get-support).

Se quiser pedir uma nova funcionalidade para adicionar ao Intune, considere o preenchimento de um relatório no nosso site [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Os grupos criados pelo Intune durante a migração podem afetar o funcionamento de outros produtos da Microsoft

Quando migra do Intune clássico para o Portal do Azure, poderá ver um novo grupo com o nome **Todos os Utilizadores – b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Tenha em atenção que este grupo contém todos os utilizadores do Azure Active Directory, não apenas os utilizadores licenciados do Intune. Este facto pode provocar problemas com outros produtos Microsoft se estiver à espera que alguns dos utilizadores existentes ou novos não sejam membros de nenhum dos grupos.

### <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>A alteração dos grupos criados pelo Intune durante a migração atrasa a migração

Durante a preparação para a migração, os grupos são copiados do Intune para o Azure AD. Todas as outras alterações que fizer no portal do Intune clássico serão atualizadas no grupo do Azure AD. No entanto, as alterações feitas no Azure AD não serão sincronizadas de volta na consola do Intune clássico. Este facto pode fazer com que a migração para o portal do Azure falhe e provoque atrasos na migração.

### <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>As políticas de conformidade do Intune não aparecem na consola nova

As políticas de conformidade que criou no portal do Intune clássico são migradas, mas não são apresentadas no portal do Azure. O facto deve-se à alteração da estrutura no portal do Azure. As políticas de conformidade que criou no portal do Intune clássico ainda são impostas, mas tem de vê-las e editá-las no portal clássico.
Além disso, as novas políticas de conformidade que criar no portal do Azure não serão visíveis no portal clássico.
Para obter mais informações, veja [O que é a conformidade do dispositivo](device-compliance.md).




### <a name="administration-and-accounts"></a>Administração e contas

Os Administradores Globais (também designados por Administradores Inquilinos) podem continuar a realizar tarefas diárias de administração sem uma licença separada do Intune ou do Enterprise Mobility Suite (EMS). No entanto, se os Administradores Globais pretenderem utilizar o serviço, como, por exemplo, para inscrever os seus próprios dispositivos, um dispositivo da empresa ou utilizar o Portal da Empresa do Intune, precisarão de uma licença do Intune ou do EMS como qualquer outro utilizador.

### <a name="apple-enrollment-profile-migration"></a>Migração de perfis de inscrição da Apple
Nos próximos meses, o Intune vai ativar a gestão de inscrições do Apple Configurator e do Programa de Inscrição de Dispositivos Apple através do novo Portal do Azure. Se eliminar o token do Programa de Inscrição de Dispositivos da Apple e não carregar um token atualizado, o token original será restaurado no novo Portal do Azure como parte da migração da sua conta do Intune. Para remover este token e impedir a inscrição do DEP, basta eliminar o token no Portal do Azure. 

### <a name="rbac-for-apple-corporate-owned-device-enrollment"></a>RBAC para a inscrição de dispositivos pertencentes à empresa da Apple
As funções de Inquilino ou Administrador de Serviço Intune do Azure AD são necessárias para realizar tarefas de inscrição de DEP da Apple e do Configurador da Apple, apesar de as permissões RBAC estarem listadas e disponíveis na função de Utilizador personalizada. O suporte da função RBAC para estas funcionalidades será comunicado no futuro.

