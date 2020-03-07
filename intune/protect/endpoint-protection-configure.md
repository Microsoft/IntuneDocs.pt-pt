---
title: Configurar definições de proteção de ponto final no Microsoft Intune – Azure | Microsoft Docs
description: Crie definições de proteção de ponto final ao criar um perfil de dispositivo com o Windows 10 ou macOS no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: 45cdbfe98bca8f7b0e307ed47ad3f78193e6d04c
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78370101"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Adicionar definições de proteção de ponto final no Intune

Com o Intune, pode utilizar perfis de configuração do dispositivo para gerir funcionalidades comuns de proteção de pontos finais nos dispositivos, incluindo:

- Firewall
- BitLocker
- Permitir e bloquear aplicações
- Microsoft Defender e encriptação

Por exemplo, pode criar um perfil de proteção de ponto final que apenas permita aos utilizadores do macOS instalarem aplicações a partir da Mac App Store. Em alternativa, ative o Windows SmartScreen ao executar aplicações em dispositivos com o Windows 10.

Antes de criar um perfil, reveja os seguintes artigos que detalham as definições de proteção de pontofinal Que intune pode gerir para cada plataforma suportada:

- [Definições do macOS](endpoint-protection-macos.md)
- [Definições do Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de ponto final

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

3. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de ponto final.

4. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:

   - **macOS**
   - **Windows 10 e posterior**

5. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**.

6. Consoante a plataforma que escolheu, as definições que pode configurar variam. Consulte:

   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)

7. Depois de configurar as definições aplicáveis, selecione **Criar** na página de **perfil Criar.**

   O perfil é criado e apresentado na página da lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Adicione regras personalizadas de Firewall para dispositivos Windows 10

Quando configurar o Microsoft Defender Firewall como parte de um perfil que inclui regras de proteção de pontos finais para o Windows 10, pode configurar regras personalizadas para Firewalls. As regras personalizadas permitem expandir-se no conjunto pré-definido de regras de Firewall suportadas para o Windows 10.

Quando planeia perfis com regras personalizadas de Firewall, considere as seguintes informações, que podem afetar a forma como escolhe agrupar regras de firewall nos seus perfis:

- Cada perfil suporta até 150 regras de firewall. Quando se utiliza mais de 150 regras, crie perfis adicionais, cada um limitado a 150 regras.

- Para cada perfil, se uma única regra não for aplicável, todas as regras desse perfil são falhadas e nenhuma das regras é aplicada ao dispositivo.

- Quando uma regra não se aplica, todas as regras do perfil são reportadas como falhadas. Intune não pode identificar que regra individual falhou.  

As regras de Firewall que o Intune pode gerir são detalhadas no fornecedor de serviços de [configuração]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) do Windows Firewall (CSP). Para rever a lista de definições de firewall personalizadas para dispositivos Windows 10 que intune suporta, consulte [as regras de Firewall personalizadas](endpoint-protection-windows-10.md#firewall-rules).

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Para adicionar regras de firewall personalizadas a um perfil de proteção Endpoint

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > perfis de **configuração** > **criar perfil**.

3. Para *a Plataforma,* selecione **o Windows 10 e, mais tarde,** e, em seguida, para *o tipo de perfil* selecione **proteção endpoint**.

4. Selecione **Microsoft Defender Firewall** para abrir a página de configuração e, em seguida, para as regras de *Firewall* selecione **Adicionar** para abrir a página **'Criar Regra'.**

5. Especifique as definições para a regra firewall e, em seguida, selecione **OK** para salvá-la. Para rever as opções de regra de firewall personalizadas disponíveis na documentação, consulte [as regras de Firewall personalizadas](endpoint-protection-windows-10.md#firewall-rules).

6. Depois de guardar a regra, aparece na página *Microsoft Defender Firewall* na lista de regras.

7. Para modificar uma regra, selecione a regra da lista, para abrir a página 'Regra de **Edição'.**

8. Para eliminar uma regra de um perfil, selecione a elipse **(...)** para a regra e, em seguida, selecione **Delete**.

9. Para alterar a ordem em que as regras se exibem, selecione a *seta para cima, para baixo o* ícone da seta no topo da lista de regras.

## <a name="next-steps"></a>Próximos passos

Para atribuir um perfil a grupos, veja [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).
