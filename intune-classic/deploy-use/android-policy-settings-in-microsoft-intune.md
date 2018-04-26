---
title: Definições da política para Android e Samsung KNOX
description: Crie políticas que controlem as definições e funcionalidades em dispositivos Android que gere com o Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 10/20/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8d1e20ecd5c6cc1f7bef4541d08a1571a99ac35e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Definições da política para Android e Samsung KNOX Standard no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Intune oferece um conjunto de definições gerais incorporadas que pode configurar em dispositivos Android. Além disso, pode especificar valores de OMA-URI (Open Mobile Alliance Uniform Resource Identifier) para criar definições personalizadas que não estão disponíveis no Intune.

## <a name="general-configuration-policy"></a>Política de configuração geral

Utilize a **política de configuração geral para Android** do Intune para configurar definições para:

-   **Definições de segurança do dispositivo móvel** – escolha de uma lista de definições predefinidas que permitem controlar uma série de funcionalidades e a funcionalidade do dispositivo.

-   **Modo de local público** (apenas para dispositivos Samsung KNOX Standard) – bloqueie um dispositivo para permitir apenas o funcionamento de funcionalidades específicas. Por exemplo, pode permitir que um dispositivo execute apenas uma aplicação gerida que especificar ou pode desativar os botões de volume num dispositivo. Estas definições podem ser utilizadas para um modelo de demonstração de um dispositivo ou para um dispositivo com a finalidade de desempenhar apenas uma função, como um dispositivo de ponto de venda.

-   **Aplicações conformes e não conformes** – especifique uma lista de aplicações que são conformes ou não conformes na sua empresa. Em dispositivos Android e iOS, o **Relatório de Aplicações Não Conformes** pode ser utilizado para ver a conformidade de aplicações especificadas na lista comparativamente às aplicações instaladas pelos utilizadores. Na verdade, o relatório não pode bloquear a instalação da aplicação.

> [!TIP]
> Pode configurar termos e condições para os utilizadores, para garantir que estes têm conhecimento de que todas as aplicações nos respetivos dispositivos, incluindo aplicações pessoais, serão avaliadas e que as aplicações não conformes serão bloqueadas ou comunicadas como não conformes. Os utilizadores têm de aceitar estes termos e condições antes de poderem inscrever os respetivos dispositivos e utilizar o portal da empresa para obter aplicações. Para obter mais informações sobre como utilizar os termos e condições, consulte [Definições de políticas de termos e condições no Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se a definição que procura não for apresentada neste tópico, poderá conseguir criá-la através de uma política personalizada para Android que lhe permita utilizar definições OMA-URI para controlar o dispositivo. Para obter mais informações, consulte [Definições de política personalizada](#custom-policy-settings) mais adiante neste tópico.

### <a name="password-settings"></a>Definições de palavra-passe

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|-|----------------|----------------|
|**Exigir uma palavra-passe para desbloquear os dispositivos móveis**|Especifica se é exigida uma palavra-passe nos dispositivos suportados.|Sim|Sim|
|**Comprimento mínimo da palavra-passe**|Especifica o comprimento mínimo da palavra-passe.|Sim|Sim|
|**Número de falhas de início de sessão consecutivas a permitir antes de o dispositivo ser apagado**|Especifica o número de falhas de início de sessão consecutivas a permitir antes de o dispositivo ser apagado.|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica o número de minutos de inatividade antes de o dispositivo bloquear automaticamente.|Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de uma palavra-passe ter de ser alterada.|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Especifica o número de palavras-passe utilizadas anteriormente a memorizar.|Sim|Sim|
|**Memorizar histórico de palavras-passe** - **Evita a reutilização de palavras-passe anteriores**|Impede a reutilização de palavras-passe anteriores.|Sim|Sim|
|**Qualidade da palavra-passe**|Especifica o nível de complexidade da palavra-passe exigido e se podem ser utilizados dispositivos biométricos.|Sim|Sim|
|**Permitir desbloqueio por impressão digital**|Permite a utilização de uma impressão digital para desbloquear o dispositivo.|Não|Sim|
|**Permitir o bloqueio do smart card e outros agentes de fidedignidade**<br>(Android 5 e posterior)|Permite controlar a funcionalidade Smart Lock nos dispositivos Android compatíveis. Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.|Sim|Não|

### <a name="encryption-settings"></a>Definições de encriptação

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Encriptação obrigatória no dispositivo móvel**|Necessita que os ficheiros no dispositivo móvel sejam encriptados.|Sim|Sim|
|**Encriptação obrigatória nos cartões de armazenamento**|Especifica se o cartão de armazenamento do dispositivo tem de estar encriptado.|Não|Sim|

### <a name="system-settings"></a>Definições do sistema

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Permitir captura de ecrã**|Permite ao utilizador capturar o conteúdo do ecrã como uma imagem.|Não|Sim|
|**Permitir submissão de dados de diagnóstico**|Permite ao dispositivo enviar informações de diagnóstico para a Google.|Não|Sim|
|**Permitir a reposição de fábrica**|Permite ao utilizador efetuar uma reposição de fábrica no dispositivo.|Não|Sim|

### <a name="cloud-settings---documents-and-data"></a>Definições da cloud – documentos e dados

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------------------|----------------|
|**Permitir cópia de segurança do Google**|Permite a utilização da cópia de segurança do Google.|Não|Sim|

### <a name="cloud-settings---accounts-and-synchronization"></a>Definições da cloud – contas e sincronização

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Permitir sincronização automática da conta Google**|Permite que as definições da conta Google sejam sincronizadas automaticamente.|Não|Sim|

### <a name="application-settings---browser"></a>Definições da aplicação – browser

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Permitir browser**|Especifica se pode ser utilizado o browser predefinido do dispositivo.|Não|Sim|
|**Permitir preenchimento automático**|Permite a utilização da função de preenchimento automático do browser.|Não|Sim|
|**Permitir bloqueador de janelas pop-up**|Permite a utilização do bloqueador de janelas pop-up no browser.|Não|Sim|
|**Permitir cookies**|Permite ao browser do dispositivo utilizar cookies.|Não|Sim|
|**Permitir scripting ativo**|Permite ao browser do dispositivo utilizar o scripting ativo.|Não|Sim|

### <a name="application-settings---apps"></a>Definições da aplicação - aplicações

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Permitir loja do Google Play**|Permite ao utilizador aceder à loja do Google Play no dispositivo.|Não|Sim|

### <a name="device-capabilities-settings---hardware"></a>Definições das capacidades do dispositivo - hardware

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Permitir câmara**|Permite a utilização da câmara do dispositivo.|Sim|Sim|
|**Permitir armazenamento amovível**|Permite ao dispositivo utilizar armazenamento amovível, como um cartão SD.|Não|Sim|
|**Permitir Wi-Fi**|Permite a utilização das capacidades Wi-Fi do dispositivo.|Não|Sim|
|**Permitir partilha de Wi-Fi**|Permite a utilização de tethering Wi-Fi no dispositivo.|Não|Sim|
|**Permitir geolocalização**|Permite ao dispositivo utilizar informações de localização.|Não|Sim|
|**Permitir NFC**|Permite operações que utilizam comunicação de proximidade se o dispositivo a suportar.|Não|Sim|
|**Permitir Bluetooth**|Permite a utilização de Bluetooth no dispositivo.|Não|Sim|
|**Permitir desligar**|Permite ao utilizador desligar o dispositivo.<br /><br />Se esta definição estiver desativada, a definição **Número de falhas de início de sessão repetidas permitidas antes da eliminação de dados no dispositivo** para dispositivos Samsung KNOX Standard não funcionará.|Não|Sim|

### <a name="device-capabilities-settings---cellular"></a>Definições das capacidades do dispositivo - rede móvel

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Permitir chamadas em roaming**|Permite chamadas em roaming quando o dispositivo estiver numa rede celular.|Não|Sim|
|**Permitir roaming de dados**|Permite dados em roaming quando o dispositivo estiver numa rede celular.|Não|Sim|
|**Permitir mensagens SMS/MMS**|Permite a utilização de mensagens SMS e MMS no dispositivo.|Não|Sim|

### <a name="device-capabilities-settings---features"></a>Definições das capacidades do dispositivo - funcionalidades

|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Permitir assistente de voz**|Permite a utilização de software de assistente de voz no dispositivo.|Não|Sim|
|**Permitir marcação por voz**|Ativa ou desativa a funcionalidade de marcação por voz no dispositivo.|Não|Sim|
|**Permitir copiar e colar**|Permite as funções de copiar e colar no dispositivo.|Não|Sim|
|**Permitir partilha da área de transferência entre aplicações**|Permite a utilização da área de transferência para efetuar a ação copiar e colar entre aplicações.|Não|Sim|
|**Permitir o YouTube**|Permite a utilização do YouTube no dispositivo.|Não|Sim|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Definições para aplicações conformes e não conformes
Na lista **Aplicações Conformes e &amp;Não Conformes**, especifique uma lista de aplicações conformes ou não conformes com as informações seguintes:

> [!NOTE]
> Uma única política só pode conter uma lista de aplicações conformes ou uma lista de aplicações não conformes. Não é possível especificar ambas na mesma política.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Indica as aplicações que não são geridas pelo Intune e que não pretende que sejam instaladas e executadas pelos utilizadores. Se os utilizadores instalarem uma destas aplicações, estas serão listadas no relatório de aplicações não conformes.|
|**Não comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Indica as aplicações que pretende permitir. Para permanecerem em conformidade, os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada. Especifique um nome da aplicação, o fabricante da aplicação (opcional) e o URL da aplicação na loja de aplicações.<br /><br />Para obter mais informações, veja [Especificar URLs para lojas de aplicações](#specify-urls-to-app-stores) mais adiante neste tópico.|
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o URL da aplicação no ficheiro.|
|**Editar**|Permite editar o nome, o fabricante e o URL da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|

As políticas que contêm as definições de aplicações conformes e não conformes têm de ser implementadas em grupos de utilizadores.

### <a name="kiosk-mode-settings"></a>Definições do modo de local público
Especifique as seguintes definições para **dispositivos Samsung KNOX Standard**:

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Selecione uma aplicação gerida que possa ser executada quando o dispositivo estiver no modo de local público**|Escolha **Procurar** e, em seguida, selecione a aplicação gerida que pode ser executada quando o dispositivo estiver no modo de local público (as aplicações especificadas como uma ligação para a loja não são atualmente suportadas). Não será permitida a execução de outras aplicações no dispositivo.|
|**Permitir os botões de volume**|Ativa ou desativa a utilização dos botões de volume no dispositivo.|
|**Permitir o botão suspender/reativar ecrã**|Ativa ou desativa o botão suspender/reativar ecrã do dispositivo.|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Informações de referência para aplicações conformes e não conformes

#### <a name="monitor-compliant-and-noncompliant-apps"></a>Monitorizar aplicações conformes e não conformes
Utilize o **Relatório de Aplicações Não Conformes** para ver a conformidade das aplicações permitidas e bloqueadas.

###### <a name="to-run-the-noncompliant-apps-report"></a>Para executar o Relatório de Aplicações Não Conformes

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Relatórios** &gt; **Relatório de Aplicações Não Conformes**.

2.  Selecione os grupos de dispositivos que pretende verificar. Em seguida, escolha se pretende verificar a existência de aplicações conformes, aplicações não conformes ou ambas. Por fim, escolha **Ver Relatório**.

#### <a name="specify-urls-to-app-stores"></a>Especificar URLs para lojas de aplicações
Para especificar um URL de aplicação na lista de aplicações conformes e não conformes, siga os seguintes passos:

Na [secção Aplicações do Google Play](https://play.google.com/store/apps), procure a aplicação que pretende utilizar.

Abra a página de instalação da aplicação e copie o URL para a área de transferência. Agora pode utilizar este URL na lista de aplicações conformes ou na lista de aplicações não conformes.

Exemplo: procure Microsoft Office Mobile no Google Play. O URL que irá utilizar será **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## <a name="custom-policy-settings"></a>Definições de política personalizada
Utilize a **política de configuração personalizada para Android** do Microsoft Intune para implementar as definições OMA-URI que podem ser utilizadas para controlar funcionalidades nos dispositivos Android. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições do Android que não são configuráveis com políticas do Intune.
Atualmente, o Intune suporta um número limitado de políticas personalizadas do Android. Consulte os exemplos neste tópico para saber quais as políticas que pode configurar.

### <a name="general-settings"></a>Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    | **Nome** |Introduza um nome exclusivo para a política personalizada do Android para o ajudar a identificá-la na consola do Intune.|
    | **Descrição** |Indique uma descrição geral da política personalizada do Android e outras informações relevantes que o ajudem a localizá-la.|

### <a name="oma-uri-settings"></a>Definições OMA-URI

   |Nome da definição|Detalhes|
    |--------|--------------------|
    | **Nome da definição** |Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
    | **Descrição da definição** |Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    | **Tipo de dados** |Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia, Cadeia (XML), Data e hora, Número inteiro, Vírgula flutuante** ou **Booleano**.|
    | **OMA-URI (sensível às maiúsculas e minúsculas)** |Especifique o OMA-URI para o qual pretende fornecer uma definição.|
    | **Valor** |Indique o valor a associar ao OMA-URI especificado anteriormente.|

### <a name="examples"></a>Exemplos

- [Criar um perfil Wi-Fi com uma chave pré-partilhada](pre-shared-key-wi-fi-profile.md)
- [Utilizar uma política personalizada para criar um perfil de VPN por aplicação para dispositivos Android](per-app-vpn-for-android-pulse-secure.md)
- [Utilizar políticas personalizadas para permitir e bloquear aplicações para dispositivos Samsung KNOX](custom-policy-to-allow-and-block-samsung-knox-apps.md)

## <a name="supported-samsung-knox-standard-devices"></a>Dispositivos Samsung KNOX Standard suportados

A aplicação Portal da Empresa tenta apenas a ativação do Samsung KNOX durante a inscrição MDM se o dispositivo for apresentado na [lista de dispositivos KNOX suportados](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Isto ajuda a evitar erros de ativação de KNOX que impedem a inscrição MDM. Os dispositivos que não suportam a ativação do Samsung KNOX são inscritos como dispositivos Android padrão. Um dispositivo Samsung pode ter alguns números de modelo que suportem o KNOX, enquanto outros não. Verifique a compatibilidade com o KNOX junto do revendedor do seu dispositivo antes da compra e implementação de dispositivos Samsung.

Pode encontrar uma lista de dispositivos Samsung KNOX suportados, juntamente com a lista de [dispositivos suportados pelo Intune](/intune/supported-devices-browsers.md#intune-supported-devices).

### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
