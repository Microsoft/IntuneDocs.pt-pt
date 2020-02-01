---
title: Entrega de certificados de resolução de problemas a dispositivos quando utiliza SCEP com microsoft Intune / Microsoft Docs
description: Problemas atiram a entrega de um certificado a um dispositivo da AC ao utilizar perfis de certificadoS SCEP com Intune para implementar certificados.
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913197"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Resolução de problemas na entrega de certificados provisionados pela SCEP a dispositivos no Microsoft Intune

Utilize as informações deste artigo para o ajudar a investigar a entrega de certificados aos dispositivos quando utilizar o Protocolo de Inscrição de Certificados Simples (SCEP) para fornecer certificados em Intune. Depois de o servidor do Serviço de Inscrição de Dispositivos de Rede (NDES) receber o certificado solicitado para um dispositivo da autoridade de certificação (CA), passa esse certificado de volta para o dispositivo.

Este artigo aplica-se à etapa 5 do fluxo de trabalho de comunicação do [SCEP;](troubleshoot-scep-certificate-profiles.md) entrega do certificado ao dispositivo que apresentou o pedido de certificado.

## <a name="review-the-certification-authority"></a>Rever a autoridade de certificação

Quando a AC emitir o certificado, verá uma entrada semelhante ao seguinte exemplo na AC:

![Exemplo de certificados emitidos](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Reveja o dispositivo

### <a name="android"></a>Android

Para dispositivos matriculados pelo administrador do dispositivo, verá uma notificação semelhante à seguinte imagem, o que o leva a instalar o certificado:

![Notificação Android](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Para Android Enterprise ou Samsung Knox, a instalação do certificado é automática e silenciosa.

Para ver um certificado instalado no Android, utilize uma aplicação de visualização de certificados de terceiros.

Também pode rever o [log OMADM](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)dos dispositivos . Procure entradas que se assemelhem às seguintes, que são registadas quando os certificados instalam:

**Certificado de raiz:**

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**Certificado previsto através do SCEP**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS e iPadOS

No dispositivo iOS ou iPadOS, pode visualizar o certificado no perfil de Gestão de Dispositivos. Faça uma perfuração para ver detalhes sobre os certificados instalados.

![certificado iOS](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

Também pode encontrar entradas que se assemelham ao seguinte no [registo de depuração do iOS:](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

No dispositivo Windows, verifique se o certificado foi entregue:

- Corra **eventvwr.msc** para abrir o Espectador de Eventos. Aceda a Registos de **Aplicações e Serviços** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin** e procure o **Evento 39**. Este Evento deve ter uma descrição geral de: **SCEP: Certificado instalado com sucesso.**

   ![Evento 39 no registo de aplicações do Windows](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Para visualizar o certificado no dispositivo, faça a **certmgr.msc** para abrir os certificados MMC e verificar se os certificados raiz e SCEP estão instalados corretamente no dispositivo na loja pessoal:

   1. Vá a **Certificados (computador local)**  > Autoridades de **Certificação de Raiz Fidedignas** > **Certificados,** e verifique se o certificado de raiz da sua CA está presente. Os valores *para emitidos para* e *emitidos por* serão os mesmos.
   2. Nos Certificados MMC, vá a **Certificados – Utilizador Atual** > **Certificados**de > **Pessoais,** e verifique se o certificado solicitado está presente, com *emitido por* igual ao nome da AC.

## <a name="troubleshoot-failures"></a>Solucionar problemas de falhas

### <a name="android"></a>Android

Para resolver este passo, reveja os erros que estão registados no registo DeMA Da OMA.

### <a name="ios-and-ipados"></a>iOS e iPadOS

Para resolver este passo, reveja os erros que estão registados no registo de depuração dos dispositivos.

### <a name="windows"></a>Windows

Para problemas com problemas com o certificado não estar instalado no dispositivo, procure no registo do Windows Event erros que sugiram problemas:

- No dispositivo, execute **eventvwr.msc** para abrir o Espectador de Eventos e, em seguida, vá a Registos de **Aplicações e Serviços** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**.

Os erros com a entrega e instalação do certificado no dispositivo estão tipicamente relacionados com as operações do Windows e não com o Intune.

## <a name="next-steps"></a>Próximos passos

Quando o certificado se implanta com sucesso no dispositivo, mas intune não reporta sucesso, veja o [NDES a reportar.](troubleshoot-scep-certificate-reporting.md)
