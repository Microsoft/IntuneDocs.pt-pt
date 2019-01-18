---
title: Inscrever dispositivos Android de dedicado ou totalmente gerido de dispositivos no Intune
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android enterprise dedicado ou dispositivos de fulluy gerido no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 9f9f95c42be252e0b2be515344e01a1d93e2cc6c
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387096"
---
# <a name="enroll-your-android-dedicated-devices-or-fully-managed-devices-preview"></a>Inscrever os dispositivos dedicados Android ou totalmente geridos dispositivos (pré-visualização)

Depois que tiver configurado a sua [dispositivos dedicados do Android](android-kiosk-enroll.md) ou [dispositivos totalmente geridos](android-fully-managed-enroll.md) no Intune, pode inscrever os dispositivos. A forma como inscreve os seus dispositivos Android depende do sistema operativo.

| Método de inscrição | Versão mínima do SO Android para dispositivos dedicados | Versão mínima do SO Android para dispositivos totalmente geridos |
| ----- | ----- | ----- |
| Comunicação de Proximidade | 5.1 | 6.0 |
| Entrada de token | 6.0 | 6.0 |
| Código QR | 7.0 | 7.0 |
| Zero Touch  | 8.0\* | 8.0\* |

\* No fabricantes de participantes.

### <a name="enroll-by-using-near-field-communication-nfc"></a>Inscrever com NFC (Comunicação de Proximidade)

Para dispositivos que suportam o NFC, pode aprovisionar os seus dispositivos através da criação de uma etiqueta NFC formatada de modo especial. Pode utilizar a sua própria aplicação ou qualquer ferramenta de criação de etiquetas NFC. Para obter mais informações, consulte [inscrição de dispositivos com base em C Android Enterprise com o Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) e [documentação de API de gestão de Android da Google](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Inscrever com um token

Em dispositivos Android 6 e posteriores, pode utilizar o token para inscrever o dispositivo. O Android 6.1 e versões posteriores também podem tirar partido da leitura de códigos QR ao utilizar o método de inscrição **aft#setup**.

1. Ligue o seu dispositivo apagado.
2. No ecrã **Bem-vindo**, selecione o seu idioma.
3. Ligue a sua rede **Wi-Fi** e, em seguida, selecione **SEGUINTE**.
4. Aceite os termos e condições da Google e selecione **SEGUINTE**.
5. No ecrã de início de sessão do Google, introduza **afw#setup** em vez de uma conta do Gmail e, em seguida, selecione **SEGUINTE**.
6. Selecione **INSTALAR** para a aplicação **Android Device Policy**.
7. Continue a instalação desta política.  Alguns dispositivos podem exigir a aceitação de termos adicionais. 
8. No ecrã **Inscrever este dispositivo**, permita que o seu dispositivo leia o código QR ou opte por introduzir manualmente o token.
9. Siga as instruções no ecrã para concluir a inscrição. 

### <a name="enroll-by-using-a-qr-code"></a>Inscrever com um código QR

Em dispositivos Android 7 e posteriores, pode ler o código QR do perfil de inscrição para inscrever o dispositivo.

> [!Note]
> O zoom do browser pode fazer com que os dispositivos não consigam ler códigos QR. Aumentar o zoom do browser resolve o problema.

1. Para iniciar a leitura do código QR no dispositivo Android, toque múltiplas vezes no primeiro ecrã que vir após apagar.
2. Em dispositivos Android 7 e 8, ser-lhe-á pedido para instalar um leitor de QR. Os dispositivos Android 9 e posteriores já têm um leitor de QR instalado.
3. Utilize o leitor de QR para ler o código QR do perfil de inscrição e, em seguida, siga as instruções no ecrã para concluir a inscrição.

### <a name="enroll-by-using-google-zero-touch"></a>Inscrever com o sistema Zero Touch da Google

Para utilizar o sistema Zero Touch da Google, o dispositivo tem de o suportar e estar associado a um fornecedor que faça parte do serviço.  Para obter mais informações, veja o [site do programa Zero Touch da Google](https://www.android.com/enterprise/management/zero-touch/). 

1. Crie uma nova Configuração na consola do Zero Touch.
2. Selecione **Microsoft Intune** na lista pendente de DPC da EMM.
3. Na consola do Zero Touch da Google, copie/cole o seguinte JSON no campo de extras da DPC. Substitua a cadeia *YourEnrollmentToken* pelo token de inscrição que criou como parte do seu perfil de inscrição. Certifique-se de que coloca o token de inscrição entre aspas.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Escolha **Aplicar**.


## <a name="next-steps"></a>Passos Seguintes
- [Implementar aplicações Android](apps-deploy.md)
- [Adicionar políticas de configuração para Android](device-profiles.md)

