---
title: "Definir restrições de inscrição no Intune"
titleSuffix: Intune on Azure
description: "Restrinja a inscrição por plataforma e defina um limite de inscrição de dispositivos no Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/05/2017
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
- Restringir dispositivos pessoais (apenas para iOS e Android)

>[!NOTE]
>As restrições de inscrição não são uma funcionalidade de segurança. A identidade dos dispositivos pode ser falsificada de forma a contornar estas restrições. Estas restrições são uma forma de dissuadir utilizadores sem fins maliciosos.

## <a name="set-device-type-restrictions"></a>Definir restrições de tipos de dispositivos
As restrições de inscrição predefinidas aplicam-se a todos os utilizadores a quem não foram atribuídas restrições de prioridade mais elevada.  
1. No portal do Intune, selecione **Inscrição de dispositivos** e **Restrições de inscrição**.
![Captura de ecrã a mostrar a área de trabalho de restrições de dispositivos, com as restrições de tipos de dispositivos predefinidos e as restrições de limites de dispositivos.](media/device-restrictions-set-default.png)
2. Em **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**, selecione **Predefinido**.
3. Em **Todos os Utilizadores**, selecione **Plataformas**. Selecione **Permitir** ou **Bloquear** para cada plataforma:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Clique em **Guardar**.
4. Em **Todos os Utilizadores**, selecione **Configurações de Plataformas** e selecione as seguintes configurações:
  - **Propriedade Pessoal** – especifique se quer **Permitir** ou **Bloquear** dispositivos Android e iOS.
  ![Captura de ecrã a mostrar a área de trabalho de restrições de dispositivos, com as configurações de plataformas de dispositivos predefinidas a mostrar as definições de dispositivos pessoais que foram configuradas.](media/device-restrictions-platform-configurations.png)
  Clique em **Guardar**.

>[!NOTE]
>Se bloquear a inscrição de dispositivos pessoais Android, os dispositivos Android for Work continuarão a poder ser inscritos.

## <a name="set-device-limit-restrictions"></a>Definir restrições de limite de dispositivos
As restrições de inscrição predefinidas aplicam-se a todos os utilizadores a quem não foram atribuídas restrições de prioridade mais elevada.  
1. No portal do Intune, selecione **Inscrição de dispositivos** e **Restrições de inscrição**.
2. Selecione **Restrições de inscrição** > **Restrições de Limite de Dispositivos**.
3. Em **Todos os Utilizadores**, selecione **Limite de Dispositivos**. Especifique o número máximo de dispositivos inscritos por utilizador.  
![Captura de ecrã a mostrar o painel de restrições de limites de dispositivos, com as restrições de limites de dispositivos.](./media/device-restrictions-limit.png)

  Clique em **Guardar**.
