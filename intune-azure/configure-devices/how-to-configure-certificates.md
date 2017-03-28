---
title: Como configurar certificados com o Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para criar e atribuir certificados que o ajudam a proteger ligações Wi-Fi, VPN, entre outras."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: d1c1833ea7fe9e794a70b2b2536f44801b68fa7e
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>Como configurar certificados no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Quando concede aos utilizadores acesso aos recursos da empresa através de VPN, Wi-Fi ou perfis de e-mail, pode proteger o acesso através de um certificado instalado em cada dispositivo de utilizador. O fluxo de trabalho de alto nível é o seguinte:

1. Confirme que tem aplicada a infraestrutura de certificado correta. Pode utilizar [certificados SCEP](configure-certificate-infrastructure-for-scep.md) e [certificados PKCS](configure-certificate-infrastructure-for-pfx.md).
2. Instale um certificado de raiz ou um certificado de Autoridade de Certificação (AC) intermediária em cada dispositivo, para que estes reconheçam a legitimidade da sua AC. Para tal, crie e implemente um **perfil de certificado fidedigno**. Ao atribuir este perfil, os dispositivos que gere com o Intune vão pedir e receber o certificado de raiz. Tem de criar um perfil separado para cada plataforma. Os perfis de certificado fidedigno estão disponíveis para estas plataformas:
    - iOS 8.0 e posterior
    - macOS 10.9 e posterior
    - Android 4.0 e posterior <!--Android for Work --->
    - Windows 8.1 e posterior
    - Windows Phone 8.1 e posterior
    - Windows 10 e posterior
3. Crie perfis de certificados para que os dispositivos solicitem a utilização de um certificado para autenticação do acesso a VPN, Wi-Fi e e-mail. Pode criar e implementar um perfil de certificado **PKCS** ou **SCEP** em dispositivos que executam as plataformas seguintes:
    - iOS 8.0 e posterior
    - Android 4.0 e posterior
    - Android for Work
    - Windows 10 (para Computadores e Dispositivos Móveis) e posterior

    Apenas pode utilizar um perfil de certificado SCEP com estas plataformas:

-     macOS 10.9 e posterior
-     Windows Phone 8.1 e posterior

Tem de criar um perfil separado para cada plataforma de dispositivo. Ao criar o perfil, associe-o ao perfil de certificado de raiz fidedigna criado.

### <a name="further-considerations"></a>Considerações adicionais

- Se não tiver uma Autoridade de Certificação Empresarial, tem de criar uma.
- Se decidir, com base nas suas plataformas de dispositivos, utilizar o perfil de protocolo SCEP (Simple Certificate Enrollment Protocol), terá também de configurar um servidor do Serviço de Inscrição de Dispositivos de Rede (NDES).
- Se planear utilizar os perfis SCEP ou PKCS, terá de transferir e configurar o Microsoft Intune Certificate Connector.

## <a name="before-you-start"></a>Antes de começar


### <a name="if-you-want-to-use-scep-certificates"></a>Se quiser utilizar certificados SCEP

Preencha os pré-requisitos obrigatórios na [Infraestrutura de certificados para SCEP](/intune-azure/configure-devices/configure-certificate-infrastructure-for-scep).

### <a name="if-you-want-to-use-pkcs-certificates"></a>Se quiser utilizar certificados PKCS

Preencha os pré-requisitos obrigatórios na [Infraestrutura de certificados para PKCS](/intune-azure/configure-devices/configure-certificate-infrastructure-for-pfx).

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>Tarefa 1: exportar o certificado da AC de Raiz Fidedigna
Exporte o certificado de Autoridades de Certificação(AC) de Raiz Fidedigna como um ficheiro **.cer** a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporte a chave privada.

Irá importar este certificado quando configurar um perfil de certificado Fidedigno.

## <a name="task-2-create-trusted-certificate-profiles"></a>Tarefa 2: criar perfis de Certificado fidedignos
Tem de criar um perfil de certificado fidedigno para poder criar um perfil de certificado SCEP ou PKCS. Precisa de um perfil de certificado fidedigno e de um perfil SCEP ou PKCS para cada plataforma de dispositivo.

### <a name="to-create-a-trusted-certificate-profile"></a>Para criar um perfil de certificado Fidedigno

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de certificado fidedigno.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado fidedigno. Atualmente, pode escolher uma das seguintes plataformas para as definições de certificados:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Certificado fidedigno**.
7. Navegue para o certificado guardado na tarefa 1 e, em seguida, clique em **OK**.
8. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:
    - **Arquivo de certificados no computador – Raiz**
    - **Arquivo de certificados no computador – Intermédio**
    - **Armazenamento de certificados de utilizador – Intermédio**
8. Quando tiver terminado, escolha **OK**, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).


> [!Note]
> Os dispositivos Android apresentarão um aviso a indicar que uma aplicação de terceiros instalou um certificado fidedigno.

## <a name="task-3-create-scep-or-pkcs-certificate-profiles"></a>Tarefa 3: criar perfis de certificado SCEP ou PKCS
Após criar um perfil de certificado fidedigno, crie perfis de certificado SCEP ou PKCS para cada plataforma que queira utilizar. Ao criar um perfil de certificado SCEP, tem de especificar um perfil de certificado fidedigno para a mesma plataforma. Esta ação liga os dois perfis de certificado, mas mesmo assim tem de atribuir cada perfil separadamente.

### <a name="to-create-an-scep-certificate-profile"></a>Para criar um perfil de certificado de SCEP

1. No Portal do Azure, selecione a carga de trabalho **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de certificado SCEP.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado SCEP. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Certificado SCEP**.
7. No painel **Certificado SCEP**, configure as seguintes definições:
    - **Período de validade do certificado** – Se tiver executado o comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** na AC emissora, que permite um período de validade personalizado, poderá especificar o tempo restante até o certificado expirar.<br>Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora. 
    - **Fornecedor de armazenamento de chaves (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10) – Especifique onde será armazenada a chave do certificado. Escolha um dos seguintes valores:
        - **Inscrever em KSP de Trusted Platform Module (TPM) se estiver presente, caso contrário, KSP de Software**
        - **Inscrever em KSP de Trusted Platform Module (TPM), caso contrário, ocorre uma falha**
        - **Inscrever em Passport, caso contrário, ocorre uma falha (Windows 10 e posterior)**
        - **Inscrever em KSP de Software**
    - **Formato do nome do requerente** – Na lista, selecione de que forma o Intune cria automaticamente o nome do requerente no pedido de certificado. Se o certificado se destinar a um utilizador, pode também incluir o endereço de e-mail do utilizador no nome do requerente. Escolha entre:
        - **Não configurado**
        - **Nome comum**
        - **Nome comum, incluindo o e-mail**
        - **Nome comum como e-mail**
    - **Nome alternativo do requerente** – Especifique o modo como o Intune cria automaticamente os valores para o nome alternativo do requerente (SAN) no pedido de certificado. Por exemplo, se tiver selecionado um tipo de certificado de utilizador, pode incluir o nome principal de utilizador (UPN) no nome alternativo do requerente. Se o certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, tem de definir o nome alternativo do requerente com o UPN. 
    - **Utilização de chave** – Especifique as opções de utilização de chave para este certificado. Pode selecionar de entre as seguintes opções: 
        - **Cifragem de chaves:** permita a troca de chaves apenas quando a chave for encriptada. 
        - **Assinatura digital:** permita a troca de chaves apenas quando uma assinatura digital ajudar a proteger a chave. 
    - **Tamanho da chave (bits)** – Selecione o número de bits que estará contido na chave. 
    - **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10) – Selecione um dos tipos de algoritmo hash disponíveis para utilizar com este certificado. Selecione o maior nível de segurança que os dispositivos de ligação suportam. 
    - **Certificado de Raiz** – Escolha um perfil de certificado da AC de raiz que tenha configurado anteriormente e atribuído ao utilizador ou dispositivo. Este certificado da AC tem de ser o certificado de raiz da AC que irá emitir o certificado que está a configurar neste perfil de certificado. 
    - **Utilização da chave expandida** – Escolha **Adicionar** para adicionar valores ao objetivo do certificado. Na maioria dos casos, o certificado irá exigir a **Autenticação de Cliente** para o utilizador ou dispositivo poder ser autenticado num servidor. Contudo, pode adicionar mais utilizações de chave conforme necessário. 
    - **Definições de Inscrição**
        - **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
        - **URLs do Servidor SCEP** – Especifique um ou mais URLs para os servidores NDES que irão emitir os certificados através de SCEP. 
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.

Siga as instruções na página de configuração do perfil para configurar as definições do perfil de certificado de SCEP.
>[!Note]
> Apenas para dispositivos iOS: em Formato de nome do Requerente, selecione Personalizado para introduzir um formato de nome do requerente personalizado.
> As duas variáveis atualmente suportadas pelo formato personalizado são **Nome Comum (CN)** e **E-mail (E)**. Através de uma combinação destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, como este: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**. Neste exemplo, criou um formato de nome de requerente que, além das variáveis CN e E, utiliza cadeias para os valores Unidade Organizacional, Organização, Localização, Estado e País. [Este tópico](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) mostra a função **CertStrToName** e as cadeias suportadas dela.


### <a name="to-create-a-pkcs-certificate-profile"></a>Para criar um perfil de certificado PKCS

No Portal do Azure, selecione a carga de trabalho **Configurar dispositivos**.
2. No painel **Configuração do dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, clique em **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de certificado PKCS.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado PKCS em:
    - **Android**
    - **iOS**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Certificado PKCS**.
7. No painel **Certificado PKCS**, configure as seguintes definições:
    - **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
    - **Período de validade do certificado** – Se tiver executado o comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** na AC emissora, que permite um período de validade personalizado, poderá especificar o tempo restante até o certificado expirar.<br>Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora.
    - **Fornecedor de armazenamento de chave (KSP)** (Windows 10) –
    - **Autoridade de certificação** -
    - **Nome da autoridade de certificação** -
    - **Nome do modelo de certificado** – Introduza o nome de um modelo de certificado que o Serviço de Inscrição de Dispositivos de Rede esteja configurado para utilizar e que tenha sido adicionado a uma AC emissora.
    Confirme que o nome corresponde exatamente a um dos modelos de certificado listados no registo do servidor com o Serviço de Inscrição de Dispositivos de Rede em execução. Certifique-se de que especifica o nome do modelo de certificado e não o nome a apresentar do modelo de certificado. 
    Para localizar os nomes dos modelos de certificado, navegue para a seguinte chave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Verá os modelos de certificado listados como valores para **EncryptionTemplate**, **GeneralPurposeTemplate**e **SignatureTemplate**. Por predefinição, o valor dos três modelos de certificado é IPSECIntermediateOffline, que é mapeado para o nome a apresentar de modelo **IPSec (Pedido offline)**. 
    - **Formato do nome do requerente** – Na lista, selecione de que forma o Intune cria automaticamente o nome do requerente no pedido de certificado. Se o certificado se destinar a um utilizador, pode também incluir o endereço de e-mail do utilizador no nome do requerente. Escolha entre:
        - **Não configurado**
        - **Nome comum**
        - **Nome comum, incluindo o e-mail**
        - **Nome comum como e-mail**
    - **Nome alternativo do requerente** – Especifique o modo como o Intune cria automaticamente os valores para o nome alternativo do requerente (SAN) no pedido de certificado. Por exemplo, se tiver selecionado um tipo de certificado de utilizador, pode incluir o nome principal de utilizador (UPN) no nome alternativo do requerente. Se o certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, tem de definir o nome alternativo do requerente com o UPN.
    - **Utilização da chave expandida** (Android) – Escolha **Adicionar** para adicionar valores ao objetivo do certificado. Na maioria dos casos, o certificado irá exigir a **Autenticação de Cliente** para o utilizador ou dispositivo poder ser autenticado num servidor. Contudo, pode adicionar mais utilizações de chave conforme necessário. 
    - **Certificado de Raiz** (Android) – Escolha um perfil de certificado da AC de raiz que tenha configurado anteriormente e atribuído ao utilizador ou dispositivo. Este certificado da AC tem de ser o certificado de raiz da AC que irá emitir o certificado que está a configurar neste perfil de certificado.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.

## <a name="task-4-assign-certificate-profiles"></a>Tarefa 4: atribuir perfis de certificado

Antes de atribuir perfis de certificado a grupos, considere o seguinte:

- Ao atribuir perfis de certificado a grupos, o ficheiro de certificado do perfil de certificado da AC fidedigna é instalado no dispositivo. O dispositivo utiliza o perfil de certificado de SCEP ou PKCS para criar um pedido de certificado por parte do dispositivo.
- Os perfis de certificado são instalados apenas em dispositivos que executam a plataforma que utiliza quando criou o perfil.
- Pode implementar perfis de certificado em coleções de utilizadores ou de dispositivos.
- Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, implemente o perfil de certificado num grupo de utilizadores, em vez de num grupo de dispositivos. Se implementar num grupo de dispositivos, é necessário um registo do dispositivo completo antes de o dispositivo receber políticas.
- Apesar de implementar cada perfil separadamente, também terá de implementar a AC da Raiz Fidedigna e o perfil SCEP ou PKCS. Caso contrário, a política de certificados SCEP ou PKCS falhará.

## <a name="next-steps"></a>Passos seguintes
Veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md) para obter informações gerais sobre como atribuir perfis de dispositivo.

