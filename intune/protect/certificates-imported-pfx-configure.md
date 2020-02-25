---
title: Utilize certificados PFX importados no Microsoft Intune - Azure Microsoft Docs
description: Utilize certificados de criptografia de chave pública importados (PKCS) com a Microsoft Intune, incluindo a importação de certificados, configurando o modelo de certificado, instalação do Conector de Certificado PFX importado intune e crie um PKCS importado Perfil de certificado.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2020
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
ms.openlocfilehash: 02fa3acdaf0dc450afee97dfaaf5870166013356
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569528"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Configure e utilize certificados PKCS importados com Intune

O Microsoft Intune suporta a utilização de certificados de pares de chaves públicas importados (PKCS), comumente utilizados para encriptação S/MIME com perfis de e-mail. Certos perfis de e-mail em Intune suportam uma opção para ativar S/MIME onde pode definir um certificado de assinatura S/MIME e cert de encriptação S/MIME.

A encriptação S/MIME é desafiante porque o e-mail é encriptado com um certificado específico. Deve ter a chave privada do certificado que encriptou o e-mail no dispositivo onde está a ler o e-mail para que possa ser desencriptado. Os certificados de encriptação são renovados regularmente, o que significa que pode precisar do seu histórico de encriptação em todos os seus dispositivos para garantir que pode ler e-mails mais antigos.  Uma vez que o mesmo certificado necessita de ser utilizado em todos os dispositivos, não é possível utilizar perfis de [certificadoS SCEP](certificates-scep-configure.md) ou [PKCS](certficates-pfx-configure.md) para o efeito, uma vez que esses mecanismos de entrega de certificados fornecem certificados únicos por dispositivo.

Para mais informações sobre a utilização de S/MIME com [Intune, use S/MIME para encriptar e-mail](certificates-s-mime-encryption-sign.md).

## <a name="supported-platforms"></a>Plataformas suportadas

Intune apoia a importação de certificados PFX para as seguintes plataformas:

- Android - Administrador de Dispositivos
- Android Enterprise - Totalmente Gerido
- Android Enterprise - Perfil de trabalho
- iOS
- Mac
- Windows 10

## <a name="requirements"></a>Requisitos

Para utilizar certificados PKCS importados com Intune, necessitará da seguinte infraestrutura:

- **Conector de certificado PFX para Microsoft Intune**:

  Cada inquilino intune suporta uma única instância deste conector. Pode instalar este conector no mesmo servidor que uma instância do conector Microsoft Intune Certificate.

  Este conector trata dos pedidos de ficheiros PFX importados para Intune para encriptação de e-mail S/MIME para um utilizador específico.

  Este conector pode atualizar-se automaticamente quando novas versões estiverem disponíveis. Para utilizar a capacidade de atualização, deve certificar-se de que as firewalls estão abertas que permitem ao conector contactar **autoupdate.msappproxy.net** na porta **443**.

  Para mais informações, consulte [os pontos finais da Rede para o Microsoft Intune](../fundamentals/intune-endpoints.md)e os requisitos de configuração da [rede Intune e largura de banda](../fundamentals/network-bandwidth-use.md).

- **Servidor do Windows:**

  Utiliza um Servidor Windows para alojar o Conector de CertificadoPFX para o Microsoft Intune.  O conector é utilizado para processar pedidos de certificados importados para Intune.
  
  O conector requer acesso às mesmas portas que detalhadopara dispositivos geridos, como se encontra no [conteúdo do ponto final](https://docs.microsoft.com/intune/fundamentals/intune-endpoints#access-for-managed-devices)do nosso dispositivo .

  Intune suporta a instalação do *Conector* de Certificado Intune microsoft no mesmo servidor que o *Conector de Certificado PFX para microsoft Intune*.

  Para suportar o conector, o servidor deve executar .NET 4.6 Quadro ou superior. Se não for instalada a estrutura .NET 4.6 quando iniciar a instalação do conector, a instalação do conector instala-o automaticamente.

- **Estúdio Visual 2015 ou superior** (opcional):

  Usa o Visual Studio para construir o módulo PowerShell ajudante com cmdlets para importar certificados PFX para o Microsoft Intune. Para obter os cmdlets powerShell do ajudante, consulte [PFXImport PowerShell Project no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Como funciona

Quando utiliza o Intune para implementar um **certificado PFX importado** a um utilizador, existem dois componentes em jogo, além do dispositivo:

- **Serviço Intune**: Armazene os certificados PFX em estado encriptado e manuseie a implementação do certificado para o dispositivo utilizador.  As palavras-passe que protegem as chaves privadas dos certificados são encriptadas antes de serem carregadas usando um módulo de segurança de hardware (HSM) ou criptografia do Windows, garantindo que Intune não pode aceder à chave privada a qualquer momento.

- **Conector de certificado PFX para Microsoft Intune**: Quando um dispositivo solicita um certificado PFX que foi importado para Intune, a palavra-passe encriptada, o certificado e a chave pública do dispositivo são enviadas para o conector.  O conector desencripta a palavra-passe utilizando a chave privada no local e, em seguida, volta a encriptar a palavra-passe (e quaisquer perfis de lista seletivos se utilizar o iOS) com a chave do dispositivo antes de enviar o certificado de volta para Intune.  Intone então entrega o certificado ao dispositivo e o dispositivo é capaz de desencriptar com a chave privada do dispositivo e instalar o certificado.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Descarregue, instale e configure o Conector de Certificado PFX para o Microsoft Intune

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **conectores** de certificado > **Adicionar**.

   ![Conector de certificado PFX para download do Microsoft Intune](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

3. Siga as orientações para o download do *Conector de Certificado PFX para o Microsoft Intune* para um local acessível a partir do servidor onde vai instalar o conector.

4. Depois de o download estar concluído, faça o sinal de sessão no servidor e execute o instalador (PfxCertificateConnectorBootstrapper.exe).  
   - Quando aceita a localização de instalação predefinida, o conector instala-se para `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - O serviço do conector é executado na conta do sistema local. Se for necessário um proxy para acesso à Internet, confirme que a conta de serviço local pode aceder às definições de procuração no servidor.

5. O PFX Certificate Connector for Microsoft Intune abre o separador **Enrollment** (Inscrição) após a instalação. Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissão de administrador global do Azure ou de administrador do Intune.

   > [!WARNING]
   > Por predefinição, na **Configuração de Segurança Melhorada** do Windows Server IE está definida para **On,** o que pode causar problemas com o início de sessão no Office 365.

6. Feche a janela.

7. No Microsoft Endpoint Manager Admin Center, volte à **administração do Inquilino** > **Conectores e tokens** > **Conectores**de Certificado. Em alguns momentos, aparece uma marca de verificação verde e as atualizações do estado da ligação. O servidor do conector pode agora comunicar com Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importar Certificados PFX para Intune

Usa o [Microsoft Graph](https://docs.microsoft.com/graph) para importar os certificados PFX dos seus utilizadores para Intune. O helper [PFXImport PowerShell Project no GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) fornece-lhe cmdlets para fazer as operações com facilidade.

Se preferir utilizar a sua própria solução personalizada utilizando o Graph, utilize o tipo de [recurso userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Construa cmdlets 'PFXImport PowerShell Project'

Para utilizar os cmdlets PowerShell, você mesmo constrói o projeto usando o Visual Studio. O processo é direto e, embora possa ser executado no servidor, recomendamos que o execute na sua estação de trabalho.  

1. Vá à raiz do repositório [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) no GitHub e, em seguida, descarregue ou clone o repositório com Git para a sua máquina.

   ![Botão de descarregamento GitHub](./media/certificates-imported-pfx-configure/github-download.png)

2. Vá para `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` e abra o projeto com o Visual Studio usando o ficheiro **PFXImportPS.sln**.

3. No topo, mude de **Debug** para **Lançamento**.

4. Vá **construir** e selecione **Build PFXImportPS**. Depois de alguns momentos verá que a **confirmação conseguida** da Build aparece na parte inferior esquerda do Visual Studio.

   ![Opção Visual Studio Build](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. O processo de construção cria uma nova pasta com o Módulo PowerShell em `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Utilizará esta pasta **de lançamento** para os próximos passos.

### <a name="create-the-encryption-public-key"></a>Criar a chave pública de encriptação

Importa certificados PFX e as chaves privadas de Intune. A palavra-passe que protege a chave privada é encriptada com uma chave pública que é armazenada no local. Pode utilizar criptografia windows, um módulo de segurança de hardware ou outro tipo de criptografia para gerar e armazenar os pares de chaves públicos/privados.  Dependendo do tipo de criptografia utilizada, o par de chaves público/privado pode ser exportado num formato de ficheiro para fins de backup.

O módulo PowerShell fornece métodos para criar uma chave utilizando a criptografia do Windows. Também pode usar outras ferramentas para criar uma chave.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Para criar a chave de encriptação usando a criptografia do Windows

1. Copie a pasta *de Lançamento* criada pelo Visual Studio para o servidor onde instalou o **Conector de CertificadoPFX para o Microsoft Intune**. Esta pasta contém o módulo PowerShell.

2. No servidor, abra o *PowerShell* como Administrador e, em seguida, navegue para a pasta *Desbloqueio* que contém o módulo PowerShell.

3. Para importar o módulo, execute `Import-Module .\IntunePfxImport.psd1` para importar o módulo.

4. Em seguida, corra `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]
   > O fornecedor que utilizar deve ser novamente selecionado quando importar Certificados PFX. Pode utilizar o Fornecedor de Armazenamento de Chaves do **Software microsoft**, embora seja suportado para utilizar um fornecedor diferente. O nome-chave também é fornecido como um exemplo, e você pode usar um nome chave diferente da sua escolha.

   Se planeia importar o certificado da sua estação de trabalho, pode exportar esta chave para um ficheiro com o seguinte comando: `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path\Filename.PFX>"`

   A chave privada deve ser importada no servidor que acolhe o Conector de CertificadoPFX para o Microsoft Intune para que os certificados PFX importados possam ser processados com sucesso.

#### <a name="to-use-a-hardware-security-module-hsm"></a>Para utilizar um módulo de segurança de hardware (HSM)

Pode utilizar um módulo de segurança de hardware (HSM) para gerar e armazenar o par de chaves público/privado. Para mais informações, consulte a documentação do fornecedor hSM.

### <a name="import-pfx-certificates"></a>Certificados PFX de importação

O processo seguinte utiliza os cmdlets PowerShell como um exemplo de como importar os certificados PFX. Pode escolher diferentes opções dependendo dos seus requisitos.

As opções incluem:

- Finalidade (certificados de grupos em conjunto com base numa etiqueta):
  - não atribuído
  - smimeEncryption
  - smimeSigning

- Regime de enchimento:
  - oaepSha256
  - oaepSha384
  - oaepSha512

Selecione o Fornecedor de Armazenamento chave que corresponde ao fornecedor utilizado para criar a chave.

#### <a name="to-import-the-pfx-certificate"></a>Para importar o certificado PFX  

1. Exportar os certificados de qualquer Autoridade de Certificação (CA) seguindo a documentação do prestador.  Para os Serviços de Certificadode Diretório Ativo da Microsoft, pode utilizar [este script de amostra](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).

2. No servidor, abra o *PowerShell* como Administrador e, em seguida, navegue para a pasta *Desbloqueio* que contém o módulo PowerShell.

3. Para importar o módulo, corra `Import-Module .\IntunePfxImport.psd1`

4. Para autenticar o Intune Graph, execute `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Como a autenticação é executada contra o Graph, deve fornecer permissões ao AppID. Se é a primeira vez que usas este utilitário, é necessário um *administrador global.* Os cmdlets PowerShell utilizam o mesmo AppID que o utilizado com [amostras intune PowerShell](https://github.com/microsoftgraph/powershell-intune-samples).

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

   - **Finalidade prevista**: Especificar o objetivo dos certificados importados para este perfil. Os administradores podem importar certificados com diferentes fins previstos (como a assinatura S/MIME ou a encriptação S/MIME). A finalidade selecionada no perfil do certificado corresponde ao perfil do certificado com os certificados importados adequados. O objetivo pretendido é uma etiqueta para agrupar os certificados importados em conjunto e não garante que os certificados importados com essa etiqueta cumpram o objetivo pretendido.  
   - **Período de validade**do certificado : A menos que o período de validade tenha sido alterado no modelo de certificado, esta opção não se aplica a um ano.
   - **Fornecedor de armazenamento de chaves (KSP)**: para dispositivos com Windows, selecione onde armazenar as chaves no dispositivo.

5. Selecione **OK** > **Criar** para guardar o perfil.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. [Atribua](../configuration/device-profile-assign.md) o novo perfil do dispositivo.
