---
title: "Notas de versão para o Microsoft Intune | Microsoft Intune"
description: "Notas de versão do Intune"
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f1147e5fe766bc4642439c4ad23b2fdfbf74bb03
ms.openlocfilehash: da476088435d6ef8bd58ecad1b221254a30858cc


---

# Notas de versão para o Microsoft Intune
O Microsoft Intune é uma solução integrada de gestão de cliente baseada em nuvem que fornece ferramentas, relatórios e licenças de atualização para a versão mais recente do Windows. Também ajuda a manter os seus computadores atualizados e seguros. Além disso, o Intune permite-lhe gerir dispositivos móveis na rede através do Exchange ActiveSync ou diretamente através do Intune. As notas de versão seguintes descrevem informações importantes e os problemas conhecidos no Microsoft Intune.


## Os utilizadores de Android não conseguem enviar mensagens de e-mail quando o acesso condicional do Exchange Online está implementado

**Problema:** os utilizadores com a versão Android 5.1.1 e posteriores nos respetivos dispositivos Samsung não podem enviar mensagens de e-mail quando o acesso condicional do Exchange Online tiver sido configurado. A Samsung reconhece que o problema se encontra no respetivo cliente de correio incorporado no Android 5.1.1 e posterior, e está a investigar uma correção.

**Solução 1:** aconselhe os utilizadores a utilizarem a aplicação Outlook para Android.

**Solução 2:** para permitir que os utilizadores afetados enviem e-mails, pode seguir estes passos:

1. Coloque cada utilizador afetado num grupo de segurança na secção "grupos excluídos" da política de acesso condicional do Exchange Online.
2. Permita que o utilizador sincronize temporariamente os e-mails no cliente de e-mail incorporado.
3. Remova o utilizador afetado do grupo excluído e confirme que o utilizador já pode enviar e-mails.

A Microsoft irá continuar a trabalhar em conjunto com a Samsung numa correção ou em soluções adicionais.



## A alteração dos perfis de acesso a recursos entre grupos para iOS e Android pode falhar
**Problema:** quando altera os perfis de acesso a recursos de e-mail ou o protocolo SCEP (Simple Certificate Enrollment Protocol) entre grupos, os perfis podem entrar em conflito e falhar. Por exemplo, imaginemos que tem um perfil de e-mail existente que aponta para um servidor do Exchange no local, direcionado para o Grupo A. Em seguida, cria um novo perfil de e-mail que aponta para o Exchange Online, direcionado para o Grupo B. Quando mover os utilizadores do Grupo A para o Grupo B, os dispositivos irão manter o perfil de e-mail do Exchange no local e tentar instalar o perfil de e-mail do Exchange Online que está direcionado para o Grupo B.

Neste momento, pode ocorrer uma das seguintes situações: 
* Se os perfis de e-mail A e B forem idênticos, o dispositivo rejeita o perfil de e-mail B porque o perfil de e-mail B já contém o perfil de e-mail A.
* Se o perfil de e-mail A for diferente do perfil de e-mail B, tal como mencionado no exemplo, o dispositivo acaba por ficar com dois perfis de e-mail.

> [!NOTE]
> O nome de anfitrião e o atributo utilizado para o nome de utilizador são verificados para distinguir um perfil de e-mail do outro.

Em ambos os casos, o perfil de acesso a recursos (perfil de e-mail) não foi removido do dispositivo, para evitar a remoção não intencional do acesso de um utilizador ao e-mail ou ao certificado SCEP do cliente.

**Solução:** Nenhuma.

## Quando inscreve um dispositivo Windows 8.1 que tem de ser autenticado num servidor proxy, o processo de inscrição falha sem causa visível
**Problema:** Quando inscreve um dispositivo Windows 8.1 e este tem de ser autenticado num servidor proxy durante o processo de inscrição, a inscrição falha se o dispositivo não tiver as credenciais do servidor proxy em cache. Quando as credenciais do servidor proxy não estão em cache no dispositivo, o processo de inscrição tem de aguardar que o utilizador introduza as credenciais. No entanto, o pedido para fornecer as credencias do servidor proxy não é apresentado durante o processo de inscrição. Por esse motivo, o processo de inscrição não consegue efetuar a autenticação do servidor proxy. Não é apresentada nenhuma indicação visível para esta falha ao utilizador.

**Solução:** para os dispositivos Windows 8.1 que têm de estar inscritos numa rede que requer a utilização de um servidor proxy autenticado, configure e guarde as credenciais do servidor proxy antes de inscrever o dispositivo. Para configurar e guardar as credenciais num dispositivo Windows 8.1:

1.  No dispositivo Windows 8.1, abra o Internet Explorer.
2.  Quando lhe forem pedidas as credenciais do servidor proxy, introduza as credenciais e, em seguida, selecione a opção **Memorizar credenciais**.
3.  Inscreva o dispositivo.

## Os dispositivos Windows Phone 8.1 não conseguem inscrever-se no Microsoft Intune quando a autenticação do dispositivo está ativada no AD FS.
**Problema:** quando inscreve um dispositivo Windows Phone 8.1, a inscrição falha se a definição opcional para a autenticação do dispositivo for ativada como parte da política de autenticação global dos Serviços de Federação do Active Directory (AD FS).

**Solução:** Desative a autenticação do dispositivo no servidor do AD FS, desmarcando **Ativar autenticação do dispositivo** em **Editar Política de Autenticação Global**. Para mais informações, consulte [Configurar Políticas de Autenticação](http://technet.microsoft.com/library/dn486781.aspx).


## A ferramenta Microsoft App Wrapping Tool for Android não tem nenhuma função incorporada de desinstalação
**Problema:** A ferramenta **Microsoft App Wrapping Tool for Android** não tem uma funcionalidade incorporada para desinstalar a ferramenta.

**Solução:** Navegue até à localização onde instalou a ferramenta e elimine o diretório. A localização de instalação predefinida é: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Para saber mais sobre a ferramenta de encapsulamento de aplicações, consulte [Preparar as aplicações Android para a gestão com a Ferramenta de Encapsulamento de Aplicações](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## A assistência remota não está disponível em computadores com Windows 8 ou Windows 8.1.
**Problema:** Nesta versão, a funcionalidade de assistência remota não está disponível em computadores com Windows 8 ou Windows 8.1.

**Solução:** Nenhuma.

## As notificações de alerta para destinatários que são adicionados automaticamente podem não funcionar
**Problema:** se os destinatários forem adicionados automaticamente a uma notificação de alerta, poderão não receber sempre as notificações.

**Solução:** para garantir que os destinatários recebem a mensagem de notificação, deve adicioná-los manualmente às notificações de alerta.

## Suporte de idiomas no portal do Azure
O portal do Azure suporta os seguintes idiomas: alemão, checo, chinês (simplificado), chinês (tradicional), coreano, espanhol, francês, húngaro, inglês, italiano, japonês, neerlandês, polaco, português (Brasil), português (Portugal), russo, sueco e turco.

A Consola de Administração do Intune e as experiências em dispositivos móveis destinadas ao utilizador suportam dinamarquês, grego, finlandês, norueguês e romeno, para além de todos os idiomas suportados pelo portal do Azure.



<!--HONumber=Oct16_HO2-->


