---
title: "Aplicações permitidas e bloqueadas para KNOX | Microsoft Intune"
description: "Perfil personalizado para criar uma lista de aplicações permitidas e bloqueadas para KNOX."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7679d624ba22b2a062ef2534a642e38a5f57fde
ms.openlocfilehash: 273627573f58e1bde4fd19c548ce87639f25ca4b



---
# Utilizar políticas personalizadas para permitir e bloquear aplicações para dispositivos Samsung KNOX

Utilize os procedimentos deste tópico para criar uma política personalizada do Microsoft Intune que cria um dos seguintes casos:

- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. A execução das aplicações nesta lista está bloqueada, mesmo se já tiverem sido instaladas quando a política foi aplicada.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Apenas as aplicações na lista podem ser instaladas. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos que executem Samsung KNOX.

## Para criar uma lista de aplicações permitidas ou bloqueadas

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Política** &gt; **Políticas de Configuração** &gt; **Adicionar**.
2. Na caixa de diálogo **Criar uma Nova Política**, expanda **Android**, escolha **Configuração Personalizada**, e, em seguida, escolha **Criar Política**.
3. Forneça um nome e uma descrição opcional para a política e, em seguida, na secção **Definições OMA-URI**, escolha **Adicionar**.
4. Na caixa de diálogo **Adicionar ou Editar Definição OMA-URI**, especifique o seguinte: para uma lista de aplicações cuja execução está bloqueada no dispositivo:
    
    - **Nome da definição.** Introduza **PreventStartPackages**.
    - **Descrição da definição.** Introduza uma descrição opcional, como ''Lista de aplicações cuja execução está bloqueada''.
    -   **Tipo de dados.** Na lista pendente, escolha **Cadeia**.
    -   **OMA-URI.** Introduza **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Valor.** Introduza uma lista de nomes de pacotes de aplicações que pretende permitir. Pode utilizar **; : ,** ou **|** como delimitador. (Exemplo: pacote1;pacote2;)

    Para uma lista de aplicações que os utilizadores têm permissão para instalar a partir da Google Play Store, excluindo todas as outras aplicações:

    - **Nome da definição.** Introduza **AllowInstallPackages**.
    - **Descrição da definição.** Introduza uma descrição opcional, como ''Lista de aplicações que os utilizadores podem instalar a partir do Google Play''.
    - **Tipo de dados.** Na lista pendente, escolha **Cadeia**.
    - **OMA-URI.** Introduza **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Valor.** Introduza uma lista de nomes de pacotes de aplicações que pretende permitir. Pode utilizar **; : ,** ou **|** como delimitador. (Exemplo: pacote1;pacote2;)

4. Clique em **OK** e, em seguida, clique em **Guardar Política**. 

>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

Da próxima vez que cada dispositivo visado iniciar sessão, serão aplicadas as definições da aplicação.


## Implementar a política

1.  Na área de trabalho **Política** , selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir Implementação**, selecione um ou mais grupos nos quais quer implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

 
Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

### Consulte também
[Definições de política de Android e Samsung KNOX no Microsoft Intune](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


