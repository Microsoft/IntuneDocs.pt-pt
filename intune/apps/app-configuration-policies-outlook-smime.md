---
title: Configurar S/MIME com o Outlook para iOS no Microsoft Intune
description: Entenda S/MIME com o Outlook para iOS no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9572f4accb1be232d4667d99b98beff90d81379
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000419"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Configurar S/MIME com o Outlook para iOS

O S/MIME (Internet Mail Extensions) seguro/multipropósito fornece uma camada adicional de segurança para emails enviados de e para uma conta do Exchange ActiveSync (EAS). O [Microsoft Outlook](https://aka.ms/omsmime) pode utilizar S/MIME para permitir que os usuários criptografem mensagens e anexos de saída, garantindo que somente o destinatário pretendido possa ler e acessar o conteúdo da mensagem ao usar contas do Office 365. Os usuários também podem assinar digitalmente uma mensagem, o que permite que os destinatários verifiquem a identidade do remetente e confirme que a mensagem não foi violada. Esse recurso é possível com o uso de certificados. Para obter mais informações, consulte [Understanding S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> Esse recurso foi atrasado, mas será lançado em breve.

> [!NOTE]
> Este tópico descreve como implantar certificados raiz confiáveis por meio [do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). O Microsoft Endpoint Manager é uma plataforma de gerenciamento de ponto de extremidade única e integrada para gerenciar todos os seus pontos de extremidade. Este centro de administração do Microsoft Endpoint Manager integra o ConfigMgr e o Microsoft Intune.

## <a name="about-message-encryption"></a>Sobre criptografia de mensagem
Os usuários podem enviar mensagens criptografadas para pessoas em sua organização e pessoas fora de sua organização se tiverem a parte pública dos certificados de criptografia. As chaves privadas associadas aos certificados de criptografia sempre devem ser protegidas e protegidas pelo destinatário da mensagem criptografada. A chave privada do certificado de criptografia é usada para descriptografar a mensagem pelo destinatário.

Mensagens criptografadas podem ser lidas somente por destinatários que têm o certificado correspondente ao que criptografou a mensagem. Se você tentar enviar uma mensagem criptografada para destinatários cujo certificado de criptografia não está disponível, o aplicativo solicitará que você remova esses destinatários antes de enviar o email.

## <a name="about-digital-signatures"></a>Sobre assinaturas digitais
Uma mensagem assinada digitalmente garante ao destinatário que a mensagem não foi violada e a identidade do remetente é autêntica. Os destinatários só poderão verificar a assinatura digital se estiverem usando um cliente de email que ofereça suporte a S/MIME.

## <a name="prerequisites"></a>Pré-requisitos
- O Outlook para iOS dá suporte apenas a S/MIME em contas do Office 365.
- O S/MIME deve ser configurado para o Office 365. Para obter mais informações, consulte [como configurar o S/MIME no Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- Você deve ter uma autoridade de certificação que possa emitir certificados que podem ser usados para assinatura e criptografia.
- Implante certificados raiz confiáveis por meio do Gerenciador de pontos de extremidade. Para obter mais informações, consulte [criar perfis de certificado confiável](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- Os certificados de criptografia devem ser importados no Gerenciador de pontos de extremidade. Para obter mais informações, consulte [configurar e usar certificados PKCS importados com o Intune](~/protect/certificates-imported-pfx-configure.md).
- Instale e configure o conector PFX para Microsoft Intune. Para obter mais informações, consulte [baixar, instalar e configurar o conector de certificado pfx para Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Os dispositivos devem ser registrados no MDM para receber certificados raiz e S/MIME confiáveis automaticamente do Gerenciador de pontos de extremidade.

> [!IMPORTANT]
> Você deve baixar e instalar o conector PFX atualizado (versão 6.1911.11.0 ou posterior) para Microsoft Intune usar certificados de criptografia S/MIME com o Outlook para iOS.

## <a name="smime-support-in-outlook-for-ios"></a>Suporte a S/MIME no Outlook para iOS
O Outlook para iOS dá suporte à assinatura S/MIME e à criptografia de mensagens usando certificados. Muitos clientes têm certificados de criptografia e assinatura separados, em oposição a ter um único certificado que dá suporte à assinatura e à criptografia. Os certificados de autenticação são geralmente exclusivos em dispositivos registrados de um usuário individual, enquanto os certificados de criptografia são compartilhados entre os dispositivos registrados de um usuário individual. Muitas vezes, os usuários terão usado S/MIME por anos e terão usado certificados de criptografia diferentes ao longo do tempo, pois os certificados são renovados. Os históricos de certificado de criptografia, incluindo suas chaves privadas, devem estar presentes no dispositivo do usuário para que o email que pode ter sido criptografado com qualquer um desses certificados no passado possa ser lido. Também é possível ter um único certificado que dê suporte à assinatura e à criptografia.

O Outlook para iOS dá suporte a duas maneiras de entregar certificados a dispositivos para que eles possam ser usados para S/MIME:

- **Os usuários** podem enviar por email os certificados S/MIME para si mesmos e instalá-los de anexos no Outlook para Ios em seus dispositivos móveis.
- **Os administradores** podem importar históricos de certificado de criptografia de qualquer autoridade de certificação para o Gerenciador de pontos de extremidade. O Endpoint Manager entregará automaticamente esses certificados a qualquer dispositivo registrado pelo usuário. Geralmente, protocolo SCEP (SCEP) é usado para certificados de assinatura. Com o SCEP, a chave privada é gerada e armazenada no dispositivo registrado e um certificado exclusivo é entregue a cada dispositivo registrado por um usuário, que pode ser usado para não-repúdio. Os administradores importam históricos de certificado de criptografia para seus usuários para o Gerenciador de ponto de extremidade, que, em seguida, entrega todos os certificados de criptografia do usuário para qualquer dispositivo registrado. Por fim, o Endpoint Manager dá suporte a credenciais derivadas para clientes que precisam de suporte para o padrão NIST 800-157. No iOS, o Portal da Empresa é usado para recuperar certificados de assinatura e criptografia do Intune.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Configurando o Outlook para iOS S/MIME no Gerenciador de pontos de extremidade
Para configurar o Outlook para iOS S/MIME no Gerenciador de pontos de extremidade, incluindo a entrega automática de certificados S/MIME que o Outlook para iOS pode usar, use as seguintes etapas:

### <a name="add-the-microsoft-outlook-app"></a>Adicionar o aplicativo Microsoft Outlook
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Adicione o aplicativo Microsoft Outlook para iOS da loja de aplicativos ao Gerenciador de pontos de extremidade ou Sincronize o Outlook para iOS no Apple Volume Purchase Program. Para obter mais informações, consulte [adicionar aplicativos da loja do Ios ao Microsoft Intune](~/apps/store-apps-ios.md) ou [como gerenciar aplicativos Ios e MacOS adquiridos por meio de Apple Volume Purchase Program com Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Criar a política de configuração do Outlook para iOS S/MIME

As etapas a seguir permitem criar e configurar a política do Outlook para iOS S/MIME no Gerenciador de pontos de extremidade. Essas configurações fornecem entrega automatizada dos certificados de assinatura e criptografia.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecione **aplicativos** > políticas de **configuração de aplicativos** > **Adicionar**.<br>
O painel **Adicionar política de configuração** será exibido.
2. Insira o **nome** e a **Descrição** da política de configuração.
3. Selecione **dispositivos gerenciados** como o **tipo de registro de dispositivo**.
4. Selecione **Ios/iPadOS** como a **plataforma**.
5. Clique em **selecionar o aplicativo necessário** para localizar e associar o aplicativo Microsoft Outlook para IOS que você adicionou anteriormente. 
6. Clique em **definições de configuração** para adicionar definições de configuração. 
    - Selecione **usar designer de configuração** ao lado do **formato de definições de configuração** e aceite as configurações padrão. Para obter mais informações, consulte [definições de configuração do Microsoft Outlook](~/apps/app-configuration-policies-outlook.md).
7. Clique em **S/MIME** para exibir as **configurações de s/MIME do Outlook**.
8. Defina **habilitar S/MIME** como **Sim**.
9. Defina **implantar certificados S/MIME do Intune** para **Sim**.
10. Em **certificados de assinatura** ao lado de **tipo de perfil de certificado**, escolha uma das seguintes opções:
    - **SCEP** – cria um certificado que é exclusivo para o dispositivo e usuário que podem ser usados pelo Microsoft Outlook para assinatura. Para obter informações relacionadas, consulte [Configurar a infraestrutura para dar suporte ao SCEP com o Intune](~/protect/certificates-scep-configure.md) e [criar um perfil de certificado SCEP](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **Certificados PKCS importados** – usa um certificado que é exclusivo para o usuário, mas pode ser compartilhado entre dispositivos e foi importado para o Gerenciador de ponto de extremidade pelo administrador em nome do usuário. O certificado é entregue a qualquer dispositivo registrado pelo usuário. O Gerenciador de pontos de extremidade selecionará automaticamente o certificado importado que dá suporte à assinatura para fornecer ao dispositivo o corresponde ao usuário registrado.
    - **Credenciais derivadas** – usa um certificado que já está no dispositivo que pode ser usado para assinatura. O certificado deve ser recuperado no dispositivo usando os fluxos de credenciais derivadas no Intune.
11. Em **certificados de criptografia** ao lado de **tipo de perfil de certificado**, escolha uma das seguintes opções:
    - **Certificados PKCS importados** – entrega todos os certificados de criptografia que foram importados para o Gerenciador de pontos de extremidade pelo administrador em qualquer dispositivo em que um usuário registrar o Gerenciador de ponto de extremidade selecionará automaticamente o certificado importado ou certificados que dão suporte à criptografia para entregar ao dispositivo que corresponde ao usuário registrado.
    - **Credenciais derivadas** – usa um certificado que já está no dispositivo que pode ser usado para assinatura. O certificado deve ser recuperado no dispositivo usando os fluxos de credenciais derivadas no Intune.
12. Ao lado de **notificações do usuário final**, escolha notificar usuários finais selecionando **portal da empresa** ou **email** para recuperar os certificados S/MIME para o Outlook para Ios.

    No iOS, os usuários devem usar o aplicativo Portal da Empresa para recuperar seus certificados S/MIME. O Gerenciador de pontos de extremidade informará o usuário de que eles precisam para iniciar o Portal da Empresa para recuperar seus certificados S/MIME por meio da seção notificações do Portal da Empresa, uma notificação por push e/ou um email. Clicar em uma das notificações levará o usuário a uma página de aterrissagem que informará o progresso da recuperação dos certificados. Depois que os certificados são recuperados, o usuário pode usar S/MIME de dentro do Microsoft Outlook para iOS para assinar e criptografar email.
    
    As notificações do usuário final incluem as seguintes opções:
       - **Portal da empresa** – se selecionado, os usuários receberão uma notificação por push em seu dispositivo, o que os levará para a página de aterrissagem em portal da empresa em que os certificados S/MIME serão recuperados.
        - **Email** – envia um email para o usuário final informando que eles precisam iniciar portal da empresa para recuperar seus certificados S/MIME. Se o usuário estiver em seu dispositivo iOS registrado quando clicar no link no email, ele será redirecionado para o Portal da Empresa para recuperar seus certificados.
    
13. Selecione **atribuições** para atribuir a política de configuração de aplicativo aos grupos do Azure AD. Para obter mais informações, veja [Atribuir aplicações a grupos com o Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações, consulte [políticas de configuração de aplicativo para Microsoft Intune](app-configuration-policies-overview.md).
