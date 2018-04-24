---
title: Definir a autoridade de gestão de dispositivos móveis
titlesuffix: Microsoft Intune
description: Definir a autoridade de gestão de dispositivos móveis no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e15e1678fa93269eb650f8a5684091b430ebf1cd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="set-the-mobile-device-management-authority"></a>Definir a autoridade de gestão de dispositivos móveis

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.

As configurações possíveis são:

- **Intune Autónomo** – gestão apenas na cloud, que configura através do portal do Azure. Inclui o conjunto completo das funcionalidades que o Intune oferece. [Defina a autoridade de MDM na consola do Intune](#set-mdm-authority-to-intune).

- **Intune Híbrido** – integração da solução cloud do Intune com o System Center Configuration Manager. Configura o Intune com a consola do Configuration Manager. [Defina a autoridade de MDM no Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestão de Dispositivos Móveis para o Office 365** – integração do Office 365 com a solução cloud do Intune. Configura o Intune a partir do Centro de Administração do Office 365. Inclui um subconjunto das funcionalidades que estão disponíveis com o Intune Autónomo. Defina a autoridade de MDM no Centro de Administração do Office 365.

> [!IMPORTANT]
> No Configuration Manager versão 1610 ou posterior e no Microsoft Intune versão 1705, pode alterar a autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Para obter detalhes, veja [O que fazer se escolher a definição de autoridade MDM errada](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Definir a autoridade de MDM como o Intune

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione a faixa cor de laranja para abrir a definição **Autoridade de Gestão de Dispositivos Móveis**.
4. Em **Autoridade de Gestão de Dispositivos Móveis**, selecione a sua autoridade de MDM a partir das seguintes opções:
   - **Autoridade de MDM do Intune**
   - **Autoridade MDM do Configuration Manager**
   - **Nenhum**

   ![Captura de ecrã do ecrã Definir a autoridade de gestão de dispositivos móveis do Intune](media/set-mdm-auth.png)

   Uma mensagem indica que definiu com êxito a autoridade de MDM como o Intune.

## <a name="enable-device-enrollment"></a>Ativar a inscrição de dispositivos

Com o Intune definido como a sua autoridade de MDM, os utilizadores podem inscrever dispositivos pessoais e obter acesso a recursos, como o e-mail, das seguintes formas ao instalar o Portal da Empresa (iOS, macOS e Windows), adicionar credenciais de trabalho (Windows) ou aceder ao site do Portal da Empresa (iOS, Android, macOS).

As diferentes plataformas têm os seguintes requisitos para ativar ou simplificar a inscrição:
- **iOS** – (obrigatório) [obter um certificado push de MDM da Apple](apple-mdm-push-certificate-get.md) e, em seguida, [ativar a inscrição dos dispositivos iOS pertencentes à empresa](ios-enroll.md) (opcional).
- **Android** – (opcional) [ativar os perfis de trabalho do Android](android-enroll.md)
- **Windows** – (opcional) ativar a [Inscrição automática](windows-enroll.md) ou a [inscrição em massa](windows-bulk-enroll.md)
- **macOS** – (obrigatório) [obter um Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md).


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.
