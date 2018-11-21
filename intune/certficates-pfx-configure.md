---
title: Utilizar certificados PKCS com o Microsoft Intune – Azure | Micrososft Docs
description: Adicionar ou criar certificados Public Key Cryptography Standard com o Microsoft Intune, incluindo os passos para exportar um certificado de raiz, configurar o modelo de certificado, transferir e instalar o Microsoft Intune Certificate Connector (NDES), criar um perfil de configuração de dispositivo, criar um perfil de Certificado PKCS no Azure e Autoridade de Certificação.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 70d1594220b3315db2c7d7eeb01a915aaf2ec995
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186738"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurar e utilizar certificados PKCS com o Intune

> [!IMPORTANT]
> Estamos a fazer algumas melhorias à funcionalidade S/MIME descrita neste artigo. Por esse motivo, a funcionalidade S/MIME será removida temporariamente do Intune. Quando esta funcionalidade for lançada, iremos remover esta nota.

Os certificados autenticam e protegem o acesso aos seus recursos empresariais, tal como um VPN ou a sua rede Wi-Fi. Este artigo mostra-lhe como exportar um certificado PKCS e, em seguida, adicioná-lo a um perfil do Intune.

## <a name="requirements"></a>Requisitos

Para utilizar certificados PKCS com o Intune, certifique-se de que tem a seguinte infraestrutura:

- **Domínio do Active Directory**: todos os servidores indicados nesta secção têm de ser associados ao seu domínio do Active Directory.

  Para obter mais informações sobre como instalar e configurar o AD DS, veja [Design e Planeamento do AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autoridade de Certificação** (AC): uma Autoridade de Certificação (AC) Empresarial

  Para obter mais informações sobre como instalar e configurar os Serviços de Certificados do Active Directory (AD CS), veja [Active Directory Certificate Services Step-by-Step Guide (Guia Passo a Passo dos Serviços de Certificados do Active Directory)](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > O Intune requer a execução do AD CS com uma Autoridade de Certificação (AC) Empresarial e não uma AC Autónoma.

- **Um cliente**: para ligar à AC Empresarial

- **Certificado de raiz**: uma cópia exportada do certificado de raiz da AC Empresarial

- **Microsoft Intune Certificate Connector**: utilize o portal do Azure para transferir o instalador do **Certificate Connector** (**NDESConnectorSetup.exe**). 

  O conector processa os pedidos de certificado PKCS utilizados para autenticação ou assinaturas de e-mail com S/MIME.

  O Certificate Connector do NDES também suporta o modo Federal Information Processing Standard (FIPS). O FIPS não é obrigatório, mas pode emitir e revogar certificados quando está ativado.

- **PFX Certificate Connector for Microsoft Intune**: se planeia utilizar a encriptação de e-mail S/MIME, utilize o portal do Azure para transferir o instalador do **PFX Certificate Connector for Microsoft Intune** (**PfxCertificateConnectorBootstrapper.exe**). O conector processa pedidos para ficheiros PFX importados no Intune para encriptação de e-mail S/MIME para um utilizador específico.

- **Windows Server**: aloja o:

  - Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) para cenários de autenticação e de assinaturas de e-mail com S/MIME
  - PFX Certificate Connector for Microsoft Intune (PfxCertificateConnectorBootstrapper.exe) para cenários de encriptação de e-mail com S/MIME.

  Pode executar ambos os conectores (**Microsoft Intune Certificate Connector** e **PFX Certificate Connector for Microsoft Intune**) no mesmo servidor.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportar o certificado de raiz da AC Empresarial

Para autenticar com VPN, Wi-Fi ou outros recursos, é necessário um certificado de AC intermédio ou de raiz em cada dispositivo. Os passos seguintes explicam como obter o certificado necessário a partir da AC Empresarial.

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra uma linha de comandos como administrador.
3. Exporte o Certificado da AC de Raiz (.cer) para uma localização onde possa aceder ao mesmo mais tarde.
4. Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

   `certutil -ca.cert certnew.cer`

   Para obter mais informações, veja [Tarefas do certutil para gerir certificados](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurar modelos de certificado na autoridade de certificação

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra a consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** e selecione **Gerir**.
3. Localize o modelo de certificado de **Utilizador**, clique com o botão direito do rato nele e escolha **Duplicar Modelo**. As **Propriedades de Novo Modelo** são abertas.

    > [!NOTE]
    > Para cenários de encriptação e assinaturas de e-mail com S/MIME, muitos administradores utilizam certificados separados para assinar e encriptar. Se estiver a utilizar os Serviços de Certificados do Microsoft Active Directory, pode utilizar o modelo **Apenas Assinatura do Exchange** para certificados de assinaturas de e-mail S/MIME e o modelo **Utilizador do Exchange** para certificados de encriptação S/MIME.  Se estiver a utilizar outra autoridade de certificação, sugerimos que consulte as respetivas orientações para configurar modelos de assinaturas e encriptação.

4. No separador **Compatibilidade**:

  - Defina **Autoridade de Certificação** como **Windows Server 2008 R2**
  - Defina **Destinatário do certificado** como **Windows 7/Server 2008 R2**

5. No separador **Geral**, defina o **Nome a apresentar do modelo** para algo que seja relevante para si.

    > [!WARNING]
    > Por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*. Anote o nome do modelo, irá precisar dele mais tarde.

6. Em **Processamento de Pedidos**, selecione **Permitir que a chave privada seja exportada**.
7. Em **Criptografia**, confirme se o **Tamanho mínimo da chave** está definido como 2048.
8. Em **Nome do Requerente**, selecione **Fornecer no pedido**.
9. Em **Extensões**, confirme se vê o Sistema de Encriptação de Ficheiros, Proteger o E-mail e Autenticação de Cliente em **Políticas de Aplicações**.

    > [!IMPORTANT]
    > Para os modelos de certificado iOS, aceda ao separador **Extensões**, atualize a **Utilização de Chaves** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

10. Em **Segurança**, adicione a Conta de Computador do servidor no local onde irá instalar o Microsoft Intune Certificate Connector. Conceda a esta conta as permissões **Ler** e **Inscrever**.
11. Selecione **Aplicar** > **OK** para guardar o modelo de certificado. Feche a **Consola de Modelos de Certificado**.
12. Na consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** > **Novo** > **Modelo de Certificado a Emitir**. Selecione o modelo criado nos passos anteriores. Selecione **OK**.
13. Para o servidor gerir os certificados em nome dos utilizadores e dos dispositivos inscritos no Intune, siga estes passos:

    1. Clique com o botão direito do rato na Autoridade de Certificação e escolha **Propriedades**.
    2. No separador Segurança, adicione a conta do Computador do servidor onde executa os conectores (**Microsoft Intune Certificate Connector** ou **PFX Certificate Connector for Microsoft Intune**). Conceda as permissões **Emitir e Gerir Certificados** e **Pedir Certificados** à conta de computador.

14. Termine a sessão na AC Empresarial.

## <a name="download-install-and-configure-the-certificate-connectors"></a>Transferir, instalar e configurar os conectores de certificados

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connecparar

> [!IMPORTANT] 
> O Microsoft Intune Certificate Connector **tem** de ser instalado num servidor Windows separado. Não pode ser instalado na Autoridade de Certificação (AC) emissora.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Autoridade de Certificação** > **Adicionar**.
3. Transfira e guarde o ficheiro de conector. Guarde-o numa localização acessível a partir do servidor onde vai instalar o conector.

    ![ConnectorDownload][ConnectorDownload]

4. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.5 Framework ou superior está instalado, pois é necessário para o Certificate Connector do NDES. O .NET 4.5 Framework vem incluído automaticamente com o Windows Server 2012 R2 e versões mais recentes.
    2. Execute o instalador (NDESConnectorSetup.exe) e aceite a localização predefinida. O conector é instalado em `\Program Files\Microsoft Intune\NDESConnectorUI`. Nas Opções do Instalador, selecione **PFX Distribution** (Distribuição PFX). Continue para concluir a instalação.
    3. Por predefinição, o serviço do conector é executado na conta do sistema local. Se for necessário um proxy para aceder à Internet, confirme que a conta do serviço local consegue aceder às definições de proxy no servidor.

5. O Conector do NDES é aberto no separador **Enrollment** (Inscrição). Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissões administrativas globais.
6. No separador **Avançadas**, recomendamos que deixe a opção **Utilizar a conta SYSTEM deste computador (predefinição)** selecionada.
7. **Aplicar** > **Fechar**
8. Aceda novamente ao portal do Azure (**Intune** > **Configuração do Dispositivo** > **Autoridade de Certificação**). Alguns momentos depois, é apresentada uma marca de verificação verde e o **Connection status** (Estado da ligação) muda para **Active** (Ativo). Agora o servidor do conector pode comunicar com o Intune.

> [!NOTE]
> O suporte de TLS 1.2 está incluído com o Microsoft Intune Certificate Connector. Assim, se o servidor com o Microsoft Intune Certificate Connector instalado suportar TLS 1.2, é utilizado TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>PFX Certificate Connector for Microsoft Intune

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Autoridade de Certificação** > **Adicionar**
3. Transfira e instale o PFX Certificate Connector for Microsoft Intune. Guarde-o numa localização acessível a partir do servidor onde vai instalar o conector.
4. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.6 Framework ou superior está instalado, pois é necessário para o PFX Certificate Connector for Microsoft Intune. Se o .NET 4.6 Framework não estiver instalado, o instalador instala-o automaticamente.
    2. Execute o instalador (PfxCertificateConnectorBootstrapper.exe) e aceite a localização predefinida. O conector é instalado em `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. O serviço do conector é executado na conta do sistema local. Se for necessário um proxy para aceder à Internet, confirme que a conta do serviço local consegue aceder às definições de proxy no servidor.

5. O PFX Certificate Connector for Microsoft Intune abre o separador **Enrollment** (Inscrição) após a instalação. Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissão de administrador global do Azure ou de administrador do Intune.
6. Feche a janela.
7. Aceda novamente ao portal do Azure (**Intune** > **Configuração do Dispositivo** > **Autoridade de Certificação**). Alguns momentos depois, é apresentada uma marca de verificação verde e o **Connection status** (Estado da ligação) muda para **Active** (Ativo). Agora o servidor do conector pode comunicar com o Intune.

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.

   ![NavigateIntune][NavigateIntune]

2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado fidedigno**

3. Aceda às **Definições** e introduza o ficheiro .cer do Certificado da AC de Raiz que exportou anteriormente.

   > [!NOTE]
   > Consoante a plataforma que selecionou no **Passo 3**, poderá ter ou não uma opção para escolher o **Arquivo de destino** do certificado.

   ![ProfileSettings][ProfileSettings]

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de certificado PKCS

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado PKCS**

3. Aceda a **Definições** e introduza as seguintes propriedades:

    - **Limiar de renovação (%)**: recomenda-se 20%.
    - **Período de validade do certificado**: se não tiver alterado o modelo de certificado, esta opção poderá estar definida como um ano.
    - **Fornecedor de armazenamento de chaves (KSP)**: para dispositivos com Windows, selecione onde armazenar as chaves no dispositivo.
    - **Autoridade de certificação**: apresenta o nome de domínio completamente qualificado (FQDN) interno da sua AC Empresarial.
    - **Nome da autoridade de certificação**: apresenta o nome da sua AC Empresarial, por exemplo "Autoridade de Certificação da Contoso".
    - **Nome do modelo de certificado**: o nome do modelo criado anteriormente. Nota: por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*.
    - **Formato do nome do requerente**: defina esta opção como **Nome comum**, exceto se for exigido outro.
    - **Nome alternativo do requerente**: defina esta opção como **Nome principal de utilizador (UPN)**, exceto se for exigido outro.

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Criar um perfil de certificado PKCS importado

Pode importar certificados anteriormente emitidos para um determinado utilizador a partir de qualquer autoridade de certificação para o Intune. Os certificados importados são instalados em cada dispositivo que um utilizador inscreve. A encriptação de e-mail S/MIME é o cenário mais comum para importar certificados PFX existentes para o Intune. Um utilizador poderá ter múltiplos certificados para encriptar e-mails. As chaves privadas desses certificados têm de existir em todos os dispositivos de um utilizador para que consigam desencriptar e-mails encriptados.

Para importar certificados para o Intune, pode utilizar os [cmdlets do PowerShell disponibilizados no GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Após importar certificados para o Intune, crie um perfil de **certificado PKCS importado** e atribua-o a grupos do Azure Active Directory.

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina **Tipo de perfil** para **Certificado PKCS importado**

3. Aceda a **Definições** e introduza as seguintes propriedades:

    - **Finalidade suposta**: a finalidade dos certificados importados para este perfil. Um administrador poderá ter importado certificados com finalidades diferentes (por exemplo, autenticação, assinatura S/MIME ou encriptação S/MIME). A finalidade selecionada no perfil do certificado corresponde ao perfil do certificado com os certificados importados adequados.
    - **Período de validade do certificado**: se não tiver alterado o modelo de certificado, esta opção poderá estar definida como um ano.
    - **Fornecedor de armazenamento de chaves (KSP)**: para dispositivos com Windows, selecione onde armazenar as chaves no dispositivo.

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Passos Seguintes
[Utilizar certificados SCEP](certificates-scep-configure.md) ou [emitir certificados PKCS de um serviço Web de gestão de PKI da Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegar para o Intune no portal do Azure e criar um novo perfil para um certificado fidedigno"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Criar um perfil e carregar um certificado fidedigno"
[ConnectorDownload]: ./media/certificates-download-connector.png "Transferir o certificate connector a partir do portal do Azure"  
