---
title: Preparar-se para inscrever dispositivos | Microsoft Intune
description: "Configurar os pré-requisitos da gestão de dispositivos móveis (MDM) e preparar-se para inscrever sistemas operativos diferentes."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7bea7ba4ef59c6b1400414b59456e19dc1c152fb
ms.openlocfilehash: 768dd08ad838b621f18a24747618ef1e37c5c804


---

# Prepare-se para inscrever dispositivos no Microsoft Intune
Para permitir aos empregados inscrever dispositivos móveis (incluindo [Android](set-up-android-management-with-microsoft-intune.md), [iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md), [Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md) e [PCs Windows](set-up-windows-device-management-with-microsoft-intune.md)) no Intune ou parar gerir dispositivos proprietários da companhia, tem de ativar a inscrição de dispositivos. Para permitir a inscrição, tem de definir uma autoridade de gestão de dispositivos móveis (MDM), configurar o Portal da Empresa do Intune, atribuir licenças e ativar a inscrição na plataforma do dispositivo.

## Definir autoridade de gestão de dispositivos móveis
A autoridade de MDM define o serviço de gestão que tem permissão para gerir um conjunto de dispositivos. As opções para a autoridade de MDM incluem o Intune autónomo e o Configuration Manager com o Intune. Se definir o Configuration Manager como autoridade de gestão, nenhum outro serviço pode ser utilizado para gestão de dispositivos móveis.

>[!IMPORTANT]
> Considere cuidadosamente se pretende gerir dispositivos móveis apenas com o Intune (serviço online) ou com o System Center Configuration Manager com o Intune (solução de software no local em conjunto com o serviço online). A definição da autoridade de gestão de dispositivos móveis não pode ser alterada.



1.  Na [consola do administração do Microsoft Intune](http://manage.microsoft.com), escolha **Administrador** &gt; **Gestão de Dispositivos Móveis**.

2.  Na lista **Tarefas** , clique em **Definir Autoridade de Gestão de Dispositivos Móveis**. A caixa de diálogo **Definir Autoridade de Gestão de Dispositivos Móveis** é aberta.

    ![Caixa de diálogo Definir autoridade de MDM](../media/intune-mdm-authority.png)

3.  O Intune pede a confirmação de que pretende o Intune como a sua autoridade MDM. Selecione a caixa de verificação e, em seguida, escolha **Sim** para utilizar o Microsoft Intune para gerir dispositivos móveis.

## Configurar o Portal da Empresa do Intune

O Portal da Empresa do Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.

> [!TIP]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa.

Personalizar o Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para tal, basta iniciar sessão na [consola de administrador do Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos ou de serviços, escolher **Administrador** &gt; **Portal da Empresa** e configurar as definições do Portal da Empresa.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### Informações de contacto e declaração de privacidade da empresa

O nome da empresa é apresentado como o título do Portal da Empresa. Os detalhes e as informações de contacto são apresentados aos utilizadores no ecrã Contactar TI do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |Nome da empresa|40|Este nome é apresentado como o título do Portal da Empresa. **Nota**: apenas carateres alfanuméricos. Este campo não suporta carateres especiais.|
    |Nome do contacto do departamento de TI|40|Este nome é apresentado na página **Contactar TI**.|
    |Número de telefone do departamento de TI|20|Este número de contacto é apresentado na página **Contactar TI**.|
    |Endereço de e-mail do departamento de TI|40|Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato **alias@nomedodominio.com**.|
    |Informações adicionais|120|Estas informações são apresentadas na página **Contactar TI**.|
    |URL da declaração de privacidade da empresa|79|Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato https://www.contoso.com.|

### Contactos de suporte
O site de suporte é apresentado para os utilizadores no Portal da Empresa para que possam aceder ao suporte online.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |URL do site de suporte|150|Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato https://www.contoso.com. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa.|
    |Nome do site|40|Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação **Aceder ao site de TI** será apresentada na página **Contactar TI** no Portal da Empresa.|


### Personalização da imagem corporativa da empresa

Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.

|Nome do campo|Mais informações|
    |----------|----------------|
    |Cor do tema|Selecione a cor do tema que pretende aplicar ao Portal da Empresa.|
    |Incluir o logótipo da empresa|Quando ativa esta opção, pode carregar o logótipo da sua empresa que pretende que seja apresentado no Portal da Empresa. Pode carregar dois logótipos: um que é apresentado quando o fundo do Portal da Empresa é branco, e outro que é apresentado quando o fundo do Portal da Empresa utiliza a cor do tema que selecionou. Cada logótipo tem de ser um ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 100 pixéis e ter um tamanho de 750 KB ou menos.|
    |Selecionar um fundo para a aplicação Portal da Empresa do [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]|Esta definição afeta apenas o fundo da aplicação Portal da Empresa do [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)].|


Depois de guardar as alterações, pode utilizar as ligações fornecidas na parte inferior da página **Portal da Empresa** da consola de administração para ver o Web site do Portal da Empresa. Estas ligações não podem ser alteradas. Quando um utilizador inicia sessão, estas ligações apresentam as suas subscrições no Portal da Empresa.

## Atribuir uma licença de utilizador do Intune

Para adicionar manualmente utilizadores baseados na nuvem e atribuir licenças às contas de utilizador baseadas na nuvem e às contas sincronizadas do Active Directory no local com o Azure Active Directory (Azure AD), é utilizado o **portal de gestão do Office 365**.

1.  Inicie sessão no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) com as suas credenciais de administrador de inquilino.

2.  Selecione a conta de utilizador à qual pretende atribuir uma licença de utilizador do Intune e selecione a caixa de verificação **Microsoft Intune** nas propriedades da conta de utilizador.

3.  A conta de utilizador será agora adicionada ao grupo de utilizadores do Microsoft Intune, que atribui as permissões de utilizador para utilizar o serviço e inscrever os respetivos dispositivos para gestão.

## Configurar a gestão de dispositivos
Depois de configurar a autoridade de MDM, tem de configurar a gestão de dispositivos nos sistemas operativos que a sua organização pretende suportar. Os passos necessários para configurar a gestão de dispositivos variam consoante o sistema operativo. Por exemplo, o SO Android não requer que efetue nenhuma ação na consola de administração do Intune. Por outro lado, o Windows e o iOS requerem uma relação de confiança entre os dispositivos e o Intune para permitir a gestão.

> [!div class="op_single_selector"]
- [Configurar a gestão de Android com o Microsoft Intune](set-up-android-management-with-microsoft-intune.md)
- [Configurar a gestão de iOS e Mac com o Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)
- [Configurar a gestão de dispositivos Windows com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)

Também pode:
 - Utilize a [conta do gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) para inscrever muitos dispositivos.
 - [Especifique os dispositivos pertencentes à empresa com os números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) para ajudar a inscrever dispositivos e a política de destino.



<!--HONumber=Aug16_HO2-->


