---
title: Solucionar problemas do conector de certificado Microsoft Intune e IDs de evento | Microsoft Docs
description: Solucione problemas do Microsoft Intune Certificate Connector revisando IDs e descrições de eventos e examine os códigos de diagnóstico para o serviço do conector do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 682d51269798dff181a3bd8384268da862118a70
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729440"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Eventos do Intune Certificate Connector e códigos de diagnóstico

A partir da versão 6.1806.X.X, o Serviço do Intune Connector regista eventos no **Visualizador de Eventos** (**Registos de Aplicações e Serviços** > **Microsoft Intune Connector**). Utilize estes eventos para o ajudar a resolver potenciais problemas na configuração do Intune Connector. Estes eventos registam sucessos e falhas de uma operação e também contêm códigos de diagnóstico com mensagens que ajudam o administrador de TI a resolver problemas.

> [!TIP]  
> Para solucionar problemas e verificar a configuração do conector do Intune, consulte [exemplos de script da autoridade de certificação](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>IDs e descrições do evento

| ID do Evento      | Nome do Evento    | Descrição do Evento | Códigos de Diagnóstico Relacionados |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Serviço de conector iniciado | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Serviço de conector parado | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Certificado de inscrição do conector renovado com êxito | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Não foi possível renovar o certificado de inscrição do conector. Reinstale o conector. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Falha ao obter o certificado de inscrição do conector do registo. Reveja os detalhes do evento para o thumbprint do certificado relacionado com este evento. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Verifique as informações de diagnóstico nos detalhes do evento. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Certificado PKCS emitido com êxito. Reveja os detalhes do evento para obter o ID do dispositivo, o ID do utilizador, o nome CA, o nome do modelo de certificado e o thumbprint do certificado relacionados com este evento. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Falha ao emitir um certificado PKCS. Reveja os detalhes do evento para obter o ID do dispositivo, o ID do utilizador, o nome CA, o nome do modelo de certificado e o thumbprint do certificado relacionados com este evento. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Certificado revogado com êxito. Reveja os detalhes do evento para o ID do dispositivo, o ID do utilizador, o nome CA e o número de série do certificado relacionados com este evento. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Falha ao revogar o certificado. Reveja os detalhes do evento para o ID do dispositivo, o ID do utilizador, o nome CA e o número de série do certificado relacionados com este evento. Para obter mais informações, veja os Registos NDES SVC.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Os dados de pedido ou revogação do certificado foram carregados com êxito. Reveja os detalhes do evento para obter os detalhes do carregamento. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Falha ao carregar os dados de pedido ou revogação do certificado. Reveja os detalhes do evento > Estado de Carregamento para determinar o ponto de falha.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Foi transferido com êxito o pedido para assinar um certificado, transferir um certificado de cliente ou revogar um certificado. Reveja os detalhes do evento para obter os detalhes da transferência.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Falha ao transferir o pedido para assinar um certificado, transferir um certificado de cliente ou revogar um certificado. Reveja os detalhes do evento para obter os detalhes da transferência. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Ponto de Registo de Certificados verificou com êxito um desafio de cliente | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | O Ponto de Registo de Certificados foi concluído, mas rejeitou o pedido. Consulte o código de diagnóstico e a mensagem para obter mais detalhes. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Falha do Ponto de Registo de Certificados ao verificar um desafio de cliente. Consulte o código de diagnóstico e a mensagem para obter mais detalhes. Veja os detalhes da mensagem do evento para obter o ID de Dispositivo que corresponde ao desafio. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | O Ponto de Registo de Certificados concluiu com êxito o processo de notificação e enviou o certificado para o dispositivo cliente. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | O Ponto de Registo de Certificados não conseguiu concluir o processo de notificação. Veja os detalhes da mensagem do evento para obter informações sobre o pedido. Verifique a ligação entre o servidor do NDES e a AC. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Códigos de diagnóstico

| Código de Diagnóstico | Nome do Diagnóstico | Mensagem de Diagnóstico |
| -------------   | -------------   | -------------      |
| 0x00000000 | Êxito  | Êxito |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | A autoridade de certificação não é válida ou está inacessível. Verifique se a autoridade de certificação está disponível e se o servidor consegue comunicar com a mesma. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | O certificado Symantec Client Auth não foi encontrado no arquivo de certificados local. Veja o artigo [Instalar o certificado de autorização de registo da Symantec](certificates-digicert-configure.md#install-the-digicert-ra-certificate) para obter mais informações.  |
| 0x00000402 | RevokeCert_AccessDenied  | A conta especificada não tem permissões para revogar um certificado de AC. Veja o campo Nome da AC nos detalhes da mensagem de evento para determinar a AC emissora.  |
| 0x00000403 | CertThumbprint_NotFound  | Não foi possível localizar um certificado que corresponda à sua pesquisa. Inscreva o conector do certificado e tente novamente. |
| 0x00000404 | Certificate_NotFound  | Não foi possível localizar um certificado que corresponda às informações fornecidas. Volte a inscrever o conector do certificado e tente novamente. |
| 0x00000405 | Certificate_Expired  | Um certificado expirou. Volte a inscrever o conector do certificado para renovar o certificado e tente novamente. |
| 0x00000408 | CRPSCEPCert_NotFound  | Não foi possível encontrar o certificado de Encriptação CRP. Verifique se o NDES e o Intune Connector estão configurados corretamente. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Não foi possível obter o certificado de assinatura. Verifique se o Serviço do Intune Connector está configurado corretamente e se está em execução. Verifique também se os eventos de transferência de certificado foram efetuados com êxito. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Falha ao anular a serialização do pedido de desafio SCEP. Verifique se o NDES e o Conector do Intune estão configurados corretamente. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Pedido recusado devido a um desafio de certificado expirado. O dispositivo cliente pode tentar novamente depois de obter um novo desafio do servidor de gestão. |
| 0x0FFFFFFFF | Unknown_Error  | Não conseguimos concluir o pedido porque ocorreu um erro do lado do servidor. Tente novamente. |


## <a name="next-steps"></a>Passos seguintes
Para obter assistência adicional, use a [implantação do perfil de certificado SCEP de solução de problemas no guia Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) .
