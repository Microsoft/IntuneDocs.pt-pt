---
title: "Ajudar os utilizadores finais a compreender as mensagens da aplicação Portal da Empresa | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 40f2ead80326a451dfd59a4969191009dc35deef


---

# Ajudar os utilizadores finais a compreender as mensagens da aplicação Portal da Empresa

As seguintes informações aplicam-se apenas a dispositivos Android 6.0 e posteriores. Durante a inscrição de dispositivos, os utilizadores finais veem duas mensagens, as quais são apresentados durante o processo de inscrição:

- Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?
- Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no seu dispositivo?

Consulte os parágrafos seguintes para obter detalhes sobre estas mensagens e informações que pode partilhar com os utilizadores finais sobre as mesmas.

## Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?

### Texto da mensagem e onde aparece
O texto da mensagem é **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?** e aparece quando os utilizadores iniciam sessão pela primeira vez na aplicação Portal da Empresa para iniciarem a inscrição do respetivo dispositivo.

### O que significa a mensagem
A mensagem está a pedir aos utilizadores para permitirem que o número de telefone e o IMEI do seu dispositivo sejam enviados para o serviço Intune e apresentados na consola de Administração, na página de Hardware.

> [!NOTE]
> **A aplicação do Portal da Empresa nunca efetua ou gere chamadas telefónicas!** O texto da mensagem é controlado pelo Google e não pode ser alterado.

Para ver a página **Hardware**, aceda a **Grupos** > **Todos os dispositivos móveis** > **Dispositivos**. Selecione o dispositivo do utilizador e aceda a **Ver Propriedades** > **Hardware**.

### O que acontece se os utilizadores permitirem ou negarem o acesso
Se os utilizadores permitirem o acesso, o número de telefone e o IMEI do dispositivo serão apresentados na página de Hardware na consola de Administração.

Se os utilizadores negarem o acesso, podem continuar a utilizar a aplicação Portal da Empresa e inscrever o respetivo dispositivo, mas o número de telefone e o IMEI do dispositivo do cliente estarão em branco na página de Hardware da consola de Administração. Na segunda vez que os utilizadores iniciam sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostra uma caixa de verificação **Não voltar a perguntar** que os utilizadores podem selecionar para que a mensagem não volte a aparecer.

Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores iniciarem sessão novamente na aplicação Portal da Empresa depois da inscrição.</br></br>Se, posteriormente, os utilizadores decidirem permitir o acesso, podem aceder a **Definições** > **Aplicações** > **Portal da Empresa** > **Permissões** > **Telemóvel** e, em seguida, ativar a permissão.

### Para onde enviar os seus utilizadores para obterem mais informações
Passo 5 em [Inscrever o dispositivo Android no Intune](/Intune/EndUser/enroll-your-device-in-intune-android)

## Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no seu dispositivo?

### Texto da mensagem e onde aparece
O texto da mensagem é **Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no seu dispositivo?** e aparece quando os utilizadores tocam em **Enviar dados** para enviar registos de dados para o administrador de TI.

### O que significa a mensagem
A mensagem está a pedir aos utilizadores para permitirem que o respetivo dispositivo escreva registos de dados no cartão SD do dispositivo e para permitirem que esses registos sejam movidos utilizando um cabo USB.   

> [!NOTE]
> **A aplicação Portal da Empresa nunca acede a multimédia, ficheiros e fotografias dos utilizadores!** O texto da mensagem é controlado pelo Google e não pode ser alterado.

### O que acontece se os utilizadores permitirem ou negarem o acesso
Se os utilizadores permitirem o acesso, os registos serão copiados para o cartão SD.

Se os utilizadores negarem o acesso, podem ainda enviar registos de dados, mas os registos não serão copiados para o cartão SD do dispositivo.

Na segunda vez que os utilizadores iniciam sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostra uma caixa de verificação **Não voltar a perguntar** que os utilizadores podem selecionar para que a mensagem não volte a aparecer. Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores tentarem enviar registos. Se, posteriormente, os utilizadores decidirem permitir o acesso, podem aceder a **Definições** > **Aplicações** > **Portal da Empresa** > **Permissões** > **Armazenamento** e, em seguida, ativar a permissão.

### Para onde enviar os seus utilizadores para obterem mais informações
[Enviar registos de dados de diagnóstico ao administrador de TI por e-mail](/Intune/EndUser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)


### Consulte também
[O que dizer aos utilizadores finais sobre a utilização do Intune](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)



<!--HONumber=Jul16_HO1-->


