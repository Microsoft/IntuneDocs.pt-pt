---
title: "Proteger dados das aplicações através de políticas de MAM | Documentos da Microsoft"
description: "Este tópico explica de que forma é que as políticas de gestão de aplicações móveis podem ajudar a proteger os dados empresariais, a evitar a perda de dados e a manter as informações pessoais e de trabalho separadas."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 33febef8787887401960592d95356347f6917681
ms.openlocfilehash: 9959e9f757e83c7aa4274b7e7b9df949fff022cc
ms.contentlocale: pt-pt
ms.lasthandoff: 05/04/2017


---

# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>Proteger os dados da aplicação através de políticas de proteção de aplicações com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>Como pode proteger dados de aplicações
Os seus funcionários utilizam dispositivos móveis para tarefas pessoais e profissionais. Se, por um lado, quer garantir que os seus funcionários são produtivos, por outro, também quer evitar a perda de dados, intencional e acidental.  Além disso, pretende ser capaz de proteger os dados da empresa aos quais os seus funcionários acedem com dispositivos que não gere.

Pode utilizar as políticas de proteção de aplicações do Intune para ajudar a proteger os dados da sua empresa. Uma vez que as políticas de proteção de aplicações do Intune podem ser utilizadas **independentemente de qualquer solução de gestão de dispositivos móveis (MDM)**, pode utilizar as políticas de MAM para proteger os dados da sua empresa ao inscrever ou não os dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

Pode configurar as políticas de proteção de aplicações para aplicações executadas em dispositivos que estão:

-   **Inscritos no Microsoft Intune:** os dispositivos desta categoria pertencem, normalmente, à empresa.

-   **Inscritos numa solução de MDM de terceiros:** os dispositivos desta categoria pertencem, normalmente, à empresa.

      > [!NOTE]
      > Não recomendamos a utilização de políticas de proteção de aplicações com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

-   **Não inscritos em nenhuma solução de MDM:** os dispositivos desta categoria pertencem, normalmente, aos funcionários e não são geridos ou não estão inscritos no Intune ou noutras soluções de MDM de terceiros.

> [!IMPORTANT]
> Pode criar políticas de proteção de aplicações para as aplicações móveis do Office que estão ligados aos serviços do Office 365. As políticas de proteção de aplicações não são suportadas para aplicações que se ligam aos serviços Exchange no local, ao Skype para Empresas nem ao SharePoint.

## <a name="benefits-of-using-app-protection-policies"></a>Vantagens da utilização de políticas de proteção de aplicações

-   **Ajudam a proteger os dados da sua empresa ao nível da aplicação.** Como a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

-   **A produtividade do utilizador não é afetada e as políticas não são aplicadas quando a aplicação for utilizada num contexto pessoal.** As políticas são aplicadas apenas num contexto profissional, o que lhe permite proteger os dados da empresa sem afetar os dados pessoais.

A utilização de MDM com políticas de proteção de aplicações tem outras vantagens e as empresas podem utilizar as políticas de MAM com e sem MDM em simultâneo. Por exemplo, um funcionário poderá utilizar um telemóvel atribuído pela empresa, bem como um tablet pessoal. Neste caso, o telemóvel da empresa está inscrito na MDM e protegido por políticas de proteção de aplicações, ao passo que o dispositivo pessoal está protegido apenas por políticas de proteção de aplicações.

- **A MDM assegura que o dispositivo está protegido.** Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

- **As políticas de proteção de aplicações asseguram que as proteções de camada de aplicação estão implementadas.** Por exemplo, pode ter uma política que exige um PIN para abrir uma aplicação num contexto profissional, impedir que os dados sejam partilhados entre aplicações e impedir que os dados de aplicações da empresa sejam guardados numa localização de armazenamento pessoal.

## <a name="devices-that-support-mam"></a>Dispositivos que suportam MAM
Atualmente, as políticas de proteção de aplicações são suportadas em:
-   iOS 8.1 ou posterior
-   Android 4 ou posterior

>[!NOTE]
>Os dispositivos Windows não são suportados pelo MAM sem um cenário de inscrição. No entanto, quando inscrever dispositivos Windows 10 com o Intune, pode utilizar o Windows Information Protection, que oferece uma funcionalidade semelhante. Para mais detalhes, consulte [Protect your enterprise data using Windows Information Protection (WIP) (Proteger os seus dados empresariais com o Windows Information Protection [WIP] – em inglês)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


##  <a name="how-app-protection-policies-protect-app-data"></a>Como as políticas de proteção de aplicações protegem os dados das aplicações

###  <a name="apps-without-app-protection-policies"></a>Aplicações sem políticas de proteção de aplicações

![Imagem que mostra como os dados podem mover-se livremente entre aplicações quando não existem políticas de proteção de aplicações implementadas](../media/Apps_without_MAM_policies.png)

Quando utiliza as aplicações sem restrições, os dados pessoais e da empresa podem confundir-se. Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou podem ser transferidos para aplicações fora da sua competência, resultando em perda de dados. As setas no diagrama mostram a movimentação de dados sem restrições entre aplicações (empresariais e pessoais) e para localizações de armazenamento.

### <a name="data-protection-with-app-protection-policies"></a>Proteção de dados com políticas de proteção de aplicações

![Imagem que mostra como os dados da empresa são protegidos quando são aplicadas políticas de proteção de aplicações](../media/Apps_with_mobile_app_policies.png)

Pode utilizar as políticas de proteção de aplicações para impedir que os dados da empresa sejam guardados no armazenamento local do dispositivo e restringir a movimentação de dados para outras aplicações que não estão protegidas por políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de reposicionamento de dados como **Impedir operações Guardar como** e **Restringir operações cortar, copiar e colar**.
- Aceder a definições de política, como **Exigir PIN simples para o acesso** e **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>Proteção de dados com políticas de proteção de aplicações nos dispositivos geridos por uma solução de MDM

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos BYOD (Bring Your Own Devices)](../media/MAM_BYOD_November.png)

**Para dispositivos inscritos numa solução de MDM**: o diagrama anterior mostra as camadas de proteção que as políticas de MDM e as políticas de proteção de aplicações oferecem em conjunto.

A solução de MDM:

-   Inscreve o dispositivo.

-   Implementa aplicações no dispositivo.

-   Fornece gestão e conformidade dos dispositivos contínuas.

**As políticas de proteção de aplicações têm mais vantagens porque:**

-   Ajudam a proteger os dados da empresa contra fugas para aplicações e serviços de consumidor.

-   Aplicam restrições (guardar como, área de transferência, PIN, etc.) a aplicações móveis.

-   Eliminam dados da empresa de aplicações sem as remover do dispositivo.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Proteção de dados com políticas de proteção de aplicações para dispositivos sem inscrição

![Imagem que mostra como as políticas de proteção de aplicações funcionam em dispositivos geridos](../media/MAM_ManagedDevices_November.png)

O diagrama anterior ilustra como as políticas de proteção de dados funcionam ao nível da aplicação sem MDM.

Para dispositivos BYOD que não estejam inscritos em nenhuma solução de MDM, as políticas de proteção de aplicações podem ajudar a proteger os dados da empresa ao nível da aplicação.

No entanto, existem algumas limitações a ter em atenção:

-   Não pode implementar aplicações no dispositivo. O utilizador tem de obter as aplicações na loja.

-   Não pode aprovisionar perfis de certificado nestes dispositivos.

-   Não pode configurar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.


## <a name="multi-identity"></a>Várias identidades

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes (profissionais e pessoais) para aceder às mesmas aplicações, enquanto as políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho.  

Por exemplo, quando um utilizador inicia a aplicação OneDrive com a sua conta profissional, não é possível mover os ficheiros para uma localização de armazenamento pessoal. No entanto, quando utilizam o OneDrive com a sua conta pessoal, podem copiar e mover dados dos seus OneDrive pessoais, sem restrições.  

- Saiba mais sobre as aplicações que suportam [MAM e múltiplas identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

##  <a name="next-steps"></a>Próximos passos
- [Preparar-se para configurar políticas de proteção de aplicações](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Criar e implementar políticas de proteção de aplicações com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

