---
title: "Aplicar políticas de conformidade a dispositivos geridos pelo Jamf"
titlesuffix: Azure portal
description: Utilize a conformidade para ajudar a proteger os dispositivos geridos pelo Jamf.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6184552ce901ffc062f0453f169ec992049ae69b
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Impor a conformidade em Macs geridos com o Jamf Pro

|Aplica-se a: Intune no portal do Azure |
|--|
|Está à procura de documentação sobre o Intune no portal clássico? [Aceda aqui](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Atualmente, em Pré-visualização Privada|
|--|
|As funcionalidades descritas neste tópico só estão disponíveis para clientes que estão atualmente em pré-visualização privada. Esta mensagem será removida quando as mesmas forem lançadas para todos os clientes.|
| |

Pode utilizar o Azure Active Directory e as políticas de acesso condicional do Microsoft Intune para garantir que os utilizadores finais cumprem os requisitos da organização. Pode aplicar estas políticas em Macs [geridos com o Jamf Pro](conditional-access-integrate-jamf.md). Para tal, precisa do acesso às consolas do Intune e do Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configurar políticas de conformidade de dispositivos no Intune

1. Abra o Microsoft Azure e navegue para **Intune** > **Conformidade do Dispositivo** > **Políticas**. Pode criar políticas para macOS, incluindo escolher uma série de ações (por exemplo, enviar e-mails de aviso) para os utilizadores e grupos não conformes.
2. Pesquise os grupos pretendidos e, em seguida, aplique as políticas.

## <a name="require-the-company-portal-app-for-macos"></a>Exigir a aplicação Portal da Empresa para macOS

1. Num dispositivo macOS, aceda a https://aka.ms/macoscompanyportal para transferir a versão atual da aplicação do Portal da Empresa para macOS.
2. Abra o Jamf Pro e navegue para **Gestão de computadores** > **Pacotes**.
3. Crie um novo pacote com a aplicação Portal da Empresa para macOS e, em seguida, clique em **Guardar**.
4. Abra **Computadores** > **Políticas** e, em seguida, selecione **Novo**.
5. Utilize o payload **Geral** para configurar definições para a política, incluindo a frequência de acionamento e de execução.
6. Selecione o payload **Pacotes** e clique em **Configurar**.
7. Clique em **Adicionar** para selecionar o pacote com a aplicação Portal da Empresa.
8. Escolha **Instalar** no menu de pop-up **Ação**.
9. Configure as definições do pacote.
10. Clique no separador **Âmbito** para especificar os computadores nos quais deve ser instalada a aplicação Portal da Empresa. Clique em **Guardar**. A política será executada nos dispositivos abrangidos da próxima vez que o acionador selecionado ocorrer no computador e cumprir os critérios do payload **Geral**.

## <a name="direct-your-users-to-register-jamf-pro-managed-devices-with-azure-active-directory"></a>Direcionar os utilizadores para registarem dispositivos geridos pelo Jamf Pro com o Azure Active Directory

> [!NOTE]
> Terá de [implementar o Portal da Empresa](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) para macOS antes de passar para os passos seguintes.  

Os utilizadores finais têm de iniciar a aplicação Portal da Empresa através do Jamf Self-Service para registar o dispositivo com o Azure AD como um dispositivo gerido pelo Jamf Pro.

1. No Jamf Pro, navegue para **Computadores** > **Políticas** e crie uma nova política para o registo do dispositivo.
2. Configure o payload **Acesso Condicional**, incluindo a frequência de acionamento e de execução. Defina a prioridade como **Após**.
3. Clique no separador **Âmbito** e defina o âmbito da política para todos os dispositivos visados.
4. Clique no separador **Self-Service** para disponibilizar a política no Jamf Self-Service. Inclua a política na categoria **Conformidade do Dispositivo**. Clique em **Guardar**.
