---
title: Utilizar Extensões de Mobilidade Zebra em dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o Microsoft Intune para gerir e utilizar dispositivos Zebra a executar o Android com Extensões de Mobilidade (MX) Zebra. Fique a conhecer todos os passos, incluindo como instalar a aplicação do Portal da Empresa, fazer sideload da aplicação, atribuir a função de administrador do dispositivo, criar um perfil do StageNow e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3f5625a84a3d2327a5ccac24ad10d2bb0e48c02
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59896636"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Utilizar e gerir dispositivos Zebra com as Extensões de Mobilidade Zebra no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune inclui um conjunto avançado de funcionalidades, incluindo a gestão de aplicações e a configuração de definições do dispositivo. Estas definições e funcionalidades incorporadas servem para gerir dispositivos Android fabricados pela Zebra Technologies, também conhecidos como “dispositivos Zebra”.

O Intune também oferece outras formas de gerir as definições *específicas* dos dispositivos Zebra:

- Em dispositivos Android Enterprise, utilize **OEMConfig** para configurar as definições que não estão incorporadas no Intune. Para obter mais informações, veja [Utilizar e gerir dispositivos Zebra no Android Enterprise com OEMConfig](android-oem-configuration-overview.md).
- Em dispositivos Android, utilize os perfis **Extensões de Mobilidade (MX)** para personalizar ou adicionar outras definições específicas da Zebra.

Este artigo mostra-lhe como utilizar as Extensões de Mobilidade (MX) Zebra em dispositivos Zebra no Microsoft Intune. Para utilizar OEMConfig, aceda a [Utilizar e gerir dispositivos Zebra no Android Enterprise com OEMConfig](android-oem-configuration-overview.md).

Esta funcionalidade aplica-se a:

- Android

A sua empresa pode utilizar os dispositivos Zebra na venda a retalho, na fábrica e em muitas outras situações. Por exemplo, é um revendedor e o seu ambiente inclui milhares de dispositivos móveis Zebra utilizados pelos seus assistentes comerciais. O Intune pode ajudar a gerir estes dispositivos como parte da sua solução de gestão de dispositivos móveis (MDM).

Com o Intune, pode inscrever dispositivos Zebra para implementar as aplicações de linha de negócio nos dispositivos. Os perfis de “configuração do dispositivo” permitem criar perfis MX para gerir as definições específicas da Zebra.

## <a name="before-you-begin"></a>Antes de começar

- Verifique se tem a versão mais recente da aplicação de ambiente de trabalho StageNow da Zebra Technologies.
- Não deixe de ver [Zebra's full MX feature matrix](http://techdocs.zebra.com/mx/compatibility) (Matriz completa de funcionalidades MX da Zebra) (abre o site da Zebra) para confirmar que os perfis que cria são compatíveis com a versão da MX, a versão do SO e o modelo do dispositivo.
- Determinados dispositivos, como os dispositivos TC20/25, não suportam todas as funcionalidades MX disponíveis no StageNow. Não deixe de ver [Zebra's feature matrix](http://techdocs.zebra.com/mx/tc2x/) (Matriz de funcionalidades da Zebra) (abre o site da Zebra) para obter informações de suporte atualizadas.

## <a name="step-1-install-the-latest-company-portal-app"></a>Passo 1: Instalar a aplicação do Portal da Empresa mais recente

No dispositivo, aceda à Google Play Store e transfira e instale a aplicação do Portal da Empresa do Intune da Microsoft. Quando instalada a partir do Google Play, a aplicação do Portal da Empresa obtém as atualizações e as correções automaticamente.

Se o Google Play não estiver disponível, transfira o [Portal da Empresa do Microsoft Intune para Android](https://www.microsoft.com/download/details.aspx?id=49140) (abre outro site da Microsoft) e [faça o seu sideload](#sideload-the-company-portal-app) (neste artigo). Quando instalada desta maneira, a aplicação não recebe atualizações nem correções automaticamente. Tem de atualizar regularmente e aplicar manualmente os patches.

### <a name="sideload-the-company-portal-app"></a>Fazer sideload da aplicação Portal da Empresa

Recorre ao “sideloading” quando não utiliza o Google Play para instalar uma aplicação. Para fazer sideload da aplicação do Portal da Empresa, utilize o StageNow. 

Os passos seguintes permitem obter uma descrição geral. Para obter detalhes específicos, veja a documentação da Zebra. O artigo [Enroll in an MDM using StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (Inscrever-se na MDM com o StageNow) (abre o site da Zebra) pode ser uma boa opção.

1. No StageNow, crie um perfil para se **Inscrever na MDM**.
2. Em **Implementação**, opte por transferir o ficheiro do agente MDM.
3. Defina os passos **Suporte da Aplicação** e **Transferir Configuração** como **Não**.
4. Em **Transferir MDM**, selecione **Transferir/Copiar Ficheiro**. Adicione a origem e o destino do pacote Android do Portal da Empresa (APK).
5. Em **Iniciar MDM**, deixe os valores predefinidos tal como estão. Adicione os seguintes detalhes:

    - **Nome do Pacote**: `com.microsoft.windowsintune.companyportal`
    - **Nome da Classe**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Avance para publicar o perfil e consuma-o com a aplicação StageNow no dispositivo. A aplicação do Portal da Empresa é instalada e aberta no dispositivo.

> [!TIP]
> Para obter mais informações sobre o StageNow e para que serve, veja [StageNow Android device staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (Transição de dispositivos Android com StageNow) (abre o site da Zebra).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Passo 2: Confirmar que a aplicação do Portal da Empresa tem a função de administrador de dispositivos

A aplicação do Portal da Empresa exige um Administrador de Dispositivos para gerir os dispositivos Android. Para ativar a função de Administrador de Dispositivos, alguns dispositivos Zebra incluem uma interface de utilizador (IU) no dispositivo. Se o dispositivo incluir uma IU, a aplicação do Portal da Empresa avisará o utilizador final para atribuir o Administrador de Dispositivos durante a [inscrição](#step-3-enroll-the-device-in-to-intune) (neste artigo).

Se a interface de utilizador não estiver disponível, utilize o **DevAdmin Manager** no StageNow para criar um perfil que atribui manualmente o Administrador de Dispositivos à aplicação do Portal da Empresa.

Os passos seguintes permitem obter uma descrição geral. Para obter detalhes específicos, veja a documentação da Zebra. 
O artigo [Set battery swap mode as device administrator](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (Definir o modo de troca de baterias como administrador de dispositivos) (abre o site da Zebra) pode ser uma boa opção.

1. No StageNow, crie um perfil e selecione **Modo Xpert**.
2. Adicione **DevAdmin Manager** ao perfil.
3. Defina **Ação de Administração de Dispositivos** como **Ativar como Administrador de Dispositivos**.
4. Defina **Nome do Pacote de Administração de Dispositivos** como `com.microsoft.windowsintune.companyportal`.
5. Defina **Nome da Classe de Administração de Dispositivos** como `com.microsoft.omadm.client.PolicyManagerReceiver`.

Avance para publicar o perfil e consuma-o com a aplicação StageNow no dispositivo. É atribuída à aplicação do Portal da Empresa a função de Administrador de Dispositivos.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Passo 3: Inscrever o dispositivo no Intune

Depois de concluir os dois primeiros passos, a aplicação do Portal da Empresa é instalada no dispositivo. O dispositivo está pronto para ser inscrito no Intune.

Veja [Inscrever dispositivos Android](android-enroll.md) para obter os passos. Se tiver muitos dispositivos Zebra, talvez prefira utilizar uma [conta de gestor de inscrição de dispositivos (DEM)](device-enrollment-manager-enroll.md). A utilização de uma conta DEM também remove a opção para anular a inscrição da aplicação do Portal da Empresa, para que os utilizadores não possam anular facilmente a inscrição do dispositivo.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Passo 4: Criar um perfil de gestão de dispositivos no StageNow

Utilize o StageNow para criar um perfil que configura as definições que quer gerir no dispositivo. Para obter detalhes específicos, veja a documentação da Zebra. O artigo [Profiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (Perfis) (abre o site da Zebra) pode ser uma boa opção.

Quando cria o perfil no StageNow, no último passo, selecione **Exportar para MDM**. Esta opção gera um ficheiro XML. Guarde este ficheiro, pois precisará dele num passo posterior.

> [!TIP]
> É recomendado testar o perfil antes de o implementar nos dispositivos da sua organização. Para testar, no último passo da criação de perfis com o StageNow no computador, utilize as opções **Testar**. Em seguida, consuma o ficheiro gerado pelo StageNow com a aplicação StageNow no dispositivo. 
> 
> A aplicação StageNow no dispositivo mostrará os registos gerados quando testar o perfil. [Utilizar registos do StageNow em dispositivos Zebra com Android no Intune](android-zebra-mx-logs-troubleshoot.md) tem informações sobre como utilizar os registos do StageNow para compreender os erros.

> [!NOTE]
> Se fizer referência a aplicações, atualizar pacotes ou atualizar outros ficheiros no perfil do StageNow, vai querer que o dispositivo obtenha estas atualizações. Para obter as atualizações, o dispositivo tem de ligar ao servidor de implementação do StageNow quando o perfil é aplicado. 
> 
> Em alternativa, pode utilizar as funcionalidades incorporadas no Intune para obter essas alterações, incluindo: 
> - As funcionalidades de gestão de aplicações para [adicionar](apps-add.md), [implementar](apps-deploy.md), atualizar e [monitorizar](apps-monitor.md) as aplicações.
> - Gerir as [atualizações do sistema e de aplicações](device-restrictions-android-for-work.md#device-owner-only) nos dispositivos com o Android Enterprise

Depois de testar o ficheiro, o próximo passo é implementar o perfil nos dispositivos com o Intune.

> [!NOTE]
> Implemente um perfil em cada dispositivo. Se existirem vários perfis do StageNow que queira implementar nos dispositivos, exporte-os e combine as definições num único ficheiro XML antes de o adicionar ao Intune. 
> 
> Não vai querer duas definições a configurar a mesma propriedade no mesmo ficheiro XML. O objetivo é evitar conflitos entre definições no dispositivo.

## <a name="step-5-create-a-profile-in-intune"></a>Passo 5: Criar um perfil no Intune

No Intune, crie um perfil de configuração de dispositivos:

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** > filtre o **Intune** > selecione **Intune**.
2. Selecione **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **Android**.
    - **Tipo de perfil**: selecione **Perfil MX (apenas Zebra)**.

4. Em **Perfil MX no formato .xml**, adicione o ficheiro XML do perfil que [exportou do StageNow](#step-4-create-a-device-management-profile-in-stagenow) (neste artigo).
5. Selecione **OK** > **Criar** para guardar as alterações. A política é criada e apresentada na lista.

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Da próxima vez que o dispositivo verificar se existem atualizações de configuração, o perfil MX será implementado no dispositivo. Os dispositivos são sincronizados com o Intune quando são inscritos e, depois, aproximadamente a cada 8 horas. Também pode [forçar uma sincronização no Intune](device-sync.md). Ou, no dispositivo, abra a aplicação **Portal da Empresa** > **Definições** > **Sincronizar**. 

> [!TIP]
> - Por motivos de segurança, não verá o texto XML do perfil depois de o guardar. O texto é encriptado e apenas verá asteriscos (`****`). Para sua referência, é recomendado guardar cópias dos perfis MX antes de os adicionar ao Intune.
> 
> - Para atualizar um perfil depois de ter sido atribuído aos dispositivos Zebra, crie um ficheiro XML do StageNow atualizado, edite o perfil do Intune existente e adicione o novo ficheiro XML do StageNow. Este novo ficheiro substitui a anterior política do StageNow no perfil.

## <a name="next-steps"></a>Próximos passos

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
- [Utilizar OEMConfig para gerir dispositivos Zebra no Android Enterprise](android-oem-configuration-overview.md).
- [Utilizar registos do StageNow para resolver problemas de dispositivos Zebra](android-zebra-mx-logs-troubleshoot.md).
