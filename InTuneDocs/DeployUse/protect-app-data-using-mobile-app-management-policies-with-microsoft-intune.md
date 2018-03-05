<<<<<<< HEAD
---
title: "Proteger dados das aplicações através de políticas de MAM | Microsoft Intune"
description: "Este tópico explica de que forma é que as políticas de gestão de aplicações móveis podem ajudar a proteger os dados empresariais, a evitar perda de dados e a manter as informações pessoais e de trabalho separadas."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: e751619f6d65e10099d1f8ff5a2342185181af69

||||||| merged common ancestors
---
title: "Proteger dados das aplicações através de políticas de MAM | Microsoft Intune"
description: "Este tópico explica de que forma é que as políticas de gestão de aplicações móveis podem ajudar a proteger os dados empresariais, a evitar perda de dados e a manter as informações pessoais e de trabalho separadas."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: e751619f6d65e10099d1f8ff5a2342185181af69

=======
---
title: "Proteger dados das aplicações através de políticas de MAM | Microsoft Intune"
description: "Este tópico explica de que forma é que as políticas de gestão de aplicações móveis podem ajudar a proteger os dados empresariais, a evitar perda de dados e a manter as informações pessoais e de trabalho separadas."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 027e7e56e6f7d3a604336e0465f688af514c69e6
ms.openlocfilehash: fc484be99d0956e707f96c0c285b2750754f746c

>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

---
<<<<<<< HEAD

# Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune
||||||| merged common ancestors

# Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune
=======

# <a name="protect-app-data-using-mobile-app-management-policies-with-microsoft-intune"></a>Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune
>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

## <a name="how-you-can-protect-app-data"></a>Como pode proteger dados de aplicações
Os seus funcionários utilizam dispositivos móveis para tarefas pessoais e profissionais.  Se, por um lado, quer garantir que os seus funcionários são produtivos, por outro, também quer evitar a perda de dados, intencional e não intencional.  Além disso, quer ter a capacidade de proteger os dados da empresa acedidos através de dispositivos, mesmo quando não são geridos por si.

Pode utilizar políticas de gestão de aplicações móveis (MAM) do Intune para ajudar a proteger os dados da sua empresa. Uma vez que as políticas de MAM do Intune podem ser utilizadas **independentemente de qualquer solução de gestão de dispositivos móveis (MDM)**, pode utilizá-las para proteger os dados da sua empresa ao inscrever ou não os dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

As políticas de MAM podem ser configuradas para aplicações executadas em dispositivos que estão:

- **Inscritos no Microsoft Intune:** os dispositivos desta categoria pertencem, normalmente, à empresa.

-   **Inscritos numa solução de gestão de dispositivos móveis (MDM) de terceiros:** os dispositivos desta categoria pertencem, normalmente, à empresa.

  > [!NOTE]
  > As políticas de gestão de aplicações móveis não devem ser utilizadas com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

-   **Não inscritos em nenhuma solução de gestão de dispositivos móveis:** os dispositivos desta categoria pertencem, normalmente, aos funcionários e não são geridos ou não estão inscritos no Intune ou noutras soluções de MDM de terceiros.

> [!IMPORTANT]
> Pode criar políticas de gestão de aplicações móveis para as aplicações móveis do Office que se ligam aos serviços do Office 365. As políticas de MAM não são suportadas para aplicações que se ligam aos serviços Exchange no local, ao Skype para Empresas nem ao SharePoint.

**As vantagens importantes da utilização de políticas de MAM são**

-   Proteger os dados da sua empresa ao nível da aplicação.  Uma vez que a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

-   A produtividade do utilizador final não é afetada e as políticas não são aplicadas quando a aplicação for utilizada num contexto pessoal.  As políticas são aplicadas apenas num contexto profissional, permitindo-lhe proteger os dados da empresa sem afetar os dados pessoais.

A utilização de MDM com políticas de MAM tem outras vantagens e as empresas podem utilizar as políticas de MAM com ou sem MDM ao mesmo tempo. Por exemplo, um funcionário pode utilizar um telemóvel atribuído pela empresa, bem como um tablet pessoal.  Neste caso, o telemóvel da empresa está inscrito na MDM e protegido por políticas de MAM, ao passo que o dispositivo pessoal está protegido apenas por políticas de MAM.

- **A MDM assegura que o dispositivo está protegido**.  Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

- **As políticas de MAM asseguram que as proteções de camada de aplicação estão implementadas**. Por exemplo, pode exigir um PIN para abrir uma aplicação num contexto profissional, definir se os dados podem ser partilhados entre aplicações ou impedir que os dados de aplicações da empresa sejam guardados numa localização de armazenamento pessoal.


### <a name="mam-polices-are-currently-supported-on"></a>Atualmente, as políticas de MAM são suportadas em:
-   iOS 8.1 ou posterior

-   Android 4 ou posterior

Os dispositivos Windows não são atualmente suportados.
##  <a name="how-mam-policies-protect-app-data"></a>Como é que as políticas de MAM protegem os dados das aplicações

####  <a name="apps-without-mam-policies"></a>Aplicações sem políticas de MAM:

![Imagem que mostra que os dados podem mover-se livremente entre aplicações quando não existem políticas de MAM implementadas](../media/Apps_without_MAM_policies.png)

Quando as aplicações são utilizadas sem restrições, os dados pessoais e da empresa podem confundir-se.  Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou ser transferidos para aplicações fora da sua competência, resultando em perda de dados. As setas no diagrama mostram a movimentação de dados sem restrições entre aplicações (empresariais e pessoais) e para localizações de armazenamento.

### <a name="data-protection-with-mam-policies"></a>Proteção de dados com políticas de MAM:

![Imagem que mostra como os dados da empresa são protegidos quando são aplicadas políticas de MAM ](../media/Apps_with_mobile_app_policies.png)

Pode utilizar as políticas de MAM para impedir que os dados da empresa sejam guardados no armazenamento local do dispositivo e restringir a movimentação de dados para outras aplicações que não estão protegidas por políticas de MAM. As definições das políticas de MAM incluem:
- Políticas de reposicionamento de dados como **Impedir operações Guardar como**, **Restringir operações cortar, copiar e colar**.
- Aceder a definições de política, como **Exigir PIN simples para o acesso**, **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

### <a name="data-protection-with-mam-policies-on-devices-managed-by-a-mdm-solution"></a>Proteção de dados com políticas de MAM nos dispositivos geridos por uma solução MDM:

![Imagem que mostra como as políticas de MAM funcionam em dispositivos BYOD](../media/MAM_BYOD_November.png)

**Para dispositivos inscritos numa solução de MDM**-

A ilustração acima mostra as camadas de proteção que as políticas de MDM e de MAM oferecem em conjunto.

A solução de MDM:

-   Inscreve o dispositivo

-   Implementa as aplicações no dispositivo

-   Fornece gestão e conformidade dos dispositivos contínuas

**As políticas de MAM acrescentam valor ao:**

-   Ajudar a proteger os dados da empresa contra fugas para aplicações e serviços de consumidor

-   Aplicar restrições (guardar como, área de transferência, PIN, etc.) a aplicações móveis

-   Eliminar dados da empresa de aplicações sem as remover do dispositivo


### <a name="data-protection-with-mam-policies-for-devices-without-enrollment"></a>Proteção de dados com políticas de MAM para dispositivos sem inscrição

![Imagem que mostra como as políticas de MAM funcionam em dispositivos geridos](../media/MAM_ManagedDevices_November.png)

O diagrama acima ilustra como as políticas de proteção de dados funcionam ao nível da aplicação sem MDM.

Nos dispositivos BYOD não inscritos em nenhuma solução de MDM, as políticas de MAM podem ajudar a proteger os dados da empresa ao nível da aplicação.
No entanto, existem algumas limitações a ter em atenção, como:

-   Não pode implementar aplicações no dispositivo.  O utilizador final tem de obter as aplicações na loja.

-   Não pode aprovisionar perfis de certificado nestes dispositivos.

-   Não pode aprovisionar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.


## <a name="multi-identity"></a>Várias identidades

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes, profissionais e pessoais, para aceder às mesmas aplicações, enquanto as políticas de MAM são aplicadas quando as aplicações são utilizadas no contexto de trabalho.  

Por exemplo, quando o utilizador final inicia a aplicação OneDrive com a sua conta profissional, não é possível mover os ficheiros para uma localização de armazenamento pessoal. No entanto, quando o utilizador final utiliza o OneDrive com a sua conta pessoal, pode copiar e mover dados do seu OneDrive pessoal, sem restrições.  

Todas as aplicações móveis do Office suportam várias identidades.

##  <a name="next-steps"></a>Passos seguintes
[Configurar políticas de gestão de aplicações móveis](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Nov16_HO2-->


