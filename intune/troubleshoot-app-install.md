---
title: Resolver problemas com a instalação de aplicações
titleSuffix: Microsoft Intune
description: Utilize o painel de resolução de problemas do Microsoft Intune para o ajudar a resolver problemas com a instalação de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa723942c9633a3851f75e3e08bf843cbb4bdf55
ms.sourcegitcommit: a25cd79a33feb536d9b2fc11aa7d3e3972f1ca5a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70842162"
---
# <a name="troubleshoot-app-installation-issues"></a>Resolver problemas com a instalação de aplicações

Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. O Microsoft Intune disponibiliza detalhes da falha na instalação da aplicação que permitem que os operadores de suporte técnico e os administradores do Intune vejam informações da aplicação para resolver pedidos de ajuda do utilizador. O painel de resolução de problemas no Intune proporciona os detalhes da falha, incluindo detalhes sobre as aplicações geridas no dispositivo de um utilizador. São disponibilizados detalhes sobre o ciclo de vida ponto a ponto de uma aplicação em cada dispositivo individual no painel **Aplicações Geridas**. Pode ver os problemas de instalação, como quando a aplicação foi criada, modificada, direcionada e entregue a um dispositivo. 

## <a name="app-troubleshooting-details"></a>Detalhes da solução de problemas do aplicativo

O Intune proporciona detalhes da resolução de problemas com a aplicação com base nas aplicações instaladas no dispositivo de um utilizador específico.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
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

Os detalhes do erro da instalação da aplicação irão indicar o problema. Pode usar estes detalhes para determinar a melhor ação a tomar para resolver o problema. Para obter mais informações sobre como solucionar problemas de instalação do aplicativo, consulte [erros de instalação do aplicativo](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>A instalação do aplicativo de destino do grupo de usuários não atinge o dispositivo
As ações a seguir devem ser consideradas quando você tiver problemas ao instalar aplicativos:
- Se o aplicativo não for exibido no Portal da Empresa, verifique se o aplicativo está implantado com a intenção **disponível** e se o usuário está acessando o portal da empresa com o tipo de dispositivo com suporte no aplicativo.
- Para dispositivos Windows BYOD, o usuário precisa adicionar uma conta de trabalho ao dispositivo.
- Verifique se o usuário está acima do limite de dispositivos do AAD:
  1. Navegue até [Azure Active Directory configurações do dispositivo](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Anote o valor definido para máximo de **dispositivos por usuário**.
  3. Navegue até [Azure Active Directory usuários](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Selecione o usuário afetado e clique em **dispositivos**.
  5. Se o usuário estiver acima do limite definido, exclua os registros obsoletos que não são mais necessários.
- Para dispositivos do iOS DEP, verifique se o usuário está listado como **registrado pelo usuário** na folha de visão geral do dispositivo do Intune. Se aparecer NA, implante uma política de configuração para o Portal da Empresa do Intune. Para obter mais informações, consulte [Configurar o aplicativo portal da empresa](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Solução de problemas de instalação do aplicativo Win32

Selecione o aplicativo Win32 que foi implantado usando a extensão de gerenciamento do Intune. Você pode selecionar a opção **coletar logs** quando a instalação do aplicativo Win32 falhar. 

> [!IMPORTANT]
> A opção **coletar logs** não será habilitada quando o aplicativo Win32 tiver sido instalado com êxito no dispositivo.<p>Antes de coletar informações de log do aplicativo Win32, a extensão de gerenciamento do Intune deve ser instalada no cliente do Windows. A extensão de gerenciamento do Intune é instalada quando um script do PowerShell ou um aplicativo Win32 é implantado em um usuário ou grupo de segurança de dispositivo. Para obter mais informações, consulte [extensão de gerenciamento do Intune-pré-requisitos](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Coletar arquivo de log

Para coletar os logs de instalação do aplicativo Win32, primeiro siga as etapas fornecidas na seção [detalhes de solução de problemas do aplicativo](troubleshoot-app-install.md#app-troubleshooting-details). Em seguida, continue com as seguintes etapas:

1. Clique na opção **coletar logs** na folha **detalhes da instalação** .

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Forneça caminhos de arquivo com nomes de arquivo de log para iniciar o processo de coleta de arquivo de log e clique em **OK**.
    
    > [!NOTE]
    > A coleta de log levará menos de duas horas. Tipos de arquivo com suporte: *. log,. txt,. dmp,. cab,. zip,. xml,. evtx e. Evtl*. São permitidos no máximo 25 caminhos de arquivo.

3. Depois que os arquivos de log tiverem sido coletados, você poderá selecionar o link **logs** para baixar os arquivos de log.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Uma notificação será exibida indicando o êxito da coleta de log do aplicativo.

#### <a name="win32-log-collection-requirements"></a>Requisitos de coleta de log do Win32

Há requisitos específicos que devem ser seguidos para coletar arquivos de log:

- Você deve especificar o caminho completo do arquivo de log. 
- Você pode especificar variáveis de ambiente para coleta de log, como as seguintes:<br>
  *% PROGRAMFILES%,% PROGRAMDATA%% PUBLIC%,% WINDIR%,% TEMP%,% TMP%*
- Somente as extensões de arquivo exatas são permitidas, como:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- O arquivo de log máximo a ser carregado é 60 MB ou 25 arquivos, o que ocorrer primeiro. 
- A coleta de log de instalação do aplicativo Win32 está habilitada para aplicativos que atendem à tentativa de atribuição de aplicativo necessária, disponível e desinstalação.
- Os logs armazenados são criptografados para proteger qualquer informação de identificação pessoal contida nos logs.
- Ao abrir tíquetes de suporte para falhas de aplicativo Win32, anexe os logs de falha relacionados usando as etapas fornecidas acima.

## <a name="app-installation-errors"></a>Erros de instalação da aplicação

As seguintes mensagens de erro e descrições fornecem detalhes sobre erros de instalação no Android e no iOS. 

### <a name="android-errors"></a>Erros do Android

Esta seção menciona tanto o administrador do dispositivo quanto o registro Samsung Knox. Para obter mais informações, consulte [registro de administrador do dispositivo Android](android-enroll-device-administrator.md) e [registrar automaticamente dispositivos Android usando o registro móvel do Knox do Samsung](android-samsung-knox-mobile-enroll.md). 

| Mensagem de erro/código | Descrição |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Falha ao instalar o aplicativo. (0xC7D14FB5) | Essa mensagem de erro é exibida quando o Intune não pode determinar a causa raiz do erro de instalação do aplicativo do Android. Não são fornecidas informações pelo Android durante a falha. Esse erro é retornado quando o download do APK foi bem-sucedido, mas a instalação do aplicativo falhou. Esse erro pode ocorrer com mais frequência devido a um arquivo APK inadequado que não pode ser instalado no dispositivo. Uma possível causa pode ser quando Google Play proteger bloqueia a instalação do aplicativo devido a questões de segurança. Outra causa possível desse erro é quando um dispositivo não dá suporte ao aplicativo. Por exemplo, se o aplicativo exigir a versão da API 21 + e o dispositivo tiver a versão 19 da API no momento. O Intune retorna esse erro para os dispositivos DA e KNOX e, embora possa haver uma notificação de que os usuários possam clicar para tentar novamente, se houver um problema com o APK, ele nunca continuará a falhar. Se o aplicativo for um aplicativo disponível, a notificação poderá ser ignorada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada. |
| A instalação do aplicativo foi cancelada porque o arquivo de instalação (APK) foi excluído após o download, mas antes da instalação. (0xC7D14FBA) | O download do APK foi bem-sucedido, mas antes de o usuário instalar o aplicativo, o arquivo foi removido do dispositivo. Isso pode acontecer se houvesse uma grande diferença de tempo entre download e instalação. Por exemplo, o usuário cancelou a instalação original, esperou e, em seguida, clicou na notificação para tentar novamente. Essa mensagem de erro é retornada para apenas cenários DA dos. Os cenários do KNOX podem ser realizados silenciosamente. Apresentamos uma notificação para tentar novamente para que o usuário possa aceitar em vez de cancelar. Se o aplicativo for um aplicativo disponível, a notificação poderá ser ignorada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada. |
| A instalação do aplicativo foi cancelada porque o processo foi reiniciado durante a instalação. (0xC7D14FBB) | O dispositivo foi reinicializado durante o processo de instalação do APK, resultando em uma instalação cancelada. Essa mensagem de erro é retornada para dispositivos DA e KNOX. O Intune apresenta uma notificação de que os usuários podem clicar para tentar novamente. Se o aplicativo for um aplicativo disponível, a notificação poderá ser ignorada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada. |
| O aplicativo não foi detectado após a instalação ter sido concluída com êxito. (0x87D1041C) | O usuário desinstalou explicitamente o aplicativo. Esse erro não é retornado do cliente. É um erro produzido quando o aplicativo foi instalado em um ponto, mas depois o usuário o desinstalou. Esse erro só deve ocorrer para os aplicativos necessários. Os utilizadores podem desinstalar aplicações não necessárias. Esse erro só pode ocorrer no DA. Os dispositivos KNOX bloqueiam a desinstalação de aplicações geridas. A próxima sincronização republicará a notificação no dispositivo para o usuário instalar. O utilizador pode ignorar a notificação. Esse erro continuará a ser relatado até que o usuário instale o aplicativo. |
| O download falhou devido a um erro desconhecido. (0xC7D14FB2) | Esse erro ocorre quando o download falha. Esse erro pode ocorrer normalmente devido a problemas de Wi-Fi ou conexões lentas. Esse erro é retornado somente para cenários DA dos. Para cenários do KNOX, o usuário não precisa instalar, isso pode ser feito silenciosamente. O Intune apresenta uma notificação de que os usuários podem clicar para tentar novamente. Se o aplicativo for um aplicativo disponível, a notificação poderá ser ignorada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada. |
| O download falhou devido a um erro desconhecido. A política será repetida na próxima vez em que o dispositivo for sincronizado. (0xC7D15078) | Esse erro ocorre quando o download falha. Esse erro pode ocorrer normalmente devido a problemas de Wi-Fi ou conexões lentas. Esse erro é retornado somente para cenários DA dos. Para cenários do KNOX, o usuário não precisa instalar, isso pode ser feito silenciosamente. |
| O usuário final cancelou a instalação do aplicativo. (0xC7D14FB1) | O usuário desinstalou explicitamente o aplicativo. Esse erro é retornado quando a atividade de instalação do sistema operacional Android foi cancelada pelo usuário. O usuário pressionou o botão Cancelar quando o prompt de instalação do sistema operacional foi apresentado ou clicou fora do prompt. Esse erro é retornado somente para cenários DA dos. Para cenários do KNOX, o usuário não precisa instalar, isso pode ser feito silenciosamente. O Intune apresenta uma notificação de que os usuários podem clicar para tentar novamente. Se o aplicativo for um aplicativo disponível, a notificação poderá ser ignorada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada. Peça ao usuário para não cancelar a instalação. |
| O processo de download do arquivo foi interrompido inesperadamente. (0xC7D15015) | O sistema operacional interrompeu o processo de download antes de ser concluído. Esse erro pode ocorrer quando o dispositivo tem bateria fraca ou o download está demorando muito. Esse erro é retornado somente para cenários DA dos. Para cenários do KNOX, o usuário não precisa instalar, isso pode ser feito silenciosamente. O Intune apresenta uma notificação de que os usuários podem clicar para tentar novamente. Se o aplicativo for um aplicativo disponível, a notificação poderá ser ignorada. No entanto, se a aplicação for necessária, a notificação não pode ser dispensada. Verifique se o dispositivo tem uma conexão de rede confiável.  |
| O serviço de download de arquivo foi interrompido inesperadamente. A política será repetida na próxima vez em que o dispositivo for sincronizado. (0xC7D1507C) | O sistema operacional finalizou o processo de download antes de ser concluído. Esse erro pode ocorrer quando o dispositivo tem bateria fraca ou o download está demorando muito. Esse erro é retornado somente para cenários DA dos. Para cenários do KNOX, o usuário não precisa instalar, isso pode ser feito silenciosamente. Sincronize manualmente o dispositivo ou aguarde 24 horas e verifique o status. |
| Falha ao desinstalar o aplicativo. (0xc7d14fb8) | Esse erro é uma falha de desinstalação genérica. O sistema operacional não especificou por que houve falha na desinstalação do aplicativo. Alguns aplicativos de administrador não podem simplesmente ser desinstalados. Verifique se o aplicativo pode ser desinstalado manualmente e colete os logs de Portal da Empresa se a desinstalação falhar. |
| O arquivo APK de instalação do aplicativo usado para a atualização não corresponde à assinatura do aplicativo atual no dispositivo. (0xc7d14fb7) | O sistema operacional Android tem a limitação de exigir que o certificado de assinatura para a versão de atualização seja exatamente o mesmo que o certificado usado para assinar a versão existente. Se o desenvolvedor não puder usar o mesmo certificado para assinar a nova versão, será necessário desinstalar o aplicativo existente e reimplantar o novo aplicativo em vez de atualizar o aplicativo existente. |
| O usuário final cancelou a instalação do aplicativo. (0xc7d14fb9) | Instrua o usuário a aceitar o aplicativo do Intune implantado e instalar o aplicativo quando solicitado. |
| A desinstalação do aplicativo foi cancelada porque o processo foi reiniciado durante a instalação. (0xc7d14fbc) | O processo de instalação do aplicativo foi encerrado pelo sistema operacional ou o dispositivo foi reiniciado. Tente instalar novamente e coletar logs de Portal da Empresa se esse erro ocorrer novamente. |
| O arquivo APK de instalação do aplicativo não pode ser instalado porque não foi assinado. (0xc7d14fb6) | Por padrão, o sistema operacional Android requer que OS aplicativos sejam assinados. Verifique se o aplicativo está assinado antes da implantação. |

### <a name="ios-errors"></a>Erros do iOS

| Mensagem de erro/código | Descrição/dicas de solução de problemas |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | O agente MDM da Apple retornou que o comando de instalação falhou. |
| (0x87D1313C) | A conexão de rede foi perdida enquanto a URL do serviço de download atualizada foi enviada para o dispositivo. Especificamente, um servidor com o nome de host especificado não pôde ser encontrado. |
| o dispositivo iOS está ocupado no momento. (0x87D11388) | O dispositivo iOS estava ocupado, o que resultou em um erro. O dispositivo foi bloqueado. O usuário precisa desbloquear o dispositivo para instalar o aplicativo. |
| Falha na instalação do aplicativo. (0x87D13B64) | Ocorreu uma falha na instalação do aplicativo. os logs do console do iOS são necessários para solucionar esse erro. |
| O aplicativo é gerenciado, mas expirou ou foi removido pelo usuário. (0x87D13B66) | O usuário desinstalou explicitamente o aplicativo ou o aplicativo expirou, mas não pôde ser baixado ou a detecção do aplicativo não corresponde à resposta do dispositivo. Além disso, este erro pode ocorrer com base num erro da plataforma iOS 9.2.2. |
| O aplicativo está agendado para instalação, mas precisa de um código de resgate para concluir a transação. (0x87D13B60) | Esse erro normalmente ocorre com aplicativos da iOS Store que são aplicativos pagos. |
| O aplicativo não foi detectado após a instalação ter sido concluída com êxito. (0x87D1041C) | O processo de detecção do aplicativo não correspondeu à resposta do dispositivo. |
| O usuário rejeitou a oferta para instalar o aplicativo. (0x87D13B62) | Durante a instalação inicial do aplicativo, o usuário clicou em cancelar. Peça ao usuário para aceitar a solicitação de instalação na próxima vez. |
| O usuário rejeitou a oferta para atualizar o aplicativo. (0x87D13B63) | O usuário final clicou em cancelar durante o processo de atualização. Implante conforme necessário ou instrua o usuário a aceitar o prompt de atualização. |
| Erro desconhecido (0x87D103E8) | Ocorreu um erro desconhecido na instalação do aplicativo. Esse é o erro resultante quando outros erros não ocorreram. |
| Só é possível instalar aplicativos VPP no iPad compartilhado (-2016330861). | Os aplicativos devem ser obtidos usando Apple Volume Purchase Program para instalar o em um iPad compartilhado. |
| Não é possível instalar aplicativos quando a loja de aplicativos está desabilitada (-2016330860). | A loja de aplicativos deve ser habilitada para que o usuário instale o aplicativo. |
| Não é possível localizar a licença VPP para o aplicativo (-2016330859). | Tente revogar e reatribuir a licença do aplicativo. |
| Não é possível instalar aplicativos de sistema com seu provedor de MDM (-2016330858). | A instalação de aplicativos pré-instalados pelo sistema operacional iOS não é um cenário com suporte. |
| Não é possível instalar aplicativos quando o dispositivo está no modo perdido (-2016330857). | Todo o uso do dispositivo é bloqueado no modo perdido. Desabilitar o modo perdido para instalar aplicativos. |
| Não é possível instalar aplicativos quando o dispositivo está no modo de quiosque (-2016330856). | Tente adicionar este dispositivo a um grupo de exclusão para a política de configuração do modo de quiosque para instalar aplicativos. |
| Não é possível instalar aplicativos de 32 bits neste dispositivo (-2016330852). | O dispositivo não dá suporte à instalação de aplicativos de 32 bits. Tente implantar a versão de 64 bits do aplicativo. |
| O usuário deve entrar na loja de aplicativos (-2016330855). | O usuário precisa entrar na App Store para que o aplicativo possa ser instalado. |
| Problema desconhecido. Tente novamente (-2016330854). | A instalação do aplicativo falhou devido a um motivo desconhecido. Tente novamente mais tarde. |
| Falha na instalação do aplicativo. O Intune tentará novamente na próxima vez em que o dispositivo for sincronizado (-2016330853). | A instalação do aplicativo encontrou um erro de dispositivo. Sincronize o dispositivo para tentar instalar o aplicativo novamente. |
| A atribuição de licença falhou com o erro da Apple ' não há licenças de VPP restantes ' (0x87d13b7e) | Este comportamento é por predefinição. Para resolver isso, adquira licenças VPP adicionais ou solicite licenças de usuários que não são mais direcionadas. |
| Falha na instalação do aplicativo 12024: Causa desconhecida. (0x87d13b6e) | A Apple não nos forneceu informações suficientes para determinar por que a instalação falhou. Nada para relatar. |
| Política de configuração de aplicativo necessária não presente, verifique se a política é destinada aos mesmos grupos. (0x87d13b7f) | O aplicativo requer configuração de aplicativo, mas nenhuma configuração de aplicativo é direcionada. O administrador deve garantir que os grupos aos quais o aplicativo se destina também tenham a configuração de aplicativo necessária direcionada para os grupos. |
| O licenciamento do VPP do dispositivo é aplicável somente a dispositivos iOS 9.0 +. (0x87d13b69) | Atualizar dispositivos iOS afetados para iOS 9.0 +. |
| O aplicativo está instalado no dispositivo, mas não é gerenciado. (0x87d13b8f) | Esse erro ocorre apenas para aplicativos LOB. O aplicativo foi instalado fora do Intune. Para resolver esse erro, desinstale o aplicativo do dispositivo. Na próxima vez que a sincronização do dispositivo ocorrer, o dispositivo deverá instalar o aplicativo do Intune. |
| Gerenciamento de aplicativo recusado pelo usuário (0x87d13b68) | Peça ao usuário para aceitar o gerenciamento de aplicativos. |
| Erro desconhecido. (0x87d1279d) | Esse erro ocorre em aplicativos da iOS Store, mas o cenário de erro é desconhecido. |
| A versão mais recente do aplicativo não pôde ser atualizada de uma versão anterior. (0x87D13B9D) | Essa mensagem de erro será exibida se o aplicativo estiver instalado e gerenciado, mas com a versão incorreta no dispositivo. Essa situação inclui quando um dispositivo recebe um comando para atualizar um aplicativo, mas a nova versão ainda não foi instalada e relatada. Esse erro será relatado para o primeiro check-in de um dispositivo depois que a atualização tiver sido implantada e ocorrerá até que o dispositivo relate que a nova versão está instalada ou falhe devido a um erro diferente.  |


### <a name="other-installation-errors"></a>Outros erros de instalação

|  Mensagem de erro/código  |  Descrição  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (erro do cliente)  |  Para instalar esta aplicação, precisa de ter um sistema preparado para sideloading. Verifique se o pacote do aplicativo está assinado com uma assinatura confiável e instalado em um dispositivo ingressado no domínio que tenha a política **AllowAllTrustedApps** habilitada ou um dispositivo que tenha uma licença de Sideload do Windows com a política **AllowAllTrustedApps** habilitado. Para obter mais informações, consulte [solução de problemas de empacotamento, implantação e consulta de aplicativos da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).   |
|  0x80073CF0  |  Não foi possível abrir o pacote. Causas possíveis:<ul><li> O pacote não está assinado.</li><li> O nome do Publicador não corresponde ao assunto do certificado de autenticação.</li></ul> Verifique o log de eventos do **AppxPackagingOM** para obter informações. Para obter mais informações, consulte [solução de problemas de empacotamento, implantação e consulta de aplicativos da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CF3  |  Falha na atualização, dependência ou validação de conflito do pacote. Causas possíveis:<ul><li> O pacote de entrada está em conflito com um pacote instalado.</li><li> Uma dependência de pacote especificada não foi encontrada.</li><li> O pacote não oferece suporte à arquitetura de processador correta.</li></ul> Verifique o log de eventos do **AppXDeployment-Server** para obter informações. Para obter mais informações, consulte [solução de problemas de empacotamento, implantação e consulta de aplicativos da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CFB  |  O pacote fornecido já está instalado e a reinstalação do pacote está bloqueada. Você poderá receber esse erro se estiver instalando um pacote que não é idêntico ao pacote que já está instalado. Verifique se a assinatura digital também faz parte do pacote. Quando um pacote é reconstruído ou assinado novamente, esse pacote já não é totalmente idêntico ao pacote anteriormente instalado. Existem duas opções possíveis para corrigir este erro:<ul><li> Aumente o número de versão do aplicativo e, em seguida, recompile e assine novamente o pacote.</li><li> Remova o pacote antigo para cada usuário no sistema antes de instalar o novo pacote.</li></ul> Para obter mais informações, consulte [solução de problemas de empacotamento, implantação e consulta de aplicativos da Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x87D1041C  |  A aplicação foi instalada com êxito, mas a aplicação não foi detetada. O aplicativo foi implantado com êxito pelo Intune e, subsequentemente, desinstalado. Os motivos para o aplicativo que está sendo desinstalado incluem:<ul><li> O usuário final desinstalou o aplicativo.</li><li> As informações de identidade no pacote não correspondem aos relatórios de dispositivo para aplicativos ruins.</li><li>Para MSIs de atualização automática, a versão do produto não corresponde às informações do aplicativo depois que ele é atualizado fora do Intune.</li></ul> Diga ao utilizador para reinstalar a aplicação a partir do portal da empresa. Observe que os aplicativos necessários serão reinstalados automaticamente quando o dispositivo fizer check-in.  |
|  0x8000FFFF  |  Ocorreu um erro inesperado durante a instalação. Verifique os logs de instalação para obter informações adicionais.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Resolução de problemas de aplicações da Loja Microsoft

As informações presentes no tópico [Resolução de problemas de empacotamento, implementação e consulta de aplicações da Loja Microsoft](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) ajudam-no a resolver problemas comuns que poderá encontrar ao instalar aplicações da Loja Microsoft, quer seja através do Intune ou de outros meios.

## <a name="app-troubleshooting-resources"></a>Recursos de solução de problemas do aplicativo
- [Implantando o Visio e o Project como parte da sua implantação do Office Pro Plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Tome medidas para garantir que os aplicativos MSfB implantados por meio da instalação do Intune no Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Solucionando problemas de implantações de aplicativo MSI no Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Práticas recomendadas para distribuição de software para o agente do computador Windows clássico do Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Passos Seguintes

- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, consulte [sucesso do cliente do Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](get-support.md).
