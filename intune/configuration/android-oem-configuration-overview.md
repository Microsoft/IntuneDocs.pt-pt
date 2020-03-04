---
title: Utilize o OEMConfig em dispositivos Android Enterprise no Microsoft Intune - Azure Microsoft Docs
description: Utilize o Microsoft Intune para gerir e utilizar dispositivos que executam o Android Enterprise com a OEMConfig. Veja todos os passos, incluindo uma visão geral, consulte os pré-requisitos, crie o perfil de configuração em Intune e veja uma lista de aplicações oEMConfig suportadas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bc811bcac80f8321284ece8d3860efc7164a270
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256327"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Utilizar e gerir dispositivos Android Enterprise com OEMConfig no Microsoft Intune

No Microsoft Intune, pode utilizar o OEMConfig para adicionar, criar e personalizar configurações específicas do OEM para dispositivos Android Enterprise. OEmConfig é normalmente usado para configurar configurações que não estão incorporadas em Intune. Diferentes fabricantes de equipamentos originais (OEM) incluem diferentes configurações. As definições disponíveis dependem do que o OEM inclui na sua aplicação OEMConfig.

Esta funcionalidade aplica-se a:  

- Android Enterprise

Este artigo descreve o OEMConfig, lista os pré-requisitos, mostra como criar um perfil de configuração, e lista as aplicações oEMConfig suportadas em Intune.

## <a name="overview"></a>Descrição geral

As políticas da OEMConfig são um tipo especial de política de configuração do dispositivo semelhante à política de configuração de [aplicações.](../apps/app-configuration-policies-overview.md) OEMConfig é um padrão definido pela Google que utiliza a configuração de aplicações no Android para enviar configurações de dispositivos para aplicações escritas por OEMs (fabricantes de equipamentos originais). Esta norma permite que o OEMs e os EMMs (gestão da mobilidade empresarial) construam e apoiem funcionalidades específicas do OEM de forma padronizada. [Saiba mais sobre a OEMConfig.](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)

Historicamente, os EMMs, como o Intune, constroem manualmente suporte para funcionalidades específicas do OEM após serem introduzidas pelo OEM. Esta abordagem conduz a esforços duplicados e a uma adoção lenta.

Com a OEMConfig, um OEM cria um esquema que define funcionalidades de gestão específicas do OEM. O OEM incorpora o esquema numa aplicação e, em seguida, coloca esta aplicação no Google Play. O EMM lê o esquema da aplicação e expõe o esquema na consola de administrador da EMM. A consola permite que os administradores intune configurem as definições no esquema.

Quando a aplicação OEMConfig se instala num dispositivo, utiliza as definições configuradas no administrador da EMM para gerir o dispositivo. As definições do dispositivo são executadas pela aplicação OEMConfig, em vez de um agente MDM construído pelo EMM.

Quando o OEM adiciona e melhora as funcionalidades de gestão, o OEM também atualiza a aplicação no Google Play. Como administrador, obtém estas novas funcionalidades e atualizações (incluindo correções) sem esperar que os EMMs incluam estas atualizações.

> [!TIP]
> Só é possível utilizar a OEMConfig com dispositivos que suportem esta funcionalidade e ter uma aplicação OEMConfig correspondente. Consulte o seu OEM para obter detalhes específicos.

## <a name="before-you-begin"></a>Antes de começar

Ao utilizar a OEMConfig, esteja atento às seguintes informações:

- Intune expõe o esquema da aplicação OEMConfig para que possa configurá-lo. Intune não valida nem altera o esquema fornecido pela app. Portanto, se o esquema estiver incorreto, ou tiver dados imprecisos, então estes dados ainda são enviados para dispositivos. Se encontrar um problema que tenha origem no esquema, contacte o OEM para obter orientação.
- Intune não influencia nem controla o conteúdo do esquema da aplicação. Por exemplo, Intune não tem qualquer controlo sobre cordas, linguagem, as ações permitidas, e assim por diante. Recomendamos contactar o OEM para obter mais informações sobre a gestão dos seus dispositivos com a OEMConfig.
- A qualquer momento, os OEMs podem atualizar as suas funcionalidades e esquemas suportados e enviar uma nova aplicação para o Google Play. Intune sincroniza sempre a versão mais recente da aplicação OEMConfig do Google Play. Intune não mantém versões mais antigas do esquema ou da app. Se encontrar conflitos de versão, recomendamos que contacte o OEM para obter mais informações.
- Designar um perfil OEMConfig para um dispositivo. Se vários perfis forem atribuídos ao mesmo dispositivo, poderá ver um comportamento inconsistente. O modelo OEMConfig suporta apenas uma única política por dispositivo.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar a OEMConfig nos seus dispositivos, certifique-se de que tem os seguintes requisitos:

- Um dispositivo Android Enterprise matriculado em Intune.
- Uma aplicação OEMConfig construída pelo OEM, e enviada para o Google Play. Se não estiver no Google Play, contacte o OEM para obter mais informações.
- O administrador intune tem permissões de controlo de acesso (RBAC) baseadas em papéis para **aplicações móveis,** Configurações de **Dispositivos,** e a permissão "read" no **Android for Work**. Estas permissões são necessárias porque os perfis oEMConfig utilizam configurações de aplicações geridas para gerir as configurações do dispositivo.

## <a name="prepare-the-oemconfig-app"></a>Prepare a app OEMConfig

Certifique-se de que o dispositivo suporta o OEMConfig, a aplicação OEMConfig correta é adicionada ao Intune e a aplicação está instalada no dispositivo. Contacte o OEM para obter esta informação.

> [!TIP] 
> As aplicações OEMConfig são específicas do OEM. Por exemplo, uma aplicação Sony OEMConfig instalada num dispositivo Zebra Technologies não faz nada.

1. Obtenha a aplicação OEMConfig na Loja de Play Da Google Gerida. [Adicione aplicações geridas do Google Play a dispositivos empresariais Android](../apps/apps-add-android-for-work.md) lista os passos.
2. Alguns OEMs podem enviar dispositivos com a aplicação OEMConfig pré-instalada. Se a aplicação não estiver pré-instalada, utilize o Intune para [adicionar e implementar a aplicação para dispositivos](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Criar um perfil OEMConfig

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Plataforma**: Selecione **empresa Android**.
    - **Tipo de perfil**: Selecione **OEMConfig**.

4. Selecione **Criar**.
5. No Básico, insira as **seguintes**propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Aplicação OEMConfig**: **Escolha Selecione uma aplicação OEMConfig**.

6. Na **aplicação Associated,** selecione uma aplicação OEMConfig existente que adicionou anteriormente > **Selecione**. Certifique-se de que escolhe a aplicação OEMConfig correta para os dispositivos a que atribui a apólice.

    Se não vir nenhuma aplicação listada, então crie o Managed Google Play e obtenha aplicações da loja Managed Google Play. [Adicione aplicações geridas](../apps/apps-add-android-for-work.md) do Google Play a dispositivos Android Enterprise lista os passos.

    > [!IMPORTANT]
    > Se adicionou uma aplicação OEMConfig e a sincronizou no Google Play, mas não está listada como uma **aplicação Associada,** poderá ter de contactar a Intune para embarcar na aplicação. Consulte [a adição de uma nova app](#supported-oemconfig-apps) (neste artigo).

7. Selecione **Seguinte**.
8. Nas **definições de Configuração,** selecione o designer de **configuração** ou **o editor JSON:**

    > [!TIP]
    > Leia a documentação do OEM para se certificar de que está a configurar corretamente as propriedades. Estas propriedades da aplicação estão incluídas pelo OEM, não pelo Intune. Intune faz a validação mínima das propriedades, ou do que você entra. Por exemplo, se introduzir `abcd` para um número de porta, o perfil economiza como está e é implantado nos seus dispositivos com os valores que configura. Certifique-se de introduzir a informação correta.

    - **Designer de configuração**: Quando selecionar esta opção, as propriedades disponíveis dentro do esquema da aplicação são mostradas para que possa configurar.

      - Os menus de contexto no designer de configuração indicam que há mais opções disponíveis. Por exemplo, o menu de contexto pode permitir-lhe adicionar, eliminar e reencomendar definições. Estas opções estão incluídas pelo OEM. Certifique-se de ler a documentação da aplicação OEM para saber como estas opções devem ser usadas para criar perfis.

      - Muitas definições têm valores predefinidos fornecidos pelo OEM. Para ver se há um valor predefinido, paire sobre o ícone da informação ao lado da definição. Um dica de ferramenta supor os valores predefinidos para essa definição (se aplicável) e mais detalhes fornecidos pelo OEM.

      - Clicar em **Clear** elimina uma definição do perfil. Se uma definição não estiver no perfil, o seu valor no dispositivo não mudará quando o perfil é aplicado.

      - Se criar um pacote vazio (não configurado) no designer de configuração, é eliminado ao mudar para o editor da JSON.

    - **Editor da JSON**: Quando seleciona esta opção, um editor da JSON abre com um modelo para o esquema de configuração completo incorporado na aplicação. No editor, personalize o modelo com valores para as diferentes configurações. Se utilizar o designer de **configuração** para alterar os seus valores, o editor da JSON substitui o modelo com valores do designer de configuração.

      - Se estiver a atualizar um perfil existente, o editor da JSON mostra as definições que foram guardadas pela última vez com o perfil.

      - Os schemas oEMConfig podem ser grandes e complexos. Se preferir atualizar estas definições utilizando um editor diferente, selecione o botão de **modelo Descarregamento JSON.** Utilize um editor à sua escolha para adicionar os seus valores de configuração ao modelo. Em seguida, copie e cole o seu JSON atualizado na propriedade do **editor da JSON.**

      - Pode utilizar o editor da JSON para criar uma cópia de segurança da sua configuração. Depois de configurar as definições, utilize esta funcionalidade para obter as definições JSON com os seus valores. Copie e cole o JSON num ficheiro e guarde-o. Agora tem um ficheiro de reserva.

    Quaisquer alterações feitas no designer de configuração também são feitas automaticamente no editor da JSON. Da mesma forma, quaisquer alterações feitas no editor da JSON são feitas automaticamente no designer de configuração. Se a sua entrada contiver valores inválidos, não pode alternar entre o designer de configuração e o editor jSON até corrigir os problemas.

9. Selecione **Seguinte**.
10. Nas **etiquetas scope** (opcional), atribua uma etiqueta para filtrar o perfil a grupos de TI específicos, tais como `US-NC IT Team` ou `JohnGlenn_ITDepartment`. Para obter mais informações sobre etiquetas de âmbito, consulte [Use RBAC e etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .

    Selecione **Seguinte**.

11. Em **Atribuições,** selecione os utilizadores ou grupos que receberão o seu perfil. Atribuir um perfil a cada dispositivo. O modelo OEMConfig suporta apenas uma política por dispositivo.

    Para obter mais informações sobre a atribuição de perfis, consulte os perfis de [utilizador e dispositivo de atribuição](device-profile-assign.md).

    Selecione **Seguinte**.

12. Em **Review + criar,** reveja as suas definições. Quando selecionar **Criar,** as suas alterações são guardadas e o perfil é atribuído. A política também está na lista de perfis.

Da próxima vez que o dispositivo verificar as atualizações de configuração, as definições específicas do OEM configuradas são aplicadas à aplicação OEMConfig.

> [!NOTE]
> A norma OEMConfig não inclui atualmente relatórios de estado. Assim, por padrão, os perfis mostram um estado **pendente.**

## <a name="supported-oemconfig-apps"></a>Aplicativos OEMConfig suportados

Em comparação com as aplicações padrão, as aplicações OEMConfig expandem os privilégios de configurações geridas concedidos pela Google para suportar esquemas mais complexos. Intune suporta atualmente as seguintes aplicações OEMConfig:

-----------------

| OEM | ID do Pacote | Documentação OEM (se disponível) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Guia de administrador de plugin de serviço Knox](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Tecnologias Zebra | com.zebra.oemconfig.common | [Visão geral da Zebra OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Documentação do utilizador para OEMConfig Datalogic](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Rio Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink - Barcos de barras | com.spectralink.códigode.service |  |
| Spectralink - Botões | com.spectralink.buttons |  |
| Spectralink - Dispositivo | com.spectralink.slnkdevicesettings  |  |
| Spectralink - Exploração Madeireira | com.spectralink.slnklogger |  |
| Spectralink - VQO | com.spectralink.slnkvqo |  |
| Seuic | com.seuic.seuicoemconfig | |
| Unitech Electronics | com.unitech.oemconfig | |

-----------------

Se existe uma aplicação OEMConfig para o seu dispositivo, mas não está na tabela acima, ou não aparece na consola Intune, o email `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> As aplicações OEMConfig devem embarcar pela Intune antes de poderem ser configuradas com perfis OEMConfig. Uma vez que uma aplicação é suportada, você não precisa contactar a Microsoft sobre a configuração no seu inquilino. Basta seguir as instruções nesta página.
>
> Se sentir que uma aplicação OEMConfig se comporta mal, contacte os desenvolvedores da aplicação OEMConfig. Intune não é responsável por problemas técnicos com as aplicações individuais da OEMConfig.

## <a name="next-steps"></a>Próximos passos

[Monitorize o estado do perfil](device-profile-monitor.md).
