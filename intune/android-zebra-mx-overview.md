---
title: Utilize as riscas das extensões de mobilidade em dispositivos Android no Microsoft Intune – Azure | Documentos da Microsoft
description: Utilize o Microsoft Intune para gerir e utilizar dispositivos as riscas das Android com extensões de mobilidade as riscas das (MX). Ver todas as etapas, incluindo instalar a aplicação Portal da empresa, fazer sideload do aplicativo, atribuir a função de administrador do dispositivo, criar um perfil de StageNow e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490609"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Utilizar e gerir as riscas das dispositivos com as riscas das extensões de mobilidade no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune inclui um conjunto avançado de funcionalidades, incluindo gestão de aplicações e configurar as definições do dispositivo. Estas definições e funcionalidades incorporadas são utilizadas para gerir dispositivos Android fabricados pelas riscas das tecnologias, também conhecido como "dispositivos das riscas das".

Se desejar personalizar ou adicionar mais específicas as riscas das definições, também pode utilizar as riscas das **extensões de mobilidade (MX)** nestes dispositivos. 

Esta funcionalidade aplica-se a:

- Android

Sua empresa utilizar dispositivos as riscas para revenda, no chão de fábrica e muito mais. Por exemplo, é um varejista e seu ambiente incluir milhares de dispositivos móveis das riscas das utilizados pela associados de vendas. Intune pode ajudar a gerir estes dispositivos como parte da sua solução de gestão (MDM) de dispositivos móveis.

Com o Intune, pode inscrever dispositivos as riscas para implementar as suas aplicações de linha de negócio para os dispositivos. Perfis de "Configuração do dispositivo" permitem-lhe criar perfis de MX para gerir as definições das riscas das específicas.

Este artigo mostra-lhe como utilizar a mobilidade das riscas das extensões (MX) em dispositivos das riscas no Microsoft Intune.

## <a name="before-you-begin"></a>Antes de começar

- Certifique-se de que tem a versão mais recente da aplicação de ambiente de trabalho de StageNow nas riscas das tecnologias.
- Certifique-se de que verifique [matriz de recursos de MX das riscas das completa](http://techdocs.zebra.com/mx/compatibility) (abre o site da web das riscas das) para confirmar os perfis que cria são compatíveis com a versão de MX, versão do SO e modelo do dispositivo.
- Determinados dispositivos, tais como TC20/25 dispositivos não suportam todas as funcionalidades disponíveis do MX no StageNow. Certifique-se de que verifique [matriz de recursos das riscas das](http://techdocs.zebra.com/mx/tc2x/) (abre o site da web das riscas das) para informações de suporte atualizado.

## <a name="step-1-install-the-latest-company-portal-app"></a>Passo 1: Instalar a mais recente aplicação do Portal da empresa

No dispositivo, aceda à Google Play store e transferir e instalar a aplicação Portal da empresa do Intune da Microsoft. Quando instalado no Google Play, a aplicação Portal da empresa obtém as atualizações e correções de automaticamente.

Se o Google Play não estiver disponível, transfira o [Portal de empresa do Microsoft Intune para Android](https://www.microsoft.com/download/details.aspx?id=49140) (abre-se outro Web site da Microsoft), e [sideload-](#sideload-the-company-portal-app) (neste artigo). Quando instalado dessa maneira, a aplicação não recebe atualizações ou correções automaticamente. Deve atualizar regularmente e a aplicação de patches manualmente.

### <a name="sideload-the-company-portal-app"></a>Carregar em sideload a aplicação do Portal da empresa

"Sideload" é quando não utiliza o Google Play para instalar uma aplicação. Para fazer sideload do aplicativo de Portal da empresa, utilize StageNow. 

Os passos seguintes fornecem uma visão geral. Para obter detalhes específicos, consulte a documentação das riscas das. [Inscreva-se num MDM usando StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (abre o site da web das riscas das) pode ser um bom recurso.

1. StageNow, criar um perfil para **inscrever num MDM**.
2. Na **implementação**, optar por transferir o ficheiro de agente MDM.
3. Definir o **aplicação de suporte** e **transferir configuração** para os passos **não**.
4. Na **transferir MDM**, selecione **transferência/Copiar ficheiro**. Adicione a origem e de destino do pacote da empresa Portal Android (ficheiro. APK).
5. Na **MDM iniciar**, deixe os valores predefinidos, como-é. Adicione os seguintes detalhes:

    - **Nome do pacote**: `com.microsoft.windowsintune.companyportal`
    - **Nome de classe**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Avance para o perfil de publicação e consumi-las com a aplicação de StageNow no dispositivo. A aplicação Portal da empresa é instalada e aberta no dispositivo.

> [!TIP]
> Para obter mais informações sobre StageNow e o que ele faz, consulte [transição de dispositivo StageNow Android](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (abre o site da web das riscas das).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Passo 2: Confirmar a que aplicação Portal da empresa tenha a função de administrador de dispositivo

A aplicação Portal da empresa necessita de administrador de dispositivos para gerir dispositivos Android. Para ativar a função de administrador do dispositivo, alguns dispositivos as riscas das incluem uma interface de utilizador (IU) no dispositivo. Se o dispositivo inclui uma interface do Usuário, a aplicação Portal da empresa solicita que o utilizador final para conceder o administrador do dispositivo durante [inscrição](#step-3-enroll-the-device-in-to-intune) (neste artigo).

Se uma interface do Usuário não estiver disponível, utilize o **DevAdmin Manager** no StageNow para criar um perfil que concede manualmente o administrador do dispositivo para a aplicação Portal da empresa.

Os passos seguintes fornecem uma visão geral. Para obter detalhes específicos, consulte a documentação das riscas das. 
[Conjunto de troca de baterias como administrador de dispositivo](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (abre o site das riscas das) pode ser um bom recurso.

1. No StageNow, crie um perfil e selecione **Xpert modo**.
2. Adicione **DevAdmin Manager** ao perfil.
3. Definir **ação de administração do dispositivo** ao **ativar como administrador de dispositivo**.
4. Definir **nome de pacote de administrador do dispositivo** para `com.microsoft.windowsintune.companyportal`.
5. Definir **nome de classe de administrador do dispositivo** para `com.microsoft.omadm.client.PolicyManagerReceiver`.

Avance para o perfil de publicação e consumi-las com a aplicação de StageNow no dispositivo. A aplicação Portal da empresa é concedida a função de administrador do dispositivo.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Passo 3: Inscrever o dispositivo no Intune

Depois de concluir os primeiros dois passos, a aplicação Portal da empresa está instalada no dispositivo. O dispositivo está pronto para ser inscrito no Intune.

[Inscrever dispositivos Android](android-enroll.md) lista os passos. Se tiver muitos dispositivos as riscas das, talvez queira usar um [conta de Gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Passo 4: Criar um perfil de gestão de dispositivos no StageNow

Utilize StageNow para criar um perfil que configura as definições que pretende gerir no dispositivo. Para obter detalhes específicos, consulte a documentação das riscas das. [Perfis](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (abre o site das riscas das) pode ser um bom recurso.

Quando cria o perfil no StageNow, no último passo, selecione **exportar para o MDM**. Isso gera um arquivo XML. Guarde este ficheiro. Precisa num passo posterior.

> [!TIP]
> É recomendado para testar o perfil antes de implementar em dispositivos na sua organização. Para testar, no último passo durante a criação de perfis com StageNow no seu computador, utilize o **testar** opções. Em seguida, consuma o ficheiro gerado pelo StageNow com a aplicação de StageNow no dispositivo. 
> 
> A aplicação de StageNow no dispositivo mostra logs gerados quando testar o perfil. [Registos de utilização StageNow em dispositivos das riscas com Android no Intune](android-zebra-mx-logs-troubleshoot.md) tem informações sobre como utilizar os registos de StageNow para compreender os erros.

> [!NOTE]
> Se fazer referência a aplicações, pacotes de atualização ou atualizar outros ficheiros no seu perfil StageNow, quer o dispositivo para obter estas atualizações. Para obter as atualizações, o dispositivo tem de ligar ao servidor de implantação de StageNow quando o perfil é aplicado. 
> 
> Em alternativa, pode utilizar as funcionalidades incorporadas no Intune para obter essas alterações, incluindo: 
> - Funcionalidades de gestão de aplicações para [adicione](apps-add.md), [implementar](apps-deploy.md), atualizar, e [monitor](apps-monitor.md) aplicações.
> - Gerir [atualizações de sistema e aplicação](device-restrictions-android-for-work.md#device-owner-only) em dispositivos com o Android Enterprise

Depois de testar o ficheiro, a próxima etapa é implementar o perfil para dispositivos com o Intune.

> [!NOTE]
> Implemente um perfil de cada dispositivo. Se existirem vários perfis de StageNow que pretende implementar nos dispositivos, em seguida, exportar os perfis de StageNow e combinar as definições num único arquivo XML antes de o adicionar ao Intune. 
> 
> Não quer duas definições que configuram a mesma propriedade no mesmo ficheiro XML. O objetivo é evitar conflitos entre as definições no dispositivo.

## <a name="step-5-create-a-profile-in-intune"></a>Passo 5: Criar um perfil no Intune

No Intune, crie um perfil de configuração do dispositivo:

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **Android**.
    - **Tipo de perfil**: Selecione **perfil de MX (apenas as riscas das)**.

4. Na **perfil MX no formato. XML**, adicione o ficheiro de perfil XML [exportou a partir da StageNow](#step-4-create-a-device-management-profile-in-stagenow) (neste artigo).
5. Selecione **OK** > **Criar** para guardar as alterações. A política é criada e apresentada na lista.

O perfil está criado, mas ainda não está ativo. Em seguida, [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

Da próxima vez que o dispositivo verifica a existência de atualizações de configuração, o perfil de MX é implementado no dispositivo. Sincronizar dispositivos com o Intune, quando inscrever dispositivos e, em seguida, aproximadamente a cada 8 horas. Também pode [forçar a sincronização no Intune](device-sync.md). Ou, no dispositivo, abra a **aplicação Portal da empresa** > **definições** > **sincronização**. 

> [!TIP]
> - Por motivos de segurança, não verá o texto XML do perfil depois de o guardar. O texto é encriptado e apenas verá asteriscos (`****`). Para referência, é recomendado para guardar as cópias dos perfis de MX antes de os adicionar ao Intune.
> 
> - Para atualizar um perfil depois do que é atribuído aos dispositivos as riscas das, criar um ficheiro XML de StageNow atualizado, editar o perfil do Intune existente e adicionar o novo arquivo XML de StageNow. Este novo ficheiro substitui a política de StageNow anterior no perfil.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

[Utilizar registos de StageNow para resolver problemas de dispositivos das riscas das](android-zebra-mx-logs-troubleshoot.md).
