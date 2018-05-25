---
title: Definições de restrição de dispositivos no Microsoft Intune para dispositivos Android
titlesuffix: ''
description: Saiba que definições do Intune pode utilizar para controlar as definições e funcionalidades em dispositivos a executar o Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 100742b378b30eab84b28c01728b2b382dd5155c
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="microsoft-intune-android-and-samsung-knox-standard-device-restriction-settings"></a>Definições de restrição de dispositivos do Microsoft Intune para Android e Samsung Knox Standard 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe todas as definições de restrições de dispositivos do Microsoft Intune que pode configurar para dispositivos a executar o Android.

>[!TIP]
>Se as definições que pretende não estiverem disponíveis, poderá conseguir configurá-las nos seus dispositivos através de um [perfil personalizado](custom-settings-android.md).

## <a name="general"></a>Geral

- **Câmara** – permite a utilização da câmara do dispositivo.
- **Copiar e colar (apenas Samsung Knox)** – permite as funções de copiar e colar no dispositivo.
- **Partilha da área de transferência entre aplicações (apenas Samsung Knox)** – permite a utilização da área de transferência para copiar e colar entre aplicações.
- **Submissão de dados de diagnóstico (apenas Samsung Knox)** – impede o utilizador de submeter dados de diagnóstico a partir do dispositivo.
- **Reposição de fábrica (apenas Samsung Knox)** – permite ao utilizador realizar uma reposição de fábrica no dispositivo.
- **Geolocalização (apenas Samsung Knox)** – permite que o dispositivo utilize informações de localização.
- **Desligar (apenas Samsung Knox)** – permite ao utilizador desligar o dispositivo.<br>Se desativado, o **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** não pode ser definido.
- **Captura de ecrã (apenas Samsung Knox)** – permite ao utilizador capturar os conteúdos do ecrã como uma imagem.
- **Assistente de voz (apenas Samsung Knox)** – permite a utilização de software de assistente de voz no dispositivo.
- **YouTube (apenas Samsung Knox)** – permite a utilização da aplicação YouTube no dispositivo.
- **Dispositivos partilhados (apenas Samsung Knox)** – configure um dispositivo Samsung Knox Standard gerido como partilhado. Neste modo, os utilizadores finais podem iniciar ou terminar sessão do dispositivo com as suas credenciais do Azure AD. O dispositivo continua a ser gerido quer esteja quer não esteja a ser utilizado.<br>Quando utilizado conjuntamente com um perfil de certificado SCEP, esta funcionalidade permite que os utilizadores finais partilhem um dispositivo com o mesmo conjunto de aplicações para todos os utilizadores, mas com os respetivos certificados de utilizador SCEP.  Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.  Esta funcionalidade é limitada a aplicações LOB.
- **Bloquear alterações de data e hora (Samsung Knox)** – impede que o utilizador altere as definições de data e hora do dispositivo. 

## <a name="password"></a>Palavra-passe

- **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.|Sim|Sim|

    > [!NOTE]
    > Os dispositivos Samsung Knox exigem automaticamente um PIN de 4 dígitos durante a inscrição na MDM. Os dispositivos Android nativos podem exigir automaticamente um PIN para ficarem em conformidade com o acesso condicional.

- **Comprimento mínimo da palavra-passe** – introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre 4 e 16 carateres).
- **Máximo de minutos de inatividade até o ecrã bloquear** – especifica o número de minutos de inatividade antes de o dispositivo bloquear automaticamente.
- **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – especifica o número de falhas de início de sessão consecutivas a permitir antes de os dados do dispositivo serem apagados.
- **Expiração de palavra-passe (dias)** – especifica o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
-  **Tipo obrigatório de palavra-passe** – especifica o nível de complexidade da palavra-passe exigido e se podem ser utilizados dispositivos biométricos. Escolha entre:
    - **Predefinição do dispositivo**
    - **Biométrica de segurança baixa**
    - **Pelo menos numérica**
    - **Complexo numérico** – não são permitidos números repetidos ou consecutivos (como "1111" ou "1234").<sup>1</sup>
    - **Pelo menos alfabética**
    - **Pelo menos alfanumérica**
    - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores** – impede que o utilizador final crie uma palavra-passe que já tenha utilizado antes.
- **Desbloqueio por impressão digital (apenas Samsung Knox)** – permite a utilização de uma impressão digital para desbloquear os dispositivos suportados.
- **Smart Lock e outros agentes de fidedignidade** – permite-lhe controlar a funcionalidade Smart Lock em dispositivos Android compatíveis (Samsung Knox Standard 5.0 e posterior). Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, isto pode ser utilizado quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.
- **Encriptação** – requer que os ficheiros no dispositivo estejam encriptados.

    > [!NOTE]
    > Se for imposta uma política de encriptação, os dispositivos Samsung Knox exigem que os utilizadores definam uma palavra-passe complexa de 6 carateres como o código de acesso do dispositivo.

<sup>1</sup> Antes de atribuir esta definição aos dispositivos, verifique se atualiza a aplicação Portal da Empresa para a versão mais recente nesses dispositivos.

Se configurar a definição **Numérica complexa** e, em seguida, a atribuir a um dispositivo com uma versão anterior à versão 5.0 do Android, aplicar-se-á o seguinte comportamento.
- Se a aplicação Portal da Empresa estiver a executar uma versão anterior à 1704, não será aplicada nenhuma política de PIN ao dispositivo e será apresentado um erro no portal do Azure.
- Se a aplicação Portal da Empresa executar a versão 1704 ou posterior, apenas pode ser aplicado um PIN simples. As versões do Android anteriores à 5.0 não suportam esta definição. Nenhum erro é apresentado no portal do Azure.


## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (apenas Samsung Knox)** – permite ao utilizador aceder à Google Play Store no dispositivo.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma destas listas para ambos os dispositivos Android e Samsung Knox Standard:

Uma lista de **Aplicações proibidas** – indique as aplicações (não geridas pelo Intune) que serão reportadas se os utilizadores as instalarem e executarem.
Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas.
Os perfis de dispositivo que contêm as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações conformes e não conformes, siga os seguintes passos:

Na [secção Aplicações do Google Play](https://play.google.com/store/apps), procure a aplicação que pretende utilizar.

Abra a página de instalação da aplicação e copie o URL para a área de transferência. Agora pode utilizar este URL na lista de aplicações conformes ou na lista de aplicações não conformes.

Exemplo: procure o **Microsoft Planner** na [secção Aplicações da Google Play Store](https://play.google.com/store/apps). Utilize o URL: **https://play.google.com/store/apps/details?id=com.microsoft.planner**.

### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para obter a lista de um ficheiro csv. Utilize o formato <*URL da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clique em **Exportar** no ficheiro csv que contenha o conteúdo da lista de aplicações restritas no mesmo formato.      

## <a name="browser"></a>Browser

- **Browser (apenas Samsung Knox)** – especifica se o browser predefinido do dispositivo pode ser utilizado.
- **Preenchimento automático (apenas Samsung Knox)** – permite a utilização da função de preenchimento automático do browser.
- **Cookies (apenas Samsung Knox)** – permite que o browser do dispositivo utilize cookies.
- **Javascript (apenas Samsung Knox)** – permite que o browser do dispositivo execute scripts em Java.
- **Pop-ups (apenas Samsung Knox)** – permite a utilização do bloqueador de janelas de pop-up no browser.

## <a name="allow-or-block-apps"></a>Permitir ou Bloquear aplicações

Estas definições podem servir para especificar aplicações que podem ser instaladas ou iniciadas apenas em dispositivos com o Samsung Knox Standard.
Além disso, também pode especificar aplicações instaladas que serão ocultadas do utilizador do dispositivo. Os utilizadores não podem executar estas aplicações.

- **Aplicações com permissão para serem instaladas (apenas no Samsung Knox Standard)**
- **Aplicações com início bloqueado (apenas no Samsung Knox Standard)**
- **Aplicações ocultadas do utilizador (apenas no Samsung Knox Standard)**

Para cada definição, configure uma lista de aplicações através de um dos seguintes procedimentos:

- **Adicionar aplicações pelo nome do pacote** – utilizado principalmente para aplicações de linha de negócio. Introduza o nome da aplicação e o nome do pacote de aplicação.
- **Adicionar aplicações pelo URL** – Introduza o nome da aplicação e o URL na loja do Google Play.
- **Adicionar aplicações geridas** – Na lista de aplicações geridas com o Intune, selecione a aplicação de que necessita.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Cópia de segurança do Google (apenas Samsung Knox)** – permite a utilização da cópia de segurança do Google.
- **Sincronização automática da conta Google (apenas Samsung Knox)** – permite que as definições da conta Google sejam sincronizadas automaticamente.
- **Armazenamento amovível (apenas Samsung Knox)** – permite que o dispositivo utilize o armazenamento amovível, como um cartão SD.
- **Encriptação em cartões de armazenamento (apenas Samsung Knox)** – especifica se o cartão de armazenamento do dispositivo tem de estar encriptado.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Roaming de dados (apenas Samsung Knox)** – permite o roaming de dados quando o dispositivo estiver numa rede móvel.
- **Mensagens SMS/MMS (apenas Samsung Knox)** – permite a utilização de mensagens SMS e MMS no dispositivo.
- **Marcação por voz (apenas Samsung Knox)** – ativa ou desativa a funcionalidade de marcação por voz no dispositivo.
- **Chamadas em roaming (apenas Samsung Knox)** – permite as chamadas em roaming quando o dispositivo estiver numa rede móvel.
- **Bluetooth (apenas Samsung Knox)** – permite a utilização do Bluetooth no dispositivo.
- **NFC (apenas Samsung Knox)** – permite operações que utilizam comunicação de proximidade nos dispositivos suportados.
- **Wi-Fi (apenas Samsung Knox)** – permite a utilização das funcionalidades de Wi-Fi do dispositivo.
- **Tethering Wi-Fi (apenas Samsung Knox)** – permite a utilização de tethering Wi-Fi no dispositivo.

## <a name="kiosk"></a>Modo de Local Público

As definições de modo de local público aplicam-se apenas a dispositivos Samsung Knox Standard e apenas a aplicações que gere com o Intune.

- **Selecionar uma aplicação gerida** – Escolha uma das seguintes opções para adicionar uma ou mais aplicações geridas que podem ser executadas quando o dispositivo está no modo de local público. Não é permitida a execução de outras aplicações no dispositivo. Enquanto o dispositivo se encontrar no modo de local público, os browsers pré-instalados não podem ser definidos como uma aplicação com permissão para ser executada. Se for necessário utilizar um browser, considere a utilização do [Managed Browser](app-configuration-managed-browser.md).
    - **Adicionar aplicações pelo nome do pacote**
    - **Adicionar aplicações por URL**
    - **Adicionar aplicações geridas**.
- **Botão de suspensão do ecrã** – Ativa ou desativa o botão suspender/reativar ecrã do dispositivo.
- **Botões de volume** - Ativa ou desativa a utilização dos botões de volume no dispositivo.


## <a name="next-steps"></a>Próximos passos

Continue a seguir as instruções em [Como configurar definições de restrições de dispositivos](device-restrictions-configure.md) para criar e atribuir o perfil de restrição de dispositivos.
