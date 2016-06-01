---
# required metadata

title: O seu computador já está inscrito | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d3a40f5-99e9-48dc-9706-f7a3a23e5704

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# O seu computador já está inscrito
Está a ver esta página porque executou a Configuração do software de cliente do Intune. No entanto, o software já está instalado no seu computador e não é possível continuar a Configuração.

Esta situação poderá ter acontecido porque:

-   O software de cliente foi instalado anteriormente e a Configuração foi executada novamente.

-   A Configuração foi executada no computador depois de o administrador de TI ter extinguido o seu dispositivo do Intune. Depois de o seu dispositivo ser extinguido, poderá demorar várias horas para que o software de cliente seja removido do seu computador.

-   A Configuração detetou uma falha na instalação ou remoção do software de cliente.

## O que é que a Configuração instala no seu computador
A Configuração instala o cliente do Intune. Depois de a Configuração ser concluída, o software de cliente continua em execução em segundo plano onde configura o seu computador para ser utilizado com o Intune. Este processo pode demorar algum tempo para ser concluído e inclui:

-   A inscrição do seu computador no Intune

-   O envio do inventário sobre o hardware do computador e o software instalado

-   A configuração da política do Intune, incluindo a instalação do Endpoint Protection (se estiver configurado)

-   Instalar o Intune Center

Depois de o Intune Center estar instalado, pode utilizá-lo para aceder ao portal da empresa, onde pode associar o seu computador à sua conta profissional.

## Microsoft Intune Center
O Intune Center é instalado como uma aplicação no seu computador depois de ter instalado o software de cliente e inscrito o seu computador no Intune com êxito. Pode utilizar o Intune Center para:

-   **Obter aplicações a partir do portal da empresa** - Localize e instale as aplicações implementadas pelo seu administrador de TI. Quando inicia sessão pela primeira vez no portal da empresa num computador inscrito recentemente, é-lhe apresentada a opção para associar a sua conta profissional a esse computador.

-   **Procurar atualizações de software** - Localize atualizações de software implementadas pelo seu administrador do Intune.

-   **Iniciar uma análise do Endpoint Protection ao seu computador** - Pode iniciar uma análise para detetar a existência de software malicioso no seu computador.

-   **Pedir assistência remota** - Esta opção só está disponível se a assistência remota for suportada pelo sistema operativo do seu computador.

## Verificar se o software de cliente está instalado ou se foi removido
**Verifique se o cliente está instalado:**
A instalação do cliente do Intune foi concluída se as seguintes aplicações estiverem disponíveis no computador:

-   **Intune Center**

-   **Endpoint Protection do Intune** (se o Endpoint Protection tiver sido ativado pelo seu administrador de TI)

Se estiver familiarizado com a utilização do Gestor de Tarefas, pode procurar o serviço de cliente do Intune, que deverá estar a executar:

-   **OmcSvc**

**Verifique se o cliente foi removido:**
Depois de desinstalar o cliente do Intune de um computador, as aplicações instaladas quando o cliente foi instalado são removidas, incluindo o Intune Center.

O serviço de cliente do Intune **OmcSvc** é removido.

## Como remover um software de cliente do computador
Por predefinição, o software de cliente do Intune será desinstalado várias horas depois de o seu administrador de TI ter extinguido o seu computador da consola de administração do Intune.

Para desinstalar manualmente o software de cliente do Intune de um computador, pode utilizar os passos seguintes para forçar a desinstalação:

1.  No computador, abra uma linha de comandos no modo de administrador.

2.  Aceda à pasta **%programfiles%\Microsoft\OnlineManagement\Common**

3.  Execute o seguinte comando: **ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune**

Esta ação irá agendar a remoção do software de cliente.



<!--HONumber=May16_HO1-->


