---
title: Gerir dispositivos que executam o Windows Holographic com o Microsoft Intune – Azure | Microsoft Docs
description: Com o Microsoft Intune, pode realizar diferentes tarefas em dispositivos que executam o Windows Holographic for Business, incluindo configurar o Portal da Empresa, criar uma política de conformidade, personalizar definições de OMA-ORI, implementar aplicações, categorizar dispositivos em grupos, criar perfis, restringir dispositivos, permitir atualizações de software, definir termos e condições, configurar definições de Wi-Fi e VPN e utilizar o Hello para Empresas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18f86580fc4c80fade7aeaa9678e9d8edac9a53e
ms.sourcegitcommit: b57be56524ddb5026fab94f7638dc516ed118325
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/03/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>Personalizar dispositivos que executam o Windows Holographic com o Intune

O Microsoft Intune suporta dispositivos com o Windows Holographic for Business, como o [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/).

Para gerir dispositivos que executam o Windows Holographic com o Microsoft Intune, tem de criar um Perfil de Atualização de Edição. Este perfil de atualização atualiza os dispositivos do Windows Holographic para o Windows Holographic for Business. Para o Microsoft HoloLens, pode comprar a edição Commercial Suite para obter a licença necessária para a atualização. Para obter mais informações, veja [Atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business](holographic-upgrade.md).

Para ajudar a gerir e personalizar os seus dispositivos com o Windows Holographic for Business, pode utilizar as tarefas neste artigo. Por exemplo, pode gerir atualizações de software, configurar definições de VPN, entre outros.

## <a name="azure-active-directory"></a>Azure Active Directory

O Azure Active Directory (AD) é um ótimo recurso para o ajudar a gerir e controlar os seus dispositivos com o Windows Holographic for Business. Com o Intune e o Azure AD, pode: 

- **[Configurar dispositivos associados ao Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup)**: no Azure Active Directory (AD), pode adicionar os seus dispositivos com o Windows 10 do trabalho, incluindo dispositivos com o Windows Holographic for Business. Esta funcionalidade permite que o Azure AD controle o dispositivo. Ajuda a assegurar que os seus utilizadores estão a aceder aos seus recursos da empresa a partir de dispositivos que cumpram as normas de segurança e conformidade que estabeleceu.

  O tópico [Introdução à gestão de dispositivos no Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction) fornece mais detalhes.

- **[Inscrever dispositivos Windows em massa](windows-bulk-enroll.md)**: pode associar inúmeros dispositivos Windows novos ao Azure Active Directory e ao Intune. Esta funcionalidade chama-se inscrição em massa e utiliza pacotes de aprovisionamento. Estes pacotes associam os dispositivos com o Windows Holographic for Business ao seu inquilino do Azure AD e inscrevem-nos no Intune.

## <a name="company-portal"></a>Portal da Empresa
**[Configurar a aplicação Portal da Empresa](company-portal-app.md)**

O Intune inclui o Portal da Empresa, que é onde os utilizadores acedem aos dados da empresa, inscrevem dispositivos, instalam aplicações, contactam o seu departamento de TI, entre outros. Pode personalizar a aplicação Portal da Empresa para os seus dispositivos com o Windows Holographic for Business.

## <a name="compliance-policy"></a>Política de conformidade
**[Criar uma política de conformidade de dispositivo](compliance-policy-create-windows.md)**

As políticas de conformidade são regras e definições que os dispositivos têm de cumprir para estarem em conformidade. Pode utilizar estas políticas com acesso condicional para bloquear o acesso a recursos da empresa para dispositivos que não estão em conformidade. No Intune, pode criar políticas de conformidade para permitir ou bloquear o acesso a dispositivos com o Windows Holographic for Business. Por exemplo, pode criar uma política que exija que o Bitlocker esteja ativado.

Veja também **[Introdução às políticas de conformidade](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Implementar e gerir aplicações
**[Adicionar aplicações ao Intune](apps-add.md)**

Com o Intune, pode adicionar aplicações aos seus dispositivos com o Windows Holographic for Business. Existem várias formas de implementar aplicações, incluindo:

- [Adicionar aplicações da Microsoft Store](store-apps-windows.md)
- [Adicionar aplicações que cria](lob-apps-windows.md)
- [Atribuir aplicações a grupos](apps-deploy.md)

O Microsoft Intune pode implementar Aplicações Universais do Windows para dispositivos Microsoft HoloLens com o Windows Holographic for Business. Pode carregar diretamente os pacotes de aplicações no portal do Azure do Intune ou implementá-los a partir do Microsoft Store for Business. Para obter mais informações sobre as áreas relacionadas, veja o seguinte:
- Para implementar aplicações de Linha de Negócio (LOB) através do portal do Azure do Intune, veja [Como adicionar aplicações de linha de negócios (LOB) Windows ao Microsoft Intune](lob-apps-windows.md).
- Para implementar aplicações com o Microsoft Store for Business, veja [Como gerir aplicações compradas na Microsoft Store para Empresas com o Microsoft Intune](windows-store-for-business.md). 
- Para saber mais sobre a gestão de aplicações com o Microsoft Intune, veja [O que é a gestão de aplicações no Microsoft Intune?](app-management.md).
- Para saber mais sobre como desenvolver aplicações do Microsoft HoloLens, veja [Mixed reality apps for Microsoft HoloLens](https://www.microsoft.com/hololens/apps) (Aplicações de realidade mista do Microsoft HoloLens). 

> [!NOTE]
> Os dispositivos HoloLens com o Windows 10 Holographic for Business 1607 não suportam aplicações licenciadas online da Microsoft Store para Empresas. Para saber mais, veja [Install apps on HoloLens](https://docs.microsoft.com/en-us/hololens/hololens-install-apps) (Instalar aplicações no HoloLens).

## <a name="device-actions"></a>Ações do dispositivo
O Intune tem algumas ações incorporadas que permitem que os administradores de TI realizem diferentes tarefas, localmente no dispositivo ou remotamente através do Intune no portal do Azure. Os utilizadores também podem emitir um comando remoto a partir do Portal da Empresa do Intune para dispositivos pessoais inscritos no Intune.

Ao utilizar dispositivos com o Windows Holographic for Business, pode realizar as seguintes ações: 

- **[Reposição de dados de fábrica](devices-wipe.md#factory-reset)**: a ação **Reposição de dados de fábrica** remove o dispositivo do Intune e restaura as predefinições de fábrica do dispositivo. Utilize esta ação antes de dar o dispositivo a um novo utilizador ou se o dispositivo for perdido ou roubado.

- **[Remover dados da empresa](devices-wipe.md#remove-company-data)**: a ação **Remover dados da empresa** remove o dispositivo do Intune e os dados de aplicações geridas, definições e perfis de e-mail atribuídos através do Intune. Os dados pessoais do utilizador permanecem no dispositivo.

- **[Sincronizar dispositivos para obter as políticas e ações mais recentes](device-sync.md)**: a ação **Sincronizar** força o dispositivo a comunicar imediatamente com o Intune. Quando um dispositivo comunica com o Intune, recebe imediatamente todas as ações ou políticas pendentes que tenham sido atribuídas ao mesmo. Esta funcionalidade ajuda a validar e resolver problemas de políticas que atribuiu, sem esperar pela próxima comunicação agendada.

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

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Restrições de dispositivos](device-restrictions-windows-holographic.md)

As restrições de dispositivos permitem-lhe controlar diferentes definições e funcionalidades nos seus dispositivos, incluindo exigir uma palavra-passe, instalar aplicações da [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), ativar o Bluetooth, entre outros. Estas restrições são criadas num perfil do Intune. Este perfil pode ser aplicado a múltiplos dispositivos com o Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Configurar a VPN](vpn-settings-configure.md)

As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. No Intune, pode criar um perfil VPN que inclui definições específicas para os seus dispositivos com o Windows Holographic for Business. Por exemplo, pode criar um perfil VPN para que todos os dispositivos com o Windows Holographic for Business utilizem a VPN do Citrix como o tipo de ligação.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Configurar Wi-Fi](wi-fi-settings-configure.md)

Também pode criar um perfil de Wi-Fi no Intune para atribuir definições de rede sem fios aos seus dispositivos com o Windows Holographic for Business. Quando atribui um perfil de Wi-Fi, os seus utilizadores finais obtêm acesso de rede empresarial, sem qualquer configuração de rede. Por exemplo, pode criar uma rede Wi-Fi dedicada apenas para os seus dispositivos com o Windows Holographic for Business.

## <a name="software-updates"></a>Atualizações de software
**[Gerir atualizações de software](windows-update-for-business-configure.md)**

O Intune inclui uma funcionalidade denominada cadência de atualizações para dispositivos com o Windows 10. Esta cadência de atualizações inclui um grupo de definições que determinam como as atualizações são instaladas. Por exemplo, pode criar uma janela de manutenção para instalar atualizações ou pode optar por reiniciar após as atualizações serem instaladas. Uma cadência de atualizações pode ser aplicada a múltiplos dispositivos com o Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Termos e condições
**[Definir os termos e condições da sua empresa para o acesso dos utilizadores](terms-and-conditions-create.md)**

Antes de os utilizadores conseguirem inscrever dispositivos e aceder às aplicações da empresa, incluindo e-mail, pode exigir que os utilizadores aceitem os termos e condições da sua empresa. No Intune, pode definir como os termos e condições são apresentados no Portal da Empresa e também atribuir estes termos e condições a dispositivos com o Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas
**[Utilizar o Windows Hello para Empresas](windows-hello.md)**

O Hello para Empresas é um método de início de sessão alternativo que utiliza uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual. Com o Hello para Empresas, os seus dispositivos com o Windows Holographic for Business podem iniciar sessão com um PIN com um comprimento mínimo definido por si.
