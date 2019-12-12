---
title: Usar logs do StageNow em dispositivos Android pretas no Microsoft Intune-Azure | Microsoft Docs
description: Consulte problemas comuns e resoluções ao usar o StageNow em dispositivos Android com Microsoft Intune. Além disso, saiba como obter logs e veja exemplos de como ler os logs para obter êxito ou erros.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ed93c86d3fbe7ed7a6ac5d4b1a3494fb55f2bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506985"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Solucione problemas e veja possíveis problemas em dispositivos Android pretas no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

No Microsoft Intune, você pode usar o [MX (pretas Mobility Extensions) para gerenciar dispositivos Android pretas](android-zebra-mx-overview.md). Ao usar dispositivos pretas, você cria perfis no StageNow para gerenciar as configurações e carregá-las no Intune. O Intune usa o aplicativo StageNow para aplicar as configurações nos dispositivos. O aplicativo StageNow também cria um arquivo de log detalhado no dispositivo que é usado para solucionar problemas.

Esta funcionalidade aplica-se a:

- Android

Por exemplo, você cria um perfil no StageNow para configurar um dispositivo. Quando você cria o perfil StageNow, a última etapa gera um arquivo para testar o perfil. Você consome esse arquivo com o aplicativo StageNow no dispositivo.

Em outro exemplo, você cria um perfil no StageNow e o testa. No Intune, você adiciona o perfil StageNow e, em seguida, atribui-o aos seus dispositivos pretas. Ao verificar o status do perfil atribuído, o perfil mostra um status de alto nível.

Em ambos os casos, você pode obter mais detalhes do arquivo de log StageNow, que é salvo no dispositivo sempre que um perfil StageNow se aplica.

Alguns problemas não estão relacionados ao conteúdo do perfil StageNow e não são refletidos nos logs.

Este artigo mostra como ler os logs do StageNow e lista alguns outros problemas em potencial com dispositivos pretas que podem não ser refletidos nos logs.

[Usar e gerenciar dispositivos pretas com o pretas Mobility Extensions](android-zebra-mx-overview.md) tem mais informações sobre esse recurso.

## <a name="get-the-logs"></a>Obter os logs

### <a name="use-the-stagenow-app-on-the-device"></a>Usar o aplicativo StageNow no dispositivo
Quando você testa um perfil diretamente usando o StageNow em seu computador no, em vez de usar [o Intune para implantar o perfil](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), o aplicativo StageNow no dispositivo salva os logs do teste. Para obter o arquivo de log, use a opção **mais (...)** no aplicativo StageNow no dispositivo.

### <a name="get-logs-using-android-debug-bridge"></a>Obter logs usando Android Debug Bridge
Para obter logs depois que o perfil já estiver implantado com o Intune, conecte o dispositivo a um computador com o [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) (abre o site do Android).

No dispositivo, os logs são salvos em `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Obter logs de email
Para obter logs depois que o perfil já estiver implantado com o Intune, os usuários finais poderão enviar por email os logs usando um aplicativo de email no dispositivo. No dispositivo pretas, abra o aplicativo Portal da Empresa e [envie os logs](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). Usar o recurso de logs de envio também cria uma ID de incidente PowerLift, que você pode referenciar se entrar em contato com o suporte da Microsoft.

## <a name="read-the-logs"></a>Ler os logs

Ao examinar os logs, há um erro sempre que você vir a marca de `<characteristic-error>`. Os detalhes do erro são gravados na marca de `<parm-error>` > Propriedade `desc`.

## <a name="error-types"></a>Tipos de erro

Os dispositivos pretas incluem níveis diferentes de relatório de erros:

- O CSP não tem suporte no dispositivo. Por exemplo, o dispositivo não é um dispositivo de celular e não tem um Gerenciador de celular.
- A versão MX ou OSX não corresponde. Cada CSP tem controle de versão. Para obter uma matriz de suporte completo, consulte a [documentação do pretas](http://techdocs.zebra.com/mx/) (abre o site da pretas).
- O dispositivo relata outro problema ou erro.

## <a name="examples"></a>Exemplos

Por exemplo, você tem o seguinte perfil de entrada:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

No log, o XML é idêntico à entrada. Essa saída correspondente significa que o perfil foi aplicado com êxito ao dispositivo sem erros:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Em outro exemplo, você tem a seguinte entrada:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

O log mostra um erro, pois ele contém uma marca `<characteristic-error>`. Nesse cenário, o perfil tentou instalar um pacote Android (APK) que não existe no caminho fornecido:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Outros problemas potenciais com dispositivos pretas

Esta seção lista outros possíveis problemas que você pode ver ao usar dispositivos pretas com o administrador do dispositivo. Esses problemas não são relatados nos logs do StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView está desatualizado

Quando dispositivos mais antigos entram usando o aplicativo Portal da Empresa, os usuários podem ver uma mensagem informando que o componente WebView do sistema está desatualizado e precisa ser atualizado. Se o dispositivo tiver Google Play instalado, conecte-o à Internet e verifique se há atualizações. Se o dispositivo não tiver Google Play instalado, obtenha a versão atualizada do componente e aplique-o aos dispositivos. Ou atualize para o sistema operacional mais recente do dispositivo emitido pelo pretas.

### <a name="management-actions-take-a-long-time"></a>As ações de gerenciamento levam muito tempo

Se os serviços do Google Play não estiverem disponíveis, algumas tarefas levarão até 8 horas para serem concluídas. As [limitações do aplicativo portal da empresa do Intune para Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (abre outro site da Microsoft) podem ser um bom recurso.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Suspeita de dispositivo suspeito" mostra no Intune

Esse erro significa que o Intune suspeita que um dispositivo Android não pretas está relatando seu modelo e fabricante como um dispositivo pretas.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Portal da Empresa aplicativo é mais antigo que a versão mínima necessária

O Intune pode atualizar a versão mínima necessária do aplicativo Portal da Empresa. Se Google Play não estiver instalado no dispositivo, o aplicativo Portal da Empresa não será atualizado automaticamente. Se a versão mínima necessária for mais nova do que a versão instalada, o aplicativo Portal da Empresa parará de funcionar. Atualize para o aplicativo Portal da Empresa mais recente usando [Sideload em dispositivos pretas](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Próximos passos

[Quadros de discussão do pretas](https://developer.zebra.com/community/home/discussions) (abre o site da pretas)

[Usar e gerenciar dispositivos pretas com as extensões de mobilidade do pretas no Intune](android-zebra-mx-overview.md)
