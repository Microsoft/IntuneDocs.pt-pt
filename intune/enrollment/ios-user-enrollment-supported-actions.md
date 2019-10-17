---
title: Ações e opções do Intune com suporte com o registro de usuário da Apple
titleSuffix: Microsoft Intune
description: Saiba quais opções e ações do Intune têm suporte com o registro de usuário da Apple
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96c802e76aab673aa6a9108dc0a14f553c26b96b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505413"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Ações e opções do Intune com suporte com o registro de usuário da Apple

O registro de usuário dá suporte a um subconjunto de opções de gerenciamento de dispositivo. Se um perfil de configuração pré-existente for aplicado a um dispositivo de registro de usuário, somente as configurações com suporte do registro de usuário serão aplicadas a esse dispositivo.

## <a name="password-settings"></a>Definições de palavra-passe

Em dispositivos de registro de usuário, se você definir qualquer configuração de senha, as configurações de **senhas simples** serão automaticamente definidas como **Bloquear**e um PIN de 6 dígitos será imposto.

Por exemplo, você define a configuração de **expiração de senha** e envia por push essa política para dispositivos registrados pelo usuário. Nos dispositivos, acontece o seguinte:
- A configuração de **expiração de senha** é ignorada.
- Senhas simples, como `1111` ou `1234`, não são permitidas.
- Um PIN de 6 dígitos é imposto.

## <a name="administrator-remote-device-actions-and-options"></a>Ações e opções de dispositivo remoto do administrador
Os administradores podem executar as seguintes ações e opções em dispositivos de registro de usuário:
- Extinguir
- Eliminar
- Bloqueio Remoto
- Sincronizá

Não há suporte para todas as outras ações.

## <a name="end-user-actions"></a>Ações do usuário final
Em dispositivos de registro de usuário, os usuários finais podem executar essas ações em seus dispositivos no aplicativo Portal da Empresa e no site:
- Nome. Essa ação se aplica somente ao nome voltado para o usuário dentro do Portal da Empresa. Ele não renomeará completamente o dispositivo fora desse contexto.
- Remove
- Bloqueio Remoto
- Verificar status

## <a name="other-supported-options"></a>Outras opções com suporte

As opções a seguir têm suporte no Intune para dispositivos registrados usando o registro de usuário da Apple:
- VPN por aplicativo. Esse suporte exclui os domínios do Safari, pois o registro de usuário não dá suporte à definição das configurações do Safari.
- Fio 
- Remoção do aplicativo corporativo após o cancelamento do registro
- Implantação de aplicativo por meio do VPP (plano de compra por volume) licenciado pelo usuário
- Detecção de jailbreak

Há suporte para as seguintes restrições:
- Exibir documentos corporativos em aplicativos não gerenciados
- Exibindo documentos não corporativos em aplicativos corporativos
- Permitir que aplicativos não gerenciados leiam de contas de contatos gerenciados
- Descartar como um destino não gerenciado
- Backup criptografado necessário
- Sincronização de aplicativos gerenciados para a nuvem
- Acesso ao centro de controle enquanto o dispositivo está bloqueado
- Acesso ao centro de notificações enquanto o dispositivo está bloqueado
- Exibição atual enquanto o dispositivo está bloqueado
- Bloquear capturas de tela
- Bloquear o backup do catálogo corporativo
- Bloquear a sincronização de metadados do catálogo empresarial
- Exigir cópia de segurança encriptada
- Exigir detecção de pulso de inspeção
- Bloquear Siri
- Bloquear Siri enquanto o dispositivo estiver bloqueado
- Exigir avisos de fraude do Safari
- Bloquear o envio de diagnóstico para a Apple


## <a name="options-not-supported"></a>Opções sem suporte
As opções a seguir não têm suporte em dispositivos registrados com o registro do usuário. Se você precisar dessas opções, confira registro de dispositivo para dispositivos de propriedade pessoal ou registro de dispositivo automatizado para dispositivos corporativos.
- Coletar inventário de aplicativo para aplicativos fora do volume APFS gerenciado.
- Coletar inventário de certificados e perfis de provisionamento fora do volume APFS gerenciado.
- Coletar UDID e outros identificadores de dispositivo persistentes.
- O registro de usuário dá suporte a uma ID de registro exclusiva para cada dispositivo registrado, mas essa ID não persiste após o cancelamento do registro.
- Os seguintes recursos do Intune não têm suporte devido a essa limitação:
- Perfis de usuário SCEP com formato de nome de entidade de numbe Serial. r
- VPN no nível do dispositivo.
- Implantação de aplicativo VPP licenciado para dispositivo.
- Controle de MDM de aplicativos fora do volume APFS gerenciado.
- As políticas de proteção de aplicativo ainda serão aplicadas a esses aplicativos. No entanto, você não poderá assumir o gerenciamento ou implantar uma versão gerenciada desses aplicativos, a menos que o usuário os exclua de seus dispositivos.
- Ações, configurações, configurações e comandos que exigem supervisão. 

## <a name="next-steps"></a>Próximos passos

[Configurar o registro de usuário do iOS e iPadOS](ios-user-enrollment.md)