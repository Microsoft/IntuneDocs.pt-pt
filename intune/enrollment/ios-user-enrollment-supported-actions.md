---
title: Intune ações e opções suportadas com a Inscrição do Utilizador da Apple
titleSuffix: Microsoft Intune
description: Saiba quais as ações e opções intune que são suportadas com a Inscrição do Utilizador da Apple
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/14/2020
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
ms.openlocfilehash: 9c6fb7da3a791d369fc3005367ee7670af8bc63e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414139"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Intune ações e opções suportadas com a Inscrição do Utilizador da Apple

A Inscrição do Utilizador suporta um subconjunto de opções de gestão de dispositivos. Se for aplicado um perfil de configuração pré-existente a um dispositivo de inscrição do utilizador, apenas serão aplicadas configurações suportadas pela Inscrição do Utilizador nesse dispositivo.

> [!NOTE]
> O suporte para a inscrição de utilizadores da Apple em Intune está atualmente em pré-visualização para iOS e iPadOS.

## <a name="password-settings"></a>Definições de palavra-passe

Nos dispositivos de inscrição do utilizador, se configurar qualquer definição de palavra-passe, as definições **de palavras-passe Simples** são automaticamente definidas para **Bloquear**, e um PIN de 6 dígitos é aplicado.

Por exemplo, configura a definição de validade da **Palavra-passe** e empurra esta política para dispositivos inscritos pelo utilizador. Nos dispositivos, acontece o seguinte:
- A definição de expiração da **palavra-passe** é ignorada.
- Não são permitidas senhas simples, como `111111` ou `123456`.
- Um pino de 6 dígitos é imposto.

## <a name="administrator-remote-device-actions-and-options"></a>Ações e opções de dispositivos remotos administrador
Os administradores podem executar as seguintes ações e opções em dispositivos de inscrição do utilizador:
- Extinguir
- Eliminar
- Bloqueio Remoto
- Sincronizar

Todas as outras ações não são apoiadas.

## <a name="end-user-actions"></a>Ações de utilizador final
Nos dispositivos de inscrição do utilizador, os utilizadores finais podem executar estas ações nos seus dispositivos a partir da aplicação e website do Portal da Empresa:
- Mudar o nome. Esta ação aplica-se apenas ao nome virado para o utilizador dentro do Portal da Empresa. Não vai mudar completamente o nome do dispositivo fora desse contexto.
- Remove
- Bloqueio Remoto
- Verificar estado

## <a name="app-deployment-options"></a>Opções de implementação de aplicativos
Os seguintes tipos de aplicações podem ser implementados em dispositivos de inscrição do utilizador:
- Aplicativos do Plano de Compra de Volume (VPP) licenciados pelo utilizador, incluindo aplicações personalizadas
- Aplicações de linha de negócio (LOB)
- Aplicações Web

## <a name="other-supported-options"></a>Outras opções apoiadas

As seguintes opções são suportadas em Intune para dispositivos matriculados utilizando a inscrição do Utilizador da Apple:
- VPN por app. Este suporte exclui os Domínios do Safari, uma vez que a inscrição do utilizador não suporta configurar as definições do Safari.
- Wi-Fi 
- Remoção de aplicativos corporativos após não inscrição
- Deteção de Jailbreak

As seguintes restrições são suportadas:
- Ver documentos corporativos em aplicações não geridas
- Visualização de documentos não corporativos em aplicações corporativas
- Permitir que aplicações não geridas leiam a partir de contas de contactos geridas
- AirDrop como um destino não gerido
- Cópia de segurança encriptada necessária
- Aplicativos geridos sincronizam-se com a nuvem
- Acesso do Centro de Controlo enquanto dispositivo bloqueado
- Acesso do Centro de Notificação enquanto dispositivo bloqueado
- Vista de hoje enquanto dispositivo bloqueado
- Imagens de blocos
- Backup do Livro de Empresas de Bloco
- Sincronização de metadados do Livro da Empresa de Blocos
- Exigir cópia de segurança encriptada
- Requerem a deteção do pulso do relógio
- Bloco Siri
- Bloqueie a Siri enquanto o dispositivo está bloqueado
- Requeiram avisos de fraude do Safari
- Submissão de diagnósticos de blocos à Apple


## <a name="options-not-supported"></a>Opções não suportadas
As seguintes opções não são suportadas em dispositivos matriculados com inscrição no utilizador. Se precisar destas opções, consulte a Inscrição do Dispositivo para dispositivos pessoais ou inscrição automática de dispositivos para dispositivos corporativos.
- Colete o inventário de aplicativos para apps fora do volume APFS gerido.
- Recolher o inventário dos certificados e dos perfis de provisionamento fora do volume APFS gerido.
- Colete UDID e outros identificadores de dispositivos persistentes.
- A Inscrição do Utilizador suporta um ID de inscrição único para cada dispositivo matriculado, mas este ID não persiste após a não inscrição.
- As seguintes funcionalidades Intune não são suportadas por causa desta limitação:
- Perfis de utilizador SCEP com formato de nome de nome de série.
- VPN ao nível do dispositivo.
- Implementação de aplicativos VPP licenciados por dispositivos.
- Instale aplicações da App Store como aplicações geridas.
- Controlo de APLICAções mdm fora do volume APFS gerido.
- As Políticas de Proteção de Aplicações continuarão a aplicar-se a estas aplicações. No entanto, não será capaz de assumir a gestão ou implementar uma versão gerida destas aplicações, a menos que o utilizador as elimine do seu dispositivo.
- Ações, configurações, configurações e comandos que requerem supervisão. 


## <a name="known-issues-in-preview"></a>Questões conhecidas na pré-visualização
- Revogação da licença VPP: Não aparece uma notificação de que a licença foi revogada. O comportamento atual é que a revogação é bem sucedida, mas o utilizador final não é notificado. 
- Relatório de aplicações VPP: No relatório localizado nas Aplicações clientes > Apps > [Nome da Aplicação] > Estado de Instalação de Dispositivos, as aplicações VPP implementadas para dispositivos Inscritos no Utilizador estão a reportar como "falhadas", mesmo quando a aplicação se implementa com sucesso no dispositivo. 
- Relatório de aplicação: Para tipos de aplicações não suportados com inscrição de utilizador, os relatórios podem fornecer mensagens de erro irrelevantes. 
- Experiência de aplicação do Portal da Empresa: Os utilizadores vêem todas as aplicações direcionadas para os mesmos, independentemente de esses tipos de aplicações serem suportados para dispositivos Inscritos no Utilizador. 
- Experiência de aplicação do Portal da Empresa: Os utilizadores vêem o mesmo texto indicando o que as organizações podem ver para a Inscrição de Utilizadores e Dispositivos se o administrador personalizar o texto indicando o que as organizações não podem ver.


## <a name="next-steps"></a>Próximos passos

[Configurar iOS/iPadOS e iPadOS User Enrollment](ios-user-enrollment.md)
