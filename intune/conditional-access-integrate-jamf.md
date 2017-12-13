---
title: Integrar o Jamf Pro com o Intune para conformidade
titlesuffix: Azure portal
description: Utilize a conformidade para ajudar a proteger os dispositivos geridos pelo Jamf.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 87ddb1a5f6ca5cc9be2815aacc9c1570a51e792f
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2017
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

|Aplica-se a: Intune no portal do Azure |
|--|
|Está à procura de documentação sobre o Intune no portal clássico? [Aceda aqui](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Atualmente, em Pré-visualização Privada|
|--|
|As funcionalidades descritas neste tópico só estão disponíveis para clientes que estão atualmente em pré-visualização privada. Esta mensagem será removida quando as mesmas forem lançadas para todos os clientes.|
| |

Se a sua organização utilizar o [Jamf Pro](https://www.jamf.com) para gerir os Macs dos utilizadores finais, poderá utilizar as políticas de conformidade do Microsoft Intune com o acesso condicional do Azure Active Directory para garantir que os dispositivos na sua organização estão em conformidade.

## <a name="prerequisites"></a>Pré-requisitos

É preciso o seguinte para configurar o acesso condicional com o Jamf Pro:

- Acesso à Pré-visualização Privada do Intune para acesso condicional
- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS com OS X 10.11 Yosemite ou posterior

## <a name="connecting-intune-to-jamf-pro"></a>Ligar o Intune ao Jamf Pro

Pode ligar o Intune através do Jamf Pro ao:

1. Criar uma nova aplicação no Azure
2. Integrar o Intune com o Jamf Pro
3. Configurar o acesso condicional no Jamf Pro

## <a name="create-a-new-application-in-azure-active-directory"></a>Criar uma nova aplicação no Azure Active Directory

1. Abra o **Azure Active Directory** > **Registos das Aplicações**.
2. Clique em **+Novo registo de aplicação**.
3. Introduza um **nome a apresentar**, tal como **Acesso Condicional do Jamf**.
4. Selecione **Aplicação Web/API**.
5. Especifique o **URL de Início de Sessão** com o seu URL de instância do Jamf Pro.
6. Clique em **Criar aplicação**.
7. Guarde o **ID da Aplicação** recentemente criado e, em seguida, abra **Definições** e navegue até **Acesso à API** > **Chaves** para criar uma nova Chave da Aplicação. Introduza uma **Descrição**, o prazo até a mesma **Expirar** e, em seguida, guarde a Chave da Aplicação. 

  > [!IMPORTANT]
  > A Chave da Aplicação só é apresentada uma vez durante este processo. Lembre-se de a guardar num local de fácil acesso.

8. Abra as **Definições**, navegue até **Acesso à API** > **Permissões Obrigatórias** e elimine todas as permissões.

  > [!NOTE]
  > Adicione uma nova permissão necessária. A aplicação só poderá funcionar corretamente se tiver a permissão única necessária.

9.  Selecione a **API do Microsoft Intune** e clique em **Selecionar**.
10. Escolha **Enviar atributos do dispositivo para o Microsoft Intune** e clique em **Selecionar**.
11. Clique no botão **Conceder Permissões** depois de guardar as permissões necessárias da aplicação.

  > [!NOTE]
  > Se a Chave da Aplicação expirar, terá de criar uma nova Chave da Aplicação no Microsoft Azure e, em seguida, atualizar os dados do Acesso Condicional no Jamf Pro. O Azure permite-lhe ter a chave antiga e a nova chave ativas para evitar interrupções ao serviço.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. No portal do Microsoft Azure, abra o **Microsoft Intune** > **Conformidade do Dispositivo** > **Gestão de dispositivos de parceiros**.
2. Ative o Conector de Conformidade para Jamf ao colar o ID da Aplicação no campo **ID da Aplicação do Azure Active Directory do Jamf**.
3. Clique em **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. No Jamf Pro, navegue para **Gestão Global** > **Acesso Condicional**. Clique no botão **Edit** (Editar) no separador **Microsoft Intune Integration** (Integração do Microsoft Intune).
2. Selecione a caixa de verificação **Enable Microsoft Intune Integration** (Ativar a Integração do Microsoft Intune).
3. Indique as informações necessárias sobre o seu inquilino do Azure, incluindo a **Location** (Localização), o **Domain name** (Nome de domínio), bem como o **Application ID** (ID da Aplicação) e a **Application Key** (Chave da Aplicação) que guardou dos passos anteriores.
4. Clique em **Save** (Guardar). O Jamf Pro testará as definições e verificará se obteve êxito.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

Após terminar de configurar a integração entre o Intune e o Jamf, tem de [aplicar as políticas de conformidade aos dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md).

## <a name="information-shared-from-jamf-pro-to-intune"></a>Informações partilhadas do Jamf Pro com o Intune

O Jamf Pro recolhe informações de inventário sobre dispositivos macOS geridos. O Jamf Pro reporta as seguintes informações ao Intune:

* ID do Azure AD do Dispositivo
* Estado de Inventário do JAMF (estado de inventário de um computador registado através do Jamf Pro nas últimas 24 horas)
* Versão do SO
* ID do Azure AD do Utilizador
* Dados encriptados (FileVault 2)
* Estado do Controlador de Chamadas
* Palavra-passe: número mínimo de conjuntos de carateres
* Expiração da palavra-passe (dias)
* Tipo de Palavra-passe – simples, alfanumérico ou desconhecido
* Impedir o Início de Sessão Automático
* Comprimento do Código de Acesso Necessário
* Palavra-passe: número de palavras-passe anteriores para impedir a reutilização
* Proteção da Integridade do Sistema
* Hora do Último Registo
* Tipo de Arquitetura
* Ranhuras de RAM Disponíveis
* Capacidade de Bateria
* ROM de Arranque
* Velocidade do Barramento
* Tamanho da Cache
* Nome do Dispositivo
* Associação a um Domínio
* ID do Jamf
* Endereço MAC
* Fabrico
* Model
* Identificador do Modelo
* Velocidade da NIC
* Número de Núcleos
* Número de Processadores
* SO
* Platform
* Velocidade do Processador
* Tipo de Processador
* Endereço MAC Secundário
* Número de Série
* Versão do SMC
* Total de RAM
* UDID
* E-mail do Utilizador

## <a name="next-steps"></a>Próximos passos

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)