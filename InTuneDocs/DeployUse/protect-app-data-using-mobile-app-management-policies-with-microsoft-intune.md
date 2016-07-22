---
# required metadata

title: Proteger dados de aplicações através de políticas de gestão de aplicações móveis | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteger dados de aplicações através de políticas de gestão de aplicações móveis com o Microsoft Intune

## Como pode proteger dados de aplicações
Os seus empregados utilizam dispositivos móveis para tarefas pessoais e profissionais.  Se, por um lado, quer garantir que os seus empregados são produtivos, por outro, também quer evitar a perda de dados, intencional e não intencional.  Além disso, quer ter a capacidade de proteger os dados da empresa acedidos através de dispositivos, mesmo quando não são geridos por si.

Pode utilizar políticas de gestão de aplicações móveis (MAM) do Intune para ajudar a proteger os dados da sua empresa. Uma vez que as políticas de MAM do Intune podem ser utilizadas independentemente de qualquer solução de gestão de dispositivos móveis (MDM), pode utilizá-las para proteger os dados da sua empresa ao inscrever ou não os dispositivos numa solução de gestão de dispositivos. Ao implementar **políticas ao nível da aplicação**, pode restringir o acesso aos recursos da empresa e manter os dados sob a alçada do seu departamento de TI.

As políticas de MAM suportam aplicações executadas em:

-   **Dispositivos que são geridos e estão inscritos** no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Os dispositivos desta categoria são, normalmente, dispositivos pertencentes à empresa.

  > [!IMPORTANT]
  > Se estiver a utilizar o Intune para gerir os seus dispositivos iOS e Android, pode criar políticas de gestão de aplicações móveis para as aplicações móveis do Office que se ligam aos serviços do Office 365. As políticas de MAM não são suportadas para aplicações que se ligam aos serviços do SharePoint ou do Exchange no local.

-   **Dispositivos que são geridos e estão inscritos numa solução de gestão de dispositivos móveis de terceiros**.   Os dispositivos desta categoria são, normalmente, dispositivos pertencentes à empresa.

  > [!NOTE] As políticas de gestão de aplicações móveis não devem ser utilizadas com soluções de gestão de aplicações móveis ou de contentores seguros de terceiros.

-   **Dispositivos que não são geridos**.  Os dispositivos desta categoria são, normalmente, dispositivos pertencentes aos empregados, que não são geridos ou inscritos no Intune ou em outras soluções MDM.

**Os vantagens importantes da utilização de políticas de MAM são:**

-   Proteger os dados da sua empresa ao nível da aplicação.  Uma vez que a gestão de aplicações móveis não requer a gestão de dispositivos, pode proteger os dados da empresa nos dispositivos geridos e não geridos. A gestão centra-se na identidade do utilizador, o que elimina a necessidade de gestão de dispositivos.

-   A produtividade do utilizador final não é afetada e as políticas não são aplicadas quando a aplicação for utilizada num contexto pessoal.  As políticas são aplicadas apenas num contexto profissional, permitindo-lhe proteger os dados da empresa sem afetar os dados pessoais.

A utilização de MDM com políticas de MAM tem outras vantagens e as empresas podem utilizar as políticas de MAM com ou sem MDM ao mesmo tempo. Por exemplo, um empregado pode utilizar um telemóvel atribuído pela empresa, bem como um tablet pessoal.  Neste caso, o telemóvel da empresa está inscrito na MDM e protegido por políticas de MAM, ao passo que o dispositivo pessoal está protegido apenas por políticas de MAM.

- **A MDM assegura que o dispositivo está protegido**.  Por exemplo, pode exigir um PIN para aceder ao dispositivo ou pode implementar aplicações geridas no mesmo. Também pode implementar aplicações em dispositivos através da sua solução de MDM, para obter maior controlo sobre a gestão de aplicações.

- **As políticas de MAM asseguram que as proteções de camada de aplicação estão implementadas**. Por exemplo, pode exigir um PIN para abrir uma aplicação num contexto profissional, definir se os dados podem ser partilhados entre aplicações ou impedir que os dados de aplicações da empresa sejam guardados numa localização de armazenamento pessoal.


### Atualmente, as políticas de MAM são suportadas em:
-   iOS 8.1 ou posterior

-   Android 4 ou posterior

Os dispositivos Windows não são atualmente suportados.
##  Como é que as políticas de MAM protegem os dados das aplicações

####  Aplicações sem políticas de MAM:

![Imagem que mostra que os dados podem mover-se livremente entre aplicações quando não existem políticas de MAM implementadas](../media/Apps_without_MAM_policies.png)

Quando as aplicações são utilizadas sem restrições, os dados pessoais e da empresa podem confundir-se.  Os dados da empresa podem acabar em localizações como um armazenamento pessoal ou ser transferidos para aplicações fora da sua competência, resultando em perda de dados. As setas no diagrama mostram a movimentação de dados sem restrições entre aplicações (empresariais e pessoais) e para localizações de armazenamento.

### Proteção de dados com políticas de MAM:

![Imagem que mostra como os dados da empresa são protegidos quando são aplicadas políticas de MAM ](../media/Apps_with_mobile_app_policies.png)

Pode utilizar as políticas de MAM para impedir que os dados da empresa sejam guardados no armazenamento local do dispositivo e restringir a movimentação de dados para outras aplicações que não estão protegidas por políticas de MAM. As definições das políticas de MAM incluem:
- Políticas de reposicionamento de dados como **Impedir operações Guardar como**, **Restringir operações cortar, copiar e colar**.
- Aceder a definições de política, como **Exigir PIN simples para o acesso**, **Bloquear execução de aplicações geridas em dispositivos desbloqueados por jailbreak ou rooting**.

### Proteção de dados com políticas de MAM nos dispositivos geridos por uma solução MDM:

![Imagem que mostra como as políticas de MAM funcionam em dispositivos BYOD](../media/MAM_BYOD_November.png)

**Para dispositivos inscritos numa solução MDM**-

A ilustração acima mostra as camadas de proteção que as políticas de MDM e de MAM oferecem em conjunto.

A solução de MDM:

-   Inscreve o dispositivo

-   Implementa as aplicações no dispositivo

-   Fornece gestão e conformidade dos dispositivos contínuas

**As políticas de MAM acrescentam valor ao:**

-   Ajudar a proteger os dados da empresa contra fugas para aplicações e serviços de consumidor

-   Aplicar restrições (guardar como, área de transferência, PIN, etc.) a aplicações móveis

-   Eliminar dados da empresa de aplicações sem as remover do dispositivo


### Proteção de dados com políticas de MAM para dispositivos sem inscrição

![Imagem que mostra como as políticas de MAM funcionam em dispositivos geridos](../media/MAM_ManagedDevices_November.png)

O diagrama acima ilustra como as políticas de proteção de dados funcionam ao nível da aplicação sem MDM.

Nos dispositivos BYOD não inscritos em nenhuma solução de MDM, as políticas de MAM podem ajudar a proteger os dados da empresa ao nível da aplicação.
No entanto, existem algumas limitações a ter em atenção, como:

-   Não pode implementar aplicações no dispositivo.  O utilizador final tem de obter as aplicações na loja.

-   Não pode aprovisionar perfis de certificado nestes dispositivos.

-   Não pode aprovisionar definições de Wi-Fi nem de VPN da empresa nestes dispositivos.


## Várias identidades

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes, profissionais e pessoais, para aceder às mesmas aplicações, enquanto as políticas de MAM são aplicadas quando as aplicações são utilizadas no contexto de trabalho.  

Por exemplo, quando o utilizador final inicia a aplicação OneDrive com a sua conta profissional, não é possível mover os ficheiros para uma localização de armazenamento pessoal. No entanto, quando o utilizador final utiliza o OneDrive com a sua conta pessoal, pode copiar e mover dados do seu OneDrive pessoal, sem restrições.  

Para obter uma explicação detalhada da experiência de utilização de aplicações associadas a políticas de MAM, e de como as aplicações com suporte de várias identidades só permitem a aplicação de políticas de MAM no contexto de trabalho, leia o artigo [Utilizar aplicações com suporte de várias identidades](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md#using-apps-with-multi-identity-support)

Todas as aplicações móveis do Office suportam várias identidades.

##  Passos seguintes
[Configurar políticas de gestão de aplicações móveis](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


