---
# required metadata

title: Localizar um nome da família de pacotes (PFN) para VPN por aplicação | Microsoft Intune|
description:
keywords:
author: nbigman
manager: [ALIAS]
ms.date: 05/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: [ALIAS]
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Localizar um nome de família do produto (PFN) para a configuração de VPN por aplicação

Existem duas formas de localizar um PFN, de modo a que possa configurar uma VPN por aplicação.

## Localizar um PFN para uma aplicação que está instalada num computador Windows 10 

Se a aplicação com que está a trabalhar já estiver instalada num computador Windows 10, pode utilizar o cmdlet [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) do PowerShell para obter o PFN.

A sintaxe para Get-AppxPackage é:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> Nota: pode ter de executar o PowerShell como administrador para obter o PFN

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



## Localizar um PFN se a aplicação não estiver instalada num computador

1.  Aceda a https://www.microsoft.com/en-us/store/apps
2.  Introduza o nome da aplicação na barra de procura. No nosso exemplo, procure OneNote.
3.  Clique na ligação para a aplicação. Tenha em atenção que o URL a que acede tem uma série de letras no final. No nosso exemplo, o URL tem este aspeto:
`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  Noutro separador, cole o seguinte URL `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`,  substituindo `<app id>` pelo id de aplicação obtido a partir de https://www.microsoft.com/en-us/store/apps - a série de letras no final do URL no passo 3. No nosso exemplo, o exemplo do OneNote, teria de colar: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

No Edge, são apresentadas as informações que pretende; no Internet Explorer, clique em **Abrir** para ver as informações. O valor PFN é atribuído na primeira linha. Eis o aspeto dos resultados para o nosso exemplo:
 

`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`



<!--HONumber=May16_HO3-->


