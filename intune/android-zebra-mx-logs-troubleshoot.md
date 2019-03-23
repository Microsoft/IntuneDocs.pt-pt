---
title: Registos de utilização StageNow em dispositivos das riscas das Android no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver problemas e resoluções comuns ao utilizar StageNow em dispositivos Android com o Microsoft Intune. Além disso, saiba como obter registos e ver exemplos de como ler os registos para o êxito ou erros.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5edc528abf5c3cb58200e2d0511fac3220cfad11
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58395254"
---
# <a name="use-stagenow-logs-to-troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Utilizar StageNow registos para resolver e ver problemas potenciais em dispositivos das riscas das Android no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

No Microsoft Intune, pode utilizar [ **as riscas das mobilidade extensões (MX)** para gerir as riscas das Android dispositivos](android-zebra-mx-overview.md). Ao utilizar dispositivos as riscas das, criar perfis no StageNow para gerir as definições e carregá-los para o Intune. O Intune utiliza a aplicação de StageNow para aplicar as definições nos dispositivos. A aplicação de StageNow também cria um ficheiro de registo detalhado no dispositivo que é utilizado para resolver.

Esta funcionalidade aplica-se a:

- Android

Por exemplo, criar um perfil no StageNow para configurar um dispositivo. Quando cria o perfil de StageNow, a última etapa gera um ficheiro para testar o perfil. Consumir este ficheiro com a aplicação de StageNow no dispositivo.

Noutro exemplo, criar um perfil no StageNow e testá-lo. No Intune, adicionar o perfil de StageNow e, em seguida, atribuí-la para os seus dispositivos as riscas das. Ao verificar o estado do perfil atribuído, o perfil mostra um Estado de alto nível. Pretende obter mais detalhes.

Em ambos os casos, pode obter mais detalhes do ficheiro de registo StageNow, que é guardado no dispositivo sempre que um perfil de StageNow aplica-se.

Este artigo mostra-lhe como ler os logs de StageNow e lista alguns possíveis problemas com dispositivos as riscas das.

[Utilizar e gerir as riscas das dispositivos com as riscas das extensões de mobilidade](android-zebra-mx-overview.md) tem mais informações sobre esta funcionalidade.

## <a name="read-the-logs"></a>Leia os registos

Ao examinar os registos, existe um erro sempre que visualizar a `<characteristic-error>` marca. Detalhes do erro são escritos para o `<parm-error>` tag > `desc` propriedade.

## <a name="error-types"></a>Tipos de erros

Os dispositivos das riscas das incluem diferentes níveis de comunicação de erros:

- O CSP não é suportado no dispositivo. Por exemplo, o dispositivo não é um dispositivo móvel e não tem um Gerenciador de celular.
- A versão MX ou OSX é sem correspondência. Cada CSP tem a mesma versão. Para uma matriz de suporte completo, consulte [documentação das riscas das](http://techdocs.zebra.com/mx/) (abre o site da web das riscas das).
- O dispositivo comunica outro problema ou erro.

## <a name="examples"></a>Exemplos

Por exemplo, tem o seguinte perfil de entrada:

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

O registo, o XML é idêntico de entrada. Este resultado correspondente significa que o perfil aplicado com êxito para o dispositivo sem erros:

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

Noutro exemplo, tem a seguinte entrada:

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

O registo mostra um erro, porque contém um `<characteristic-error>` marca. Neste cenário, o perfil tentou instalar um pacote de Android (ficheiro. APK) que não existe no caminho especificado:

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

## <a name="potential-issues-with-zebra-devices"></a>Potenciais problemas com dispositivos as riscas das

Esta secção lista os possíveis problemas que poderão ocorrer ao utilizar dispositivos das riscas com o administrador de dispositivos.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView está desatualizada

Dispositivos mais antigos que iniciar sessão com a aplicação Portal da empresa, utilizadores poderão ver uma mensagem que o componente System WebView está desatualizado e precisa atualizado. Se o dispositivo tiver o Google Play instalado, ligá-la à internet e procurar atualizações. Se o dispositivo não tiver instalado o Google Play, obter a versão atualizada do componente e aplicá-la para os dispositivos. Ou, atualize para o dispositivo mais recente sistema operacional emitido pelas riscas das.

### <a name="management-actions-take-a-long-time"></a>Ações de gestão demoram muito tempo

Se os serviços do Google Play não estão disponíveis, algumas tarefas demorar até 8 horas a concluir. [Aplicação do Portal de limitações da empresa do Intune para Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (abre-se outro web site da Microsoft) pode ser um bom recurso.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Dispositivo spoofing suspeito" mostra no Intune

Este erro significa que o Intune suspeita de que um não - as riscas das dispositivo Android está a comunicar seu modelo e fabricante como um dispositivo das riscas das.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Aplicação Portal da empresa é anterior à versão mínima necessária

Atualizar a versão mínima necessária da aplicação Portal da empresa o Intune. Se o Google Play não estiver instalado no dispositivo, a aplicação Portal da empresa não é atualizada automaticamente. Se o mínimo necessário de versão é mais recente do que a versão instalada, a aplicação Portal da empresa deixa de funcionar. Atualização para a mais recente através de aplicação de Portal da empresa [sideload em dispositivos as riscas das](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Passos Seguintes

[Quadros de discussão as riscas das](https://developer.zebra.com/community/home/discussions) (abre o site da web das riscas das)

[Utilizar e gerir as riscas das dispositivos com as riscas das extensões de mobilidade no Intune](android-zebra-mx-overview.md)
