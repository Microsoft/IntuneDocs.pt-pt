---
title: "Definições de política do Windows | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a280fcbecf82e6ff27e40d2d53331b3988953ff7
ms.openlocfilehash: aa62528e588b0579669ab8d115766efd72e6f9b2


---

# Definições de política do Windows no Microsoft Intune
Utilize a **Política de configuração geral do Windows (Windows 8.1 e posterior)** para configurar as definições para dispositivos Windows 8.1 e Windows 8 inscritos:

## Definições de aplicabilidade

|Nome da definição|Detalhes|
|----------------|----------------------------------|
|**Aplicar todas as configurações ao Windows 10**|Permite que as definições nesta política possam ser aplicadas aos dispositivos Windows 10, além dos dispositivos Windows 8 e Windows 8.1.|

## Definições de segurança

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica.|Sim|Sim|
|**Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres**|Existem quatro conjuntos de carateres, letras minúsculas, letras maiúsculas, números e símbolos. Esta definição especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe. No entanto, para dispositivos iOS, isto especifica o número de carateres de símbolos que têm de ser incluídos na palavra-passe.|Sim|Sim|
|**Comprimento mínimo da palavra-passe**<sup>1</sup>|Configura o comprimento mínimo necessário (em carateres) da palavra-passe nos dispositivos.|Sim|Sim|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Apaga o dispositivo se o início de sessão falhar este número de vezes.|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**|Escolha o número de minutos durante o qual um dispositivo tem de estar inativo antes de ser necessária uma palavra-passe para o desbloquear.| Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Especifica se o utilizador pode utilizar as palavras-passe utilizadas anteriormente.|Sim|Sim|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.|Sim|Sim|
|**Permitir palavra-passe por imagem e PIN**|Permite a utilização de um PIN e de uma palavra-passe por imagem no dispositivo. Uma palavra-passe por imagem permite ao utilizador iniciar sessão com gestos numa imagem. Um PIN permite aos utilizadores iniciar sessão rapidamente com um código de 4 dígitos.|Sim|Sim|
<sup>1</sup> Quando implementa uma política de comprimento de palavra-passe em dispositivos com o Windows RT, os utilizadores serão forçados a repor as respetivas palavras-passe, ainda que estas estejam em conformidade com os requisitos da política.

## Definições de encriptação

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Encriptação obrigatória no dispositivo móvel**<sup>1</sup>|Requer que os ficheiros no dispositivo estejam encriptados.<br>Para dispositivos Windows Phone 8, tem de definir esta opção como **Sim**.|Sim|Não|
<sup>1</sup> Informações adicionais para dispositivos com o Windows 8.1

-   Para impor a encriptação nos dispositivos que executam o Windows 8.1, tem de instalar a [atualização de cliente MDM para Windows de dezembro de 2014](http://support.microsoft.com/kb/3013816) em cada dispositivo.

-   Se ativar esta definição em dispositivos com o Windows 8.1, todos os utilizadores do dispositivo têm de ter uma Conta Microsoft.

-   Para que a encriptação funcione, o dispositivo tem de estar em conformidade com os requisitos de certificação de hardware do [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) da Microsoft.

-   Quando impõe a encriptação a um dispositivo, a chave de recuperação só é acessível a partir da Conta Microsoft do utilizador, que é acedida a partir da respetiva conta do OneDrive. Não pode recuperar esta chave em nome de um utilizador.

## Definições de malware

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Requerer firewall de rede**|Requer que a Firewall do Windows esteja ativada.|Sim|Não|
|**Ativar SmartScreen**|Requer a utilização do Windows SmartScreen nos dispositivos.|Sim|Não|

## Definições do sistema

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Requerer atualizações automáticas**|Ative a definição de atualizações automáticas nos dispositivos.|Sim|Não|
|**Requerer atualizações automáticas – classificação mínima de atualizações a instalar automaticamente**|Escolha a classificação das atualizações que serão instaladas automaticamente:<br /><br />-   **Importante** – Instala todas as atualizações classificadas como importantes.<br />-   **Recomendada** – Instala todas as atualizações classificadas como importantes ou recomendadas.|Sim|Não|
|**Controlo de Conta de Utilizador**|Requer a utilização do Controlo de Conta de Utilizador (UAC) nos dispositivos.|Sim|Não|
|**Permitir submissão de dados de diagnóstico**|Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.|Sim|Não|


## Definições da nuvem - documentos e dados

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**URL das Pastas de Trabalho**|Define o URL da pasta de trabalho para permitir que os documentos sejam sincronizados em todos os dispositivos.|Sim|Não|

## Definições de e-mail

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Torne a conta Microsoft opcional na aplicação Windows Mail**|Permite o acesso à aplicação Windows Mail sem uma conta da Microsoft.|Sim|Não|

## Definições da aplicação - browser

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Permitir preenchimento automático**|O utilizador pode alterar as definições de conclusão automática no browser.|Sim|Não|
|**Permitir bloqueador de janelas de pop-up**|Ativa ou desativa o bloqueador de janelas pop-up do browser.|Sim|Não|
|**Permitir plug-ins**|O utilizador pode adicionar plug-ins ao Internet Explorer.|Sim|Não|
|**Permitir scripting ativo**|O browser pode executar scripts, como scripts do Active X.|Sim|Não|
|**Permitir aviso de fraude**|Ativar ou desativar avisos de sites potencialmente fraudulentos.|Sim|Não|
|**Permitir site da intranet para introdução de uma única palavra**|Permite a utilização de uma única palavra para direcionar o Internet Explorer para um site, como o Bing.|Sim|Não|
|**Permitir deteção automática de rede intranet**|Ajuda a configurar a segurança para sites intranet no Internet Explorer.|Sim|Não|
|**Nível de segurança para a Internet**|Defina o nível de segurança para os sites da Internet no Internet Explorer.|Sim|Não|
|**Nível de segurança para a intranet**|Defina o nível de segurança para os sites de intranet no Internet Explorer.|Sim|Não|
|**Nível de segurança para sites fidedignos**|Configurar o nível de segurança da zona de sites fidedignos.|Sim|Não|
|**Nível de segurança para sites restritos**|Configurar o nível de segurança da zona de sites restritos.|Sim|Não|
|**Enviar cabeçalho Do Not Track**|No Internet Explorer, envie um cabeçalho Do Not Track para os sites visitados.|Sim|Não|
|**Permitir acesso ao menu do Modo Empresarial**|Permite aos utilizadores aceder às opções de menu do Modo de Empresa a partir do Internet Explorer.<br>Se for selecionada, também pode especificar uma **Localização do relatório de registo** que contém um URL para um relatório que mostra os sites para os quais os utilizadores ativaram o acesso Modo de Empresa.|Sim|Não|
|**Localização da lista de sites do Modo Empresarial**|Especificar a localização da lista de sites que utilizarão o Modo de Empresa quando este está ativo.|Sim|Não|

## Definições das capacidades do dispositivo - rede móvel

|Nome da definição|Detalhes|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Permitir roaming de dados**|Permite o roaming de dados quando o dispositivo estiver numa rede celular.|Sim|Não|



### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


