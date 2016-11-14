---
title: Aceder ao e-mail empresarial com perfis de e-mail | Microsoft Intune
description: "As definições de perfil de e-mail podem ser utilizadas para configurar as definições de acesso de e-mail para clientes de e-mail específicos em dispositivos móveis."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 56988f0a69e6ff281439e6e77d1814ec130c8b49
ms.openlocfilehash: dcd8f956d1706f4bdcb2dca79e9f1ff5d5bb57b0


---

# <a name="configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune"></a>Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Muitas plataformas móveis incluem um cliente de e-mail nativo que é fornecido como parte do sistema operativo. Alguns destes clientes podem ser configurados através de perfis de e-mail, conforme descrito neste tópico.

As definições de perfil de e-mail podem ser utilizadas para configurar as definições de acesso de e-mail para clientes de e-mail específicos em dispositivos móveis. Nas plataformas suportadas, os clientes de e-mail nativos podem ser configurados pelo Microsoft Intune para permitir que os utilizadores acedam ao respetivo e-mail da empresa nos dispositivos pessoais sem qualquer configuração adicional.

Se necessitar de medidas adicionais de prevenção de perda de dados, utilize o [Acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), que controla o acesso à caixa de correio do utilizador em qualquer cliente de e-mail, incluindo clientes de e-mail nativos.

Os administradores de TI ou os utilizadores também podem optar por instalar clientes de e-mail alternativos (por exemplo, o Microsoft Outlook para Android ou iOS). Estes clientes de e-mail podem não suportar perfis de e-mail e não podem ser configurados através de perfis de e-mail do Intune.  

Pode utilizar os perfis de e-mail para configurar o cliente de e-mail nativo nos seguintes tipos de dispositivos:
-   Windows Phone 8.1 e posterior
-   Windows 10 (para ambiente de trabalho), Windows 10 Mobile e posterior
-   iOS 8.0 e posterior
-   Samsung KNOX Standard (4.0 e posterior)
-   Android for Work

>[!NOTE]
>O Intune fornece dois perfis de e-mail do Android for Work, um para cada uma das aplicações de e-mail, Gmail e Nine Work. Estas aplicações estão disponíveis na Google Play Store e suportam ligações com o Exchange. Para ativar a conectividade de e-mail, implemente uma destas aplicações de e-mail nos dispositivos dos seus utilizadores e, em seguida, crie e implemente o perfil adequado.

Além de configurar uma conta de e-mail no dispositivo, pode configurar a quantidade de e-mails a sincronizar e, dependendo do tipo de dispositivo, os tipos de conteúdo a sincronizar.

>[!NOTE]
>
>Se o utilizador tiver instalado um perfil de e-mail antes da configuração de um perfil pelo Intune, o resultado da implementação do perfil de e-mail do Intune depende da plataforma do dispositivo:

>**iOS**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O perfil de e-mail duplicado criado pelo utilizador bloqueia a implementação de um perfil do Intune criado pelo administrador. Este é um problema comum, uma vez que os utilizadores do iOS criam um perfil de e-mail e depois fazem a inscrição. O portal da empresa informa o utilizador de que não é compatível devido ao respetivo perfil de e-mail configurado manualmente e indica-lhe para remover esse perfil. O utilizador deve remover o seu perfil de e-mail, para que o perfil do Intune possa ser configurado. De modo a evitar este problema, indique aos seus utilizadores para efetuarem a inscrição antes da instalação de um perfil de e-mail e permitirem que o Intune configure o perfil.

>**Windows**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O Intune substitui o perfil de e-mail existente criado pelo utilizador.

>**Samsung KNOX**: um perfil de e-mail duplicado existente é detetado com base no endereço de e-mail e é substituído pelo perfil do Intune. Se o utilizador configurar essa conta, esta é substituída novamente pelo perfil do Intune. Tenha em atenção que isto pode causar alguma confusão ao utilizador.

>Dado que o Samsung KNOX não utiliza o nome de anfitrião para identificar o perfil, recomendamos que não crie múltiplos perfis de e-mail a utilizar no mesmo endereço de e-mail em diferentes anfitriões, uma vez que estes substituem-se uns aos outros.

>**Android for Work**: o perfil do Intune só é aplicado a aplicações de e-mail específicas no perfil de trabalho do dispositivo e não afeta a configuração de e-mail do dispositivo.


## <a name="secure-email-profiles"></a>Proteger perfis de e-mail
Pode proteger os perfis de e-mail através de um certificado ou de uma palavra-passe.

### <a name="certificates"></a>Certificados
Quando cria o perfil de e-mail, escolhe um perfil de certificado que tenha criado anteriormente no Intune. Este é conhecido como o certificado de identidade e é utilizado para autenticar um perfil de certificado fidedigno (ou um certificado de raiz) para determinar que o dispositivo do utilizador tem permissões para se ligar. O certificado fidedigno é implementado no computador que autentica a ligação de e-mail, normalmente, o servidor de e-mail nativo.

Para mais informações sobre como criar e utilizar perfis de certificado no Intune, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).

### <a name="user-name-and-password"></a>Nome de utilizador e palavra-passe
O utilizador é autenticado no servidor de e-mail nativo ao fornecer o respetivo nome de utilizador e palavra-passe.

A palavra-passe não se encontra no perfil de e-mail, por isso, o utilizador tem de fornecer estas informações ao ligar-se ao e-mail.

### <a name="create-an-email-profile"></a>Criar um perfil de e-mail

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Política** &gt; **Adicionar Política**.

2.  Configure um dos seguintes tipos de política:

    -   **Perfil de E-mail para o Samsung KNOX Standard (4.0 e posterior)**

    -   **Perfil de E-mail (iOS 8.0 e posterior)**

    -   **Perfil de E-mail (Windows Phone 8.1 e posterior)**

    -   **Perfil de E-mail (Windows 10 Desktop e Mobile e posterior)**

    -   **Perfil de E-mail (Android for Work – Gmail)**

    -   **Perfil de E-mail (Android for Work – Nine Work)**

    Só pode criar e implementar uma política de perfil de e-mail personalizada. As definições recomendadas não estão disponíveis.

3.  Utilize a tabela seguinte para o ajudar a configurar as definições de perfil de e-mail:

|Nome da definição | Mais informações|
| ----------- | --------------- |
    |**Nome**|Nome exclusivo para o perfil de e-mail.|
    |**Descrição**|Uma descrição que o ajude a identificar este perfil.|
    |**Anfitrião**|O nome do anfitrião do servidor da empresa que aloja o seu serviço de e-mail nativo.|
    |**Nome da conta**|O nome a apresentar para a conta de e-mail, conforme irá aparecer aos utilizadores nos respetivos dispositivos.|
    |**Nome de Utilizador**|Como será obtido o nome de utilizador para a conta de e-mail. Selecione **Nome de utilizador** para um Exchange Server no local ou selecione **Nome Principal de Utilizador** para o Office 365.|
    |**Endereço de e-mail**|Como é gerado o endereço de e-mail para o utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.|
    |**Método de autenticação** (Android for Work, Samsung KNOX e iOS)|Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.|
    |**Selecionar um certificado de cliente para autenticação de cliente (Certificado de Identidade)** (Android for Work, Samsung KNOX e iOS)|Selecione o certificado SCEP de cliente criado anteriormente que será utilizado para autenticar a ligação ao Exchange. Para mais informações sobre como utilizar perfis de certificado no Intune, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md). Esta opção só é apresentada se o método de autenticação for **Certificados**.|
    |**Utilizar S/MIME** (Samsung KNOX e iOS)|Envie e-mail através de encriptação S/MIME.|
    |**Certificado de assinatura** (Samsung KNOX e iOS)|Selecione o certificado de assinatura que será utilizado para assinar o e-mail de envio. Esta opção só é apresentada quando seleciona **Utilizar S/MIME**.|
    |**Número de dias de e-mail a sincronizar**|O número de dias de e-mail que pretende sincronizar ou selecione **Sem limite** para sincronizar todos os e-mails disponíveis.|
    |**Agenda de sincronização** (Android for Work, Samsung KNOX, Windows Phone 8 e posterior, Windows 10)|Selecione a agenda pela qual os dispositivos irão sincronizar os dados do Exchange Server. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.|
    |**Utilizar SSL**|Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server. Para dispositivos com o Samsung KNOX 4.0 ou posterior, tem de exportar o seu certificado SSL do Exchange Server e implementá-lo como um Perfil de Certificado Fidedigno do Android no Intune. O Intune não suporta o acesso a este certificado se for instalado no Exchange Server através de outros meios.|
    |**Tipo de conteúdo para sincronizar** (todas as plataformas exceto o Android for Work – Gmail)|Selecione os tipos de conteúdo que pretende sincronizar com os dispositivos.|
    |**Permitir o envio de e-mail a partir de aplicações de terceiros** (apenas iOS)|Permitir que o utilizador selecione este perfil como conta predefinida para o envio de e-mail e permitir que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativo, por exemplo, para anexar ficheiros ao e-mail.|

> [!IMPORTANT]
>
> Se implementar um perfil de e-mail e, em seguida, pretender alterar os valores para **anfitrião** ou **Endereço de e-mail**, tem de eliminar o perfil de e-mail existente e criar um novo com os valores necessários.

4.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política** .

## <a name="deploy-the-policy"></a>Implementar a política

1.  Na área de trabalho **Política**, selecione a política que pretende implementar e, em seguida, escolha **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação**, para:

    -   **Para implementar a política** – selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, escolha **Adicionar** &gt; **OK**.

    -   **Para fechar a caixa de diálogo sem implementar a política** – selecione **Cancelar**.

Um resumo do estado e alertas na página **Descrição Geral** da área de trabalho **Política** identificam problemas com a política que necessitam da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho Dashboard.

> [!NOTE]
> - No Android for Work, certifique-se de que também implementa as aplicações Gmail ou Nine Work para além do perfil de e-mail adequado.
> - Se pretende remover um perfil de e-mail de um dispositivo, edite a implementação e remova todos os grupos dos quais o dispositivo é membro.



<!--HONumber=Nov16_HO1-->


