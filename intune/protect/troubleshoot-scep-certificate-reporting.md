---
title: Problemas relatam a implementação de certificados de sucesso para dispositivos quando utilizar o SCEP com a Microsoft Intune  Microsoft Docs
description: Problemas de resolução do relatório por NDES e do conector ao Intune sobre uma implementação bem sucedida de certificados que foram provisionados com perfis de certificadoS SCEP.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913241"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Relatório sinuoso nDES de resolução de problemas de implementações de certificados no Microsoft Intune

Utilize as seguintes informações para confirmar que o NDES e o Microsoft Intune Certificate Connector reportam com sucesso ao Intune que o certificado foi entregue a um dispositivo. Reportar ao Intune é a última fase para utilizar perfis de certificadoS SCEP para fornecer dispositivos Windows com um certificado.

Este artigo aplica-se à etapa 6 do fluxo de trabalho de [comunicação scep](troubleshoot-scep-certificate-profiles.md).

## <a name="review-for-signs-of-successful-reporting"></a>Revisão de sinais de relatórios bem sucedidos

Se o relatório tiver sido bem sucedido, encontrará entradas que se assemelham aos seguintes exemplos no servidor NDES:

- **Registo IIS:**

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Registo de conector de certificado intune](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Registo de conector de certificado intune](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **Estatuto de Pedido de Certificado:**

  Vá à pasta *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* onde verá as pastas **Failed**, **Processing**e **Succeed** que contêm ficheiros de estado de pedido de certificado.

  Se o pedido de certificado for processado com sucesso, verá novos ficheiros na pasta **Succeed.** Pode utilizar *o Notepad.exe* para abrir os ficheiros e visualizar os dados que são enviados para o Serviço Intune pelo Conector de Certificado Intune. Os dados que foram enviados incluem detalhes como **CertificateSerialNumber,** **UserID,** **DeviceID**e **Thumbprint**.

### <a name="troubleshoot-stuck-files"></a>Ficheiros presos de resolução de problemas

Se não vir novos ficheiros a serem criados na pasta *Succeed,* verifique se existem ficheiros na pasta *Deprocessamento.*

Verifique se o Serviço de Conector Intune foi iniciado no servidor NDES e não existem erros no Ndesconnector.svclog.

## <a name="next-steps"></a>Próximos passos

[Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md)
