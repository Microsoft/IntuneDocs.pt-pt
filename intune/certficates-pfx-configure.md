---
title: Utilizar certificados de chaves públicos e privados no Microsoft Intune – Azure | Documentos da Microsoft
description: Adicionar ou criar certificados de padrões de criptografia de chave pública (PKCS) com o Microsoft Intune, incluindo os passos para exportar um certificado de raiz, configurar o modelo de certificado, transferir e instalar o conector de certificado do Intune (NDES), criar um dispositivo configuração de perfil e criar um perfil de certificado PKCS no Azure e a sua autoridade de certificação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02a5a7bd3625b5e95ddb304df7cf64461cca9c10
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049129"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurar e utilizar certificados PKCS com o Intune

O Intune suporta a utilização de certificados privados e públicos par de chaves (PKCS). Este artigo pode ajudá-lo a configurar a infraestrutura necessária, como conectores de certificado no local, exportar um certificado PKCS e, em seguida, adicionar o certificado para um perfil de configuração de dispositivos do Intune.

O Microsoft Intune inclui definições incorporadas para utilizar certificados PKCS para acesso e autenticação aos seus recursos de que as organizações. Certificados de autenticação e acesso seguro aos seus recursos empresariais, como uma VPN ou de uma rede Wi-Fi. Implementar estas definições em dispositivos com perfis de configuração de dispositivo no Intune.


## <a name="requirements"></a>Requisitos

Para utilizar certificados PKCS com o Intune, terá a seguinte infraestrutura:

- **Domínio do Active Directory**:  
  Todos os servidores indicados nesta secção tem de ser associados ao domínio do Active Directory.

  Para obter mais informações sobre como instalar e configurar serviços de domínio do Active Directory (AD DS), consulte [Design do AD DS e planeamento](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autoridade de certificação**:  
   Autoridade de certificação empresarial (AC).

  Para obter informações sobre como instalar e configurar os serviços de certificados do Active Directory (AD CS), consulte [Guia do passo a passo de serviços de certificados do Active Directory](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > O Intune requer a execução do AD CS com uma Autoridade de Certificação (AC) Empresarial e não uma AC Autónoma.

- **Um cliente**:  
  Para estabelecer ligação com a AC empresarial.

- **Certificado de raiz**:  
  Uma cópia exportada do certificado de raiz da AC Empresarial.

- **O Intune Certificate Connector** (também chamado de *NDES Certificate Connector*):  
  No portal do Intune, aceda a **configuração do dispositivo** > **Certificate Connectors** > **adicionar**e siga o *os passos para instalar o conector para PKCS #12*. Utilize a ligação de transferência no portal para iniciar a transferência do programa de instalação do conector de certificado **NDESConnectorSetup.exe**.  

  Este conector processa os pedidos de certificado PKCS utilizados para autenticação ou a assinatura de e-mail de S/MIME.

  O conector do NDES certificado também suporta o modo de Federal Information Processing Standard (FIPS). O FIPS não é obrigatório, mas pode emitir e revogar certificados quando está ativado.

- **Conector do certificado PFX para o Microsoft Intune**:  
   Se planeia utilizar a encriptação de correio eletrónico de S/MIME, utilize o portal do Intune para transferir o conector para o *certificados PFX importados*.  Aceda a **configuração do dispositivo** > **Certificate Connectors** > **adicionar**e siga o *passos para instalar o conector para Importar os certificados PFX*. Utilize o link de download no portal para iniciar a transferência do programa de instalação **PfxCertificateConnectorBootstrapper.exe**. 

  Este conector processa pedidos para ficheiros PFX importados para o Intune para encriptação de correio eletrónico de S/MIME para um utilizador específico.  

  Este conector pode atualizar automaticamente em si quando novas versões se tornam disponíveis. Para utilizar a capacidade de atualização, tem de:
  - Instale o conector do certificado PFX importadas para o Microsoft Intune no seu servidor.
  - Para receber automaticamente as atualizações importantes, certifique-se de firewalls aberto que permitem que o conector contactar **autoupdate.msappproxy.net** na porta **443**.  


- **Windows Server**:  
  Utilizar um servidor do Windows para o anfitrião:

  - Cenários de assinatura de e-mail do Microsoft Intune Certificate Connector - para autenticação e S/MIME
  - Conector de certificado PFX para o Microsoft Intune - para cenários de encriptação de correio eletrónico de S/MIME.

  Pode instalar ambos os conectores (*Microsoft Intune Certificate Connector* e *PFX Certificate Connector*) no mesmo servidor.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportar o certificado de raiz da AC Empresarial

Para autenticar um dispositivo com VPN, Wi-Fi ou outros recursos, um dispositivo tem um certificado de AC intermediária ou de raiz. Os passos seguintes explicam como obter o certificado necessário a partir da AC Empresarial.

**Utilize uma linha de comandos**:  
1. Inicie sessão para o servidor de autoridade de certificação de raiz com a conta de administrador.
 
2. Aceda a **começar** > **executar**e, em seguida, introduza **Cmd** para abrir a linha de comandos. 
    
3. Especifique **certutil-CA. cert ca_name.cer** para exportar o certificado de raiz como um arquivo chamado *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configurar modelos de certificado na AC

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra a consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** e selecione **Gerir**.
3. Localize o modelo de certificado de **Utilizador**, clique com o botão direito do rato nele e escolha **Duplicar Modelo**. As **Propriedades de Novo Modelo** são abertas.

    > [!NOTE]
    > Para cenários de encriptação e assinaturas de e-mail com S/MIME, muitos administradores utilizam certificados separados para assinar e encriptar. Se estiver a utilizar os Serviços de Certificados do Microsoft Active Directory, pode utilizar o modelo **Apenas Assinatura do Exchange** para certificados de assinaturas de e-mail S/MIME e o modelo **Utilizador do Exchange** para certificados de encriptação S/MIME.  Se estiver a utilizar uma autoridade de certificação 3rd, recomenda-se para rever as suas orientações para configurar modelos de assinatura e encriptação.

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
13. Para o servidor gerir os certificados para dispositivos inscritos e utilizadores, utilize os seguintes passos:

    1. Clique com o botão direito do rato na Autoridade de Certificação e escolha **Propriedades**.
    2. No separador Segurança, adicione a conta do Computador do servidor onde executa os conectores (**Microsoft Intune Certificate Connector** ou **PFX Certificate Connector for Microsoft Intune**). 
    3. Conceda as permissões **Emitir e Gerir Certificados** e **Pedir Certificados** à conta de computador.

14. Termine a sessão na AC Empresarial.

## <a name="download-install-and-configure-the-certificate-connectors"></a>Transferir, instalar e configurar os conectores de certificados

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connecparar

> [!IMPORTANT]  
> O Microsoft Intune Certificate Connector não pode ser instalado na autoridade de certificado (AC) emissora e, em vez disso, tem de ser instalado num servidor separado do Windows.  

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços**, filtre por **Intune** > selecione **Intune**.
2. Selecione **configuração do dispositivo** > **conectores de certificação** > **adicionar**.
3. Transfira e guarde o ficheiro de conector para uma localização pode aceder a partir do servidor onde pretende instalar o conector.

    ![Download de conector do NDES](media/certificates-pfx-configure/download-ndes-connector.png)
 

4. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.5 Framework ou superior está instalado, pois é necessário para o Certificate Connector do NDES. O .NET 4.5 Framework vem incluído automaticamente com o Windows Server 2012 R2 e versões mais recentes.
    2. Execute o instalador (NDESConnectorSetup.exe) e aceite a localização predefinida. O conector é instalado em `\Program Files\Microsoft Intune\NDESConnectorUI`. Nas Opções do Instalador, selecione **PFX Distribution** (Distribuição PFX). Continue para concluir a instalação.
    3. Por predefinição, o serviço do conector é executado na conta do sistema local. Se for necessário um proxy para aceder à Internet, confirme que a conta do serviço local consegue aceder às definições de proxy no servidor.

5. O Conector do NDES é aberto no separador **Enrollment** (Inscrição). Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissões administrativas globais.
6. No separador **Avançadas**, recomendamos que deixe a opção **Utilizar a conta SYSTEM deste computador (predefinição)** selecionada.
7. **Aplicar** > **Fechar**
8. Volte ao portal do Intune (**Intune** > **configuração do dispositivo** > **conectores de certificação**). Após alguns instantes, é apresentada uma marca de verificação verde e o **estado da ligação** é **Active Directory**. Agora o servidor do conector pode comunicar com o Intune.
9. Se tiver um proxy web no seu ambiente de rede, poderá ter configurações adicionais para ativar o conector funcione. Para obter mais informações, consulte [funcionam com o existente no local servidores proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) na documentação do Azure Active Directory.

> [!NOTE]  
> O Microsoft Intune Certificate Connector oferece suporte a TLS 1.2. Se o TLS 1.2 estiver instalado no servidor que aloja o conector, o conector utiliza o TLS 1.2. Caso contrário, é utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>PFX Certificate Connector for Microsoft Intune

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **configuração do dispositivo** > **conectores de certificação** > **adicionar**
3. Transfira e instale o PFX Certificate Connector for Microsoft Intune. Guarde-o numa localização acessível a partir do servidor onde vai instalar o conector.
4. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.6 Framework ou superior está instalado, pois é necessário para o PFX Certificate Connector for Microsoft Intune. Se o .NET 4.6 Framework não estiver instalado, o instalador instala-o automaticamente.
    2. Execute o instalador (PfxCertificateConnectorBootstrapper.exe) e aceite a localização predefinida, que instala o conector para `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. O serviço do conector é executado na conta do sistema local. Se for necessário um proxy para aceder à Internet, confirme que a conta do serviço local consegue aceder às definições de proxy no servidor.

5. O PFX Certificate Connector for Microsoft Intune abre o separador **Enrollment** (Inscrição) após a instalação. Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissão de administrador global do Azure ou de administrador do Intune.
6. Feche a janela.
7. Volte ao portal do Azure (**Intune** > **configuração do dispositivo** > **conectores de certificação**). Após alguns instantes, é apresentada uma marca de verificação verde e o **estado da ligação** é **Active Directory**. Agora o servidor do conector pode comunicar com o Intune.

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
    ![Navegue para o Intune e criar um novo perfil para um certificado fidedigno](media/certificates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado fidedigno**

3. Aceda às **Definições** e introduza o ficheiro .cer do Certificado da AC de Raiz que exportou anteriormente.

   > [!NOTE]
   > Consoante a plataforma que selecionou no **passo 2**, pode ou não ter uma opção para escolher a **arquivo de destino** para o certificado.

   ![Criar um perfil e carregar um certificado fidedigno](media/certificates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

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

    - **Limiar de renovação (%)**: Recomendado é de 20%.
    - **Período de validade do certificado**: Se não alterar o modelo de certificado, esta opção pode ser definida para um ano.
    - **Fornecedor de armazenamento de chaves (KSP)**: Para Windows, selecione onde pretende armazenar as chaves no dispositivo.
    - **Autoridade de certificação**: Apresenta o nome de domínio completamente qualificado (FQDN) interno da AC empresarial.
    - **Nome da autoridade de certificação**: Lista o nome da AC empresarial, como "Autoridade de certificação de Contoso".
    - **Nome do modelo de certificado**: O nome do modelo criado anteriormente. Nota: por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*.
    - **Formato de nome de requerente**: Defina esta opção como **nome comum** , exceto se for exigido.
    - **Nome alternativo do requerente**: Defina esta opção como **nome principal de utilizador (UPN)** , exceto se for exigido.

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Criar um perfil de certificado PKCS importado

Pode importar certificados emitidos anteriormente a um utilizador específico, a partir de qualquer AC no Intune. Os certificados importados são instalados em cada dispositivo que um utilizador inscreve. A encriptação de e-mail S/MIME é o cenário mais comum para importar certificados PFX existentes para o Intune. Um usuário pode ter muitos certificados para criptografar o e-mail. As chaves privadas desses certificados têm de existir em todos os dispositivos de um utilizador para que consigam desencriptar e-mails encriptados.

Para importar certificados para o Intune, pode utilizar os [cmdlets do PowerShell disponibilizados no GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Após importar certificados para o Intune, crie um perfil de **certificado PKCS importado** e atribua-o a grupos do Azure Active Directory.

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina **Tipo de perfil** para **Certificado PKCS importado**

3. Aceda a **Definições** e introduza as seguintes propriedades:

    - **Finalidade suposta**: A finalidade dos certificados que são importados para este perfil. Um administrador poderá ter importado certificados com finalidades diferentes (por exemplo, autenticação, assinatura S/MIME ou encriptação S/MIME). A finalidade selecionada no perfil do certificado corresponde ao perfil do certificado com os certificados importados adequados.
    - **Período de validade do certificado**: Se não alterar o modelo de certificado, esta opção pode ser definida para um ano.
    - **Fornecedor de armazenamento de chaves (KSP)**: Para Windows, selecione onde pretende armazenar as chaves no dispositivo.

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="whats-new-for-connectors"></a>O que há de novo para os conectores
Atualizações para os conectores de duas certificado são lançadas periodicamente. Quando atualizamos um conector, pode ler sobre as alterações aqui. 

O *conector de certificados PFX para o Microsoft Intune* [oferece suporte a atualizações automáticas](#requirements), enquanto o *Intune Certificate Connector* é atualizado manualmente.

### <a name="may-6-2019"></a>6 de Maio de 2019
- **Conector de certificados PFX para o Microsoft Intune - versão 6.1905.0.402**  
  Alterações nesta versão:  
  - O intervalo de consulta para o conector é reduzido de 5 minutos para 30 segundos.
 
### <a name="april-2-2019"></a>2 de Abril de 2019
- **Intune Certificate Connector - versão 6.1904.1.0**  
  Alterações nesta versão:  
  - Foi corrigido um problema em que o conector pode não conseguir inscrever-se ao Intune depois de iniciar sessão para o conector com uma conta de administrador global.  
  - Inclui correções de fiabilidade de revogação de certificados.  
  - Inclui correções de desempenho para aumentar o quão rapidamente os pedidos de certificado PKCS são processados.  

- **Conector de certificados PFX para o Microsoft Intune - versão 6.1904.0.401**
  > [!NOTE]  
  > Atualização automática para esta versão do conector do PFX não está disponível até 11 de Abril de 2019.  

  Alterações nesta versão:  
  - Foi corrigido um problema em que o conector pode não conseguir inscrever-se ao Intune depois de iniciar sessão para o conector com uma conta de administrador global.  


## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

[Utilizar certificados SCEP](certificates-scep-configure.md), ou [emitir certificados PKCS de uma PKI da Symantec serviço web manager](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegar para o Intune no portal do Azure e criar um novo perfil para um certificado fidedigno"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Criar um perfil e carregar um certificado fidedigno"
[ConnectorDownload]: ./media/certificates-download-connector.png "Transferir o certificate connector a partir do portal do Azure"  
