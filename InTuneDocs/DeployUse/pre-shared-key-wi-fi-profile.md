---
title: Wi-Fi com PSK | Microsoft Intune
description: "Utilize a Configuração Personalizada para criar um perfil Wi-Fi com uma chave pré-partilhada."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f11f752f6c38736a2dfa5875050f50bd86bae4
ms.openlocfilehash: 14e43dadc0d7bc20238ec87447f311fdc864d891



---
# Criar um perfil Wi-Fi com uma chave pré-partilhada
Eis como utilizar a **Configuração Personalizada** do Intune para criar um perfil Wi-Fi com uma chave pré-partilhada. Este tópico também contém um exemplo de como criar um perfil Wi-Fi baseado em EAP.

> [!NOTE]
-   Poderá considerar mais fácil copiar o código de um computador com ligação à rede, conforme descrito abaixo.
- Para Android, tem também a opção de utilizar este [Android PSK Generator](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) fornecido por Johnathon Biersack.
-   Pode adicionar várias redes e chaves, adicionando mais definições de OMA-URI.
-  Para iOS, utilize o Apple Configurator numa estação Mac para configurar o perfil. Em alternativa, utilize este [iOS PSK Mobile Config Generator](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) fornecido por Johnathon Biersack.


1.  Para criar um perfil Wi-Fi com uma chave pré-partilhada para Android ou Windows, ou um perfil Wi-Fi baseado em EAP, quando criar uma política, escolha **Configuração Personalizada** para essa plataforma de dispositivo, em vez de um perfil Wi-Fi.

2.  Forneça um nome e uma descrição.
3.  Adicione uma nova definição de OMA-URI:

   a.   Introduza um nome para esta definição de rede Wi-Fi.

   b.   Introduza uma descrição da definição de OMA-URI ou deixe em branco.

   c.   **Tipo de Dados**: definido como "String(XML)"

   d.   **OMA-URI**:

    - **Para Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **Para Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Certifique-se de que inclui o caráter de ponto no início.

    SSID é o SSID para o qual está a criar a política. Por exemplo,
    `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **Campo de Valor** é onde cola o código XML. Segue-se um exemplo. Cada valor deve ser adaptado às suas definições de rede. Consulte a secção de comentários do código para obter algumas indicações.
4. Escolha **OK**, guarde e, em seguida, implemente a política.

    > [!NOTE]
    > Esta política só pode ser implementada em grupos de utilizadores.

Da próxima vez que cada dispositivo for registado, a política será aplicada e será criado um perfil Wi-Fi no dispositivo. O dispositivo poderá ligar à rede automaticamente.
## Perfil Android ou Wi-Fi do Windows

Segue-se um exemplo do código XML de um perfil Android ou Wi-Fi do Windows:

> [!IMPORTANT]
> 
> `<protected>false</protected>`tem de ser definido como **falso**, pois **verdadeiro** pode fazer com que o dispositivo espere uma palavra-passe encriptada e, em seguida, tente decifrá-la, o que pode resultar numa falha de ligação.
> 
>  `<hex>53534944</hex>` deve ser definido para o valor hexadecimal de `<name><SSID of wifi profile></name>`.
>  Os dispositivos com Windows 10 podem devolver um erro *0x87D1FDE8 A remediação falhou* falso, mas continuarão a ser aprovisionados com o perfil.

    <!--
    <Name of wifi profile> = Name of profile
    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
    <nonBroadcast><true/false></nonBroadcast>
    <Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
    <Type of encryption> = Type of encryption used by the network
    <protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
    <password> = Password to connect to the network
    <hex>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
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
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial>MyPassword</keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>

## Perfil Wi-Fi baseado em EAP
Segue-se um exemplo do código XML de um perfil Wi-Fi baseado em EAP:

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

## Criar o ficheiro XML a partir de uma ligação Wi-Fi existente
Também pode criar um ficheiro XML a partir de uma ligação Wi-Fi existente:
1. Num computador ligado ou que tenha ligado recentemente à rede sem fios, abra a seguinte pasta: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}.

    É melhor utilizar um computador que não tenha ligado a muitas redes sem fios, uma vez que tem de procurar em cada perfil para encontrar a correta.
3.     Procure nos ficheiros XML para localizar o ficheiro com o nome correto.
4.     Depois de localizar o ficheiro XML correto, copie e cole o código XML no campo de Dados da página de definições de OMA-URI.

## Implementar a política

1.  Na área de trabalho **Política**, selecione a que pretende implementar e escolha **Gerir a Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - Selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, escolha **Adicionar** &gt; **OK**.

    -   **Para fechar a caixa de diálogo sem implementar a política** - escolha **Cancelar**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

### Consulte também
[Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)



<!--HONumber=Sep16_HO3-->


