---
title: "Gerir a transferência de dados entre aplicações iOS | Microsoft Intune"
description: "Utilize este tópico para compreender como pode utilizar a funcionalidade Open In do iOS e as políticas de gestão de aplicações móveis para gerir as transferências de dados entre aplicações."
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: b95b721ba2d26f3d8f621a7ca5a4968bc86c1daf


---

# Gerir a transferência de dados entre aplicações iOS com o Microsoft Intune
## Gerir aplicações iOS
A proteção dos dados da sua empresa inclui garantir que as transferências de ficheiros estão limitadas a aplicações que são geridas por si.  Pode gerir aplicações iOS das seguintes formas:

-   Evite a perda de dados da empresa ao configurar uma política de MAM para as aplicações, que serão denominadas aplicações **geridas por políticas**.

-   Também pode implementar e gerir aplicações através do **canal MDM**.  o requer que os dispositivos estejam inscritos na solução de MDM. Estas podem ser aplicações **geridas por políticas** ou outras aplicações geridas.

A funcionalidade **Gestão Open in** dos dispositivos iOS pode limitar as transferências de ficheiros entre as aplicações que são implementadas através do **canal MDM**. As restrições da gestão Open in são estipuladas nas definições de configuração e implementadas utilizando a solução MDM.  Quando o utilizador instala a aplicação implementada, são aplicadas as restrições definidas.
##  Utilizar a MAM com aplicações iOS
As políticas de gestão de aplicações móveis (MAM) podem ser utilizadas com a funcionalidade **Gestão Open in** para proteger os dados da empresa das seguintes formas:

-   **Dispositivos propriedade do empregado não geridos por nenhuma solução MDM:** pode configurar as definições de política de MAM para **Permitir à aplicação transferir dados apenas para aplicações geridas**. Quando o utilizador final abre um ficheiro protegido numa aplicação não gerida por políticas, o ficheiro é ilegível.

-   **Dispositivos geridos pelo Intune:** para dispositivos inscritos no Intune, a transferência de dados entre aplicações com políticas de MAM e outras aplicações iOS geridas implementadas através do Intune é permitida automaticamente. Para permitir a transferência de dados entre aplicações com políticas de MAM, ative a definição **Permitir que a aplicação transfira dados apenas para aplicações geridas**. Pode utilizar a funcionalidade **Gestão Open in** para controlar a transferência de dados entre as aplicações que são implementadas através do Intune.   

-   **Dispositivos geridos por uma solução MDM de terceiros:** pode restringir a transferência de dados apenas às aplicações geridas utilizando a funcionalidade do iOS **Gestão Open in**.
Para assegurar que as aplicações que implementa através da solução MDM de terceiros também estão associadas às políticas de MAM configuradas no Intune, tem de configurar a definição de UPN do utilizador, tal como descrito nas instruções [Configurar definição de UPN do utilizador](#configure-user-upn-setting).  Quando as aplicações são implementadas com a definição de UPN do utilizador, as políticas de MAM são aplicadas à aplicação quando o utilizador final inicia sessão com a respetiva conta profissional.

> [!IMPORTANT]
> A definição de UPN do utilizador só é necessária para as aplicações implementadas em dispositivos geridos por uma solução MDM de terceiros.  Nos dispositivos geridos pelo Intune, esta definição não é necessária.

## Configurar definição de UPN do utilizador
Esta configuração é necessária para os dispositivos geridos por uma solução MDM de terceiros. O procedimento descrito abaixo é um fluxo geral sobre como implementar a definição de UPN e a experiência de utilizador final resultante:


1.  No portal do Azure, [configure uma política de gestão de aplicações móveis](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para a plataforma iOS. Configure definições de política em conformidade com os requisitos da sua empresa e selecione as aplicações que devem ter esta política.

2.  Implemente as aplicações e o perfil de e-mail que pretende que sejam geridos **através da solução MDM de terceiros** utilizando a definição descrita nos passos 3 e 4.

3.  Implemente a aplicação com as seguintes definições de configuração de aplicação: key=IntuneMAMUPN, Value=<nomedeutilizador@empresa.com> [exemplo: "IntuneMAMUPN", "jondoe@microsoft.com"]

4.  Implemente a política de gestão Open In nos dispositivos inscritos.

### Exemplo de experiência de utilizador final

1.  O utilizador final instala a aplicação Microsoft Word no dispositivo.

2.  O utilizador final inicia a aplicação de e-mail nativa gerida para aceder ao e-mail.

3.  O utilizador final tenta abrir o documento a partir da aplicação de e-mail nativa no Microsoft Word.

4.  Quando é iniciada a aplicação Word, é pedido ao utilizador final que inicie sessão com a respetiva conta profissional.  Esta conta profissional que o utilizador final introduz quando solicitado deve corresponder à conta especificada nas definições de configuração da aplicação Microsoft Word.

    > [!NOTE]
    > O utilizador final pode adicionar outras contas pessoais ao Word para fazer o seu trabalho pessoal e não ser afetado pelas políticas de MAM quando utilizar a aplicação Word num contexto pessoal.

5.  Quando o início de sessão é bem-sucedido, as definições da política de aplicação são aplicadas à aplicação Word.

6.  Agora, a transferência de dados é concluída com êxito e o documento é marcado como identidade empresarial na aplicação. Além disso, os dados são tratados num contexto de trabalho e as definições de política são aplicadas em conformidade.

### Consulte também
[Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


