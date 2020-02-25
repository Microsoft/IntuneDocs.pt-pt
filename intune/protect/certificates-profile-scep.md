---
title: Utilize perfis de certificadoS SCEP com microsoft Intune - Azure / Microsoft Docs
description: Crie e atribua perfis de certificados simples de inscrição de certificados (SCEP) com a Microsoft Intune.
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
ms.openlocfilehash: 3cd153a4c602ba49a5b5135d1d6cb32a61f2668d
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576511"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Criar e atribuir perfis de certificado SCEP em Intune

Depois de [configurar](certificates-scep-configure.md) a sua infraestrutura para suportar certificados simples de protocolo de inscrição de certificados (SCEP), pode criar e, em seguida, atribuir perfis de certificadoS SCEP aos utilizadores e dispositivos no Intune.

> [!IMPORTANT]  
> Antes de criar perfis de certificadoS SCEP, os dispositivos que utilizarão um perfil de certificado SCEP devem confiar na autoridade de certificação de raiz fidedigna (CA). Utilize um perfil de *certificado fidedigno* no Intune para fornecer o certificado De Raiz fidedigna aos utilizadores e dispositivos Para obter informações sobre o perfil de certificado fidedigno, consulte [Exportar o certificado de raiz fidedigno](certificates-configure.md#export-the-trusted-root-ca-certificate) ca e criar perfis de certificado sintetizados em *certificados de utilização para autenticação no Intune*. [](certificates-configure.md#create-trusted-certificate-profiles)


## <a name="create-a-scep-certificate-profile"></a>Criar um perfil de certificado SCEP

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > perfil de **configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

4. Introduza um **Nome** e uma **Descrição** para o perfil de certificado SCEP.

5. A partir da lista de drop-down da **Plataforma,** selecione uma [plataforma de dispositivo suportada](certificates-configure.md#supported-platforms-and-certificate-profiles) para este certificado SCEP.

6. A partir da lista de abandono do **tipo perfil,** selecione **certificado SCEP**.  

   Para a plataforma **Android Enterprise,** o *tipo de perfil* é dividido em duas categorias, *Apenas proprietário de dispositivos* e perfil de *trabalho*. Certifique-se de selecionar o perfil de certificado SCEP correto para os dispositivos que gere.  

   Perfis de certificado SCEP para o perfil do Proprietário do *Dispositivo Apenas* têm as seguintes limitações:

   1. No âmbito da Monitorização, o relatório de certificados não está disponível para os perfis de certificado SCEP do Proprietário do Dispositivo.

   2. Não pode usar o Intune para revogar os certificados que foram provisionados pelos perfis de certificado SCEP para os Proprietários de Dispositivos. Pode gerir a revogação através de um processo externo ou diretamente com a autoridade de certificação. 

   4. Para dispositivos dedicados ao Android Enterprise, os perfis de certificadoS SCEP são suportados apenas para configuração e autenticação de rede Wi-Fi.  Os perfis de certificadoS SCEP em dispositivos dedicados ao Android Enterprise não são suportados para autenticação vpn ou app.   

   
7. Selecione **Definições**, e, em seguida, complete as seguintes configurações:

   - **Tipo de certificado:**

     *(Aplica-se a: Android, Android Enterprise, iOS/iPadOS, macOS, Windows 8.1 e mais tarde, e Windows 10 e mais tarde.)*

     Selecione um tipo dependendo de como utilizará o perfil do certificado:

     - **Utilizador**: Os certificados de *utilizador* podem conter atributos de utilizador e dispositivo no assunto e SAN do certificado.  
     - **Dispositivo**: Os certificados do *dispositivo* só podem conter atributos de dispositivo no assunto e san do certificado.

       Utilize **o Dispositivo** para cenários como dispositivos sem uso, como quiosques ou dispositivos Windows. Nos dispositivos Windows, o certificado é colocado na loja de certificados Local Computer.

   - **Formato de nome do assunto:**

     Selecione como Intune cria automaticamente o nome do assunto no pedido de certificado. As opções para o formato de nome de assunto dependem do tipo de Certificado que selecionar, seja **utilizador** ou **dispositivo**.

     > [!NOTE]
     > Existe uma [questão conhecida](#avoid-certificate-signing-requests-with-escaped-special-characters) para a utilização de SCEP para obter certificados quando o nome do assunto no pedido de assinatura de certificado (CSR) inclui um dos seguintes caracteres como um personagem escapado (procededo por um \\de backslash):
     > - \+
     > - ;
     > - ,
     > - =

     - **Tipo de certificado Utilizador**

       As opções de formato para o *formato de nome sujeito* incluem:

       - **Não configurado**
       - **Nome comum**
       - **Nome comum, incluindo o e-mail**
       - **Nome comum como e-mail**
       - **Identidade Internacional do Equipamento Móvel (IMEI)**
       - **Número de série**
       - **Personalizado**: ao selecionar esta opção, é também apresentada a caixa de texto **Personalizado**. Utilize este campo para introduzir um formato de nome de requerente personalizado, incluindo variáveis. O formato personalizado suporta duas variáveis: **Nome Comum (CN)** e **E-mail (E)** . O **Nome Comum (CN)** pode ser definido para qualquer uma das seguintes variáveis:

         - **CN={{{UserName}}** : O nome principal do utilizador, tal como janedoe@contoso.com.
         - **CN={{AAD_Device_ID}}** : um ID atribuído ao registar um dispositivo no Azure Active Directory (AD). Este ID é normalmente utilizado na autenticação com o Azure AD.
         - **CN={{{SERIALNUMBER}}** : O número de série único (SN) normalmente utilizado pelo fabricante para identificar um dispositivo.
         - **CN={{{IMEINumber}}** : O número único de identidade de equipamento móvel internacional (IMEI) utilizado para identificar um telemóvel.
         - **CN={{{OnPrem_Distinguished_Name}}** : Uma sequência de nomes relativos distintos separados por vírem, tais como *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

           Para utilizar a variável *{{OnPrem_Distinguished_Name}}* certifique-se de sincronizar o atributo do utilizador de nome no *local* utilizando o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) para o seu AD Azure.

         - **CN={{noPremisesSamAccountName}}** : Os administradores podem sincronizar o atributo samAccountName do Diretório Ativo para a AD Azure utilizando a ligação Azure AD a um atributo chamado *noPremisesSamAccountName*. Intune pode substituir essa variável como parte de um pedido de emissão de certificado em matéria de certificado. O atributo samAccountName é o nome de entrada do utilizador utilizado para suportar clientes e servidores a partir de uma versão anterior do Windows (pré-Windows 2000). O formato de sinal do utilizador no formato de nome é: *DomainName\testUser*, ou apenas *testUser*.

            Para utilizar a variável *{{onPremisesSamAccountName}}* certifique-se de sincronizar o atributo do utilizador *no LocalsSamAccountName* utilizando o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) para o seu Azure AD.

         Através de uma combinação de uma ou várias destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, como o seguinte:  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

         Este exemplo inclui um formato de nome de assunto que utiliza as variáveis CN e E, e cordas para valores da Unidade Organizacional, Organização, Localização, Estado e País. O artigo [função CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) descreve esta função e as cadeias suportadas da mesma.

      - **Tipo de certificado Dispositivo**

        As opções de formato para o formato de nome sujeito incluem as seguintes variáveis:

        - **{{AAD_Device_ID}}** ou **{{AzureADDeviceId}}** - Qualquer variável pode ser usada para identificar um dispositivo pelo seu ID AD Azure.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{Número de Série}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullQualifiedDomainName}}** *(Apenas aplicável para dispositivos windows e focados em domínios)*
        - **{{MEID}}**

        Pode especificar estas variáveis, seguidas pelo texto para a variável, na caixa de texto. Por exemplo, o nome comum para um dispositivo chamado *Device1* pode ser adicionado como **CN={{DeviceName}}Dispositivo1**.

        > [!IMPORTANT]
        > - Quando especificar uma variável, encerre o nome variável em parênteses encaracolados { } como se pode ver no exemplo, para evitar um erro.  
        > - As propriedades do dispositivo utilizadas no *assunto* ou *SAN* de um certificado de dispositivo, como **IMEI,** **SerialNumber**, e **FullQualifiedDomainName,** são propriedades que podem ser falsificadas por uma pessoa com acesso ao dispositivo.
        > - Um dispositivo deve suportar todas as variáveis especificadas num perfil de certificado para que esse perfil seja instalado nesse dispositivo.  Por exemplo, se **{{IMEI}}** for utilizado no nome do assunto de um perfil SCEP e for atribuído a um dispositivo que não tenha um número IMEI, o perfil não é instalado.

   - **Nome alternativo do assunto**: Selecione como insintono cria automaticamente o nome alternativo do sujeito (SAN) no pedido de certificado. As opções para o SAN dependem do tipo certificado que selecionou; utilizador ou **dispositivo.**

      - **Tipo de certificado Utilizador**

        Selecione entre os atributos disponíveis:

        - **Endereço de e-mail**
        - **Nome principal do utilizador (UPN)**

        Por exemplo, os tipos de certificados de utilizador podem incluir o nome principal do utilizador (UPN) no nome alternativo do assunto. Se um certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, defina o nome alternativo do requerente como UPN.

      - **Tipo de certificado Dispositivo**

        Utilize o dropdown **do Atributo** e selecione um atributo, atribua um **Valor,** e **adicione-o** ao perfil do certificado. Pode adicionar vários valores selecionando atributos adicionais.

        Os atributos disponíveis incluem:

        - **Endereço de e-mail**
        - **Nome principal do utilizador (UPN)**
        - **DNS**

        Com o tipo de certificado *Dispositivo*, pode utilizar as seguintes variáveis de certificado de dispositivo para o valor:

        - **{{AAD_Device_ID}}** ou **{{AzureADDeviceId}}** - Qualquer variável pode ser usada para identificar um dispositivo pelo seu ID AD Azure.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{Número de Série}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullQualifiedDomainName}}**
        - **{{MEID}}**

        Para especificar um valor para um atributo, inclua o nome variável com parênteses encaracolados, seguido do texto para essa variável. Por exemplo, um valor para o atributo DNS pode ser adicionado **{{AzureADDeviceId}.domain.com** onde *.domain.com* é o texto. Para um utilizador chamado *User1,* um endereço de e-mail pode aparecer como {{FullQualifiedDomainName}}User1@Contoso.com.

        > [!IMPORTANT]
        > - Quando utilizar uma variável de certificado de dispositivo, encerre o nome variável em suportes encaracolados { }.
        > - Não utilize suportes encaracolados **{ }** , símbolos de **tubos|** , e pontos evícolas; no texto que segue a variável.
        > - As propriedades do dispositivo utilizadas no *assunto* ou *SAN* de um certificado de dispositivo, como **IMEI,** **SerialNumber**, e **FullQualifiedDomainName,** são propriedades que podem ser falsificadas por uma pessoa com acesso ao dispositivo.
        > - Um dispositivo deve suportar todas as variáveis especificadas num perfil de certificado para que esse perfil seja instalado nesse dispositivo.  Por exemplo, se **{{IMEI}}** for utilizado no SAN de um perfil SCEP e for atribuído a um dispositivo que não tenha um número IMEI, o perfil não é instalado.

   - **Período de validade**do certificado:

     Pode introduzir um valor inferior ao período de validade do modelo de certificado, mas não superior. Se configurar o modelo de certificado para [suportar um valor personalizado que pode ser definido dentro da consola Intune,](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template)utilize esta definição para especificar o valor do tempo restante antes do termo do certificado.

     Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode introduzir um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora.

   - Fornecedor de **armazenamento chave (KSP)** :

     *(Aplica-se a: Windows 8.1 e mais tarde, e Windows 10 e mais tarde)*

     Especifique onde a chave do certificado está armazenada. Escolha entre os seguintes valores:

     - **Inscrever em KSP de Trusted Platform Module (TPM) se estiver presente, caso contrário, KSP de Software**
     - **Inscrever em KSP de Trusted Platform Module (TPM), caso contrário, ocorre uma falha**
     - **Inscrever em Passport, caso contrário, ocorre uma falha (Windows 10 e posterior)**
     - **Inscrever em KSP de Software**

   - **Utilização da chave:**

     Selecione as principais opções de utilização do certificado:

     - **Assinatura digital**: permitir a troca de chaves apenas quando uma assinatura digital ajudar a proteger a chave.
     - **Cifragem de chaves**: permitir a troca de chaves apenas quando a chave for encriptada.

   - **Tamanho da chave (bits)** :

     Selecione o número de bits contidos na tecla.

   - **Algoritmo de hash:**

     *(Aplica-se ao Android, empresa Android, Windows Phone 8.1, Windows 8.1 e mais tarde, e Windows 10 e mais tarde)*

     Selecione um dos tipos de algoritmo hash disponíveis para utilizar com este certificado. Selecione o maior nível de segurança que os dispositivos de ligação suportam.

   - **Certificado de raiz:**

     Selecione o *perfil de certificado fidedigno* que configurado anteriormente e atribuído aos utilizadores e dispositivos aplicáveis para este perfil de certificado SCEP. O perfil de certificado fidedigno é utilizado para fornecer utilizadores e dispositivos com o certificado Trust Root CA. Para obter informações sobre o perfil de certificado fidedigno, consulte [Exportar o seu certificado de CA de raiz fidedigna](certificates-configure.md#export-the-trusted-root-ca-certificate) e criar perfis de [certificados fidedignos](certificates-configure.md#create-trusted-certificate-profiles) em *certificados de utilização para autenticação no Intune*. Se tiver uma Autoridade de Certificação de Raiz e uma Autoridade de Certificação emissora, selecione o perfil de certificado De Raiz Fidedigno que está associado à Autoridade de Certificação emissora.

   - **Utilização alargada da chave:**

     Adicione valores para o fim a que se destina o certificado. Na maioria dos casos, o certificado requer *autenticação do cliente* para que o utilizador ou dispositivo possa autenticar um servidor. Pode adicionar utilizações adicionais de chaves conforme necessário.

   - **Limiar de renovação (%)**

     Insira a percentagem do tempo de vida útil do certificado que permanece antes de o dispositivo solicitar a renovação do certificado. Por exemplo, se introduzir 20, a renovação do certificado será tentada quando o certificado estiver 80% expirado. As tentativas de renovação continuam até que a renovação seja bem sucedida. A renovação gera um novo certificado, que resulta num novo par de chaves público/privado.

   - **URLs do Servidor SCEP:**

     Introduza um ou mais URLs para os Servidores NDES que emitem certificados via SCEP. Por exemplo, insira algo como *https://ndes.contoso.com/certsrv/mscep/mscep.dll.* Pode adicionar URLs SCEP adicionais para o equilíbrio de carga, conforme necessário, uma vez que os URLs são empurrados aleatoriamente para o dispositivo com o perfil. Se um dos servidores SCEP não estiver disponível, o pedido SCEP falhará e é possível que em check-ins posteriores do dispositivo, o pedido cert possa ser feito contra o mesmo servidor que está em baixo.

8. Selecione **OK**, e, em seguida, selecione **Criar**. O perfil é criado e aparece na configuração do Dispositivo - Lista de *Perfis.*

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Evite pedidos de assinatura de certificados com caracteres especiais escapados

Há uma edição conhecida para pedidos de certificadoS SCEP e PKCS que incluem um Nome De Assunto (CN) com um ou mais dos seguintes caracteres especiais como um personagem escapado. Nomes de assuntos que incluem um dos caracteres especiais como um personagem escapado resultam numa RSE com um nome de assunto incorreto. Um nome de assunto incorreto resulta na falha na validação do desafio SCEP intune e nenhum certificado emitido.

Os caracteres especiais são:
- \+
- ,
- ;
- =

Quando o seu nome de assunto incluir um dos caracteres especiais, utilize uma das seguintes opções para contornar esta limitação:

- Encapsular o valor NC que contém o caráter especial com citações.  
- Retire o carácter especial do valor NC.

**Por exemplo,** tem um Nome de Assunto que aparece como utilizador de *teste (TestCompany, LLC)* .  Uma RSE que inclui um CN que tem a vírem entre *a TestCompany* e a *LLC* apresenta um problema.  O problema pode ser evitado colocando cotações em todo o NC, ou removendo a vírem entre *a TestCompany* e *a LLC:*

- **Adicionar cotações**: *CN=* "Test User (TestCompany, LLC)",OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **Remova a vírcia:** *CN=Utilizador de teste (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 No entanto, as tentativas de escapar da vírem utilizando um personagem backslash falharão com um erro nos registos de CRP:
 
- **Víramida escapada**: *CN=Utilizador de teste (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

O erro é semelhante ao seguinte erro:

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Atribuir o perfil de certificado

Atribuir perfis de certificado SCEP da mesma forma que [implementa perfis de dispositivopara](../configuration/device-profile-assign.md) outros fins. No entanto, considere o seguinte antes de continuar:

- Ao atribuir perfis de certificado SCEP a grupos, o ficheiro de certificado Trust Root CA (conforme especificado no perfil de *certificado fidedigno)* é instalado no dispositivo. O dispositivo utiliza o perfil de certificado SCEP para criar um pedido de certificado para o certificado De Raiz De Confiança CA.

- O perfil do certificado SCEP instala apenas em dispositivos que executam a plataforma que especificou quando criou o perfil do certificado.

- Pode atribuir perfis de certificado a coleções de utilizadores ou de dispositivos.

- Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, atribua o perfil de certificado a um grupo de utilizadores, em vez de atribuir a um grupo de dispositivos. Se atribuir a um grupo de dispositivos, será preciso um registo do dispositivo completo antes de o dispositivo receber políticas.

- Se utilizar a cogestão para Intune e Configuration Manager, no Gestor de Configuração [defina o slider](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads) de carga de trabalho para políticas de acesso a recursos para **Intune** ou **Pilot Intune**. Esta definição permite que os clientes do Windows 10 iniciem o processo de solicitação do certificado.

- Embora crie e atribua separadamente o perfil de certificado fidedigno e o perfil de certificado SCEP, ambos devem ser atribuídos. Sem ambos instalados num dispositivo, a política de certificados SCEP falha. Certifique-se de que os perfis de certificados de raiz fidedignos também são implantados para os mesmos grupos que o perfil SCEP.

> [!NOTE]
> Nos dispositivos iOS/iPadOS, quando um perfil de certificado SCEP está associado a um perfil adicional, como um perfil Wi-Fi ou VPN, o dispositivo recebe um certificado para cada um desses perfis adicionais. Isto resulta no dispositivo iOS/iPadOS com vários certificados entregues pelo pedido de certificado SCEP.  Se for desejado um único certificado, deve utilizar certificados PKCS em vez de certificados SCEP.  Isto deve-se a diferenças na forma como os certificados SCEP e PKCS são entregues aos dispositivos.

## <a name="next-steps"></a>Próximos passos

[Atribuir perfis](../configuration/device-profile-assign.md)

[Implantação de problemas de perfis de certificados SCEP](../protect/troubleshoot-scep-certificate-profiles.md)