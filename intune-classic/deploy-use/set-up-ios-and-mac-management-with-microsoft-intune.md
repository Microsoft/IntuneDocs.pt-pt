---
title: Set up iOS and Mac management
description: Ative a gestão de dispositivos móveis (MDM) para dispositivos iOS, incluindo iPads e iPhones, bem como dispositivos Mac OS X com o Microsoft Intune.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 280efe7e7a5a1616ebab9abce7b7a5d78e321e7c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-ios-and-mac-device-management"></a>Configurar a gestão de dispositivos iOS e Mac

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Intune permite a gestão de dispositivos móveis (MDM), como iPads, iPhones e dispositivos macOS, e concede aos utilizadores acesso a aplicações e e-mail empresariais. É necessário um certificado do serviço Apple Push Notification (APNs) para que o Intune possa gerir dispositivos iOS e Mac. Quando o certificado for adicionado ao Intune, os utilizadores podem instalar a aplicação Portal da Empresa para inscrever os respetivos dispositivos ou o administrador pode configurar a [gestão de dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurar o Intune**<br>
    Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** e ao configurar a MDM.

2.  **Obter um pedido de assinatura do certificado**<br>
    Como um utilizador administrativo, abra a [consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Admin** &gt; **Mobile Device Management** &gt; **iOS and Mac OS X** &gt; **Upload an APNs Certificate** e selecione **Download the APNs certificate request**. Guarde o ficheiro de pedido de assinatura de certificado (.csr) localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

    ![Caixa de diálogo Carregar certificado do APNs](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obter um certificado do serviço Apple Push Notification**<br>
    Aceda ao [Portal Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sessão com o ID Apple da sua empresa para criar o certificado de APNs através do ficheiro .csr. Após selecionar **Carregar** no Portal do Certificado Push da Apple, irá receber um ficheiro .json que não pode ser utilizado para o APNs. Conclua a transferência, regresse ao Apple Push Certificates Portal para obter **Certificados para Servidores de Terceiros** e selecione **Transferir**.

    Transfira o certificado de APNs (.pem) e guarde o ficheiro localmente.

    > [!NOTE]
    > Terá de renovar (e não substituir) este certificado de APNs todos os anos. Utilize o mesmo ID Apple para iniciar sessão no Portal do Certificado Push da Apple para renovar o certificado e, em seguida, utilize as mesmas instruções neste tópico para transferir o certificado e carregue-o para o Intune.

4.  **Adicionar o certificado APNs ao Intune**<br>
    Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Admin** &gt; **Mobile Device Management** &gt; **iOS and Mac OSX** &gt; **Upload an APNs Certificate** e selecione **Upload the APNs certificate**. Aceda ao ficheiro de certificado (.pem), selecione **Abrir** e, em seguida, introduza o seu **ID Apple**. Com o certificado APNs, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.

5.  **Indique aos utilizadores como devem inscrever os respetivos dispositivos para poderem aceder aos recursos da empresa.**

    Para obter instruções sobre a inscrição do utilizador final, veja [Inscrever o dispositivo iOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) e [Inscrever o dispositivo macOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos). O processo de inscrição informa os utilizadores sobre o que podem esperar e o que os administradores de TI podem e não podem ver nos respetivos dispositivos.

    Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:
    - [Recursos sobre a experiência do utilizador final com o Microsoft Intune](/intune/end-user-educate)
    - [Orientações para o utilizador final para dispositivos iOS e Mac](https://docs.microsoft.com/intune-user-help/using-your-ios-or-macOS-device-with-intune)

Se a sua empresa ou organização comprar dispositivos iOS para os utilizadores, esses dispositivos também podem ser inscritos para gestão como [dispositivos iOS propriedade da empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Consulte Também
[Pré-requisitos para a inscrição no Microsoft Intune](prerequisites-for-enrollment.md)
