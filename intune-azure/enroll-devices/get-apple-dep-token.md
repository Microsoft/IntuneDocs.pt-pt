---
title: "Obter um certificado do DEP da Apple para o Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: instruções para configurar e carregar um certificado push de MDM, um pré-requisito para a gestão de dispositivos da Apple no Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: b2c79e92f6378825bdaac03d2d9be699bdaca95b
ms.lasthandoff: 02/15/2017

---

# <a name="get-an-apple-dep-certificate"></a>Obter um certificado do DEP da Apple 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de poder inscrever dispositivos iOS pertencentes à empresa no DEP, precisa de um token do DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos propriedade da empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do Perfil de Inscrição para a Apple e atribuir dispositivos a esses perfis.

Para gerir dispositivos iOS propriedade da empresa com o Programa de Inscrição de Dispositivos da Apple (DEP), a sua empresa tem de se associar ao DEP da Apple e de obter dispositivos através desse programa. Os detalhes desse processo estão disponíveis em: https://deploy.apple.com. Entre as vantagens do programa incluem-se a configuração automatizada de dispositivos sem utilizar um cabo USB para ligar cada dispositivo a um computador.

> [!NOTE]
> Leia esta nota apenas se for um cliente que tenha sido migrado da consola de administração do Intune para o portal do Azure. Caso tenha eliminado um token DEP da Apple a partir da consola de administração do Intune durante o período de migração, pode constatar que o token DEP foi restaurado para a sua conta do Intune. Se tal acontecer, elimine o token DEP no portal do Azure. 

**Para obter um certificado do DEP da Apple**</br>
No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel Intune, escolha **Inscrever dispositivos** > **Token DEP da Apple** e, em seguida, siga os passos numerados no portal do Azure, que são apresentados abaixo.

**Passo 1. Transfira um certificado de chave pública do Intune obrigatório para criar um token DEP da Apple.**<br>
Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.

**Passo 2: Transfira um token DEP da Apple a partir do site da Apple adequado.**<br>
Selecione [Criar um token DEP através de Programas de Implementação da Apple](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. Tem de utilizar este ID Apple para renovar o seu token DEP.

   1.  No [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com), aceda a **Programa de Inscrição de Dispositivos** &gt; **Gerir Servidores** e, em seguida, selecione **Adicionar Servidor MDM**.

   2.  Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

   3.  É aberta a caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

   4.  A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** mostra uma ligação para o **Token do Seu Servidor**. Transfira o ficheiro do token do servidor (.p7m) para o seu computador e, em seguida, selecione **Concluído**.

    Este ficheiro do certificado (.p7m) é utilizado para estabelecer uma relação de confiança entre os servidores do Intune e do Programa de Inscrição de Dispositivos da Apple.

**Passo 3: Introduza o ID Apple que serviu para criar o seu token DEP da Apple. Este ID pode servir para renovar o seu token DEP da Apple.**

**Passo 4: Navegue para o seu token DEP da Apple para carregar. O Intune sincronizará automaticamente com a sua conta de DEP.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.

