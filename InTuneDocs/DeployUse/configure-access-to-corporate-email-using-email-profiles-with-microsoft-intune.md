---
title: Aceder ao e-mail empresarial com perfis de e-mail | Microsoft Intune
description: "As definições de perfil de e-mail podem ser utilizadas para configurar as definições de acesso de e-mail para clientes de e-mail específicos em dispositivos móveis."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/021/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: cddc1a68b14520774555416dcd496a06a0f89385


---

# Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune
Muitas plataformas móveis incluem um cliente de e-mail *nativo* que é fornecido como parte do sistema operativo.  Alguns destes clientes podem ser configuráveis através de perfis de e-mail, descritos neste tópico.

Se precisar de prevenção de perda de dados (DLP) adicional, escolha [Acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), que controla o acesso à caixa de correio do utilizador em qualquer cliente de e-mail, incluindo clientes de e-mail nativos.

As definições de perfil de e-mail podem ser utilizadas para configurar as definições de acesso de e-mail para clientes de e-mail específicos em dispositivos móveis. A maioria das plataformas móveis inclui um cliente de e-mail *nativo* que é fornecido como parte do sistema operativo.  Nas plataformas suportadas, os clientes de e-mail nativos podem ser configurados pelo Microsoft Intune para permitir que os utilizadores acedam ao respetivo e-mail da empresa nos dispositivos pessoais sem qualquer configuração.  

Os administradores de TI ou os utilizadores também podem optar por instalar clientes de e-mail alternativos como, por exemplo, o Microsoft Outlook para Android ou iOS.  Estes clientes de e-mail podem não suportar perfis de e-mail e não são configuráveis através de perfis de e-mail do Microsoft Intune.  

Pode utilizar os perfis de e-mail para configurar o cliente de e-mail nativo nos seguintes tipos de dispositivos:
-   Windows Phone 8 e posterior
-   Ambiente de trabalho do Windows 10, Windows 10 Mobile e posterior
-   iOS 7.1 e posterior
-   Samsung KNOX Standard (4.0 e posterior)


Para além de configurar uma conta de e-mail no dispositivo, pode configurar definições de sincronização, tais como a quantidade de e-mail a sincronizar e, dependendo do tipo de dispositivo, os tipos de conteúdo a sincronizar.
>[!NOTE]
>
>Se o utilizador tiver instalado um perfil de e-mail anterior ao aprovisionamento de um perfil pelo Intune, sendo que o resultado da implementação do perfil de e-mail do Intune depende da plataforma do dispositivo:

>-**iOS**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. Um perfil de e-mail duplicado criado pelo utilizador irá bloquear a implementação de um perfil do Intune criado pelo administrador. Este é um problema comum, uma vez que os utilizadores do iOS criam um perfil de e-mail e depois fazem a inscrição. O portal da empresa irá informar o utilizador da não conformidade devido ao respetivo perfil de e-mail configurado manualmente e solicitará ao utilizador para remover esse perfil. O utilizador deve remover o respetivo perfil de e-mail, para que o perfil do Intune possa ser implementado. Para evitar este problema, indique aos seus utilizadores para inscreverem-se antes de instalar um perfil de e-mail e para permitir que o Intune implemente o perfil.

>-**Windows**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. O Intune vai substituir o perfil de e-mail existente criado pelo utilizador.

>-**Samsung KNOX**: o Intune identifica uma conta de e-mail duplicada com base no endereço de e-mail e substituí-lo com o perfil do Intune. Se o utilizador configurar essa conta, esta será substituída novamente pelo perfil do Intune. Tenha em atenção que isto pode causar alguma confusão ao utilizador cuja configuração de conta seja substituída.

>Dado que o Samsung KNOX não utiliza o nome de anfitrião para identificar o perfil, recomendamos que não crie múltiplos perfis de e-mail para implementar o mesmo endereço de e-mail em diferentes anfitriões, como estes serão substituídas entre si.
    

## Proteger perfis de e-mail
Pode proteger os perfis de e-mail através de um de dois métodos:

### Certificados
Quando cria o perfil de e-mail, escolhe um perfil de certificado que tenha criado anteriormente no Intune. Este é conhecido como o certificado de identidade e é utilizado para autenticar um perfil de certificado fidedigno (ou um certificado de raiz) para determinar que o dispositivo do utilizador tem permissões para se ligar. O certificado fidedigno é implementado no computador que autentica a ligação de e-mail, normalmente, o servidor de e-mail nativo.

Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [Secure resource access with  certificate profiles (Proteger o acesso a recursos com perfis de certificado)](secure-resource-access-with-certificate-profiles.md).

### Nome de utilizador e palavra-passe
O utilizador é autenticado no servidor de e-mail nativo ao fornecer o respetivo nome de utilizador e palavra-passe.

A palavra-passe não se encontra no perfil de e-mail, por isso, o utilizador terá de fornecer estas informações ao ligar-se ao e-mail.

### Criar um perfil de e-mail

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; ** Adicionar Política**.

2.  Configure um dos seguintes tipos de política:

    -   **Perfil de E-mail para o Samsung KNOX Standard (4.0 e posterior)**

    -   **Perfil de e-mail (iOS 7.1 e posterior)**

    -   **Perfil de E-mail (Windows Phone 8 e posterior)**

    -   **Perfil de E-mail (Windows 10 Desktop e Mobile e posterior)**

    Só pode criar e implementar uma política de perfil de e-mail personalizada. As definições recomendadas não estão disponíveis.

3.  Utilize a tabela seguinte para o ajudar a configurar as definições de perfil de e-mail:
    |Nome da definição|Mais informações|
    |----------------|-----------------------------------------------------------------------------|
    |**Nome**|Nome exclusivo para o perfil de e-mail.|
    |**Descrição**|Uma descrição que o ajude a identificar este perfil.|
    |**Anfitrião**|O nome do anfitrião do servidor da empresa que aloja o seu serviço de e-mail nativo.|
    |**Nome da conta**|O nome a apresentar para a conta de e-mail, conforme irá aparecer aos utilizadores nos respetivos dispositivos.|
    |**Nome de Utilizador**|Como será obtido o nome de utilizador para a conta de e-mail. Selecione **Nome de utilizador** para um Exchange Server no local ou selecione **Nome Principal de Utilizador** para o Office 365.|
    |**Endereço de e-mail**|Como é gerado o endereço de e-mail para o utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.|
    |**Método de autenticação** (Samsung KNOX e iOS)|Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.|
    |**Selecionar um certificado de cliente para autenticação de cliente (Certificado de Identidade)** (Samsung KNOX e iOS)|Selecione o certificado SCEP de cliente criado anteriormente que será utilizado para autenticar a ligação ao Exchange. Para obter mais informações sobre como utilizar perfis de certificado no Intune, veja [Secure resource access with  certificate profiles (Proteger o acesso a recursos com perfis de certificado)](secure-resource-access-with-certificate-profiles.md).<br /><br />Esta opção só é apresentada se o método de autenticação for **Certificados**.|
    |**Utilizar S/MIME** (Samsung KNOX e iOS)|Envie e-mail através de encriptação S/MIME.|
    |**Certificado de assinatura** (Samsung KNOX e iOS)|Selecione o certificado de assinatura que será utilizado para assinar o e-mail de envio.<br /><br />Esta opção só é apresentada quando seleciona **Utilizar S/MIME**.|
    |**Número de dias de e-mail a sincronizar**|O número de dias de e-mail que pretende sincronizar ou selecione **Sem limite** para sincronizar todos os e-mails disponíveis.|
    |**Agenda de sincronização** (Samsung KNOX, Windows Phone 8 e posterior, Windows 10)|Selecione a agenda pela qual os dispositivos irão sincronizar os dados do Exchange Server. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.|
    |**Utilizar SSL**|Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.<br /><br />Para dispositivos com o Samsung KNOX 4.0 ou posterior, tem de exportar o seu certificado SSL do Exchange Server e implementá-lo como um Perfil de Certificado Fidedigno do Android no Intune. O Intune não suporta o acesso a este certificado se for instalado no Exchange Server através de outros meios.|
    |**Tipo de conteúdo a sincronizar**|Selecione os tipos de conteúdo que pretende sincronizar com os dispositivos.|
    |**Permitir o envio de e-mail a partir de aplicações de terceiros** (apenas iOS)|Permitir que o utilizador selecione este perfil como conta predefinida para o envio de e-mail e permitir que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativo, por exemplo, para anexar ficheiros ao e-mail.|

    > [!IMPORTANT]
    > Se implementar um perfil de e-mail e, em seguida, pretender alterar os valores para **anfitrião** ou **Endereço de e-mail**, tem de eliminar o perfil de e-mail existente e criar um novo com os valores necessários.

4.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política** .

## Implementar a política

1.  Na área de trabalho **Política** , selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Fechar a caixa de diálogo sem implementar a política** - clique em **Cancelar**.

Um resumo do estado e alertas na página **Descrição Geral** da área de trabalho **Política** identificam problemas com a política que necessitam da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho Dashboard.

> [!NOTE]
> Se pretende remover um perfil de e-mail de um dispositivo, edite a implementação e remova todos os grupos dos quais o dispositivo é membro.



<!--HONumber=Aug16_HO1-->


