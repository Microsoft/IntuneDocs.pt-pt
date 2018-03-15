---
title: Dados que o Intune envia para a Apple
titlesuffix: Azure portal
description: Lista de dados que o Intune envia para a Apple.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d23fdce58b9ef35fe292ca6570904320e0922f16
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/27/2018
---
# <a name="data-intune-sends-to-apple"></a>Dados que o Intune envia para a Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Quando um dos seguintes serviços da Apple está ativado num dispositivo, o Microsoft Intune estabelece uma ligação com a Apple e partilha informações do utilizador e do dispositivo com a mesma: 

- [Programa de Inscrição de Dispositivos (DEP) da Apple](device-enrollment-program-enroll-ios.md)
- [Certificado Push de MDM da Apple (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/en-us/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync.md)
- [Apple Volume Purchase Program (VPP)](vpp-apps-ios.md)

Antes de o Microsoft Intune poder estabelecer uma ligação, tem de criar uma conta Apple para cada um dos serviços da Apple.

A seguinte tabela lista os dados que o Microsoft Intune envia de um dispositivo para os serviços ativados da Apple. 

| Serviço | Dados enviados para a Apple | Utilizado para |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | Se o servidor aceitar o dispositivo, o dispositivo fornece o seu token de notificação push ao servidor. O servidor deve utilizar este token para enviar mensagens push para o dispositivo. Esta mensagem de registo também contém uma cadeia PushMagic. O servidor tem de memorizar esta cadeia e incluí-la em todas as mensagens push que enviar para o dispositivo. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token do servidor | Token de dispositivo de notificação push utilizado para autenticar no serviço da Apple. |
| ASM/DEP | nome_do_servidor | Um nome identificável para o servidor MDM. |
| ASM/DEP | uuid_do_servidor | Um identificador de servidor gerado pelo sistema. |
| ASM/DEP | id_do_administrador | Um ID Apple da pessoa que gerou os tokens atualmente em utilização. |
| ASM/DEP | nome_da_organização | O nome da organização. |
| ASM/DEP | e-mail_da_organização | O endereço de e-mail da organização. |
| ASM/DEP | telefone_da_organização | O telefone da organização. |
| ASM/DEP | morada_da_organização | A morada da organização. |
| ASM/DEP | id_da_organização | ID do cliente do DEP. Esta chave só está disponível na versão 3 do protocolo e posterior. |
| ASM/DEP | número_de_série | O número de série do dispositivo (cadeia). |
| ASM/DEP | modelo | O nome do modelo (cadeia). |
| ASM/DEP | descrição | Uma descrição do dispositivo (cadeia). |
| ASM/DEP | etiqueta_de_recursos | A etiqueta de recursos do dispositivo (cadeia). |
| ASM/DEP | estado_do_perfil | O estado da instalação do perfil. Valores possíveis: **vazio**, **atribuído**, **emitido** ou **removido**. |
| ASM/DEP | uuid_do_perfil | O ID exclusivo do perfil atribuído. |
| ASM/DEP | dispositivo_atribuído_por | O e-mail da pessoa que atribuiu o dispositivo. |
| ASM/DEP | so | O sistema operativo do dispositivo: iOS, OSX ou tvOS. Esta chave é válida na versão 2 do Protocolo do Servidor X e posterior. |
| ASM/DEP | família_do_dispositivo | A família de produtos Apple do dispositivo: iPad, iPhone, iPod, Mac ou Apple TV. Esta chave é válida na versão 2 do Protocolo do Servidor X e posterior. |
| ASM/DEP | nome_do_perfil | Cadeia. Um nome legível por humanos para o perfil. |
| ASM/DEP | número_de_telefone_de_suporte | Opcional. Cadeia. Um número de telefone de suporte da organização. |
| ASM/DEP | endereço_de_e-mail_de_suporte | Opcional. Cadeia. Um endereço de e-mail de suporte da organização. Esta chave é válida na versão 2 do Protocolo do Servidor X e posterior. |
| ASM/DEP | departamento | Opcional. Cadeia. O nome do departamento ou localização definido pelo utilizador. |
| ASM/DEP | dispositivos | Matriz de cadeias com números de série de dispositivos. (Poderá estar vazio.) |
| VPP | GUID do UserId do Intune | GUID gerado pelo Intune. |
| VPP | UPN do ID Apple gerido | O ID Apple especificado pelo Administrador ao configurar a ligação do token VPP com a Apple. |
| VPP | Número de Série | O número de série do dispositivo gerido. |

Para parar de utilizar os serviços da Apple com o Microsoft Intune e eliminar os dados, tem de desativar o token da Apple do Microsoft Intune e eliminar a sua conta Apple. Consulte a conta Apple para saber como desempenhar a gestão da conta.


