---
title: Implantação de aplicativo do Windows 10 usando Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre os cenários de implantação de aplicativos do Windows 10 disponíveis com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: c9d792bd07ae8d7d712748874d64314dd258c5e8
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563950"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Implantação de aplicativo do Windows 10 usando Microsoft Intune 

O Microsoft Intune dá suporte a uma variedade de tipos de aplicativos e cenários de implantação em dispositivos Windows 10. Depois de adicionar uma aplicação ao Intune, pode atribuí-la a utilizadores e dispositivos. Este artigo fornece mais detalhes sobre os cenários com suporte do Windows 10 e também aborda os principais detalhes a serem observados quando você estiver implantando aplicativos no Windows. 

As aplicações de linha de negócio (LOB) e as aplicações da Microsoft Store para Empresas são os tipos de aplicações suportadas em dispositivos com o Windows 10. As extensões de arquivo para aplicativos do Windows incluem. msi,. Appx e. appxbundle.  

> [!Note]
> Para implantar aplicativos modernos, você precisa de pelo menos:
> - Para o Windows 10 1803: [23 de maio de 2018 – KB4100403 (Compilação 17134.81 do SO)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Para o Windows 10 1709: [21 de junho de 2018 – KB4284822 (Compilação 16299.522 do SO)](https://support.microsoft.com/help/4284822).
>
> Somente o Windows 10 1803 e versões posteriores dão suporte à instalação de aplicativos quando não há um usuário primário associado.
>
> Não há suporte para a implantação de aplicativos LOB em dispositivos que executam o Windows 10 Home Editions.

## <a name="windows-10-lob-apps"></a>Aplicativos de LOB do Windows 10

Você pode assinar e carregar aplicativos LOB do Windows 10 no console de administração do Intune. Eles podem incluir aplicativos modernos, como aplicativos Plataforma Universal do Windows (UWP) e pacotes de aplicativos do Windows (AppX), bem como aplicativos Win 32, como arquivos de pacote do Microsoft Installer (MSI) simples. O administrador deve carregar e implantar manualmente as atualizações de aplicativos LOB. Essas atualizações são instaladas automaticamente em dispositivos de usuário que instalaram o aplicativo. Nenhuma intervenção do usuário é necessária e o usuário não tem controle sobre as atualizações. 

## <a name="microsoft-store-for-business-apps"></a>Aplicações da Loja Microsoft para Empresas

Microsoft Store para aplicativos de negócios são aplicativos modernos, adquiridos no portal de administração do Microsoft Store for Business. Em seguida, eles são sincronizados para Microsoft Intune para gerenciamento. Os aplicativos podem ser licenciados online ou offline. O Microsoft Store gerencia atualizações diretamente, sem nenhuma ação adicional exigida pelo administrador. Você também pode impedir atualizações para aplicativos específicos usando um URI (Uniform Resource Identifier) personalizado. Para obter mais informações, veja [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (Gestão de aplicações empresariais – impedir as atualizações automáticas da aplicação). O usuário também pode desabilitar atualizações para todos os Microsoft Store para aplicativos de negócios no dispositivo. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Categorizar Microsoft Store para aplicativos de negócios 
Para categorizar Microsoft Store para aplicativos de negócios: 

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos**. 
3. Selecione um Microsoft Store para o aplicativo de negócios. Em seguida, selecione **propriedades** > **informações do aplicativo** > **categoria**. 
4. Selecione uma categoria.

## <a name="install-apps-on-windows-10-devices"></a>Instalar aplicativos em dispositivos Windows 10
Dependendo do tipo de aplicativo, você pode instalar o aplicativo em um dispositivo Windows 10 de uma das duas maneiras:

- **Contexto do usuário**: quando um aplicativo é implantado no contexto do usuário, o aplicativo gerenciado é instalado para esse usuário no dispositivo quando o usuário faz logon no dispositivo. Observe que a instalação do aplicativo não tem sucesso até que o usuário entre no dispositivo. 
  - Aplicativos de linha de negócios modernos e Microsoft Store para aplicativos de negócios (online e offline) podem ser implantados no contexto do usuário. Os aplicativos dão suporte às tentativas obrigatórias e disponíveis.
  - Os aplicativos Win32 criados como modo de usuário ou modo duplo podem ser implantados no contexto do usuário e dar suporte às tentativas necessárias e disponíveis. 
- **Contexto do dispositivo**: quando um aplicativo é implantado no contexto do dispositivo, o aplicativo gerenciado é instalado diretamente no dispositivo pelo Intune.
  - Somente os aplicativos de linha de negócios modernos e os Microsoft Store licenciados offline para aplicativos de negócios podem ser implantados no contexto do dispositivo. Esses aplicativos só dão suporte à intenção necessária.
  - Os aplicativos Win32 criados como modo de máquina ou modo duplo podem ser implantados no contexto do dispositivo e dar suporte apenas à intenção necessária.

> [!NOTE]
> Para aplicativos Win32 criados como aplicativos de modo duplo, o administrador deve escolher se o aplicativo funcionará como um modo de usuário ou aplicativo de modo de máquina para todas as atribuições associadas a essa instância. O contexto de implantação não pode ser alterado por atribuição.  

Quando um aplicativo é implantado no contexto do dispositivo, a instalação só é realizada com sucesso quando é direcionada a um dispositivo que dá suporte ao contexto do dispositivo. Além disso, implementar no contexto do dispositivo suporta as seguintes condições:
- Se um aplicativo for implantado no contexto do dispositivo e for direcionado a um usuário, a instalação falhará. O status e o erro a seguir aparecem no console do administrador:
  - Estado: falha.
  - Erro: um usuário não pode ser direcionado a uma instalação de contexto de dispositivo.
- Se um aplicativo for implantado no contexto do dispositivo, mas for direcionado a um dispositivo que não dá suporte ao contexto do dispositivo, a instalação falhará. O status e o erro a seguir aparecem no console do administrador:
  - Estado: falha.
  - Erro: esta plataforma não suporta instalações de contexto do dispositivo. 

> [!Note]
> Depois de salvar uma atribuição de aplicativo com uma implantação específica, você não pode alterar o contexto para essa atribuição, exceto para aplicativos modernos. Para aplicativos modernos, você pode alterar o contexto do contexto do usuário para o contexto do dispositivo. 

Se houver um conflito nas políticas em um único usuário ou dispositivo, as seguintes prioridades se aplicarão:
- Uma política de contexto do dispositivo tem uma prioridade mais alta do que uma política de contexto de utilizador. 
- Uma política de instalação tem uma prioridade mais alta do que uma política de desinstalação.

Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md). Para obter mais informações sobre tipos de aplicações no Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicativos a grupos com Microsoft Intune](apps-deploy.md)
- [Como monitorar aplicativos](apps-monitor.md)
