---
title: Usar perfis de certificado SCEP com Microsoft Intune-Azure | Microsoft Docs
description: Crie e atribua perfis de certificado de protocolo SCEP (SCEP) com Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
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
ms.openlocfilehash: 9469bbe7098bf8c3d29a6357cb5ad971124bde09
ms.sourcegitcommit: f46df983b66845bea24a90aaa2ac6cace16b9b0b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051935"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Criar e atribuir perfis de certificado SCEP no Intune

Depois de [configurar sua infraestrutura](certificates-scep-configure.md) para dar suporte a certificados de protocolo SCEP (SCEP), você pode criar e atribuir perfis de certificado SCEP a usuários e dispositivos no Intune.

> [!IMPORTANT]  
> Antes de criar perfis de certificado SCEP, os dispositivos que usarão um perfil de certificado SCEP devem confiar em sua AC (autoridade de certificação) raiz confiável. Usar um *perfil de certificado confiável* no Intune para provisionar o certificado de AC raiz confiável para usuários e dispositivos para obter informações sobre o perfil de certificado confiável, consulte [exportar o certificado de AC raiz confiável](certificates-configure.md#export-the-trusted-root-ca-certificate) e [criar um certificado confiável perfis](certificates-configure.md#create-trusted-certificate-profiles) em *usar certificados para autenticação no Intune*.


## <a name="create-a-scep-certificate-profile"></a>Criar um perfil de certificado SCEP

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfil de configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

4. Introduza um **Nome** e uma **Descrição** para o perfil de certificado SCEP.

5. Na lista suspensa **plataforma** , selecione uma [plataforma de dispositivo com suporte](certificates-configure.md#supported-platforms-and-certificate-profiles) para este certificado SCEP.

6. Na lista suspensa **tipo de perfil** , selecione **certificado SCEP**.  

   Para a plataforma **Android Enterprise** , o *tipo de perfil* é dividido em duas categorias, *somente proprietário do dispositivo* e *somente perfil de trabalho*. Certifique-se de selecionar o perfil de certificado SCEP correto para os dispositivos que você gerencia.  

   Os perfis de certificado SCEP para o perfil *somente proprietário do dispositivo* têm as seguintes limitações:

   1. Não há suporte para as seguintes variáveis:

      - CN = {{OnPrem_Distinguished_Name}}
      - CN = {{onPremisesSamAccountName}}

   2. Em monitoramento, o relatório de certificados não está disponível para perfis de certificado SCEP do proprietário do dispositivo.

   3. Você não pode usar o Intune para revogar certificados que foram provisionados por perfis de certificado SCEP para proprietários de dispositivo. Você pode gerenciar a revogação por meio de um processo externo ou diretamente com a autoridade de certificação. 

7. Selecione **configurações**e, em seguida, conclua as seguintes configurações:

   - **Tipo de certificado**:

     *(Aplica-se a: Android, Android Enterprise, iOS, macOS, Windows 8.1 e posterior e Windows 10 e posterior.)*

     Selecione um tipo dependendo de como você usará o perfil de certificado:

     - **Usuário**: certificados de *usuário* podem conter atributos de usuário e de dispositivo no assunto e San do certificado.  
     - **Dispositivo**: certificados de *dispositivo* só podem conter atributos de dispositivo no assunto e San do certificado.

       Use o **dispositivo** para cenários como dispositivos sem usuário, como quiosques ou para dispositivos Windows. Em dispositivos Windows, o certificado é colocado no repositório de certificados do computador local.

   - **Formato do nome da entidade**:

     Selecione como o Intune cria automaticamente o nome da entidade na solicitação de certificado. As opções para o formato de nome da entidade dependem do tipo de certificado selecionado, seja **usuário** ou **dispositivo**.

     > [!NOTE]
     > Há um [problema conhecido](#avoid-certificate-signing-requests-with-escaped-special-characters) para usar o SCEP para obter certificados quando o nome da entidade na CSR (solicitação de assinatura de certificado) resultante inclui um dos seguintes caracteres como um caractere de escape (continuado por uma barra invertida \\):
     > - \+
     > - ;
     > - ,
     > - =

     - **Tipo de certificado Utilizador**

       As opções de formato para o *formato de nome da entidade* incluem:

       - **Não configurado**
       - **Nome comum**
       - **Nome comum, incluindo o e-mail**
       - **Nome comum como e-mail**
       - **Identidade Internacional do Equipamento Móvel (IMEI)**
       - **Número de série**
       - **Personalizado**: ao selecionar esta opção, é também apresentada a caixa de texto **Personalizado**. Utilize este campo para introduzir um formato de nome de requerente personalizado, incluindo variáveis. O formato personalizado suporta duas variáveis: **Nome Comum (CN)** e **E-mail (E)** . O **Nome Comum (CN)** pode ser definido para qualquer uma das seguintes variáveis:

         - **CN = {{username}}** : o nome UPN do usuário, como janedoe@contoso.com.
         - **CN={{AAD_Device_ID}}** : um ID atribuído ao registar um dispositivo no Azure Active Directory (AD). Este ID é normalmente utilizado na autenticação com o Azure AD.
         - **CN = {{SERIALNUMBER}}** : o número de série exclusivo (SN) normalmente usado pelo fabricante para identificar um dispositivo.
         - **CN = {{IMEINumber}}** : o número exclusivo IMEI (identidade de equipamentos móveis internacional) usado para identificar um telefone celular.
         - **CN = {{OnPrem_Distinguished_Name}}** : uma sequência de nomes distintos relativos separados por vírgula, como *CN = Jane Doe, ou = accounts, DC = Corp, DC = contoso, DC = com*.

           Para usar a variável *{{OnPrem_Distinguished_Name}}* , certifique-se de sincronizar o atributo de usuário *onpremisesdistinguishedname* usando [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) para o Azure AD.

         - **CN = {{onPremisesSamAccountName}}** : os administradores podem sincronizar o atributo samAccountName de Active Directory ao Azure ad usando o Azure ad Connect em um atributo chamado *onPremisesSamAccountName*. O Intune pode substituir essa variável como parte de uma solicitação de emissão de certificado no assunto de um certificado. O atributo samAccountName é o nome de entrada do usuário usado para dar suporte a clientes e servidores de uma versão anterior do Windows (anterior ao Windows 2000). O formato do nome de entrada do usuário é: *DomainName\testUser*ou somente *testuser*.

            Para usar a variável *{{onPremisesSamAccountName}}* , certifique-se de sincronizar o atributo de usuário *onPremisesSamAccountName* usando [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) ao Azure AD.

         Através de uma combinação de uma ou várias destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, como o seguinte:  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

         Esse exemplo inclui um formato de nome de entidade que usa as variáveis CN e e e cadeias de caracteres para os valores de unidade organizacional, organização, local, estado e país. O artigo [função CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) descreve esta função e as cadeias suportadas da mesma.

      - **Tipo de certificado Dispositivo**

        As opções de formato para o formato de nome da entidade incluem as seguintes variáveis:

        - **{{AAD_Device_ID}}** ou **{{AzureADDeviceId}}** -qualquer variável pode ser usada para identificar um dispositivo por sua ID do Azure AD.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(aplicável somente para dispositivos Windows e ingressados no domínio)*
        - **{{MEID}}**

        Você pode especificar essas variáveis, seguidas pelo texto da variável, na caixa de texto. Por exemplo, o nome comum para um dispositivo chamado *Device1* pode ser adicionado como **CN = {{DeviceName}} Device1**.

        > [!IMPORTANT]
        > - Quando você especifica uma variável, coloque o nome da variável entre chaves {}, como mostrado no exemplo, para evitar um erro.  
        > - As propriedades de dispositivo usadas no *assunto* ou *San* de um certificado de dispositivo, como **IMEI**, **SerialNumber**e **FullyQualifiedDomainName**, são propriedades que podem ser falsificadas por uma pessoa com acesso ao dispositivo.
        > - Um dispositivo deve dar suporte a todas as variáveis especificadas em um perfil de certificado para que esse perfil seja instalado nesse dispositivo.  Por exemplo, se **{{IMEI}}** for usado no nome da entidade de um perfil SCEP e for atribuído a um dispositivo que não tem um número IMEI, o perfil não será instalado.

   - **Nome alternativo da entidade**: selecione como o Intune cria automaticamente o San (nome alternativo da entidade) na solicitação de certificado. As opções para a SAN dependem do tipo de certificado selecionado; o **usuário** ou o **dispositivo**.

      - **Tipo de certificado Utilizador**

        Selecione um dos atributos disponíveis:

        - **Endereço de e-mail**
        - **Nome principal do usuário (UPN)**

        Por exemplo, os tipos de certificado de usuário podem incluir o nome principal do usuário (UPN) no nome alternativo da entidade. Se um certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, defina o nome alternativo do requerente como UPN.

      - **Tipo de certificado Dispositivo**

        Use a lista suspensa **atributo** e selecione um atributo, atribua um **valor**e **adicione** -o ao perfil de certificado. Você pode adicionar vários valores selecionando atributos adicionais.

        Os atributos disponíveis incluem:

        - **Endereço de e-mail**
        - **Nome principal do usuário (UPN)**
        - **DNS**

        Com o tipo de certificado *Dispositivo*, pode utilizar as seguintes variáveis de certificado de dispositivo para o valor:

        - **{{AAD_Device_ID}}** ou **{{AzureADDeviceId}}** -qualquer variável pode ser usada para identificar um dispositivo por sua ID do Azure AD.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        Para especificar um valor para um atributo, inclua o nome da variável com chaves, seguido pelo texto para essa variável. Por exemplo, um valor para o atributo DNS pode ser adicionado **{{AzureADDeviceId}}. domain. com** onde *. domain.com* é o texto. Para um usuário chamado *user1* , um endereço de email pode aparecer como {{FullyQualifiedDomainName}} User1@Contoso.com.

        > [!IMPORTANT]
        > - Ao usar uma variável de certificado de dispositivo, coloque o nome da variável entre chaves {}.
        > - Não use chaves **{}** , símbolos de pipe **|** e ponto-e-vírgulas **;** no texto que segue a variável.
        > - As propriedades de dispositivo usadas no *assunto* ou *San* de um certificado de dispositivo, como **IMEI**, **SerialNumber**e **FullyQualifiedDomainName**, são propriedades que podem ser falsificadas por uma pessoa com acesso ao dispositivo.
        > - Um dispositivo deve dar suporte a todas as variáveis especificadas em um perfil de certificado para que esse perfil seja instalado nesse dispositivo.  Por exemplo, se **{{IMEI}}** for usado na San de um perfil SCEP e for atribuído a um dispositivo que não tem um número IMEI, o perfil não será instalado.

   - **Período de validade do certificado**:

     Pode introduzir um valor inferior ao período de validade do modelo de certificado, mas não superior. Se você configurou o modelo de certificado para [dar suporte a um valor personalizado que pode ser definido no console do Intune](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template), use essa configuração para especificar a quantidade de tempo restante antes que o certificado expire.

     Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode introduzir um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora.

   - **Provedor de armazenamento de chaves (KSP)** :

     *(Aplica-se a: Windows 8.1 e posterior e Windows 10 e posterior)*

     Especifique onde a chave para o certificado é armazenada. Escolha um dos seguintes valores:

     - **Inscrever em KSP de Trusted Platform Module (TPM) se estiver presente, caso contrário, KSP de Software**
     - **Inscrever em KSP de Trusted Platform Module (TPM), caso contrário, ocorre uma falha**
     - **Inscrever em Passport, caso contrário, ocorre uma falha (Windows 10 e posterior)**
     - **Inscrever em KSP de Software**

   - **Uso da chave**:

     Selecione as opções de uso de chave para o certificado:

     - **Assinatura digital**: permita a troca de chaves somente quando uma assinatura digital ajudar a proteger a chave.
     - **Codificação de chave**: permitir troca de chaves somente quando a chave for criptografada.

   - **Tamanho da chave (bits)** :

     Selecione o número de bits contidos na chave.

   - **Algoritmo de hash**:

     *(Aplica-se ao Android, Android Enterprise, Windows Phone 8,1, Windows 8.1 e posterior e Windows 10 e posterior)*

     Selecione um dos tipos de algoritmo hash disponíveis para utilizar com este certificado. Selecione o maior nível de segurança que os dispositivos de ligação suportam.

   - **Certificado raiz**:

     Selecione o *perfil de certificado confiável* que você configurou anteriormente e atribuiu a usuários e dispositivos aplicáveis para este perfil de certificado SCEP. O perfil de certificado confiável é usado para provisionar usuários e dispositivos com o certificado de autoridade de certificação raiz confiável. Para obter informações sobre o perfil de certificado confiável, consulte [exportar seu certificado de AC raiz confiável](certificates-configure.md#export-the-trusted-root-ca-certificate) e [criar perfis de certificado confiável](certificates-configure.md#create-trusted-certificate-profiles) em *usar certificados para autenticação no Intune*. Se você tiver uma autoridade de certificação raiz e uma autoridade de certificação emissora, selecione o perfil de certificado raiz confiável que está associado à autoridade de certificação emissora.

   - **Uso estendido de chave**:

     Adicione valores para a finalidade desejada do certificado. Na maioria dos casos, o certificado requer *autenticação de cliente* para que o usuário ou o dispositivo possa se autenticar em um servidor. Você pode adicionar mais usos de chave, conforme necessário.

   - **Limite de renovação (%)** :

     Insira a porcentagem do tempo de vida do certificado que permanece antes da renovação das solicitações de dispositivo do certificado. Por exemplo, se você inserir 20, a renovação do certificado será tentada quando o certificado for 80% expirado. As tentativas de renovação continuam até que a renovação seja bem-sucedida. A renovação gera um novo certificado, o que resulta em um novo par de chaves pública/privada.

   - **URLs do servidor SCEP**:

     Insira uma ou mais URLs para os servidores NDES que emitem certificados via SCEP. Por exemplo, insira algo como *https://ndes.contoso.com/certsrv/mscep/mscep.dll* . Você pode adicionar outras URLs de SCEP para balanceamento de carga conforme necessário, pois as URLs são enviadas aleatoriamente para o dispositivo com o perfil. Se um dos servidores de SCEP não estiver disponível, a solicitação de SCEP falhará e será possível que, em check-ins posteriores do dispositivo, a solicitação de certificado possa ser feita no mesmo servidor que está inativo.

8. Selecione **OK**e, em seguida, selecione **criar**. O perfil é criado e aparece na lista de *perfis de configuração do dispositivo* .

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Evitar solicitações de assinatura de certificado com caracteres especiais de escape

Há um problema conhecido para solicitações de certificado SCEP e PKCS que incluem um nome de entidade (CN) com um ou mais dos seguintes caracteres especiais como um caractere de escape. Os nomes de entidades que incluem um dos caracteres especiais como um caractere de escape resultam em um CSR com um nome de entidade incorreto. Um nome de assunto incorreto resulta na falha na validação do desafio SCEP do Intune e nenhum certificado emitido.

Os caracteres especiais são:
- \+
- ,
- ;
- =

Quando o nome da entidade incluir um dos caracteres especiais, use uma das opções a seguir para contornar essa limitação:

- Encapsula o valor CN que contém o caractere especial com aspas.  
- Remova o caractere especial do valor CN.

**Por exemplo**, você tem um nome de entidade que aparece como *usuário de teste (TestCompany, LLC)* .  Um CSR que inclui um CN que tem a vírgula entre *TestCompany* e *LLC* apresenta um problema.  O problema pode ser evitado colocando-se aspas em todo o CN ou removendo a vírgula entre *TestCompany* e *LLC*:

- **Adicionar aspas**: *CN =* "usuário de teste (TestCompany, LLC)", ou = accounts, DC = Corp, DC = contoso, DC = com *
- **Remova a vírgula**: *CN = test User (TestCompany LLC), ou = accounts, DC = Corp, DC = contoso, DC = com*

 No entanto, as tentativas de escapar a vírgula usando um caractere de barra invertida falharão com um erro nos logs do CRP:
 
- **Vírgula com escape**: *CN = usuário de teste (TestCompany \\, LLC), ou = accounts, DC = Corp, DC = contoso, DC = com*

O erro é semelhante ao seguinte erro:

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Atribuir o perfil de certificado

Atribua perfis de certificado SCEP da mesma maneira que [implanta perfis de dispositivo](../configuration/device-profile-assign.md) para outras finalidades. No entanto, considere o seguinte antes de continuar:

- Quando você atribui perfis de certificado SCEP a grupos, o arquivo de certificado de autoridade de certificação raiz confiável (conforme especificado no *perfil de certificado confiável*) é instalado no dispositivo. O dispositivo usa o perfil de certificado SCEP para criar uma solicitação de certificado para esse certificado de AC raiz confiável.

- O perfil de certificado SCEP é instalado somente em dispositivos que executam a plataforma que você especificou quando criou o perfil de certificado.

- Pode atribuir perfis de certificado a coleções de utilizadores ou de dispositivos.

- Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, atribua o perfil de certificado a um grupo de utilizadores, em vez de atribuir a um grupo de dispositivos. Se atribuir a um grupo de dispositivos, será preciso um registo do dispositivo completo antes de o dispositivo receber políticas.

- Se você usar o cogerenciamento para o Intune e o Configuration Manager, no Configuration Manager [defina o controle deslizante da carga de trabalho](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) para a política de acesso ao recurso para o **Intune** ou o **Intune piloto**. Essa configuração permite que os clientes do Windows 10 iniciem o processo de solicitação do certificado.

- Embora você crie e atribua o perfil de certificado confiável e o perfil de certificado SCEP separadamente, ambos devem ser atribuídos. Sem ambos instalados em um dispositivo, a política de certificado SCEP falha. Certifique-se de que todos os perfis de certificado raiz confiáveis também sejam implantados nos mesmos grupos que o perfil SCEP.

> [!NOTE]
> Em dispositivos iOS, quando um perfil de certificado SCEP é associado a um perfil adicional, como um perfil de Wi-Fi ou VPN, o dispositivo recebe um certificado para cada um desses perfis adicionais. Isso resulta no dispositivo iOS com vários certificados entregues pela solicitação de certificado SCEP.  Se desejar um único certificado, você deverá usar certificados PKCS em vez de certificados SCEP.  Isso se deve às diferenças em como os certificados SCEP e PKCS são entregues aos dispositivos.

## <a name="next-steps"></a>Próximos passos

[Atribuir perfis](../configuration/device-profile-assign.md)
