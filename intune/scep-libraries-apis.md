---
title: Autoridades de certificado de APIs para carregar parte 3
titlesuffix: Microsoft Intune
description: Adicione ou integre a solução do GitHub do SCEP para outras autoridades de certificado (AC) para emitir certificados SCEP para dispositivos no Microsoft Intune. Esta solução inclui APIs de Java e C# que validam, enviam notificações de êxito e falhas para o Intune, e utilizam fábricas de sockets SSL ao comunicarem com o Intune. Veja uma descrição geral dos passos para testar a sua configuração da AC do SCEP.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 274b512a8fa4b4026d26c8b5e6a704f51a0bef95
ms.sourcegitcommit: 9a4c5b6c2ce511edaeace25426a23f180cb71e15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57565796"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>Utilizar APIs para adicionar outras ACs para o SCEP ao Intune

No Microsoft Intune, pode adicionar autoridades de certificado (AC) de terceiros e defini-las para emitir e validar certificados com o protocolo SCEP (Simple Certificate Enrollment Protocol). O artigo [Add third-party certification authority](certificate-authority-add-scep-overview.md) (Adicionar autoridades de certificação de terceiros) disponibiliza uma descrição geral desta funcionalidade e descreve as tarefas de Administrador no Intune.

Existem também algumas tarefas de programador que utilizam uma biblioteca open source publicada pela Microsoft em GitHub.com. A biblioteca inclui uma API que:

- Valida a palavra-passe do SCEP gerada dinamicamente pelo Intune
- Notifica o Intune relativamente aos certificados criados em dispositivos que submetem pedidos do SCEP

Com esta API, o seu servidor do SCEP de outra empresa é integrado com a solução de gestão do SCEP do Intune para dispositivos geridos por MDM. A biblioteca abstrai aspetos como a autenticação, a localização do serviço e a API de Serviço do Intune de ODATA dos utilizadores.

## <a name="scep-management-solution"></a>Solução de gestão do SCEP

![Como é que o SCEP de outras autoridades de certificação se integra com o Microsoft Intune](./media/scep-certificate-vendor-integration.png)

Com o Intune, os administradores criam perfis do SCEP e atribuem-nos aos dispositivos geridos por MDM. Os perfis do SCEP incluem parâmetros como:

- O URL do servidor do SCEP
- O Certificado de Raiz Fidedigna da Autoridade de Certificação
- Atributos de certificado e mais

Os dispositivos que dão entrada no Intune têm um perfil do SCEP atribuído e são configurados com estes parâmetros. Uma palavra-passe de desafio do SCEP gerada dinamicamente é criada pelo Intune e atribuída ao dispositivo.

Esse desafio contém:

- A palavra-passe de desafio gerada dinamicamente
- Os detalhes sobre os parâmetros esperados no CSR (pedido de assinatura do certificado) que o dispositivo emite para o servidor do SCEP
- O prazo de expiração do desafio

O Intune encripta estas informações, assina o blob encriptado e empacota estes detalhes na palavra-passe de desafio do SCEP.

Os dispositivos que contactam o servidor do SCEP para pedir um certificado dão esta palavra-passe de desafio do SCEP. O servidor do SCEP envia o CSR e a palavra-passe de desafio SCEP encriptada para o Intune para validação.  Esta palavra-passe de desafio e o CRS têm de passar a validação para que o servidor do SCEP emita um certificado para o dispositivo. Quando um desafio do SCEP é validado, ocorrem as seguintes verificações:


- Valida a assinatura do blob encriptado
- Valida que o desafio não expirou
- Valida que o perfil ainda abrange o dispositivo
- Valida que as propriedades do certificado pedidas pelo dispositivo no CSR correspondem aos valores esperados

A solução de gestão do SCEP também inclui relatórios. Um administrador pode obter informações sobre o estado de implementação do perfil do SCEP e sobre os certificados emitidos para os dispositivos.

## <a name="integrate-with-intune"></a>Integrar com o Intune

O código da biblioteca para integrar com o SCEP do Intune está disponível para transferência no [repositório do GitHub Microsoft/Intune-Resource-Access](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).

Integrar a biblioteca nos seus produtos inclui os seguintes passos. Para estes passos, são necessários conhecimentos sobre como trabalhar com repositórios do GitHub e criar soluções e projetos no Visual Studio.

1. Registe-se para receber notificações do repositório
2. Clone ou transfira o repositório
3. Aceda à implementação da biblioteca de que precisa na pasta `\src\CsrValidation` (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
4. Crie a biblioteca ao seguir as instruções no ficheiro README
5. Inclua a biblioteca no projeto que compõe o seu servidor do SCEP
6. Realize as seguintes tarefas no servidor do SCEP:

    - Permita que o administrador configure o [Identificador da Aplicação Azure, Chave da Aplicação Azure e ID de Inquilino](#onboard-scep-server-in-azure) (neste artigo) que a biblioteca utiliza para autenticação. Os administradores devem ter permissão para atualizar a Chave da Aplicação Azure.
    - Identifique pedidos do SCEP que incluam uma palavra-passe do SCEP gerada pelo Intune.
    - Utilize a biblioteca **Validar API de Pedido** para validar palavras-passe do SCEP geradas pelo Intune.
    - Utilize as APIs de notificação da biblioteca para notificar o Intune relativamente aos certificados emitidos para pedidos do SCEP que tenham as palavras-passe do SCEP geradas pelo Intune. Notifique também o Intune relativamente a erros que ocorram ao processar estes pedidos do SCEP.
    - Confirme que o servidor regista informações suficientes para ajudar os administradores a resolverem problemas.

7. Efetue o [teste de integração](#integration-testing) (neste artigo) e aborde todos os problemas existentes
8. Disponibilize orientação por escrito ao cliente que explique:

    - Como o Servidor do SCEP precisa de ser integrado no portal do Azure
    - Como obter o Identificador da Aplicação Azure e a Chave da Aplicação Azure necessários para configurar a biblioteca

### <a name="onboard-scep-server-in-azure"></a>Integrar o servidor do SCEP no Azure

Para ser autenticado no Intune, o servidor do SCEP necessita de um ID da Aplicação Azure, de uma Chave da Aplicação Azure e de um ID de Inquilino. O Servidor do SCEP também precisa de autorização para aceder à API do Intune.

Para obter estes dados, o administrador do servidor do SCEP inicia sessão no portal do Azure, regista a aplicação, dá a permissão da **API do Microsoft Intune/validação do desafio do SCEP** à mesma, cria uma chave para a aplicação e, em seguida, transfere o ID da aplicação, a respetiva chave e o ID de inquilino.

Para orientação sobre como registar uma aplicação e obter os IDs e as chaves, veja [Use portal to create an AAD application and service principal to access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) (Utilizar o portal para criar uma aplicação do Microsoft Azure Active Directory e principal do serviço para aceder a recursos).

### <a name="java-library-api"></a>API da Biblioteca de Java

A biblioteca de Java é implementada como um projeto Maven que restringe as respetivas dependências quando é criada. A API é implementada no espaço de nomes `com.microsoft.intune.scepvalidation` pela classe `IntuneScepServiceClient`.

#### <a name="intunescepserviceclient-class"></a>Classe IntuneScepServiceClient

A classe `IntuneScepServiceClient` inclui os métodos utilizados pelo serviço do SCEP para validar as palavras-passe do SCEP, para notificar o Intune relativamente aos certificados que são criados e para listar todos os erros.

##### <a name="intunescepserviceclient-constructor"></a>Construtor IntuneScepServiceClient

Assinatura:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Descrição:

Instancia e configura um objeto `IntuneScepServiceClient`.

Parâmetros:

    - configProperties – objeto de propriedades que contém informações de configuração do cliente

A configuração tem de incluir as seguintes propriedades:

    - AAD_APP_ID= "o ID da Aplicação Azure obtido durante o processo de integração"
    - AAD_APP_KEY= "a Chave da Aplicação Azure obtida durante o processo de integração"
    - TENANT= "o ID de inquilino obtido durante o processo de integração"
    - PROVIDER_NAME_AND_VERSION= "as informações utilizadas para identificar o seu produto e a respetiva versão"
    
Se a sua solução precisar de um proxy com ou sem autenticação, pode adicionar as seguintes propriedades:

    - PROXY_HOST="O anfitrião onde está alojado o proxy."
    - PROXY_PORT="A porta de escuta do proxy."
    - PROXY_USER="O nome de utilizador a utilizar se o proxy usar autenticação básica."
    - PROXY_PASS="A palavra-passe a utilizar se o proxy usar autenticação básica."

Exceções geradas:

    - IllegalArgumentException – gerada se o construtor for executado sem um objeto de propriedade adequado.

> [!IMPORTANT]
> É melhor instanciar uma instância desta classe e utilizá-la para processar múltiplos pedidos do SCEP. Ao fazê-lo, reduz a sobrecarga, porque cria uma cache das informações dos tokens de autenticação e da localização do serviço.

**Notas de segurança**  
O implementador do servidor do SCEP tem de proteger os dados introduzidos nas propriedades de configuração e guardados contra adulteração e divulgação. É recomendado utilizar ACLs e encriptação adequadas para proteger as informações.

##### <a name="validaterequest-method"></a>Método ValidateRequest

Assinatura:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Descrição:

Valida um pedido de certificado SCEP.

Parâmetros:

    - transactionId – o ID da Transação do SCEP
    - certificateRequest – Base64 do Pedido de Certificado PKCS #10 codificado com DER codificado como uma cadeia

Exceções geradas:

    - IllegalArgumentException – gerada se um parâmetro não válido for utilizado na chamada
    - IntuneScepServiceException – gerada se for detetado que o pedido do certificado não é válido
    - Exception – gerada se ocorrer um erro inesperado

> [!IMPORTANT]
> As exceções geradas por este método devem ser registadas pelo servidor. Tenha em conta que as propriedades `IntuneScepServiceException` têm informações detalhadas sobre a razão da falha da validação do pedido do certificado.

**Notas de segurança**  

  - Se este método gerar uma exceção, o servidor do SCEP**não poderá** emitir um certificado para o cliente.
  - As falhas de validação do pedido de certificado SCEP poderão indicar que existe um problema na infraestrutura do Intune. Também poderão indicar que um atacante está a tentar obter um certificado.

##### <a name="sendsuccessnotification-method"></a>Método SendSuccessNotification

Assinatura:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Descrição:

Notifica o Intune que um certificado é criado como parte do processamento de um pedido de SCEP.

Parâmetros:

    - transactionId – o ID da Transação do SCEP
    - certificateRequest – Base64 do Pedido de Certificado PKCS #10 codificado com DER codificado como uma cadeia
    - certThumprint – thumprint do certificado aprovisionado
    - certSerialNumber – número de série do certificado aprovisionado
    - certExpirationDate – data de expiração do certificado aprovisionado. A cadeia de data/hora deve ter o formato de hora de UTC da Web (YYYY-MM-DDThh:mm:ss.sssTZD) – ISO 8601.
    - certIssuingAuthority – nome da autoridade que emitiu o certificado

Exceções geradas:

    - IllegalArgumentException – gerada se um parâmetro não válido for utilizado na chamada
    - IntuneScepServiceException – gerada se for detetado que o pedido do certificado não é válido
    - Exception – gerada se ocorrer um erro inesperado

> [!IMPORTANT]
> As exceções geradas por este método devem ser registadas pelo servidor. Tenha em conta que as propriedades `IntuneScepServiceException` têm informações detalhadas sobre a razão da falha da validação do pedido do certificado.

**Notas de segurança**

  - Se este método gerar uma exceção, o servidor do SCEP**não poderá** emitir um certificado para o cliente.
  - As falhas de validação do pedido de certificado SCEP poderão indicar que existe um problema na infraestrutura do Intune. Também poderão indicar que um atacante está a tentar obter um certificado.

##### <a name="sendfailurenotification-method"></a>Método SendFailureNotification

Assinatura:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Descrição:

Notifica o Intune de que ocorreu um erro ao processar um pedido do SCEP. Este método não deve ser invocado para exceções geradas pelos métodos desta classe.

Parâmetros:

    - transactionId – o ID da Transação do SCEP
    - certificateRequest – Base64 do Pedido de Certificado PKCS #10 codificado com DER codificado como uma cadeia
    - hResult – código de erro do Win32 que descreve com mais exatidão o erro que foi encontrado. Veja [Win32 Error Codes](https://msdn.microsoft.com/library/cc231199.aspx) (Códigos de Erro do Win32)
    - errorDescription – descrição do erro encontrado

Exceções geradas:

    - IllegalArgumentException – gerada se um parâmetro não válido for utilizado na chamada
    - IntuneScepServiceException – gerada se for detetado que o pedido do certificado não é válido
    - Exception – gerada se ocorrer um erro inesperado

> [!IMPORTANT]
> As exceções geradas por este método devem ser registadas pelo servidor. Tenha em conta que as propriedades `IntuneScepServiceException` têm informações detalhadas sobre a razão da falha da validação do pedido do certificado.

**Notas de segurança**

  - Se este método gerar uma exceção, o servidor do SCEP**não poderá** emitir um certificado para o cliente.
  - As falhas de validação do pedido de certificado SCEP poderão indicar que existe um problema na infraestrutura do Intune. Também poderão indicar que um atacante está a tentar obter um certificado.

##### <a name="setsslsocketfactory-method"></a>Método SetSslSocketFactory

Assinatura:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Descrição:

Utilize este método para informar o cliente de que tem de utilizar a fábrica de sockets SSL especificada (em vez da predefinida) ao comunicar com o Intune.

Parâmetros:

    - factory – a fábrica de sockets SSL que o cliente deve utilizar para pedidos HTTPS

Exceções geradas:

    - IllegalArgumentException – gerada se um parâmetro não válido for utilizado na chamada

> [!NOTE]
> A fábrica de sockets SSL tem de estar definida se tal for obrigatório antes de executar os restantes métodos desta classe.

## <a name="integration-testing"></a>Teste de integração

É obrigatório validar e testar se a sua solução está devidamente integrada com o Intune. Segue-se uma descrição geral dos passos:

1. Configure uma [conta de avaliação do Intune](account-sign-up.md).
2. Integre o [Servidor do SCEP no portal do Azure](#onboard-scep-server-in-azure) (incluído neste artigo).
3. [Configure o Servidor do SCEP](certificates-scep-configure.md) com os IDs e chave criados na integração do seu servidor do SCEP.
4. [Inscreva dispositivos](device-enrollment.md) para testar os cenários na [matriz de teste de cenários](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
5. [Crie um perfil do Certificado de Raiz Fidedigna](certificates-scep-configure.md) para testar a sua Autoridade de Certificação.
6. Crie perfis do SCEP para testar os cenários listados na [matriz de testes de cenários](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
7. [Atribua os perfis](device-profile-assign.md) a utilizadores que inscreveram dispositivos.
8. Aguarde que os dispositivos sincronizem com o Intune. Em alternativa, pode [sincronizar os dispositivos](device-sync.md) manualmente.
9. Confirme que os perfis do Certificado de Raiz Fidedigna e do SCEP [estão implementados nos dispositivos](device-profile-monitor.md).
10. Confirme que o Certificado de Raiz Fidedigna está instalado em todos os dispositivos.
11. Confirme que os Certificados do SCEP de todos os perfis atribuídos estão instalados em todos os dispositivos.
12. Confirme que as propriedades dos certificados instalados correspondem às propriedades definidas no perfil do SCEP.
13. Confirme que os certificados emitidos estão listados na consola do Intune.

## <a name="see-also"></a>Consulte também

- [Descrição geral de como adicionar outra AC](certificate-authority-add-scep-overview.md)
- [Configurar o Intune](setup-steps.md)
- [Inscrição de dispositivos](device-enrollment.md)
- [Configurar perfis de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) (a configuração Servidor/Conector do NDES não é utilizada neste cenário)
