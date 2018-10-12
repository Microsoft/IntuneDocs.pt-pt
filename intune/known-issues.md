---
title: Problemas conhecidos no Microsoft Intune – Azure | Microsoft Docs
description: Saiba mais sobre os problemas conhecidos no Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e523e4fb6505b2faaa0aa776b89454524130ba8
ms.sourcegitcommit: 503d76e0b066d0db77bcc48e5116c861f6a6fb57
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47187857"
---
# <a name="known-issues-in-microsoft-intune"></a>Problemas conhecidos no Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize este artigo para saber mais sobre os problemas conhecidos no Microsoft Intune.

Se quiser comunicar um erro que não se encontra listado aqui, [abra um pedido de suporte](get-support.md).

Se quiser pedir uma nova funcionalidade para o Intune, considere o preenchimento de um relatório no site do [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="migration"></a>Migração

### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal"></a>Exportar políticas de conformidade do portal clássico do Azure para recriar estas políticas no Intune no portal do Azure

As políticas de conformidade que criou no portal clássico do Azure serão preteridas. Pode rever e eliminar quaisquer políticas de conformidade existentes, mas não pode atualizá-las. Se precisar de migrar políticas de conformidade para o Intune no portal do Azure atual, pode exportar as políticas sob a forma de um ficheiro separado por vírgulas (ficheiro .csv). Em seguida, utilize os detalhes no ficheiro para recriar estas políticas no Intune no portal do Azure.

> [!IMPORTANT]
> Quando o portal clássico do Azure for descontinuado, deixará de conseguir aceder ou ver as suas políticas de conformidade. Por isso, não se esqueça de as exportar e recriar no portal do Azure antes de o portal clássico do Azure ser descontinuado.

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>As funcionalidades do Cliente de PC legadas do Intune só estão disponíveis na consola do Silverlight

A capacidade para gerir o Windows 10 no Intune no portal do Azure está disponível através da inscrição na MDM do Windows. Para obter mais informações, veja [Intune na consola do Azure e Cliente de PC do Intune legado](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Os grupos criados pelo Intune durante a migração podem afetar o funcionamento de outros produtos da Microsoft

Quando migrar do Intune para o portal do Azure, poderá ver um novo grupo com o nome **Todos os Utilizadores – b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Este grupo contém todos os utilizadores do Azure Active Directory, não apenas os utilizadores licenciados do Intune. Esta utilização pode provocar problemas com outros produtos Microsoft se estiver à espera que alguns dos utilizadores existentes ou novos não sejam membros de nenhum dos grupos.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Os painéis de estado de políticas migradas não funcionam

Não pode ver as informações de estado de políticas que foram migradas a partir do portal clássico do Azure no portal do Azure. No entanto, pode continuar a ver relatórios dessas políticas no portal clássico. Para ver as informações de estado de políticas de configuração migradas, recrie as mesmas no portal do Azure.

## <a name="apps"></a>Aplicações


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>Múltiplos pedidos de instalação de aplicações para determinadas aplicações VPP
Poderá ver múltiplos pedidos de instalação para determinadas aplicações VPP que já estão instaladas nos dispositivos dos utilizadores finais. Este problema ocorre se tiver a opção **Atualizações automáticas da aplicação** definida como **Ativado** para o token VPP que carregou para o Intune no portal do Azure.    

Para resolver este problema, pode desativar a opção **Atualizações automáticas da aplicação** para o token VPP. Para tal, abra o Microsoft Intune no portal do Azure. No Intune, selecione **Aplicações do cliente** > **Tokens iOS VPP**. Em seguida, selecione o Token VPP que implementou a aplicação afetada e selecione **Editar** > **Atualizações automáticas da aplicação** > **Desativado** > **Guardar**. Em alternativa, pode parar a implementação da aplicação afetada como uma aplicação VPP, o que irá parar a apresentação dos pedidos.    

Este é um problema conhecido na versão atual. Iremos disponibilizar futuramente uma correção para resolver este problema. Quando a correção for implementada, os seus utilizadores deixarão de ver múltiplos pedidos de instalação de aplicações.

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>As aplicações para iOS compradas em volume só estão disponíveis no idioma predefinido do inquilino do Intune
As aplicações para iOS compradas em volume são apresentadas e só podem ser atribuídas para os mesmos indicativos de país que a sua conta do Intune. O Intune só sincroniza aplicações da mesma região do iTunes que o indicativo de país da conta do inquilino do Intune. Por exemplo, se comprar uma aplicação que só está disponível numa loja dos E.U.A., mas a sua conta estiver em alemão, o Intune não mostra essa aplicação.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>São carregadas múltiplas cópias do mesmo programa para iOS comprado em volume
Não clique no botão **Carregar** múltiplas vezes para o mesmo token VPP. Isto irá resultar no carregamento de tokens VPP duplicados e as aplicações irão sincronizar múltiplas vezes para o mesmo token VPP.

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>Algum tráfego do Managed Browser não é encaminhado através do Proxy de Aplicações do Azure <!-- 2463492 -->
Existe um problema conhecido com a integração do Proxy de Aplicações e do Managed Browser em que algum tráfego terciário (tal como chamadas AJAX ou javascript) não é encaminhado através do Proxy de Aplicações do Azure. Este é um problema conhecido na versão atual.  

<!-- ## Groups -->

## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Não pode guardar uma política do Windows Information Protection para alguns dispositivos

Para dispositivos não inscritos com o Intune, apenas pode especificar um domínio primário no campo **Identificar Empresa** nas definições de uma política do Windows Information Protection.
Se adicionar domínios adicionais (através de **Definições avançadas** > **Perímetro da rede** > **Adicionar um domínio protegido**), não poderá guardar a política. A mensagem de erro apresentada será alterada em breve para ser mais precisa.

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Suporte do cliente VPN do Cisco AnyConnect e Cisco Legacy AnyConnect – iOS

Em dispositivos iOS, a integração de controlo de acesso de rede (NAC) não funciona com o novo cliente Cisco AnyConnect. Estamos a trabalhar com a Cisco para disponibilizar a integração de NAC.

[Criar perfis VPN no Intune](vpn-settings-ios.md) proporciona mais detalhes sobre os clientes Cisco AnyConnect e Cisco Legacy AnyConnect.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Utilizar o tipo de palavra-passe numérica com dispositivos Mac OS Sierra

Atualmente, se selecionar o **Tipo de palavra-passe necessária** **Numérica** num perfil de restrição de dispositivos para dispositivos Mac OS Sierra, aquela é imposta como **Alfanumérica**. Se pretender utilizar uma palavra-passe numérica com esses dispositivos, não configure esta definição.
Este problema pode ser corrigido numa versão futura do Mac OS.

Para obter mais informações sobre estas definições, veja [Definições de restrição de dispositivos macOS no Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Conformidade

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>As políticas de conformidade do Intune não aparecem na consola nova

As políticas de conformidade que criou no portal clássico são migradas, mas não são apresentadas no portal do Azure devido a alterações de estrutura do portal do Azure. As políticas de conformidade que criou no portal clássico do Intune ainda são impostas, mas tem de vê-las e editá-las no portal clássico.

Além disso, as novas políticas de conformidade que criar no portal do Azure não são visíveis no portal clássico.

Para obter mais informações, veja [O que é a conformidade do dispositivo](device-compliance.md).

<!-- ## Enrollment -->

## <a name="conditional-access"></a>Acesso condicional

### <a name="conditional-access-settings-from-intune-do-not-show-up-in-new-console"></a>As definições de acesso condicional do Intune não aparecem na consola nova

Depois do seu inquilino ter sido migrado para o portal do Azure, as definições de acesso condicional vão continuar a ser aplicadas; no entanto, não são apresentadas no portal do Intune no Azure. 

Se quiser ver e gerir essas definições no portal do Azure, terá de remover as definições antigas do portal clássico e recriá-las no portal do Azure. 

Para obter mais informações, veja [Melhores práticas para o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/best-practices).

## <a name="data-protection"></a>Proteção de dados

### <a name="ios-app-protection-policies"></a>Políticas de proteção de aplicações para iOS

Pode definir [políticas de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) disponíveis para os utilizadores em dispositivos geridos através de gestão de aplicações móveis (MAM) sem inscrição. Devido a um erro temporário, só pode definir estas políticas para versões do iOS com um único ponto decimal em vez de versões com múltiplos pontos decimais. Em vez de definir uma versão mínima do iOS 10.3.1, irá defini-la para o iOS 10.3. Este problema será resolvido numa futura atualização para o SDK do iOS.


## <a name="administration-and-accounts"></a>Administração e contas

Os Administradores Globais (também designados por Administradores Inquilinos) podem continuar a realizar tarefas diárias de administração sem uma licença separada do Intune ou do Enterprise Mobility Suite (EMS). No entanto, para utilizar o serviço, como, por exemplo, para inscrever os seus próprios dispositivos, um dispositivo da empresa ou utilizar o Portal da Empresa do Intune, precisam de uma licença do Intune ou do EMS.

<!-- ## Additional items -->
