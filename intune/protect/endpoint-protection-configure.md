---
title: Configurar definições de proteção de ponto final no Microsoft Intune – Azure | Microsoft Docs
description: Crie definições de proteção de ponto final ao criar um perfil de dispositivo com o Windows 10 ou macOS no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 884e4211a880feb3eb533238a5e7246b2738ce46
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502315"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Adicionar definições de proteção de ponto final no Intune  

Com o Intune, você pode usar perfis de configuração de dispositivo para gerenciar recursos comuns de segurança do Endpoint Protection em dispositivos, incluindo:  
- Firewall   
- BitLocker  
- Permitindo e bloqueando aplicativos  
- Windows Defender e criptografia  

Por exemplo, pode criar um perfil de proteção de ponto final que apenas permita aos utilizadores do macOS instalarem aplicações a partir da Mac App Store. Em alternativa, ative o Windows SmartScreen ao executar aplicações em dispositivos com o Windows 10.  

Antes de criar um perfil, examine os seguintes artigos que detalham as configurações do Endpoint Protection que o Intune pode gerenciar para cada plataforma com suporte:  
   - [Definições do macOS](endpoint-protection-macos.md)  
   - [Definições do Windows 10](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de ponto final  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.  
4. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de ponto final.  
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:  
   - **macOS**  
   - **Windows 10 e posterior**  
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**.  
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. Consulte:  
   - [Definições do macOS](endpoint-protection-macos.md)  
   - [Definições do Windows 10](endpoint-protection-windows-10.md)  

8. Depois de definir as configurações aplicáveis, selecione **criar** na página **Criar perfil** .  

   O perfil é criado e apresentado na página da lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Adicionar regras de firewall personalizadas para dispositivos Windows 10  

Ao configurar o Windows Defender firewall como parte de um perfil que inclui regras do Endpoint Protection para Windows 10, você pode configurar regras personalizadas para firewalls. As regras personalizadas permitem que você expanda o conjunto predefinido de regras de firewall com suporte para o Windows 10.  

Ao planejar perfis com regras de firewall personalizadas, considere as seguintes informações, o que pode afetar a maneira como você opta por agrupar regras de firewall em seus perfis:  
- Cada perfil dá suporte a até 150 regras de firewall. Quando você usa mais de 150 regras, crie perfis adicionais, cada um limitado a 150 regras.  
- Para cada perfil, se uma única regra não for aplicada, todas as regras nesse perfil falharão e nenhuma das regras será aplicada ao dispositivo.  
- Quando uma regra não é aplicada, todas as regras no perfil são relatadas como com falha. O Intune não pode identificar qual regra individual falhou.  

As regras de firewall que o Intune pode gerenciar são detalhadas no [provedor de serviços de configuração do firewall]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) do Windows (CSP). Para examinar a lista de configurações de firewall personalizadas para dispositivos Windows 10 aos quais o Intune dá suporte, consulte [regras de firewall personalizadas](endpoint-protection-windows-10.md#firewall-rules).  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Para adicionar regras de firewall personalizadas a um perfil do Endpoint Protection  

1. No Intune, acesse **configuração do dispositivo** > **perfis** > **Criar perfil**.  

2. Para *plataforma*, selecione **Windows 10 e posterior**e, em seguida, para *tipo de perfil* , selecione **Endpoint Protection**.  

3. Selecione **Windows Defender firewall** para abrir a página de configuração e, para *regras de firewall* , selecione **Adicionar** para abrir a página **criar regra** .  

4. Especifique as configurações para a regra de firewall e, em seguida, selecione **OK** para salvá-la. Para examinar as opções de regra de firewall personalizadas disponíveis na documentação do, consulte [regras de firewall personalizadas](endpoint-protection-windows-10.md#firewall-rules).  

5. Depois de salvar a regra, ela aparece na página do *Windows Defender firewall* na lista de regras.  

6. Para modificar uma regra, selecione a regra na lista para abrir a página **Editar regra** .  

7. Para excluir uma regra de um perfil, selecione as reticências **(...)** da regra e, em seguida, selecione **excluir**.  

8. Para alterar a ordem na qual as regras são exibidas, selecione o ícone de seta para *cima e para baixo* na parte superior da lista de regras.  


## <a name="next-steps"></a>Próximos passos  

Para atribuir um perfil a grupos, veja [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).  
