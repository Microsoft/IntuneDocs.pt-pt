---
title: Solucionar problemas do conector de certificado Microsoft Intune e IDs de evento | Microsoft Docs
titleSuffix: Microsoft Intune
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
ms.openlocfilehash: 2d798f22ee4e0f11f46626eec01ad3b739d61467
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306720"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Eventos do Intune Certificate Connector e códigos de diagnóstico

A partir da versão 6.1806. x. x, o serviço do conector do Intune registra eventos na **Visualizador de eventos** (**logs de aplicativos e serviços** > **Microsoft Intune conector**). Use esses eventos para ajudar a solucionar possíveis problemas na configuração do conector do Intune. Esses eventos registram êxitos e falhas de uma operação e também contêm códigos de diagnóstico com mensagens para ajudar o administrador de ti a solucionar problemas.

> [!TIP]  
> Para solucionar problemas e verificar a configuração do conector do Intune, consulte [exemplos de script da autoridade de certificação](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>IDs e descrições de eventos

| ID do evento      | Nome do evento    | Descrição do evento | Códigos de diagnóstico relacionados |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Serviço de conector iniciado | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Serviço de conector interrompido | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Certificado de registro de conector renovado com êxito | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Falha ao renovar o certificado de registro do conector. Reinstale o conector. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Falha ao recuperar o certificado de registro do conector do registro. Examine os detalhes do evento para a impressão digital do certificado relacionada a esse evento. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Verifique as informações de diagnóstico em detalhes do evento. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Certificado PKCS emitido com êxito. Examine os detalhes do evento para a ID do dispositivo, ID de usuário, nome da autoridade de certificação, nome do modelo de certificado e impressão digital do certificado relacionado a esse evento. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Falha ao emitir um certificado PKCS. Examine os detalhes do evento para a ID do dispositivo, ID de usuário, nome da autoridade de certificação, nome do modelo de certificado e impressão digital do certificado relacionado a esse evento. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Certificado revogado com êxito. Examine os detalhes do evento para a ID do dispositivo, ID de usuário, nome da autoridade de certificação e número de série do certificado relacionados a esse evento. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Falha ao revogar o certificado. Examine os detalhes do evento para a ID do dispositivo, ID de usuário, nome da autoridade de certificação e número de série do certificado relacionados a esse evento. Para obter informações adicionais, consulte os logs do serviço do do NDES.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | A solicitação ou os dados de revogação do certificado foram carregados com êxito. Examine os detalhes do evento para obter os detalhes de upload. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Falha ao carregar os dados de solicitação ou de revogação do certificado. Examine os detalhes do evento > o estado de carregamento para determinar o ponto de falha.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Solicitação baixada com êxito para assinar um certificado, baixar um certificado de cliente ou revogar um certificado. Examine os detalhes do evento para obter os detalhes de download.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Falha ao baixar a solicitação para assinar um certificado, baixar o certificado do cliente ou revogar um certificado. Examine os detalhes do evento para obter os detalhes de download. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | O ponto de registro de certificado verificou com êxito um desafio do cliente | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Ponto de registro de certificado concluído, mas rejeitou a solicitação. Consulte código de diagnóstico e mensagem para obter mais detalhes. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Falha do ponto de registro de certificado ao verificar um desafio do cliente. Consulte código de diagnóstico e mensagem para obter mais detalhes. Consulte detalhes da mensagem de evento para a ID do dispositivo correspondente ao desafio. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | O ponto de registro de certificado terminou com êxito o processo de notificação e enviou o certificado para o dispositivo cliente. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | O ponto de registro de certificado falhou ao concluir o processo de notificação. Consulte os detalhes da mensagem de evento para obter informações sobre a solicitação. Verifique a conexão entre o servidor NDES e a CA. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Códigos de diagnóstico

| Código de diagnóstico | Nome do diagnóstico | Mensagem de diagnóstico |
| -------------   | -------------   | -------------      |
| 0x00000000 | Êxito  | Êxito |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | A autoridade de certificação não é válida ou está inacessível. Verifique se a autoridade de certificação está disponível e se o servidor pode se comunicar com ela. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | O certificado de autenticação do cliente Symantec não foi encontrado no repositório de certificados local. Consulte o artigo [instalar o certificado de autorização de registro da Symantec](certificates-digicert-configure.md#install-the-digicert-ra-certificate) para obter mais informações.  |
| 0x00000402 | RevokeCert_AccessDenied  | A conta especificada não tem permissões para revogar um certificado da AC. Consulte o campo nome da autoridade de certificação nos detalhes da mensagem de evento para determinar a AC emissora.  |
| 0x00000403 | CertThumbprint_NotFound  | Não foi possível encontrar um certificado que corresponda à sua entrada. Registre o conector de certificado e tente novamente. |
| 0x00000404 | Certificate_NotFound  | Não foi possível encontrar um certificado que corresponda à entrada fornecida. Registre novamente o conector de certificado e tente novamente. |
| 0x00000405 | Certificate_Expired  | Um certificado expirou. Registre novamente o conector de certificado para renovar o certificado e tente novamente. |
| 0x00000408 | CRPSCEPCert_NotFound  | Não foi possível encontrar o certificado de criptografia do CRP. Verifique se o NDES e o conector do Intune estão configurados corretamente. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Não foi possível recuperar o certificado de autenticação. Verifique se o serviço do conector do Intune está configurado corretamente e se o serviço do conector do Intune está em execução. Verifique também se os eventos de download de certificado foram bem-sucedidos. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Falha ao desserializar a solicitação de desafio SCEP. Verifique se o NDES e o conector do Intune estão configurados corretamente. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Solicitação negada devido a um desafio de certificado expirado. O dispositivo cliente pode tentar novamente após obter um novo desafio do servidor de gerenciamento. |
| 0x0FFFFFFFF | Unknown_Error  | Não é possível concluir sua solicitação porque ocorreu um erro no lado do servidor. Tente novamente. |


## <a name="next-steps"></a>Passos seguintes
Para obter assistência adicional, use a [implantação do perfil de certificado SCEP de solução de problemas no guia Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) .
