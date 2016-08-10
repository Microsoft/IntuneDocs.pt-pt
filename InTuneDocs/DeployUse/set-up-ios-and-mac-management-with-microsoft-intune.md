---
title: "Configurar a gestão de iOS e Mac | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos iOS, incluindo iPads e iPhones, bem como dispositivos Mac OS X com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: e61e764f4761ab83500ff6f0febe253d427729d9


---

# Configurar a gestão de dispositivos iOS e Mac
Para configurar o seu dispositivo iOS ou Mac, pode encontrar ajuda [aqui](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md).

Gestão de dispositivos móveis do Intune para iPads, iPhones e dispositivos Mac OS X e forneça acesso a aplicações e ao e-mail da empresa. É necessário um certificado do serviço Apple Push Notification (APMs) para que o Intune possa gerir dispositivos iOS e Mac. Quando o certificado for adicionado ao Intune os utilizadores podem instalar a aplicação do Portal da Empresa para inscrever os dispositivos deles ou o administrador pode configurar a [gestão de dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurar o Intune**<br>
    Se ainda não o fez, prepare a gestão de dispositivos móveis [definindo a autoridade de gestão de dispositivos móveis](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) como **Microsoft Intune** e configurando a MDM.

2.  **Obter um pedido de assinatura do certificado**<br>
    Como um utilizador administrativo, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS e Mac OS X** &gt; **Carregar um Certificado do APNs** e clique em **Transferir o pedido de certificado do APNs**. Guarde o ficheiro de pedido de assinatura de certificado (.csr) localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

    ![Caixa de diálogo Carregar certificado do APNs](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obter um certificado de serviço Apple Push Notification**<br>
    Vá para o [Portal Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sessão com o ID Apple da sua empresa para criar o certificado do APNs através do ficheiro .csr. Depois de clicar em **Carregar** no Apple Push Certificates Portal, irá receber um ficheiro .json que não pode ser utilizado para o APNs. Conclua a transferência e regresse ao Apple Push Certificates Portal para obter **Certificados para Servidores de Terceiros** e clique em **Transferir**.

    Transfira o certificado do APNs (.pem) e guarde o ficheiro localmente. Este ID Apple tem de ser utilizado no futuro para renovar o certificado APNs.

4.  **Adicionar o certificado do APNs ao Intune**<br>
    Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS e Mac OSX** &gt; **Carregar um Certificado do APNs** e clique em** Carregar o certificado do APNs**. **Procure** o certificado do ficheiro (.pem), clique em **Abrir** e, em seguida, introduza o seu **ID Apple**. Com o certificado APNs, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.

5.  **Informar os utilizadores de como obter acesso a recursos de empresa com o portal da empresa**<br>
    Os seus utilizadores terão de saber como inscrever os dispositivos deles e o que esperar quando passarem a ser geridos.
    - [O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Orientações para o utilizador final para dispositivos iOS e Mac](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Se a sua empresa ou organização comprar dispositivos iOS para os utilizadores, esses dispositivos também podem ser inscritos para gestão como [dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Consulte Também
[Prepare-se para inscrever dispositivos no Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


