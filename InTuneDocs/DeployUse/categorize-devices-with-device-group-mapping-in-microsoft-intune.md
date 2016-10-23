---
title: Categorizar os dispositivos com o mapeamento de grupo de dispositivos | Microsoft Intune
description: "Utilize o mapeamento de grupos de dispositivos do Microsoft Intune para agrupar dispositivos em categorias definidas por si, para facilitar a gestão desses dispositivos."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: 84850f4e9136e6304e51991d6ab0a0ae2a37e7a7


---

# Categorizar os dispositivos com o mapeamento de grupo de dispositivos no Microsoft Intune
Utilize o **mapeamento de grupo de dispositivo** do Microsoft Intune para adicionar automaticamente dispositivos a grupos com base nas categorias que definir, para facilitar a gestão desses dispositivos. 

O mapeamento de grupo de dispositivos utiliza o seguinte fluxo de trabalho:
1. Criar categorias que os utilizadores escolhem quando inscrevem o respetivo dispositivo
2. O utilizador cria grupos ou utiliza grupos existentes para cada categoria que pretende utilizar. Consoante a versão do Intune que estiver a utilizar, estes grupos serão grupos do Intune ou grupos de segurança do Active Directory.
2. O utilizador configura regras que mapeiam a categoria que escolher para o grupo de dispositivos que criou.
3. Quando os utilizadores finais inscreverem o respetivo dispositivo, têm de escolher uma categoria a partir da lista de categorias que configurou. Depois de escolherem, o respetivo dispositivo é automaticamente adicionado ao grupo que criou correspondente. Caso um dispositivo já se encontre inscrito, será pedido ao utilizador final para selecionar uma categoria da próxima vez que aceder à aplicação Portal da Empresa.
4. Nessa altura, pode implementar políticas e aplicações a estes grupos.

Pode criar as categorias de dispositivo que pretender, por exemplo:
* Dispositivo de ponto de venda
* Dispositivo de demonstração
* Vendas
* Contabilidade
* Manager

## Informações importantes acerca de uma alteração na gestão de grupo do Intune

Com base no seu feedback, estamos a unificar as experiências de agrupamento e filtragem no Enterprise Mobility + Security. Por esta razão, em breve iremos converter os grupos do Intune em grupos de segurança baseados no Azure Active Directory. Após esta alteração, deixará de criar grupos através do Intune. Passará a criá-los no portal do Azure. Esta alteração será efetuada de forma gradual e pode ler os detalhes completos acerca da mesma, bem como a respetiva linha cronológica [neste tópico](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### Que procedimento neste tópico deve utilizar para configurar o mapeamento de grupo de dispositivos?

Devido à implementação faseada dos grupos de segurança baseados no Azure Active Directory, tem de abrir a área de trabalho **Grupos** na [consola de administração do Intune](https://manage.microsoft.com) para identificar que procedimento deve utilizar:

-  Caso veja uma ligação para o portal do Azure, já não está a utilizar os grupos do Intune. Siga o procedimento [Como configurar o mapeamento de grupo de dispositivos (para grupos do Azure Active Directory)](##How-to-configure-device-group-mapping-(for-Azure-Active-Directory-groups) abaixo.
-  Caso não veja uma ligação para o portal do Azure, ainda está a utilizar os grupos do Intune. Siga o procedimento [Como configurar o mapeamento de grupo de dispositivos (para grupos do Intune)](##How-to-configure-device-group-mapping-(for-Intune-groups) abaixo.

## Como configurar o mapeamento de grupo de dispositivos para grupos do Intune
1. Para cada categoria de dispositivo que pretenda utilizar, crie um grupo de dispositivos do Intune ou identifique um grupo existente. Para informações sobre como criar grupos, consulte [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Admin**.
3. Na área de trabalho **Administração**, expanda **Gestão de Dispositivos Móveis** e, em seguida clique em **Mapeamento de Grupos de Dispositivos**.
4. Na página **Mapeamento de Grupo de Dispositivos**, ative o mapeamento de grupo de dispositivos.
5. Clique em **Adicionar** para criar uma nova regra de mapeamento.
6. Na caixa de diálogo **Adicionar regra de mapeamento de grupo de dispositivos**, introduza o nome da categoria que pretende criar e, em seguida, na lista pendente, escolha a coleção de dispositivos para a qual pretende mapear esta categoria. Clique em **Adicionar** quando terminar.
7. Quando terminar de adicionar categorias e grupos, selecione **Guardar**.



## Como configurar o mapeamento de grupo de dispositivos para grupos do Azure Active Directory

### Passo 1–- crie categorias de dispositivo na consola de administração do Intune
1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Admin**.
3. Na área de trabalho **Administração**, expanda **Gestão de Dispositivos Móveis** e, em seguida selecione **Categorias de Dispositivos**.
4. Na página **Categorias de Dispositivos**, verá uma lista onde pode configurar categorias de dispositivos: 
- Pode introduzir um nome e, em seguida, clicar em **Adicionar**, para o adicionar a uma nova categoria de dispositivo.
- Pode ainda selecionar uma categoria e, em seguida, **Eliminar** a mesma.

Irá utilizar o nome de categoria de dispositivo quando criar grupos de segurança do Azure Active Directory no Passo 2.

### Passo 2 – crie grupos de segurança do Azure Active Directory

Neste passo irá criar grupos dinâmicos no portal do Azure com base na categoria de dispositivo e no nome da categoria de dispositivo.

Para continuar, consulte o artigo [Using attributes to create advanced rules (Utilizar atributos para criar regras avançadas – em inglês)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) na documentação do Azure Active Directory.
Utilize as informações neste tópico para criar um grupo de dispositivos com uma regra avançada utilizando o atributo **deviceCategory**.
Por exemplo (**device.deviceCategory -eq** "<*o nome de categoria do dispositivo que obteve na consola de administração do Intune*>")


## Após configurar grupos de dispositivos

Quando os utilizadores inscreverem o respetivo dispositivo, é-lhes apresentada uma lista das categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o respetivo dispositivo é adicionado ao grupo de dispositivos do Intune ou ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

### Consulte também
[Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Oct16_HO2-->


