---
title: Utilização de perfis de certificadoS SCEP para fornecer certificados com microsoft Intune / Microsoft Docs
description: Problemas de resolução da utilização do SCEP por dispositivos para solicitar certificados de utilização com o Intune, incluindo a comunicação de dispositivos para NDES, NDES para as autoridades de certificação, e do Conector de Certificado Intune para o serviço Intune.
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
ms.openlocfilehash: ae7ffe5a8c20aa7edd67853ff86ef9e28cf2d175
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913181"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Visão geral para resolução de perfis de certificadoS SCEP com microsoft Intune

A utilização de perfis de certificados de protocolo de inscrição simples de certificados (SCEP) pode ser um desafio para a resolução de problemas em Intune. Este artigo é uma visão geral que pode ajudá-lo a resolver problemas por:

- Explicando a arquitetura e o fluxo de comunicação do processo SCEP
- Ajudando-o a reduzir onde existe um problema nesse fluxo de comunicação
- Identificação dos ficheiros de registo chave referenciados em artigos subsequentes para perfis de certificados de resolução de problemas

As informações neste e nos artigos de resolução de problemas do certificado SCEP aplicam-se à utilização de perfis de certificadoS SCEP com dispositivos Android, iOS/iPad e Windows. Informações semelhantes para o macOS não estão disponíveis neste momento.

Para resolver problemas o Serviço de Inscrição de Dispositivos de Rede (NDES), consulte os seguintes artigos de support.microsoft.com:

- [Verifique a configuração nDES no local para obter certificados SCEP em Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Configuração nDES de resolução de problemas para utilização com perfis de certificados Microsoft Intune]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

Antes de prosseguir, certifique-se de que preencheu os [pré-requisitos para a utilização](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates)de perfis de certificadoS SCEP , incluindo a implementação de um certificado de raiz através de um perfil de certificado fidedigno.

## <a name="scep-communication-flow-overview"></a>Visão geral do fluxo de comunicação SCEP

O gráfico seguinte demonstra uma visão geral básica do processo de comunicação scep em Intune.

![Fluxo de perfil de certificado SCEP](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. Implementar um perfil de [certificado SCEP](troubleshoot-scep-certificate-profile-deployment.md). Intune gera uma cadeia de desafios, que requer um utilizador específico, finalidade de certificado e tipo de certificado.

2. [Dispositivo para comunicação do servidor NDES](troubleshoot-scep-certificate-device-to-ndes.md). O dispositivo utiliza o URI para NDES a partir do perfil para contactar o servidor NDES para que possa apresentar um desafio.

3. [NDES para comunicação](troubleshoot-scep-certificate-ndes-policy-module.md)de módulos políticos. O NDES reencaminha o desafio para o módulo de política do Conector de Certificado Intune no servidor, que valida o pedido.

4. [NDES à autoridade de certificação.](troubleshoot-scep-certificate-ndes-policy-module.md) A NDES aprova pedidos válidos para emitir um certificado à Autoridade de Certificação (CA).

5. [Entrega do certificado ao dispositivo.](troubleshoot-scep-certificate-delivery.md) O certificado é entregue no dispositivo.

6. [Reportagem da implantação ao Intune](troubleshoot-scep-certificate-reporting.md). O Conector de Certificado Intune informa o evento de emissão do certificado ao Intune.

## <a name="log-files"></a>Ficheiros de registo

Para identificar problemas para o fluxo de trabalho de comunicação e fornecimento de certificados, reveja os ficheiros de registo da infraestrutura do Servidor e dos dispositivos. As secções posteriores para resolução de problemas dos perfis de certificadoS SCEP referem-se aos ficheiros de registo referenciados nesta secção.

- [Registos de Infraestruturas e Servidores](#logs-for-on-premises-infrastructure)

Os registos do dispositivo dependem da plataforma do dispositivo:  

- [iOS e iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>Registos para infraestruturas no local
  
A infraestrutura no local que suporta a utilização de perfis de certificadoS SCEP para implementação de certificados inclui o Conector de Certificado Intune da Microsoft, o NDES que funciona num Servidor Windows e a autoridade de certificação.

Os ficheiros de registo para estas funções incluem o Windows Event Viewer, as consolas de Certificados e vários ficheiros de registo específicos do Conector de CertificadoIno, NDES ou outras funções e operações que fazem parte da infraestrutura no local.

A lista seguinte inclui registos ou consolas referenciados nos artigos subsequentes de resolução de problemas da SCEP. 

- **NDESConnector_date_time.svclog:**

  Este registo mostra a comunicação do Conector de Certificado Intune da Microsoft para o serviço de nuvem Intune. Pode utilizar a ferramenta de [visualização](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) de rastreio de serviço para visualizar este ficheiro de registo.

  Chave de registo relacionada: *HKLM\SW\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Localização: No servidor que acolhe NDES a *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\*

- **CertificateRegistrationPoint_date_time.svclog:**

  Este registo mostra o módulo de política NDES que recebe e verifica os pedidos de certificado. Pode utilizar a ferramenta de [visualização](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) de rastreio de serviço para visualizar este ficheiro de registo.

  Localização: No servidor que acolhe NDES a *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\logs\*

- **NDESPlugin.log**:

  Este registo mostra a aprovação dos pedidos de certificado para o Ponto de Registo do Certificado e a verificação resultante desses pedidos.

  Localização: No servidor que acolhe NDES a *%program_files%\Microsoft Intune\NDESPolicyModule\logs*

- **Registos IIS:**

  Os registos iIS mostram os pedidos de certificado saem do NDES.

  Localização: No servidor que acolhe O NDES em *c:\inetpub\logs\LogFiles\W3SVC1*

- **Registo de aplicações do Windows:**

  Este registo é útil na investigação de problemas do IIS, como o conjunto de aplicações SCEP.

  Localização: No servidor que acolhe NDES: Executar **eventvwr.msc** para abrir o Windows Event Viewer




### <a name="logs-for-android-devices"></a>Registos para dispositivos Android

Para dispositivos que executam o Android, utilize o ficheiro de registo de aplicativos **Do Portal da Empresa Android,** **OMADM.log**. Antes de recolher e rever os registos, certifique-se de que a [Verbose Logging](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md) está ativada e, em seguida, reproduzir o problema.

Para recolher os registos OMADM de um dispositivo, consulte [registos de upload e e-mail utilizando um cabo USB](/intune-user-help/send-logs-to-your-it-admin-using-cable-android.md).

Também pode enviar e enviar registos de [e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android.md#upload-and-email-logs-from-microsoft-intune-app) para suporte.

### <a name="logs-for-ios-and-ipados-devices"></a>Registos para dispositivos iOS e iPadOS

Para dispositivos que executam iOS ou iPadOS, utilize registos de depuração e **Xcode** que funcionam num computador Mac:

1. Ligue o dispositivo iOS ao Mac e, em seguida, vá às **Aplicações** > **Utilities** para abrir a aplicação Consola. 

2. Em **ação,** **selecione Incluir Mensagens de Informação** e incluir **Mensagens de Depuração**.

   ![Selecione opções de registo](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Reproduza o problema e, em seguida, guarde os registos para um ficheiro de texto:
   1. **Selecione Editar** > **Selecione Tudo** para selecionar todas as mensagens no ecrã atual e, em seguida, selecione **Editar** > **Copiar** para copiar as mensagens para a área de redação. 
   2. Abra a aplicação TextEdit, colá os registos copiados num novo ficheiro de texto e, em seguida, guarde o ficheiro.


O registo do Portal da Empresa para dispositivos iOS e iPadOS não contém informações sobre perfis de certificadoS SCEP.

### <a name="logs-for-windows-devices"></a>Registos para dispositivos Windows

Para dispositivos que executam o Windows, utilize os registos do Windows Event para diagnosticar problemas de inscrição ou gestão de dispositivos para dispositivos que gere com o Intune.

No dispositivo, aabra os registos de **aplicações e serviços** do **Observador** >  > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**

![Registos de eventos windows](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>Próximos passos

Revisão [da implementação dos perfis de certificados SCEP](troubleshoot-scep-certificate-profile-deployment.md) 
