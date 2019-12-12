---
title: Configurar a inscrição para dispositivos Windows com o Microsoft Intune
titleSuffix: ''
description: Configure a inscrição para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b84cd52dfe2eb6332ddbc89bc00a17ec3361b79
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000436"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configurar a inscrição para dispositivos Windows

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo ajuda os administradores de TI a simplificar a inscrição de dispositivos Windows para os seus utilizadores. Assim que tiver [configurado o Intune](../fundamentals/setup-steps.md), os utilizadores inscrevem os dispositivos do Windows ao [iniciar sessão](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) na respetiva conta escolar ou profissional.  

Enquanto administrador do Intune, pode simplificar a inscrição das seguintes formas:

- [Ativar a inscrição automática](#enable-windows-10-automatic-enrollment) (é necessário o Azure AD Premium)
- [Registo CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Ativar a inscrição em massa](../windows-bulk-enroll.md) (é necessário o Azure AD Premium e o Windows Configuration Designer)

Dois fatores determinam como pode simplificar a inscrição de dispositivos do Windows:

- **Utiliza o Azure Active Directory Premium?** <br>O [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) está incluído com o Enterprise Mobility + Security e outros planos de licenciamento.
- **Que versões de clientes do Windows serão inscritas pelos utilizadores?** <br>Os dispositivos Windows 10 podem ser inscritos automaticamente ao adicionar uma conta escolar ou profissional. As versões anteriores têm de ser inscritas através da aplicação Portal da Empresa.

||**Azure AD Premium**|**Outros AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscrição automática](#enable-windows-10-automatic-enrollment) |Inscrição do utilizador|
|**Versões do Windows anteriores**|Inscrição do utilizador|Inscrição do utilizador|

As organizações que podem utilizar a inscrição automática também podem configurar a [inscrição de dispositivos em massa](../windows-bulk-enroll.md) com a aplicação Windows Configuration Designer.

## <a name="device-enrollment-prerequisites"></a>Pré-requisitos de registro de dispositivo

Antes que um administrador possa registrar dispositivos no Intune para gerenciamento, as licenças já devem ter sido atribuídas à conta do administrador. [Leia sobre como atribuir licenças para registro de dispositivo](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>Suporte para múltiplos utilizadores

O Intune dá suporte a vários usuários em dispositivos que:

- executar a atualização do criador do Windows 10
- estão Azure Active Directory ingressados no domínio.

Quando os utilizadores padrão iniciam sessão com as suas credenciais do Azure AD, recebem aplicações e políticas atribuídas ao respetivo nome de utilizador. Somente o [usuário principal](../remote-actions/find-primary-user.md) do dispositivo pode usar o portal da empresa para cenários de autoatendimento, como instalar aplicativos e executar ações de dispositivo (remover, redefinir). Para dispositivos Windows 10 compartilhados que não têm um usuário primário atribuído, o Portal da Empresa ainda pode ser usado para instalar aplicativos disponíveis.

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Simplificar a inscrição do Windows sem o Azure AD Premium
Para simplificar a inscrição, crie um alias (tipo de registo CNAME) de servidor de nomes de domínio (DNS) que redirecione os pedidos de inscrição para os servidores do Intune. Caso contrário, os utilizadores que tentem ligar ao Intune terão de introduzir o nome de servidor do Intune durante a inscrição.

**Passo 1: criar o registo CNAME** (opcional)<br>
Crie registos de recursos DNS CNAME para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.

|Tipo|Nome do anfitrião|Aponta para|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|
|CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 hora|

Se a empresa utilizar mais do que um sufixo UPN, tem de criar um CNAME para cada nome de domínio e apontar cada um para EnterpriseEnrollment-s.manage.microsoft.com. Por exemplo, os utilizadores na Contoso utilizam os seguintes formatos como e-mail/UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

Os administradores de DNS da Contoso devem criar os seguintes CNAMEs:

|Tipo|Nome do anfitrião|Aponta para|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Suportados Pontos Finais adicionais, mas Não Recomendados
Enterpriseenrollment-s.Manage.microsoft.com é o FQDN preferencial para a inscrição, mas existem dois outros pontos finais que foram utilizados pelos clientes no passado e que são suportados. EnterpriseEnrollment.manage.microsoft.com (sem o -s) e manage.microsoft.com ambos funcionam como o destino para o servidor de deteção automática, mas o utilizador vai ter de selecionar OK numa mensagem de confirmação. Se apontar para EnterpriseEnrollment-s.manage.microsoft.com, o utilizador não terá de fazer o passo adicional da confirmação, por isso, esta é a configuração recomendada

## <a name="alternate-methods-of-redirection-are-not-supported"></a>Não São Suportados Métodos Alternativos de Redirecionamento
Não é suportada a utilização de um método que não seja a configuração do CNAME. Por exemplo, não é suportada a utilização de um servidor proxy para redirecionar enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc para enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc ou para manage.microsoft.com/EnrollmentServer/Discovery.svc.

**Passo 2: verificar o CNAME** (opcional)<br>
1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **registro** do Windows ** > Windows > ** **validação de CNAME**.
2. Na caixa **Domínio**, introduza o site da empresa e, em seguida, selecione **Testar**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informar os utilizadores sobre como inscrever dispositivos Windows
Informe os seus utilizadores sobre como inscrever os dispositivos Windows e o que esperar após começarem a ser geridos.

> [!NOTE]
> Os utilizadores finais têm de aceder ao site do Portal da Empresa através do Microsoft Edge para verem as aplicações do Windows que atribuiu a versões específicas do Windows. Os outros browsers, incluindo o Google Chrome, o Mozilla Firefox e o Internet Explorer, não suportam este tipo de filtragem.

Para obter instruções de inscrição do utilizador final, veja [Inscrever o dispositivo Windows no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Também pode dizer aos utilizadores para consultarem [Que informações pode o administrador de TI ver no meu dispositivo](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Se não tiver a Inscrição automática de MDM ativada, mas tiver dispositivos Windows 10 que foram associados ao Azure AD, serão visíveis dois registos na consola do Intune após a inscrição. Pode parar este processo ao certificar-se de que os utilizadores com dispositivos associados ao Azure AD acedem a **Contas** > **Acesso profissional ou escolar** e **Ligar** com a mesma conta. 

Para obter mais informações sobre as tarefas do utilizador final, veja [Recursos sobre a experiência do utilizador final com o Microsoft Intune](../fundamentals/end-user-educate.md).

## <a name="registration-and-enrollment-cnames"></a>CNAMEs de registro e registro
Azure Active Directory tem um CNAME diferente que ele usa para o registro de dispositivo para dispositivos iOS, Android e Windows. O acesso condicional do Intune requer que os dispositivos sejam registrados, também chamado de "Workplace Unido". Se você planeja usar o acesso condicional, também deverá configurar o CNAME EnterpriseRegistration para cada nome de empresa que você tiver.

| Tipo | Nome do anfitrião | Aponta para | TTL |
| --- | --- | --- | --- |
| NAME | EnterpriseRegistration. company_domain. com | EnterpriseRegistration.windows.net | 1 hora|

Para obter mais informações sobre o registro de dispositivo, consulte [gerenciar identidades de dispositivo usando o portal do Azure](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal)

## <a name="windows-10-auto-enrollment-and-device-registration"></a>Registro automático de dispositivo e registro do Windows 10
Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se nenhum registro CNAME de registro for encontrado, os usuários serão solicitados a inserir manualmente o nome do servidor MDM, enrollment.manage.microsoft.us.

| Tipo | Nome do anfitrião | Aponta para | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.dominio_empresa.com | EnterpriseEnrollment-s.manage.microsoft.us | 1 hora|
|CNAME | EnterpriseRegistration.dominio_empresa.com | EnterpriseRegistration.windows.net | 1 hora |


## <a name="next-steps"></a>Próximos passos

- [Considerações sobre quando gerir dispositivos Windows com o Intune no Azure](../fundamentals/intune-legacy-pc-client.md).
