---
title: Resolver problemas relacionados com perfis de e-mail
description: "Problemas de perfis de e-mail e como resolvê-los."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f79ebec4dea17bd03b88d97aa1d7b30a58e35cdb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Resolver problemas com perfis de e-mail no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Alguns problemas de perfis de e-mail e a forma de resolvê-los encontram-se descritos aqui.

Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md) para ver mais formas de obter ajuda.


## <a name="unable-to-send-images-from--email-account"></a>Não é possível enviar imagens a partir da conta de e-mail
Os utilizadores que têm contas de e-mail configuradas automaticamente não conseguem enviar imagens a partir dos dispositivos deles.
Isto ocorre quando a opção **Permitir o envio de e-mails a partir de aplicações de terceiros** não está ativada.

### <a name="intune-solution"></a>Solução do Intune

1.  Abra a Consola de Administração do Microsoft Intune, selecione a carga de trabalho **Política** &gt;**Política de Configuração**.

2.  Selecione o perfil de e-mail e escolha **Editar**.

3.  Selecione **Permitir o envio de e-mails a partir de aplicações de terceiros.**

### <a name="configuration-manager-integrated-with-intune-solution"></a>Solução do Configuration Manager integrado com o Intune

1.  Abra a consola do Configuration Manager &gt; **Ativos e Conformidade**.

2.  Expanda **Descrição Geral** -&gt; **Definições de Conformidade** -&gt; **Acesso a Recursos da Empresa** e selecione **Perfis de E-mail**.

3.  Clique com o botão direito do rato no perfil de e-mail e abra **Propriedades**.

4.  No separador **Definições de Sincronização**, selecione **Permitir o envio de e-mails a partir de aplicações de terceiros**.


## <a name="device-already-has-an-email-profile-installed"></a>O dispositivo já tem um perfil de email instalado

Se o utilizador tiver instalado um perfil de e-mail anterior ao aprovisionamento de um perfil pelo Intune, sendo que o resultado da implementação do perfil de e-mail do Intune depende da plataforma do dispositivo:

-**iOS**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. Um perfil de e-mail duplicado criado pelo utilizador irá bloquear a implementação de um perfil do Intune criado pelo administrador. Este é um problema comum, uma vez que os utilizadores do iOS criam um perfil de e-mail e depois fazem a inscrição. O portal da empresa irá informar o utilizador da não conformidade devido ao respetivo perfil de e-mail configurado manualmente e solicitará ao utilizador para remover esse perfil. O utilizador deve remover o respetivo perfil de e-mail, para que o perfil do Intune possa ser implementado. Para evitar este problema, indique aos seus utilizadores para inscreverem-se antes de instalar um perfil de e-mail e para permitir que o Intune implemente o perfil.

-**Windows**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. O Intune vai substituir o perfil de e-mail existente criado pelo utilizador.

-**Samsung KNOX Standard**: o Intune identifica uma conta de e-mail duplicada com base no endereço de e-mail e substitui a conta duplicada pelo perfil do Intune. Se o utilizador configurar essa conta, esta será substituída novamente pelo perfil do Intune. Tenha em atenção que isto pode causar alguma confusão ao utilizador cuja configuração de conta seja substituída.

Dado que o Samsung KNOX não utiliza o nome de anfitrião para identificar o perfil, recomendamos que não crie múltiplos perfis de e-mail para implementar o mesmo endereço de e-mail em diferentes anfitriões, como estes serão substituídas entre si.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Erro 0x87D1FDE8 para dispositivo KNOX Standard
**Problema**: depois de criar e implementar um perfil de e-mail do Exchange Active Sync para Samsung KNOX Standard em vários dispositivos Android, é comunicado o erro **0x87D1FDE8** ou **falha na remediação** no separador propriedades &gt; política do dispositivo.

Reveja a configuração do seu perfil EAS para Samsung KNOX e a política de origem. A opção de sincronização do Samsung Notes já não é suportada e não deve ser selecionada no seu perfil. Certifique-se de que os dispositivos têm tido tempo suficiente para processar a política, até 24 horas.

## <a name="next-steps"></a>Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
