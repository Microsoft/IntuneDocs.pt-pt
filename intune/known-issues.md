---
title: Problemas conhecidos no Microsoft Intune no Azure
titleSuffix: Intune on Azure
description: Leia sobre os problemas conhecidos no Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d069775cf51e8c077a6f30123bf4fa2fe58b6bd8
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="known-issues-in-microsoft-intune"></a>Problemas conhecidos no Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Utilize este tópico para saber mais sobre os problemas conhecidos no Microsoft Intune.

Se quiser comunicar um erro que não se encontra listado aqui, [abra um pedido de suporte](get-support.md).

Se quiser pedir uma nova funcionalidade para o Intune, considere o preenchimento de um relatório no nosso site [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="migration"></a>Migração

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Os grupos criados pelo Intune durante a migração podem afetar o funcionamento de outros produtos da Microsoft

Quando migrar do Intune clássico para o portal do Azure, poderá ver um novo grupo com o nome **Todos os Utilizadores – b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Este grupo contém todos os utilizadores do Azure Active Directory, não apenas os utilizadores licenciados do Intune. Esta utilização pode provocar problemas com outros produtos Microsoft se estiver à espera que alguns dos utilizadores existentes ou novos não sejam membros de nenhum dos grupos.

### <a name="secondary-migration-required-for-select-capabilities"></a>Migração secundária necessária para capacidades selecionadas

As contas do Intune criadas antes de janeiro de 2017 devem ser migradas antes destas capacidades poderem ser utilizadas no portal do Azure:

- Perfis de Inscrição de Dispositivos Empresariais
- Programa de Inscrição de Dispositivos da Apple
- Dispositivos empresariais pré-inscritos por grupo de número de série do iOS
- Gestores de Inscrição de Dispositivos
- Apple Volume Purchase Program

Uma vez que estas capacidades não podem ser geridas no Silverlight clássico e nas consolas do Azure, a migração:
- Desativa-as na consola clássica
- Ativa-as na consola do Azure  

Se agora pode gerir estas funcionalidades do Intune no portal do Azure, tenha em atenção os seguintes pontos:

#### <a name="removes-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Remove perfis predefinidos de Inscrição de Dispositivos Empresariais no DEP da Apple
O portal do Azure não suporta o perfil predefinido de Inscrição de Dispositivos Empresariais para dispositivos do Programa de Inscrição de Dispositivos (DEP) da Apple. Esta funcionalidade, disponível na consola clássica do Intune no Silverlight, é descontinuada para evitar a atribuição inadvertida de perfis. Quando os números de série de DEP são sincronizados no portal do Azure, não é atribuído nenhum perfil de Inscrição de Dispositivos Empresariais. Um perfil de inscrição deve ser atribuído antes de utilizar o dispositivo.

#### <a name="apple-dep-token-restored-with-migration"></a>Token do DEP da Apple restaurado com a migração

Se eliminar um token do Programa de Inscrição de Dispositivos da Apple no portal clássico do Intune (Silverlight) e não carregar um novo token para o portal do Azure, o token original será restaurado no portal do Azure quando migrar. Para remover este token e impedir a inscrição do DEP, elimine o token no portal do Azure.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Os painéis de estado de políticas migradas não funcionam

Não pode ver as informações de estado de políticas que foram migradas do portal clássico no portal do Azure. No entanto, pode continuar a ver relatórios dessas políticas no portal clássico. Para ver as informações de estado de políticas de configuração migradas, recrie as mesmas no portal do Azure.

## <a name="apps"></a>Aplicações

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>As aplicações para iOS compradas em volume só estão disponíveis no idioma predefinido do inquilino do Intune
As aplicações para iOS compradas em volume são apresentadas e só podem ser atribuídas para os mesmos indicativos de país que a sua conta do Intune. O Intune só sincroniza aplicações da mesma região do iTunes que o indicativo de país da conta do inquilino do Intune. Por exemplo, se comprar uma aplicação que só está disponível na loja dos E.U.A., mas a sua conta estiver em alemão, o Intune não mostrará essa aplicação.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>São carregadas múltiplas cópias do mesmo programa para iOS comprado em volume
Não clique no botão **Carregar** múltiplas vezes para o mesmo token VPP. Isto irá resultar no carregamento de tokens VPP duplicados e as aplicações irão sincronizar múltiplas vezes para o mesmo token VPP. 

<!-- ## Groups -->

## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Não pode guardar uma política do Windows Information Protection para alguns dispositivos

Para dispositivos não inscritos com o Intune, apenas pode especificar um domínio primário no campo **Identificar Empresa** nas definições de uma política do Windows Information Protection.
Se adicionar domínios adicionais (através de **Definições avançadas** > **Perímetro da rede** > **Adicionar um domínio protegido**), não poderá guardar a política. A mensagem de erro apresentada será alterada em breve para ser mais precisa.

### <a name="cisco-anyconnect-vpn-client-support"></a>Suporte do cliente VPN do Cisco AnyConnect
 
O lançamento mais recente do cliente VPN do Cisco AnyConnect (4.0.07072) não é atualmente compatível com o Intune. Uma atualização do Intune futura irá incluir compatibilidade com esta versão do cliente VPN. Até lá, recomendamos que não atualize o cliente VPN do Cisco AnyConnect e que continue a utilizar a versão existente.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Utilizar o tipo de palavra-passe numérica com dispositivos Mac OS Sierra

Atualmente, se selecionar o **Tipo de palavra-passe necessária** **Numérica** num perfil de restrição de dispositivos para dispositivos Mac OS Sierra, aquela é imposta como **Alfanumérica**. Se pretender utilizar uma palavra-passe numérica com esses dispositivos, não configure esta definição.
Este problema pode ser corrigido numa versão futura do Mac OS.

Para obter mais informações sobre estas definições, veja [Definições de restrição de dispositivos macOS no Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Conformidade

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>As políticas de conformidade do Intune não aparecem na consola nova

As políticas de conformidade que criou no portal clássico são migradas, mas não são apresentadas no portal do Azure devido a alterações de estrutura do portal do Azure. As políticas de conformidade que criou no portal do Intune clássico ainda são impostas, mas tem de vê-las e editá-las no portal clássico do Intune.
Além disso, as novas políticas de conformidade que criar no portal do Azure não são visíveis no portal clássico do Intune.

Para obter mais informações, veja [O que é a conformidade do dispositivo](device-compliance.md).

<!-- ## Enrollment -->


## <a name="data-protection"></a>Proteção de dados

### <a name="ios-app-protection-policies"></a>Políticas de proteção de aplicações para iOS

Pode definir [políticas de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) disponíveis para os utilizadores em dispositivos geridos através de gestão de aplicações móveis (MAM) sem inscrição. Devido a um erro temporário, só pode definir estas políticas para versões do iOS com um único ponto decimal em vez de versões com múltiplos pontos decimais. Em vez de definir uma versão mínima do iOS 10.3.1, irá defini-la para o iOS 10.3. Este problema será resolvido numa futura atualização para o SDK do iOS.


## <a name="administration-and-accounts"></a>Administração e contas

Os Administradores Globais (também designados por Administradores Inquilinos) podem continuar a realizar tarefas diárias de administração sem uma licença separada do Intune ou do Enterprise Mobility Suite (EMS). No entanto, para utilizar o serviço, como, por exemplo, para inscrever os seus próprios dispositivos, um dispositivo da empresa ou utilizar o Portal da Empresa do Intune, precisam de uma licença do Intune ou do EMS.

<!-- ## Additional items -->












 
