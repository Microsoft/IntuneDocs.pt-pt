---
title: Adicionar proteção de ponto final ao macOS no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos macOS, utilize o controlador de chamadas para determinar onde as aplicações podem ser instaladas, incluindo a Mac App Store. Ativar ou configurar uma firewall permite aplicações específicas, bloqueia aplicações específicas, utiliza o modo invisível e até bloqueia determinados tipos de ligações de entrada com o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 358a396e762f1f20051abadfc2f3df80f37ca8c8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502291"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Configurações do MacOS Endpoint Protection no Intune  

Este artigo mostra as configurações do Endpoint Protection que você pode configurar para dispositivos que executam o macOS. Você define essas configurações usando um perfil de configuração de dispositivo macOS para o [Endpoint Protection](endpoint-protection-configure.md) no Intune.  

## <a name="gatekeeper"></a>Controlador de chamadas  

- **Permitir que os aplicativos sejam baixados destes locais**  
  Limite os aplicativos que um dispositivo pode iniciar, dependendo de onde os aplicativos foram baixados. A intenção é proteger os dispositivos contra malware e permitir que os aplicativos apenas das fontes confiáveis.  

  - **Não configurado**  
  - **Mac App Store**  
  - **Mac App Store e programadores identificados**  
  - **Em qualquer lugar**  

  **Padrão**: não configurado  

- **O usuário pode substituir o gatekeeper**  
  Impede que os usuários substituam a configuração do gatekeeper e impede que os usuários controlem clicando para instalar um aplicativo. Quando estiver ativado, os utilizadores podem manter a tecla Ctrl premida e clicar em qualquer aplicação e instalá-la.  
 
  - **Não configurado** -os usuários podem controlar e clicar para instalar aplicativos.  
  - **Bloquear** – impede que os usuários usem o controle-clique para instalar aplicativos.  

  **Padrão**: não configurado  

## <a name="firewall"></a>Firewall  

Utilize a firewall para controlar ligações por aplicação e não por porta. Utilizar definições por aplicação torna mais fácil obter as vantagens de proteção da firewall. Também ajuda a impedir que aplicações indesejáveis controlem as portas da rede que estão abertas para as aplicações legítimas.  

**Genéricos**
- **Firewall**  
  Habilite o firewall para configurar como as conexões de entrada são tratadas em seu ambiente.  
  - **Não configurado**  
  - **Desabilitar**  

  **Padrão**: não configurado  

- **Conexões de entrada**  
  Bloqueie todas as conexões de entrada, exceto as conexões necessárias para os serviços básicos da Internet, como DHCP, Bonjour e IPSec. Esta funcionalidade também bloqueia todos os serviços de partilha, tal como a Partilha de Ficheiros e a Partilha de Ecrãs. Se estiver a utilizar serviços de partilha, mantenha esta definição como *Não configurado*.  
  - **Não configurado**  
  - **Bloquear**  

  **Padrão**: não configurado  

**Permitir ou bloquear conexões de entrada para aplicativos específicos.**  

  - **Aplicativos permitidos**  
    Selecione os aplicativos que têm permissão explícita para receber conexões de entrada.  

  - **Aplicativos bloqueados**  
    Selecione os aplicativos que devem bloquear conexões de entrada.  

  - **Modo furtivo**  
    Para impedir que o computador responda às solicitações de investigação, habilite o modo furtivo. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. São ignorados pedidos inesperados, tais como o protocolo ICMP (ping).  
    - **Não configurado**  
    - **Desabilitar**  

    **Padrão**: não configurado  

## <a name="filevault"></a>FileVault  
Para obter mais informações sobre as configurações do Apple FileVault, consulte [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) no conteúdo do desenvolvedor da Apple. 

> [!IMPORTANT]  
> A partir do macOS 10,15, a configuração do FileVault requer o registro de MDM aprovado pelo usuário. 

- **FileVault**  
  Você pode *habilitar* a criptografia de disco completa usando o XTS-AES 128 com o FileVault em dispositivos que executam o MacOS 10,13 e posterior.  
  - **Não configurado**  
  - **Desabilitar**  

  **Padrão**: não configurado  

  - **Tipo de chave de recuperação**  
    Chaves de recuperação de *chave pessoal* são criadas para dispositivos. Defina as configurações a seguir para a chave pessoal.  

    - **Local da chave de recuperação pessoal** – especifique uma mensagem curta para o usuário que explica como e onde eles podem recuperar sua chave de recuperação pessoal. Esse texto é inserido na mensagem que o usuário vê em sua tela de logon quando solicitado a inserir sua chave de recuperação pessoal se uma senha for esquecida.  
      
    - **Rotação de chave de recuperação pessoal** – especifique com que frequência a chave de recuperação pessoal de um dispositivo será girada. Você pode selecionar o padrão **não configurado**ou um valor de **1** a **12** meses.  

  - **Desabilitar aviso ao sair**  
    Impedir o prompt para o usuário que solicita que eles habilitem o FileVault quando eles se desconectarem.  Quando definido como desabilitado, o prompt na saída é desabilitado e, em vez disso, o usuário recebe uma solicitação quando entra.  
    - **Não configurado**  
    - **Desabilitar** – desabilitar o prompt na saída.

    **Padrão**: não configurado  

  - **Número de vezes com permissão para ignorar**  
  Defina o número de vezes que um usuário pode ignorar prompts para habilitar FileVault antes que FileVault seja necessário para que o usuário entre. 

    - **Não configurado** -a criptografia no dispositivo é necessária antes que a próxima entrada seja permitida.  
    - **1** a **10** -permite que um usuário ignore o prompt de 1 a 10 vezes antes de exigir a criptografia no dispositivo.  
    - **Sem limite, sempre avisar** -o usuário é solicitado a habilitar FileVault, mas a criptografia nunca é necessária.  
 
    **Padrão**: *varia* -quando a configuração *desabilitar prompt em sair* está definida como **não configurado**, essa configuração assume como padrão **não configurado**. Quando *desabilitar prompt na saída* estiver definido como **desabilitar**, essa configuração padrão será **1** e o valor **não configurado não** será uma opção.

Para obter mais informações sobre o FileVault com o Intune, consulte [chaves de recuperação do FileVault](encryption-monitor.md#filevault-recovery-keys).
