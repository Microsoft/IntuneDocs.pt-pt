---
title: Categorizar os dispositivos com o mapeamento de grupo de dispositivos | Documentos da Microsoft
description: "Utilize o mapeamento de grupos de dispositivos do Microsoft Intune para agrupar dispositivos em categorias definidas por si, para facilitar a gestão desses dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 57c739444c18d12a6d7ee8ca591f9a1dd72985d7
ms.lasthandoff: 04/14/2017

---

# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>Categorizar os dispositivos com o mapeamento de grupo de dispositivos no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

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

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>Informações importantes acerca de uma alteração na gestão de grupo do Intune

Com base no seu feedback, estamos a unificar as experiências de agrupamento e filtragem no Enterprise Mobility + Security. Por esta razão, em breve iremos converter os grupos do Intune em grupos de segurança baseados no Azure Active Directory. Após esta alteração, deixará de criar grupos através do Intune. Passará a criá-los no portal do Azure. Esta alteração será efetuada de forma gradual e pode ler os detalhes completos acerca da mesma, bem como a respetiva linha cronológica [neste tópico](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>Que procedimento neste tópico deve utilizar para configurar o mapeamento de grupo de dispositivos?

Devido à implementação faseada dos grupos de segurança baseados no Azure Active Directory, tem de abrir a área de trabalho **Grupos** na [consola de administração do Intune](https://manage.microsoft.com) para identificar que procedimento deve utilizar:

-  Caso veja uma ligação para o portal do Azure, já não está a utilizar os grupos do Intune. Siga o procedimento [Como configurar o mapeamento de grupo de dispositivos para grupos do Azure Active Directory](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups) abaixo.
-  Caso não veja uma ligação para o portal do Azure, ainda está a utilizar os grupos do Intune. Siga o procedimento [Como configurar o mapeamento de grupo de dispositivos para grupos do Intune](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups) abaixo.

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>Como configurar o mapeamento de grupo de dispositivos para grupos do Intune
1. Para cada categoria de dispositivo que pretenda utilizar, crie um grupo de dispositivos do Intune ou identifique um grupo existente. Para informações sobre como criar grupos, consulte [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Admin**.
3. Na área de trabalho **Admin**, expanda **Mobile Device Management** e, em seguida clique em **Device Group Mapping**.
4. Na página **Device Group Mapping**, ative o mapeamento de grupo de dispositivos.
5. Clique em **Add** para criar uma nova regra de mapeamento.
6. Na caixa de diálogo **Add device group mapping rule**, introduza o nome da categoria que pretende criar e, em seguida, na lista pendente, escolha a coleção de dispositivos para a qual pretende mapear esta categoria. Clique em **Add** quando terminar.
7. Quando terminar de adicionar categorias e grupos, selecione **Save**.



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>Como configurar o mapeamento de grupo de dispositivos para grupos do Azure Active Directory

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>Passo 1–- crie categorias de dispositivo na consola de administração do Intune
1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Admin**.
3. Na área de trabalho **Admin**, expanda **Mobile Device Management** e, em seguida selecione **Device Categories**.
4. Na página **Device Categories**, verá uma lista onde pode configurar categorias de dispositivos: 
- Pode introduzir um nome e, em seguida, clicar em **Add**, para o adicionar a uma nova categoria de dispositivo.
- Pode ainda selecionar uma categoria e, em seguida, **Delete** a mesma.

Irá utilizar o nome de categoria de dispositivo quando criar grupos de segurança do Azure Active Directory no Passo 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Passo 2 – crie grupos de segurança do Azure Active Directory

Neste passo irá criar grupos dinâmicos no portal do Azure com base na categoria de dispositivo e no nome da categoria de dispositivo.

Para continuar, consulte o artigo [Using attributes to create advanced rules (Utilizar atributos para criar regras avançadas – em inglês)](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) na documentação do Azure Active Directory.
Utilize as informações neste tópico para criar um grupo de dispositivos com uma regra avançada utilizando o atributo **deviceCategory**.
Por exemplo (**device.deviceCategory -eq** "<*o nome de categoria do dispositivo que obteve na consola de administração do Intune*>")


## <a name="after-you-configure-device-groups"></a>Após configurar grupos de dispositivos

Quando os utilizadores inscreverem o respetivo dispositivo, é-lhes apresentada uma lista das categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o respetivo dispositivo é adicionado ao grupo de dispositivos do Intune ou ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

### <a name="see-also"></a>Consulte também
[Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

