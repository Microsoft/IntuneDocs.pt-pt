---
title: "Introdução aos grupos na pré-visualização do portal do Azure no Intune"
titleSuffix: Intune Azure preview
description: "Conhecer as novidades nos grupos na pré-visualização do portal do Azure no Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0a6e2b75b1c85c0cd0ed98623dcd9d87b15eb082
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="get-started-with-groups"></a>Introdução aos grupos

[!INCLUDE[azure preview](./includes/azure_preview.md)]

Recebemos o seu feedback e fizemos algumas alterações à forma como trabalha com os grupos no Microsoft Intune.
Se estiver a utilizar o Intune a partir do portal do Azure, os grupos do Intune migraram para os grupos de segurança do Azure Active Directory.

A vantagem para si é que agora utiliza a mesma experiência de grupos em todas as suas aplicações do Enterprise Mobility + Security e Azure AD. Além disso, poderá utilizar o PowerShell e a Graph API para expandir e personalizar esta nova funcionalidade.

Os grupos de segurança do Azure AD suportam todos os tipos de implementações do Intune para utilizadores e dispositivos. Além disso, pode utilizar os grupos dinâmicos do Azure AD atualizados automaticamente com base nos atributos fornecidos. Por exemplo, pode criar um grupo de dispositivos que executam o iOS 9. Sempre que um dispositivo que execute o iOS 9 for inscrito, o dispositivo é apresentado automaticamente no grupo dinâmico.

## <a name="what-is-not-available"></a>O que não está disponível?

Algumas das capacidades de grupos do Intune que poderá ter utilizado anteriormente não estão disponíveis no Azure AD:

- Os grupos do Intune **Utilizadores Sem Grupo** e **Dispositivos Sem Grupo** já não estão disponíveis.
- A opção **Excluir membros específicos** de um grupo não existe no portal do Azure. No entanto, pode utilizar um grupo de segurança do Azure AD com regras avançadas para replicar este comportamento. Por exemplo, para criar uma regra avançada que inclui todas as pessoas do seu departamento de Vendas num grupo de segurança, mas exclui as regras com a palavra "Assistente" no respetivo título, pode utilizar esta regra avançada:

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- O grupo **Todos os Dispositivos Geridos pelo Exchange ActiveSync** na consola do Intune não foi migrado para o Azure AD. No entanto, pode continuar a aceder às informações sobre os dispositivos geridos por EAS a partir do portal do Azure.

## <a name="how-to-get-started"></a>Como começar?

- Leia os seguintes tópicos para saber mais sobre os grupos de segurança do Azure AD e como funcionam:
    -  [Gerir o acesso aos recursos com grupos do Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
    -  [Gerir grupos no Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-  Certifique-se de que os administradores que precisam de criar grupos são adicionados à função **Administrador do Serviço Intune** do Azure AD. A função Administrador do Serviço Azure AD não tem as permissões **Gerir Grupo**.
-  Se os seus grupos do Intune utilizaram a opção **Excluir membros específicos**, tem de decidir se pode reestruturar esses grupos sem exclusões ou se precisa de regras avançadas para satisfazer as necessidades da empresa.


## <a name="what-happened-to-intune-groups"></a>O que aconteceu aos grupos do Intune?
Quando os grupos são migrados do portal clássico do Intune para o Intune no portal do Azure, as seguintes regras são aplicáveis:

| Grupos no Intune|Grupo no Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Grupo de utilizadores estático|Grupo de segurança estático do Azure AD|
|Grupo de utilizadores dinâmico|Grupos de segurança estáticos do Azure AD com uma hierarquia de grupo de segurança do Azure AD|
|Grupo de dispositivos estático|Grupo de segurança estático do Azure AD|
|Grupo de dispositivos dinâmico|Grupo de segurança dinâmico do Azure AD|
|Um grupo com uma condição de inclusão|Grupo de segurança estático do Azure AD que contém quaisquer membros estáticos ou dinâmicos da condição de inclusão no Intune|
|Um grupo com uma condição de exclusão|Não migrado|
|Os grupos incorporados:<br>- **Todos os Utilizadores**<br>- **Utilizadores Sem Grupo**<br>- **Todos os Dispositivos**<br>- **Dispositivos Sem Grupo**<br>- **Todos os Computadores**<br>- **Todos os Dispositivos Móveis**<br>- **Todos os Dispositivos Geridos pela MDM**<br>- **Todos os Dispositivos Geridos pelo EAS**|Grupos de segurança do Azure AD|

## <a name="group-hierarchy"></a>Hierarquia de grupos

Na consola clássica do Intune, todos os grupos têm um grupo principal. Os grupos só podem conter membros do seu grupo principal. No Azure AD, os grupos subordinados podem conter membros que não estejam no seu grupo principal.

## <a name="group-attributes"></a>Atributos do grupo
Os atributos podem ter propriedades de dispositivos que podem ser utilizadas na definição de grupos. Esta tabela descreve como esses critérios serão migrados para os grupos de segurança do Azure AD.

| Atributo no Intune|Atributo no Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Atributo de Unidade Organizacional (UO) para grupos de dispositivos|Atributo de UO para grupos dinâmicos.|
|Atributo de nome de domínio para grupos de dispositivos|Atributo de Nome de Domínio para grupos dinâmicos.|
|Grupo de segurança como um atributo para grupos de utilizadores|Os grupos não podem ser atributos em consultas dinâmicas do Azure AD. Os grupos dinâmicos só podem conter atributos específicos de utilizadores ou dispositivos.|
|Atributo de gestor para grupos de utilizadores|Regra Avançada para o atributo *gestor* nos grupos dinâmicos|
|Todos os utilizadores do grupo de utilizadores principal|Grupo estático com o respetivo grupo como membro|
|Todos os dispositivos móveis do grupo de dispositivos principal|Grupo estático com o respetivo grupo como membro|
|Todos os dispositivos móveis geridos pelo Intune|Atributo Tipo de Gestão com "MDM" como o valor para grupo dinâmico|
|Grupos aninhados em grupos estáticos |Grupos aninhados em grupos estáticos|
|Grupos aninhados em grupos dinâmicos|Grupo dinâmico com um nível de aninhamento|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>O que acontece às políticas e às aplicações implementadas anteriormente?

As políticas e as aplicações continuam a ser implementadas em grupos, tal como antes. No entanto, agora irá gerir estes grupos a partir do portal do Azure, em vez da consola clássica do Intune.
