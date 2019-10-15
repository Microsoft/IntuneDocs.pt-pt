---
title: Adicionar identificadores corporativos ao Intune
titleSuffix: ''
description: Saiba como adicionar identificadores corporativos (método de registro, IMEI e números de série) a Microsoft Intune.
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
ms.openlocfilehash: afc9d953e1d324adb3f00eb5209732a858bbbcda
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314669"
---
# <a name="identify-devices-as-corporate-owned"></a>Identificar dispositivos como corporativos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como administrador do Intune, você pode identificar dispositivos como corporativos para refinar o gerenciamento e a identificação. O Intune pode executar tarefas de gerenciamento adicionais e coletar informações adicionais, como o número de telefone completo e um inventário de aplicativos de dispositivos corporativos. Você também pode definir restrições de dispositivo para bloquear o registro por dispositivos que não são de propriedade corporativa.

No momento do registro, o Intune atribui automaticamente o status de propriedade corporativa aos dispositivos que são:

- Registrado com uma conta do [Gerenciador de registro de dispositivos](device-enrollment-manager-enroll.md) (todas as plataformas)
- Registrado com o Apple [programa de registro de dispositivos](device-enrollment-program-enroll-ios.md), [Apple School Manager](apple-school-manager-set-up-ios.md)ou [Apple Configurator](apple-configurator-enroll-ios.md) (somente Ios)
- [Identificado como corporativo antes do registro](#identify-corporate-owned-devices-with-imei-or-serial-number) com números IMEI (identificador de equipamentos móveis internacional) (todas as plataformas com números IMEI) ou número de série (Ios e Android)
- Ingressou em Azure Active Directory com as credenciais corporativas ou de estudante. Os [dispositivos Azure Active Directory registrados](https://docs.microsoft.com/azure/active-directory/devices/overview) serão marcados como pessoais.
- Definir como corporativo na [lista de propriedades do dispositivo](#change-device-ownership)

Após o registro, você pode [alterar a configuração de propriedade](#change-device-ownership) entre **pessoal** e **corporativo**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identificar dispositivos de propriedade corporativa com IMEI ou número de série

Como administrador do Intune, você pode criar e importar um arquivo de valores separados por vírgulas (. csv) que lista números IMEI de 14 dígitos ou números de série. O Intune usa esses identificadores para especificar a propriedade do dispositivo como corporativo durante o registro do dispositivo. Cada IMEI ou número de série pode ter detalhes especificados na lista para fins administrativos.

Esse recurso tem suporte para as seguintes plataformas:

| Plataforma | Números IMEI | Números de série |
|---|---|---|
| Windows | Com suporte (Windows Phone) | Não suportado |
| iOS/macOS | Não suportado | Suportadas |
| Sistema operacional Android gerenciada pelo administrador do dispositivo v10 | Não suportado | Não suportado |
| Outros Android | Não suportado | Suportadas |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Saiba como localizar um número de série do dispositivo Apple](https://support.apple.com/HT204308).<br>
[Saiba como localizar o número de série do seu dispositivo Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Adicionar identificadores corporativos usando um arquivo. csv
Para criar a lista, crie uma lista de valores separados por vírgulas de duas colunas (. csv) sem um cabeçalho. Adicione o IMEI de 14 dígitos ou os números de série na coluna esquerda e os detalhes na coluna à direita. Somente um tipo de ID, IMEI ou número de série pode ser importado em um único arquivo. csv. Os detalhes são limitados a 128 caracteres e são apenas para uso administrativo. Os detalhes não são exibidos no dispositivo. O limite atual é de 5.000 linhas por arquivo. csv.

**Carregue um arquivo. csv que tenha números de série** – crie uma lista de valores separados por vírgulas de duas colunas (. csv) sem cabeçalho e limite a lista a 5.000 dispositivos ou 5 MB por arquivo. csv.

|||
|-|-|
|&lt;ID #1 &gt;|&lt;Device #1 detalhes @ no__t-1|
|&lt;ID #2 &gt;|&lt;Device #2 detalhes @ no__t-1|

Esse arquivo. csv quando exibido em um editor de texto aparece como:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Alguns dispositivos Android e iOS têm vários números IMEI. O Intune lê apenas um número IMEI por dispositivo registrado. Se você importar um número IMEI, mas não for o IMEI inventariado pelo Intune, o dispositivo será classificado como um dispositivo pessoal, em vez de um dispositivo de propriedade corporativa. Se você importar vários números IMEI para um dispositivo, os números de os exibirão **desconhecido** para o status do registro.<br>
>Observe também: os números de série são a forma recomendada de identificação para dispositivos iOS.
>Não há garantia de que os números de série do Android sejam exclusivos ou presentes. Verifique com o fornecedor do dispositivo para entender se o número de série é uma ID de dispositivo confiável.
>Os números de série relatados pelo dispositivo para o Intune podem não corresponder à ID exibida nas configurações do Android/sobre os menus no dispositivo. Verifique o tipo de número de série relatado pelo fabricante do dispositivo.
>A tentativa de carregar um arquivo com números de série que contenham pontos (.) causará falha no carregamento. Não há suporte para números de série com pontos.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Carregar uma lista. csv de identificadores corporativos

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro de dispositivo** > **identificadores de dispositivo corporativo** > **Adicionar** > **carregar arquivo CSV**.

   ![Espaço de trabalho identificador de dispositivo corporativo com o botão Adicionar realçado](./media/corporate-identifiers-add/add-corp-id.png)

2. Na folha **adicionar identificadores** , especifique o tipo de identificador: **IMEI** ou **serial**.

3. Clique no ícone de pasta e especifique o caminho para a lista que você deseja importar. Navegue até o arquivo. csv e escolha **Adicionar**. 

4. Se o arquivo. CSV contiver identificadores corporativos que já estão no Intune, mas tiverem detalhes diferentes, o pop-up **revisar identificadores duplicados** será exibido. Selecione os identificadores que você deseja substituir no Intune e escolha **OK** para adicionar os identificadores. Para cada identificador, somente a primeira duplicata será comparada.

## <a name="manually-enter-corporate-identifiers"></a>Inserir manualmente identificadores corporativos

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro de dispositivo** > **identificadores de dispositivo corporativo** > **Adicionar** > **Insira manualmente**.

2. Na folha **adicionar identificadores** , especifique o tipo de identificador: **IMEI** ou **serial**.

3. Insira o **identificador** e os **detalhes** para cada identificador que você deseja adicionar. Quando você terminar de inserir identificadores, escolha **Adicionar**.

5. Se você inseriu identificadores corporativos que já estão no Intune, mas tem detalhes diferentes, o pop-up **revisar identificadores duplicados** é exibido. Selecione os identificadores que você deseja substituir no Intune e escolha **OK** para adicionar os identificadores. Para cada identificador, somente a primeira duplicata será comparada.

Você pode clicar em **Atualizar** para ver novos identificadores de dispositivo.

Os dispositivos importados não são necessariamente registrados. Os dispositivos podem ter um estado de **registrado** ou **não contatado**. **Não contatado** significa que o dispositivo nunca se comunicará no com o serviço do Intune.

## <a name="delete-corporate-identifiers"></a>Excluir identificadores corporativos

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro de dispositivo** > **identificadores de dispositivo corporativo**.
2. Selecione os identificadores de dispositivo que você deseja excluir e escolha **excluir**.
3. Confirme a eliminação.

A exclusão de um identificador corporativo para um dispositivo registrado não altera a propriedade do dispositivo. Para alterar a propriedade de um dispositivo, acesse **dispositivos**, selecione o dispositivo, escolha **Propriedades**e altere a **Propriedade do dispositivo**.

## <a name="imei-specifications"></a>Especificações de IMEI
Para obter especificações detalhadas sobre identificadores de equipamentos móveis internacionais, consulte [3GGPP TS 23, 3](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Alterar a propriedade do dispositivo

As propriedades de dispositivos exibem a **Propriedade** para cada registro de dispositivo no Intune. Como administrador, você pode especificar dispositivos como **pessoais** ou **corporativos**.

**Para alterar a propriedade do dispositivo:**
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), vá para **dispositivos** e escolha o dispositivo.
2. Escolha **Propriedades**.
3. Especifique a **Propriedade do dispositivo** como **pessoal** ou **corporativo**.

   ![Propriedades do dispositivo mostrando as opções categoria do dispositivo e Propriedade do dispositivo](./media/corporate-identifiers-add/device-properties.png)
