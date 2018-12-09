---
title: Configurar a inscrição para dispositivos Windows com o Microsoft Intune
titlesuffix: ''
description: Configure a inscrição para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9562eb2c8fae49628ac042f28f172fb9f8fd5106
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112549"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configurar a inscrição para dispositivos Windows

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo ajuda os administradores de TI a simplificar a inscrição de dispositivos Windows para os seus utilizadores. Assim que tiver [configurado o Intune](setup-steps.md), os utilizadores inscrevem os dispositivos do Windows ao [iniciar sessão](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) na respetiva conta escolar ou profissional.  

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

## <a name="multi-user-support"></a>Suporte para múltiplos utilizadores

O Intune suporta a gestão de vários utilizadores para dispositivos a executar a atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory. Quando os utilizadores padrão iniciam sessão com as suas credenciais do Azure AD, recebem aplicações e políticas atribuídas ao respetivo nome de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como instalar aplicações.

[!INCLUDE [AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Simplificar a inscrição do Windows sem o Azure AD Premium
Para simplificar a inscrição, crie um alias (tipo de registo CNAME) de servidor de nomes de domínio (DNS) que redirecione os pedidos de inscrição para os servidores do Intune. Caso contrário, os utilizadores que tentem ligar ao Intune terão de introduzir o nome de servidor do Intune durante a inscrição.

**Passo 1: criar o registo CNAME** (opcional)<br>
Crie registos de recursos DNS CNAME para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.

|Type|Nome do anfitrião|Aponta para|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|
|CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 hora|

Se a empresa utilizar mais do que um sufixo UPN, tem de criar um CNAME para cada nome de domínio e apontar cada um para EnterpriseEnrollment-s.manage.microsoft.com. Por exemplo, os utilizadores na Contoso utilizam os seguintes formatos como e-mail/UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.constoso.com\

Os administradores de DNS da Contoso devem criar os seguintes CNAMEs:

|Type|Nome do anfitrião|Aponta para|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

**Passo 2: verificar o CNAME** (opcional)<br>
1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Validação de CNAME**.
2. Na caixa **Domínio**, introduza o site da empresa e, em seguida, selecione **Testar**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informar os utilizadores sobre como inscrever dispositivos Windows
Informe os seus utilizadores sobre como inscrever os dispositivos Windows e o que esperar após começarem a ser geridos.

> [!NOTE]
> Os utilizadores finais têm de aceder ao site do Portal da Empresa através do Microsoft Edge para verem as aplicações do Windows que atribuiu a versões específicas do Windows. Os outros browsers, incluindo o Google Chrome, o Mozilla Firefox e o Internet Explorer, não suportam este tipo de filtragem.

Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Também pode dizer aos utilizadores para consultarem [Que informações pode o administrador de TI ver no meu dispositivo](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Se não tiver a Inscrição automática de MDM ativada, mas tiver dispositivos Windows 10 que foram associados ao Azure AD, serão visíveis dois registos na consola do Intune após a inscrição. Pode parar este processo ao certificar-se de que os utilizadores com dispositivos associados ao Azure AD acedem a **Contas** > **Acesso profissional ou escolar** e **Ligar** com a mesma conta. 

Para obter mais informações sobre as tarefas do utilizador final, veja [Recursos sobre a experiência do utilizador final com o Microsoft Intune](end-user-educate.md).

## <a name="next-steps"></a>Passos Seguintes

- [Considerações sobre quando gerir dispositivos Windows com o Intune no Azure](intune-legacy-pc-client.md).
