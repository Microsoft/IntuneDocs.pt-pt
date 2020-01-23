---
title: Resolver problemas com a instalação de aplicações
titleSuffix: Microsoft Intune
description: Utilize o painel de resolução de problemas do Microsoft Intune para o ajudar a resolver problemas com a instalação de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540984"
---
# <a name="troubleshoot-app-installation-issues"></a>Resolver problemas com a instalação de aplicações

Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. O Microsoft Intune disponibiliza detalhes da falha na instalação da aplicação que permitem que os operadores de suporte técnico e os administradores do Intune vejam informações da aplicação para resolver pedidos de ajuda do utilizador. O painel de resolução de problemas no Intune proporciona os detalhes da falha, incluindo detalhes sobre as aplicações geridas no dispositivo de um utilizador. São disponibilizados detalhes sobre o ciclo de vida ponto a ponto de uma aplicação em cada dispositivo individual no painel **Aplicações Geridas**. Pode ver os problemas de instalação, como quando a aplicação foi criada, modificada, direcionada e entregue a um dispositivo. 

> [!NOTE]
> Para obter informações sobre códigos de erro de instalação de aplicativo específico, consulte [referência de erro de instalação de aplicativo do Intune](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Detalhes da solução de problemas do aplicativo

O Intune proporciona detalhes da resolução de problemas com a aplicação com base nas aplicações instaladas no dispositivo de um utilizador específico.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **solução de problemas + suporte**.
4. Clique em **Selecionar utilizador** para selecionar um utilizador para o qual quer executar a resolução de problemas. O painel **Selecionar utilizadores** será apresentado.
5. Selecione um utilizador ao escrever o nome ou endereço de e-mail. Clique em **Selecionar** na parte inferior do painel. As informações de resolução de problemas do utilizador são apresentadas no painel **Resolução de problemas**. 
6. Selecione o dispositivo com o qual quer resolver problemas na lista **Dispositivos**.
    ![O painel de Resolução de Problemas do Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Selecione **Aplicações Geridas** a partir do painel do dispositivo selecionado. É apresentada uma lista de aplicações geridas.
    ![Detalhes de um dispositivo específico gerido pelo Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Selecione uma aplicação na lista onde o **Estado da Instalação** indicar uma falha.
    ![Uma aplicação selecionada que mostra detalhes da falha na instalação.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > A mesma aplicação pode ser atribuída a vários grupos, mas com diferentes ações pretendidas (intenções) para a aplicação. Por exemplo, uma intenção resolvida para uma aplicação apresentará a indicação **excluída** se a aplicação estiver excluída para um utilizador durante a atribuição de aplicações. Para obter mais informações, veja [Como são resolvidos conflitos entre intenções de aplicações](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Se ocorrer uma falha na instalação de uma aplicação necessária, o utilizador ou o suporte técnico poderá sincronizar o dispositivo e repetir a instalação da aplicação.

Os detalhes do erro da instalação da aplicação irão indicar o problema. Pode usar estes detalhes para determinar a melhor ação a tomar para resolver o problema. Para obter mais informações sobre como solucionar problemas de instalação do aplicativo, consulte [erros de instalação do aplicativo Android](app-install-error-codes.md#android-app-installation-errors) e [erros de instalação do aplicativo IOS](app-install-error-codes.md#ios-app-installation-errors).

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>A instalação do aplicativo de destino do grupo de usuários não atinge o dispositivo
As ações a seguir devem ser consideradas quando você tiver problemas ao instalar aplicativos:
- Se o aplicativo não for exibido no Portal da Empresa, verifique se o aplicativo está implantado com a intenção **disponível** e se o usuário está acessando o portal da empresa com o tipo de dispositivo com suporte no aplicativo.
- Para dispositivos Windows BYOD, o usuário precisa adicionar uma conta de trabalho ao dispositivo.
- Verifique se o usuário está acima do limite de dispositivos do AAD:
  1. Navegue até [Azure Active Directory configurações do dispositivo](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Anote o valor definido para máximo de **dispositivos por usuário**.
  3. Navegue até [Azure Active Directory usuários](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Selecione o usuário afetado e clique em **dispositivos**.
  5. Se o usuário estiver acima do limite definido, exclua os registros obsoletos que não são mais necessários.
- Para dispositivos do iOS DEP, verifique se o usuário está listado como **registrado pelo usuário** no painel Visão geral do dispositivo do Intune. Se aparecer NA, implante uma política de configuração para o Portal da Empresa do Intune. Para obter mais informações, consulte [Configurar o aplicativo portal da empresa](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Solução de problemas de instalação do aplicativo Win32

Selecione o aplicativo Win32 que foi implantado usando a extensão de gerenciamento do Intune. Você pode selecionar a opção **coletar logs** quando a instalação do aplicativo Win32 falhar. 

> [!IMPORTANT]
> A opção **coletar logs** não será habilitada quando o aplicativo Win32 tiver sido instalado com êxito no dispositivo.<p>Antes de coletar informações de log do aplicativo Win32, a extensão de gerenciamento do Intune deve ser instalada no cliente do Windows. A extensão de gerenciamento do Intune é instalada quando um script do PowerShell ou um aplicativo Win32 é implantado em um usuário ou grupo de segurança de dispositivo. Para obter mais informações, consulte [extensão de gerenciamento do Intune-pré-requisitos](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Coletar arquivo de log

Para coletar os logs de instalação do aplicativo Win32, primeiro siga as etapas fornecidas na seção [detalhes de solução de problemas do aplicativo](troubleshoot-app-install.md#app-troubleshooting-details). Em seguida, continue com as seguintes etapas:

1. Clique na opção **coletar logs** no painel **detalhes da instalação** .

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Forneça caminhos de arquivo com nomes de arquivo de log para iniciar o processo de coleta de arquivo de log e clique em **OK**.

    > [!NOTE]
    > A coleta de log levará menos de duas horas. Tipos de arquivo com suporte: *. log,. txt,. dmp,. cab,. zip,. xml,. evtx e. Evtl*. São permitidos no máximo 25 caminhos de arquivo.

3. Depois que os arquivos de log tiverem sido coletados, você poderá selecionar o link **logs** para baixar os arquivos de log.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Uma notificação será exibida indicando o êxito da coleta de log do aplicativo.

#### <a name="win32-log-collection-requirements"></a>Requisitos de coleta de log do Win32

Há requisitos específicos que devem ser seguidos para coletar arquivos de log:

- Você deve especificar o caminho completo do arquivo de log. 
- Você pode especificar variáveis de ambiente para coleta de log, como as seguintes:<br>
  *% PROGRAMFILES%,% PROGRAMDATA%% PUBLIC%,% WINDIR%,% TEMP%,% TMP%*
- Somente as extensões de arquivo exatas são permitidas, como:<br>
  *. log,. txt,. dmp,. cab,. zip,. xml*
- O arquivo de log máximo a ser carregado é 60 MB ou 25 arquivos, o que ocorrer primeiro. 
- A coleta de log de instalação do aplicativo Win32 está habilitada para aplicativos que atendem à tentativa de atribuição de aplicativo necessária, disponível e desinstalação.
- Os logs armazenados são criptografados para proteger qualquer informação de identificação pessoal contida nos logs.
- Ao abrir tíquetes de suporte para falhas de aplicativo Win32, anexe os logs de falha relacionados usando as etapas fornecidas acima.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Resolução de problemas de aplicações da Loja Microsoft

As informações presentes no tópico [Resolução de problemas de empacotamento, implementação e consulta de aplicações da Loja Microsoft](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) ajudam-no a resolver problemas comuns que poderá encontrar ao instalar aplicações da Loja Microsoft, quer seja através do Intune ou de outros meios.

## <a name="app-troubleshooting-resources"></a>Recursos de solução de problemas do aplicativo
- [Implantando o Visio e o Project como parte da sua implantação do Office Pro Plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Tome medidas para garantir que os aplicativos MSfB implantados por meio da instalação do Intune no Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Solucionando problemas de implantações de aplicativo MSI no Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Práticas recomendadas para distribuição de software para o agente do computador Windows clássico do Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Próximos passos

- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](../fundamentals/help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, consulte [sucesso do cliente do Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
