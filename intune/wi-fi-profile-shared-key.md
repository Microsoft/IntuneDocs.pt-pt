---
title: Criar perfil de WiFi com chave pré-compartilhada-Microsoft Intune-Azure | Microsoft Docs
description: Utilize um perfil personalizado para criar um perfil Wi-Fi com uma chave pré-partilhada e obter código XML de exemplo para perfis Android, Windows e perfis Wi-Fi baseados em EAP no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 632bf2c68133f80a44950f154e1b5d9092da3cab
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/25/2019
ms.locfileid: "71303264"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key---intune"></a>Utilizar um perfil de dispositivo personalizado para criar um perfil Wi-Fi com uma chave pré-partilhada – Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As chaves pré-partilhadas (PSK) são normalmente utilizadas para autenticar utilizadores em redes Wi-Fi ou em LANs sem fios. Com o Intune, pode criar um perfil Wi-Fi através de uma chave pré-partilhada. Para criar o perfil, utilize a funcionalidade **Perfis de dispositivos personalizados** no Intune. Este artigo inclui alguns exemplos de como criar um perfil Wi-Fi baseado em EAP.

> [!IMPORTANT]
>- A utilização de uma chave pré-partilhada no Windows 10 faz com que seja apresentado um erro de remediação no Intune. Quando isto acontece, o perfil Wi-Fi é atribuído corretamente ao dispositivo e funciona conforme esperado.
>- Se exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, certifique-se de que o ficheiro está protegido. Como a chave se encontra em texto simples, é sua responsabilidade protegê-la.

## <a name="before-you-begin"></a>Antes de começar

- Poderá ser mais fácil copiar o código de um computador com ligação a essa rede, conforme descrito mais à frente neste artigo.
- Pode adicionar várias redes e chaves, adicionando mais definições de OMA-URI.
- Para iOS, utilize o Apple Configurator numa estação Mac para configurar o perfil.
- O PSK necessita de uma cadeia de 64 dígitos hexadecimais ou uma frase de acesso de 8 a 63 carateres ASCII imprimíveis. Não há suporte para alguns caracteres, como asterisco (*).

## <a name="create-a-custom-profile"></a>Criar um perfil personalizado
Pode criar um perfil personalizado com uma chave pré-partilhada para perfis Android, Windows e perfis Wi-Fi baseados em EAP. Para criar o perfil através do portal do Azure, veja [Criar definições personalizadas de dispositivos](custom-settings-configure.md). Ao criar o perfil de dispositivo, selecione **Personalizado** na plataforma de dispositivos. Não selecione o perfil Wi-Fi. Ao selecionar Personalizado, certifique-se de que: 

1. Introduz um nome e descrição para o perfil.
2. Adiciona uma nova definição de OMA-URI com as seguintes propriedades: 

   a. Introduza um nome para esta definição de rede Wi-Fi.

   b. (Opcional) Introduza uma descrição da definição de OMA-URI ou deixe em branco.

   c. Defina o **Tipo de Dados** para **Cadeia**.

   d. **OMA-URI**:

   - **Para Android**: ./Vendor/MSFT/WiFi/Profile/SSID/Settings
   - **Para Windows**: ./Vendor/MSFT/WiFi/Profile/SSID/WlanXml

     > [!NOTE]
     > Certifique-se de que inclui o caráter de ponto no início.

     SSID é o SSID para o qual está a criar a política. Por exemplo, se o Wi-Fi for nomeado `Hotspot-1`, insira `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

   e. **Campo de Valor** é onde cola o código XML. Veja os exemplos neste artigo. Atualize cada valor para corresponder às suas definições de rede. A secção de comentários do código inclui algumas indicações.
3. Selecione **OK**, guarde e, em seguida, atribua a política.

    > [!NOTE]
    > Esta política só pode ser atribuída a grupos de utilizadores.

Da próxima vez que cada dispositivo for registado, a política será aplicada e será criado um perfil Wi-Fi no dispositivo. Assim, o dispositivo poderá ligar à rede automaticamente.

## <a name="android-or-windows-wi-fi-profile-example"></a>Exemplo de perfil Android ou Wi-Fi do Windows

O seguinte exemplo inclui o código XML de um perfil Android ou Wi-Fi do Windows. O exemplo é disponibilizado para mostrar o formato correto e indicar mais detalhes. Ele é apenas um exemplo e não foi concebido como uma configuração recomendada para o seu ambiente.

### <a name="important-considerations"></a>Considerações importantes

- `<protected>false</protected>` tem de ser definido como **falso**. Se estiver definido como **verdadeiro**, poderá fazer com que o dispositivo espere uma palavra-passe encriptada e, em seguida, tente decifrá-la, o que poderá resultar numa falha de ligação.

- `<hex>53534944</hex>` deve estar definido para o valor hexadecimal de `<name><SSID of wifi profile></name>`. Dispositivos Windows 10 podem retornar um erro `x87D1FDE8 Remediation failed` falso, mas o dispositivo ainda contém o perfil.

- O XML tem caracteres especiais, como o `&` (e comercial). O uso de caracteres especiais pode impedir que o XML funcione conforme o esperado. 

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

## <a name="eap-based-wi-fi-profile-example"></a>Exemplo de perfil Wi-Fi baseado em EAP
O seguinte exemplo inclui o código XML de um perfil Wi-Fi baseado em EAP: O exemplo é disponibilizado para mostrar o formato correto e indicar mais detalhes. Ele é apenas um exemplo e não foi concebido como uma configuração recomendada para o seu ambiente.


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

Você também pode criar um arquivo XML de uma conexão Wi-Fi existente. Em um computador com Windows, use as seguintes etapas:

1. Crie uma pasta local para os perfis W-Fi exportados, como c:\WiFi.
2. Abra um prompt de comando como administrador (clique com o botão `cmd`direito do mouse em  >  **Executar como administrador**)
3. Execute `netsh wlan show profiles`. Os nomes de todos os perfis são listados.
4. Execute `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. Este comando cria um arquivo chamado `Wi-Fi-YourProfileName.xml` em c:\Wifi.

    - Se você estiver exportando um perfil de Wi-Fi que inclui uma chave pré-compartilhada, `key=clear` adicione ao comando:
  
      `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

      `key=clear`exporta a chave em texto sem formatação, o que é necessário para usar o perfil com êxito.

Depois de ter o arquivo XML, copie e cole a sintaxe XML em configurações OMA-URI > **tipo de dados**. [Criar um perfil personalizado](#create-a-custom-profile) (neste artigo) lista as etapas.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}`também inclui todos os perfis no formato XML.

## <a name="best-practices"></a>Melhores práticas

- Antes de implementar um perfil de Wi-Fi com PSK, confirme que o dispositivo consegue ligar diretamente ao ponto final.

- Ao girar chaves (senhas ou frases secretas), espere tempo de inatividade e planeje suas implantações. Considere emitir novos perfis de Wi-Fi durante as horas de descanso. Além disso, avise os usuários de que a conectividade pode ser afetada.

- Para uma transição suave, verifique se o dispositivo do usuário final tem uma conexão alternativa com a Internet. Por exemplo, o usuário final pode voltar para o convidado WiFi (ou outra rede WiFi) ou ter conectividade celular para se comunicar com o Intune. A ligação adicional permite ao utilizador receber atualizações da política quando o Perfil de Wi-Fi empresarial for atualizado no dispositivo.
