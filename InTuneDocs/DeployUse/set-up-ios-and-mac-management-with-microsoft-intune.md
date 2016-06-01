---
# required metadata

title: Configurar a gestão de dispositivos iOS e Mac com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurar a gestão de dispositivos iOS e Mac
Com o Microsoft Intune, pode ativar a inscrição de dispositivos iOS e Mac OS X BYOD ("bring your own device") para dar acesso ao e-mail e às aplicações da empresa aos utilizadores de iPhone, iPad e Mac. Após a inscrição, os utilizadores podem instalar a aplicação Portal da Empresa do Intune e os respetivos dispositivos podem ser direcionados pela política através da consola de administração do Intune.

Antes de poder gerir dispositivos iOS com o Intune, os dispositivos têm de conseguir comunicar com o Intune. A Apple requer uma relação de confiança com o Intune estabelecida através da importação de um certificado de serviço Apple Push Notification (APNs).

1.  **Configurar o Intune**<br>
    Se ainda não o fez, prepare a gestão de dispositivos móveis [definindo a autoridade de gestão de dispositivos móveis](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) como **Microsoft Intune** e configurando a MDM.

2.  **Obter um pedido de assinatura do certificado**<br>
    Como um utilizador administrativo, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS e Mac OS X** &gt; **Carregar um Certificado do APNs** e clique em **Transferir o pedido de certificado do APNs**. Guarde o ficheiro de pedido de assinatura de certificado (.csr) localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

    ![Caixa de diálogo Carregar certificado do APNs](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obter um certificado de serviço Apple Push Notification**<br>
    Vá para o [Portal Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sessão com o ID Apple da sua empresa para criar o certificado do APNs através do ficheiro .csr. Depois de clicar em **Carregar** no Apple Push Certificates Portal, irá receber um ficheiro .json que não pode ser utilizado para o APNs. Conclua a transferência e regresse ao Apple Push Certificates Portal para obter **Certificados para Servidores de Terceiros** e clique em **Transferir**

    Transfira o certificado do APNs (.pem) e guarde o ficheiro localmente. Este ID Apple tem de ser utilizado no futuro para renovar o certificado APNs.

4.  **Adicionar o certificado do APNs ao Intune**<br>
    Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS e Mac OS X** &gt; **Carregar um Certificado do APNs**, clique em **Carregar o certificado do APNs**. **Navegue** até ao ficheiro de certificado (.pem), clique em **Abrir** e, em seguida, introduza o seu **ID Apple**. Com o certificado APNs, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. Informar os utilizadores de como obter acesso a recursos de empresa com o portal da empresa

5.  **Os seus utilizadores terão de saber como inscrever os respetivos dispositivos e o que esperar quando passarem a ser geridos.**<br>
    O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune [Se a sua empresa ou organização comprar dispositivos iOS para os utilizadores, esses dispositivos também podem ser inscritos para gestão como [dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)](what-to-tell-your-end-users-about-using-microsoft-intune.md)

Consulte Também

### Prepare-se para inscrever dispositivos no Microsoft Intune
[Get ready to enroll devices in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


