---
title: "Gerir a transferência de dados entre aplicações iOS | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: utilize este tópico para compreender como pode utilizar a funcionalidade Open In do iOS e as políticas de gestão de aplicações móveis para gerir as transferências de dados entre aplicações."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c09c0b5d76a3035b2af82fe32d4b6c6e35d06baf
ms.openlocfilehash: 4ad494b42313e064a2d5ecc8056e19a522cfe051
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-manage-data-transfer-between-ios-apps"></a>Como gerir a transferência de dados entre aplicações iOS
## <a name="manage-ios-apps"></a>Gerir aplicações iOS
A proteção dos dados da sua empresa inclui garantir que as transferências de ficheiros estão limitadas a aplicações que são geridas por si.  Pode gerir aplicações iOS das seguintes formas:

-   Evite a perda de dados da empresa ao configurar uma política de proteção de aplicações para as aplicações, que serão denominadas aplicações **geridas por políticas**. Veja [todas as aplicações otimizadas para o Intune que pode gerir com a política de proteção de aplicações](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Também pode implementar e gerir aplicações através do **canal MDM**.  o requer que os dispositivos estejam inscritos na solução de MDM. Estas podem ser aplicações **geridas por políticas** ou outras aplicações geridas.

A funcionalidade **Gestão Open in** dos dispositivos iOS pode limitar as transferências de ficheiros entre as aplicações que são implementadas através do **canal MDM**. As restrições da gestão Open in são estipuladas nas definições de configuração e implementadas utilizando a solução MDM.  Quando o utilizador instala a aplicação implementada, são aplicadas as restrições definidas.
##  <a name="using-app-protection-with-ios-apps"></a>Utilizar a proteção de aplicações com aplicações iOS
As políticas proteção de aplicações podem ser utilizadas com a funcionalidade **Gestão Open In** do iOS para proteger os dados da empresa das seguintes formas:

-   **Dispositivos propriedade do empregado não geridos por nenhuma solução MDM:** pode configurar as definições de política de proteção de aplicações para **Permitir que a aplicação transfira dados apenas para aplicações geridas**. Quando o utilizador final abre um ficheiro protegido numa aplicação não gerida por políticas, o ficheiro é ilegível.

-   **Dispositivos geridos pelo Intune:** para dispositivos inscritos no Intune, a transferência de dados entre aplicações com políticas de proteção de aplicações e outras aplicações iOS geridas implementadas através do Intune é permitida automaticamente. Para permitir a transferência de dados entre aplicações com políticas de proteção de aplicações, ative a definição **Permitir que a aplicação transfira dados apenas para aplicações geridas**. Pode utilizar a funcionalidade **Gestão Open in** para controlar a transferência de dados entre as aplicações que são implementadas através do Intune.   

-   **Dispositivos geridos por uma solução MDM de terceiros:** pode restringir a transferência de dados apenas às aplicações geridas utilizando a funcionalidade do iOS **Gestão Open in**.
Para assegurar que as aplicações que implementa através da solução MDM de terceiros também estão associadas às políticas de proteção de aplicações configuradas no Intune, tem de configurar a definição de UPN do utilizador, tal como descrito nas instruções [Configurar definição de UPN do utilizador](#configure-user-upn-setting-for-third-party-emm).  Quando as aplicações são implementadas com a definição de UPN do utilizador, as políticas de proteção de aplicações são aplicadas à aplicação quando o utilizador final inicia sessão com a conta profissional dele.

> [!IMPORTANT]
> A definição de UPN do utilizador só é necessária para as aplicações implementadas em dispositivos geridos por uma solução MDM de terceiros.  Nos dispositivos geridos pelo Intune, esta definição não é necessária.


## <a name="configure-user-upn-setting-for-third-party-emm"></a>Configurar definição de UPN do utilizador para EMM de terceiros
A configuração da definição de UPN do utilizador é **obrigatória** para dispositivos que são geridos por uma solução de EMM de terceiros. O procedimento descrito abaixo é um fluxo geral sobre como configurar a definição de UPN e a experiência de utilizador final resultante:


1.  No [portal do Azure](https://portal.azure.com), [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) para dispositivos iOS. Configure definições de política em conformidade com os requisitos da sua empresa e selecione as aplicações iOS que devem ter esta política.

2.  Implemente as aplicações e o perfil de e-mail que pretende que seja gerido **através da sua solução de MDM de terceiros** ao seguir os passos generalizados abaixo. Esta experiência também é abrangida pelo Exemplo 1.

  1.  Implemente a aplicação com as seguintes definições de configuração de aplicações:

      **chave** = IntuneMAMUPN, **valor** = <username@company.com>

      Exemplo: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

  2.  Implemente a política de gestão Open In ao utilizar o seu fornecedor de MDM de terceiros nos dispositivos inscritos.


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>Exemplo 1: experiência de administrador na consola de MDM de terceiros

1. Aceda à consola de administração do seu fornecedor de MDM de terceiros. Aceda à secção da consola na qual implementa as definições de configuração de aplicações para dispositivos iOS inscritos.

2. Na secção Configuração da Aplicação, introduza a definição seguinte:

  **chave** = IntuneMAMUPN, **valor** = <username@company.com>

  A sintaxe exata do par chave/valor pode diferir com base no seu fornecedor de MDM de terceiros. A tabela abaixo mostra exemplos de fornecedores de MDM de terceiros e os valores exatos que deve introduzir para o par chave/valor.

|Fornecedor de MDM de terceiros| Chave de Configuração | Tipo de Valor | Valor de Configuração|
| ------- | ---- | ---- | ---- |
|VMware AirWatch| IntuneMAMUPN | Cadeia | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | Cadeia | ${userUPN} **ou** ${userEmailAddress} |


### <a name="example-2-end-user-experience"></a>Exemplo 2: experiência de utilizador final

1.  O utilizador final instala a aplicação Microsoft Word no dispositivo.

2.  O utilizador final inicia a aplicação de e-mail nativa gerida para aceder ao e-mail.

3.  O utilizador final tenta abrir o documento a partir da aplicação de e-mail nativa no Microsoft Word.

4.  Quando é iniciada a aplicação Word, é pedido ao utilizador final que inicie sessão com a respetiva conta profissional.  Esta conta profissional que o utilizador final introduz quando solicitado deve corresponder à conta especificada nas definições de configuração da aplicação Microsoft Word.

    > [!NOTE]
    > O utilizador final pode adicionar outras contas pessoais ao Word para fazer o trabalho pessoal dele e não ser afetado pelas políticas de proteção de aplicações quando utilizar a aplicação Word num contexto pessoal.

5.  Quando o início de sessão é efetuado com êxito, as definições da política de proteção de aplicações são aplicadas à aplicação Word.

6.  A transferência de dados será efetuada e o documento será etiquetado com uma identidade da empresa na aplicação. Além disso, os dados são tratados num contexto de trabalho e as definições de política são aplicadas em conformidade.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar a definição de UPN de utilizador para EMM de terceiros

Após configurar a definição de UPN de utilizador, deve validar a capacidade da aplicação iOS de receber e estar em conformidade com a política de proteção de aplicações do Intune.

Por exemplo, a definição de política **Exigir PIN da aplicação** é fácil de testar visualmente num dispositivo. Se a definição de política estiver definida para **Sim**, o utilizador final deve ver um pedido para definir ou introduzir um PIN quando tenta aceder aos dados da empresa.

Em primeiro lugar, [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) à aplicação iOS. Veja [Validar as políticas de proteção de aplicações](validate-app-protection-policies.md) para obter mais informações sobre como testar a política de proteção de aplicações.


### <a name="see-also"></a>Veja também
[O que é uma política de proteção de aplicações do Intune](what-is-app-protection-policy.md)

