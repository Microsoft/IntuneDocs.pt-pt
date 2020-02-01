---
title: Usar certificados PFX importados no Microsoft Intune – Azure | Microsoft Docs
description: Usar certificados PKCS importados com Microsoft Intune, incluindo a importação de certificados, a configuração do modelo de certificado, a instalação do conector de certificado PFX importado pelo Intune e a criação de um PKCS importado Perfil de certificado.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda; rimarram
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 469ee615cd9a9f1d3a7aee40ce764b8d8100fe69
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912895"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Configurar e usar certificados PKCS importados com o Intune

O Microsoft Intune dá suporte ao uso de certificados PKCS (par de chaves públicas) importados, comumente usados para criptografia S/MIME com perfis de email. Determinados perfis de email no Intune dão suporte a uma opção para habilitar o S/MIME, em que é possível definir um certificado de autenticação S/MIME e o certificado de criptografia S/MIME.

A criptografia S/MIME é desafiadora porque o email é criptografado com um certificado específico. Você deve ter a chave privada do certificado que criptografou o email no dispositivo em que você está lendo o email para que ele possa ser descriptografado. Os certificados de criptografia são renovados regularmente, o que significa que você pode precisar do seu histórico de criptografia em todos os seus dispositivos para garantir que você possa ler emails mais antigos.  Como o mesmo certificado precisa ser usado em dispositivos, não é possível usar perfis de certificado [SCEP](certificates-scep-configure.md) ou [PKCS](certficates-pfx-configure.md) para essa finalidade, pois esses mecanismos de entrega de certificados entregam certificados exclusivos por dispositivo.

Para obter mais informações sobre como usar S/MIME com o Intune, [use s/MIME para criptografar email](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Requisitos

Para usar certificados PKCS importados com o Intune, você precisará da seguinte infraestrutura:

- **Conector de certificado pfx para Microsoft Intune**:

  Cada locatário do Intune dá suporte a uma única instância desse conector. Você pode instalar esse conector no mesmo servidor que uma instância do conector de certificado Microsoft Intune.

  Esse conector lida com solicitações para arquivos PFX importados para o Intune para criptografia de email S/MIME para um usuário específico.

  Esse conector pode se atualizar automaticamente quando novas versões forem disponibilizadas. Para usar o recurso de atualização, você deve garantir que os firewalls estejam abertos e permitir que o conector entre em contato com o **AutoUpdate.msappproxy.net** na porta **443**.

  Para obter mais informações sobre todos os pontos de extremidade de rede que o conector acessa, consulte [requisitos e largura de banda de configuração de rede do Intune](../fundamentals/network-bandwidth-use.md).

- **Windows Server**:

  Você usa um Windows Server para hospedar o conector de certificado PFX para Microsoft Intune.  O conector é usado para processar solicitações de certificados importados para o Intune.

  O Intune dá suporte à instalação do *Microsoft Intune Certificate Connector* no mesmo servidor que o *conector de certificado pfx para Microsoft Intune*.

  Para dar suporte ao conector, o servidor deve executar o .NET 4,6 Framework ou superior. Se o .NET 4,6 Framework não estiver instalado quando você iniciar a instalação do conector, a instalação do conector o instalará automaticamente.

- **Visual Studio 2015 ou superior** (opcional):

  Use o Visual Studio para criar o módulo auxiliar do PowerShell com cmdlets para importar certificados PFX para Microsoft Intune. Para obter os cmdlets do PowerShell auxiliar, consulte [projeto do PFXImport PowerShell no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Como funciona

Quando você usa o Intune para implantar um **certificado pfx importado** para um usuário, há dois componentes em jogo, além do dispositivo:

- **Serviço do Intune**: armazena os certificados PFX em um estado criptografado e manipula a implantação do certificado para o dispositivo do usuário.  As senhas que protegem as chaves privadas dos certificados são criptografadas antes de serem carregadas usando um HSM (módulo de segurança de hardware) ou criptografia do Windows, garantindo que o Intune não possa acessar a chave privada a qualquer momento.

- **Conector de certificado pfx para Microsoft Intune**: quando um dispositivo solicita um certificado PFX que foi importado para o Intune, a senha criptografada, o certificado e a chave pública do dispositivo são enviados para o conector.  O conector descriptografa a senha usando a chave privada local e, em seguida, criptografa novamente a senha (e quaisquer perfis do plist se usar o iOS) com a chave do dispositivo antes de enviar o certificado de volta para o Intune.  O Intune, em seguida, entrega o certificado para o dispositivo e o dispositivo é capaz de descriptografá-lo com a chave privada do dispositivo e instalar o certificado.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Baixar, instalar e configurar o conector de certificado PFX para Microsoft Intune

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Administração de locatários** > **conectores e tokens** > **conectores de certificado** > **Adicionar**.

   ![Conector de certificado PFX para download de Microsoft Intune](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

3. Siga as orientações para baixar o *conector de certificado pfx para Microsoft Intune* em um local acessível do servidor em que você vai instalar o conector.

4. Após a conclusão do download, entre no servidor e execute o instalador (PfxCertificateConnectorBootstrapper. exe).  
   - Quando você aceita o local de instalação padrão, o conector é instalado no `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - O serviço do conector é executado na conta do sistema local. Se um proxy for necessário para acesso à Internet, confirme se a conta de serviço local pode acessar as configurações de proxy no servidor.

5. O PFX Certificate Connector for Microsoft Intune abre o separador **Enrollment** (Inscrição) após a instalação. Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissão de administrador global do Azure ou de administrador do Intune.

   > [!WARNING]
   > Por padrão, na configuração de **segurança avançada do IE** do Windows Server é definida como **on** , que pode causar problemas com a entrada no Office 365.

6. Feche a janela.

7. No centro de administração do Microsoft Endpoint Manager, volte para **Administração de locatários** > **conectores e tokens** > **conectores de certificado**. Em alguns instantes, uma marca de seleção verde é exibida e as atualizações de status de conexão. O servidor do conector agora pode se comunicar com o Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importar certificados PFX para o Intune

Você usa [Microsoft Graph](https://docs.microsoft.com/graph) para importar os certificados PFX dos usuários para o Intune. O [projeto auxiliar PFXImport PowerShell no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) fornece cmdlets para realizar as operações com facilidade.

Se você preferir usar sua própria solução personalizada usando o Graph, use o [tipo de recurso userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Compilar cmdlets ' PFXImport PowerShell Project '

Para fazer uso dos cmdlets do PowerShell, você mesmo cria o projeto usando o Visual Studio. O processo é direto e, embora possa ser executado no servidor, é recomendável executá-lo em sua estação de trabalho.  

1. Vá para a raiz do repositório do [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) no GitHub e, em seguida, baixe ou clone o repositório com o Git em seu computador.

   ![Botão de download do GitHub](./media/certificates-imported-pfx-configure/github-download.png)

2. Vá para `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` e abra o projeto com o Visual Studio usando o arquivo **PFXImportPS. sln**.

3. Na parte superior, altere de **debug** para **Release**.

4. Vá para **Compilar** e selecione **criar PFXImportPS**. Após alguns instantes, você verá que a confirmação da **compilação bem-sucedida** aparece na parte inferior esquerda do Visual Studio.

   ![Opção de compilação do Visual Studio](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. O processo de compilação cria uma nova pasta com o módulo do PowerShell em `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Você usará essa pasta de **lançamento** para as próximas etapas.

### <a name="create-the-encryption-public-key"></a>Criar a chave pública de criptografia

Você importa os certificados PFX e suas chaves privadas para o Intune. A senha que protege a chave privada é criptografada com uma chave pública que é armazenada no local. Você pode usar a criptografia do Windows, um módulo de segurança de hardware ou outro tipo de criptografia para gerar e armazenar os pares de chaves pública/privada.  Dependendo do tipo de criptografia usado, o par de chaves pública/privada pode ser exportado em um formato de arquivo para fins de backup.

O módulo do PowerShell fornece métodos para criar uma chave usando a criptografia do Windows. Você também pode usar outras ferramentas para criar uma chave.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Para criar a chave de criptografia usando a criptografia do Windows

1. Copie a pasta de *liberação* que é criada pelo Visual Studio para o servidor em que você instalou o **conector de certificado pfx para Microsoft Intune**. Essa pasta contém o módulo do PowerShell.

2. No servidor, abra o *PowerShell* como administrador e, em seguida, navegue até a pasta de *liberação* que contém o módulo do PowerShell.

3. Para importar o módulo, execute `Import-Module .\IntunePfxImport.psd1` para importar o módulo.

4. Em seguida, execute `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]
   > O provedor usado deve ser selecionado novamente quando você importar certificados PFX. Você pode usar o **provedor de armazenamento de chaves de software da Microsoft**, embora tenha suporte para usar um provedor diferente. O nome da chave também é fornecido como um exemplo, e você pode usar um nome de chave diferente de sua escolha.

   Se você planeja importar o certificado de sua estação de trabalho, você pode exportar essa chave para um arquivo com o seguinte comando: `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path\Filename.PFX>"`

   A chave privada deve ser importada no servidor que hospeda o conector de certificado PFX para Microsoft Intune para que os certificados PFX importados possam ser processados com êxito.

#### <a name="to-use-a-hardware-security-module-hsm"></a>Para usar um módulo de segurança de hardware (HSM)

Você pode usar um HSM (módulo de segurança de hardware) para gerar e armazenar o par de chaves pública/privada. Para obter mais informações, consulte a documentação do provedor do HSM.

### <a name="import-pfx-certificates"></a>Importar certificados PFX

O processo a seguir usa os cmdlets do PowerShell como um exemplo de como importar os certificados PFX. Você pode escolher opções diferentes dependendo de seus requisitos.

As opções incluem:

- Finalidade pretendida (agrupa certificados juntos com base em uma marca):
  - não atribuído
  - smimeEncryption
  - smimeSigning

- Esquema de preenchimento:
  - oaepSha256
  - oaepSha384
  - oaepSha512

Selecione o provedor de armazenamento de chaves que corresponde ao provedor usado para criar a chave.

#### <a name="to-import-the-pfx-certificate"></a>Para importar o certificado PFX  

1. Exporte os certificados de qualquer autoridade de certificação (CA) seguindo a documentação do provedor.  Para os serviços de certificados do Microsoft Active Directory, você pode usar [este script de exemplo](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).

2. No servidor, abra o *PowerShell* como administrador e, em seguida, navegue até a pasta de *liberação* que contém o módulo do PowerShell.

3. Para importar o módulo, execute `Import-Module .\IntunePfxImport.psd1`

4. Para autenticar no grafo do Intune, execute `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Como a autenticação é executada no grafo, você deve fornecer permissões para a AppID. Se for a primeira vez que você usou esse utilitário, um *administrador global* será necessário. Os cmdlets do PowerShell usam o mesmo AppID que aquele usado com os [exemplos do PowerShell Intune](https://github.com/microsoftgraph/powershell-intune-samples).

5. Converta a senha para cada arquivo PFX que você está importando para uma cadeia de caracteres segura executando `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`.

6. Para criar um objeto **UserPFXCertificate,** execute `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>"`

   Por exemplo: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption"`

   > [!NOTE]
   > Quando você importa o certificado de um sistema diferente do servidor em que o conector está instalado, use o comando a seguir que inclui o caminho do arquivo de chave: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. Importe o objeto **UserPFXCertificate** para o Intune executando `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`

8. Para validar que o certificado foi importado, execute `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`

Para obter mais informações sobre outros comandos disponíveis, consulte o arquivo Leiame em [projeto do PFXImport PowerShell no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Criar um perfil de certificado PKCS importado

Após importar certificados para o Intune, crie um perfil de **certificado PKCS importado** e atribua-o a grupos do Azure Active Directory.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfil de configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

   - O **Nome** do perfil
   - Opcionalmente, defina uma descrição
   - A **Plataforma** na qual vai implementar o perfil
   - Defina **Tipo de perfil** para **Certificado PKCS importado**

4. Selecione **configurações**e insira as seguintes propriedades:

   - **Finalidade pretendida**: Especifique a finalidade pretendida dos certificados que são importados para esse perfil. Os administradores podem importar certificados com diferentes finalidades pretendidas (como assinatura S/MIME ou criptografia S/MIME). A finalidade selecionada no perfil do certificado corresponde ao perfil do certificado com os certificados importados adequados. A finalidade pretendida é uma marca para agrupar certificados importados e não garante que os certificados importados com essa marca atendam à finalidade pretendida.  
   - **Período de validade do certificado**: a menos que o período de validade tenha sido alterado no modelo de certificado, essa opção usa como padrão um ano.
   - **Fornecedor de armazenamento de chaves (KSP)** : para dispositivos com Windows, selecione onde armazenar as chaves no dispositivo.

5. Selecione **OK** > **Criar** para guardar o perfil.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. [Atribua](../configuration/device-profile-assign.md) o novo perfil de dispositivo.
