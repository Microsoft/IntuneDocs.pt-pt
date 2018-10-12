---
title: O que são as políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como as políticas de proteção de aplicações do Microsoft Intune ajudam a proteger os dados da sua empresa e evitar perdas de dados.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 64e58ef4d27d2f967eff8c503842345879799168
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232210"
---
# <a name="what-are-app-protection-policies"></a>O que são as políticas de proteção de aplicações?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As políticas de proteção de aplicações do Microsoft Intune ajudam a proteger os dados da sua empresa e evitar perdas de dados.

## <a name="how-you-can-protect-app-data"></a>Como pode proteger dados de aplicações
Os seus empregados utilizam dispositivos móveis para tarefas pessoais e profissionais.  Se, por um lado, quer garantir que os seus funcionários são produtivos, por outro, também quer evitar a perda de dados, intencional e não intencional.  Além disso, quer ter a capacidade de proteger os dados da empresa acedidos através de dispositivos, mesmo quando não são geridos por si.

Pode utilizar as políticas de proteção de aplicações do Intune para ajudar a proteger os dados da sua empresa. Uma vez que as políticas de proteção de aplicações do Intune podem ser utilizadas **independentemente de qualquer solução de gestão de dispositivos móveis (MDM)**, pode utilizá-las para proteger os dados da sua empresa ao inscrever ou não os dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

As políticas de proteção de aplicações podem ser configuradas para aplicações executadas em dispositivos que estão:

- **Inscritos no Microsoft Intune:** os dispositivos desta categoria pertencem, normalmente, à empresa.

- **Inscritos numa solução de gestão de dispositivos móveis (MDM) de terceiros:** os dispositivos desta categoria pertencem, normalmente, à empresa.

  > [!NOTE]
  > As políticas de gestão de aplicações móveis não devem ser utilizadas com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

- **Não inscritos em nenhuma solução de gestão de dispositivos móveis:** os dispositivos desta categoria pertencem, normalmente, aos funcionários e não são geridos ou não estão inscritos no Intune ou noutras soluções de MDM de terceiros.

> [!IMPORTANT]
> Pode criar políticas de gestão de aplicações móveis para as aplicações móveis do Office que se ligam aos serviços do Office 365. Também pode proteger o acesso a caixas de correio do Exchange no local ao criar políticas de proteção de aplicações do Intune para o Outlook para iOS e Android com Autenticação Moderna híbrida. Antes de utilizar esta funcionalidade, certifique-se de que cumpre os [requisitos do Outlook para iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). As políticas de proteção de aplicações não são suportadas para outras aplicações que se ligam aos serviços do SharePoint ou do Exchange no local.

**As vantagens importantes da utilização das políticas de proteção de aplicações**

-   Proteger os dados da sua empresa ao nível da aplicação.  Uma vez que a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

-   A produtividade do utilizador final não é afetada e as políticas não são aplicadas quando a aplicação for utilizada num contexto pessoal.  As políticas são aplicadas apenas num contexto profissional, permitindo-lhe proteger os dados da empresa sem afetar os dados pessoais.

A utilização da MDM com políticas de proteção de aplicações tem outras vantagens e as empresas podem utilizar as políticas de proteção de aplicações com ou sem MDM ao mesmo tempo. Por exemplo, um funcionário pode utilizar um telemóvel atribuído pela empresa, bem como um tablet pessoal.  Neste caso, o telemóvel da empresa está inscrito na MDM e protegido por políticas de proteção de aplicações, ao passo que o dispositivo pessoal está protegido apenas por políticas de proteção de aplicações.

- **A MDM assegura que o dispositivo está protegido**.  Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

- **As políticas de proteção de aplicações asseguram que as proteções da camada de aplicação estão implementadas**. Por exemplo, pode exigir um PIN para abrir uma aplicação num contexto profissional, definir se os dados podem ser partilhados entre aplicações ou impedir que os dados de aplicações da empresa sejam guardados numa localização de armazenamento pessoal.


### <a name="supported-platforms-for-app-protection-polices"></a>Plataformas suportadas das políticas de proteção de aplicações
O suporte para plataformas de políticas de proteção de aplicações do Intune está alinhado com o suporte para plataformas de aplicações do Office. Para obter mais detalhes, veja [Requisitos de Sistema do Office](https://products.office.com/en-US/office-system-requirements).

Os dispositivos Windows não são atualmente suportados. No entanto, quando inscrever dispositivos com o Windows 10 com o Intune, pode utilizar o Windows Information Protection, que oferece uma funcionalidade semelhante. Para mais detalhes, consulte [Protect your enterprise data using Windows Information Protection (WIP) (Proteger os seus dados empresariais com o Windows Information Protection [WIP] – em inglês)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  <a name="how-app-protection-policies-protect-app-data"></a>Como as políticas de proteção de aplicações protegem os dados das aplicações

####  <a name="apps-without-app-protection-policies"></a>Aplicações sem políticas de proteção de aplicações

![Imagem que mostra que os dados podem mover-se livremente entre aplicações quando não existem políticas de proteção de aplicações implementadas](./media/apps-without-protection-policies.png)

Quando as aplicações são utilizadas sem restrições, os dados pessoais e da empresa podem confundir-se.  Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou ser transferidos para aplicações fora da sua competência, resultando em perda de dados. As setas no diagrama mostram a movimentação de dados sem restrições entre aplicações (empresariais e pessoais) e para localizações de armazenamento.


### <a name="data-protection-with-app-protection-policies"></a>Proteção de dados com políticas de proteção de aplicações

![Imagem que mostra como os dados da empresa são protegidos quando são aplicadas políticas de proteção de aplicações ](./media/apps-with-protection-policies.png)


Pode utilizar as políticas de proteção de aplicações para impedir que os dados da empresa sejam guardados no armazenamento local do dispositivo e restringir a movimentação de dados para outras aplicações que não estão protegidas por políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de reposicionamento de dados como **Impedir operações Guardar como**, **Restringir operações cortar, copiar e colar**.
- Aceder a definições de política, como **Exigir PIN simples para o acesso**, **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>Proteção de dados com políticas de proteção de aplicações nos dispositivos geridos por uma solução MDM

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos BYOD](./media/app-protection-policies-with-mdm.png)

**Para dispositivos inscritos numa solução de MDM**-

A ilustração acima mostra as camadas de proteção que as políticas de MDM e de proteção de aplicações oferecem em conjunto.

A solução de MDM:

-   Inscreve o dispositivo

-   Implementa as aplicações no dispositivo

-   Fornece gestão e conformidade dos dispositivos contínuas

**As políticas de proteção de aplicações acrescentam valor ao:**

-   Ajudar a proteger os dados da empresa contra fugas para aplicações e serviços de consumidor

-   Aplicar restrições (guardar como, área de transferência, PIN, etc.) a aplicações cliente

-   Eliminar dados da empresa de aplicações sem as remover do dispositivo


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Proteção de dados com políticas de proteção de aplicações para dispositivos sem inscrição

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos geridos](./media/app-protection-policies-without-mdm.png)

O diagrama acima ilustra como as políticas de proteção de dados funcionam ao nível da aplicação sem MDM.

Nos dispositivos BYOD não inscritos em nenhuma solução de MDM, as políticas de proteção de aplicações podem ajudar a proteger os dados da empresa ao nível da aplicação.
No entanto, existem algumas limitações a ter em atenção, como:

-   Não pode implementar aplicações no dispositivo.  O utilizador final tem de obter as aplicações na loja.

-   Não pode aprovisionar perfis de certificado nestes dispositivos.

-   Não pode aprovisionar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.

## <a name="app-protection-global-policy"></a>Política Global de proteção de aplicações

Se um administrador do OneDrive navegar até **admin.office.com** e selecionar acesso por **Dispositivo**, pode definir os controlos da **Gestão de aplicações móveis** para as aplicações cliente OneDrive e SharePoint. 

As definições, disponibilizadas para a consola de administração do OneDrive, configuram uma política de proteção de aplicações do Intune especial denominada política **Global**. Esta política global é aplicável a todos os utilizadores no seu inquilino e não existe nenhuma forma de controlar a segmentação da política. 

Uma vez ativada, as aplicações OneDrive e SharePoint para iOS e Android serão protegidas com as definições selecionadas por predefinição. Um profissional de TI pode editar esta política na consola do Intune depois de criada, adicionar mais aplicações segmentadas e modificar qualquer definição de política. 

Por predefinição, só pode existir uma política **Global** por inquilino. No entanto, é possível utilizar [Graph APIs do Intune](intune-graph-apis.md) para criar políticas globais adicionais por inquilino, mas não é recomendado. A criação de políticas globais adicionais não é recomendada, uma vez que resolver problemas relacionados com a implementação destas políticas pode tornar-se complicado.

Embora a política **Global** se aplique a todos os utilizadores no seu inquilino, qualquer política de proteção de aplicações padrão do Intune substituirá estas definições.


## <a name="multi-identity"></a>Várias identidades

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes (profissionais e pessoais) para aceder às mesmas aplicações, enquanto as políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho.

Por exemplo, quando um utilizador inicia a aplicação OneDrive com a sua conta profissional, não é possível mover os ficheiros para uma localização de armazenamento pessoal. No entanto, quando utilizam o OneDrive com a sua conta pessoal, podem copiar e mover dados dos seus OneDrive pessoais, sem restrições.

- Saiba mais sobre as aplicações que suportam [MAM e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

##  <a name="next-steps"></a>Próximos passos

[Como criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Consulte também
As aplicações de terceiros como a aplicação móvel do Salesforce funcionam com o Intune de formas específicas para proteger os dados empresariais. Para obter mais informações sobre como a aplicação Salesforce em particular funciona com o Intune (incluindo configurações de aplicações de MDM), veja [Aplicação Salesforce e Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
