---
title: Troubleshoot e reveja os registos de perfis de dispositivowi-fi no Microsoft Intune - Azure Microsoft Docs
description: Compreenda e problemas problemas de configuração do dispositivo Wi-Fi nos dispositivos Android, iOS/iPadOS e Windows no Microsoft Intune. Reveja os registos e consulte algumas questões comuns e possíveis resoluções.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: db663f96f1e4fe84c506395b98c52956069e5426
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512828"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Perfis de configuração de dispositivowi-fi de resolução de problemas no Microsoft Intune

No Intune, pode criar perfis de configuração do dispositivo que incluam definições de ligação para a sua rede Wi-Fi. Utilize estas definições para ligar os dispositivos Android, iOS/iPadOS e Windows dos utilizadores à rede da organização.

Este artigo mostra como é um perfil Wi-Fi quando se aplica com sucesso aos dispositivos. Também inclui informações de registo, questões comuns, e muito mais. Use este artigo para ajudar a resolver problemas com os seus perfis Wi-Fi.

Para obter mais informações sobre os perfis Wi-Fi em Intune, consulte [Adicionar e utilizar as definições de Wi-Fi nos seus dispositivos](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

Os exemplos deste artigo utilizam a autenticação de certificado SCEP para os perfis Intune. Também assume que os perfis Trust Root e SCEP funcionam corretamente no dispositivo.

## <a name="android"></a>Android

Nesta secção, passamos pela experiência final do utilizador ao instalar os perfis de configuração num dispositivo Android.

### <a name="end-user-experience-example"></a>Exemplo de experiência de utilizador final

Este cenário utiliza um dispositivo Nokia 6.1. Antes de o perfil Wi-Fi ser instalado no dispositivo, instale os perfis Trust Root e SCEP.

1. Os utilizadores finais recebem uma notificação para instalar o perfil do certificado Raiz Fidedigna:

    > [!div class="mx-imgBorder"]
    > ![notificação da aplicação Portal da Empresa de Amostras no Android para instalar](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png) de perfil de certificado de raiz fidedigna

2. A próxima notificação solicita a instalação do perfil de certificado SCEP:

    > [!div class="mx-imgBorder"]
    > ![Notificação da aplicação Portal da Empresa de Amostras  no Android para instalar o perfil de certificado SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Ao utilizar um dispositivo Android gerido por administrador de dispositivos, pode haver vários certificados listados. Quando um perfil de certificado é revogado ou removido, o certificado permanece no dispositivo. Neste cenário, selecione o certificado mais recente. Normalmente é o último certificado mostrado na lista.
    >
    > Esta situação não ocorre nos dispositivos Android Enterprise e Samsung Knox. Para mais informações, consulte [Gerir dispositivos](../enrollment/android-enterprise-overview.md) de perfil de trabalho Android e [remover certificados SCEP e PKCS](../protect/remove-certificates.md#android-knox-devices).

3. Em seguida, os utilizadores recebem uma notificação para instalar o perfil Wi-Fi:

    > [!div class="mx-imgBorder"]
    > ![Notificação da aplicação Portal da Empresa de Amostras  no Android para instalar o perfil de certificado SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Quando concluída, a ligação Wi-Fi é mostrada como uma rede guardada:

    > [!div class="mx-imgBorder"]
    > ![ligação Wi-Fi mostra como uma rede salva](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Rever registos de aplicativos do Portal da Empresa

No Android, o ficheiro **Omadmlog.log** detalha as atividades do perfil Wi-Fi quando está instalado no dispositivo. Pode ter até cinco ficheiros de registo omadmlog. Certifique-se de obter o carimbo de tempo da última sincronização, pois irá ajudá-lo a encontrar as entradas de registo relacionadas.

No exemplo seguinte, utilize a [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) para ler os registos e procure "wifimgr":

> [!div class="mx-imgBorder"]
> ![ligação Wi-Fi mostra como uma rede salva](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

O seguinte registo mostra os resultados da sua pesquisa e mostra o perfil Wi-Fi aplicado com sucesso:

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

## <a name="iosipados"></a>iOS/iPadOS

Após a instalação do perfil Wi-Fi no dispositivo, é mostrado no Perfil de **Gestão:**

> [!div class="mx-imgBorder"]
> perfil de gestão ![no dispositivo iOS/iPadOS em Intune](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![ligação Wi-Fi mostra como uma rede Wi-Fi no dispositivo iOS/iPadOS em Intune](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-iosipados-console-and-device-logs"></a>Reveja os registos de consolas iOS/iPadOS e dispositivos

Nos dispositivos iOS/iPadOS, o registo de aplicações do Portal da Empresa não inclui informações sobre perfis Wi-Fi. Para ver detalhes de instalação dos seus perfis Wi-Fi, utilize os Registos consola/dispositivo:

1. Ligue o dispositivo iOS/iPadOS ao Mac. Vá a **Aplicações** > **Utilities**e abra a aplicação Consola.
2. Em **ação,** **selecione Incluir Mensagens de Informação** e incluir **Mensagens de Depuração:**

    > [!div class="mx-imgBorder"]
    > ![incluir mensagens de informação e incluir mensagens de depuração na aplicação de consola iOS/iPadOS](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Reproduza o cenário e guarde os registos para um ficheiro de texto:

    1. Selecione todas as mensagens no ecrã atual: **Editar** > **Selecione Tudo**.
    2. Copiar as mensagens: **Editar** > **Copiar**.
    3. Colhe os dados de registo num editor de texto e guarde o ficheiro.

4. Procure no ficheiro de registo guardado para ver informações detalhadas. Quando o perfil instala com sucesso, a sua saída é semelhante ao seguinte registo:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Depois de instalado o perfil Wi-Fi no dispositivo, aceda a **Definições** > **Contas** > Trabalho de **Acesso ou escola**. Selecione a sua conta > **Informação:**

> [!div class="mx-imgBorder"]
> ![Aceder ao trabalho ou à escola e selecionar Informações sobre dispositivos Windows](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

Em **Áreas geridas pela Microsoft,** o **Wi-Fi** é mostrado:

> [!div class="mx-imgBorder"]
> ![Nas áreas geridas pela Microsoft, veja que o Wi-Fi está listado no Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Para ver a ligação Wi-Fi, vá a **Definições** > **Rede e Internet**  > **Wi-Fi:**

> [!div class="mx-imgBorder"]
> ![No Windows, veja a ligação Wi-Fi como uma rede conhecida em definições](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Rever registos de espectadores de eventos

Nos dispositivos Windows, os detalhes sobre os perfis Wi-Fi estão registados no Visualizador de Eventos:

1. Abra a aplicação **Espectador de Eventos.**
2. No menu **'Ver',** selecione **Registos Desalíticos e Debug**.
3. Expandir registos de **aplicações e serviços** > **Microsoft** > **Windows** > **Dispositivos Gestão-Empresa-Provedor de Diagnóstico** > **Admin**

A sua saída é semelhante aos seguintes registos:

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

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Edição 1: O perfil Wi-Fi não está implantado no dispositivo

- Confirme que o perfil Wi-Fi é atribuído ao grupo correto:

    1. No centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Dispositivos** > perfis de **configuração**.
    2. Selecione o seu perfil > **Atribuições**. Confirme que os grupos selecionados estão corretos.
    3. No Endpoint Manager, selecione **Troubleshooting + Suporte**. Reveja a informação de **Atribuição.**

- No Endpoint Manager, selecione **Troubleshooting + Suporte**. Confirme que o dispositivo pode sincronizar com Intune verificando o **último check-in a** tempo.

- Se o perfil Wi-Fi estiver ligado aos perfis Trust Root e SCEP, confirme que ambos os perfis estão implantados no dispositivo. O perfil Wi-Fi tem uma dependência destes perfis.

- No Windows 10 e dispositivos mais recentes, reveja o registo de Informações de Diagnóstico do MDM:

  1. Vá a **Definições** > **Contas** > **Trabalho de acesso ou escola.**
  2. Selecione o seu trabalho ou conta escolar > **Info**.
  3. Na parte inferior da página **Definições,** selecione **Criar relatório**.
  4. Abre-se uma janela que mostra o caminho para os ficheiros de registo. Selecione **Exportação**.
  5. Vá ao caminho `\Users\Public\Documents\MDMDiagnostics` e veja o relatório:

      > [!div class="mx-imgBorder"]
      > ![Amostra de Informação de Diagnóstico do MDM que mostra a configuração do perfil Wi-Fi nos dispositivos do Windows 10](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Para mais informações, consulte [diagnosticar falhas de MDM no Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- Nos dispositivos Android, se os perfis Trust Root e SCEP não estiverem instalados no dispositivo, vê a seguinte entrada no ficheiro Omadmlog da aplicação Portal da Empresa:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Quando os perfis Trust Root e SCEP estão no dispositivo Android e em conformidade, o perfil Wi-Fi pode não estar no dispositivo. Este problema acontece quando o fornecedor de **CertificateSelector** da aplicação Portal da Empresa não encontra um certificado que corresponda aos critérios especificados. Os critérios específicos podem estar no Modelo de Certificado ou no perfil SCEP.

    Se o certificado de correspondência não for encontrado, os certificados do dispositivo não estão instalados. O perfil Wi-Fi não é aplicado porque não tem o certificado correto. Neste cenário, vê a seguinte entrada no ficheiro Omadmlog da aplicação Portal da Empresa:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    O registo da amostra seguinte mostra que os certificados estão excluídos porque **foram** especificados os critérios de utilização da chave estendida (EKU). Mas os certificados atribuídos ao dispositivo não têm o EKU:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    A amostra seguinte mostra que o perfil SCEP inseriu no EKU **para qualquer fim.** Mas, não está inscrito no Modelo de Certificado na autoridade do certificado (CA). Para corrigir o problema, adicione a opção **Qualquer Propósito** ao modelo de certificado. Ou remover a opção **Qualquer Propósito** do perfil SCEP.

    > [!div class="mx-imgBorder"]
    > ![No Android, adicione qualquer propósito ao modelo de certificado na autoridade do certificado](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![No Android, adicione qualquer propósito ao perfil de configuração de certificado SCEP em Intune](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Confirme que todos os certificados necessários na cadeia de certificados completos estão no dispositivo Android. Caso contrário, o perfil Wi-Fi não pode ser instalado no dispositivo. Para mais informações, consulte a autoridade de [certificados intermédios desaparecida](https://developer.android.com/training/articles/security-ssl#MissingCa) (abre o site do Android).
  - Filtrar o Omadmlog com palavras-chave para procurar informações, como qual o certificado utilizado no perfil Wi-Fi e se o perfil for aplicado com sucesso.

    Por exemplo, utilize [cmTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) para ler os registos. Utilize a cadeia de pesquisa para filtrar "wifimgr":

    > [!div class="mx-imgBorder"]
    > ![Filter CMTrace para procurar perfis de configuração WiFiMgr em dispositivos Android](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    A saída é semelhante ao seguinte tronco:

    > [!div class="mx-imgBorder"]
    > ![amostra de saída de log CMTrace que mostra o perfil de configuração WiFi Intune aplicado com sucesso em dispositivos](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Se vir um erro no registo, copie o carimbo de tempo do erro e desfile o registo. Em seguida, use a opção "encontrar" com o carimbo de tempo para ver o que aconteceu antes do erro.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Edição 2: O perfil Wi-Fi está implantado no dispositivo, mas o dispositivo não pode ligar-se à rede

Tipicamente, esta questão é causada por algo fora de Intune. As seguintes tarefas podem ajudá-lo a compreender e resolver problemas de conectividade:

- Ligue-se manualmente à rede utilizando um certificado com os mesmos critérios que está no perfil Wi-Fi.

  Se conseguir ligar, veja as propriedades do certificado na ligação manual. Em seguida, atualize o perfil Wi-Fi Intune com as mesmas propriedades do certificado.
- Os erros de conectividade são normalmente registados no registo do servidor Radius. Por exemplo, deve mostrar se o dispositivo tentou ligar-se ao perfil Wi-Fi.

## <a name="need-more-help"></a>Preciso de mais ajuda

- Utilize os fóruns de [utilizador Intune](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) ou [obtenha suporte da Microsoft](../fundamentals/get-support.md).

- Para obter mais informações sobre perfis Wi-Fi no Microsoft Intune, consulte os seguintes artigos:

  - Adicione as definições de Wi-Fi para dispositivos que executam [Android](wi-fi-settings-android.md), [iOS/iPadOS,](wi-fi-settings-ios.md)e [Windows 10 e mais tarde](wi-fi-settings-windows.md).
  - [Dica de suporte - Como configurar NDES para implementações de certificados SCEP em Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Resolução de problemas a implementação do perfil do [certificado SCEP](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) e a [configuração NDES](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- Para obter as últimas novidades, informações e dicas tecnológicas, consulte os blogs oficiais:
  - [Blog da Microsoft Intune Support Team](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Blog de Mobilidade e Segurança Empresarial da Microsoft](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Próximos passos

[Monitorize os seus perfis.](device-profile-monitor.md)
