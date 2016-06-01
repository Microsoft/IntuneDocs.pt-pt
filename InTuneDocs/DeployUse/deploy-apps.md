---
# required metadata

title: Implementar aplicações | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Implementar aplicações com o Microsoft Intune

Este tópico explica alguns dos conceitos que tem de compreender antes de iniciar a implementação de aplicações com o Microsoft Intune.

## Intune Software Publisher
O **Microsoft Intune Software Publisher** é iniciado quando adiciona ou modifica aplicações a partir da consola do administrador do Microsoft Intune. A partir do publicador, pode selecionar e configurar um tipo de instalador de software que irá carregar aplicações (programas para computadores ou aplicações para dispositivos móveis) a armazenar no armazenamento na nuvem do Intune ou ligar a uma loja online ou aplicação Web.

### Requisitos
Antes de começar a utilizar o Microsoft Intune Software Publisher, tem de instalar a versão completa do [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Após a instalação, poderá ser necessário reiniciar o computador para que o Software Publisher abra corretamente.

## Espaço de armazenamento na nuvem
Todas as aplicações que implementar com o tipo de instalação do instalador de software têm de ser compactadas e carregadas para o armazenamento na nuvem do Microsoft Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na nuvem, o qual é utilizado para armazenar aplicações e atualizações geridas. Uma subscrição paga inclui 20 GB, com a opção de adquirir armazenamento adicional.

Pode ver quanto espaço está a utilizar e adquirir mais armazenamento no nó **Utilização do Armazenamento** da área de trabalho **Admin**.

Estas regras aplicam-se à aquisição de armazenamento adicional baseado na nuvem para o Intune:

-   Precisa de ter uma subscrição paga ativa para adquirir armazenamento adicional.

-   Apenas os administradores de faturação ou administradores globais do seu Microsoft Online Service podem adquirir armazenamento adicional através do portal de contas do Intune. Para adicionar, eliminar ou gerir estes administradores, tem de ser um administrador global e iniciar sessão no portal de contas do Intune.

-   Se for um cliente de licenciamento em volume que adquiriu o Intune ou o Suplemento Microsoft Intune através do Contrato Enterprise, contacte o seu Gestor de Conta Microsoft ou o Parceiro Microsoft para obter informações sobre os preços e adquirir armazenamento adicional.

#### Requisitos de espaço de armazenamento na nuvem

-   Todos os ficheiros associados a uma aplicação têm de estar na mesma localização e acessíveis pelo Intune.

-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.

-   Para carregar ficheiros, tem de ter uma velocidade mínima de Internet de 768 kbps.

## Ações de implementação de aplicações
Ao implementar aplicações, pode escolher uma das seguintes ações de implementação:

-   **Instalação necessária** – A aplicação é instalada no dispositivo, sem ser necessária intervenção do utilizador final.

    > Para os dispositivos iOS que não estejam no modo supervisionado e para todos os dispositivos Android, o utilizador tem de aceitar a oferta da aplicação antes da instalação da mesma.
    >
    > Já não pode criar novas implementações de aplicações para dispositivos iOS com um sistema operativo anterior ao iOS 7.1. Quaisquer implementações de aplicações existentes para dispositivos com um sistema operativo anterior ao iOS 7.1 continuarão a funcionar e a ser geridas pelo Intune.

-   **Instalação disponível** – A aplicação é apresentada no portal da empresa e os utilizadores finais podem instalá-la a pedido.

-   **Desinstalar** – A aplicação é desinstalada do dispositivo.

-   **Não aplicável** – A aplicação não é apresentada no portal da empresa e não é instalada em nenhum dispositivo.

#### Compreender as ações de implementação que estão disponíveis para cada tipo de instalador

|Tipo de instalador|Instalação necessária|Instalação disponível|Desinstalar|Não aplicável|
|------------------|--------------------|---------------------|-------------|------------------|
|Pacote de aplicações do Windows (implementado num grupo de utilizadores)|Sim|Sim|Sim|Sim|
|Pacote de aplicações do Windows (implementado num grupo de dispositivos)|Sim|Não|Sim|Sim|
|Pacote de aplicações para dispositivos móveis (implementado num grupo de utilizadores)|Sim|Sim|Sim|Sim|
|Pacote de aplicações para dispositivos móveis (implementado num grupo de dispositivos)|Sim|Não|Sim|Sim|
|Windows Installer (implementado num grupo de utilizadores)|Não|Sim|Não|Sim|
|Windows Installer (implementado num grupo de dispositivos)|Sim|Não|Sim|Sim|
|Ligação externa (implementada num grupo de utilizadores)|Não|Sim|Não|Sim|
|Ligação externa (implementada num grupo de dispositivos)|Não|Não|Não|Não|
|Aplicação iOS gerida da loja de aplicações (implementada num grupo de utilizadores)|Sim|Sim|Sim|Sim|
|Aplicação iOS gerida da loja de aplicações (implementada num grupo de dispositivos)|Sim|Não|Sim|Sim|
> Quando implementa aplicações, se selecionar grupos de utilizadores e de dispositivos, só pode implementar a aplicação como uma **Instalação disponível**

## Conflitos de implementação
Quando duas aplicações com a mesma ação de implementação são recebidas por um dispositivo, aplicam-se as seguintes regras:

-   As implementações num grupo de dispositivos têm prioridade sobre as implementações num grupo de utilizadores. No entanto, se uma aplicação for implementada num grupo de utilizadores com uma ação de implementação de **Disponível** e a mesma aplicação for também implementada num grupo de dispositivos com a ação de implementação de **Não Aplicável**, a aplicação será disponibilizada no portal da empresa para instalação por parte dos utilizadores.

-   A intenção do administrador de TI tem prioridade sobre o utilizador.

-   Uma ação de instalação tem prioridade sobre uma ação de desinstalação.

-   Se uma instalação necessária e uma instalação disponível forem recebidas por um dispositivo, as ações são combinadas (a aplicação é tanto necessária quanto disponível).


## Passos seguintes

Saiba como [implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md)

<!--HONumber=May16_HO2-->


