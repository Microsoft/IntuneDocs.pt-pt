---
title: "Definições de política do Windows | Microsoft Intune"
description: "Utilize a política de configuração geral do Windows (Windows 8.1 e posterior) do Intune para configurar as definições para dispositivos Windows 8 e Windows 8.1 inscritos."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 073e3df63a5de9cf92c739c1ced858e21a9ac351
ms.openlocfilehash: 6b2d805561067d2dc0de70d93c45622a951e5981


---

# Definições de política do Windows no Microsoft Intune
Utilize a **política de configuração geral do Windows (Windows 8.1 e posterior)** do Microsoft Intune para configurar as definições seguintes para dispositivos Windows 8 e Windows 8.1 inscritos:

## Definições de aplicabilidade

|Nome da definição|Detalhes|
|----------------|----------------------------------|
|**Aplicar todas as configurações ao Windows 10**|Permite que as definições nesta política possam ser aplicadas aos dispositivos Windows 10, além dos dispositivos Windows 8 e Windows 8.1.|

## Definições de segurança

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como alfanumérica ou apenas numérica.|Sim|Sim|
|**Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres**|Especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe. Existem quatro conjuntos de carateres: letras minúsculas, letras maiúsculas, números e símbolos. No entanto, para dispositivos iOS, esta definição especifica o número de símbolos que têm de ser incluídos na palavra-passe.|Sim|Sim|
|**Comprimento mínimo da palavra-passe**<sup>1</sup>|Configura o comprimento mínimo necessário (em carateres) da palavra-passe.|Sim|Sim|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Apaga o dispositivo em caso de falha deste número de tentativas de início de sessão.|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica o número de minutos durante o qual um dispositivo tem de estar inativo antes de ser necessária uma palavra-passe para o desbloquear.| Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Especifica se o utilizador pode utilizar as palavras-passe utilizadas anteriormente.|Sim|Sim|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.|Sim|Sim|
|**Permitir palavra-passe por imagem e PIN**|Permite a utilização de um PIN e de uma palavra-passe por imagem. Uma palavra-passe por imagem permite ao utilizador iniciar sessão com gestos numa imagem. Um PIN permite aos utilizadores iniciar sessão rapidamente com um código de quatro dígitos.|Sim|Sim|
<sup>1</sup>Quando implementa uma política de comprimento de palavra-passe em dispositivos com o Windows RT, os utilizadores serão forçados a repor as respetivas palavras-passe, ainda que estas estejam em conformidade com os requisitos da política.

## Definições de encriptação

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Encriptação obrigatória no dispositivo móvel**<sup>1</sup>|Requer que os ficheiros no dispositivo estejam encriptados.<br>Para dispositivos Windows Phone 8, tem de definir esta opção como **Sim**.|Sim|Não|
<sup>1</sup> Informações adicionais para dispositivos com o Windows 8.1

-   Para impor a encriptação nos dispositivos que executam o Windows 8.1, tem de instalar a [atualização de cliente MDM para Windows de dezembro de 2014](http://support.microsoft.com/kb/3013816) em cada dispositivo.

-   Se ativar esta definição em dispositivos com o Windows 8.1, todos os utilizadores do dispositivo têm de ter uma conta Microsoft.

-   Para que a encriptação funcione, o dispositivo tem de estar em conformidade com os requisitos de certificação de hardware do [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) da Microsoft.

-   Quando impõe a encriptação a um dispositivo, a chave de recuperação só é acessível a partir da conta Microsoft do utilizador, que é acedida a partir da respetiva conta do OneDrive. Não pode recuperar esta chave em nome de um utilizador.

## Definições de malware

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Requerer firewall de rede**|Requer que a Firewall do Windows esteja ativada.|Sim|Não|
|**Ativar SmartScreen**|Requer a utilização do Windows SmartScreen.|Sim|Não|

## Definições do sistema

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-------|---------------------------|--------------|
|**Requerer atualizações automáticas**|Ativa a definição de atualizações automáticas nos dispositivos.|Sim|Não|
|**Requerer atualizações automáticas – classificação mínima de atualizações a instalar automaticamente**|Escolhe a classificação das atualizações que serão instaladas automaticamente:<br /><br />-   **Importante** – Instala todas as atualizações classificadas como importantes.<br />-   **Recomendada** – Instala todas as atualizações classificadas como importantes ou recomendadas.|Sim|Não|
|**Controlo de Conta de Utilizador**|Requer a utilização do Controlo de Conta de Utilizador (UAC) nos dispositivos.|Sim|Não|
|**Permitir submissão de dados de diagnóstico**|Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.|Sim|Não|


## Definições da nuvem - documentos e dados

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**URL das Pastas de Trabalho**|Define o URL da pasta de trabalho para permitir que os documentos sejam sincronizados em todos os dispositivos.|Sim|Não|

## Definições de e-mail

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Torne a conta Microsoft opcional na aplicação Windows Mail**|Permite o acesso à aplicação Windows Mail sem uma conta Microsoft.|Sim|Não|

## Definições da aplicação - browser

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Permitir preenchimento automático**|Permite que os utilizadores alterem as definições de conclusão automática no browser.|Sim|Não|
|**Permitir bloqueador de janelas de pop-up**|Ativa ou desativa o bloqueador de janelas pop-up do browser.|Sim|Não|
|**Permitir plug-ins**|Permite aos utilizadores adicionar plug-ins ao Internet Explorer.|Sim|Não|
|**Permitir scripting ativo**|Permite ao browser executar scripts, como scripts do Active X.|Sim|Não|
|**Permitir aviso de fraude**|Ativa ou desativa avisos de web sites potencialmente fraudulentos.|Sim|Não|
|**Permitir site da intranet para introdução de uma única palavra**|Permite a utilização de uma única palavra para direcionar o Internet Explorer para um site, como o Bing.|Sim|Não|
|**Permitir deteção automática de rede intranet**|Ajuda a configurar a segurança para sites intranet no Internet Explorer.|Sim|Não|
|**Nível de segurança para a Internet**|Define o nível de segurança para os sites da Internet no Internet Explorer.|Sim|Não|
|**Nível de segurança para a intranet**|Define o nível de segurança para os sites da intranet no Internet Explorer.|Sim|Não|
|**Nível de segurança para sites fidedignos**|Configura o nível de segurança da zona de sites fidedignos.|Sim|Não|
|**Nível de segurança para sites restritos**|Configura o nível de segurança da zona de sites restritos.|Sim|Não|
|**Enviar cabeçalho Do Not Track**|Envia um cabeçalho Do Not Track para os sites visitados no Internet Explorer.|Sim|Não|
|**Permitir acesso ao menu do Modo Empresarial**|Permite aos utilizadores aceder às opções de menu do Modo de Empresa a partir do Internet Explorer.<br>Se selecionar esta definição, também pode especificar uma **Localização do relatório de registo**, a qual contém um URL para um relatório que mostra os web sites para os quais os utilizadores ativaram o acesso Modo de Empresa.|Sim|Não|
|**Localização da lista de sites do Modo Empresarial**|Especifica a localização da lista de web sites que utilizarão o Modo de Empresa quando este está ativo.|Sim|Não|

## Definições das capacidades do dispositivo - rede móvel

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----|------------------------------|--------------|
|**Permitir roaming de dados**|Permite dados em roaming quando o dispositivo estiver numa rede celular.|Sim|Não|



### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Sep16_HO2-->


