---
title: O que são as políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como as políticas de proteção de aplicações do Microsoft Intune ajudam a proteger os dados da sua empresa e evitar perdas de dados.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45e9f50881ff7da0554a4731712441b5fedb01d8
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292251"
---
# <a name="what-are-app-protection-policies"></a>O que são as políticas de proteção de aplicações?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As políticas de proteção de aplicações do Microsoft Intune ajudam a proteger os dados da sua empresa e evitar perdas de dados.

## <a name="how-you-can-protect-app-data"></a>Como pode proteger dados de aplicações
Os seus funcionários utilizam dispositivos móveis para tarefas pessoais e profissionais. Se, por um lado, quer garantir que os seus funcionários são produtivos, por outro, quer evitar a perda de dados, intencional e não intencional. Também irá querer proteger os dados da empresa que são acedidos a partir de dispositivos que não são geridos por si.

Pode utilizar as políticas de proteção de aplicações do Intune **independentemente de qualquer solução de gestão de dispositivos móveis (MDM)**. Esta independência ajuda-o a proteger dados da sua empresa com ou sem inscrição de dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

As políticas de proteção de aplicações podem ser configuradas para aplicações executadas em dispositivos que estão:

- **Inscritos no Microsoft Intune:** Estes dispositivos são, normalmente, pertencentes à empresa.

- **Inscritos numa solução de gestão (MDM) de terceiros de dispositivos móveis:** Estes dispositivos são, normalmente, pertencentes à empresa.

  > [!NOTE]
  > As políticas de gestão de aplicações móveis não devem ser utilizadas com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

- **Não inscritos em nenhuma solução de gestão de dispositivos móveis:** Os dispositivos são, normalmente, os dispositivos que não são geridos ou inscritos no Intune ou noutras soluções MDM de funcionários.

> [!IMPORTANT]
> Pode criar políticas de gestão de aplicações móveis para as aplicações móveis do Office que se ligam aos serviços do Office 365. Também pode proteger o acesso a caixas de correio do Exchange no local ao criar políticas de proteção de aplicações do Intune para o Outlook para iOS e Android com Autenticação Moderna híbrida. Antes de utilizar esta funcionalidade, certifique-se de que cumpre os [requisitos do Outlook para iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). As políticas de proteção de aplicações não são suportadas para outras aplicações que se ligam aos serviços do SharePoint ou do Exchange no local.

**As vantagens importantes da utilização de políticas de proteção de aplicação são**:

-   Proteger os dados da sua empresa ao nível da aplicação. Como a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

-   A produtividade do utilizador final não é afetada e as políticas não são aplicadas quando a aplicação for utilizada num contexto pessoal. As políticas são aplicadas apenas num contexto profissional, o que lhe permite proteger os dados da empresa sem afetar os dados pessoais.

A utilização da MDM com políticas de proteção de aplicações tem outras vantagens e as empresas podem utilizar as políticas de proteção de aplicações com ou sem MDM ao mesmo tempo. Por exemplo, considere um funcionário que utiliza os um telemóvel atribuído pela empresa e o seu próprio tablet pessoal. O telemóvel da empresa está inscrito na MDM e protegido por políticas de proteção de aplicações, ao passo que o dispositivo pessoal está protegido apenas por políticas de proteção de aplicações.

- **A MDM assegura que o dispositivo está protegido**. Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

- **As políticas de proteção de aplicações asseguram que as proteções da camada de aplicação estão implementadas**. Por exemplo, pode:
  - Exigir um PIN para abrir uma aplicação num contexto de trabalho 
  - Controlar a partilha de dados entre aplicações 
  - Impedir a gravação de dados empresariais da aplicação numa localização de armazenamento pessoal


### <a name="supported-platforms-for-app-protection-policies"></a>Plataformas suportadas das políticas de proteção de aplicações
Suporte de plataformas de políticas do Intune app protection se alinha com suporte de plataformas de aplicações móveis do Office para dispositivos Android e iOS. Para obter detalhes, veja a secção **Aplicações móveis** de [Requisitos de Sistema do Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> O Portal da empresa do Intune é necessário no dispositivo para receber políticas de proteção de aplicações do Android. Para obter mais informações, consulte a [requisitos de aplicações de acesso do Portal da empresa do Intune](end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Como as políticas de proteção de aplicações protegem os dados das aplicações

#### <a name="apps-without-app-protection-policies"></a>Aplicações sem políticas de proteção de aplicações

![Imagem conceptual para o movimento de dados entre aplicações sem políticas no local](./media/apps-without-protection-policies.png)

Quando as aplicações são utilizadas sem restrições, os dados pessoais e da empresa podem confundir-se. Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou ser transferidos para aplicações fora da sua competência e que resulta em perda de dados. As setas no diagrama anterior mostram o movimento de dados sem restrições entre aplicações (empresariais e pessoais) e para localizações de armazenamento.


### <a name="data-protection-with-app-protection-policies"></a>Proteção de dados com políticas de proteção de aplicações

![Imagem conceptual, que mostra os dados da empresa que está a ser protegidos por políticas](./media/apps-with-protection-policies.png)


Pode utilizar Políticas de proteção de aplicações para impedir que os dados da empresa sejam guardados no armazenamento local do dispositivo. Também pode restringir o movimento de dados para outras aplicações que não estão protegidas pelas Políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de reposicionamento de dados como **Impedir operações Guardar como** e **Restringir operações cortar, copiar e colar**.
- Definições de política de acesso, como **Exigir PIN simples para o acesso** e **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>Proteção de dados com políticas de proteção de aplicações nos dispositivos geridos por uma solução Gestão de Dispositivos Móveis

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos BYOD](./media/app-protection-policies-with-mdm.png)

**Para dispositivos inscritos numa solução de MDM**-

A ilustração anterior mostra as camadas de proteção que as políticas de MDM e de proteção de aplicações oferecem em conjunto.

A solução de MDM:

-   Inscreve o dispositivo

-   Implementa as aplicações no dispositivo

-   Fornece gestão e conformidade dos dispositivos contínuas

**As políticas de proteção de aplicações acrescentam valor ao:**

-   Ajudar a proteger os dados da empresa contra fugas para aplicações e serviços de consumidor

-   Aplicar restrições como *guardar como*, *área de transferência* ou *PIN* a aplicações cliente

-   Eliminar dados da empresa de aplicações sem as remover do dispositivo


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Proteção de dados com políticas de proteção de aplicações para dispositivos sem inscrição

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos geridos](./media/app-protection-policies-without-mdm.png)

O diagrama anterior ilustra como as políticas de proteção de dados funcionam ao nível da aplicação sem MDM.

Nos dispositivos BYOD não inscritos em nenhuma solução de MDM, as políticas de proteção de aplicações podem ajudar a proteger os dados da empresa ao nível da aplicação.
No entanto, existem algumas limitações a ter em atenção, como:

-   Não pode implementar aplicações no dispositivo. O utilizador final tem de obter as aplicações na loja.

-   Não pode aprovisionar perfis de certificado nestes dispositivos.

-   Não pode aprovisionar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.

## <a name="app-protection-global-policy"></a>Política Global de proteção de aplicações

Se um administrador do OneDrive navegar até **admin.office.com** e selecionar acesso por **Dispositivo**, poderá definir os controlos da **Gestão de aplicações móveis** para as aplicações cliente OneDrive e SharePoint. 

As definições, disponibilizadas para a consola de administração do OneDrive, configuram uma política de proteção de aplicações do Intune especial denominada política **Global**. Esta política global aplica-se a todos os utilizadores no seu inquilino e não existe nenhuma forma de controlar a segmentação da política. 

Uma vez ativada, as aplicações OneDrive e SharePoint para iOS e Android estão protegidas com as definições selecionadas por predefinição. Um profissional de TI pode editar esta política na consola do Intune para adicionar mais aplicações segmentadas e para modificar qualquer definição de política. 

Por predefinição, só pode existir uma política **Global** por inquilino. No entanto, pode utilizar [Graph APIs do Intune](intune-graph-apis.md) para criar políticas globais adicionais por inquilino, mas não é recomendado. A criação de políticas globais adicionais não é recomendada, uma vez que resolver problemas relacionados com a implementação destas políticas pode tornar-se complicado.

Embora a política **Global** se aplique a todos os utilizadores no seu inquilino, qualquer política de proteção de aplicações padrão do Intune substituirá estas definições.


## <a name="multi-identity"></a>Várias identidades

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes (profissionais e pessoais) para aceder às mesmas aplicações, enquanto as políticas de proteção de aplicações aplicam-se apenas quando as aplicações são utilizadas no contexto de trabalho.

Para um exemplo de contexto pessoa, considere um utilizador que inicia um novo documento do Word, esse é considerado um contexto pessoal para que não são aplicadas políticas de proteção de aplicações do Intune. Depois do documento é salvo na conta empresarial do OneDrive, em seguida, ele será considerado contexto empresarial e as políticas de proteção de aplicações do Intune serão aplicadas.

Para obter um exemplo de contexto de trabalho, considere um utilizador que inicia a aplicação OneDrive com sua conta profissional. No contexto de trabalho, não pode mover ficheiros para uma localização de armazenamento pessoal. Posteriormente, quando utiliza o OneDrive com a sua conta pessoal, pode copiar e mover dados dos seus OneDrive pessoais, sem restrições.

- Saiba mais sobre as aplicações que suportam [MAM e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

## <a name="next-steps"></a>Passos Seguintes

[Como criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Consulte também
As aplicações de terceiros como a aplicação móvel do Salesforce funcionam com o Intune de formas específicas para proteger os dados empresariais. Para obter mais informações sobre como a aplicação Salesforce em particular funciona com o Intune (incluindo configurações de aplicações de MDM), veja [Aplicação Salesforce e Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
