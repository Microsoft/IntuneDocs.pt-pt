---
title: Crie o perfil Wi-Fi com chave pré-partilhada no Microsoft Intune - Azure / Microsoft Docs
description: Utilize um perfil personalizado para criar um perfil Wi-Fi com uma chave pré-partilhada e obter código XML de exemplo para perfis Android, Windows e perfis Wi-Fi baseados em EAP no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9b56ba1515608afb6c2a0d151f5412711d49e57
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886716"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Utilize um perfil de dispositivo personalizado para criar um perfil Wi-Fi com uma chave pré-partilhada no Intune



As teclas pré-partilhadas (PSK) são normalmente usadas para autenticar utilizadores em redes WiFi ou LANs sem fios. Com o Intune, pode criar um perfil Wi-Fi através de uma chave pré-partilhada. Para criar o perfil, utilize a funcionalidade **Perfis de dispositivos personalizados** no Intune. Este artigo inclui alguns exemplos de como criar um perfil Wi-Fi baseado em EAP.

Esta funcionalidade suporta:

- Administrador do dispositivo Android
- Windows
- Wi-Fi baseado em EAP

> [!IMPORTANT]
> - A utilização de uma chave pré-partilhada com o Windows 10 provoca um erro de reparação a mostrar em Intune. Quando isto acontece, o perfil Wi-Fi é atribuído corretamente ao dispositivo e funciona conforme esperado.
> - Se exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, certifique-se de que o ficheiro está protegido. Como a chave se encontra em texto simples, é sua responsabilidade protegê-la.

## <a name="before-you-begin"></a>Antes de começar

- Poderá ser mais fácil copiar o código de um computador com ligação a essa rede, conforme descrito mais à frente neste artigo.
- Pode adicionar várias redes e chaves, adicionando mais definições de OMA-URI.
- Para iOS, utilize o Apple Configurator numa estação Mac para configurar o perfil.
- O PSK necessita de uma cadeia de 64 dígitos hexadecimais ou uma frase de acesso de 8 a 63 carateres ASCII imprimíveis. Alguns personagens, como o asterisco, não são suportados.

## <a name="create-a-custom-profile"></a>Criar um perfil personalizado

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para a apólice. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é definições de **perfil Wi-Fi Personalizado oMA-URI para dispositivos Android**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolha a sua plataforma.
    - **Tipo de perfil**: Selecione **Personalizado**.

4. Em **Definições,** **selecione Adicionar**. Introduza um novo cenário OMA-URI com as seguintes propriedades:

    1. **Nome**: Introduza um nome para a definição OMA-URI.
    2. **Descrição**: Introduza uma descrição para a definição OMA-URI. Esta definição é opcional, mas recomendada.
    3. **OMA-URI**: Introduza uma das seguintes opções:

        - **Para Android**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **Para Janelas**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > Certifique-se de que inclui o caráter de ponto no início.

        SSID é o SSID para o qual está a criar a política. Por exemplo, se o Wi-Fi for nomeado `Hotspot-1`, introduza `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

    4. **Tipo de dados**: Selecione **string**.

    5. **Valor**: Colar o seu código XML. Veja os [exemplos](#android-or-windows-wi-fi-profile-example) deste artigo. Atualize cada valor para corresponder às suas definições de rede. A secção de comentários do código inclui algumas indicações.

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O seu perfil está na lista de perfis. Em seguida, [atribua este perfil](../device-profile-assign.md) aos seus grupos de utilizadores. Esta política só pode ser atribuída a grupos de utilizadores.

Da próxima vez que cada dispositivo for registado, a política será aplicada e será criado um perfil Wi-Fi no dispositivo. Assim, o dispositivo poderá ligar à rede automaticamente.

## <a name="android-or-windows-wi-fi-profile-example"></a>Exemplo de perfil Android ou Wi-Fi do Windows

O seguinte exemplo inclui o código XML de um perfil Android ou Wi-Fi do Windows. O exemplo é disponibilizado para mostrar o formato correto e indicar mais detalhes. Ele é apenas um exemplo e não foi concebido como uma configuração recomendada para o seu ambiente.

### <a name="what-you-need-to-know"></a>O que tem de saber

- `<protected>false</protected>` tem de ser definido como **falso**. Se estiver definido como **verdadeiro**, poderá fazer com que o dispositivo espere uma palavra-passe encriptada e, em seguida, tente decifrá-la, o que poderá resultar numa falha de ligação.

- `<hex>53534944</hex>` deve estar definido para o valor hexadecimal de `<name><SSID of wifi profile></name>`. Os dispositivos windows 10 podem devolver um erro `x87D1FDE8 Remediation failed` falso, mas o dispositivo ainda contém o perfil.

- XML tem caracteres especiais, como o `&` (ampersand). A utilização de caracteres especiais pode impedir que o XML funcione como esperado. 

### <a name="example"></a>Exemplo

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>Exemplo de perfil Wi-Fi baseado em EAP
O exemplo seguinte inclui o código XML de um perfil de Wi-Fi baseado em EAP: o exemplo é disponibilizado para mostrar o formato correto e indicar mais detalhes. Ele é apenas um exemplo e não foi concebido como uma configuração recomendada para o seu ambiente.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Criar o ficheiro XML a partir de uma ligação Wi-Fi existente

Também pode criar um ficheiro XML a partir de uma ligação Wi-Fi existente. Num computador Windows, utilize os seguintes passos:

1. Crie uma pasta local para os perfis W-Fi exportados, como c:\WiFi.
2. Abra um pedido de comando como administrador (clique à direita `cmd` > **Executar como administrador).**
3. Execute `netsh wlan show profiles`. Os nomes de todos os perfis estão listados.
4. Execute `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. Este comando cria um ficheiro chamado `Wi-Fi-YourProfileName.xml` em c:\Wifi.

    - Se estiver a exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, adicione `key=clear` ao comando:
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` exporta a chave em texto simples, que é obrigado a utilizar com sucesso o perfil.

Depois de ter o ficheiro XML, copiar e colar a sintaxe XML nas definições OMA-URI > Tipo de **dados**. [Criar um perfil personalizado](#create-a-custom-profile) (neste artigo) lista os passos.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` também inclui todos os perfis em formato XML.

## <a name="best-practices"></a>Melhores práticas

- Antes de implementar um perfil de Wi-Fi com PSK, confirme que o dispositivo consegue ligar diretamente ao ponto final.

- Ao rodar as teclas (palavras-passe ou frases-passe), espere tempo de inatividade e planeie as suas implementações. Considere emitir novos perfis de Wi-Fi durante as horas de descanso. Além disso, avisam os utilizadores de que a conectividade pode ser afetada.

- Para uma transição suave, certifique-se de que o dispositivo do utilizador final tem uma ligação alternativa à Internet. Por exemplo, o utilizador final pode mudar para WiFi convidado (ou qualquer outra rede Wi-Fi) ou ter conectividade celular para comunicar com intune. A ligação adicional permite ao utilizador receber atualizações da política quando o Perfil de Wi-Fi empresarial for atualizado no dispositivo.

## <a name="next-steps"></a>Próximos passos

Certifique-se de [atribuir o perfil](device-profile-assign.md)e [monitorizar](device-profile-monitor.md) o seu estado.
