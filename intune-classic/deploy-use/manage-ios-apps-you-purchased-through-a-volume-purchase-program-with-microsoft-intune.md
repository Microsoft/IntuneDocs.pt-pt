---
title: "Gerir aplicações iOS compradas em grandes volumes"
description: "Utilize o Intune para gerir aplicações compradas em volume na Apple ao importar as informações da licença a partir da loja de aplicações, ao controlar a quantidade de licenças que utilizou e ao impedir que instale mais cópias da sua aplicação do que as que tem."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5da29dceb5308eab72e5b24e220586aa739982ea
ms.sourcegitcommit: 1afff0fd464ece84ffea6bc0c71c78215d59e696
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Manage iOS apps you purchased through a volume-purchase program with Microsoft Intune (Gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

A iOS App Store permite-lhe comprar várias licenças para uma aplicação que pretende executar na sua empresa. Isto ajuda a reduzir a sobrecarga administrativa de controlar várias cópias adquiridas de aplicações.

O Microsoft Intune ajuda-o a gerir aplicações compradas através deste programa ao importar as informações da licença a partir da loja de aplicações, ao controlar a quantidade de licenças que utilizou e ao impedir que instale mais cópias da sua aplicação do que as que tem.

> [!Important]
> Atualmente, o Intune atribui licenças de aplicações VPP (Volume Purchase Program for Business) iOS a utilizadores e não a dispositivos. Por este motivo, os utilizadores têm de introduzir a respetiva palavra-passe do ID Apple para instalar a aplicação.
> O Apple Volume Purchase Program for Education e as aplicações B2B não são suportados nesta versão.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gerir aplicações compradas em volume para dispositivos iOS
Compra várias licenças para aplicações iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/). Isto envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, terá de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender o seguinte:

* O Intune suporta a adição de até 256 tokens VPP.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.
* Antes de começar a utilizar o VPP iOS com o Intune, remova as contas de utilizador VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não irá sincronizar essas contas de utilizador no serviço como medida de segurança. O Intune só irá sincronizar os dados do serviço Apple VPP que foram criados pelo Intune.
* Só pode implementar as aplicações VPP do iOS em dispositivos de utilizadores que tenham sido inscritos com o Protocolo de Inscrição de Dispositivos (DEP) se a afinidade de utilizador do dispositivo estiver configurada.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obter e carregar um token Apple VPP

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Admin** &gt; **iOS e Mac OS X** &gt;  **Volume Purchase Program**.

2.  Escolha a ligação **Conta Apple VPP**. Se ainda não o fez, inscreva-se no Volume Purchase Program for Business. Após a inscrição, transfira o token VPP da Apple para a sua conta.

3.  Na página **Gerir Apple Volume Purchase Program (VPP)** da consola do Intune, clique em **Carregar o token VPP**.

4.  Na caixa de diálogo **Carregar o token VPP**, introduza ou cole o nome do token VPP e o seu ID Apple e, em seguida, escolha **Carregar**.

5.  Na caixa de diálogo de aviso, selecione a caixa de verificação para indicar que compreende que não é possível alterar mais tarde para outra conta VPP e, em seguida, escolha **Sim**.

Na página **Volume Purchase Program**, pode agora ver informações sobre o token Apple VPP, incluindo a última atualização, quando irá expirar e a última sincronização com o Intune.

Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, selecionando **Sincronizar agora**.

## <a name="to-deploy-a-volume-purchased-app"></a>Implementar uma aplicação adquirida em grandes volumes

1.  Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Aplicações** &gt; **Aplicações** &gt; **Aplicações Compradas em Volume**. Esta lista mostra todas as aplicações que foram sincronizadas a partir do serviço Apple VPP.

2.  Escolha a aplicação que pretende implementar, escolha **Gerir Implementação** e, em seguida, utilize as instruções no tópico [Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md) para concluir o carregamento, a criação e a implementação da aplicação.

> [!TIP]
> Tem de escolher uma ação de implementação **Necessária**. As instalações disponíveis não são atualmente suportadas. Além disso, só pode implementar a aplicação a grupos de utilizadores.

Se implementar a aplicação como uma instalação **Necessária**, é utilizada uma licença por cada utilizador que a instalar.

Para recuperar uma licença, tem de alterar a ação de implementação para **Desinstalar**. A licença será recuperada quando desinstalar a aplicação.

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação VPP pela primeira vez, é-lhe pedido para se associar ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação.

Se não existirem licenças adicionais disponíveis, a implementação irá falhar.

## <a name="to-monitor-apple-vpp-apps"></a>Para monitorizar as aplicações Apple VPP
Pode monitorizar as aplicações VPP que foram implementadas e quantas licenças são utilizadas na área de trabalho **Aplicações**, no nó **Aplicações Compradas em Volume**.

> [!TIP]
> Também pode utilizar a aplicação **Filtros** para examinar o estado de cada instalação da aplicação.

### <a name="see-also"></a>Veja também
[Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md)
