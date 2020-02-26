---
title: Implementação de aplicações do Windows 10 utilizando o Microsoft Intune
titleSuffix: ''
description: Conheça os cenários de implementação de aplicações do Windows 10 disponíveis com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7251a2db0c36db9d01e51ca8fc62bd4e072d80e6
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609220"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Implementação de aplicações do Windows 10 utilizando o Microsoft Intune 

O Microsoft Intune suporta uma variedade de tipos de aplicações e cenários de implementação em dispositivos Windows 10. Depois de adicionar uma aplicação ao Intune, pode atribuí-la a utilizadores e dispositivos. Este artigo fornece mais detalhes sobre os cenários suportados pelo Windows 10, e também cobre detalhes chave para notar quando está a implementar aplicações para o Windows. 

As aplicações de linha de negócio (LOB) e as aplicações da Microsoft Store para Empresas são os tipos de aplicações suportadas em dispositivos com o Windows 10. As extensões de ficheiros para aplicações do Windows incluem .msi, .appx e .appxbundle.  

> [!Note]
> Para implementar aplicações modernas, precisa pelo menos:
> - Para o Windows 10 1803: [23 de maio de 2018 – KB4100403 (Compilação 17134.81 do SO)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Para o Windows 10 1709: [21 de junho de 2018 – KB4284822 (Compilação 16299.522 do SO)](https://support.microsoft.com/help/4284822).
>
> Apenas o Windows 10 1803 e posteriormente suportam a instalação de apps quando não há nenhum utilizador principal associado.
>
> A implementação de aplicações LOB não é suportada em dispositivos que executam edições do Windows 10 Home.

## <a name="supported-windows-10-app-types"></a>Tipos de aplicativos suportados do Windows 10

Os tipos de aplicações específicos são suportados com base na versão do Windows 10 que os seus utilizadores estão a executar. A tabela seguinte fornece o tipo de aplicação e a capacidade de suporte do Windows 10.

| Tipo de aplicação | Casa | Pro | Empresa | Enterprise | Educação | Modo S | HoloLens<sup>1 | Surface Hub | WCOS | Mobile |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  . MSI | Não | Sim | Sim | Sim | Sim | Não | Não | Não | Não | Não |
| . IntuneWin | Não | Sim | Sim | Sim | Sim | 19H2+ | Não | Não | Não | Não |
| Escritório C2R | Não | Sim | Sim | Sim | Sim | RS4+ | Não | Não | Não | Não |
| LOB: APPX/MSIX | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim |
| MSFB Offline | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim |
| MSFB Online | Sim | Sim | Sim | Sim | Sim | Sim | RS4+ | Não | Sim | Sim |
| Aplicações na Web | Sim | Sim | Sim | Sim | Sim | Sim | Sim<sup>2 | Sim<sup>2 | Sim | Sim<sup>2 |
| Link da loja | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim | Sim |

<sup>1</sup> Para desbloquear a gestão de aplicações, atualize o seu dispositivo HoloLens para [Holographic for Business](../fundamentals/windows-holographic-for-business.md).<br />
<sup>2</sup> Lançamento apenas do Portal da Empresa.

> [!NOTE]
> Todos os tipos de aplicativos do Windows requerem inscrição.

## <a name="windows-10-lob-apps"></a>Aplicativos Lob do Windows 10

Pode assinar e carregar aplicações lob do Windows 10 para a consola intune. Estas podem incluir aplicações modernas, como aplicações universal Windows Platform (UWP) e Pacotes de Aplicações Windows (AppX), bem como aplicações Win 32, como ficheiros simples de pacotes de instalação da Microsoft (MSI). O administrador deve carregar manualmente e implementar atualizações de aplicações LOB. Estas atualizações são automaticamente instaladas em dispositivos de utilizador que tenham instalado a aplicação. Não é necessária nenhuma intervenção do utilizador e o utilizador não tem controlo sobre as atualizações. 

## <a name="microsoft-store-for-business-apps"></a>Aplicações da Microsoft Store para Empresas

As aplicações microsoft Store for Business são aplicações modernas, compradas no portal de administração da Microsoft Store para empresas. São então sincronizados com a Microsoft Intune para gestão. As aplicações podem ser licenciadas online ou offline. A Microsoft Store gere diretamente as atualizações, sem nenhuma ação adicional exigida pelo administrador. Também pode prevenir atualizações para aplicações específicas utilizando um identificador de recursos uniformes personalizado (URI). Para obter mais informações, veja [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (Gestão de aplicações empresariais – impedir as atualizações automáticas da aplicação). O utilizador também pode desativar atualizações para todas as aplicações da Microsoft Store for Business no dispositivo. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Categorize a Microsoft Store para aplicações empresariais 
Para categorizar as aplicações da Microsoft Store para as empresas: 

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações.** 
3. Selecione uma aplicação Microsoft Store for Business. Em seguida, selecione **Propriedades** > categoria **de**informações de **aplicações** > . 
4. Selecione uma categoria.

## <a name="install-apps-on-windows-10-devices"></a>Instale aplicações em dispositivos Windows 10
Dependendo do tipo de aplicação, pode instalar a aplicação num dispositivo Windows 10 de uma de duas formas:

- **Contexto**do utilizador : Quando uma aplicação é implementada no contexto do utilizador, a aplicação gerida é instalada para esse utilizador no dispositivo quando o utilizador insere no dispositivo. Note que a instalação da aplicação não é bem sucedida até que o utilizador inste no dispositivo. 
  - As aplicações LOB modernas e as aplicações Microsoft Store for Business (online e offline) podem ser implementadas no contexto do utilizador. As aplicações suportam as intenções necessárias e disponíveis.
  - As aplicações Win32 construídas como Modo utilizador ou Modo Dual podem ser implementadas no contexto do utilizador e suportar as intenções necessárias e disponíveis. 
- **Contexto**do dispositivo : Quando uma aplicação é implantada no contexto do dispositivo, a aplicação gerida é instalada diretamente no dispositivo pela Intune.
  - Apenas aplicações lob modernas e aplicações licenciadas offline Microsoft Store para empresas podem ser implementadas no contexto do dispositivo. Estas aplicações apenas suportam a intenção necessária.
  - As aplicações Win32 construídas como Modo Máquina ou Modo Dual podem ser implementadas no contexto do dispositivo, e suportam apenas a intenção necessária.

> [!NOTE]
> Para aplicações Win32 construídas como aplicações dual mode, o administrador deve escolher se a aplicação funcionará como uma aplicação modo utilizador ou modo máquina para todas as atribuições associadas a essa instância. O contexto de implantação não pode ser alterado por atribuição.  

As aplicações só podem ser instaladas no contexto do dispositivo quando suportadas pelo dispositivo e pelo tipo de aplicação Intune. Pode instalar os seguintes tipos de aplicações no contexto do dispositivo e atribuir estas aplicações a um grupo de dispositivos:

- Aplicativos Win32
- Microsoft Store licenciada offline para aplicações empresariais
- Aplicativos LOB (MSI, APPX e MSIX)
- Office 365 ProPlus

As aplicações Do Windows LOB (especificamente APPX e MSIX) e Microsoft Store for Business (aplicações Offline) que selecionou para instalar no contexto do dispositivo devem ser atribuídas a um grupo de dispositivos. A instalação falha se uma destas aplicações for implementada no contexto do utilizador. O seguinte estado e erro aparece na consola de administração:
  - Estado: falha.
  - Erro: Um utilizador não pode ser alvo com uma instalação de contexto do dispositivo.

> [!IMPORTANT]
> Quando utilizado em combinação com um cenário de fornecimento de luvas brancas Autopilot, não existe qualquer requisito para aplicações LOB e aplicações Microsoft Store para negócios implementadas no contexto do dispositivo para direcionar um grupo de dispositivos. Para mais informações, consulte a [implementação](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove)da luva branca Do Windows Autopilot .

> [!Note]
> Depois de guardar uma atribuição de aplicativos com uma implementação específica, não pode alterar o contexto para essa atribuição, exceto para aplicações modernas. Para aplicações modernas, pode alterar o contexto do contexto do utilizador para o contexto do dispositivo. 

Se houver um conflito nas políticas num único utilizador ou dispositivo, aplicam-se as seguintes prioridades:
- Uma política de contexto do dispositivo tem uma prioridade mais alta do que uma política de contexto de utilizador. 
- Uma política de instalação tem uma prioridade mais alta do que uma política de desinstalação.

Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md). Para obter mais informações sobre tipos de aplicações no Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicativos a grupos com o Microsoft Intune](apps-deploy.md)
- [Como monitorizar aplicações](apps-monitor.md)
