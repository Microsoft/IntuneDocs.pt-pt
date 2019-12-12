---
title: Preparar o Intune para a gestão de dispositivos móveis
titleSuffix: Microsoft Intune
description: Avalie os requisitos técnicos e empresariais antes de migrar para o Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe44d2215c3c70de504e9bf95596b274a613f42a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505275"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>Fase 1: preparar o Microsoft Intune para a gestão de dispositivos móveis (MDM)

Antes de explorar os detalhes da configuração do Intune, vamos rever os requisitos da gestão de dispositivos móveis da sua organização. Poderá ser útil executar relatórios de utilizadores ativos no seu fornecedor de MDM atual para identificar os grupos de utilizadores críticos. Em seguida, você pode começar a abordar as perguntas na seção [avaliar requisitos de MDM](migration-guide-prepare.md#assess-mdm-requirements) .

## <a name="assess-mdm-requirements"></a>Avaliar requisitos de MDM

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Que tipos de dispositivos precisa de gerir?

- Que [plataformas](supported-devices-browsers.md) precisa de suportar?

- Os dispositivos que precisa suportar são dispositivos pessoais ou da empresa?

- Que tipo de conectividade utiliza? Wi-Fi, rede móvel, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>O que é que os seus utilizadores precisam de fazer em dispositivos geridos?

- Precisa de aprovisionar aplicações para os utilizadores finais?

- Utiliza aplicações de linha de negócio personalizadas? Ou só precisa de aplicações do arquivo público?

- Precisa de aprovisionar contas de e-mail?

### <a name="what-kinds-of-users"></a>Que tipos de utilizadores?

- Quantos utilizadores irão utilizar um único dispositivo?

- Que termos de utilização precisa?

  - Envolva o departamento jurídico neste aspeto desde o início.
  - Qual é a localização necessária?

- Os utilizadores estão familiarizados com a tecnologia e a TI em geral?

### <a name="what-is-your-device-security-policy"></a>Qual é a sua política de segurança de dispositivos?

- Precisa de encriptação ao nível do dispositivo?

- Quais são os comprimentos do código de acesso/PIN do seu dispositivo atual?

- Precisa de desativar funcionalidades do dispositivo ou restringir determinados comportamentos do dispositivo? Pode controlar várias definições específicas da plataforma com perfis de configuração de dispositivos, por exemplo:
  - Desativar a câmara
  - Bloquear no modo de aplicação única<br/>

- Que tipos de autenticação tem de suportar? Se precisar de uma autenticação baseada em certificados, que tipos de certificados têm de ser aprovisionados?
  - O Intune pode aprovisionar certificados com perfis de acesso a recursos para os dispositivos inscritos.
  - Que tipo de Infraestrutura de Chaves Públicas (PKI) precisa de suportar?
  <br></br>
- Precisa de suportar a Rede Privada Virtual (VPN) ao nível do dispositivo ou da aplicação?

  - O Intune pode aprovisionar configurações de VPN para fornecedores de VPN de terceiros.
  <br/><br/>
- Podem ser feitas exceções temporárias para determinados requisitos de forma a evitar períodos de inatividade? Ou os dispositivos com acesso cumprem sempre todos os requisitos de segurança?

## <a name="next-steps"></a>Próximos passos
Leia estes [casos práticos](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) de setores da indústria diferentes para ver como as organizações avaliaram os respetivos requisitos para a gestão de dispositivos móveis.

Reveja a [configuração básica do Intune](migration-guide-setup.md).
