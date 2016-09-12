---
title: Resolver problemas com perfis de e-mail| Microsoft Intune
description: "Problemas de perfis de e-mail e como resolvê-los."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 08/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: 79076b65fe85adeaffd5435915cb5eca2a15413f


---

# Resolver problemas com perfis de e-mail no Microsoft Intune
Alguns problemas de perfis de e-mail e a forma de resolvê-los encontram-se descritos aqui.

Se estas informações não resolverem o problema, veja [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](how-to-get-support-for-microsoft-intune.md) para ver mais formas de ajuda.


## Não é possível enviar imagens a partir da conta de e-mail
Os utilizadores que têm contas de e-mail configuradas automaticamente não conseguem enviar imagens a partir dos dispositivos deles.
Isto ocorre quando a opção **Permitir o envio de e-mails a partir de aplicações de terceiros** não está ativada.

### Solução do Intune

1.  Abra a Consola de Administração do Microsoft Intune, selecione a carga de trabalho **Política** &gt;**Política de Configuração**.

2.  Selecione o perfil de e-mail e escolha **Editar**.

3.  Selecione **Permitir o envio de e-mails a partir de aplicações de terceiros.**

### Solução do Configuration Manager integrado com o Intune

1.  Abra a consola do Configuration Manager &gt; **Ativos e Conformidade**.

2.  Expanda **Descrição Geral** -&gt; **Definições de Conformidade** -&gt; **Acesso a Recursos da Empresa** e selecione **Perfis de E-mail**.

3.  Clique com o botão direito do rato no perfil de e-mail e abra **Propriedades**.

4.  No separador **Definições de Sincronização**, selecione **Permitir o envio de e-mails a partir de aplicações de terceiros**.


## O dispositivo já tem um perfil de email instalado

Se o utilizador tiver instalado um perfil de e-mail anterior ao aprovisionamento de um perfil pelo Intune, sendo que o resultado da implementação do perfil de e-mail do Intune depende da plataforma do dispositivo:

-**iOS**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. Um perfil de e-mail duplicado criado pelo utilizador irá bloquear a implementação de um perfil do Intune criado pelo administrador. Este é um problema comum, uma vez que os utilizadores do iOS criam um perfil de e-mail e depois fazem a inscrição. O portal da empresa irá informar o utilizador da não conformidade devido ao respetivo perfil de e-mail configurado manualmente e solicitará ao utilizador para remover esse perfil. O utilizador deve remover o respetivo perfil de e-mail, para que o perfil do Intune possa ser implementado. Para evitar este problema, indique aos seus utilizadores para inscreverem-se antes de instalar um perfil de e-mail e para permitir que o Intune implemente o perfil.

-**Windows**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. O Intune vai substituir o perfil de e-mail existente criado pelo utilizador.

-**Samsung KNOX**: o Intune identifica uma conta de e-mail duplicada com base no endereço de e-mail e substituí-lo com o perfil do Intune. Se o utilizador configurar essa conta, esta será substituída novamente pelo perfil do Intune. Tenha em atenção que isto pode causar alguma confusão ao utilizador cuja configuração de conta seja substituída.

Dado que o Samsung KNOX não utiliza o nome de anfitrião para identificar o perfil, recomendamos que não crie múltiplos perfis de e-mail para implementar o mesmo endereço de e-mail em diferentes anfitriões, como estes serão substituídas entre si.

## Erro 0x87D1FDE8 para dispositivo KNOX
**Problema**: depois de criar e implementar um perfil de e-mail do Exchange Active Sync para Samsung KNOX em vários dispositivos Android, é comunicado o erro **0x87D1FDE8** ou **falha na remediação** no separador propriedades &gt; política do dispositivo.

Reveja a configuração do seu perfil EAS para Samsung KNOX e a política de origem. A opção de sincronização do Samsung Notes já não é suportada e não deve ser selecionada no seu perfil. Certifique-se de que os dispositivos têm tido tempo suficiente para processar a política, até 24 horas.

## Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Aug16_HO1-->


