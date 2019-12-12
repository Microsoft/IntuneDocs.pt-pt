---
title: Recolha de dados no Intune
titleSuffix: Microsoft Intune
description: Saiba como são recolhidos os dados pessoais no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e93e69b5cce2c54ae07410309b33870dd828f563
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509079"
---
# <a name="data-collection-in-intune"></a>Recolha de dados no Intune

Quando os utilizadores inscrevem os respetivos dispositivos pessoais ou de empresa com o Intune, o Intune recolhe e partilha alguns dados pessoais. O Intune recolhe dados pessoais das seguintes origens:

- A utilização que o administrador faz do Intune no portal do Azure.
- Os dispositivos de utilizador final (quando o utilizador final se inscreve na gestão do Intune e durante a utilização).
- As contas de cliente de serviços de terceiros (de acordo com as instruções do administrador).
- Informações de diagnóstico, desempenho e utilização.

Destas origens, o Intune recolhe informações que se encaixam nas três categorias seguintes: [identificados](#identified-data), [com pseudónimo](#pseudonymized-data) e [agregados](#aggregated-data).

> [!NOTE]
> Não vendemos nenhum dado coletado por nosso serviço para terceiros por qualquer motivo.

## <a name="identified-data"></a>Dados identificados

A maior parte dos dados pessoais que o Intune recolhe são dados identificados. Estes dados estão associados a um utilizador, dispositivo ou aplicação e são essenciais para a natureza da gestão. Os dados identificados são utilizados para gerir o dispositivo e as aplicações de um utilizador e para aprovisionar o serviço do Intune.

Os dados identificados que o Intune recolhe podem incluir, entre outros: 

- Informações do utilizador
  - Nome do proprietário/nome a apresentar do utilizador (o nome do utilizador registado no Azure conforme identificado pelo ID de Utilizador do Azure)
  - Nome Principal de Utilizador ou endereço de e-mail
  - Identidades de utilizador de terceiros (como o ID Apple)
- Informações do inventário de hardware
  - Nome do dispositivo
  - Manufacturer
  - Sistema operativo
  - Número de série
  - Número IMEI
  - Endereço IP
  - Endereço Mac Wi-Fi
  - ICCID
  - Número de telefone
- Informações de registo de auditoria, incluindo dados sobre as seguintes atividades
  - Gerir o Endpoint Protection do
  - Criar
  - Atualizar (editar)
  - Eliminar
  - Atribuir
  - Tarefas remotas
- Informações de suporte
  - Informações de contacto (nome, número de telefone, endereço de e-mail)
  - Conversações por e-mail com membros da equipa de suporte, produto e/ou da experiência do cliente da Microsoft
- Informações do controlo de acesso (o Intune utiliza estes dados para gerir o acesso a funções administrativas e a funções através de funcionalidades como o [Controlo de Acesso Baseado em Funções](../fundamentals/role-based-access-control.md).
  - Autenticadores estáticos (palavra-passe do cliente)
  - Chaves de privacidade para certificados 
- Informações de conta e de administrador
  - Nome próprio e apelido do utilizador administrador
  - Nome do utilizador administrador
  - UPN (e-mail)
  - Número de telefone
  - Endereço de e-mail do proprietário da conta
  - ID do Active Directory do administrador de TI de cada cliente
  - Dados de pagamento para a faturação do cliente
  - Chave de subscrição
- Inventário da aplicação, como
  - nome da aplicação
  - versão
  - ID da aplicação
  - tamanho
  - localização da instalação
  - Os dados de inventário da aplicação apenas são recolhidos quando são marcados pelo Administrador como dispositivo pertencente à propriedade ou quando a funcionalidade da aplicação de conformidade está ativada.  
- IDs de clientes de inquilinos de terceiros, como o ID Apple. 

## <a name="pseudonymized-data"></a>Dados com pseudónimo

Os dados com pseudónimo estão associados a um identificador exclusivo, que é normalmente um número gerado pelo sistema que não pode, por si só, identificar um indivíduo, mas que é utilizado para fornecer os serviços empresariais aos utilizadores. 

Os dados com pseudónimo que o Intune recolhe podem incluir, entre outros: 

- Dados de diagnóstico, desempenho e utilização associados a um utilizador e/ou dispositivo
  - O número de vezes que uma funcionalidade é utilizada
  - Os comandos fornecidos à funcionalidade
  - O tempo de resposta de um serviço
  - As taxas de êxito das instalações e de outros processos
  - Erros da aplicação do portal da empresa do Intune
  - Identificadores de utilizador e de dispositivo
  - Identificadores para efeitos de referência, correlação e gestão 
- Dados de dispositivo que não estão associados a um dispositivo ou utilizador (se estes dados estiverem associados a um dispositivo ou utilizador, o Intune trata-os como se fossem dados identificados)
  - ID de dispositivo do Intune
  - ID de dispositivo do Azure Active Directory
  - ID de gestão de dispositivos do Intune
  - ID de inquilino
  - ID de conta
  - ID de dispositivo EAS
  - IDs específicos de plataforma
  - ID Apple para dispositivos iOS
  - Endereço Mac para dispositivos Mac
  - ID Windows para dispositivos Windows
- Informações sobre a aplicação gerida
  - ID da aplicação gerida
  - Etiqueta de dispositivo da aplicação gerida
  - ID de gestão de dispositivos do Intune
  - ID de dispositivo do Azure Active Directory
  - Chaves de encriptação

## <a name="aggregated-data"></a>Dados agregados

Os dados agregados são utilizados para aprovisionar e melhorar o serviço do Intune. 

Os dados agregados que o Intune recolhe podem incluir, entre outros: 

- Dados de utilização de administrador provenientes de todos os inquilinos do Intune (por exemplo, controlos de administrador selecionados ao interagir com a Consola de administração)
- Informações da conta do inquilino (estes dados estão disponíveis a partir do painel do Intune)
  - Número de dispositivos ou utilizadores inscritos
  - Número de plataformas de dispositivo identificadas  
  - Número de dispositivos instalados
  - installedDeviceCount: o número de dispositivos em que a aplicação está instalada.
  - notApplicableDeviceCount: o número de dispositivos a que a aplicação não é aplicável.
  - notInstalledDeviceCount: o número de dispositivos a que a aplicação é aplicável, mas em que não está instalada.
  - pendingInstallDeviceCount: o número de dispositivos a que a aplicação é aplicável e em que a instalação está pendente.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre como o Intune [armazena e processa](privacy-data-store-process.md) e [partilha](privacy-data-secure-share.md) dados pessoais. 
