---
title: Obter um certificado do DEP da Apple para o Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: instruções para configurar e carregar um certificado push de MDM, um pré-requisito para a gestão de dispositivos da Apple no Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8edc42bb86e3856ac6568cc3c1acc5d757978e79
ms.lasthandoff: 02/18/2017

---

# <a name="get-an-apple-dep-certificate"></a>Obter um certificado do DEP da Apple

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de poder inscrever dispositivos iOS da empresa através do Programa de Registo de Aparelho (DEP) da Apple, precisa de ter um token DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos propriedade da empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do perfil de inscrição para a Apple e atribuir dispositivos a esses perfis.

Para dispositivos iOS da empresa com o DEP, a sua organização tem de aderir ao Apple DEP e obter dispositivos através desse programa. Os detalhes desse processo estão disponíveis em: https://deploy.apple.com. Entre as vantagens do programa incluem-se a configuração automatizada de dispositivos sem utilizar um cabo USB para ligar cada dispositivo a um computador.

> [!NOTE]
> Esta nota só se aplica aos clientes do Intune que foram migrados da consola de administração do Intune para o portal do Azure. Caso tenha eliminado um token DEP da Apple a partir da consola de administração do Intune durante o período de migração, pode constatar que o token DEP foi restaurado para a sua conta do Intune. Se tal acontecer, elimine o token DEP no portal do Azure.

## <a name="steps-to-get-the-apple-dep-certificate"></a>Passos para obter o certificado do DEP da Apple
No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel Intune, escolha **Inscrever dispositivos** > **Token DEP da Apple** e, em seguida, siga os passos numerados no portal do Azure, que são apresentados abaixo.

**Passo 1. Transfira um certificado de chave pública do Intune obrigatório para criar um token DEP da Apple.**<br>
Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.

**Passo 2: Transfira um token DEP da Apple a partir do site da Apple adequado.**<br>
Selecione [Criar um token DEP através de Programas de Implementação da Apple](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. Tem de utilizar este ID Apple para renovar o seu token DEP.

   a.  No [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com), aceda a **Programa de Inscrição de Dispositivos** &gt; **Gerir Servidores** e, em seguida, selecione **Adicionar Servidor MDM**.

   b.  Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

   c.  É aberta a caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

   d.  A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** mostra uma ligação para o **Token do Seu Servidor**. Transfira o ficheiro do token do servidor (.p7m) para o seu computador e, em seguida, selecione **Concluído**.

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**Passo 3: Introduza o ID Apple que serviu para criar o seu token DEP da Apple. Este ID pode servir para renovar o seu token DEP da Apple.**

**Passo 4: Navegue para o seu token DEP da Apple para carregar. O Intune sincronizará automaticamente com a sua conta de DEP.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.

