---
title: Resolver problemas com a instalação de aplicações
titlesuffix: Microsoft Intune
description: Utilize o painel de resolução de problemas do Microsoft Intune para o ajudar a resolver problemas com a instalação de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 65391ca620892dcd3b95719454dabc30eb35cb6f
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839385"
---
# <a name="troubleshoot-app-installation-issues"></a>Resolver problemas com a instalação de aplicações

Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. O Microsoft Intune disponibiliza detalhes da falha na instalação da aplicação que permitem que os operadores de suporte técnico e os administradores do Intune vejam informações da aplicação para resolver pedidos de ajuda do utilizador. O painel de resolução de problemas no Intune proporciona os detalhes da falha, incluindo detalhes sobre as aplicações geridas no dispositivo de um utilizador. São disponibilizados detalhes sobre o ciclo de vida ponto a ponto de uma aplicação em cada dispositivo individual no painel **Aplicações Geridas**. Pode ver os problemas de instalação, como quando a aplicação foi criada, modificada, direcionada e entregue a um dispositivo. 

## <a name="to-review-app-troubleshooting-details"></a>Para rever os detalhes da resolução de problemas com a aplicação

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

## <a name="app-installation-errors"></a>Erros de instalação da aplicação

As seguintes mensagens de erro e descrições fornecem detalhes sobre erros de instalação no Android e no iOS. 

### <a name="android-errors"></a>Erros do Android

|    Mensagem/código de erro    |    Descrição    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    A instalação da aplicação falhou. (0xC7D14FB5)    |    Esta mensagem de erro é apresentada quando o Intune não consegue determinar a causa raiz do erro de instalação da aplicação Android. Não são fornecidas informações pelo Android durante a falha.       Este erro é apresentado quando a APK é transferida com êxito, mas a instalação da aplicação falhou. Este erro poderá ocorrer de forma mais comum devido a um ficheiro APK incorreto que não pode ser instalado no dispositivo. Uma causa possível poderá ser caso o Google Play Protect bloqueie a instalação da aplicação devido a questões de segurança. Outra causa possível deste erro é um dispositivo não suportar a aplicação. Por exemplo, se a aplicação necessitar da versão 21 ou posterior da API e o dispositivo tiver a versão 19 da API.         O Intune apresenta este erro em dispositivos KNOX e DA. Apesar de poder ser apresentada uma notificação na qual os utilizadores podem clicar para tentar novamente, se existir um problema com a APK, não ocorrerão mais falhas. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.        |
|    A instalação da aplicação foi cancelada porque o ficheiro de instalação (APK) foi eliminado depois da transferência, mas antes da instalação. (0xC7D14FBA)    |    A APK foi transferida com êxito, mas o ficheiro foi removido do dispositivo antes de o utilizador instalar a aplicação. Isto poderá ocorrer se existir um intervalo de tempo grande entre a transferência e a instalação. Por exemplo, o utilizador cancelou a instalação original, aguardou e, em seguida, clicou na notificação para tentar novamente.         Esta mensagem de erro só é apresentada para cenários de DA. Os cenários de KNOX podem ser realizados automaticamente. Apresentamos uma notificação Tentar novamente para que o utilizador possa aceitar em vez de cancelar. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    A instalação da aplicação foi cancelada porque o processo foi reiniciado durante a instalação. (0xC7D14FBB)    |    O dispositivo foi reiniciado durante o processo de instalação da APK, causando o cancelamento da instalação.        Esta mensagem de erro é apresentada em dispositivos KNOX e DA. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    A aplicação não foi detetada depois de a instalação ter sido concluída com êxito. (0x87D1041C)    |    O utilizador desinstalou explicitamente a aplicação. Este erro não é devolvido do cliente. É um erro apresentado quando uma aplicação é instalada a determinada altura e depois desinstalada pelo utilizador. Este erro só deverá ocorrer em aplicações necessárias. Os utilizadores podem desinstalar aplicações não necessárias. Este erro só pode ocorrer em dispositivos DA. Os dispositivos KNOX bloqueiam a desinstalação de aplicações geridas.       A sincronização seguinte irá voltar a apresentar a notificação no dispositivo para o utilizador instalar.   O utilizador pode ignorar a notificação. Este erro continuará a ser apresentado até que o utilizador instale a aplicação.    |
|    A transferência falhou devido a um erro desconhecido. (0xC7D14FB2)    |    Este erro ocorre quando a transferência falha. Este erro pode ocorrer devido a ligações lentas ou problemas de Wi-Fi.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    A transferência falhou devido a um erro desconhecido. A política será repetida na próxima vez que o dispositivo for sincronizado. (0xC7D15078)    |    Este erro ocorre quando a transferência falha. Este erro pode ocorrer devido a ligações lentas ou problemas de Wi-Fi.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente.    |
|    O utilizador final cancelou a instalação de aplicações. (0xC7D14FB1)    |    O utilizador desinstalou explicitamente a aplicação. Este erro é devolvido quando a atividade de instalação do SO Android é cancelada pelo utilizador. O utilizador premiu o botão Cancelar quando o pedido de instalação do SO foi apresentado ou ignorou o pedido.        Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    O processo de transferência de ficheiros parou inesperadamente. (0xC7D15015)    |    O SO parou o processo de transferência antes de ser concluído. Este erro pode ocorrer se o dispositivo tiver pouca bateria ou a transferência demorar demasiado tempo.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente. O Intune apresenta uma notificação na qual os utilizadores podem clicar para tentar novamente. No caso de se tratar de uma aplicação disponível, a notificação pode ser dispensada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada.    |
|    O serviço de transferência de ficheiros parou inesperadamente. A política será repetida na próxima vez que o dispositivo for sincronizado. (0xC7D1507C)    |    O SO parou o processo de transferência antes de ser concluído. Este erro pode ocorrer se o dispositivo tiver pouca bateria ou a transferência demorar demasiado tempo.       Este erro só é devolvido em cenários de DA. Em cenários de KNOX, não é apresentado nenhum pedido de instalação ao utilizador e esta operação pode ser feita automaticamente.    |

### <a name="ios-errors"></a>Erros do iOS

|    Mensagem/código de erro    |    Descrição    |
|:----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    (0x87D12906)    |    O Agente MDM da Apple comunicou que o comando da instalação falhou.        |
|    (0x87D1313C)    |    A ligação de rede foi perdida durante o envio do URL do serviço de transferência atualizado para o dispositivo. Mais concretamente, não foi possível encontrar um servidor com o nome de anfitrião especificado.    |
|    O dispositivo iOS está ocupado neste momento. (0x87D11388)    |    O dispositivo iOS estava ocupado, o que resultou num erro.    |
|    A instalação da aplicação falhou. (0x87D13B64)    |    Ocorreu uma falha ao instalar a aplicação. São necessários registos XCODE para resolver este erro.    |
|    A aplicação é gerida, mas expirou ou foi removida pelo utilizador. (0x87D13B66)    |    O utilizador desinstalou explicitamente a aplicação. Também é possível que a aplicação tenha expirado, mas que a transferência tenha falhado ou que a deteção da aplicação não corresponda à resposta do dispositivo.   Além disso, este erro pode ocorrer com base num erro da plataforma iOS 9.2.2.    |
|    A aplicação está agendada para instalação, mas precisa de um código de resgate para concluir a transação.   (0x87D13B60)    |    Este erro ocorre normalmente com aplicações pagas da loja iOS.     |
|    A aplicação não foi detetada depois de a instalação ter sido concluída com êxito. (0x87D1041C)    |    O processo de deteção da aplicação não corresponde à resposta do dispositivo.    |
|    O utilizador rejeitou a oferta para instalar a aplicação. (0x87D13B62)    |    Durante a instalação inicial da aplicação, o utilizador clicou em Cancelar.    |
|    O utilizador rejeitou a oferta para atualizar a aplicação. (0x87D13B63)    |    O utilizador final clicou em Cancelar durante o processo de atualização.     |
|    Erro desconhecido (0x87D103E8)    |    Ocorreu um erro de instalação da aplicação desconhecido. Este é o erro resultante se não ocorrer nenhum dos outros erros.    |

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
