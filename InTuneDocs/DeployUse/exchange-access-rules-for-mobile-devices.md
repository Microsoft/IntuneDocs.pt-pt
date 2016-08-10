---
title: "Regras de acesso ao Exchange para dispositivos móveis | Microsoft Intune"
description: "As regras de acesso do Exchange ActiveSync para permitir ou bloquear as ligações do dispositivo com o EAS"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c49e19e8c478af252d7b59c380d5500a57b71db5
ms.openlocfilehash: 7714a338d02afedde2ac090964e4d18d4410a80e


---

# Regras de acesso ao Exchange para dispositivos móveis
As regras de acesso ao Exchange para dispositivos móveis determinam o nível de acesso ao Exchange ActiveSync que é concedido a esses dispositivos. Esta definição afeta todos os dispositivos móveis, incluindo os que não estão inscritos no Microsoft Intune. Pode começar por definir uma **Regra Predefinida** que será aplicada a todos os dispositivos móveis que não tenham uma regra personalizada aplicada. A tabela seguinte contém os níveis de acesso geridos pelo Exchange ActiveSync:

|Nível de acesso|Descrição|
|----------------|---------------|
|**Permitir que os dispositivos móveis acessem o Exchange**|No estado *permitir acesso*, os dispositivos móveis podem ser sincronizados através do Exchange ActiveSync e ligar ao servidor do Exchange para obter e-mails e gerir o Calendário, Contactos, Tarefas e Notas. Isto continuará a ser efetuado desde que o dispositivo cumpra a política de caixa de correio do Exchange Active Sync configurada no Exchange, a não ser que o utilizador ou o dispositivo móvel específico tenha sido bloqueado pelo administrador do Exchange.|
|**Bloquear os dispositivos móveis de acessar o Exchange**|No estado *bloquear acesso*, os dispositivos móveis são bloqueados e não têm permissão para ligar ao servidor do Exchange. Os dispositivos irão receber um erro de HTTP 403 Proibido. O utilizador receberá uma mensagem de e-mail do servidor do Exchange com a informação de que o acesso do dispositivo móvel à respetiva caixa de correio foi bloqueado. Esta mensagem não pode estar no dispositivo móvel bloqueado. Pode adicionar texto personalizado a esta mensagem para fornecer instruções aos utilizadores cujos dispositivos foram bloqueados através da tarefa **Definir Notificação do Utilizador**.|
|**Colocar os dispositivos móveis em quarentena para que você possa permiti-los ou bloqueá-los mais tarde**|Quando um dispositivo móvel é colocado em quarentena, este pode ligar-se ao servidor do Exchange. No entanto, tem acesso limitado aos dados. O utilizador pode adicionar conteúdo às respetivas pastas Calendário, Contactos, Tarefas e Notas, mas o servidor não permitirá que o dispositivo obtenha conteúdo da caixa de correio do utilizador. O utilizador receberá uma única mensagem de e-mail a indicar que o dispositivo móvel foi colocado em quarentena. Esta mensagem é recebida no dispositivo e na caixa de correio do utilizador. Pode adicionar texto personalizado a esta mensagem para fornecer instruções aos utilizadores cujos dispositivos foram colocados em quarentena através da tarefa **Definir Notificação do Utilizador** .|

Uma estratégia de acesso é uma combinação de uma **Regra Predefinida** e de **Exceções de Plataforma** aplicáveis a todos os dispositivos móveis ligados ao Exchange. A tabela abaixo apresenta alguns exemplos de estratégias de acesso.

|Estratégia de acesso|Descrição|
|-------------------|---------------|
|Lista de permissões|Pode utilizar uma *lista de permissões* para conceder acesso a uma lista de dispositivos conhecidos e restringir o acesso aos restantes. Para o fazer, tem de criar regras personalizadas para as plataformas dos dispositivos tenham permissão para aceder às caixas de correio dos utilizadores. Ao criar esta regra, tem de definir o bloqueio ou a colocação dos restantes dispositivos em quarentena como regra de acesso predefinida. Para adicionar um dispositivo novo à lista de permissões, crie uma nova regra personalizada|
|Lista de bloqueios|Pode utilizar uma *lista de bloqueios* para conceder o acesso a todos os dispositivos por predefinição e para impedir o acesso a um conjunto de dispositivos que não que acedam à sua organização. Pode criar uma lista de bloqueios ao criar regras personalizadas para impedir que as plataformas dos dispositivos pretendidos sejam sincronizados com as caixas de correio da organização. A permissão do acesso a todos os dispositivos que não foram explicitamente bloqueados pelas regras existentes deve ser definida como a regra predefinida. Para adicionar um dispositivo ou conjunto de dispositivos novo à lista de bloqueios, crie uma nova regra personalizada.|
|Autorizações e bloqueios mistos|Além de criar listas de permissões e bloqueios, pode colocar novos dispositivos móveis em quarentena, à medida que estes são introduzidos na organização, ao mesmo tempo que os avalia. Por exemplo, se tiver uma lista de bloqueios de dispositivos móveis que não têm permissão na sua organização e uma lista de permissões de dispositivos móveis permitidos na organização, pode definir a colocação em quarentena como a regra predefinida. Todos os restantes dispositivos serão automaticamente colocados em quarentena. Isto permite descobrir novos dispositivos à medida que estes são introduzidos na organização e decidir se pretende adicionar os mesmos à lista de permissões ou à lista de bloqueios.|
O procedimento seguinte descreve o processo de criação de uma regra personalizada.

## Criar uma regra de acesso predefinida

1.  Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) &gt; **Política** &gt; **Exchange ActiveSync**.

2.  Na lista **Regra Predefinida** , selecione a Regra de Acesso que pretende aplicar a todos os dispositivos móveis não abrangidos por uma regra ou uma isenção pessoal. Escolha **Guardar**.

O procedimento seguinte descreve o processo de criação de uma regra personalizada.

## Criar uma regra de acesso personalizada

1. Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) &gt; **Política** &gt; **Exchange ActiveSync**.

2.  Na lista **Exceções de Plataforma**, escolha **Adicionar Regra** e crie uma regra personalizada. Escolha **Guardar**.



<!--HONumber=Aug16_HO1-->


