---
title: Problemas de resolução do módulo de política do Conector de Certificado Intune da Microsoft  Microsoft Docs
description: Problemas de resolução do funcionamento do módulo de política NDES quando o módulo processa um pedido de certificado quando utiliza perfis de certificado SCEP para implementar certificados com Intune.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913185"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Resolução de problemas do módulo de política NDES no Microsoft Intune

As informações deste artigo podem ajudá-lo a validar o funcionamento do módulo de política do Serviço de Inscrição de Dispositivos de Rede (NDES) que se instala com o Conector de Certificado Intune da Microsoft. Quando o NDES recebe um pedido de certificado, reencaminha o pedido para o módulo de política, que valida o pedido como válido para o dispositivo. Após a validação, a NDES contacta a autoridade do certificado (CA) para solicitar o certificado em nome do dispositivo.

Este artigo aplica-se tanto ao passo 3 como ao passo 4 do fluxo de trabalho de [comunicação scep](troubleshoot-scep-certificate-profiles.md).

## <a name="ndes-communication-to-the-policy-module"></a>Comunicação NDES ao módulo de política

Depois de receber o pedido de certificado de um dispositivo, o NDES valida esse pedido com o Intune através do módulo de política que instala com o Conector de Certificado Intune da Microsoft. Estas entradas referem-se ao ponto de registo do *certificado.*

**Entradas de log que indicam sucesso:**

Para confirmar que o pedido de validação é submetido ao módulo, procure uma entrada que se assemelhe aos seguintes exemplos nos registos do servidor NDES:

- **Registos IIS:**

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **Registo NDESPlugin**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  O exemplo seguinte indica uma validação bem sucedida do pedido de impugnação dos dispositivos e que o NDES pode agora contactar a AC:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**Quando os indicadores de sucesso não estão presentes:**

Se não encontrar estas entradas, comece por rever a orientação de resolução de problemas para o dispositivo para a comunicação do [servidor NDES](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors).

Se a informação nesse artigo não o ajudar a resolver o problema, as seguintes são entradas adicionais que podem indicar problemas.

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log contém um erro 12175

Quando o registo contém um erro 12175 semelhante ao seguinte, pode haver um problema com o certificado SSL:

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

Os navegadores e navegadores modernos em dispositivos móveis ignoram o *Nome Comum* num certificado SSL se houver *Nomes Alternativos sujeitos presentes.*

**Resolução**: Emita o certificado SSL do servidor web com os seguintes atributos para *Nome Comum* e *Nome Alternativo sujeito,* e, em seguida, ligá-lo à porta 443 no IIS:

  - **Nome do assunto**  
    CN = nome de servidor externo
  - **Nome alternativo do sujeito**  
     Nome = nome do servidor externo  
     Nome DNS = nome do servidor interno

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log contém um erro 403 – Proibido: O acesso é negado"

Quando os seguintes registos contenham um erro 403 semelhante ao seguinte, o certificado de cliente pode não ser fidedigno ou inválido:

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**Registo IIS:**

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Este problema ocorre se houver certificados ca intermédios na loja de certificados trusted Root Certification Authorities do servidor NDES.

Se um certificado tiver o mesmo *emitido* e *emitido por* valores, é um certificado de raiz. Caso contrário, é um certificado intermédio.

**Resolução**: Para corrigir o problema, identificar e remover os certificados de CA intermédios do certificado trust Root Certification Authorities.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log indica que o desafio devolve falso

Quando o resultado do desafio for **falso,** verifique se o *CertificateRegistrationPoint.svclog* está a verificar se há erros. Por exemplo, pode ver um erro de "certificado de assinatura não poderia ser recuperado" que se assemelha à seguinte entrada:

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Resolução**: No servidor onde o conector está instalado, abra o Editor de Registo, localize a chave de registo `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` e verifique se o valor do Certificado de Assinatura existe.

Se este valor não existir, reinicie o Serviço de Conector Intune em serviços.msc e verifique se o valor aparece no registo. Se o valor ainda está em falta, é muitas vezes devido a problemas de conectividade de rede entre o servidor que o NDES e o serviço Intune.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES aprova o pedido de emissão do certificado

Após uma validação bem sucedida pelo ponto de registo do certificado (o módulo de política), o NDES passa o pedido de certificado à AC em nome do dispositivo.

**Entradas de log que indicam sucesso:**

- **Registo NDESPlugin**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **Registos IIS:**

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**Quando os indicadores de sucesso não estão presentes:**

Se não vir as entradas que indicam sucesso, siga estes passos:

1. Procure problemas que estejam registados no *CertificateRegistrationPoint.svclog* quando o ponto de registo do certificado verificar o desafio. Procure as entradas entre as seguintes linhas:

   - O pedido de verificação começou.
   - CheckRequest Terminado com estatuto Falso

2. Abra o MMC da Autoridade de Certificação na CA e selecione **Pedidos Falhados** para procurar erros que ajudem a identificar um problema. A seguinte imagem é um exemplo:

   ![Exemplo de um pedido falhado](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. Reveja o registo do evento de aplicação na AC para obter erros. Normalmente pode ver erros que correspondem ao que vê nos **Pedidos Falhados** do passo anterior. A seguinte imagem é um exemplo:

   ![Reveja o registo de candidaturas](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>Próximos passos

Se o módulo de política NDES validar o pedido e o pedido for reencaminhado para a autoridade do certificado, o próximo passo é rever a entrega do [certificado ao dispositivo](troubleshoot-scep-certificate-delivery.md).
