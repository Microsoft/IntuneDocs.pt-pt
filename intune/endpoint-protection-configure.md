---
title: Configurar definições de proteção de ponto final no Microsoft Intune – Azure | Microsoft Docs
description: Crie definições de proteção de ponto final ao criar um perfil de dispositivo com o Windows 10 ou macOS no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: cbac3627a17fb28f7ec0bf06898038a6c6001ac8
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65733046"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Adicionar definições de proteção de ponto final no Intune

Com o Intune, pode utilizar perfis de configuração de dispositivos para gerir recursos de segurança do endpoint protection comuns em dispositivos, incluindo:
- Firewall 
- BitLocker
- Permitir e bloquear aplicações  
- O Windows Defender e encriptação

Por exemplo, pode criar um perfil de proteção de ponto final que apenas permita aos utilizadores do macOS instalarem aplicações a partir da Mac App Store. Em alternativa, ative o Windows SmartScreen ao executar aplicações em dispositivos com o Windows 10.

Antes de criar um perfil, reveja os artigos seguintes esse detalhe que as definições de proteção de ponto final Intune podem gerir para cada plataforma suportada: 
   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de ponto final

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=20909).
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de ponto final.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:
   - **macOS**
   - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**. 
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. Consulte:
   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)  

8. Depois de configurar as definições aplicáveis, selecione **Create** sobre o **criar perfil** página.

   O perfil é criado e apresentado na página da lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Adicionar regras de Firewall personalizadas para dispositivos Windows 10  

Ao configurar a Firewall do Windows Defender como parte de um perfil que inclui regras de proteção de ponto final para o Windows 10, pode configurar regras personalizadas para as Firewalls. Regras personalizadas permitem-lhe expandir o conjunto predefinido de regras de Firewall suportados para o Windows 10.  

Ao planear de perfis com regras de Firewall personalizadas, considere as informações seguintes, que podem afetar como escolher regras de firewall de grupo nos seus perfis:  
- Cada perfil suportar até 150 regras de firewall. Quando usa mais de 150 regras, crie perfis adicionais, cada limitado a 150 regras.  
- Para cada perfil, se uma única regra não será aplicada, todas as regras em que o perfil são falha e nenhuma das regras são aplicadas ao dispositivo.  
- Quando uma regra não consegue aplicar, todas as regras no perfil são reportadas como falhado. Intune não consegue identificar a falha de quais regras individuais. 

As regras de Firewall que o Intune pode gerir são detalhadas em do Windows [fornecedor de serviços de configuração de Firewall]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) (CSP). Para rever a lista de configurações de firewall personalizadas para dispositivos Windows 10 que o Intune suporta, consulte [regras de Firewall personalizadas](endpoint-protection-windows-10.md#custom-firewall-rules).   

#### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Para adicionar regras de firewall personalizadas para um perfil de proteção de ponto final  

1. No Intune, aceda a **configuração do dispositivo** > **perfis** > **criar perfil**.  

2. Para *plataforma*, selecione **Windows 10 e posterior**e, em seguida, para *tipo de perfil* selecionar **Endpoint protection**.  

3. Selecione **Firewall do Windows Defender** para abrir a página de configuração e, em seguida, para *regras de Firewall* selecionar **Add** para abrir o **criar regra**página.  

4. Especifique definições de conjunto para a regra de Firewall e, em seguida, selecione **OK** salvá-lo. Para rever as opções de regra de firewall personalizadas disponíveis na documentação, consulte [regras de Firewall personalizadas](endpoint-protection-windows-10.md#custom-firewall-rules).  

5. Depois de guardar a regra, ele aparece no *Firewall do Windows Defender* página na lista de regras.  

6. Para modificar uma regra, selecione a regra na lista, para abrir o **Editar regra de** página.  

7. Para eliminar uma regra de um perfil, selecione as reticências **(...)**  para a regra e, em seguida, selecione **eliminar**.  

8. Para alterar a ordem na qual as regras de apresentação, selecione o *a seta, a seta para baixo* na parte superior da lista de regras.  





## <a name="next-steps"></a>Passos Seguintes  

Para atribuir um perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).
