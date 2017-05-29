---
title: "Localizar um nome da família de pacotes (PFN) para VPN por aplicação | Documentos da Microsoft"
description: "Localize um PFN para que possa configurar uma VPN por aplicação."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ms.reviewer: tycast
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0fd7d7e1e09f193479c6ad221c8ace7470942c5a
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="find-a-package-family-name-pfn-for-per-app-vpn-configuration"></a>Localizar um nome da família de pacotes (PFN) para configuração de VPN por aplicação

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Existem duas formas de localizar um PFN, de modo a que possa configurar uma VPN por aplicação.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Localizar um PFN para uma aplicação que está instalada num computador Windows 10

Se a aplicação com que está a trabalhar já estiver instalada num computador Windows 10, pode utilizar o cmdlet [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) do PowerShell para obter o PFN.

A sintaxe de Get-AppxPackage é:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
Poderá ter de executar o PowerShell como administrador para obter o PFN.

Por exemplo, para obter informações sobre todas as aplicações universais instaladas no computador, utilize `Get-AppxPackage`.

Para obter informações sobre uma aplicação da qual sabe o nome, ou parte deste, utilize `Get-AppxPackage *<app_name>`. Tenha em atenção a utilização do caráter universal, particularmente útil se não tiver a certeza do nome completo da aplicação. Por exemplo, para obter as informações para o OneNote, utilize `Get-AppxPackage *OneNote`.


Eis as informações obtidas para o OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Localizar um PFN se a aplicação não estiver instalada num computador

1.    Aceda a https://www.microsoft.com/store/apps.
2.    Introduza o nome da aplicação na barra de procura. No nosso exemplo, procure OneNote.
3.    Escolha a ligação para a aplicação. Tenha em atenção que o URL tem uma série de letras no final. No nosso exemplo, o URL tem este aspeto: `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl`.
4.    Noutro separador, cole o seguinte URL, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`. Substitua `<app id>` pelo ID da aplicação obtido em https://www.microsoft.com/store/apps – a série de letras no final do URL no passo 3. No nosso exemplo do OneNote, teria de colar: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

O Microsoft Edge mostra as informações que pretende; no Internet Explorer, escolha **Abrir** para ver as informações. O valor de PFN é atribuído na primeira linha. Seguem-se os resultados do nosso exemplo:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`

