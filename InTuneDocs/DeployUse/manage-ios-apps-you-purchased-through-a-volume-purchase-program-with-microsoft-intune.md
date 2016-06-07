---
# required metadata

title: Gerir aplicações iOS compradas através de um programa de compra em grandes volumes | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Manage iOS apps you purchased through a volume-purchase program with Microsoft Intune (Gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune)
Algumas lojas de aplicações permitem comprar várias licenças para uma aplicação que pretende executar na empresa. Isto ajuda a reduzir a sobrecarga administrativa de controlar várias cópias adquiridas de aplicações.

O Microsoft Intune ajuda-o a gerir aplicações compradas através de um programa destes ao importar as informações da licença a partir da loja de aplicações, ao controlar a quantidade de licenças que utilizou e ao impedir que instale mais cópias da sua aplicação.

> [!Important]
> Atualmente, o Intune atribui licenças de aplicações VPP iOS a utilizadores e não a dispositivos. Por este motivo, os utilizadores finais têm de introduzir a respetiva palavra-passe do ID Apple para instalar a aplicação.

## Gerir aplicações compradas em grandes volumes para dispositivos iOS
Compra várias licenças para aplicações iOS através do [Apple Volume Purchase Program for Business (VPP)](http://www.apple.com/business/vpp/). Isto envolve configurar uma conta Apple VPP no site da Apple e o token do Apple VPP no Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

## Antes de começar
Antes de começar, terá de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender o seguinte:

* Cada organização pode ter apenas uma conta e um token VPP.
* Quando associa uma conta VPP da Apple ao Intune, não é possível associar posteriormente uma conta diferente. Por este motivo, é muito importante que mais do que uma pessoa tenha os detalhes da conta que utiliza.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. No entanto, pode iniciar uma sincronização manual em qualquer altura.
* Após importar o token VPP no Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.
* Antes de começar a utilizar o VPP iOS com o Intune, remova as contas de utilizador VPP existentes criadas com outros fornecedores de MDM. O Intune não irá sincronizar essas contas de utilizador no serviço como medida de segurança. O Intune só irá sincronizar os dados do serviço Apple VPP que foram criados pelo serviço. 

## Para obter e carregar um token Apple VPP

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Admin** &gt; **iOS e Mac OS X** &gt;  **Volume Purchase Program**

2.  Clique na ligação **Conta Apple VPP** e, se ainda não o fez, inscreva-se no Volume Purchase Program for Business. Quando tiver terminado sessão, transfira o token VPP da Apple para a sua conta.

3.  Na página **Gerir Apple Volume Purchase Program (VPP)** da consola do Intune, clique em **Carregar o token VPP**

4.  Na caixa de diálogo **Carregar o token VPP**, introduza ou cole o nome do token VPP e o seu ID Apple e clique em **Carregar**

5.  Na caixa de diálogo de aviso, clique na caixa de verificação para indicar que compreende que não é possível alterar mais tarde para outra conta VPP e, em seguida, clique em **Sim**

Na página **Volume Purchase Program**, pode agora ver informações sobre o token Apple VPP, incluindo a última atualização, quando irá expirar e a última sincronização com o Intune.

Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, ao clicar em **Sincronizar agora**

## Para carregar e implementar uma aplicação comprada em volume

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Aplicações** &gt; **Software Gerido** &gt; **Aplicações Compradas em Volume**

2.  Utilize as instruções no tópico [Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) para concluir o carregamento, a criação e a implementação da aplicação.

Se implementar a aplicação como uma instalação **Necessária**, é utilizada uma licença por cada utilizador que a instalar.

Para recuperar uma licença, tem de alterar a ação de implementação para **Desinstalar**. A licença será recuperada quando desinstalar a aplicação.

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação VPP pela primeira vez, é-lhe pedido para se associar ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação.

> Observe a coluna **Estados dos Termos VPP** para ver o estado de aceitação de cada utilizador no qual a aplicação foi implementada.

Se não existirem licenças adicionais disponíveis, a implementação irá falhar.

## Para monitorizar as aplicações Apple VPP
Pode monitorizar as aplicações VPP que foram implementadas e quantas licenças são utilizadas a partir da área de trabalho **Aplicações**, no nó **Software Gerido** &gt; **Aplicações Compradas em Volume**.

> Também pode utilizar a aplicação **Filtros** para examinar o estado de cada instalação da aplicação.

### Consulte Também
[Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=May16_HO2-->

