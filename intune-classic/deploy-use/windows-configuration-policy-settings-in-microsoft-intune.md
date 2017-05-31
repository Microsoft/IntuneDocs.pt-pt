---
title: "Definições de políticas do Windows | Documentos da Microsoft"
description: "Utilize a política de configuração geral do Windows (Windows 8.1 e posterior) do Intune para configurar as definições para dispositivos Windows 8 e Windows 8.1 inscritos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d95852c20b98ee86552672cf03364980f06f010a
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="windows-policy-settings-in-microsoft-intune"></a>Definições de política do Windows no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize a **política de configuração geral do Windows (Windows 8.1 e posterior)** do Microsoft Intune para configurar as definições seguintes para dispositivos Windows 8, Windows 8.1 e Windows RT 8.1 inscritos:

## <a name="applicability-settings"></a>Definições de aplicabilidade

|Nome da definição|Detalhes|
|----------------|----------------------------------|
|**Aplicar todas as configurações ao Windows 10**|Permite que as definições nesta política possam ser aplicadas aos dispositivos Windows 10, além dos dispositivos Windows 8 e Windows 8.1.|

## <a name="security-settings"></a>Definições de segurança

|Nome da definição|Detalhes|
|----------------|------|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como alfanumérica ou apenas numérica.|
|**Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres**|Especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe. Existem quatro conjuntos de carateres: letras minúsculas, letras maiúsculas, números e símbolos. No entanto, para dispositivos iOS, esta definição especifica o número de símbolos que têm de ser incluídos na palavra-passe.|
|**Comprimento mínimo da palavra-passe**|Configura o comprimento mínimo necessário (em carateres) da palavra-passe.|
|**Número de falhas de início de sessão consecutivas a permitir antes de o dispositivo ser apagado**|Apaga o dispositivo em caso de falha deste número de tentativas de início de sessão.|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica o número de minutos durante o qual um dispositivo tem de estar inativo antes de ser necessária uma palavra-passe para o desbloquear.|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|
|**Memorizar histórico de palavras-passe**|Especifica se o utilizador pode utilizar as palavras-passe utilizadas anteriormente.|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.|
|**Permitir palavra-passe por imagem e PIN**|Permite a utilização de um PIN e de uma palavra-passe por imagem. Uma palavra-passe por imagem permite ao utilizador iniciar sessão com gestos numa imagem. Um PIN permite aos utilizadores iniciar sessão rapidamente com um código de quatro dígitos.|

## <a name="encryption-settings"></a>Definições de encriptação

|Nome da definição|Detalhes|
|----------------|-----|
|**Encriptação obrigatória no dispositivo móvel**<sup>1</sup>|Requer que os ficheiros no dispositivo estejam encriptados.|
<sup>1</sup> Informações adicionais para dispositivos com o Windows 8.1

-   Para impor a encriptação nos dispositivos que executam o Windows 8.1, tem de instalar a [atualização de cliente MDM para Windows de dezembro de 2014](http://support.microsoft.com/kb/3013816) em cada dispositivo.

-   Se ativar esta definição em dispositivos com o Windows 8.1, todos os utilizadores do dispositivo têm de ter uma conta Microsoft.

-   Para que a encriptação funcione, o dispositivo tem de estar em conformidade com os requisitos de certificação de hardware do [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) da Microsoft.

-   Quando impõe a encriptação a um dispositivo, a chave de recuperação só é acessível a partir da conta Microsoft do utilizador, que é acedida a partir da respetiva conta do OneDrive. Não pode recuperar esta chave em nome de um utilizador.

## <a name="malware-settings"></a>Definições de software maligno

|Nome da definição|Detalhes|
|----------------|-----|
|**Exigir firewall de rede**|Requer que a Firewall do Windows esteja ativada.|
|**Ativar SmartScreen**|Requer a utilização do Windows SmartScreen.|

## <a name="system-settings"></a>Definições do sistema

|Nome da definição|Detalhes|
|----------------|-------|
|**Exigir atualizações automáticas**|Ativa a definição de atualizações automáticas nos dispositivos.|
|**Exigir atualizações automáticas – classificação mínima de atualizações a instalar automaticamente**|Escolhe a classificação das atualizações que serão instaladas automaticamente:<br /><br />-   **Importante** – Instala todas as atualizações classificadas como importantes.<br />-   **Recomendada** – Instala todas as atualizações classificadas como importantes ou recomendadas.|
|**Controlo de Conta de Utilizador**|Requer a utilização do Controlo de Conta de Utilizador (UAC) nos dispositivos.|
|**Permitir submissão de dados de diagnóstico**|Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.|


## <a name="cloud-settings--documents-and-data"></a>Definições da cloud – documentos e dados

|Nome da definição|Detalhes|
|----------------|------|
|**URL das Pastas de Trabalho**|Define o URL da pasta de trabalho para permitir que os documentos sejam sincronizados em todos os dispositivos.|

## <a name="email-settings"></a>Definições de e-mail

|Nome da definição|Detalhes|
|----------------|-----|
|**Tornar a conta Microsoft opcional na aplicação Windows Mail**|Permite o acesso à aplicação Windows Mail sem uma conta Microsoft.|

## <a name="application-settings---browser"></a>Definições da aplicação – browser

|Nome da definição|Detalhes|
|----------------|-----|
|**Permitir preenchimento automático**|Permite que os utilizadores alterem as definições de conclusão automática no browser.|
|**Permitir bloqueador de janelas pop-up**|Ativa ou desativa o bloqueador de janelas pop-up do browser.|
|**Permitir plug-ins**|Permite aos utilizadores adicionar plug-ins ao Internet Explorer.|
|**Permitir scripting ativo**|Permite ao browser executar scripts, como scripts do Active X.|
|**Permitir aviso de fraude**|Ativa ou desativa avisos de sites potencialmente fraudulentos.|
|**Permitir site da intranet para introdução de uma única palavra**|Permite a utilização de uma única palavra para direcionar o Internet Explorer para um site, como o Bing.|
|**Permitir deteção automática de rede intranet**|Ajuda a configurar a segurança para sites intranet no Internet Explorer.|
|**Nível de segurança para a Internet**|Define o nível de segurança para os sites da Internet no Internet Explorer.|
|**Nível de segurança para a intranet**|Define o nível de segurança para os sites da intranet no Internet Explorer.|
|**Nível de segurança para sites fidedignos**|Configura o nível de segurança da zona de sites fidedignos.|
|**Nível de segurança para sites restritos**|Configura o nível de segurança da zona de sites restritos.|
|**Enviar cabeçalho Do Not Track**|Envia um cabeçalho Do Not Track para os sites visitados no Internet Explorer.|
|**Permitir acesso ao menu do Modo Empresarial**|Permite aos utilizadores aceder às opções de menu do Modo de Empresa a partir do Internet Explorer.<br>Se selecionar esta definição, também pode especificar uma **Localização do relatório de registo**, a qual contém um URL para um relatório que mostra os sites para os quais os utilizadores ativaram o acesso Modo de Empresa.|
|**Localização da lista de sites do Modo Empresarial**|Especifica a localização da lista de sites que utilizarão o Modo de Empresa quando este está ativo.|

## <a name="device-capabilities-settings---cellular"></a>Definições das capacidades do dispositivo – rede móvel

|Nome da definição|Detalhes|
|----------------|----|
|**Permitir roaming de dados**|Permite dados em roaming quando o dispositivo estiver numa rede celular.|



### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

