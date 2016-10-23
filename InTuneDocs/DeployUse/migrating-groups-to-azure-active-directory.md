---
title: Migrar para os Grupos do Azure Active Directory | Microsoft Intune
description: "Como os grupos serão migrados do Intune para o Azure AD"
keywords: 
author: nbigman
manager: angerobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
translationtype: Human Translation
ms.sourcegitcommit: d92c9ffe42b36770a32c28941de3c402aec9dd68
ms.openlocfilehash: 08bcc258f64e6385ae6fa648ddb8f2b5fe68942e


---

## A nova experiência de administrador para os grupos
    
Com base no seu feedback para uma experiência de agrupamento e direcionamento no Enterprise Mobility & Security, estamos a converter os Grupos do Intune em Grupos de Segurança baseados no Azure Active Directory. Isto irá unificar a gestão de grupos através do Intune e do Azure Active Directory (Azure AD). A nova experiência irá evitar que tenha de duplicar grupos entre serviços e fornece extensibilidade através do PowerShell e do Graph. 

### Como e quando serei migrado para a nova experiência de grupos?
A migração dos clientes atuais ocorrerá ao longo de um período de tempo e só será iniciada a partir de dezembro de 2016. Receberá uma notificação antes de os seus grupos serem migrados. Se tiver alguma preocupação referente à migração, contacte a nossa equipa de migração em [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### Que novas funcionalidades estarão disponíveis para mim?
Segue-se a nova funcionalidade que será introduzida: 
 
-    Os Grupos de Segurança do Azure AD serão suportados no Intune para todos os tipos de implementações. 
-    Os Grupos de Segurança do Azure AD suportarão o agrupamento de dispositivos, bem como de utilizadores.
-    Os Grupos de Segurança do Azure AD suportarão grupos dinâmicos com atributos de dispositivos do Intune. Por exemplo, poderá agrupar dinamicamente dispositivos com base na plataforma, por exemplo, iOS. Dessa forma, quando um novo dispositivo iOS é inscrito na sua organização, é adicionado automaticamente ao grupo de dispositivos dinâmico iOS.
-    Experiências de administração partilhadas para gestão de grupos no Azure AD e no Intune.
- A *função Administrador de Serviços do Intune* será adicionada ao Azure AD para permitir aos administradores de serviços no Intune efetuar tarefas de gestão de grupos no Azure AD.

 
### Que funcionalidades do Intune não estarão disponíveis?
Embora a experiência de grupo vá ser melhorada, poderão existir algumas funcionalidades do Intune que não estarão disponíveis após a migração.

#### Funcionalidade de gestão de grupos

-   Não poderá excluir membros ou grupos quando criar um novo grupo. No entanto, os grupos dinâmicos do Azure AD irão permitir a utilização de atributos para criar regras avançadas para excluir membros com base nos critérios. Por exemplo, pode criar uma regra avançada que inclui todas as pessoas do seu departamento de Vendas num grupo de segurança, mas não as que têm a palavra "Assistente" no respetivo título, com esta regra avançada: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`. Para mais informações, consulte [Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-   Não existirá suporte para os grupos **Utilizadores Sem Grupo** e **Dispositivos Sem Grupo**. Esses grupos não serão migrados.

#### Funcionalidade dependente dos grupos

-   A função Administrador de Serviço não terá permissões para **Gerir grupos**.
-   Não poderá agrupar dispositivos do Exchange ActiveSync.  O grupo **Todos os Dispositivos Geridos do EAS** será convertido de um grupo para uma vista de relatório.
-  A funcionalidade para ordenar com grupos em relatórios não estará disponível.
-  A filtragem de grupos personalizada de regras de notificação não estará disponível.

### O que devo fazer para me preparar para esta alteração?
 Temos recomendações que facilitarão esta transição para si:
 
- Limpe todos os grupos do Intune indesejados ou desnecessários antes da migração.
- Avalie a sua utilização da exclusão em grupos e considere como reestruturar os seus grupos para que não seja necessário utilizar a exclusão ou para poder utilizar regras avançadas para o mesmo fim.
-  Se tiver administradores que não têm permissões para criar grupos no Azure AD, peça ao administrador do Azure AD para adicioná-los à função **Administrador de Serviço do Intune** do Azure AD.

Também pode saber mais sobre os grupos de segurança do Azure AD:
-  Para obter uma descrição geral, consulte [Gerir o acesso aos recursos com grupos do Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
-  Para saber como criar e gerir grupos do Azure AD, consulte [Gerir grupos no Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
-  Para saber mais sobre regras avançadas para grupos de segurança, consulte [Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).

> [!NOTE]
Poderá reparar que a documentação de grupos de segurança do Azure AD não aborda a criação de grupos para dispositivos. Esta funcionalidade será ativada no Azure AD antes que a migração de grupos do Intune comece.

## Detalhes de migração
Eis os detalhes sobre como os seus grupos do Intune serão migrados para os grupos de segurança do Azure AD.

### Migração de grupos existentes

| O grupo do Intune torna-se...|...grupo de segurança do Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Grupos de utilizador estáticos visados pela política do Intune|Grupos de segurança estáticos do Azure AD com os mesmos utilizadores|
|Grupos de utilizador dinâmicos visados pela política do Intune|Grupos de segurança estáticos do Azure AD com uma hierarquia de grupo de segurança do Azure AD|
|Grupos de dispositivos estáticos visados pela política do Intune|Grupos de segurança estáticos do Azure AD com dispositivos|
|Grupos de dispositivos dinâmicos com atributos de dispositivos, que são visados pela política do Intune|Grupos de segurança dinâmicos do Azure AD com atributos de dispositivos|
|Um grupo com uma condição de inclusão|Um grupo de segurança estático do Azure AD separado que irá conter um grupo + membros estáticos/dinâmicos que a condição de inclusão tenha permitido no Intune|
|Um grupo com uma condição de exclusão|...não será migrado. As condições de exclusão não são suportadas durante a criação de grupos estáticos no Azure AD. Uma condição de exclusão pode ser utilizada ao criar um grupo dinâmico no Azure AD.|
|Os grupos predefinidos **Todos os Utilizadores**, **Utilizadores Sem Grupo**, **Todos os Dispositivos**, **Dispositivos Sem Grupo**, **Todos os Computadores**, **Todos os Dispositivos Móveis**, **Todos os dispositivos geridos por MDM** e **Todos os dispositivos geridos por EAS**, que utiliza na política do Intune  |Grupos de segurança do Azure AD. Os grupos predefinidos que não estão a ser utilizados teriam de ser criados pelo cliente quando necessário, utilizando os grupos dinâmicos.|

### Alterações nas vistas hierárquicas
A vista hierárquica para grupos na relação Principal/subordinado no Intune era uma relação Supercunjunto/subconjunto, o que não é o caso no Azure AD. O elemento subordinado pode ter membros que o elemento principal não tinha. Os grupos também podem ter uma natureza cíclica no Azure AD: um grupo principal pode ser o grupo subordinado de um grupo subordinado.

### Atribuir conversão durante a migração
Os atributos podem ter propriedades de dispositivos que podem ser utilizadas na definição de grupos. Esta tabela descreve como esses critérios serão migrados para os grupos de segurança do Azure AD.

| Atributo do Intune|Atributo do Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Atributo de Unidade Organizacional (UO) para grupos de dispositivos|Atributo de UO para grupos dinâmicos. Atribui valores disponibilizados ao administrador relativos a cada inquilino, adicionando-o como um dos componentes de inquilinos para visualização.|
|Atributo de nome de domínio para grupos de dispositivos|Atributo de Nome de Domínio para grupos dinâmicos. Atribui valores disponibilizados ao administrador relativos a cada inquilino, adicionando-o como um dos componentes de inquilinos para visualização|
|Grupo de segurança como um atributo para grupos de utilizadores|Os grupos não podem ser atributos em consultas dinâmicas do Azure AD. Os grupos dinâmicos só podem conter atributos específicos de utilizadores ou dispositivos.|
|Atributo de gestor para grupos de utilizadores|Regra Avançada para o atributo *gestor* nos grupos dinâmicos|
|Todos os utilizadores do grupo de utilizadores principal|Grupo estático com o respetivo grupo como membro|
|Todos os dispositivos móveis do grupo de dispositivos principal|Grupo estático com o respetivo grupo como membro|
|Todos os dispositivos móveis geridos pela Gestão Direta do Microsoft Intune|Atributo Tipo de Gestão com "MDM" como o valor para grupo dinâmico|
|Todos os dispositivos móveis geridos pelo EAS|Os dispositivos EAS não podem ser agrupados no Azure AD. O grupo **Todos os Dispositivos Geridos do EAS** será convertido de um grupo para uma vista de relatório.|
|Grupos aninhados em grupos estáticos |Grupos aninhados em grupos estáticos|
|Grupos aninhados em grupos dinâmicos|Grupo dinâmico com um nível de aninhamento|


## Migração de políticas
Enquanto a migração do grupo estiver em curso, continuará a gerir as suas políticas na consola do Intune. Haverá uma ligação na consola do Intune para a sua consola de gestão do Azure, onde irá gerir os seus grupos. As suas políticas irão continuar a ser implementadas para os grupos de segurança migrados do Azure AD paralelos aos seus grupos do Intune antigos.

Quando todas as funcionalidades do Intune forem migradas para o portal de gestão do Azure (por volta do primeiro trimestre de 2017), irá gerir as políticas e os grupos no mesmo.

     
### Consulte também
[Gerir o acesso aos recursos com grupos do Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)

[Gerir grupos no Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)

[Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)



<!--HONumber=Oct16_HO2-->


