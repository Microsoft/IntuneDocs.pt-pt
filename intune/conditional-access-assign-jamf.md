---
title: "Impor políticas de conformidade a dispositivos geridos pelo Jamf"
titlesuffix: Azure portal
description: Utilize a conformidade para ajudar a proteger os dispositivos geridos pelo Jamf.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c72de87b87775155672994163140e342b7ba99b4
ms.sourcegitcommit: 000684953cbb3ceae0e2bcaa51186c9221f7aa86
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/15/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Impor a conformidade em Macs geridos com o Jamf Pro

|Aplica-se a: Intune no portal do Azure |
|--|
|Está à procura de documentação sobre o Intune no portal clássico? [Aceda aqui](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

Pode utilizar o Azure Active Directory e as políticas de acesso condicional do Microsoft Intune para garantir que os utilizadores finais cumprem os requisitos da organização. Pode aplicar estas políticas em Macs [geridos com o Jamf Pro](conditional-access-integrate-jamf.md). Para tal, precisa do acesso às consolas do Intune e do Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configurar políticas de conformidade de dispositivos no Intune

1. Abra o Microsoft Azure e navegue para **Intune** > **Conformidade do Dispositivo** > **Políticas**. Pode criar políticas para macOS, incluindo escolher uma série de ações (por exemplo, enviar e-mails de aviso) para os utilizadores e grupos não conformes.
2. Pesquise os grupos pretendidos e, em seguida, aplique as políticas.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Implementar a aplicação Portal da Empresa para macOS no Jamf Pro

Deve implementar a aplicação Portal da Empresa para macOS no Jamf Pro como uma instalação em segundo plano através do procedimento abaixo:

1. Num dispositivo macOS, transfira a versão atual da [aplicação Portal da Empresa para macOS](https://go.microsoft.com/fwlink/?linkid=862280). Não a instale, pois irá precisar de uma cópia da aplicação para carregar para o Jamf Pro.
2. Abra o Jamf Pro e navegue para **Gestão de computadores** > **Pacotes**.
3. Crie um novo pacote com a aplicação Portal da Empresa para macOS e, em seguida, clique em **Guardar**.
4. Abra **Computadores** > **Políticas** e, em seguida, selecione **Novo**.
5. Utilize o payload **Geral** para configurar as definições da política. Estas definições deverão ser:
   - Acionador: selecione **Inscrição Completa** e **Inscrição Periódica**
   - Frequência de execução: selecione **Uma por computador**
6. Selecione o payload **Pacotes** e clique em **Configurar**.
7. Clique em **Adicionar** para selecionar o pacote com a aplicação Portal da Empresa.
8. Escolha **Instalar** no menu de pop-up **Ação**.
9. Configure as definições do pacote.
10. Clique no separador **Âmbito** para especificar os computadores nos quais deve ser instalada a aplicação Portal da Empresa. Clique em **Guardar**. A política será executada nos dispositivos abrangidos da próxima vez que o acionador selecionado ocorrer no computador e cumprir os critérios do payload **Geral**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Criar uma política no Jamf Pro para que os utilizadores registem os respetivos dispositivos com o Azure Active Directory

> [!NOTE]
> Terá de [implementar o Portal da Empresa](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) para macOS antes de passar para os passos seguintes.  

Os utilizadores finais têm de iniciar a aplicação Portal da Empresa através do Jamf Self-Service para registar o dispositivo com o Azure AD como um dispositivo gerido pelo Jamf Pro. Será necessário que os seus utilizadores finais tomem medidas. Recomendamos que [contacte os seus utilizadores finais](end-user-educate.md) por e-mail, através de notificações no Jamf Pro ou por outros métodos, para que estes cliquem no botão no Jamf Self Service.

> [!WARNING]
> A aplicação Portal da Empresa tem de ser iniciada a partir do Jamf Self Service para iniciar o registo do dispositivo. <br><br>Se iniciar a aplicação Portal da Empresa manualmente (por exemplo, a partir da pasta Aplicações ou Transferências), o dispositivo não será registado. Se um utilizador final iniciar manualmente o Portal da Empresa, verá o aviso "AccountNotOnboarded".

1. No Jamf Pro, navegue para **Computadores** > **Políticas** e crie uma nova política para o registo do dispositivo.
2. Configure o payload **Integração do Microsoft Intune**, incluindo o acionamento e a frequência de execução.
3. Clique no separador **Âmbito** e defina o âmbito da política para todos os dispositivos visados.
4. Clique no separador **Self-Service** para disponibilizar a política no Jamf Self-Service. Inclua a política na categoria **Conformidade do Dispositivo**. Clique em **Guardar**.

## <a name="next-steps"></a>Próximos passos

- [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introdução ao acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
