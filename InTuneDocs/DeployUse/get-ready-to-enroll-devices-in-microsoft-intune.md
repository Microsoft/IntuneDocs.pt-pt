---
# required metadata

title: Preparar-se para inscrever dispositivos no Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Prepare-se para inscrever dispositivos no Microsoft Intune
Para permitir aos empregados inscrever dispositivos móveis (incluindo Android, iOS, Windows Phone e PCs Windows) com o Intune, é necessário ativar a inscrição de dispositivos. Para permitir a inscrição, tem de definir uma autoridade de gestão de dispositivos móveis, configurar o Portal da Empresa do Intune, atribuir licenças e ativar a inscrição para a plataforma do dispositivo.

## <a name="BKMK_Set_MDM_Authority"></a>Definir autoridade de gestão de dispositivos móveis
A autoridade de MDM define o serviço de gestão com permissão para gerir um conjunto de dispositivos. As opções para a autoridade de MDM incluem o Intune e o Configuration Manager com o Intune. Se definir o Configuration Manager como autoridade de gestão, nenhum outro serviço pode ser utilizado para gestão de dispositivos móveis.

>[!IMPORTANT]
> Considere cuidadosamente se pretende gerir dispositivos móveis ao utilizar apenas o Intune (serviço online) ou o System Center Configuration Manager com o Intune (solução de software no local em conjunto com o serviço online). A definição da autoridade de gestão de dispositivos móveis não pode ser alterada.



1.  Na [consola do administração do Microsoft Intune](http://manage.microsoft.com), clique em **Admin** &gt; **Gestão de Dispositivos Móveis**

2.  Na lista **Tarefas** , clique em **Definir Autoridade de Gestão de Dispositivos Móveis**. A caixa de diálogo **Definir Autoridade de Gestão de Dispositivos Móveis** é aberta.

    ![Caixa de diálogo Definir autoridade de MDM](../media/intune-mdm-authority.png)

3.  O Intune pede a confirmação de que pretende o Intune como a sua autoridade MDM. Selecione a caixa e, em seguida, clique em **Sim** para utilizar o Microsoft Intune para gerir dispositivos móveis.

## Configurar o Portal da Empresa do Intune e atribuir licenças
O Portal da Empresa do Intune ajuda os utilizadores a aceder aos recursos da empresa, como aplicações, localizar informações de suporte técnico e inscrever e anular a inscrição de dispositivos. Antes de inscrever dispositivos, deve [configurar o Portal da Empresa](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-7). Também tem de [atribuir licenças de utilizador](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-4) para permitir o acesso ao Intune.

## Configurar a gestão de dispositivos
Depois de configurar a autoridade de MDM, tem de configurar a gestão de dispositivos para os sistemas operativos que a organização pretende suportar. Os passos necessários para configurar a gestão de dispositivos variam consoante o sistema operativo. Por exemplo, o SO Android não requer que efetue nenhuma ação na consola de administração do Intune. Por outro lado, o Windows e o iOS requerem uma relação de confiança entre os dispositivos e o Intune para permitir a gestão.

> [!div class="op_single_selector"]
- [Configurar a gestão de Android com o Microsoft Intune](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)
- [Configurar a gestão de dispositivos Windows com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)

Também pode:
 - Utilize a [conta do gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) para inscrever muitos dispositivos
 - [Especifique os dispositivos pertencentes à empresa utilizando números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) para ajudar a inscrever dispositivos e a política de destino


<!--HONumber=May16_HO2-->


