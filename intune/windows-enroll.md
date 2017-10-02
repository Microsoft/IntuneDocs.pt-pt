---
title: Inscrever dispositivos Windows
titlesuffix: Azure portal
description: "Ative a gestão de dispositivos móveis (MDM) do Intune para dispositivos Windows.\""
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cd858d617d9a9f2154a5682f5421a096d0c28224
ms.sourcegitcommit: 75cea2402a3726c72b12df6111f6d3ee93c852bf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2017
---
# <a name="enroll-windows-devices"></a>Inscrever dispositivos Windows

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico ajuda os administradores de TI a simplificar a inscrição de dispositivos Windows para os seus utilizadores. Assim que tiver [configurado o Intune](setup-steps.md), os utilizadores inscrevem os dispositivos do Windows ao [iniciar sessão](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) na respetiva conta escolar ou profissional.  

Enquanto administrador do Intune, pode simplificar a inscrição das seguintes formas:
- [Ativar a inscrição automática](#enable-windows-10-automatic-enrollment) (é necessário o Azure AD Premium)
- [Registo CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Ativar a inscrição em massa](windows-bulk-enroll.md) (é necessário o Azure AD Premium e o Windows Configuration Designer)

Dois fatores determinam como pode simplificar a inscrição de dispositivos do Windows:

- **Utiliza o Azure Active Directory Premium?** <br>O [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) está incluído com o Enterprise Mobility + Security e outros planos de licenciamento.
- **Que versões de clientes do Windows serão inscritas pelos utilizadores?** <br>Os dispositivos Windows 10 podem ser inscritos automaticamente ao adicionar uma conta escolar ou profissional. As versões anteriores têm de ser inscritas através da aplicação Portal da Empresa.

||**Azure AD Premium**|**Outros AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscrição automática](#enable-windows-10-automatic-enrollment) |[Inscrição de utilizadores](#enable-windows-enrollment-without-azure-ad-premium)|
|**Versões do Windows anteriores**|[Inscrição de utilizadores](#enable-windows-enrollment-without-azure-ad-premium)|[Inscrição de utilizadores](#enable-windows-enrollment-without-azure-ad-premium)|

As organizações que podem utilizar a inscrição automática também podem configurar a [inscrição de dispositivos em massa](windows-bulk-enroll.md) com a aplicação Windows Configuration Designer.

**Suporte para múltiplos utilizadores**<br>
Os dispositivos a executar a Atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory são agora suportados para a gestão de vários utilizadores pelo Intune. Quando os utilizadores padrão iniciam sessão com as suas credenciais do Azure AD, recebem aplicações e políticas atribuídas ao respetivo nome de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como instalar aplicações.

[!INCLUDE[AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Simplificar a inscrição do Windows sem o Azure AD Premium
Pode simplificar a inscrição dos utilizadores através da criação de um alias (tipo de registo CNAME) de servidor de nomes de domínio (DNS), que redireciona automaticamente os pedidos de inscrição para os servidores do Intune. Se não criar um registo de recurso DNS CNAME, os utilizadores que tentarem ligar ao Intune terão de introduzir o nome do servidor Intune durante a inscrição.

**Passo 1: criar o registo CNAME** (opcional)<br>
Crie registos de recursos DNS CNAME para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.

|Tipo|Nome do anfitrião|Aponta para|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|
|CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hora|

Se tiver mais do que um sufixo UPN, tem de criar um CNAME para cada nome de domínio e apontar cada um para EnterpriseEnrollment-s.manage.microsoft.com. Se os utilizadores na Contoso utilizarem name@contoso.com e também name@us.contoso.com e name@eu.constoso.com como e-mail/UPN, o administrador de DNS da Contoso deverá criar os seguintes CNAMEs:

|Tipo|Nome do anfitrião|Aponta para|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

**Passo 2: verificar o CNAME** (opcional)<br>
No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel Intune, escolha **Inscrever dispositivos** > **Inscrição do Windows**. Introduza o URL do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informar os utilizadores sobre como inscrever dispositivos Windows
Informe os seus utilizadores sobre como inscrever os dispositivos Windows e o que esperar após começarem a ser geridos. Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Também pode dizer aos utilizadores para consultarem [Que informações pode o administrador de TI ver no meu dispositivo](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Para obter mais informações sobre as tarefas do utilizador final, veja [Recursos sobre a experiência do utilizador final com o Microsoft Intune](end-user-educate.md).
