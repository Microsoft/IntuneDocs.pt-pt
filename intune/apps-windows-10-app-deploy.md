---
title: Implementação de aplicações para Windows 10 através do Microsoft Intune
titlesuffix: ''
description: Saiba mais sobre os cenários de aplicações para Windows 10 disponíveis com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7508f2c2eca06ceacf203103ab2cad53abc39a65
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347437"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Implementação de aplicações para Windows 10 através do Microsoft Intune 

Atualmente, o Microsoft Intune suporta vários tipos de aplicações e cenários de implementação em dispositivos com o Windows 10. Depois de adicionar uma aplicação ao Intune, pode atribuí-la a utilizadores e dispositivos. As seguintes informações fornecem mais detalhes relacionados com os cenários do Windows 10 suportados. Além disso, as seguintes informações fornecem detalhes importantes a ter em conta quando implementa aplicações para o Windows. 

As aplicações de linha de negócio (LOB) e as aplicações da Microsoft Store para Empresas são os tipos de aplicações suportadas em dispositivos com o Windows 10.

> [!Note]
> A atualização do Windows 10 mínima necessária para implementar aplicações no contexto do dispositivo é a de [23 de maio de 2018 — KB4100403 (Compilação 17134.81 do SO)](https://support.microsoft.com/en-us/help/4100403/windows-10-update-kb4100403).

## <a name="windows-10-line-of-business-apps"></a>Aplicações de linha de negócio do Windows 10

As aplicações LOB para Windows 10 são assinadas e carregadas para a consola de administração do Intune e podem incluir aplicações modernas, como aplicações UWP (Plataforma Universal do Windows) e Pacotes de Aplicações do Windows (AppX), bem como aplicações Win32, como os ficheiros de pacote do Microsoft Installer (MSI) simples. As atualizações das aplicações LOB têm de ser sempre manualmente carregadas e implementadas pelo administrador. As atualizações implementadas são automaticamente instaladas em dispositivos de utilizador final que instalaram a aplicação sem a intervenção do utilizador. O utilizador não tem controlo sobre as atualizações. 

## <a name="microsoft-store-for-business-apps"></a>Aplicações da Loja Microsoft para Empresas

As aplicações da Microsoft Store para Empresas são aplicações modernas compradas a partir do portal de administração da Microsoft Store para Empresas e depois sincronizadas através do Microsoft Intune para gestão. As aplicações podem ser **licenciadas online** ou **licenciadas offline**. As atualizações da Microsoft Store para Empresas são geridas diretamente pela Microsoft Store, sem ser necessária qualquer ação adicional por parte do administrador. O administrador também pode impedir atualizações de determinadas aplicações através do URI (Uniform Resource Identifier) personalizado. Para obter mais informações, veja [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (Gestão de aplicações empresariais – impedir as atualizações automáticas da aplicação). No dispositivo, o utilizador final também pode desativar atualizações para todas as aplicações da Microsoft Store para Empresas no dispositivo. 

## <a name="installing-apps-on-windows-10-devices"></a>Instalar aplicações em dispositivos com o Windows 10
Dependendo do tipo de aplicação, a aplicação pode ser instalada num dispositivo com o Windows 10 através de uma de duas formas:

- **Contexto de Utilizador**: quando uma aplicação for implementada no contexto de utilizador, a aplicação gerida será instalada no dispositivo desse utilizador quando este iniciar sessão no mesmo. Tenha em atenção que a instalação da aplicação não será bem-sucedida até o utilizador iniciar sessão no dispositivo. 
    - As aplicações de linha de negócio e as aplicações empresariais (online e offline) podem ser implementadas no contexto de utilizador e suportarão as intenções Necessário e Disponível.
- **Contexto do Dispositivo**: quando uma aplicação for implementada no contexto do dispositivo, a aplicação gerida será instalada diretamente no dispositivo pelo Intune.
    - Apenas as aplicações de linha de negócio e as aplicações da Microsoft Store para Empresas licenciadas online podem ser implementadas no contexto do dispositivo e só suportarão a intenção Necessário.

> [!Note]
> Implementar o MSI através do MDM no contexto do dispositivo ainda não é suportado em dispositivos com o Windows 10.

Quando uma aplicação for implementada no contexto do dispositivo, a instalação só será bem-sucedida quando direcionada para um dispositivo que suporte o contexto do dispositivo. Além disso, implementar no contexto do dispositivo suporta as seguintes condições:
- Se uma aplicação for implementada no contexto do dispositivo e direcionada para um utilizador, a instalação irá falhar com o seguinte estado e erro apresentados na consola de administração:
    - Estado: falha.
    - Erro: não é possível direcionar para um utilizador com uma instalação de contexto de Dispositivo.
- Se uma aplicação for implementada no contexto do dispositivo, mas direcionada para um dispositivo que não suporta o contexto do dispositivo, a instalação irá falhar com o seguinte estado e erro apresentados na consola de administração:
    - Estado: falha.
    - Erro: esta plataforma não suporta instalações de contexto do dispositivo. 

> [!Note]
> Assim que uma atribuição de aplicações for guardada com uma implementação específica, o contexto não pode ser alterado para essa atribuição, exceto para aplicações modernas. No caso da aplicação moderna, o contexto pode ser alterado do contexto de utilizador para o contexto do dispositivo. 

Se existir um conflito nas políticas num único utilizador/dispositivo, seguem-se as prioridades de política utilizadas para determinar a política final:
- Uma política de contexto do dispositivo tem uma prioridade mais alta do que uma política de contexto de utilizador. 
- Uma política de instalação tem uma prioridade mais alta do que uma política de desinstalação.

Para obter mais informações sobre a atribuição de aplicações através do Microsoft Intune, veja [Atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md) e [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md). Para obter mais informações sobre tipos de aplicações no Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Passos seguintes

- Para saber mais sobre a atribuição de aplicações a grupos, veja [Atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).
- Para saber mais sobre a monitorização de atribuições de aplicações, veja [Como monitorizar aplicações](apps-monitor.md).
