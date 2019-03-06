---
title: Política de conformidade de dispositivos para dispositivos de Jamf | Microsoft Intune
titlesuffix: Microsoft Intune
description: Utilize as políticas de conformidade do Microsoft Intune com o acesso condicional do Azure Active Directory para ajudar a proteger os dispositivos geridos pelo Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4c6e420134461ef5165255703b8cafa0bdb71d7
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57393334"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Impor a conformidade em Macs geridos com o Jamf Pro

Aplica-se a: Intune no portal do Azure

Pode utilizar o Azure Active Directory e as políticas de acesso condicional do Microsoft Intune para garantir que os utilizadores finais cumprem os requisitos da organização. Pode aplicar estas políticas em Macs [geridos com o Jamf Pro](conditional-access-integrate-jamf.md). Para tal, precisa do acesso às consolas do Intune e do Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configurar políticas de conformidade de dispositivos no Intune

1. Abra o Microsoft Azure e navegue para **Intune** > **Conformidade do Dispositivo** > **Políticas**. Pode criar políticas para macOS, incluindo escolher uma série de ações (por exemplo, enviar e-mails de aviso) para os utilizadores não conformes e grupos.
2. Pesquise os grupos pretendidos e, em seguida, aplique as políticas.

> [!Note]
> O Intune exige que a encriptação total do disco esteja em conformidade.

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
> Terá de [implementar o Portal da Empresa](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para macOS antes de passar para os passos seguintes.  

Os utilizadores finais têm de iniciar a aplicação Portal da Empresa através do Jamf Self-Service para registar o dispositivo com o Azure AD como um dispositivo gerido pelo Jamf Pro. Será necessário que os seus utilizadores finais tomem medidas. Recomendamos que [contacte os seus utilizadores finais](end-user-educate.md) por e-mail, através de notificações no Jamf Pro ou por outros métodos, para que estes cliquem no botão no Jamf Self Service.

> [!WARNING]
> A aplicação Portal da Empresa tem de ser iniciada a partir do Jamf Self Service para iniciar o registo do dispositivo. <br><br>Se iniciar a aplicação Portal da Empresa manualmente (por exemplo, a partir da pasta Aplicações ou Transferências), o dispositivo não será registado. Se um utilizador final iniciar manualmente o Portal da Empresa, verá o aviso "AccountNotOnboarded".

1. No Jamf Pro, navegue para **Computadores** > **Políticas** e crie uma nova política para o registo do dispositivo.
2. Configure o payload **Integração do Microsoft Intune**, incluindo o acionamento e a frequência de execução.
3. Clique no separador **Âmbito** e defina o âmbito da política para todos os dispositivos visados.
4. Clique no separador **Self-Service** para disponibilizar a política no Jamf Self-Service. Inclua a política na categoria **Conformidade do Dispositivo**. Clique em **Guardar**.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Remover um dispositivo gerido por Jamf do Intune

Pode remover um dispositivo gerido por Jamf a partir da consola do Intune ao selecionar **Eliminar** na vista **Todos os dispositivos**. A eliminação de dispositivos em massa pode ser ativada ao selecionar múltiplos dispositivos e clicar em **Eliminar**.

Obtenha informações sobre como [remover um dispositivo gerido por Jamf na documentação do Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Também pode enviar um pedido de suporte para o [suporte do Jamf](https://www.jamf.com/support/) para obter ajuda adicional. 

## <a name="next-steps"></a>Passos Seguintes

- [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introdução ao acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
