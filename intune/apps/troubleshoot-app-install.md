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
ms.openlocfilehash: 13aea23f58c69d5c7e38f77ae7dfa19bd12edd35
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369340"
---
# <a name="troubleshoot-app-installation-issues"></a>Resolver problemas com a instalação de aplicações

Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. O Microsoft Intune disponibiliza detalhes da falha na instalação da aplicação que permitem que os operadores de suporte técnico e os administradores do Intune vejam informações da aplicação para resolver pedidos de ajuda do utilizador. O painel de resolução de problemas no Intune proporciona os detalhes da falha, incluindo detalhes sobre as aplicações geridas no dispositivo de um utilizador. São disponibilizados detalhes sobre o ciclo de vida ponto a ponto de uma aplicação em cada dispositivo individual no painel **Aplicações Geridas**. Pode ver os problemas de instalação, como quando a aplicação foi criada, modificada, direcionada e entregue a um dispositivo. 

> [!NOTE]
> Para obter informações específicas sobre código de erro de instalação de aplicações, consulte a referência de erro de [instalação da aplicação Intune](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Detalhes de resolução de problemas de aplicativos

O Intune proporciona detalhes da resolução de problemas com a aplicação com base nas aplicações instaladas no dispositivo de um utilizador específico.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Troubleshoot + suporte**.
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

Os detalhes do erro da instalação da aplicação irão indicar o problema. Pode usar estes detalhes para determinar a melhor ação a tomar para resolver o problema. Para obter mais informações sobre problemas de instalação de aplicações, consulte erros de instalação de [aplicações Android](app-install-error-codes.md#android-app-installation-errors) e [erros de instalação de aplicações iOS.](app-install-error-codes.md#ios-and-ipados-app-installation-errors)

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>Instalação de aplicações direcionadas ao Grupo de Utilizadores não chega ao dispositivo
As seguintes ações devem ser consideradas quando tiver problemas na instalação de apps:
- Caso a aplicação não apareça no Portal da Empresa, certifique-se de que a aplicação está implantada com a intenção **disponível** e que o utilizador está a aceder ao Portal da Empresa com o tipo de dispositivo suportado pela aplicação.
- Para dispositivos ByOD Windows, o utilizador precisa de adicionar uma conta De Trabalho ao dispositivo.
- Verifique se o utilizador ultrapassou o limite do dispositivo AAD:
  1. Navegue para as definições do dispositivo de [diretório ativo do Azure](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Tome nota do valor definido para **dispositivos máximos por utilizador**.
  3. Navegue para [utilizadores de diretório ativo azure.](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers)
  4. Selecione o utilizador afetado e clique em **Dispositivos**.
  5. Se o utilizador estiver acima do limite definido, então elimine quaisquer registos mais velhos que já não sejam necessários.
- Para dispositivos iOS/iPadOS DEP, certifique-se de que o utilizador está listado como **Inscrito pelo Utilizador** no painel de visão geral do dispositivo Intune. Se mostrar NA, então implemente uma política de config para o Portal da Empresa Intune. Para mais informações, consulte [configurar a aplicação Portal da Empresa](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-and-ipados-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Resolução de problemas de instalação de aplicações Win32

Selecione a aplicação Win32 que foi implementada utilizando a extensão de gestão Intune. Pode selecionar a opção **de registos Do Collect** quando a instalação da aplicação Win32 falhar. 

> [!IMPORTANT]
> A opção **de registos Collect** não estará ativada quando a aplicação Win32 tiver sido instalada com sucesso no dispositivo.<p>Antes de poder recolher informações sobre o registo da aplicação Win32, a extensão de gestão Intune deve ser instalada no cliente do Windows. A extensão de gestão Intune é instalada quando um script PowerShell ou uma aplicação Win32 é implantado para um grupo de segurança de utilizador ou dispositivo. Para mais informações, consulte a [extensão intune Management - Pré-requisitos](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Recolher ficheiro de registo

Para recolher os registos de instalação da aplicação Win32, siga primeiro os passos fornecidos na secção App detalhes de resolução de [problemas](troubleshoot-app-install.md#app-troubleshooting-details). Em seguida, continue com os seguintes passos:

1. Clique na opção **de registos collect** no painel de detalhes da **instalação.**

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Forneça caminhos de ficheiros com nomes de ficheiros de registo para iniciar o processo de recolha de ficheiros de registo e clique em **OK**.

    > [!NOTE]
    > A recolha de registos levará menos de duas horas. Tipos de ficheiros suportados: *.log,.txt,.dmp,.cab,.zip,xml,.evtx, e.evtl*. São permitidos no máximo 25 caminhos de ficheiros.

3. Uma vez recolhidos os ficheiros de registo, pode selecionar o link **de registos** para descarregar os ficheiros de registo.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Será apresentada uma notificação que indique o sucesso da recolha de registos da aplicação.

#### <a name="win32-log-collection-requirements"></a>Requisitos de recolha de log Win32

Existem requisitos específicos que devem ser seguidos para recolher ficheiros de registo:

- Deve especificar o caminho completo do ficheiro de registo. 
- Pode especificar variáveis ambientais para recolha de registos, tais como:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PÚBLICO%, %WINDIR%, %TEMP%, %TMP%*
- São permitidas apenas extensões exatas de ficheiros, tais como:<br>
  *.log,.txt,.dmp,.cab,.zip,.xml*
- O ficheiro de registo máximo para carregar é de 60 MB ou 25 ficheiros, o que ocorrer primeiro. 
- A recolha de registos de instalação de apps Win32 está ativada para apps que cumpram a intenção de atribuição de aplicações necessária, disponível e desinstalada.
- Os registos armazenados são encriptados para proteger qualquer informação pessoal identificável contida nos registos.
- Ao abrir os bilhetes de apoio para falhas na aplicação Win32, anexe os registos de falha relacionados utilizando os passos acima indicados.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Resolução de problemas de aplicações da Loja Microsoft

As informações presentes no tópico [Resolução de problemas de empacotamento, implementação e consulta de aplicações da Loja Microsoft](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) ajudam-no a resolver problemas comuns que poderá encontrar ao instalar aplicações da Loja Microsoft, quer seja através do Intune ou de outros meios.

## <a name="app-troubleshooting-resources"></a>Recursos de resolução de problemas de aplicativos
- [Implantação da Visio e do Projeto como parte do seu Office Pro Plus Deployment](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Tome medidas para garantir aplicações MSfB implementadas através da instalação Intune no Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Implementações de aplicações MSI em Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [As melhores práticas para distribuição de software para intune agente clássico do WINDOWS PC](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Próximos passos

- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](../fundamentals/help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para mais informações, consulte [Intune Customer Success](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
