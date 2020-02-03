---
title: Configure infraestrutura para suportar perfis de certificadoS SCEP com Microsoft Intune - Azure Microsoft Docs
description: Para utilizar o SCEP no Microsoft Intune, configure o seu domínio AD no local, crie uma autoridade de certificação, crie o servidor NDES e instale o Conector de Certificado Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 24d0a8160d852a5a44f5df688b7e0bc230d56704
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966390"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Configure infraestruturas para apoiar o SCEP com Intune

Intune apoia a utilização do Protocolo de Inscrição de Certificados Simples (SCEP) para [autenticar ligações às suas apps e recursos corporativos.](certificates-configure.md) A SCEP utiliza o certificado da Autoridade de Certificação (CA) para garantir a troca de mensagens para o Pedido de Assinatura de Certificado (CSR). Quando a sua infraestrutura suporta o SCEP, pode utilizar perfis de *certificadoS SCEP* Intune (um tipo de perfil de dispositivo em Intune) para implementar os certificados nos seus dispositivos. O Conector de Certificado Intune da Microsoft é obrigado a utilizar perfis de certificadoS SCEP com Intune quando utilizar uma Autoridade de Certificação de Certificados de Diretório Ativo. O conector não é necessário quando se utiliza [as Autoridades](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)de Certificação da Terceira Parte . 

As informações deste artigo podem ajudá-lo a configurar a sua infraestrutura para apoiar o SCEP ao utilizar serviços de certificados de diretório ativo. Depois de configurada a sua infraestrutura, pode criar e implementar perfis de [certificadoS SCEP](certificates-profile-scep.md) com Intune.

> [!TIP]
> Intune também apoia a utilização de padrões de [criptografia de chaves públicas #12 certificados.](certficates-pfx-configure.md)

## <a name="prerequisites-for-using-scep-for-certificates"></a>Pré-requisitos para a utilização de SCEP para certificados

Antes de prosseguir, certifique-se de que criou e implementou um perfil de [certificado *fidedigno* ](certificates-configure.md#export-the-trusted-root-ca-certificate) para dispositivos que utilizarão perfis de certificadoS SCEP. Os perfis de certificado SCEP referem diretamente o perfil de certificado fidedigno que utiliza para dispositivos de provisão com um certificado De Raiz De Confiança CA.

### <a name="servers-and-server-roles"></a>Funções de servidores e servidores

A infraestrutura no local seguinte deve ser executada em servidores que estejam ligados ao seu Diretório Ativo, com exceção do Servidor proxy de aplicação web.

- Autoridade de **Certificação** – Utilize um Microsoft Ative Directory CertificateServices Enterprise Certification Authority (CA) que executa numa edição enterprise do Windows Server 2008 R2 com pacote de serviço1, ou mais tarde. A versão do Windows Server que utiliza deve permanecer no suporte pela Microsoft. Não é suportada uma AC Autónoma. Para mais informações, consulte Instalar a Autoridade de [Certificação.](https://technet.microsoft.com/library/jj125375.aspx) Se o seu CA executa o Windows Server 2008 R2 SP1, tem de [instalar o hotfix a partir de KB2483564](https://support.microsoft.com/kb/2483564/).

- **Função do servidor NDES** – Tem de configurar uma função de servidor de serviço de inscrição de dispositivos de rede (NDES) no Windows Server 2012 R2 ou posteriormente. Numa secção posterior deste artigo, guiamo-lo através da instalação de [NDES](#set-up-ndes).

  - O servidor que acolhe o NDES deve ser unido ao domínio e na mesma floresta que a sua Enterprise CA.
  - Não pode usar o NDES instalado no servidor que acolhe o Enterprise CA.
  - Irá instalar o conector Microsoft Intune Certificate no mesmo servidor que acolhe o NDES.

  Para saber mais sobre o NDES, consulte a [Orientação do Serviço](https://technet.microsoft.com/library/hh831498.aspx) de Inscrição de Dispositivos de Rede na documentação do Servidor do Windows e utilizando um Módulo de Política com o Serviço de Inscrição de [Dispositivos](https://technet.microsoft.com/library/dn473016.aspx)de Rede .

- **Conector** de certificado intune da Microsoft – O Conector de Certificado Intune da Microsoft é obrigado a utilizar perfis de certificado SCEP com Intune. Este artigo irá guiá-lo através [da instalação deste conector](#install-the-intune-certificate-connector).

  O conector suporta o modo Federal de Processamento de Informação (FIPS). O FIPS não é necessário, mas quando está ativado, pode emitir e revogar certificados.
  - O conector deve ser executado no mesmo servidor que a função do servidor NDES, um servidor que executa o Windows Server 2012 R2 ou mais tarde.
  - A estrutura .NET 4.5 é exigida pelo conector e está automaticamente incluída no Windows Server 2012 R2.
  - A configuração de segurança melhorada do Internet Explorer [deve ser desativada no servidor que acolhe o NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) e o Conector de Certificado Intune da Microsoft.

É opcional a seguinte infraestrutura no local:

Para permitir que os dispositivos na internet obtenha certificados, tem de publicar o seu URL NDES externo à sua rede corporativa. Pode utilizar o Proxy de Aplicação AD Azure, o Servidor proxy de aplicação web ou outro proxy invertido.

- **Procuração de aplicação Azure AD** (opcional) – Pode utilizar o Proxy de Aplicação AD Azure em vez de um servidor dedicado à aplicação web Proxy (WAP) para publicar o seu URL NDES na internet. Isto permite que tanto dispositivos de intranet como de internet obtenha certificados. Para obter mais informações, veja [Como fornecer acesso remoto seguro às aplicações no local](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- Servidor proxy de **aplicação web** (opcional) - Utilize um servidor que execute o Windows Server 2012 R2 ou mais tarde como um servidor proxy de aplicação web (WAP) para publicar o seu URL NDES na internet.  Isto permite que tanto dispositivos de intranet como de internet obtenha certificados.

  O servidor que aloja o WAP [tem de instalar uma atualização](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](https://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](https://support.microsoft.com/kb/3011135).

  O servidor WAP deve ter um certificado SSL que corresponda ao nome que é publicado a clientes externos e confiar no certificado SSL que é usado no computador que acolhe o serviço NDES. Estes certificados permitem ao servidor WAP interromper a ligação SSL dos clientes e criar uma nova ligação SSL ao serviço NDES.

  Para obter mais informações, veja [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) (Planear certificados para o WAP) e as [informações gerais sobre os servidores WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Contas

- **Conta de serviço NDES** - Antes de configurar o NDES, identifique uma conta de utilizador de domínio para usar como conta de serviço NDES. Irá especificar esta conta quando configurar os modelos no seu CA emissor, antes de configurar o NDES.

  Esta conta deve ter os seguintes direitos no servidor que acolhe o NDES:

  - **Logon Localmente**
  - **Logon como serviço**
  - **Logon como um trabalho de lote**

  Para mais informações, consulte Criar uma conta de utilizador de [domínio para funcionar como conta de serviço NDES](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account).

- **Acesso ao computador que acolhe o serviço NDES** - Necessitará de uma conta de utilizador de domínio com permissões para instalar e configurar funções de servidor do Windows no servidor onde instala o NDES.

- **Acesso à autoridade** de certificação - Você precisará de uma conta de utilizador de domínio que tenha direitos para gerir a sua autoridade de certificação.

### <a name="network-requirements"></a>Requisitos de rede

Recomendamos a publicação do serviço NDES através de um proxy inverso, como o proxy de [aplicação Azure AD, o Web Access Proxy,](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)ou um representante de terceiros. Se não utilizar um proxy inverso, permita o tráfego de TCP na porta 443 de todos os anfitriões e endereços IP na internet para o serviço NDES.

Permita todos os portos e protocolos necessários para a comunicação entre o serviço NDES e qualquer infraestrutura de apoio no seu ambiente. Por exemplo, o computador que acolhe o serviço NDES precisa de comunicar com os servidores CA, Servidores DNS, controladores de domínio e, possivelmente, outros serviços ou servidores dentro do seu ambiente, como o Gestor de Configuração.

### <a name="certificates-and-templates"></a>Certificados e modelos

Os seguintes certificados e modelos são utilizados quando utiliza SCEP.

|Objeto    |Details    |
|----------|-----------|
|**Modelo de certificado SCEP**         |Modelo que configurará no seu CA emissor usado para completar os pedidos scep dos dispositivos. |
|**Certificado de autenticação de cliente** |Solicitado da sua AC emissora ou CA pública.<br /> Instala este certificado no computador que acolhe o serviço NDES e é utilizado pelo Conector de Certificado Intune.<br /> Se o certificado tiver o conjunto de utilizações da chave de *autenticação* do *cliente* e do servidor (**Utilizações de chaves melhoradas**) no modelo CA que utiliza para emitir este certificado. Pode então utilizar o mesmo certificado para autenticação de servidor e cliente. |
|**Certificado de autenticação do servidor** |Certificado do Servidor Web solicitado a partir da sua CA emissora ou CA pública.<br /> Instala e liga este certificado SSL no IIS no computador que acolhe o NDES.<br />Se o certificado tiver o conjunto de utilizações da chave de *autenticação* do *cliente* e do servidor (**Utilizações de chaves melhoradas**) no modelo CA que utiliza para emitir este certificado. Pode então utilizar o mesmo certificado para autenticação de servidor e cliente. |
|**Certificado da AC de Raiz Fidedigna**       |Para utilizar um perfil de certificado SCEP, os dispositivos devem confiar na sua Autoridade de Certificação de Raiz Fidedigna (CA). Utilize um perfil de *certificado fidedigno* no Intune para fornecer o certificado De Raiz de Confiança CA aos utilizadores e dispositivos. <br/><br/> **-**  Utilize um único certificado de Root Root Ca fidedigno por plataforma do sistema operativo e associe esse certificado a cada perfil de certificado fidedigno que criar. <br /><br /> **-**  Pode utilizar certificados adicionais de Root Root CA quando necessário. Por exemplo, pode utilizar certificados adicionais para fornecer um fundo a um CA que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi. Crie certificados adicionais de Root Root CA para a emissão de CAs.  No perfil de certificado SCEP que cria em Intune, não se esqueça de especificar o perfil de Root CA fidedigno para o CA emissor.<br/><br/> Para obter informações sobre o perfil de certificado fidedigno, consulte [Exportar o certificado de ca de raiz fidedigno](certificates-configure.md#export-the-trusted-root-ca-certificate) e criar perfis de [certificadofiais](certificates-configure.md#create-trusted-certificate-profiles) em *certificados de utilização para autenticação no Intune*. |

## <a name="configure-the-certification-authority"></a>Configurar a autoridade de certificação

Nas seguintes secções, irá:

- Configure e publique o modelo necessário para NDES
- Detete as permissões necessárias para a revogação do certificado.

As seguintes secções requerem conhecimento do Windows Server 2012 R2 ou posterior, e dos Serviços de Certificadode Diretório Ativo (AD CS).

### <a name="access-your-issuing-ca"></a>Aceda ao seu CA emissor

1. Inscreva-se na sua CA emissora com uma conta de domínio com direitos suficientes para gerir a AC.

2. Abra a Consola de Gestão Microsoft Management Authority Authority Authority (MMC). Ou **executar** 'certsrv.msc' ou no **Server Manager,** clique em **Ferramentas**, e, em seguida, clique na Autoridade de **Certificação**.

3. Selecione o nó de modelos de **certificado,** clique em **Ação** > **Gerir**.

### <a name="create-the-scep-certificate-template"></a>Criar o modelo de certificado SCEP

1. Crie um modelo de certificado v2 (com compatibilidade com o Windows 2003) para utilização como modelo de certificado SCEP. É possível:

   - Utilize os *modelos* de certificado snap-in para criar um novo modelo personalizado.
   - Copie um modelo existente (como o modelo de utilizador) e, em seguida, atualize a cópia para usar como modelo NDES.

2. Configure as seguintes definições nos separadores especificados do modelo:

   - **Geral:**

     - Desverificar **Publique certificado em Diretório Ativo**.
     - Especifique um nome de **exibição** de modelo amigável para que possa identificar este modelo mais tarde.

   - **Nome do assunto:**

     - Selecione **Fornecimento no pedido**. A segurança é imposta pelo módulo de política Intune para NDES.

       ![Modelo, separador nome do requerente](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **Extensões:**

     - Certifique-se de que **a Descrição das Políticas de Aplicação** inclui **a Autenticação do Cliente.**

       > [!IMPORTANT]
       > Adicione apenas as políticas de candidatura que necessita. Confirme as escolhas com os administradores de segurança.

     - Para modelos de certificados iOS e macOS, também edite o **Uso da Chave** e certifique-se de que a Assinatura é prova de **origem** não é selecionada.

     ![Modelo, separador extensões](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Segurança:**

     - Adicione a conta de **serviço NDES**. Esta conta requer **permissões de leitura** e **inscrição** para este modelo.

     - Adicione contas adicionais para administradores Intune que irão criar perfis SCEP. Estas contas requerem **permissões de leitura** para o modelo para permitir que estes administradores naveguem para este modelo enquanto criam perfis SCEP.

     ![Modelo, separador segurança](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - **Tratamento de pedidos:**

     A imagem que se segue é um exemplo. A sua configuração pode variar.  

     ![Modelo, separador processamento de pedidos](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - **Requisitos de emissão:**

     A imagem que se segue é um exemplo. A sua configuração pode variar.

     ![Modelo, separador requisitos de emissão](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. Guarde o modelo de certificado.

### <a name="create-the-client-certificate-template"></a>Criar o modelo de certificado de cliente

O Conector de Certificado Intune requer um certificado com a autenticação do *cliente Utilização* melhorada da chave e nome do assunto igual ao FQDN da máquina onde o conector está instalado. É necessário um modelo com as seguintes propriedades:

- **Extensões** > Políticas de **Aplicação** devem conter **autenticação do cliente**
- **Nome do assunto** > **Fornecimento no pedido**.

Se já tem um modelo que inclui estas propriedades, pode reutilizá-lo, caso contrário, criar um novo modelo duplicando um existente ou criando um modelo personalizado.

### <a name="create-the-server-certificate-template"></a>Criar o modelo de certificado de servidor

As comunicações entre dispositivos geridos e IIS no servidor NDES utilizam HTTPS, o que requer a utilização de um certificado. Pode utilizar o modelo de certificado **do Web Server** para emitir este certificado. Ou, se preferir ter um modelo dedicado, são necessárias as seguintes propriedades:

- **Extensões** > Políticas de **aplicação** devem conter **autenticação do servidor**
- **Nome do assunto** > **Fornecimento no pedido**.

> [!NOTE]
> Se tiver um certificado que satisfaça os dois requisitos dos modelos de certificado de cliente e servidor, pode utilizar um único certificado tanto para o IIS como para o conector Intune Certificate.

### <a name="grant-permissions-for-certificate-revocation"></a>Concessão de permissões para revogação de certificado

Para que a Intune possa revogar os certificados que já não são necessários, deve conceder permissões na Autoridade de Certificados.

No Conector de Certificado Intune, pode utilizar a conta do sistema do **servidor** NDES ou uma conta específica, como a conta de **serviço NDES**.

1. Na consola da Autoridade de Certificados, clique no nome CA e selecione **Propriedades**.

2. No separador **Segurança,** clique em **Adicionar**.

3. Concessão e Autorização de **Gestão de Certificados:**

   - Se optar por utilizar a **conta**do sistema de servidor Esfumaça , forneça as permissões ao servidor NDES.
   - Se optar por utilizar a conta de **serviço NDES,** forneça permissões para essa conta.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Modificar o período de validade do modelo de certificado

É opcional modificar o período de validade do modelo de certificado.  

Depois de [criar o modelo de certificado SCEP,](#create-the-scep-certificate-template)pode editar o modelo para rever o período de **validade** no separador **Geral.**

Por predefinição, o Intune utiliza o valor configurado no modelo. No entanto, pode configurar o CA para permitir que o solicitado introduza um valor diferente, e esse valor pode ser definido a partir da consola Intune.

> [!IMPORTANT]
> Para iOS e macOS, utilize sempre um conjunto de valor no modelo.

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Para configurar um valor que pode ser definido a partir da consola Intune

1. Na AC, execute os seguintes comandos:

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**certsvc de início líquido**

2. Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado. Selecione o nó de modelos de **certificado,** selecione **Action** > **Novo** modelo de certificado de > **para emitir,** e, em seguida, selecione o modelo de certificado que criou na secção anterior.

3. Valide que o modelo tenha sido publicado visualizando-o na pasta modelos de **certificado.**

## <a name="set-up-ndes"></a>Configurar NDES

Os seguintes procedimentos podem ajudá-lo a configurar o Serviço de Inscrição de Dispositivos de Rede (NDES) para utilização com o Intune. Para mais informações sobre o NDES, consulte [a Orientação](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11))do Serviço de Inscrição de Dispositivos de Rede .

### <a name="install-the-ndes-service"></a>Instale o serviço NDES

1. No servidor que irá hospedar o seu serviço NDES, inscreva-se como **Administrador da Empresa,** e depois utilize o [Assistente de Adicionar e Funcionalidades](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) para instalar o NDES:

   1. No Assistente, selecione **Serviços de Certificados do Active Directory** para obter acesso aos Serviços de Função AD CS. Selecione serviço de inscrição de dispositivos de **rede,** desmarque a Autoridade de **Certificação**e, em seguida, complete o assistente.

      > [!TIP]
      > Em curso de **instalação,** não selecione **Fechar**. Em alternativa, selecione a ligação para **Configurar os Serviços de Certificados do Active Directory no servidor de destino**. O assistente de **configuração AD CS** abre, que utiliza para o próximo procedimento neste artigo, *Configurar o serviço NDES*. Após a Configuração de AD CS abrir, pode fechar o assistente para Adicionar Funções e Funcionalidades.

   2. Quando o NDES é adicionado ao servidor, o assistente também instala o IIS. Confirme que o IIS tem as seguintes configurações:

      - **Servidor Web** > **Segurança** > **Filtragem de Pedidos**
      - **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 3.5**

        A instalação do ASP.NET 3.5 instala o .NET Framework 3.5. Ao instalar o .NET Framework 3.5, instala tanto a funcionalidade **.NET Framework 3.5** principal como a **Ativação HTTP**.

      - **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 4.5**

        A instalação do ASP.NET 4.5 instala o .NET Framework 4.5. Ao instalar o .NET Framework 4.5, instale a funcionalidade **.NET Framework 4.5** principal, o **ASP.NET 4.5** e a funcionalidade **Serviços do WCF** > **Ativação HTTP**.

      - **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com Metabase do IIS 6**
      - **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade WMI do IIS 6**
      - No servidor, adicione a conta do serviço do NDES como membro do grupo local **IIS_IUSR**.

2. No computador que acolhe o serviço NDES, execute o seguinte comando num pedido de comando elevado. O seguinte comando define o SPN da conta de Serviço NDES:

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   Por exemplo, se o computador que acolhe o serviço NDES for nomeado **Server01**, o seu domínio é **Contoso.com**, e a conta de serviço for **NDESService,** use:

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Configure o serviço NDES

1. No computador que acolhe o serviço NDES, abra o assistente de **configuração AD CS** e, em seguida, faça as seguintes atualizações:

   > [!TIP]
   > Se continuar a partir do último procedimento e clicar nos Serviços de Certificado de **Diretório Ativo configure no** link do servidor de destino, este assistente já deve estar aberto. Caso contrário, abra o Gestor de Servidores para aceder à configuração pós-implementação dos Serviços de Certificados do Active Directory.

   - Nos **Serviços de Role,** selecione o Serviço de Inscrição de **Dispositivos de Rede**.
   - Na **Conta de Serviço para NDES,** especifique a Conta de Serviço NDES.
   - Em **CA para NDES,** clique em **Select**, e, em seguida, selecione o CA emissor onde configurao o modelo de certificado.
   - Em **Criptografia para NDES** defina o comprimento da chave para corresponder aos requisitos da sua empresa.
   - Em **Confirmação**, selecione **Configurar** para concluir o assistente.

2. Depois de o assistente estar concluído, atualize a seguinte tecla de registo no computador que acolhe o serviço NDES:

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   Para atualizar esta tecla, identifique o **propósito** dos modelos de certificado (encontrado no seu separador **De Manuseamento de Pedidos).** Em seguida, atualize a correspondente entrada de registo substituindo os dados existentes pelo nome do modelo de certificado (não o nome de exibição do modelo) que especificou quando [criou o modelo de certificado](#create-the-scep-certificate-template).

   A seguinte tabela mapeia o objetivo do modelo de certificado para os valores do registo:

   |Objetivo do modelo de certificado (no separador Manipulação de Pedidos)|Valor do registo a editar|Valor visto na consola de administração do Intune para o perfil SCEP|
   |------------------------|-------------------------|---|
   |Assinatura               |SignatureTemplate        |Assinatura Digital |
   |Encriptação              |EncryptionTemplate       |Cifragem de Chaves  |
   |Assinatura e encriptação|GeneralPurposeTemplate   |Cifragem de Chaves <br/> Assinatura Digital |

   Por exemplo, se o Objetivo do seu modelo de certificado for **Encriptação**, edite o valor **EncryptionTemplate** para que tenha o mesmo nome do modelo de certificado.

3. Configure a filtragem do pedido IIS para adicionar suporte no IIS para os URLs longos (consultas) que o serviço NDES recebe.

   1. No gestor IIS, selecione **'Predefinido Web Site** > **Solicitar filtragem** > **Editar Definição** de funcionalidade seletiva para abrir a página de Definições de Filtragem de **Pedidos de Edição.**

   2. Configure as seguintes definições:

      - **Comprimento máximo de URL (Bytes)** = 65534
      - **Corda de consulta máxima (Bytes)** = 65534

   3. Selecione **OK** para guardar esta configuração e fechar o gestor IIS.

   4. Validar esta configuração visualizando a seguinte chave de registo para confirmar que tem os valores indicados:

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      Os seguintes valores são definidos como entradas dWORD:

      - Nome: **MaxFieldLength**, com um valor decimal de **65534**
      - Nome: **MaxRequestBytes**, com um valor decimal de **65534**

4. Reiniciar o servidor que acolhe o serviço NDES. Não utilize **o iisreset;** iireset não completa as alterações necessárias.

5. Navegue para *http://* Server_FQDN */certsrv/mscep/mscep.dll*. Deve ver uma página NDES semelhante à seguinte imagem:

   ![Testar NDES](./media/certificates-scep-configure/scep-ndes-url.png)

   Se o endereço web devolver um **Serviço 503 indisponível,** verifique o visualizador do evento dos computadores. Este erro ocorre geralmente quando o conjunto de aplicações é interrompido devido a uma permissão em falta para a conta de [serviço NDES](#accounts).
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Instale e ligue certificados no servidor que acolhe O NDES

> [!TIP]
> No procedimento seguinte, pode utilizar um único certificado para *autenticação* do servidor e *autenticação do cliente* quando esse certificado estiver configurado para satisfazer os critérios de ambas as utilizações. Os critérios para cada utilização são descritos nos passos 1 e 3 do seguinte procedimento.

1. Solicite um certificado de **autenticação** do servidor a partir do seu CA interno ou CA público e, em seguida, instale o certificado no servidor.

   Se o servidor utilizar um nome externo e interno para um único endereço de rede, então o certificado de autenticação do servidor deve ter:

   - Um **nome de assunto** com um nome de servidor público externo.
   - Um **Nome Alternativo sujeito** que inclui o nome do servidor interno.

2. Ligue o certificado de autenticação do servidor no IIS:

   1. Depois de instalar o certificado de autenticação do servidor, abra o **IIS Manager**e selecione o **Web Site predefinido**. No painel **Ações**, selecione **Enlaces**.

   1. Selecione **Adicionar**, defina o **Tipo** para **https** e, em seguida, confirme que a porta é **443**.
   
   1. Para o **certificado SSL**, especifique o certificado de autenticação de servidor.

3. No seu Servidor do NDES, peça e instale um certificado de **autenticação de cliente** à sua AC interna ou a uma autoridade de certificado pública.

   O certificado de autenticação de cliente tem de ter as seguintes propriedades:

   - **Utilização da chave melhorada**: Este valor deve incluir **a autenticação do cliente.**
   - **Nome**do Assunto : O valor deve ser igual ao nome DNS do servidor onde está a instalar o certificado (o Servidor NDES).

4. O servidor que acolhe o serviço NDES está agora pronto para suportar o Conector de Certificado Intune.

## <a name="install-the-intune-certificate-connector"></a>Instalar o Conector de Certificado Intune

O Conector de Certificado Intune da Microsoft instala-se no servidor que executa o seu serviço NDES. Não é suportado para usar O Conector de Certificado Intune no mesmo servidor que a sua Autoridade de Certificação emissora (CA).

### <a name="to-install-the-certificate-connector"></a>Para instalar o Conector de Certificado

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Administração de locatários** > **conectores e tokens** > **conectores de certificado** > **Adicionar**.

3. Descarregue e guarde o conector para o ficheiro SCEP. Guarde-o numa localização acessível a partir do servidor onde vai instalar o conector.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. Quando a transferência for concluída, aceda ao servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES). Em seguida:

   1. Confirme que a estrutura .NET 4.5 está instalada, tal como é exigido pelo Conector de Certificado Intune. O .NET 4.5 Framework é automaticamente incluído com o Windows Server 2012 R2 e versões mais recentes.

   2. Execute o instalador **NDESConnectorSetup.exe**. O instalador também instala o módulo de política para o NDES e o Serviço Web do Ponto de Registo de Certificados IIS (CRP). O Serviço Web CRP, *CertificateRegistrationSvc,* funciona como uma aplicação no IIS.

      Ao instalar o NDES para o Intune autónomo, o serviço CRP é instalado automaticamente com o Certificate Connector.

5. Quando solicitado para o certificado de cliente para o Conector de Certificado, escolha **Select**, e selecione o certificado de **autenticação** do cliente instalado no seu Servidor NDES durante a fase #3 do procedimento [Instale e ligue certificados no servidor que acolhe NDES](#install-and-bind-certificates-on-the-server-that-hosts-ndes) a partir do início deste artigo.

   Depois de selecionar o certificado de autenticação do cliente, é devolvido ao Certificado de Cliente para a superfície do **Conector** de Certificado Intune da Microsoft. Embora o certificado selecionado não seja mostrado, selecione **Next** para ver as propriedades desse certificado. Selecione **Seguinte** e, em seguida, **Instalar**.

> [!NOTE]
> Devem ser efetuadas alterações a seguir para os inquilinos do GCC High antes do lançamento do Conector de Certificado Intune.
> 
> Faça edições para os dois ficheiros de config listados abaixo que atualizarão os pontos finais do serviço para o ambiente GCC High. Note que estas atualizações mudam as URIs de **.com** para **.us** sufixos. Existem um total de três atualizações URI, duas atualizações dentro do ficheiro de configuração NDESConnectorUI.exe.config e uma atualização no ficheiro NDESConnector.exe.config.
> 
> - Nome do ficheiro: <install_Path>\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.config
> 
>   Exemplo: (%programfiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.config)
>   ```
>    <appSettings>
>        <add key="SignInURL" value="https://portal.manage.microsoft.us/Home/ClientLogon"/>
>        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
>        <add key="AccountPortalURL" value="https://manage.microsoft.us"/>
>    </appSettings>
>   ```
> 
> - Nome do ficheiro: <install_Path>\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config
>
>   Exemplo: (%programfiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config)
>    ```
>    <appSettings>
>        <add key="BaseServiceAddress" value="https://manage.microsoft.us/" />
>    ```
>
> Se estas edições não estiverem concluídas, os inquilinos do GCC High terão o erro: "Acesso negado" "Você não está autorizado a ver esta página"

6. Após o assistente ser concluído, mas antes de o fechar, selecione a opção para **Iniciar a IU do Certificate Connector**.

   Se fechar o assistente antes de lançar o Certificado Connector UI, pode reabri-lo executando o seguinte comando:

   *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe*

7. Na IU do **Certificate Connector** :

   1. Selecione **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global.

   2. A conta que utiliza deve ser atribuída a uma licença Intune válida.

   3. Depois de iniciar sessão, o Intune Certificate Connector descarrega um certificado de Intune. Este certificado é utilizado para efeitos de autenticação entre o conector e o Intune. Se a conta que usou não tiver uma licença Intune, o conector (NDESConnectorUI.exe) não obtém o certificado da Intune.  

      Se a sua organização utilizar um servidor proxy e o proxy for necessário para o servidor do NDES aceder à Internet, selecione **Utilizar servidor proxy**. Em seguida, introduza o nome do servidor proxy, a porta e as credenciais de conta para ligar.

   4. Selecione o separador **Avançadas** e, em seguida, introduza as credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados emissora. **Aplique** as suas alterações.  

    5. Agora, pode fechar a IU do Certificate Connector.

8. Abra uma linha de comandos, introduza **services.msc** e, em seguida, prima **Enter**. Clique com o botão direito do rato em **Intune Connector Service** > **Reiniciar**.

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL. Deve devolver um erro **403:** `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> O Conector intune suporta TLS 1.2. Se o servidor que acolhe o conector suportar TLS 1.2, então é utilizado TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

## <a name="next-steps"></a>Próximos passos

[Criar um perfil de certificado SCEP](certificates-profile-scep.md)  
[Problemas de resolução de problemas para o conector de certificado Intune](troubleshoot-certificate-connector-events.md)
