---
title: "Criar um perfil Wi-Fi com uma chave pré-partilhada"
titleSuffix: Microsoft Intune
description: "Utilize um perfil personalizado do Intune para criar um perfil Wi-Fi com uma chave pré-partilhada."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8229ac82e6854d75f569b7bbf04dd2f5e14856c7
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2018
---
# <a name="use-a-custom-device-profile-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>Utilizar um perfil de dispositivo personalizado para criar um perfil de Wi-Fi com uma chave pré-partilhada
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Veja como utilizar os **Perfis de dispositivos personalizados** do Intune para criar um perfil Wi-Fi com uma chave pré-partilhada. Este tópico também contém um exemplo de como criar um perfil Wi-Fi baseado em EAP.

> [!NOTE]
-   Poderá considerar mais fácil copiar o código de um computador com ligação à rede, conforme descrito abaixo.
- Para Android, tem também a opção de utilizar este [Android PSK Generator](http://intunepskgenerator.johnathonb.com/) fornecido por Johnathon Biersack.
-   Pode adicionar várias redes e chaves, adicionando mais definições de OMA-URI.
-  Para iOS, utilize o Apple Configurator numa estação Mac para configurar o perfil. Em alternativa, utilize este [iOS PSK Mobile Config Generator](http://intunepskgenerator.johnathonb.com/) fornecido por Johnathon Biersack.


1.  Para criar um perfil Wi-Fi com uma chave pré-partilhada para Android ou Windows, ou um perfil Wi-Fi baseado em EAP, quando criar um perfil de dispositivo, escolha **Personalizado** para essa plataforma de dispositivo, em vez de um perfil Wi-Fi.

2.  Forneça um nome e uma descrição.
3.  Adicione uma nova definição de OMA-URI:

   a.   Introduza um nome para esta definição de rede Wi-Fi.

   b.   Introduza uma descrição da definição de OMA-URI ou deixe em branco.

   c.   **Tipo de Dados**: definido como **Cadeia**.

   d.   **OMA-URI**:

    - **Para Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **Para Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Certifique-se de que inclui o caráter de ponto no início.

    SSID é o SSID para o qual está a criar a política. Por exemplo, `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **Campo de Valor** é onde cola o código XML. Segue-se um exemplo. Cada valor deve ser adaptado às suas definições de rede. Consulte a secção de comentários do código para obter algumas indicações.
4. Escolha **OK**, guarde e, em seguida, atribua a política.

    > [!NOTE]
    > Esta política só pode ser atribuída a grupos de utilizadores.

Da próxima vez que cada dispositivo for registado, a política será aplicada e será criado um perfil Wi-Fi no dispositivo. O dispositivo poderá ligar à rede automaticamente.

## <a name="android-or-windows-wi-fi-profile"></a>Perfil Android ou Wi-Fi do Windows

Segue-se um exemplo do código XML de um perfil Android ou Wi-Fi do Windows:

> [!IMPORTANT]
>
> `<protected>false</protected>`tem de estar definido como **falso**, pois **verdadeiro** pode fazer com que o dispositivo espere uma palavra-passe encriptada e, em seguida, tente decifrá-la, o que pode resultar numa falha de ligação.
>
>  `<hex>53534944</hex>` deve estar definido para o valor hexadecimal de `<name><SSID of wifi profile></name>`.
>  Os dispositivos com Windows 10 podem devolver um erro *0x87D1FDE8 A remediação falhou* falso, mas continuarão a ser aprovisionados com o perfil.

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
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
```

## <a name="eap-based-wi-fi-profile"></a>Perfil Wi-Fi baseado em EAP
Segue-se um exemplo do código XML de um perfil Wi-Fi baseado em EAP:

```
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
Também pode criar um ficheiro XML a partir de uma ligação Wi-Fi existente:
1. Num computador ligado ou que tenha ligado recentemente à rede sem fios, abra a seguinte pasta: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}.

    É melhor utilizar um computador que não tenha ligado a muitas redes sem fios, uma vez que tem de procurar em cada perfil para encontrar a correta.
3.     Procure nos ficheiros XML para localizar o ficheiro com o nome correto.
4.     Depois de localizar o ficheiro XML correto, copie e cole o código XML no campo de Dados da página de definições de OMA-URI.

## <a name="best-practices"></a>Melhores práticas
Antes de implementar um perfil de Wi-Fi com PSK, certifique-se de que o dispositivo consegue ligar ao ponto final diretamente.

Quando alternar chaves (palavras-passe ou frases de acesso), espere a ocorrência de um período de indisponibilidade e planeie as implementações em conformidade. Considere emitir novos perfis de Wi-Fi durante as horas de descanso. Além disso, avise os utilizadores de que a conectividade poderá ser afetada.

Para garantir uma experiência de transição tranquila, certifique-se de que o dispositivo do utilizador final tem uma ligação alternativa à Internet. Por exemplo, o utilizador final tem de conseguir mudar para a rede Guest Wi-Fi (ou outra rede Wi-Fi ) ou ter dados móveis para comunicar com o Intune. Isto permite que o utilizador continue a receber atualizações da política quando o Perfil de Wi-Fi empresarial for atualizado no dispositivo.
