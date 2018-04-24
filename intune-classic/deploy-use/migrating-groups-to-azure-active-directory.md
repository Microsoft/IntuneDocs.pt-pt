---
title: Migrar para os grupos do Azure Active Directory
description: Como os grupos serão migrados do Intune para o Azure AD
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 12/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: ef0b540b6b70ca67a0da8b00997bb761722eb76a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="a-new-way-of-using-groups-in-intune"></a>Uma nova forma de utilizar os grupos no Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Recebemos o seu feedback e estamos a fazer algumas alterações à forma como trabalha com os grupos no Microsoft Intune.
Estamos no processo de migração de todos os nossos clientes dos grupos do Intune para os grupos de segurança do Azure Active Directory.

A vantagem para si é que utilizará agora a mesma experiência de grupos em todas as suas aplicações do Enterprise Mobility + Security e Azure AD. Além disso, poderá utilizar o PowerShell e a Graph API para expandir e personalizar esta nova funcionalidade.

Os grupos de segurança do Azure AD suportam todos os tipos de implementações do Intune para utilizadores e dispositivos. Além disso, pode utilizar os grupos dinâmicos do Azure AD atualizados automaticamente com base nos atributos fornecidos. Por exemplo, pode criar um grupo de dispositivos que executam o iOS 9. Sempre que for inscrito um novo dispositivo com o iOS 9, este será adicionado automaticamente ao grupo dinâmico.

## <a name="when-is-this-happening"></a>Quando é que isto acontece?

O processo de migração está a decorrer neste momento. Será notificado antes de ser migrado.
Se já tiver sido migrado, verá uma mensagem semelhante a esta quando tentar aceder aos grupos a partir da consola clássica do Intune:

![Mensagem para mostrar os grupos migrados.](http://i.imgur.com/72KRaXj.png)

## <a name="what-wont-be-available"></a>O que deixará de estar disponível?

Algumas funcionalidades existentes de grupos do Intune não estão disponíveis no Azure AD:

- Os grupos do Intune **Utilizadores Sem Grupo** e **Dispositivos Sem Grupo** não serão migrados.
- A opção **Excluir membros específicos** de um grupo que existe atualmente na consola do Intune não existe no portal do Azure. No entanto, pode utilizar um grupo de segurança do Azure AD com regras avançadas para replicar este comportamento. Por exemplo, pode criar uma regra avançada que inclui todas as pessoas do seu departamento de Vendas num grupo de segurança, mas não as que têm a palavra "Assistente" no respetivo título, com esta regra avançada: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- O grupo **Todos os Dispositivos Geridos pelo Exchange ActiveSync** incorporado na consola do Intune não será migrado para o Azure AD. No entanto, pode continuar a aceder às informações sobre os dispositivos geridos por EAS a partir do portal do Azure.
- Não poderá filtrar os relatórios por grupos na consola clássica do Intune.
<!--- - Custom group targeting of notification rules will not be available. ROB I took this out as I couldn't replicate the behavior. --->

## <a name="how-to-get-ready"></a>Como se preparar

- Leia os seguintes tópicos do Azure AD para saber mais sobre os grupos de segurança do Azure AD e como funcionam:
    -  [Gerir o acesso aos recursos com grupos do Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
    -  [Gerir grupos no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
- Pondere remover todos os grupos do Intune que já não utiliza antes de migrar.
-  Certifique-se de que os administradores que precisam de criar grupos estão adicionados à função **Administrador do Serviço Intune** do Azure AD. Tenha em atenção que a função Administrador do Serviço Azure AD não tem as permissões **Gerir Grupo**.
-  Se utilizar grupos com a opção **Excluir membros específicos**, pondere se pode reestruturar estes grupos para não precisarem de exclusões ou se é possível utilizar regras avançadas na sua consulta do Azure AD para alcançar o mesmo resultado.


## <a name="what-happens-to-intune-groups"></a>O que acontece aos grupos do Intune?

| Grupos no Intune|Grupo no Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Grupo de utilizadores estático|Grupo de segurança estático do Azure AD|
|Grupo de utilizadores dinâmico|Grupos de segurança estáticos do Azure AD com uma hierarquia de grupo de segurança do Azure AD|
|Grupo de dispositivos estático|Grupo de segurança estático do Azure AD|
|Grupo de dispositivos dinâmico|Grupo de segurança dinâmico do Azure AD|
|Um grupo com uma condição de inclusão|Grupo de segurança estático do Azure AD que contém os membros estáticos ou dinâmicos da condição de inclusão no Intune.|
|Um grupo com uma condição de exclusão|Não migrado|
|Os grupos incorporados **Todos os Utilizadores**, **Utilizadores Sem Grupo**, **Todos os Dispositivos**, **Dispositivos Sem Grupo**, **Todos os Computadores**, **Todos os Dispositivos Móveis**, **Todos os dispositivos geridos por MDM** e **Todos os dispositivos geridos por EAS**|Grupos de segurança do Azure AD.|

No Intune, todos os grupos precisam de ter um grupo principal. Os grupos só podem conter membros do respetivo grupo principal. No Azure AD, os grupos subordinados podem conter membros que não pertencem ao grupo principal.

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

## <a name="what-happens-to-policies-and-apps-youve-already-deployed"></a>O que acontece às políticas e às aplicações já implementadas?

As políticas e as aplicações continuam a ser implementadas em grupos, tal como antes. No entanto, agora irá gerir estes grupos a partir do portal do Azure, em vez da consola clássica do Intune.
 
