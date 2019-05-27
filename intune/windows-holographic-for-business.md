---
title: Utilizar dispositivos que executam o Windows Holographic com o Microsoft Intune – Azure | Microsoft Docs
description: Com o Microsoft Intune, pode gerir e realizar diferentes tarefas em dispositivos que executam o Windows Holographic for Business e o HoloLens, incluindo configurar o Portal da Empresa, criar uma política de conformidade, personalizar definições de OMA-URI, implementar aplicações, categorizar dispositivos em grupos, criar perfis, restringir dispositivos, permitir atualizações de software, definir termos e condições, configurar definições de Wi-Fi e VPN e utilizar o Hello para Empresas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a10fa6983b8e8c34a1844c647d952ca8cbf0730c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050160"
---
# <a name="manage-and-use-different-device-management-features-on-windows-holographic-and-hololens-devices-with-intune"></a>Gerir e utilizar funcionalidades de gestão de dispositivos diferentes no Windows Holographic e dispositivos HoloLens com o Intune

O Microsoft Intune inclui muitos recursos para ajudar a gerir dispositivos que executam o Windows Holographic for Business, tais como o [Microsoft HoloLens](https://docs.microsoft.com/hololens/). Ao utilizar o Intune, pode confirmar que os dispositivos estão em conformidade com as regras da sua organização e pode personalizar o dispositivo ao adicionar uma VPN ou um perfil Wi-Fi. Outra funcionalidade importante é utilizar o dispositivo como um quiosque e executar uma aplicação específica ou um conjunto específico de aplicações.

As tarefas neste artigo ajudam-no a gerir, personalizar e proteger os seus dispositivos ao executar o Windows Holographic for Business, incluindo atualizações de software e ao utilizar o Windows Hello for Business.

Para utilizar dispositivos Windows Holographic com o Intune, crie um perfil de Atualização de Edição. Este perfil de atualização atualiza os dispositivos do Windows Holographic para o Windows Holographic for Business. Para o Microsoft HoloLens, pode comprar a edição Commercial Suite para obter a licença necessária para a atualização. Para obter mais informações, veja [Atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business](holographic-upgrade.md).

## <a name="azure-active-directory"></a>Azure Active Directory

O Azure Active Directory (AD) é um ótimo recurso para o ajudar a gerir e controlar os seus dispositivos com o Windows Holographic for Business. Com o Intune e o Azure AD, pode: 

- **[Associar dispositivos ao Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)**: No Azure Active Directory (AD), pode adicionar os seus dispositivos, Windows 10 pertencentes no trabalho, incluindo dispositivos que executam o Windows Holographic for Business. Esta funcionalidade permite que o Azure AD controle o dispositivo. Ajuda a confirmar que os seus utilizadores estão a aceder aos recursos da empresa a partir de dispositivos que cumprem as normas de segurança e conformidade que estabeleceu.

  [Gestão de dispositivos no Azure AD](https://docs.microsoft.com/azure/active-directory/devices/overview) fornece mais detalhes.

- **[Inscrição em massa para dispositivos Windows](windows-bulk-enroll.md)**: Pode aderir a grande número de novos dispositivos Windows para o Azure Active Directory (AD) e o Intune. Esta funcionalidade chama-se inscrição em massa e utiliza pacotes de aprovisionamento. Estes pacotes associam os dispositivos com o Windows Holographic for Business ao seu inquilino do Azure AD e inscrevem-nos no Intune.

## <a name="company-portal"></a>Portal da Empresa
**[Configurar a aplicação Portal da Empresa](company-portal-app.md)**

O Intune inclui a aplicação Portal da Empresa para que os utilizadores acedam aos dados da empresa, inscrevam dispositivos, instalem aplicações, contactem o respetivo departamento de TI, entre outros. Pode personalizar a aplicação Portal da Empresa para os seus dispositivos com o Windows Holographic for Business.

Com a aplicação Portal da Empresa, também pode realizar as seguintes ações:

- [Remover um dispositivo do Intune](/intune-user-help/unenroll-your-device-from-intune-windows) através da aplicação Definições ou da aplicação Portal da Empresa
- [Mudar o nome de um dispositivo](/intune-user-help/rename-your-device-cpapp)
- [Instalar aplicações](/intune-user-help/install-apps-cpapp-windows) num dispositivo
- [Sincronizar dispositivos manualmente](/intune-user-help/sync-your-device-manually-windows) a partir da aplicação Definições ou da aplicação Portal da Empresa

## <a name="compliance-policy"></a>Política de conformidade
**[Criar uma política de conformidade de dispositivo](compliance-policy-create-windows.md)**

As políticas de conformidade são regras e definições que os dispositivos têm de cumprir para estarem em conformidade. Utilize estas políticas com acesso condicional para bloquear o acesso a recursos da empresa a dispositivos que não estão em conformidade. No Intune, crie políticas de conformidade para permitir ou bloquear o acesso a dispositivos com o Windows Holographic for Business. Por exemplo, pode criar uma política que exija que o Bitlocker esteja ativado.

Veja também **[Introdução às políticas de conformidade](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Implementar e gerir aplicações
**[Adicionar aplicações ao Intune](apps-add.md)**

Com o Intune, pode adicionar aplicações aos seus dispositivos com o Windows Holographic for Business. Existem várias formas de implementar aplicações, incluindo:

- [Adicionar aplicações da Microsoft Store](store-apps-windows.md)
- [Adicionar aplicações que cria](lob-apps-windows.md)
- [Atribuir aplicações a grupos](apps-deploy.md)

O Microsoft Intune pode implementar Aplicações Universais do Windows para dispositivos Microsoft HoloLens com o Windows Holographic for Business. Pode carregar diretamente os pacotes de aplicações no Intune no portal do Azure ou implementá-los a partir da Microsoft Store para Empresas. Para obter mais informações sobre as áreas relacionadas, veja os seguintes artigos:
- Para implementar aplicações de Linha de Negócio (LOB) através do portal do Azure do Intune, veja [Como adicionar aplicações de linha de negócios (LOB) Windows ao Microsoft Intune](lob-apps-windows.md).

    > [!NOTE]
    > O Intune permite um tamanho de pacote máximo de 8 GB. Este tamanho de pacote só está disponível para as aplicações LOB carregadas para o Intune.

- Para implementar aplicações com o Microsoft Store for Business, veja [Como gerir aplicações compradas na Microsoft Store para Empresas com o Microsoft Intune](windows-store-for-business.md). 
- Para saber mais sobre a gestão de aplicações com o Microsoft Intune, veja [O que é a gestão de aplicações no Microsoft Intune?](app-management.md).
- Para saber mais sobre como desenvolver aplicações do Microsoft HoloLens, veja [Mixed reality apps for Microsoft HoloLens](https://www.microsoft.com/hololens/apps) (Aplicações de realidade mista do Microsoft HoloLens). 

> [!NOTE]
> Os dispositivos HoloLens com o Windows 10 Holographic for Business 1607 não suportam aplicações licenciadas online da Microsoft Store para Empresas. Para saber mais, veja [Install apps on HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps) (Instalar aplicações no HoloLens).

## <a name="device-actions"></a>Ações do dispositivo
O Intune tem algumas ações incorporadas que permitem que os administradores de TI realizem diferentes tarefas, localmente no dispositivo ou remotamente através do Intune no portal do Azure. Os utilizadores também podem emitir um comando remoto a partir do Portal da Empresa do Intune para dispositivos pessoais inscritos no Intune.

Ao utilizar dispositivos com o Windows Holographic for Business, pode realizar as seguintes ações: 

- **[Wipe](devices-wipe.md#wipe)**: O **apagar** ação remove o dispositivo do Intune e restaura as predefinições de fábrica do dispositivo. Utilize esta ação antes de dar o dispositivo a um novo utilizador ou se o dispositivo for perdido ou roubado.

- **[Retire](devices-wipe.md#retire)**: O **extinguir** ação remove o dispositivo do Intune. Também remove os dados da aplicação gerida, as definições e os perfis de e-mail atribuídos pelo Intune. Os dados pessoais do utilizador permanecem no dispositivo.

- **[Sincronizar dispositivos para obter as políticas e ações mais recentes](device-sync.md)**: O **sincronização** ação força o dispositivo para dar entrada imediatamente no Intune. Quando um dispositivo comunica com o Intune, recebe imediatamente todas as ações ou políticas pendentes que tenham sido atribuídas ao mesmo. Esta funcionalidade ajuda a validar e resolver problemas de políticas que atribuiu, sem esperar pela próxima comunicação agendada.

O tópico **[O que é a gestão de dispositivos do Microsoft Intune?](device-management.md)** é um bom recurso para saber mais sobre como gerir dispositivos com o portal do Azure. 

## <a name="device-categories-and-groups"></a>Grupos e categorias de dispositivos
**[Categorizar dispositivos em grupos](device-group-mapping.md)**

Com o Intune, pode criar categorias de dispositivos para adicionar automaticamente dispositivos a grupos com base em categorias que cria, tal como Vendas, Contabilidade, Recursos Humanos e por aí adiante. A ideia é simplificar a gestão dos seus dispositivos com o Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Perfis de configuração de dispositivos 
**[Introdução aos perfis de configuração](device-profiles.md) e [criar o seu próprio perfil](device-profile-create.md)**

O Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são geridas com perfis. Por exemplo, pode criar um perfil que ativa o Cortana ou utilizar o Windows Defender Smart Screen nos seus dispositivos com o Windows Holographic for Business.

Nos seus perfis, pode utilizar definições de OMA-URI para personalizar algumas definições, criar restrições de dispositivos e configurar uma rede privada virtual (VPN) e Wi-Fi.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Definições personalizadas do dispositivo](custom-settings-windows-holographic.md)

Para configurar definições de OMA-URI (Open Mobile Alliance Uniform Resource Identifier), pode criar um perfil personalizado no Intune. Utilize as definições de OMA-URI para controlar diferentes funcionalidades nos seus dispositivos com o Windows Holographic for Business, tal como ativar a VPN ou procurar atualizações no Microsoft Update.

#### <a name="configure-kiosk-modekiosk-settings-holographicmd"></a>[Configurar o modo de quiosque](kiosk-settings-holographic.md)

Com as funcionalidades de PC partilhadas ou de convidado disponíveis no Intune, pode configurar dispositivos com o Windows Holographic for Business para que sejam executados como um quiosque. Estes dispositivos podem executar uma aplicação (modo de quiosque de aplicação única) ou múltiplas aplicações (modo de quiosque de várias aplicações).

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Restrições de dispositivos](device-restrictions-windows-holographic.md)

As restrições de dispositivos permitem-lhe controlar diferentes definições e funcionalidades nos seus dispositivos, incluindo exigir uma palavra-passe, instalar aplicações da [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), ativar o Bluetooth, entre outros. Estas restrições são criadas num perfil do Intune. Este perfil pode ser aplicado a múltiplos dispositivos com o Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Configurar a VPN](vpn-settings-configure.md)

As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. No Intune, pode criar um perfil VPN que inclui definições específicas para os seus dispositivos com o Windows Holographic for Business. Por exemplo, pode criar um perfil VPN para que todos os dispositivos com o Windows Holographic for Business utilizem a VPN do Citrix como o tipo de ligação.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Configurar Wi-Fi](wi-fi-settings-configure.md)

Também pode criar um perfil de Wi-Fi no Intune para atribuir definições de rede sem fios aos seus dispositivos com o Windows Holographic for Business. Quando atribui um perfil de Wi-Fi, os seus utilizadores finais obtêm acesso de rede empresarial, sem qualquer configuração de rede. Por exemplo, pode criar uma rede Wi-Fi dedicada apenas para os seus dispositivos com o Windows Holographic for Business.

## <a name="shared-multi-user-devices"></a>Shared multi-user devices (Dispositivos multiutilizador partilhados)
[Dispositivos partilhados](shared-user-device-settings-windows-holographic.md)

Dispositivos que executam o Windows Holographic for Business, como o Microsoft HoloLens, podem ter vários utilizadores. O Intune inclui definições para controlar diferentes funcionalidades nestes dispositivos partilhados, como gerenciamento de energia, a utilizar o armazenamento local e a gestão de contas. Os perfis de configuração também podem ser aplicados a dispositivos com sistemas operativos diferentes. Por exemplo, o grupo de dispositivos pode ter dispositivos que executam o RS2 e RS3 no mesmo grupo.

## <a name="software-updates"></a>Atualizações de software
**[Gerir atualizações de software](windows-update-for-business-configure.md)**

O Intune inclui uma funcionalidade denominada cadência de atualizações para dispositivos com o Windows 10. Esta cadência de atualizações inclui um grupo de definições que determinam como as atualizações são instaladas. Por exemplo, pode criar uma janela de manutenção para instalar atualizações ou pode optar por reiniciar após as atualizações serem instaladas. Uma cadência de atualizações pode ser aplicada a múltiplos dispositivos com o Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Termos e condições
**[Definir os termos e condições da sua empresa para o acesso dos utilizadores](terms-and-conditions-create.md)**

Antes de os utilizadores inscreverem dispositivos e acederem às aplicações da sua empresa, incluindo ao e-mail, pode exigir que os utilizadores aceitem os termos e condições da sua empresa. No Intune, defina a forma como os termos e condições são apresentados no Portal da Empresa e atribua estes termos e condições a dispositivos com o Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas
**[Utilizar o Windows Hello para Empresas](windows-hello.md)**

O Hello para Empresas é um método de início de sessão alternativo que utiliza uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual. Com o Hello para Empresas, os seus dispositivos com o Windows Holographic for Business podem iniciar sessão com um PIN com um comprimento mínimo definido por si.
