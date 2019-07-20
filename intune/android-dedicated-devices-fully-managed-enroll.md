---
title: Registrar dispositivos Android Enterprise dedicados ou dispositivos totalmente gerenciados no Intune
titleSuffix: Microsoft Intune
description: Saiba como registrar dispositivos Android Enterprise dedicados ou dispositivos totalmente gerenciados no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c13ebdd6cf908a62c99d4c81443c94ce6a07d8e
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353835"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices-preview"></a>Registrar seus dispositivos Android Enterprise dedicados ou dispositivos totalmente gerenciados (versão prévia)

Depois de configurar seus [dispositivos Android Enterprise dedicados](android-kiosk-enroll.md) ou [dispositivos totalmente gerenciados](android-fully-managed-enroll.md) no Intune, você pode registrar os dispositivos. A maneira como você registra seus dispositivos Android Enterprise depende do sistema operacional.

| Método de inscrição | Versão mínima do sistema operacional Android para dispositivos dedicados e totalmente gerenciados |
| ----- | ----- |
| Comunicação de Proximidade | 5.1 |
| Entrada de token | 6.0 |
| Código QR | 7.0 |
| Zero Touch  | 8,0\* |

\*Em fabricantes participantes.

## <a name="enroll-by-using-near-field-communication-nfc"></a>Inscrever com NFC (Comunicação de Proximidade)

Para dispositivos que dão suporte a NFC, você pode provisionar seus dispositivos criando uma marca NFC especialmente formatada. Pode utilizar a sua própria aplicação ou qualquer ferramenta de criação de etiquetas NFC. Para obter mais informações, consulte [registro de dispositivo empresarial Android baseado em C com o Microsoft Intune e a](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) [documentação da API de gerenciamento do Android do Google](https://developers.google.com/android/management/provision-device#nfc_method).

## <a name="enroll-by-using-a-token"></a>Inscrever com um token

Em dispositivos Android 6 e posteriores, pode utilizar o token para inscrever o dispositivo. O Android 6,1 e versões posteriores também podem aproveitar a verificação de código QR ao usar o método de registro **AFW # setup** .

1. Ligue o seu dispositivo apagado.
2. No ecrã **Bem-vindo**, selecione o seu idioma.
3. Ligue a sua rede **Wi-Fi** e, em seguida, selecione **SEGUINTE**.
4. Aceite os termos e condições da Google e selecione **SEGUINTE**.
5. No ecrã de início de sessão do Google, introduza **afw#setup** em vez de uma conta do Gmail e, em seguida, selecione **SEGUINTE**.
6. Selecione **INSTALAR** para a aplicação **Android Device Policy**.
7. Continue a instalação desta política.  Alguns dispositivos podem exigir a aceitação de termos adicionais.
8. No ecrã **Inscrever este dispositivo**, permita que o seu dispositivo leia o código QR ou opte por introduzir manualmente o token.
9. Siga as instruções no ecrã para concluir a inscrição.

## <a name="enroll-by-using-a-qr-code"></a>Inscrever com um código QR

Em dispositivos Android 7 e posteriores, pode ler o código QR do perfil de inscrição para inscrever o dispositivo.

> [!Note]
> O zoom do browser pode fazer com que os dispositivos não consigam ler códigos QR. Aumentar o zoom do browser resolve o problema.

1. Para iniciar a leitura do código QR no dispositivo Android, toque múltiplas vezes no primeiro ecrã que vir após apagar.
2. Em dispositivos Android 7 e 8, ser-lhe-á pedido para instalar um leitor de QR. Os dispositivos Android 9 e posteriores já têm um leitor de QR instalado.
3. Utilize o leitor de QR para ler o código QR do perfil de inscrição e, em seguida, siga as instruções no ecrã para concluir a inscrição.

## <a name="enroll-by-using-google-zero-touch"></a>Inscrever com o sistema Zero Touch da Google

Para utilizar o sistema Zero Touch da Google, o dispositivo tem de o suportar e estar associado a um fornecedor que faça parte do serviço.  Para obter mais informações, veja o [site do programa Zero Touch da Google](https://www.android.com/enterprise/management/zero-touch/).

1. Crie uma nova Configuração na consola do Zero Touch.
2. Selecione **Microsoft Intune** na lista pendente de DPC da EMM.
3. Na consola do Zero Touch da Google, copie/cole o seguinte JSON no campo de extras da DPC. Substitua a cadeia *YourEnrollmentToken* pelo token de inscrição que criou como parte do seu perfil de inscrição. Certifique-se de que coloca o token de inscrição entre aspas.

    ```json
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

