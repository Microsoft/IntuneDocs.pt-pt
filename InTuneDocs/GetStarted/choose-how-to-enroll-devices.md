---
# required metadata

title: Escolher como inscrever dispositivos móveis | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Escolher como inscrever dispositivos móveis

A inscrição de dispositivos móveis é o processo pelo qual smartphones, tablets e PCs são adicionados à gestão pelo Microsoft Intune. Como administrador, tem de determinar o melhor método para inscrever os dispositivos com base no seguinte:

 -  Propriedade (pessoal ou pertencente à empresa)
 -  Utilização (partilhado ou pessoal)
 -  Plataforma (iOS, Android, Windows Phone, PC Windows, PC Mac)

As respostas às questões que se seguem irão ajudá-lo a determinar o melhor método de inscrição para os dispositivos que gere.

## Os empregados utilizam os dispositivos deles ou os dispositivos são disponibilizados pela sua organização?

  **Dispositivos pertencentes ao utilizador** - inscrição "BYOD" (Bring your own device) – os utilizadores podem instalar a aplicação do Portal da Empresa do Intune nos dispositivos deles e, depois, inscrevê-los, obtendo acesso aos recursos da empresa como e-mail, aplicações da empresa, dados da empresa e suporte.  
  > [!div class="button"]   [Inscrição BYOD >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)

  **Dispositivos pertencentes à empresa** - é possível inscrever dispositivos pertencentes à empresa (COD) de diversas formas, consoante as necessidades da organização e os tipos de dispositivos geridos. Próxima pergunta...

## Os dispositivos pertencentes à empresa são partilhados ou têm utilizadores individuais?

**Dispositivos pertencentes à empresa partilhados** - estes dispositivos não têm um único utilizador e, normalmente, não estão configurados para aceder ao e-mail. Alguns exemplos incluem dispositivos de local público ou dispositivos orientados para tarefas e que os utilizadores recolhem quando precisam dos mesmos e, depois, devolvem. Os métodos de inscrição recomendados dependem da plataforma dos dispositivos.

  - **Dispositivos Windows e Android** - um *gestor de inscrição de dispositivos* é uma conta do Intune que pode ser utilizada para inscrever muitos dispositivos partilhados com a aplicação do Portal da Empresa.
  > [!div class="button"]   [Gestor de inscrição de dispositivos >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Dispositivos iOS** - os dispositivos iOS partilhados podem ser geridos de três formas.  **Como vai inscrever os dispositivos iOS partilhados?**

    - **Programa de registo de dispositivos da Apple (DEP)** - os dispositivos iOS adquiridos ou geridos com o DEP podem ser segmentados com um perfil de inscrição. Da primeira vez que os utilizadores inscrevem os dispositivos, estes transferem o perfil do DEP e são inscritos com o mesmo.
    > [!div class="button"]     [Inscrição através de DEP >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Apple Configurator num Mac** - o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração. Se não quiser repor os dispositivos para as definições de fábrica, utilize a inscrição direta.

    > [!div class="button"]     [Inscrição através do Assistente de Configuração >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) ou [Inscrição direta >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)

    - **Nenhuma das respostas anteriores** - se não puder ou não quiser utilizar os métodos DEP ou Apple Configurator, utilize o gestor de inscrição de dispositivos do Intune.
    > [!div class="button"]     [Inscrição com o DEM >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Utilizadores Individuais** - os dispositivos pertencentes à empresa atribuídos a utilizadores individuais têm de ser monitorizados como ativos da empresa e permitir, simultaneamente, aos utilizadores aceder a e-mail e dados como dispositivos pessoais. Os métodos de inscrição recomendados dependem da plataforma dos dispositivos.

  - **Dispositivos Windows e Android** - ao importar os números de identidade internacional do equipamento móvel (IMEI) dos dispositivos pertencentes à empresa, pode marcá-los como tal no Intune. Os utilizadores podem, em seguida, inscrever os dispositivos deles como dispositivos pessoais através da instalação do Portal da Empresa para aceder aos recursos da empresa, como e-mail, aplicações e dados.
  > [!div class="button"]   [Marcar com IMEI >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **Dispositivos iOS** - os dispositivos iOS partilhados podem ser geridos de três formas.  **Como vai inscrever os dispositivos iOS partilhados?**

    - **Programa de registo de dispositivos da Apple (DEP)** - os dispositivos iOS adquiridos ou geridos com o DEP podem ser segmentados com um perfil de inscrição. Da primeira vez que os utilizadores inscrevem os dispositivos, estes transferem o perfil do DEP e são inscritos de acordo com o mesmo.
    > [!div class="button"]     [Inscrição através de DEP](../deploy-use/ios-device-enrollment-program-in-microsoft-intune).

    - **Apple Configurator num Mac** - o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração.

    Se não quiser repor os dispositivos para as definições de fábrica, utilize a inscrição direta.
    Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração.
    > [!div class="button"][Inscrição através do Assistente de Configuração de iOS](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][Inscrição direta de iOS](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Nenhuma das respostas anteriores** - se não puder ou não quiser utilizar os métodos de inscrição DEP ou Apple Configurator, pode importar os números de identidade internacional do equipamento móvel (IMEI) dos dispositivos pertencentes à empresa para os marcar como tal no Intune. Os utilizadores podem, em seguida, inscrever os dispositivos deles como dispositivos pessoais através da instalação do Portal da Empresa para aceder aos recursos da empresa, como e-mail, aplicações e dados. > [!div class="button"][Marcar dispositivos com números de IMEI](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)


<!--HONumber=Jun16_HO1-->


