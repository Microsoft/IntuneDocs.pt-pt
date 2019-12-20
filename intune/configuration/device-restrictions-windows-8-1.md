---
title: Windows 8.1 configurações de restrição de dispositivo no Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Saiba que definições do Intune pode utilizar para controlar as definições e funcionalidades em dispositivos com o Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82eaf1bc2c0737e1cc54751ff6fb5751227d180c
ms.sourcegitcommit: 42183c87b137710b8529049f8710d47127e99900
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302969"
---
# <a name="microsoft-intune-windows-81-device-restriction-settings"></a>Microsoft Intune Windows 8.1 configurações de restrição de dispositivo

Este artigo mostra as configurações Microsoft Intune restrições de dispositivo que você pode definir para dispositivos que executam o Windows 8.1.

## <a name="general"></a>Geral

- **Submissão de dados de diagnóstico** – Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.
- **Firewall** – Requer que a Firewall do Windows esteja ativada.
- **Controlo de Conta de Utilizador** – Requer a utilização do Controlo de Conta de Utilizador (UAC) nos dispositivos.

## <a name="password"></a>Palavra-passe
- **Tipo obrigatório de palavra-passe** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
- **Comprimento mínimo da palavra-passe** – Configura o comprimento mínimo obrigatório (em carateres) da palavra-passe.
- **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Elimina os dados do dispositivo se as tentativas de início de sessão falharem este número de vezes.
- **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica o número de minutos durante o qual um dispositivo tem de estar inativo antes de ser obrigatória uma palavra-passe para o desbloquear.
- **Expiração de palavra-passe (dias)** – especifica o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
- **Impedir a reutilização de palavras-passe anteriores** – Especifica se o utilizador pode utilizar as palavras-passe utilizadas anteriormente.
- **PIN e palavra-passe por imagem** – Permite a utilização de um PIN e de uma palavra-passe por imagem. Uma palavra-passe por imagem permite ao utilizador iniciar sessão com gestos numa imagem. Um PIN permite aos utilizadores iniciar sessão rapidamente com um código de quatro dígitos.
- **Encriptação** – requer que os ficheiros no dispositivo estejam encriptados.<br>Para impor a encriptação nos dispositivos que executam o Windows 8.1, tem de instalar a [atualização de cliente MDM para Windows de dezembro de 2014](https://support.microsoft.com/kb/3013816) em cada dispositivo.
Se ativar esta definição em dispositivos com o Windows 8.1, todos os utilizadores do dispositivo têm de ter uma conta Microsoft.
Para que a encriptação funcione, o dispositivo tem de estar em conformidade com os requisitos de certificação de hardware do [InstantGo da Microsoft](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97).
Quando impõe a encriptação a um dispositivo, a chave de recuperação só é acessível a partir da conta Microsoft do utilizador, que é acedida a partir da respetiva conta do OneDrive. Não pode recuperar esta chave em nome de um utilizador. 

## <a name="browser"></a>Browser
- **Preenchimento automático** – Permite que os utilizadores alterem as definições de conclusão automática no browser.
- **Avisos de fraude** – Ativa ou desativa avisos de sites potencialmente fraudulentos.
- **SmartScreen** – Ativa ou desativa avisos de sites potencialmente fraudulentos.
- **JavaScript** – Permite ao browser executar scripts, como scripts do Java.
- **Pop-ups** – Ativa ou desativa o bloqueador de janelas pop-up do browser.
- **Enviar cabeçalhos Do Not Track** – Envia um cabeçalho Do Not Track para os sites visitados no Internet Explorer.
- **Plug-ins** – Permite aos utilizadores adicionar plug-ins ao Internet Explorer.
- **Introdução de uma única palavra em site de intranet** – Permite a utilização de uma única palavra para direcionar o Internet Explorer para um site, como o Bing.
- **Deteção automática de site de intranet** – Ajuda a configurar a segurança para sites de intranet no Internet Explorer.
- **Nível de segurança da Internet** – Define o nível de segurança para os sites da Internet no Internet Explorer.
- **Nível de segurança de intranet** – Define o nível de segurança para os sites de intranet no Internet Explorer.
- **Nível de segurança de sites fidedignos** – Configura o nível de segurança da zona de sites fidedignos.
- **Segurança elevada para sites restritos** – Configura o nível de segurança da zona de sites restritos.
- **Acesso ao menu do modo de Empresa** – Permite aos utilizadores aceder às opções de menu do Modo de Empresa a partir do Internet Explorer.
Se selecionar esta definição, também pode especificar uma **Localização do relatório de registo**, a qual contém um URL para um relatório que mostra os sites para os quais os utilizadores ativaram o acesso Modo de Empresa.
- **Localização da lista de sites no Modo Empresarial** – Especifica a localização da lista de sites que utilizam o Modo Empresarial quando está ativo.

## <a name="cellular"></a>Rede móvel
- **Roaming de dados** – Permite dados em roaming quando o dispositivo estiver numa rede celular.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
- **URL de pastas de trabalho** – Define o URL da pasta de trabalho para permitir que os documentos sejam sincronizados em todos os dispositivos.
- **Acesso à aplicação Windows Mail sem uma conta Microsoft** – Ativa o acesso à aplicação Windows Mail sem uma conta Microsoft.

## <a name="next-steps"></a>Próximos passos

Crie um perfil de restrições de dispositivo no [Windows 10 e mais recente](device-restrictions-windows-10.md).
