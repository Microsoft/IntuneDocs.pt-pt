---
title: Resolver problemas com perfis de e-mail no Microsoft Intune – Azure | Documentos da Microsoft
description: Veja os problemas comuns e soluções com perfis de e-mail no Microsoft Intune, incluindo perfis de e-mail duplicado e erros em dispositivos Samsung KNOX Standard Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0fe37deb63457fef869df0f7263970a4e53cb29
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402713"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problemas comuns e resoluções com perfis de e-mail no Microsoft Intune

Reveja alguns problemas comuns de perfil de e-mail e como resolvê -los.

## <a name="device-already-has-an-email-profile-installed"></a>O dispositivo já tem um perfil de email instalado

Se os utilizadores criam um perfil de e-mail antes de se inscreverem no Intune, o perfil de e-mail do Intune poderá não funcionar conforme esperado:

- **iOS**: Intune Deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e endereço de e-mail. O perfil de e-mail criados pelo utilizador bloqueia a implementação do perfil criados pelo Intune. Este é um problema comum como iOS, os utilizadores criam um perfil de e-mail e depois inscreverem. A aplicação Portal da empresa indica que o utilizador não estiver em conformidade e pode solicitar ao utilizador para remover o perfil de e-mail.

  O utilizador deve remover o respetivo perfil de e-mail para que o perfil do Intune possam ser implementado. Para evitar este problema, indique aos seus utilizadores para inscrever e permitir que o Intune implementar o perfil de e-mail. Em seguida, os utilizadores podem criar seu perfil de e-mail.

- **Windows**: Intune Deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e endereço de e-mail. O Intune substitui o perfil de e-mail existente criado pelo utilizador.

- **Samsung KNOX Standard**: O Intune identifica uma conta de e-mail duplicado com base no endereço de e-mail e é substituído pelo perfil do Intune. Se o utilizador configurar essa conta, esta é substituída novamente pelo perfil do Intune. Isso pode causar alguma confusão ao utilizador cuja configuração de conta seja substituída.

Samsung KNOX não utiliza o nome de anfitrião para identificar o perfil. Recomendamos que não crie múltiplos perfis de e-mail para implementar o mesmo endereço de e-mail em diferentes anfitriões, como eles substituem entre si.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Erro 0x87D1FDE8 para dispositivo KNOX Standard

**Problema**: Depois de criar e implementar um Exchange Active Sync perfil de e-mail para o Samsung KNOX Standard para diferentes dispositivos Android, o **0x87D1FDE8** ou **falha na remediação** erro mostra em do dispositivo Propriedades > separador de política.

Reveja a configuração do seu perfil EAS para Samsung KNOX e a política de origem. A opção de sincronização do Samsung Notes já não é suportada, e essa opção não deve ser selecionada no seu perfil. Certifique-se de que os dispositivos têm tempo suficiente para processar a política, até 24 horas.

## <a name="unable-to-send-images-from--email-account"></a>Não é possível enviar imagens a partir da conta de e-mail

Aplica-se ao Intune no portal clássico do Azure.

Os utilizadores com contas de e-mail configuradas automaticamente não é possível enviar imagens a partir dos seus dispositivos. Este cenário poderá ocorrer se **permitir que o email seja enviado a partir de aplicações de terceiros** não está ativada.

### <a name="intune-solution"></a>Solução do Intune

1. Abra a consola de administração do Microsoft Intune, selecione **diretiva** carga de trabalho > **política de configuração**.

2. Selecione o perfil de e-mail e escolha **Editar**.

3. Selecione **Permitir o envio de e-mails a partir de aplicações de terceiros.**

### <a name="configuration-manager-integrated-with-intune-solution"></a>Solução do Configuration Manager integrado com o Intune

1. Abra a consola do Configuration Manager > **ativos e compatibilidade**.

2. Expanda **Descrição Geral** > **Definições de Conformidade** > **Acesso a Recursos da Empresa** e selecione **Perfis de E-mail**.

3. Clique com o botão direito do rato no perfil de e-mail e abra **Propriedades**.

4. No separador **Definições de Sincronização**, selecione **Permitir o envio de e-mails a partir de aplicações de terceiros**.

## <a name="next-steps"></a>Passos Seguintes

Obtenha [suportam a ajuda da Microsoft](get-support.md), ou utilize o [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).