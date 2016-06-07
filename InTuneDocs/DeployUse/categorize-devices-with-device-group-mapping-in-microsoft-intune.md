---
# required metadata

title: Categorizar os dispositivos com o mapeamento de grupo de dispositivos no Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Categorizar os dispositivos com o mapeamento de grupo de dispositivos no Microsoft Intune
Utilize o **mapeamento de grupo de dispositivos** do Microsoft Intune para agrupar dispositivos nas categorias definidas, para facilitar a gestão desses dispositivos. 

O mapeamento de grupo de dispositivos utiliza o seguinte fluxo de trabalho:
1. Crie grupos de dispositivos do Intune para cada categoria que pretende utilizar.
2. Configure regras de mapeamento de grupo de dispositivos que mapeiam a categoria que escolher para o grupo de dispositivos que criou.
3. Quando os utilizadores finais inscreverem o respetivo dispositivo, têm de escolher uma categoria de entre as categorias que configurou. Depois de escolherem, o respetivo dispositivo será adicionado automaticamente ao grupo de dispositivos correspondente que criou.
4. Em seguida, pode utilizar estes grupos de dispositivos quando implementar políticas e aplicações.

Exemplos de categorias:
* Pessoal
* Dispositivo de ponto de venda
* Dispositivo de demonstração
* Vendas
* Contabilidade
* Manager

No entanto, pode configurar quaisquer categorias que pretender.

## Como configurar o mapeamento de grupo de dispositivos
1. Cria um grupo de dispositivos do Intune para cada categoria que pretende utilizar. Para obter informações sobre como criar grupos, consulte [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Admin**.
3. Na área de trabalho **Administração**, expanda **Gestão de Dispositivos Móveis** e, em seguida clique em **Mapeamento de Grupos de Dispositivos**.
4. Na página **Mapeamento de Grupo de Dispositivos**, ative o mapeamento de grupo de dispositivos.
5. Clique em **Adicionar** para criar uma nova regra de mapeamento.
6. Na caixa de diálogo **Adicionar regra de mapeamento de grupo de dispositivos**, introduza o nome da categoria que pretende criar e, em seguida, na lista pendente, escolha a coleção de dispositivos para a qual pretende mapear esta categoria. Clique em **Adicionar** quando terminar.
7. Quando terminar de adicionar categorias e grupos, clique em **Guardar**.

Agora, quando os utilizadores inscreverem o respetivo dispositivo, será apresentada uma lista das categorias que configurou. Depois de escolherem uma categoria e concluírem a inscrição, o respetivo dispositivo será adicionado ao grupo de dispositivos que corresponde à categoria que escolheram.

### Consulte também
[Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

<!--HONumber=May16_HO1-->

