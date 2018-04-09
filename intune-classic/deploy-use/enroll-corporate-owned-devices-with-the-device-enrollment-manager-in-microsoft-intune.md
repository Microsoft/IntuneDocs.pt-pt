---
title: Inscrever com o gestor de inscrição de dispositivos
description: A conta do gestor de inscrição de dispositivos (DEM) pode gerir um grande número de dispositivos móveis pertencentes à empresa partilhados com uma única conta de utilizador.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f9ecb8cf16d8c344ea595c53ab91c9b1f00c90e
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta de utilizador especial que pode inscrever até 1000 dispositivos. Pode adicionar utilizadores existentes à conta DEM de forma a conceder-lhes capacidades especiais de DEM. Cada dispositivo inscrito utiliza uma única licença. Recomendamos que utilize os dispositivos inscritos através desta conta como dispositivos partilhados (ou seja, sem afinidade de utilizador) em vez de dispositivos pessoais ("BYOD").  

Têm de existir utilizadores no portal do Azure para serem adicionados como gestores de inscrição de dispositivos. Para garantir a segurança, o utilizador DEM não deve ser também um administrador do Intune.

>[!NOTE]
>O método de inscrição DEM não pode ser utilizado com o [Assistente de Configuração do Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) ou a [inscrição direta](ios-direct-enrollment-in-microsoft-intune.md), com a inscrição do macOS nem com o [método de inscrição DEP](ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exemplo de um cenário do gestor de inscrição de dispositivos

Um restaurante quer fornecer 50 tablets de ponto de venda aos seus empregados de mesa e monitores de apresentação de pedidos para os empregados da cozinha. Os funcionários não precisam nunca de aceder aos dados da empresa nem de iniciar sessão como utilizadores. O administrador do Intune cria uma conta de gestor de inscrição de dispositivos e adiciona um supervisor de restaurante à conta DEM, concedendo assim capacidades de DEM a esse supervisor. Agora, o supervisor pode inscrever os 50 tablets com as credenciais de DEM.

Apenas os utilizadores da consola do Intune podem ser gestores de inscrição de dispositivos. O utilizador do gestor de inscrição de dispositivos não pode ser um administrador do Intune.

O utilizador DEM pode:

-   Inscrever até 1000 dispositivos no Intune
-   Utilizar a aplicação Portal da Empresa para obter aplicações da empresa
-   Configurar o acesso aos dados da empresa ao implementar aplicações específicas de funções nos tablets

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitações dos dispositivos inscritos com uma conta DEM

Os dispositivos inscritos com uma conta de gestor de inscrição de dispositivos têm as seguintes limitações:

  - Não há nenhum "utilizador" de dispositivo específico. Por conseguinte, não existe acesso aos dados da empresa ou ao e-mail. No entanto, a VPN, por exemplo, poderá continuar a ser utilizada para fornecer aplicações de dispositivos com acesso a dados.

  - Não há acesso condicional, porque estes cenários são por utilizador.

  - O utilizador DEM não pode utilizar o Portal da Empresa para anular a inscrição de dispositivos inscritos para DEM no próprio dispositivo. O administrador do Intune tem esta capacidade, mas o utilizador DEM não a tem.

  - Apenas o dispositivo local é apresentado na aplicação Portal da Empresa ou do site.

  - Os utilizadores não podem utilizar aplicações Apple Volume Purchase Program (VPP) devido aos requisitos do Apple ID por utilizador para a gestão de aplicações.

  - (Apenas para iOS) Se utiliza DEM para inscrever dispositivos iOS, não pode utilizar o Apple Configurator nem o Programa de Inscrição de Dispositivos Apple (DEP) para inscrever dispositivos.

> [!NOTE]
> Para implementar aplicações da empresa em dispositivos geridos com o gestor de inscrição de dispositivos, implemente a aplicação Portal da Empresa como uma **Instalação Obrigatória** na conta de utilizador do gestor de inscrição de dispositivos.
> Para melhorar o desempenho, a aplicação Portal da Empresa num dispositivo DEM apresenta apenas os dispositivos locais. A gestão remota de outros dispositivos DEM só pode ser efetuada a partir da consola de administração do Intune.


## <a name="add-a-device-enrollment-manager"></a>Adicionar um gestor de inscrição de dispositivos

1.  Certifique-se de que o utilizador que pretende adicionar à conta DEM já existe. Se precisar de adicionar o utilizador, inicie sessão no [portal do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698854)e siga os passos em [Adicionar utilizadores individualmente ou em volume ao Office 365 – Ajuda para Administradores ](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

2.  Inicie sessão na [Consola de administração do Microsoft Intune](https://manage.microsoft.com) com as suas credenciais de administrador.

3.  No painel de navegação, selecione **Admin**, aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**. A página **Gestores de Inscrição de Dispositivos** é apresentada.

4.  Selecione **Adicionar...**. A caixa de diálogo **Adicionar Gestor de Inscrição de Dispositivos** é aberta.

5.  Introduza o **ID de Utilizador** da conta do Intune e, em seguida, selecione **OK**.

    O utilizador DEM pode agora inscrever dispositivos móveis com o mesmo procedimento utilizado por um utilizador final num cenário BYOD no Portal da Empresa. O utilizador final do gestor pode instalar a aplicação Portal da Empresa e inscrever o dispositivo com as suas credenciais DEM até um máximo de 1000 dispositivos. Para obter os passos de inscrição em cada plataforma para utilizadores finais, consulte:

  - [Inscrever o seu dispositivo iOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
  - [Inscrever o seu dispositivo macOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)
  - [Inscrever o seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)
  - [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Eliminar um gestor de inscrição de dispositivos do Intune

1.  Inicie sessão no [Portal de administração do Microsoft Intune](https://manage.microsoft.com) com as suas credenciais de administrador.

2.  No painel de navegação, selecione **Admin**, aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**. A página **Gestores de Inscrição de Dispositivos** é apresentada.

3.  Selecione o **Utilizador** do gestor de inscrição de dispositivos que pretende eliminar e, em seguida, selecione **Eliminar**. Este utilizador não será eliminado do Intune e os dispositivos geridos pelo mesmo continuarão inscritos no Intune. A eliminação de um gestor de inscrição de dispositivos impede o utilizador de inscrever mais dispositivos no Intune.

4.  Selecione **Sim** para confirmar que pretende eliminar o gestor de inscrição de dispositivos.

A eliminação de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos. Quando um gestor de inscrição de dispositivos é eliminado:

-   Os dispositivos inscritos não são afetados.

-   Os dispositivos inscritos continuam a ser completamente geridos.

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada mantêm-se válidas para o início de sessão no Portal da Empresa para aceder a aplicações.

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada continuam sem poder apagar ou extinguir dispositivos.

-   A relação da conta do gestor de inscrição de dispositivos eliminada com os dispositivos inscritos é mantida, mas não é possível inscrever mais dispositivos.
