---
title: Inscrever dispositivos de quiosque do Android Enterprise no Intune
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos de quiosque do Android Enterprise no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cd6aee30a88906c3f6ae078e338732589d88a5f0
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909138"
---
# <a name="set-up-enrollment-of-android-enterprise-kiosk-devices"></a>Configurar a inscrição de dispositivos de quiosque do Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O sistema operativo Android suporta dispositivos estilo quiosque com o seu conjunto de soluções COSU (Corporate-Owned, Single-Use [Propriedade da Empresa, Utilização Exclusiva]). Estes dispositivos são utilizados para um único objetivo, como sinalética digital, impressão de bilhetes, gestão de inventário, entre outros. Os administradores bloqueiam a utilização de um conjunto limitado de aplicações e ligações Web num dispositivo. Além disso, também impede os utilizadores de adicionarem outras aplicações ou de efetuarem outras ações no dispositivo.

O Intune ajuda-o a implementar aplicações e definições em dispositivos de quiosque Android. Para obter detalhes específicos sobre o Android Enterprise, veja [Android enterprise requirements (Requisitos empresariais do Android)](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Os dispositivos que gerir desta forma são inscritos no Intune sem uma conta de utilizador e não estão associados a nenhum utilizador final. Estes dispositivos não são para utilização pessoal nem para aplicações que tenham um requisito forte para dados de conta específicos do utilizador, como o Outlook ou o Gmail.

## <a name="device-requirements"></a>Requisitos de dispositivo

Os dispositivos têm de cumprir estes requisitos para serem geridos como um dispositivo de quiosque do Android Enterprise:

- Versão do SO Android 5.1 e posterior.
- Os dispositivos têm de executar uma distribuição do Android com conectividade aos GMS (Serviços Google Mobile). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

## <a name="set-up-android-kiosk-management"></a>Configurar a gestão de quiosques Android

Para configurar a gestão de quiosques Android, siga estes passos:

1. Para se preparar para gerir dispositivos móveis, tem de [definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**](mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
3. [Crie um perfil de inscrição](#create-an-enrollment-profile).
4. [Crie um grupo de dispositivos](#create-a-device-group).
5. [Inscreva os dispositivos de quiosque](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>Criar um perfil de inscrição

Tem de criar um perfil de inscrição para poder inscrever os seus dispositivos de quiosque. Depois de criar o perfil, o mesmo fornece-lhe um token de inscrição (cadeia aleatória) e um código QR. Consoante o SO Android e a versão do dispositivo, pode utilizar o token ou o código QR para [inscrever o dispositivo de quiosque](#enroll-the-kiosk-devices).

1. Aceda ao [Portal do Intune](https://portal.azure.com) e selecione **Inscrição de dispositivos** > **Inscrição Android** > **Inscrição de quiosque e dispositivos de tarefas**.
2. Selecione **Criar** e preencha os campos obrigatórios.
    - **Nome**: escreva o nome que irá utilizar quando atribuir o perfil ao grupo de dispositivos dinâmico.
    - **Data de expiração do token**: a data em que o token expira. A Google impõe um máximo de 30 dias.
3. Escolha **Criar** para guardar o perfil.

### <a name="create-a-device-group"></a>Criar um grupo de dispositivos

Pode direcionar aplicações e políticas para grupos de dispositivos dinâmicos ou atribuídos. Pode configurar grupos de dispositivos do AAD dinâmicos para povoar automaticamente os dispositivos inscritos com um perfil de inscrição específico ao seguir estes passos:

1. Aceda ao [Portal do Intune](https://portal.azure.com) e selecione **Grupos** > **Todos os grupos** > **Novo grupo**.
2. No painel **Grupo**, preencha os campos obrigatórios da seguinte forma:
    - **Tipo de grupo**: segurança
    - **Nome do grupo**: escreva um nome intuitivo (como Dispositivos da fábrica 1)
    - **Tipo de associação**: dispositivo dinâmico
3. Selecione **Adicionar consulta dinâmica**.
4. No painel **Regras de associação de grupo dinâmica**, preencha os campos da seguinte forma:
    - **Adicionar regra de associação dinâmica**: regra simples
    - **Adicionar dispositivos onde**: enrollmentProfileName
    - Na caixa do meio, selecione **Correspondência**.
    - No último campo, introduza o nome do perfil de inscrição que criou anteriormente.
5. Selecione **Adicionar consulta** > **Criar**.

### <a name="replace-or-remove-tokens"></a>Substituir ou remover tokens

Pode substituir ou remover tokens e códigos QR.

- **Substituir token**: pode gerar um novo token/código QR quando o antigo estiver prestes a expirar.
- **Revogar token**: pode expirar imediatamente o token/código QR. Quando o fizer, o token/código QR deixa de ser utilizável. Pode utilizar esta opção se:
    - partilhar acidentalmente o token/código QR com um terceiro não autorizado
    - concluir todas as inscrições e deixar de precisar do token/código QR

Substituir ou revogar um token/código QR não terá efeito em dispositivos que já tenham sido inscritos.

1. Aceda ao [Portal do Intune](https://portal.azure.com) e selecione **Inscrição de dispositivos** > **Inscrição Android** > **Inscrição de quiosque e dispositivos de tarefas**.
2. Selecione o perfil com o qual pretende trabalhar.
3. Selecione **Token**.
4. Para substituir o token, selecione **Substituir token**.
5. Para revogar o token, selecione **Revogar token**.

## <a name="enroll-the-kiosk-devices"></a>Inscrever os dispositivos de quiosque

Depois de criar o perfil de inscrição e o grupo de dispositivos dinâmico, pode inscrever os seus dispositivos de quiosque. A forma como inscreve os seus dispositivos Android depende do sistema operativo.

| Método de inscrição | Versão mínima do SO Android suportada |
| ----- | ----- |
| Comunicação de Proximidade | 5.1 |
| Entrada de token | 6.0 |
| Código QR | 7.0 |
| Zero Touch | 8.0 em fabricantes participantes |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Inscrever com NFC (Comunicação de Proximidade)

Em dispositivos Android 5.1 e posteriores que suportem NFC, pode aprovisionar os seus dispositivos ao criar uma etiqueta NFC especialmente formatada. Pode utilizar a sua própria aplicação ou qualquer ferramenta de criação de etiquetas NFC. Para obter mais informações, veja a [Documentação da API de gestão do Android da Google](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Inscrever com um token

Em dispositivos Android 6 e posteriores, pode utilizar o token para inscrever o dispositivo.

1. Ative o seu dispositivo com reposição de fábrica.
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

1. Para iniciar a leitura do código QR no dispositivo Android, toque múltiplas vezes no primeiro ecrã que vir após uma reposição de fábrica.
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

## <a name="managing-apps-on-android-kiosk-devices"></a>Gerir aplicações em dispositivos de quiosque Android

Apenas as aplicações com o Tipo de atribuição [definido como Obrigatório](apps-deploy.md#to-assign-an-app) podem ser instaladas em dispositivos de quiosque Android. As aplicações são instaladas a partir da Google Play Store Gerida da mesma forma que os dispositivos com perfil de trabalho do Android.

As aplicações são atualizadas automaticamente em dispositivos geridos quando o programador da aplicação publica uma atualização na Google Play Store.

Para remover uma aplicação de dispositivos de quiosque Android, pode seguir um dos seguintes passos:
-   Elimine a implementação da aplicação obrigatória.
-   Crie uma implementação de desinstalação para a aplicação.


## <a name="next-steps"></a>Próximos passos
- [Implementar aplicações de quiosque Android](apps-deploy.md)
- [Adicionar políticas de configuração de quiosques Android](device-profiles.md)