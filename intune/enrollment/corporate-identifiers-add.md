---
title: Adicionar identificadores empresariais ao Intune
titleSuffix: ''
description: Saiba como adicionar identificadores empresariais (método de inscrição, IMEI e números de série) ao Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac86e9155f08683ab073ae0b46ea3f2780060c90
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730004"
---
# <a name="identify-devices-as-corporate-owned"></a>Identificar os dispositivos como pertencentes à empresa

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como administrador do Intune, pode identificar os dispositivos como pertencentes à empresa para refinar a gestão e identificação. O Intune pode executar tarefas de gestão adicionais e recolher informações adicionais como o número de telemóvel completo e um inventário das aplicações de dispositivos pertencentes à empresa. Também pode definir restrições de dispositivos para bloquear a inscrição de dispositivos que não pertencem à empresa.

No momento da inscrição, o Intune atribui automaticamente o estado de propriedade da empresa a dispositivos que sejam:

- Inscrito com uma conta de [gestor de inscrições de dispositivos](device-enrollment-manager-enroll.md) (todas as plataformas)
- Inscrito com o [Programa de Registo de Aparelho](device-enrollment-program-enroll-ios.md) Apple, [Apple School Manager](apple-school-manager-set-up-ios.md) ou o [Apple Configurator](apple-configurator-enroll-ios.md) (apenas iOS)
- [Identificado como pertencente à empresa antes da inscrição](#identify-corporate-owned-devices-with-imei-or-serial-number) com números (todas as plataformas com números IMEI) de um identificador de equipamento móvel internacional (IMEI) ou número de série (iOS e Android)
- Associado ao Azure Active Directory como dispositivo com o Windows 10 Enterprise
- Definidos como empresariais na [lista de propriedades do dispositivo](#change-device-ownership)

Após a inscrição, pode [alterar a definição de propriedade](#change-device-ownership) entre **Pessoal** e **Empresarial**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identificar dispositivos pertencentes à empresa com o número de série IMEI

Enquanto administrador do Intune, pode criar e importar um ficheiro de valores separados por vírgulas (.csv) que indica os números de série ou os números IMEI de 14 dígitos. O Intune utiliza estes identificadores para especificar a propriedade dos dispositivos como empresarial durante a inscrição do dispositivo. Cada número IMEI ou número de série pode ter detalhes especificados na lista para fins administrativos.

Esse recurso tem suporte para as seguintes plataformas:

| Plataforma | Números IMEI | Números de série |
|---|---|---|
| Windows | Com suporte (Windows Phone) | Não suportado |
| iOS/macOS | Não suportado | Suportadas |
| Sistema operacional Android gerenciada pelo administrador do dispositivo v10 | Não suportado | Não suportado |
| Outros Android | Não suportado | Suportadas |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Saiba como localizar o número de série de um dispositivo Apple](https://support.apple.com/HT204308).<br>
[Saiba como localizar o número de série do seu dispositivo Apple](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Adicionar identificadores empresariais com um ficheiro .csv
Para criar a lista, crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione os números de série ou os números IMEI de 14 dígitos na coluna da esquerda e os detalhes na coluna da direita. Só pode ser importado um tipo de ID, número IMEI ou número de série num único ficheiro .csv. Os detalhes estão limitados a 128 carateres e destinam-se apenas a utilização administrativa. Os detalhes não são apresentados no dispositivo. O limite atual é de 5000 linhas por ficheiro .csv.

**Carregar um ficheiro .csv que contenha números de série** – crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5000 dispositivos ou 5 MB por ficheiro .csv.

|||
|-|-|
|&lt;ID n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
|&lt;ID n.º 2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|

Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Alguns dispositivos Android e iOS têm vários números IMEI. O Intune só lê um número IMEI por cada dispositivo inscrito. Se importar um número IMEI, mas não for um número inventariado pelo Intune, o dispositivo será classificado como um dispositivo pessoal em vez de um dispositivo pertencente à empresa. Se importar múltiplos números IMEI para um dispositivo, os números não inventariados apresentarão o estado de inscrição **Desconhecido**.<br>
>Observe também: Os números de série são a forma recomendada de identificação dos dispositivos iOS.
>Não se garante que os Números de série do Android sejam exclusivos ou estejam presentes. Contacte o fornecedor do seu dispositivo para saber se o número de série é um ID de dispositivo fiável.
>Os números de série comunicados pelo dispositivo ao Intune poderão não corresponder ao ID apresentado nos menus Definições/Acerca do Android no dispositivo. Verifique o tipo de número de série comunicado pelo fabricante do dispositivo.
>Tentar carregar um ficheiro com números de série que contenham pontos (.) irá fazer com que o carregamento falhe. Os números de série com pontos não são suportados.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Carregar uma lista .csv de identificadores empresariais

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro** > de dispositivo**identificadores** > de dispositivo corporativo**Adicionar** > **carregar arquivo CSV**.

   ![Área de trabalho de identificador do dispositivo empresarial com o botão Adicionar realçado](./media/corporate-identifiers-add/add-corp-id.png)

2. No painel **Adicionar identificadores**, especifique o tipo de identificador: **IMEI** ou **Série**.

3. Clique no ícone de pasta e especifique o caminho para a lista que pretende importar. Navegue até ao ficheiro .csv e selecione **Adicionar**. 

4. Se o ficheiro .csv incluir identificadores empresariais que já se encontram no Intune, mas que têm detalhes diferentes, será apresentado o pop-up **Reveja os identificadores duplicados**. Selecione os identificadores que pretende substituir no Intune e selecione **OK** para adicionar os identificadores. Para cada identificador, apenas o primeiro duplicado será comparado.

## <a name="manually-enter-corporate-identifiers"></a>Introduzir identificadores empresariais manualmente

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro** > de dispositivo**identificadores** > de dispositivos corporativos**Adicionar** > **Enter manualmente**.

2. No painel **Adicionar identificadores**, especifique o tipo de identificador: **IMEI** ou **Série**.

3. Insira o **identificador** e os **detalhes** para cada identificador que você deseja adicionar. Quando terminar de introduzir identificadores, selecione **Adicionar**.

5. Se introduziu identificadores empresariais que já se encontram no Intune, mas que têm detalhes diferentes, é apresentado o pop-up **Reveja os identificadores duplicados**. Selecione os identificadores que pretende substituir no Intune e selecione **OK** para adicionar os identificadores. Para cada identificador, apenas o primeiro duplicado será comparado.

Pode clicar em **Atualizar** para ver os novos identificadores de dispositivo.

Os dispositivos importados não são necessariamente inscritos. Os dispositivos podem ter o estado de **Inscrito** ou **Não contactado**. **Não contactado** significa que o dispositivo nunca comunicou com o serviço do Intune.

## <a name="delete-corporate-identifiers"></a>Eliminar identificadores empresariais

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro** > de dispositivo**identificadores de dispositivo corporativo**.
2. Selecione os identificadores de dispositivo que pretende eliminar e selecione **Eliminar**.
3. Confirme a eliminação.

Eliminar um identificador empresarial de um dispositivo inscrito não altera a propriedade do dispositivo. Para alterar a propriedade de um dispositivo, aceda a **Dispositivos**, selecione o dispositivo, depois **Propriedades** e altere a **Propriedade do dispositivo**.

## <a name="imei-specifications"></a>Especificações do IMEI
Para obter especificações detalhadas sobre os Identificadores Internacionais do Equipamento Móvel, veja [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Alterar a propriedade dos dispositivos

As propriedades dos dispositivos apresentam a **Propriedade** para os registos de cada dispositivo no Intune. Enquanto administrador, pode especificar dispositivos como **Pessoal** ou **Empresarial**.

**Para alterar a propriedade dos dispositivos:**
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), vá para **dispositivos** e escolha o dispositivo.
2. Selecione **Propriedades**.
3. Especifique a **Propriedade do dispositivo** como **Pessoal** ou **Empresarial**.

   ![Propriedades do dispositivo a mostrar as opções Categoria de dispositivo e Propriedade do dispositivo](./media/corporate-identifiers-add/device-properties.png)
