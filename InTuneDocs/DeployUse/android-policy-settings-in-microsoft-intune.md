---
# required metadata

title: Definições de política de configuração para Android no Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Definições de política para Android no Microsoft Intune

## Política de configuração geral

Utilize a **política de configuração geral para Android** do Microsoft Intune para configurar definições para:

-   **Definições de segurança do dispositivo móvel** – Escolha de uma lista de definições predefinidas que permitem controlar uma série de funcionalidades e a funcionalidade do dispositivo.

-   **Modo de local público** (apenas para dispositivos Samsung KNOX) - Bloqueie um dispositivo para permitir apenas o funcionamento de funcionalidades específicas. Por exemplo, pode permitir que um dispositivo execute apenas uma aplicação gerida que especificar ou pode desativar os botões de volume num dispositivo. Estas definições podem ser utilizadas para um modelo de demonstração de um dispositivo ou para um dispositivo com a finalidade de desempenhar apenas uma função, como um dispositivo de ponto de venda.

-   **Aplicações compatíveis e não compatíveis** - Especifique uma lista de aplicações que são compatíveis ou não compatíveis na sua empresa. Em dispositivos Android e iOS, o **Relatório de Aplicações Não Compatíveis** pode ser utilizado para ver a compatibilidade de aplicações especificadas na lista comparativamente às aplicações instaladas pelos utilizadores (mas não pode bloquear a instalação da aplicação).

> [!TIP]
> Pode configurar termos e condições para os utilizadores, para garantir que estes têm conhecimento de que as aplicações nos respetivos dispositivos, incluindo aplicações pessoais, serão avaliadas e que as aplicações não compatíveis serão bloqueadas ou comunicadas como não compatíveis. Os utilizadores têm de aceitar estes termos e condições antes de poderem inscrever os respetivos dispositivos e utilizar o portal da empresa para obter aplicações. Para mais informações sobre como utilizar os termos e condições, consulte [Definições de políticas de termos e condições no Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se a definição que procura não for apresentada neste tópico, poderá conseguir criá-la através de uma política personalizada para Android que lhe permita utilizar definições OMA-URI para controlar o dispositivo. Para mais informações, consulte **Definições de política personalizada ** mais adiante neste tópico.

### Definições de palavra-passe

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Exigir uma palavra-passe em dispositivos suportados.|Sim|Sim|
|**Comprimento mínimo da palavra-passe**|O comprimento mínimo da palavra-passe.|Sim|Sim|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Apaga o dispositivo em caso de falha deste número de tentativas de início de sessão.|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifique o número de minutos antes de o dispositivo bloquear automaticamente.|Sim|Sim|
|**Expiração da Palavra-passe (dias)**|O número de dias antes de uma palavra-passe tem de ser alterado.|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Memorize as inúmeras palavras-passe utilizadas anteriormente.|Sim|Sim|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Impede a reutilização de palavras-passe.|Sim|Sim|
|**Qualidade da palavra-passe**|Selecionar o nível de complexidade da palavra-passe exigido e se podem ser utilizados dispositivos biométricos.|Sim|Sim|
|**Permitir desbloqueio por impressão digital**|Permita a utilização de uma impressão digital para desbloquear o dispositivo.|Não|Sim|

### Definições de encriptação

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Encriptação obrigatória no dispositivo móvel**|Necessita que os ficheiros no dispositivo móvel sejam encriptados.|Sim|Sim|
|**Encriptação obrigatória nos cartões de armazenamento**|Especifica se o cartão de armazenamento do dispositivo tem de estar encriptado.|Não|Sim|

### Definições do sistema

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir captura de ecrã**|Permite ao utilizador capturar o conteúdo do ecrã como uma imagem.|Não|Sim|
|**Permitir submissão de dados de diagnóstico**|Permite ao dispositivo enviar informações de diagnóstico para a Google.|Não|Sim|
|**Permitir a reposição de fábrica**|Permitir que o utilizador efetue uma reposição de fábrica no dispositivo.|Não|Sim|

### Definições da nuvem - documentos e dados

|Nome da definição|Detalhes|Android e Samsung KNOX|Android 4.0+|
|----------------|----------------------------|----------------|
|**Permitir cópia de segurança do Google**|Permite a utilização da cópia de segurança do Google.|Não|Sim|

### Definições da nuvem – contas e sincronização

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir sincronização automática da conta Google**|Permite que as definições da conta Google sejam sincronizadas automaticamente.|Não|Sim|

### Definições da aplicação - browser

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir browser**|Especifica se a o browser do dispositivo pode ser utilizado.|Não|Sim|
|**Permitir preenchimento automático**|Permite a utilização da função de Preenchimento automático do browser.|Não|Sim|
|**Permitir bloqueador de janelas de pop-up**|Permite a utilização do bloqueador de janelas de pop-up no browser.|Não|Sim|
|**Permitir cookies**|Permite ao browser do dispositivo utilizar cookies.|Não|Sim|
|**Permitir scripting ativo**|Permite ao browser do dispositivo utilizar o scripting ativo.|Não|Sim|

### Definições da aplicação - aplicações

|Nome da definição|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir loja do Google Play**|Permite ao utilizador aceder à loja do Google Play no dispositivo.|Não|Sim|

### Definições das capacidades do dispositivo - hardware

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir câmara**|Permite a utilização da câmara do dispositivo.|Sim|Sim|
|**Permitir armazenamento amovível**|Permite ao dispositivo utilizar armazenamento amovível, como um cartão SD.|Não|Sim|
|**Permitir Wi-Fi**|Permite a utilização das capacidades Wi-Fi do dispositivo.|Não|Sim|
|**Permitir partilha de Wi-Fi**|Permite a utilização de tethering Wi-Fi no dispositivo.|Não|Sim|
|**Permitir geolocalização**|Permite ao dispositivo utilizar informações de localização.|Não|Sim|
|**Permitir NFC**|Permite operações que utilizam comunicação de proximidade se o dispositivo a suportar.|Não|Sim|
|**Permitir Bluetooth**|Permite a utilização de Bluetooth no dispositivo.|Não|Sim|
|**Permitir desligar**|Permite ao utilizador desligar o dispositivo.<br /><br />Se esta definição estiver desativada, a definição **Número de falhas de início de sessão repetidas permitidas antes da eliminação de dados no dispositivo** para dispositivos Samsung KNOX não funcionará.|Não|Sim|

### Definições das capacidades do dispositivo - rede móvel

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir chamadas em roaming**|Permite chamadas em roaming quando o dispositivo estiver numa rede celular.|Não|Sim|
|**Permitir roaming de dados**|Permite roaming de dados quando o dispositivo estiver numa rede celular.|Não|Sim|
|**Permitir mensagens SMS/MMS**|Permite a utilização de mensagens SMS e MMS no dispositivo.|Não|Sim|

### Definições das capacidades do dispositivo - funcionalidades

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir assistente de voz**|Permite a utilização de software de assistente de voz no dispositivo.|Não|Sim|
|**Permitir marcação por voz**|Ativa ou desativa a funcionalidade de marcação por voz no dispositivo.|Não|Sim|
|**Permitir copiar e colar**|Permite as funções copiar e colar no dispositivo.|Não|Sim|
|**Permitir partilha da área de transferência entre aplicações**|Utilize a área de transferência para efetuar a ação copiar e colar entre aplicações.|Não|Sim|
|**Permitir o YouTube**|Permite a utilização do YouTube no dispositivo.|Não|Sim|

### Definições para aplicações compatíveis e não compatíveis
Na lista **Aplicações Conformes e &amp;Não Conformes**, especifique uma lista de aplicações conformes ou não conformes com as informações seguintes:

> [!NOTE]
> Uma única política só pode conter uma lista de aplicações compatíveis ou uma lista de aplicações não compatíveis. Não é possível especificar ambas na mesma política.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Indica as aplicações que não são geridas pelo Intune e para as quais os utilizadores não têm permissão para instalar e executar.|
|**Não comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Indica as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada. Especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.<br /><br />Para obter ajuda, consulte Como especificar URLs para lojas de aplicações mais adiante neste tópico.|
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o URL da aplicação no ficheiro.|
|**Editar**|Permite-lhe editar o nome, o fabricante e o URL da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|

### Definições do modo de local público
Especifique as seguintes definições para **dispositivos Samsung KNOX**:

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Selecione uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público**|Clique em **Procurar** e, em seguida, selecione a aplicação gerida ou a aplicação de uma loja que terá permissão para ser executada quando o dispositivo estiver em modo de local público. Não será permitida a execução de outras aplicações no dispositivo.<br /><br />Para obter ajuda, consulte Como especificar URLs para lojas de aplicações mais adiante neste tópico.|
|**Permitir os botões de volume**|Ativa ou desativa a utilização dos botões de volume no dispositivo.|
|**Permitir o botão suspender/reativar ecrã**|Ativa ou desativa o botão suspender/reativar ecrã do dispositivo.|

### Informações de referência para aplicações compatíveis e não compatíveis

#### Monitorizar aplicações compatíveis e não compatíveis
Utilize o **Relatório de Aplicações Não Compatíveis** para ver a compatibilidade das aplicações permitidas e bloqueadas.

###### Para executar o Relatório de Aplicações Não Compatíveis

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Relatórios** &gt; **Relatório de Aplicações Não Conformes**.

2.  Selecione os grupos de dispositivos que pretende verificar, se pretende verificar as aplicações conformes, as aplicações não conformes ou ambas e, em seguida, clique em **Ver Relatório**.

#### Como especificar URLs para lojas de aplicações
Para especificar o URL de uma aplicação na lista de aplicações compatíveis e não compatíveis ou na opção **Selecionar uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público** (apenas em iOS), utilize o seguinte formato:

Na [secção Aplicações do Google Play](https://play.google.com/store/apps), procure a aplicação que pretende utilizar.

Abra a página de instalação da aplicação e copie o URL para a área de transferência. Agora pode utilizar este URL na lista de aplicações compatíveis ou na lista de aplicações não compatíveis.

**Exemplo:** procure Microsoft Office Mobile no Google Play. O URL a utilizar será **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub&hl=pt**.

## Definições de política personalizada
Utilize a **política de configuração personalizada para Android** do Microsoft Intune para implementar as definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar funcionalidades nos dispositivos Android. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições do Android que não são configuráveis com políticas do Intune. Para obter informações sobre as definições que pode configurar com estas políticas, consulte [Gerir as definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

> [!NOTE]
> Atualmente, as políticas personalizadas do Android apenas suportam a configuração de definições Wi-Fi para dispositivos Android que incluam uma chave pré-partilhada. Para mais informações, consulte Configurar um perfil Wi-Fi personalizado com uma chave pré-partilhada mais adiante neste tópico.

### Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política personalizada do Android para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política personalizada do Android e outras informações relevantes que o ajudem a localizá-la.|

### Definições OMA-URI

   |Nome da definição|Detalhes|
    |--------|--------------------|
    |**Nome da definição**|Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
    |**Descrição da definição**|Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    |**Tipo de dados**|Selecione o tipo de data em que especificará esta definição OMA-URI. Escolha entre **Cadeia, Cadeia (XML), Data e hora, Número inteiro, Vírgula flutuante** ou **Booleano**.|
    |**OMA-URI (sensível às maiúsculas e minúsculas)**|Especifique o OMA-URI para o qual pretende fornecer uma definição.|
    |**Valor**|Indique o valor a associar ao OMA-URI especificado anteriormente.|

### Exemplo: Configurar um perfil Wi-Fi personalizado com uma chave pré-partilhada
Embora o Intune suporte perfis Wi-Fi para dispositivos Android, esta funcionalidade não suporta a inclusão de chaves pré-partilhadas na configuração atualmente. Neste exemplo, aprenderá a criar uma política personalizada do Android que cria um perfil Wi-Fi com uma chave pré-partilhada no dispositivo Android.

#### Para criar um perfil Wi-Fi com uma chave pré-partilhada

1.  Certifique-se de que os utilizadores estão a utilizar a versão mais recente da aplicação [Portal da Empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) para Android.

2.  Crie uma política personalizada do Android e adicione a seguinte definição:

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Nome da definição**|Especifique um nome à sua escolha para a definição.|
|**Descrição da definição**|Especifique uma descrição para a definição.|
|**Tipo de dados**|Selecione **Cadeia (XML)**.|
|**OMA-URI**|Introduza o seguinte: ./Vendor/MSFT/WiFi/Profile/*&lt;perfil Wi-Fi&gt;*/Settings|

3.  Para **Value**, copie e cole o seguinte código XML:

    ```
    <!--
    WEP Wifi Profile
                    <Name of wifi profile> = Name of profile 
                    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
                    <WEP password> = Password to connect to the network
    -->
    <WLANProfile 
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <name><SSID of wifi profile></name>
        </SSID>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <MSM>
        <security>
          <authEncryption>
            <authentication>open</authentication>
            <encryption>WEP</encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial><WEP password></keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>
    ```

4.  Quando terminar, guarde a política e implemente-a nos dispositivos Android necessários. O novo perfil Wi-Fi aparecerá na lista de ligações no dispositivo.

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


