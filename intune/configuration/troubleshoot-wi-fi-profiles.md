---
title: Solucionar problemas e examinar os logs de perfil do dispositivo Wi-Fi no Microsoft Intune-Azure | Microsoft Docs
description: Entender e solucionar problemas de perfil de configuração de dispositivo Wi-Fi em dispositivos Android, iOS e Windows no Microsoft Intune. Examine os logs e veja alguns problemas comuns e possíveis resoluções.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f471e7f4db7ddce89d8956474822375c684944
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547972"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Solucionar problemas de perfis de configuração de dispositivo Wi-Fi no Microsoft Intune

No Intune, você pode criar perfis de configuração de dispositivo que incluem configurações de conexão para sua rede WiFi. Use essas configurações para conectar dispositivos Android, iOS e Windows dos usuários à rede da organização.

Este artigo mostra a aparência de um perfil de Wi-Fi quando ele se aplica com êxito aos dispositivos. Ele também inclui informações de log, problemas comuns e muito mais. Use este artigo para ajudar a solucionar os perfis de Wi-Fi.

Para obter mais informações sobre perfis Wi-Fi no Intune, consulte [Adicionar e usar configurações de Wi-Fi em seus dispositivos](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

Os exemplos neste artigo usam a autenticação de certificado SCEP para os perfis do Intune. Ele também pressupõe que os perfis de raiz confiável e SCEP funcionem corretamente no dispositivo.

## <a name="android"></a>Android

Nesta seção, vamos percorrer a experiência do usuário final ao instalar os perfis de configuração em um dispositivo Android.

### <a name="end-user-experience-example"></a>Exemplo de experiência do usuário final

Esse cenário usa um dispositivo Nokia 6,1. Antes de o perfil de Wi-Fi ser instalado no dispositivo, instale os perfis raiz confiável e SCEP.

1. Os usuários finais recebem uma notificação para instalar o perfil de certificado raiz confiável:

    > [!div class="mx-imgBorder"]
    > ![exemplo de notificação de aplicativo Portal da Empresa no Android para instalar o perfil de certificado raiz confiável](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. A próxima notificação solicita a instalação do perfil de certificado SCEP:

    > [!div class="mx-imgBorder"]
    > ![exemplo de notificação de aplicativo Portal da Empresa no Android para instalar o perfil de certificado SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Ao usar um dispositivo Android gerenciado pelo administrador do dispositivo, pode haver vários certificados listados. Quando um perfil de certificado é revogado ou removido, o certificado permanece no dispositivo. Nesse cenário, selecione o certificado mais recente. Normalmente, é o último certificado mostrado na lista.
    >
    > Essa situação não ocorre em dispositivos Android Enterprise e Samsung Knox. Para obter mais informações, consulte [gerenciar dispositivos de perfil de trabalho do Android](../enrollment/android-enterprise-overview.md) e remover os [certificados SCEP e PKCS](../protect/remove-certificates.md#android-knox-devices).

3. Em seguida, os usuários recebem uma notificação para instalar o perfil Wi-Fi:

    > [!div class="mx-imgBorder"]
    > ![exemplo de notificação de aplicativo Portal da Empresa no Android para instalar o perfil de certificado SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Ao concluir, a conexão Wi-Fi é mostrada como uma rede salva:

    > [!div class="mx-imgBorder"]
    > ![conexão Wi-Fi é mostrada como uma rede salva](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Examinar Portal da Empresa logs do aplicativo

No Android, o arquivo **Omadmlog. log** detalha as atividades do perfil Wi-Fi quando ele está instalado no dispositivo. Você pode ter até cinco arquivos de log do Omadmlog. Certifique-se de obter o carimbo de data/hora da última sincronização, pois isso o ajudará a encontrar as entradas de log relacionadas.

No exemplo a seguir, use [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) para ler os logs e pesquise por "wifimgr":

> [!div class="mx-imgBorder"]
> ![conexão Wi-Fi é mostrada como uma rede salva](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

O log a seguir mostra os resultados da pesquisa e mostra o perfil de Wi-Fi aplicado com êxito:

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

Depois que o perfil de Wi-Fi é instalado no dispositivo, ele é mostrado no **perfil de gerenciamento**:

> [!div class="mx-imgBorder"]
> ![perfil de gerenciamento no dispositivo iOS](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![conexão Wi-Fi é mostrada como uma rede Wi-Fi no dispositivo iOS](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>Examinar os logs do console e do dispositivo do iOS

Em dispositivos iOS, o log do aplicativo Portal da Empresa não inclui informações sobre perfis Wi-Fi. Para ver os detalhes de instalação dos seus perfis de Wi-Fi, use os logs de console/dispositivo:

1. Conecte o dispositivo iOS ao Mac. Vá para **aplicativos** > **utilitários**e abra o aplicativo de console.
2. Em **ação**, selecione **incluir mensagens de informações** e **incluir mensagens de depuração**:

    > [!div class="mx-imgBorder"]
    > ![incluir mensagens de informações e incluir mensagens de depuração no aplicativo de console do iOS](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Reproduzir o cenário e salvar os logs em um arquivo de texto:

    1. Selecione todas as mensagens na tela atual: **editar** > **selecionar tudo**.
    2. Copie as mensagens: **editar** > **cópia**.
    3. Cole os dados de log em um editor de texto e salve o arquivo.

4. Pesquise o arquivo de log salvo para ver informações detalhadas. Quando o perfil é instalado com êxito, sua saída é semelhante ao seguinte log:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Depois que o perfil de Wi-Fi for instalado no dispositivo, vá para **configurações** > **contas** > **acessar trabalho ou escola**. Selecione sua conta > **informações**:

> [!div class="mx-imgBorder"]
> ![acessar o trabalho ou a escola e selecionar informações no dispositivo Windows](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

Em **áreas gerenciadas pela Microsoft, a** **WiFi** é mostrada:

> [!div class="mx-imgBorder"]
> ![em áreas gerenciadas pela Microsoft, veja se o WiFi está listado no Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Para ver a conexão Wi-Fi, vá para **configurações** > **rede & Internet**  > **Wi-Fi**:

> [!div class="mx-imgBorder"]
> ![no Windows, consulte a conexão Wi-Fi como uma rede conhecida em configurações](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Examinar logs do Visualizador de eventos

Em dispositivos Windows, os detalhes sobre perfis Wi-Fi são registrados no Visualizador de Eventos:

1. Abra o aplicativo **Visualizador de eventos** .
2. No menu **Exibir** , selecione **Mostrar logs analíticos e de depuração**.
3. Expanda **logs de aplicativos e serviços** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **admin**

Sua saída semelhante aos seguintes logs:

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Problemas comuns

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Problema 1: o perfil de Wi-Fi não é implantado no dispositivo

- Confirme se o perfil de Wi-Fi está atribuído ao grupo correto:

    1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **dispositivos** > **perfis de configuração**.
    2. Selecione seu perfil > **atribuições**. Confirme se os grupos selecionados estão corretos.
    3. No Gerenciador de pontos de extremidade, selecione **solução de problemas + suporte**. Examine as informações de **atribuições** .

- No Gerenciador de pontos de extremidade, selecione **solução de problemas + suporte**. Confirme se o dispositivo pode sincronizar com o Intune verificando a hora da **última verificação** .

- Se o perfil de Wi-Fi estiver vinculado aos perfis raiz confiável e SCEP, confirme se ambos os perfis estão implantados no dispositivo. O perfil de Wi-Fi tem uma dependência desses perfis.

- Em dispositivos Windows 10 e mais recentes, examine o log de informações de diagnóstico do MDM:

  1. Acesse **configurações** > **contas** > **acessar trabalho ou escola**.
  2. Selecione sua conta corporativa ou de estudante > **informações**.
  3. Na parte inferior da página **configurações** , selecione **criar relatório**.
  4. Uma janela é aberta e mostra o caminho para os arquivos de log. Selecione **Export** (Exportar).
  5. Vá para o caminho de `\Users\Public\Documents\MDMDiagnostics` e exiba o relatório:

      > [!div class="mx-imgBorder"]
      > ![informações de diagnóstico de MDM de exemplo que mostram a configuração de perfil de WiFi em dispositivos Windows 10](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Para obter mais informações, consulte [diagnosticar falhas de MDM no Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- Em dispositivos Android, se os perfis raiz confiável e SCEP não estiverem instalados no dispositivo, você verá a seguinte entrada no arquivo de Omadmlog do aplicativo de Portal da Empresa:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Quando os perfis raiz confiável e SCEP estão no dispositivo Android e estão em conformidade, o perfil Wi-Fi pode não estar no dispositivo. Esse problema ocorre quando o provedor **CertificateSelector** do aplicativo portal da empresa não encontra um certificado que corresponda aos critérios especificados. Os critérios específicos podem estar no modelo de certificado ou no perfil SCEP.

    Se o certificado correspondente não for encontrado, os certificados no dispositivo não serão instalados. O perfil de Wi-Fi não foi aplicado porque não tem o certificado correto. Nesse cenário, você verá a seguinte entrada no arquivo Portal da Empresa do aplicativo Omadmlog:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    O log de exemplo a seguir mostra os certificados sendo excluídos porque foram especificados os critérios de EKU (uso estendido de chave) de **qualquer finalidade** . No entanto, os certificados atribuídos ao dispositivo não têm esse EKU:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    O exemplo a seguir mostra que o perfil SCEP inseriu o EKU de **qualquer finalidade** . Mas não é inserido no modelo de certificado na autoridade de certificação (CA). Para corrigir o problema, adicione a opção **qualquer finalidade** ao modelo de certificado. Ou remova a opção **qualquer finalidade** do perfil SCEP.

    > [!div class="mx-imgBorder"]
    > ![no Android, adicione qualquer finalidade ao modelo de certificado na autoridade de certificação](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![no Android, adicione qualquer finalidade ao perfil de configuração de certificado SCEP no Intune](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Confirme se todos os certificados necessários na cadeia de certificados completa estão no dispositivo Android. Caso contrário, o perfil de Wi-Fi não poderá ser instalado no dispositivo. Para obter mais informações, consulte [autoridade de certificado intermediária ausente](https://developer.android.com/training/articles/security-ssl#MissingCa) (abre o site do Android).
  - Filtre Omadmlog com palavras-chave para procurar informações, como qual certificado é usado no perfil de Wi-Fi e se o perfil foi aplicado com êxito.

    Por exemplo, use [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) para ler os logs. Use a cadeia de caracteres de pesquisa para filtrar "wifimgr":

    > [!div class="mx-imgBorder"]
    > ![filtrar CMTrace para procurar perfis de configuração do WiFiMgr em dispositivos Android](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    A saída é semelhante ao seguinte log:

    > [!div class="mx-imgBorder"]
    > ![exemplo de saída de log do CMTrace que mostra o perfil de configuração do Intune do Wi-Fi aplicado com êxito nos dispositivos](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Se você vir um erro no log, copie o carimbo de data/hora do erro e desfiltre o log. Em seguida, use a opção "localizar" com o carimbo de data/hora para ver o que aconteceu logo antes do erro.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Problema 2: o perfil de Wi-Fi é implantado no dispositivo, mas o dispositivo não pode se conectar à rede

Normalmente, esse problema é causado por algo fora do Intune. As seguintes tarefas podem ajudá-lo a entender e solucionar problemas de conectividade:

- Conecte-se manualmente à rede usando um certificado com os mesmos critérios que estão no perfil de Wi-Fi.

  Se você puder se conectar, examine as propriedades do certificado na conexão manual. Em seguida, atualize o perfil de Wi-Fi do Intune com as mesmas propriedades de certificado.
- Geralmente, os erros de conectividade são registrados no log do servidor RADIUS. Por exemplo, ele deve mostrar se o dispositivo tentou se conectar com o perfil de Wi-Fi.

## <a name="need-more-help"></a>Precisa de mais ajuda

- Use os [fóruns de usuário do Intune](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) ou [Obtenha suporte da Microsoft](../fundamentals/get-support.md).

- Para obter mais informações sobre perfis Wi-Fi no Microsoft Intune, consulte os seguintes artigos:

  - Adicione configurações de Wi-Fi para dispositivos que executam [Android](wi-fi-settings-android.md), [Ios](wi-fi-settings-ios.md)e [Windows 10 e posterior](wi-fi-settings-windows.md).
  - [Dica de suporte-como configurar o NDES para implantações de certificado SCEP no Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Solucionar problemas de [implantação do perfil de certificado SCEP](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) e [configuração do NDES](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- Para obter as últimas notícias, informações e dicas técnicas, consulte os Blogs oficiais:
  - [Blog da equipe de suporte do Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Blog do Microsoft Enterprise Mobility e segurança](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Próximos passos

[Monitore seus perfis](device-profile-monitor.md).
