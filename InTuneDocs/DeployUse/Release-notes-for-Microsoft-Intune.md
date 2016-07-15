---
title: "Notas de versão para o Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 1906f14568484ebbf23ac7c4350964fb2d5d508f


---

# Notas de versão para o Microsoft Intune
O Microsoft Intune é uma solução integrada de gestão de cliente baseado em nuvem que fornece ferramentas, relatórios e licenças de atualização para a versão mais recente do Windows e ajuda a manter os seus computadores atualizados e seguros. Além disso, o Intune permite-lhe gerir dispositivos móveis na rede através do Exchange ActiveSync ou diretamente através do Intune. As notas de versão seguintes descrevem informações importantes e os problemas conhecidos no Microsoft Intune.


## Os utilizadores de Android não conseguem enviar mensagens de e-mail quando o acesso condicional do Exchange Online está implementado

Os utilizadores com o Samsung Android 5.1.1 e acima nos respetivos dispositivos não conseguem enviar mensagens de e-mail quando o acesso condicional do Exchange Online tiver sido configurado. A Samsung reconhece que o problema se encontra no cliente de correio incorporado no Android 5.1.1 e acima, e está atualmente a investigar uma correção.

**Solução 1:** Aconselhe os utilizadores finais a utilizarem a aplicação Outlook para Android.

**Solução 2:** Para permitir que os utilizadores afetados enviem mensagens de e-mail, pode seguir estes passos:

1. Coloque o utilizador afetado num grupo de segurança na secção "grupos excluídos" da política de acesso condicional do Exchange Online.
2. Permita que o utilizador sincronize temporariamente o e-mail no cliente de e-mail incorporado.
3. Remova o utilizador afetado do grupo excluído e confirme que o utilizador pode agora enviar mensagens de e-mail.

A Microsoft irá continuar a trabalhar em conjunto com a Samsung numa correção ou em soluções adicionais.



## A alteração dos perfis de acesso a recursos entre grupos para iOS e Android pode falhar
**Problema:** Quando altera os perfis de acesso a recursos de e-mail ou SCEP (Simple Certificate Enrollment Protocol) entre grupos, os perfis podem entrar em conflito e falhar. Por exemplo, imaginemos que tem um perfil de -email existente que está a apontar para o servidor do Exchange no local, direcionado para o Grupo A, e que, em seguida, cria um novo perfil de e-mail que aponta para o Exchange Online, direcionado para o grupo B. Quando move os utilizadores do Grupo A para o Grupo B, os dispositivos irão manter o perfil de e-mail do Exchange no local e tentar instalar o perfil de e-mail do Exchange Online que está direcionado para o Grupo B.

Neste momento, pode ocorrer uma das seguintes situações: 
* Se os perfis de e-mail A e B forem idênticos, o dispositivo rejeita o perfil de e-mail B porque o perfil de e-mail B já contém o perfil de e-mail A.
* Se o perfil de e-mail A for diferente do perfil de e-mail B, tal como mencionado no exemplo acima, o dispositivo acaba por ficar com dois perfis de e-mail.

**Nota:** O nome de anfitrião e o atributo utilizado para o nome de utilizador são verificados para distinguir um perfil de e-mail do outro.

Em ambos os casos acima, o perfil de acesso a recursos (perfil de e-mail) não foi removido do dispositivo, para evitar a remoção não intencional do acesso de um utilizador ao e-mail ou ao certificado SCEP do cliente.

**Solução:** Nenhuma.

## Quando inscreve um dispositivo Windows 8.1 que tem de ser autenticado num servidor proxy, o processo de inscrição falha sem indicação visível da causa da falha
**Problema:** Quando inscreve um dispositivo Windows 8.1 e este tem de ser autenticado num servidor proxy durante o processo de inscrição, a inscrição falha se o dispositivo não tiver as credenciais do servidor proxy em cache. Quando as credenciais do servidor proxy não estão em cache no dispositivo, o processo de inscrição tem de aguardar que o utilizador introduza as credenciais. No entanto, o pedido para fornecer as credencias do servidor proxy não é apresentado durante o processo de inscrição. O resultado é que o processo de inscrição não pode ser autenticado num servidor proxy e não é apresentada ao utilizador uma indicação visível desta falha.

**Solução:** Nos dispositivos Windows 8.1 que têm de estar inscritos numa rede que requer a utilização de um servidor proxy autenticado, configure e guarde as credenciais do servidor proxy antes de inscrever o dispositivo. Para configurar e guardar as credenciais num dispositivo Windows 8.1:

1.  No dispositivo Windows 8.1, abra o **Internet Explorer**.

2.  Quando lhe forem pedidas as credenciais do servidor proxy, introduza as credenciais e, em seguida, selecione a opção **Memorizar credenciais**.

3.  Inscreva o dispositivo.

## Os dispositivos Windows Phone 8.1 não conseguem inscrever-se no Microsoft Intune quando a autenticação do dispositivo está ativada no AD FS.
**Problema:** Quando inscrever um dispositivo Windows Phone 8.1, a inscrição falha se a definição opcional para a autenticação do dispositivo for ativada como parte da política de autenticação global dos Serviços Federados do Active Directory (AD FS).

**Solução:** Desative a autenticação do dispositivo no servidor do AD FS, desmarcando **Ativar autenticação do dispositivo** em **Editar Política de Autenticação Global**. Para obter mais informações, consulte [Configurar Políticas de Autenticação](http://technet.microsoft.com/library/dn486781.aspx)


## A ferramenta Microsoft App Wrapping Tool for Android não tem nenhuma função incorporada de desinstalação
**Problema:** A ferramenta **Microsoft App Wrapping Tool for Android** não tem uma funcionalidade incorporada para desinstalar a ferramenta.

**Solução:** Navegue até à localização onde instalou a ferramenta e elimine o diretório. A localização de instalação predefinida é: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Para obter mais informações sobre a ferramenta Microsoft App Wrapping Tool for Android, consulte [Preparar as aplicações Android para gestão com a Ferramenta de Encapsulamento de Aplicações](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## A assistência remota não está disponível em computadores com Windows 8 ou Windows 8.1.
**Problema:** Nesta versão, a funcionalidade de assistência remota não está disponível em computadores com Windows 8 ou Windows 8.1.

**Solução:** Nenhuma.

## As notificações de alerta para destinatários que são adicionados automaticamente podem não funcionar
**Problema:** Se um destinatário for adicionado automaticamente a uma notificação de alerta, poderá não receber sempre a notificação.

**Solução:** Para garantir que os destinatários recebem a mensagem de notificação, deve adicioná-los às notificações de alerta manualmente.

## Suporte de idiomas no portal de pré-visualização do Azure
O portal de pré-visualização do Azure baseia-se numa nova plataforma e suporta os seguintes idiomas - chinês (simplificado), chinês (tradicional), checo, neerlandês, inglês, alemão, húngaro, italiano, japonês, português (Brasil), português (Portugal), russo, espanhol, francês, coreano, polaco, sueco e turco.

A Consola de administrador do Intune e o utilizador final voltado para experiências móveis suportam dinamarquês, grego, finlandês, norueguês e romeno, para além de todos os idiomas suportados pelo portal de pré-visualização do Azure.



<!--HONumber=Jun16_HO4-->


