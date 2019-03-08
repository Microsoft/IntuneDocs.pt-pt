---
title: Resolver problemas com a instalação de aplicações
titlesuffix: Microsoft Intune
description: Utilize o painel de resolução de problemas do Microsoft Intune para o ajudar a resolver problemas com a instalação de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/19/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a5e000a973932db0bbaa215ea94976219ff905c
ms.sourcegitcommit: 6da78a3c07e9ad9c72ff532867cde754e9deca00
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57577851"
---
# <a name="troubleshoot-app-installation-issues"></a>Resolver problemas com a instalação de aplicações

Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. O Microsoft Intune disponibiliza detalhes da falha na instalação da aplicação que permitem que os operadores de suporte técnico e os administradores do Intune vejam informações da aplicação para resolver pedidos de ajuda do utilizador. O painel de resolução de problemas no Intune proporciona os detalhes da falha, incluindo detalhes sobre as aplicações geridas no dispositivo de um utilizador. São disponibilizados detalhes sobre o ciclo de vida ponto a ponto de uma aplicação em cada dispositivo individual no painel **Aplicações Geridas**. Pode ver os problemas de instalação, como quando a aplicação foi criada, modificada, direcionada e entregue a um dispositivo. 

## <a name="app-troubleshooting-details"></a>Detalhes de resolução de problemas da aplicação

O Intune proporciona detalhes da resolução de problemas com a aplicação com base nas aplicações instaladas no dispositivo de um utilizador específico.

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Resolução de problemas**.
4. Clique em **Selecionar utilizador** para selecionar um utilizador para o qual quer executar a resolução de problemas. O painel **Selecionar utilizadores** será apresentado.
5. Selecione um utilizador ao escrever o nome ou endereço de e-mail. Clique em **Selecionar** na parte inferior do painel. As informações de resolução de problemas do utilizador são apresentadas no painel **Resolução de problemas**. 
6. Selecione o dispositivo com o qual quer resolver problemas na lista **Dispositivos**.
    ![O painel de Resolução de Problemas do Intune.](media/troubleshoot-app-install-01.png)
7. Selecione **Aplicações Geridas** a partir do painel do dispositivo selecionado. É apresentada uma lista de aplicações geridas.
    ![Detalhes de um dispositivo específico gerido pelo Intune.](media/troubleshoot-app-install-02.png)
8. Selecione uma aplicação na lista onde o **Estado da Instalação** indicar uma falha.
    ![Uma aplicação selecionada que mostra detalhes da falha na instalação.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > A mesma aplicação pode ser atribuída a vários grupos, mas com diferentes ações pretendidas (intenções) para a aplicação. Por exemplo, uma intenção resolvida para uma aplicação apresentará a indicação **excluída** se a aplicação estiver excluída para um utilizador durante a atribuição de aplicações. Para obter mais informações, veja [Como são resolvidos conflitos entre intenções de aplicações](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Se ocorrer uma falha na instalação de uma aplicação necessária, o utilizador ou o suporte técnico poderá sincronizar o dispositivo e repetir a instalação da aplicação.

Os detalhes do erro da instalação da aplicação irão indicar o problema. Pode usar estes detalhes para determinar a melhor ação a tomar para resolver o problema. Para obter mais informações sobre como resolver problemas de instalação da aplicação, veja [Códigos de Erro para Resolver Problemas de Instalação da Aplicação](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues).

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="win32-app-installation-troubleshooting"></a>Resolução de instalação de aplicações do Win32

Selecione a aplicação de Win32 que foi implementada utilizando a extensão de gestão do Intune. Pode selecionar o **recolher registos** opção quando ocorre uma falha de instalação da sua aplicação Win32. 

> [!IMPORTANT]
> O **recolher registos** opção não será ativada quando a aplicação de Win32 foi instalada com êxito no dispositivo.<p>Pode coletar informações de registo da aplicação de Win32, a extensão de gestão do Intune tem de estar instalada no cliente Windows. A extensão de gestão do Intune é instalada quando um script do PowerShell ou uma aplicação Win32 for implementada para um utilizador ou grupo de segurança do dispositivo. Para obter mais informações, consulte [extensão de gestão do Intune - pré-requisitos](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Recolher ficheiros de registo

Para recolher os registos de instalação de aplicações do Win32, siga os passos fornecidos na secção [detalhes de resolução de problemas de aplicação](troubleshoot-app-install.md#app-troubleshooting-details). Em seguida, continue com os seguintes passos:

1. Clique nas **recolher registos** opção a **detalhes da instalação** painel.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Fornecer caminhos de ficheiro de registo de nomes de arquivo para iniciar o processo de recolha de ficheiros de registo e clique em **OK**.
    
    > [!NOTE]
    > Recolha de registos irão demorar menos de duas horas. Tipos de ficheiro suportados: *. log,. txt,. dmp,. cab,. zip,. XML, evtx e .evtl*. É permitido um máximo de 25 caminhos de arquivo.

3. Depois de tem sido recolhidos os ficheiros de registo, pode selecionar o **registos** ligação para transferir os ficheiros de registo.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Será apresentada uma notificação que indica o êxito da coleção de registo de aplicações.

#### <a name="win32-log-collection-requirements"></a>Requisitos de coleção de registo do Win32

Existem requisitos específicos que devem ser seguidos para recolher ficheiros de registo:

- Tem de especificar o caminho do ficheiro de registo completo. 
- Pode especificar variáveis de ambiente para o conjunto de registo, como o seguinte:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Apenas as extensões de ficheiros exata são permitidas, tais como:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- O ficheiro de registo máximo para carregar é de 60 MB ou 25 arquivos, que ocorrer primeiro. 
- Recolha de registos de instalação de aplicações de Win32 está ativada para as aplicações que cumprem necessária, disponível e desinstalar o objetivo de atribuição de aplicação.
- Os registos armazenados são criptografados para proteger as informações de PII contidas nos registos.
- Embora o suporte de abertura permissões para falhas de aplicação do Win32, anexe os registos de falha relacionados através dos passos apresentados acima.

## <a name="app-installation-errors"></a>Erros de instalação da aplicação

As seguintes mensagens de erro e descrições fornecem detalhes sobre erros de instalação no Android e no iOS. 

### <a name="android-errors"></a>Erros do Android

|    Mensagem/código de erro    |    Descrição    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    A instalação da aplicação falhou. (0xC7D14FB5)    |    Esta mensagem de erro é apresentada quando o Intune não consegue determinar a causa raiz do erro de instalação da aplicação Android. Não são fornecidas informações pelo Android durante a falha.       Este erro é apresentado quando a APK é transferida com êxito, mas a instalação da aplicação falhou. Este erro poderá ocorrer de forma mais comum devido a um ficheiro APK incorreto que não pode ser instalado no dispositivo. Uma causa possível poderá ser caso o Google Play Protect bloqueie a instalação da aplicação devido a questões de segurança. Outra causa possível deste erro é um dispositivo não suportar a aplicação. Por exemplo, se a aplicação necessitar da versão 21 ou posterior da API e o dispositivo tiver a versão 19 da API.         O Intune apresenta este erro em dispositivos KNOX e DA. Apesar de poder ser apresentada uma notificação na qual os utilizadores podem clicar para tentar novamente, se existir um problema com a APK, não ocorrerão mais falhas. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.        |
|    A instalação da aplicação foi cancelada porque o ficheiro de instalação (APK) foi eliminado após a transferência, mas antes da instalação. (0xC7D14FBA)    |    A APK foi transferida com êxito, mas o ficheiro foi removido do dispositivo antes de o utilizador instalar a aplicação. Isto poderá ocorrer se existir um intervalo de tempo grande entre a transferência e a instalação. Por exemplo, o utilizador cancelou a instalação original, espera e, em seguida, clica na notificação para tentar novamente.         Esta mensagem de erro só é apresentada para cenários de DA. Os cenários de KNOX podem ser realizados automaticamente. Apresentamos uma notificação Tentar novamente para que o utilizador possa aceitar em vez de cancelar. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    A instalação da aplicação foi cancelada porque o processo foi reiniciado durante a instalação. (0xC7D14FBB)    |    O dispositivo foi reiniciado durante o processo de instalação do ficheiro APK, resultando numa instalação foi cancelada.        Esta mensagem de erro é apresentada em dispositivos KNOX e DA. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    A aplicação não foi detetada depois de a instalação ter sido concluída com êxito. (0x87D1041C)    |    O utilizador desinstalou explicitamente a aplicação. Este erro não é devolvido do cliente. É um erro apresentado quando uma aplicação é instalada a determinada altura e depois desinstalada pelo utilizador. Este erro só deverá ocorrer em aplicações necessárias. Os utilizadores podem desinstalar aplicações não necessárias. Este erro só pode ocorrer em dispositivos DA. Os dispositivos KNOX bloqueiam a desinstalação de aplicações geridas.       A sincronização seguinte irá voltar a apresentar a notificação no dispositivo para o utilizador instalar.   O utilizador pode ignorar a notificação. Este erro continuará a ser apresentado até que o utilizador instale a aplicação.    |
|    A transferência falhou devido a um erro desconhecido. (0xC7D14FB2)    |    Este erro ocorre quando a transferência falha. Este erro pode ocorrer devido a ligações lentas ou problemas de Wi-Fi.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    A transferência falhou devido a um erro desconhecido. A política será repetida na próxima vez que o dispositivo for sincronizado. (0xC7D15078)    |    Este erro ocorre quando a transferência falha. Este erro pode ocorrer devido a ligações lentas ou problemas de Wi-Fi.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente.    |
|    O utilizador final cancelou a instalação da aplicação. (0xC7D14FB1)    |    O utilizador desinstalou explicitamente a aplicação. Este erro é retornado quando instalar o SO Android atividade foi cancelada pelo utilizador. O utilizador premiu o botão Cancelar quando o pedido de instalação do SO foi apresentado ou ignorou o pedido.        Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    O processo de transferência de ficheiros parou inesperadamente. (0xC7D15015)    |    O SO parou o processo de transferência antes de ser concluído. Este erro pode ocorrer se o dispositivo tiver pouca bateria ou a transferência demorar demasiado tempo.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    O serviço de transferência de ficheiros parou inesperadamente. A política será repetida na próxima vez que o dispositivo for sincronizado. (0xC7D1507C)    |    O SO parou o processo de transferência antes de ser concluído. Este erro pode ocorrer se o dispositivo tiver pouca bateria ou a transferência demorar demasiado tempo.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente.    |

### <a name="ios-errors"></a>Erros do iOS

| Mensagem/código de erro | Sugestões de resolução de problemas/descrição |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Agente de MDM da Apple retornado que o comando de instalação falhou. |
| (0x87D1313C) | A ligação de rede foi perdida, enquanto o URL do serviço de transferência atualizado foi enviado para o dispositivo. Especificamente, não foi possível encontrar um servidor com o nome de anfitrião especificado. |
| o dispositivo iOS está ocupado neste momento. (0x87D11388) | O dispositivo iOS estava ocupado, o que resultou num erro. |
| A instalação da aplicação falhou. (0x87D13B64) | Ocorreu uma falha de instalação da aplicação. São necessários registos XCODE para resolver este erro. |
| A aplicação é gerida, mas a expirou ou foi removida pelo utilizador. (0x87D13B66) | O utilizador desinstalado explicitamente a aplicação. Também é possível que a aplicação tenha expirado, mas que a transferência tenha falhado ou que a deteção da aplicação não corresponda à resposta do dispositivo.   Além disso, este erro pode ocorrer com base num erro da plataforma iOS 9.2.2. |
| A aplicação está agendada para instalação, mas precisa de um código de resgate para concluir a transação. (0x87D13B60) | Este erro normalmente ocorre com as aplicações da iOS Store que pagos aplicações. |
| A aplicação não foi detetada após a instalação foi concluída com êxito.   (0x87D1041C) | O processo de deteção de aplicação não corresponde com a resposta do dispositivo. |
| O utilizador rejeitou a oferta para instalar a aplicação. (0x87D13B62) | Durante a instalação da aplicação inicial, o usuário clicou em Cancelar. |
| O utilizador rejeitou a oferta para atualizar a aplicação. (0x87D13B63) | O usuário final clicou em Cancelar durante o processo de atualização. |
| Erro desconhecido (0x87D103E8) | Ocorreu um erro de instalação de aplicação desconhecido. Este é o erro resultante quando outros erros de não tem ocorrido. |
| Só pode instalar as aplicações VPP no iPad partilhado (-2016330861). | As aplicações têm de ser obtidas com o Apple Volume Purchase Program para instalar num iPad partilhado. |
| Não é possível instalar aplicações quando está desativado App Store (-2016330860).  | O Store da aplicação tem de estar ativada para o utilizador instalar a aplicação. |
| Não é possível encontrar a licença do VPP para a aplicação (-2016330859).  | Tente revogar e ao reatribuir a licença da aplicação. |
| Não é possível instalar aplicações de sistemas com o seu fornecedor MDM (-2016330858). | A instalação de aplicações que estão pré-instaladas pelo sistema operativo iOS não é um cenário suportado. |
| Não é possível instalar aplicações quando o dispositivo estiver no modo perdido (-2016330857). | Toda a utilização do dispositivo está bloqueada no modo perdido.   Desative o modo perdido para instalar aplicações. |
| Não é possível instalar aplicações quando o dispositivo estiver no modo de local público (-2016330856). | Tente adicionar este dispositivo a um grupo de exclusão para a política de configuração do modo de local público para instalar aplicações. |
| Não é possível instalar aplicações de 32 bits neste dispositivo (-2016330852). | O dispositivo não suporta a instalação de aplicações de 32 bits. Experimente a implementar a versão de 64 bits da aplicação. |
| Utilizador tem de iniciar sessão para o Store da aplicação (-2016330855). | O utilizador tem de entrar para a App Store, para que possa ser instalada a aplicação. |
| Problema desconhecido. Tente novamente (-2016330854). | A instalação da aplicação falhou devido a um motivo desconhecido.   Tente novamente mais tarde. |
| A instalação da aplicação falhou. Intune tentará novamente na próxima vez que o dispositivo é sincronizado (-2016330853). | A instalação da aplicação encontrou um erro de dispositivo. Sincronize o dispositivo para tente instalar novamente a aplicação. |

### <a name="other-installation-errors"></a>Outros erros de instalação

|    Mensagem/código de erro    |    Descrição    |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    0x80073CFF, 0x80CF201C (erro do cliente)    |    Para instalar esta aplicação, precisa de ter um sistema preparado para sideloading. Certifique-se de que o pacote de aplicação é iniciado com uma assinatura fidedigna e instalado num dispositivo associado a um domínio que tenha as **AllowAllTrustedApps** política ativada ou um dispositivo que tenha uma licença Sideload do Windows com o  **AllowAllTrustedApps** política ativada. Para obter mais informações, consulte [resolução de problemas de empacotamento, implementação e consulta de aplicações da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).     |
|    0x80073CF0    |    Não foi possível abrir o pacote. Causas possíveis:<ul><li> O pacote não está assinado.</li><li> O nome do publicador não corresponde ao assunto do certificado de assinatura.</li></ul> Verifique os **AppxPackagingOM** registo de eventos para obter informações. Para obter mais informações, consulte [resolução de problemas de empacotamento, implementação e consulta de aplicações da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CF3    |    O pacote de falha de atualização, dependência ou validação de conflito. Causas possíveis:<ul><li> O pacote recebido está em conflito com o pacote instalado.</li><li> Não foi encontrada uma dependência de pacote especificado.</li><li> O pacote não suporta a arquitetura de processador correta.</li></ul> Verifique os **AppXDeployment-Server** registo de eventos para obter informações. Para obter mais informações, consulte [resolução de problemas de empacotamento, implementação e consulta de aplicações da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CFB    |    O pacote fornecido já está instalado e a reinstalação do pacote está bloqueada. Poderá receber este erro se estiver a instalar um pacote que não é idêntico ao pacote que já está instalado. Verifique se a assinatura digital também faz parte do pacote. Quando um pacote é reconstruído ou assinado novamente, esse pacote já não é totalmente idêntico ao pacote anteriormente instalado. Existem duas opções possíveis para corrigir este erro:<ul><li> Incrementar o número de versão da aplicação e, em seguida, reconstruir e voltar a assinar o pacote.</li><li> Remova o pacote antigo de todos os utilizadores do sistema antes de instalar o novo pacote.</li></ul> Para obter mais informações, consulte [resolução de problemas de empacotamento, implementação e consulta de aplicações da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x87D1041C    |    A aplicação foi instalada com êxito, mas a aplicação não foi detetada. A aplicação foi implementada com êxito pelo Intune, e foi desinstalada posteriormente. As razões para a aplicação que está a ser desinstalado incluem:<ul><li> O utilizador final desinstalar a aplicação.</li><li> As informações de identidade do pacote não correspondem a dispositivos que os relatórios para aplicações ruins.</li><li>Para MSIs atualização automática, a versão do produto não corresponde às informações da aplicação depois de ser atualizado fora do Intune.</li></ul> Diga ao utilizador para reinstalar a aplicação a partir do portal da empresa. Tenha em atenção que as aplicações necessárias serão reinstaladas automaticamente quando o dispositivo verificação seguinte.    |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Resolução de problemas de aplicações da Loja Microsoft

As informações presentes no tópico [Resolução de problemas de empacotamento, implementação e consulta de aplicações da Loja Microsoft](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) ajudam-no a resolver problemas comuns que poderá encontrar ao instalar aplicações da Loja Microsoft, quer seja através do Intune ou de outros meios.

## <a name="next-steps"></a>Passos Seguintes

- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](known-issues.md).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](get-support.md).
