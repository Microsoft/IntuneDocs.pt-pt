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
ms.openlocfilehash: 4db1a1a74c1a19f310aba0f1c10ed5d01869073f
ms.sourcegitcommit: 576b9528629981e87e775fac146932e502f07a74
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258135"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Configurar e usar certificados PKCS importados com o Intune

O Microsoft Intune dá suporte ao uso de certificados PKCS (par de chaves públicas) importados, comumente usados para criptografia S/MIME com perfis de email. Determinados perfis de email no Intune dão suporte a uma opção para habilitar o S/MIME, em que é possível definir um certificado de autenticação S/MIME e o certificado de criptografia S/MIME.

A criptografia S/MIME é desafiadora porque o email é criptografado com um certificado específico. Você deve ter a chave privada do certificado que criptografou o email no dispositivo em que você está lendo o email para que ele possa ser descriptografado. Os certificados de criptografia são renovados regularmente, o que significa que você pode precisar do seu histórico de criptografia em todos os seus dispositivos para garantir que você possa ler emails mais antigos.  Uma vez que o mesmo certificado necessita de ser utilizado em todos os dispositivos, não é possível utilizar perfis de [certificadoS SCEP](certificates-scep-configure.md) ou [PKCS](certficates-pfx-configure.md) para o efeito, uma vez que esses mecanismos de entrega de certificados fornecem certificados únicos por dispositivo.

Para mais informações sobre a utilização de S/MIME com [Intune, use S/MIME para encriptar e-mail](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Requisitos

Para usar certificados PKCS importados com o Intune, você precisará da seguinte infraestrutura:

- **Conector de certificado PFX para Microsoft Intune**:

  Cada locatário do Intune dá suporte a uma única instância desse conector. Você pode instalar esse conector no mesmo servidor que uma instância do conector de certificado Microsoft Intune.

  Esse conector lida com solicitações para arquivos PFX importados para o Intune para criptografia de email S/MIME para um usuário específico.

  Esse conector pode se atualizar automaticamente quando novas versões forem disponibilizadas. Para utilizar a capacidade de atualização, deve certificar-se de que as firewalls estão abertas que permitem ao conector contactar **autoupdate.msappproxy.net** na porta **443**.

  Para mais informações, consulte [os pontos finais da Rede para o Microsoft Intune](../fundamentals/intune-endpoints.md)e os requisitos de configuração da [rede Intune e largura de banda](../fundamentals/network-bandwidth-use.md).

- **Servidor do Windows:**

  Você usa um Windows Server para hospedar o conector de certificado PFX para Microsoft Intune.  O conector é usado para processar solicitações de certificados importados para o Intune.

  Intune suporta a instalação do *Conector* de Certificado Intune microsoft no mesmo servidor que o *Conector de Certificado PFX para microsoft Intune*.

  Para dar suporte ao conector, o servidor deve executar o .NET 4,6 Framework ou superior. Se o .NET 4,6 Framework não estiver instalado quando você iniciar a instalação do conector, a instalação do conector o instalará automaticamente.

- **Estúdio Visual 2015 ou superior** (opcional):

  Usa o Visual Studio para construir o módulo PowerShell ajudante com cmdlets para importar certificados PFX para o Microsoft Intune. Para obter os cmdlets powerShell do ajudante, consulte [PFXImport PowerShell Project no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Como funciona

Quando utiliza o Intune para implementar um **certificado PFX importado** a um utilizador, existem dois componentes em jogo, além do dispositivo:

- **Serviço Intune**: Armazene os certificados PFX em estado encriptado e manuseie a implementação do certificado para o dispositivo utilizador.  As senhas que protegem as chaves privadas dos certificados são criptografadas antes de serem carregadas usando um HSM (módulo de segurança de hardware) ou criptografia do Windows, garantindo que o Intune não possa acessar a chave privada a qualquer momento.

- **Conector de certificado PFX para Microsoft Intune**: Quando um dispositivo solicita um certificado PFX que foi importado para Intune, a palavra-passe encriptada, o certificado e a chave pública do dispositivo são enviadas para o conector.  O conector descriptografa a senha usando a chave privada local e, em seguida, criptografa novamente a senha (e quaisquer perfis do plist se usar o iOS) com a chave do dispositivo antes de enviar o certificado de volta para o Intune.  O Intune, em seguida, entrega o certificado para o dispositivo e o dispositivo é capaz de descriptografá-lo com a chave privada do dispositivo e instalar o certificado.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Baixar, instalar e configurar o conector de certificado PFX para Microsoft Intune

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **conectores** de certificado > **Adicionar**.

   ![Conector de certificado PFX para download de Microsoft Intune](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

3. Siga as orientações para o download do *Conector de Certificado PFX para o Microsoft Intune* para um local acessível a partir do servidor onde vai instalar o conector.

4. Após a conclusão do download, entre no servidor e execute o instalador (PfxCertificateConnectorBootstrapper. exe).  
   - Quando aceita a localização de instalação predefinida, o conector instala-se para `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - O serviço do conector é executado na conta do sistema local. Se um proxy for necessário para acesso à Internet, confirme se a conta de serviço local pode acessar as configurações de proxy no servidor.

5. O PFX Certificate Connector for Microsoft Intune abre o separador **Enrollment** (Inscrição) após a instalação. Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissão de administrador global do Azure ou de administrador do Intune.

   > [!WARNING]
   > Por predefinição, na **Configuração de Segurança Melhorada** do Windows Server IE está definida para **On,** o que pode causar problemas com o início de sessão no Office 365.

6. Feche a janela.

7. No Microsoft Endpoint Manager Admin Center, volte à **administração do Inquilino** > **Conectores e tokens** > **Conectores**de Certificado. Em alguns instantes, uma marca de seleção verde é exibida e as atualizações de status de conexão. O servidor do conector agora pode se comunicar com o Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importar certificados PFX para o Intune

Usa o [Microsoft Graph](https://docs.microsoft.com/graph) para importar os certificados PFX dos seus utilizadores para Intune. O helper [PFXImport PowerShell Project no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) fornece-lhe cmdlets para fazer as operações com facilidade.

Se preferir utilizar a sua própria solução personalizada utilizando o Graph, utilize o tipo de [recurso userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Compilar cmdlets ' PFXImport PowerShell Project '

Para fazer uso dos cmdlets do PowerShell, você mesmo cria o projeto usando o Visual Studio. O processo é direto e, embora possa ser executado no servidor, é recomendável executá-lo em sua estação de trabalho.  

1. Vá à raiz do repositório [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) no GitHub e, em seguida, descarregue ou clone o repositório com Git para a sua máquina.

   ![Botão de download do GitHub](./media/certificates-imported-pfx-configure/github-download.png)

2. Vá para `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` e abra o projeto com o Visual Studio usando o ficheiro **PFXImportPS.sln**.

3. No topo, mude de **Debug** para **Lançamento**.

4. Vá **construir** e selecione **Build PFXImportPS**. Depois de alguns momentos verá que a **confirmação conseguida** da Build aparece na parte inferior esquerda do Visual Studio.

   ![Opção de compilação do Visual Studio](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. O processo de construção cria uma nova pasta com o Módulo PowerShell em `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Utilizará esta pasta **de lançamento** para os próximos passos.

### <a name="create-the-encryption-public-key"></a>Criar a chave pública de criptografia

Você importa os certificados PFX e suas chaves privadas para o Intune. A senha que protege a chave privada é criptografada com uma chave pública que é armazenada no local. Você pode usar a criptografia do Windows, um módulo de segurança de hardware ou outro tipo de criptografia para gerar e armazenar os pares de chaves pública/privada.  Dependendo do tipo de criptografia usado, o par de chaves pública/privada pode ser exportado em um formato de arquivo para fins de backup.

O módulo do PowerShell fornece métodos para criar uma chave usando a criptografia do Windows. Você também pode usar outras ferramentas para criar uma chave.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Para criar a chave de criptografia usando a criptografia do Windows

1. Copie a pasta *de Lançamento* criada pelo Visual Studio para o servidor onde instalou o **Conector de CertificadoPFX para o Microsoft Intune**. Essa pasta contém o módulo do PowerShell.

2. No servidor, abra o *PowerShell* como Administrador e, em seguida, navegue para a pasta *Desbloqueio* que contém o módulo PowerShell.

3. Para importar o módulo, execute `Import-Module .\IntunePfxImport.psd1` para importar o módulo.

4. Em seguida, corra `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]
   > O provedor usado deve ser selecionado novamente quando você importar certificados PFX. Pode utilizar o Fornecedor de Armazenamento de Chaves do **Software microsoft**, embora seja suportado para utilizar um fornecedor diferente. O nome da chave também é fornecido como um exemplo, e você pode usar um nome de chave diferente de sua escolha.

   Se planeia importar o certificado da sua estação de trabalho, pode exportar esta chave para um ficheiro com o seguinte comando: `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path\Filename.PFX>"`

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

1. Exporte os certificados de qualquer autoridade de certificação (CA) seguindo a documentação do provedor.  Para os Serviços de Certificadode Diretório Ativo da Microsoft, pode utilizar [este script de amostra](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).

2. No servidor, abra o *PowerShell* como Administrador e, em seguida, navegue para a pasta *Desbloqueio* que contém o módulo PowerShell.

3. Para importar o módulo, corra `Import-Module .\IntunePfxImport.psd1`

4. Para autenticar o Intune Graph, execute `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Como a autenticação é executada no grafo, você deve fornecer permissões para a AppID. Se é a primeira vez que usas este utilitário, é necessário um *administrador global.* Os cmdlets PowerShell utilizam o mesmo AppID que o utilizado com [amostras intune PowerShell](https://github.com/microsoftgraph/powershell-intune-samples).

5. Converta a palavra-passe para cada ficheiro PFX que está a importar para uma cadeia segura executando `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`.

6. Para criar um objeto **UserPFXCertificate,** execute `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>"`

   Por exemplo: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption"`

   > [!NOTE]
   > Quando importar o certificado de um sistema diferente do servidor onde o conector está instalado, a utilização deve utilizar o seguinte comando que inclua o caminho do ficheiro chave: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. Importar o objeto **UserPFXCertificate** para Intune executando `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`

8. Para validar o certificado foi importado, executar `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`

Para obter mais informações sobre outros comandos disponíveis, consulte o ficheiro readme no [PFXImport PowerShell Project no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Criar um perfil de certificado PKCS importado

Após importar certificados para o Intune, crie um perfil de **certificado PKCS importado** e atribua-o a grupos do Azure Active Directory.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > perfil de **configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

   - O **Nome** do perfil
   - Opcionalmente, defina uma descrição
   - A **Plataforma** na qual vai implementar o perfil
   - Defina **Tipo de perfil** para **Certificado PKCS importado**

4. Selecione **Definições**e introduza as seguintes propriedades:

   - **Finalidade prevista**: Especificar o objetivo dos certificados importados para este perfil. Os administradores podem importar certificados com diferentes finalidades pretendidas (como assinatura S/MIME ou criptografia S/MIME). A finalidade selecionada no perfil do certificado corresponde ao perfil do certificado com os certificados importados adequados. A finalidade pretendida é uma marca para agrupar certificados importados e não garante que os certificados importados com essa marca atendam à finalidade pretendida.  
   - **Período de validade**do certificado : A menos que o período de validade tenha sido alterado no modelo de certificado, esta opção não se aplica a um ano.
   - **Fornecedor de armazenamento de chaves (KSP)** : para dispositivos com Windows, selecione onde armazenar as chaves no dispositivo.

5. Selecione **OK** > **Criar** para guardar o perfil.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. [Atribua](../configuration/device-profile-assign.md) o novo perfil do dispositivo.
