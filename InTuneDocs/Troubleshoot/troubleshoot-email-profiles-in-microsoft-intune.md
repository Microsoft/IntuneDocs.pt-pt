---
# required metadata

title: Resolver problemas com perfis de e-mail| Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Resolver problemas com perfis de e-mail no Microsoft Intune
Alguns problemas de perfis de e-mail e a forma de resolvê-los encontram-se descritos aqui.

Se estas informações não resolverem o problema, veja [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](how-to-get-support-for-microsoft-intune.md) para ver mais formas de ajuda.


## Não é possível enviar imagens a partir da conta de e-mail
Os utilizadores que têm contas de e-mail configuradas automaticamente não conseguem enviar imagens a partir dos dispositivos deles.
Isto ocorre quando a opção **Permitir o envio de e-mails a partir de aplicações de terceiros** não está ativada.

### Solução do Intune

1.  Abra a Consola de Administração do Microsoft Intune, selecione a carga de trabalho **Política** &gt; **Política de Configuração**

2.  Selecione o perfil de e-mail e clique em **Editar**

3.  Selecione **Permitir o envio de e-mails a partir de aplicações de terceiros.**

### Solução do Configuration Manager integrado com o Intune

1.  Abra a consola do Configuration Manager &gt; **Ativos e Conformidade**

2.  Expanda **Descrição geral** -&gt; **Definições de Conformidade** -&gt; **Acesso a Recursos da Empresa** e selecione **Perfis de E-mail**

3.  Clique com o botão direito do rato no perfil de e-mail e abra **Propriedades**

4.  No separador **Definições de Sincronização**, selecione **Permitir o envio de e-mails a partir de aplicações de terceiros**

## Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](how-to-get-support-for-microsoft-intune.md)


<!--HONumber=May16_HO2-->

