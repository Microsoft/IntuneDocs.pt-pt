---
title: "Definir restrições de inscrição no Intune"
titleSuffix: Intune on Azure
description: "Restrinja a inscrição por plataforma e defina um limite de inscrição de dispositivos no Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47dc35e5b50670027a85f395f674345b934d377b
ms.sourcegitcommit: 7674efb7de5ad54390801165364f5d9c58ccaf84
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/05/2017
---
# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Enquanto administrador do Intune, pode determinar que dispositivos podem ser inscritos para gestão no Intune. Utilize o portal do Intune para definir as seguintes restrições de inscrição de dispositivos:

- Número máximo de dispositivos inscritos
- Plataformas de dispositivos que podem ser inscritas:
  - Android
  - iOS
  - macOS
  - Windows
- Versão do sistema operativo da plataforma (apenas para iOS e Android)
  - Versão mínima
  - Versão máxima
- Restringir dispositivos pessoais (apenas para iOS, Android, macOS)

>[!NOTE]
>As restrições de inscrição não são funcionalidades de segurança. A identidade dos dispositivos pode ser falsificada de forma a contornar estas restrições. Estas restrições são uma forma de dissuadir utilizadores sem fins maliciosos.

## <a name="set-device-type-restrictions"></a>Definir restrições de tipos de dispositivos
As restrições de inscrição predefinidas aplicam-se a todas as inscrições de utilizadores e sem utilizadores.
1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Em **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**, selecione **Predefinido**.
5. Em **Todos os Utilizadores**, selecione **Plataformas**. Selecione **Permitir** ou **Bloquear** para cada plataforma:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Clique em **Guardar**.
6. Em **Todos os Utilizadores**, selecione **Configurações de Plataformas** e selecione as seguintes configurações. Para cada plataforma permitida, pode configurar as seguintes opções:
  - **Versões** – especifique as versões do sistema operativo da plataforma **Mínimas** e **Máximas** para dispositivos Android e iOS. As versões do sistema operativo não se aplicam a dispositivos inscritos com o Programa de Registo de Aparelho, o Apple School Manager ou a aplicação Apple Configurator.
  - **Propriedade Pessoal** – especifique se quer **Permitir** ou **Bloquear** dispositivos Android, iOS e macOS.
  ![Captura de ecrã a mostrar a área de trabalho de restrições de dispositivos, com as configurações de plataformas de dispositivos predefinidas a mostrar as definições de dispositivos pessoais que foram configuradas.](media/device-restrictions-platform-configurations.png)
  Clique em **Guardar**.

>[!NOTE]
>Se bloquear a inscrição de dispositivos pessoais Android, os dispositivos pessoais Android for Work continuarão a poder ser inscritos.

## <a name="set-device-limit-restrictions"></a>Definir restrições de limite de dispositivos
As restrições de inscrição predefinidas aplicam-se a todos os utilizadores.
1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. No portal do Intune, selecione **Inscrição de dispositivos** e **Restrições de inscrição**.
5. Selecione **Restrições de inscrição** > **Restrições de Limite de Dispositivos**.
6. Em **Todos os Utilizadores**, selecione **Limite de Dispositivos**. Especifique o número máximo de dispositivos inscritos por utilizador.  
![Captura de ecrã a mostrar o painel de restrições de limites de dispositivos, com as restrições de limites de dispositivos.](./media/device-restrictions-limit.png)

  Clique em **Guardar**.
