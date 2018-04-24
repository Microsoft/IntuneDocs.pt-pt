---
title: Gestão do Apple DEP para dispositivos iOS
description: Implemente um perfil de inscrição que inscreva dispositivos iOS comprados através do Programa de Inscrição de Dispositivos iOS (DEP) por ondas eletromagnéticas em dispositivos Apple geridos.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 383309944bd185ea2abc79b3bcc3488ad3377b50
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>Inscrever dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Microsoft Intune pode implementar um perfil de inscrição que inscreve os dispositivos iOS comprados através do Programa de Inscrição de Dispositivos (DEP) por ondas eletromagnéticas. O pacote de inscrição pode incluir opções do assistente de configuração do dispositivo.

>[!NOTE]
>A inscrição DEP não pode ser utilizada com o método do [gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
>Além disso, se os utilizadores inscreverem os dispositivos iOS (por exemplo, através da aplicação Portal da Empresa) e os números de série dos mesmos forem posteriormente importados e lhes for atribuído um perfil de DEP, a inscrição do dispositivo no Intune será anulada.
> Também deve ter em atenção que o macOS atualmente não suporta DEP.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-dep-management"></a>Pré-requisitos para a inscrição de dispositivos iOS com a gestão do Apple DEP

- [Instalar um certificado do APNs](set-up-ios-and-mac-management-with-microsoft-intune.md)

- A sua organização tem de aderir ao Apple DEP e obter dispositivos através desse programa. Os detalhes do processo encontram-se disponíveis em: [https://deploy.apple.com](https://deploy.apple.com). Entre as vantagens do programa incluem-se a configuração automatizada de dispositivos sem utilizar um cabo USB para ligar cada dispositivo a um computador.

- Antes de poder inscrever dispositivos iOS pertencentes à empresa no DEP, precisa de um token do DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos propriedade da empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do Perfil de Inscrição para a Apple e atribuir dispositivos a esses perfis.

## <a name="steps-to-enroll-ios-devices-by-using-apple-dep-management"></a>Passos para inscrever dispositivos iOS com a gestão do Apple DEP

Os seguintes passos explicam como inscrever dispositivos iOS no "dia 0" com a gestão do Apple DEP. À medida que os dispositivos são adicionados e removidos da sua organização, é provável que repita alguns destes passos, como adicionar ou remover números de série, conforme descrito abaixo.

### <a name="get-an-encryption-key"></a>Obter uma Chave de Encriptação

1. Como utilizador administrativo, abra a [Consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS** &gt; **Programa de Inscrição de Dispositivos** e selecione **Transferir a Chave de Encriptação**.

2. Guarde o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.

![Atualizar um token do programa de inscrição de dispositivos](../media/dev-sa-ios-dep.png)

### <a name="get-a-device-enrollment-program-token"></a>Obter um token do Programa de Inscrição de Dispositivos

1. Aceda ao [Portal do Programa de Registo de Dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. Este ID Apple tem de ser utilizado posteriormente para renovar o seu token do DEP.

2. No Portal do Programa de Inscrição de Dispositivos, aceda a **Programa de Inscrição de Dispositivos** &gt; **Gerir Servidores** e, em seguida, selecione **Adicionar Servidor MDM**.

3. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

4. É aberta a caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

5. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** mostra uma ligação para o **Token do Seu Servidor**. Transfira o ficheiro do token do servidor (.p7m) para o seu computador e, em seguida, selecione **Concluído**.

   Este ficheiro do certificado (.p7m) é utilizado para estabelecer uma relação de confiança entre os servidores do Intune e do Programa de Inscrição de Dispositivos da Apple.

### <a name="add-the-dep-token-to-intune"></a>Adicionar o token do DEP ao Intune

1. Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS** &gt; **Programa de Inscrição de Dispositivos**.

2. Selecione **Upload the DEP Token**. **Procure** o ficheiro do certificado (.p7m), introduza o seu **ID Apple** e, em seguida, selecione **Carregar**.

### <a name="add-the-corporate-device-enrollment-policy"></a>Adicionar a Política de Inscrição de Dispositivos da Empresa

1. Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com) aceda a **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione **Adicionar**.

2. Forneça detalhes **Gerais**, incluindo **Nome** e **Descrição** e especifique se os dispositivos atribuídos ao perfil têm afinidade de utilizador ou se pertencem a um grupo:

   - **Pedido de afinidade de utilizador**: o dispositivo tem de ser afiliado a um utilizador durante a configuração inicial para poder receber permissões para aceder ao e-mail e aos dados da empresa em nome do utilizador. A **Afinidade de utilizador** deve ser configurada para dispositivos geridos por DEP que pertencem aos utilizadores e que precisam de utilizar o portal da empresa (ou seja, para instalar aplicações). A autenticação multifator (MFA) não funciona durante a inscrição em dispositivos DEP com afinidade de utilizador. Depois da inscrição, a MFA funciona conforme esperado nestes dispositivos. Durante a inscrição em dispositivos DEP, não pode ser pedida a alteração da palavra-passe aos novos utilizadores que tenham de alterar a palavra-passe no primeiro início de sessão. Além disso, não será pedido aos utilizadores cujas palavras-passe expiraram que reponham a palavra-passe durante a inscrição DEP e os mesmos terão de repor a palavra-passe a partir de um dispositivo diferente.

     >[!NOTE]
     >O DEP com afinidade de utilizador requer a ativação de um [ponto final de Nome de Utilizador/Misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) para pedir o token de utilizador. [Saiba mais sobre o WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   - **Sem afinidade de utilizador**: o dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores, incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio, não irão funcionar.

   Também pode **Atribuir dispositivos ao seguinte grupo**. Selecione **Selecionar…** para escolher um grupo.

   > [!Important]
   > As atribuições de grupos estão a ser mudadas do Intune para o Azure Active Directory. Assim que a sua conta do Intune receber a atualização aplicável, não verá a opção **Atribuir dispositivos ao seguinte grupo**. [Saiba mais](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

3. Ative **Configurar definições do Programa de Inscrição de Dispositivos para esta política** para suportar DEP.

      ![Painel do assistente de configuração](../media/pol-sa-corp-enroll.png)

   Estão disponíveis as seguintes definições para dispositivos geridos por DEP:

   - **Departamento** – é apresentado quando os utilizadores tocam em **Sobre a Configuração de** durante a ativação
   - **Número de telefone de suporte** – aparece quando o utilizador clica no botão **Preciso de ajuda** durante a ativação
   - **Modo de preparação** – definido durante a ativação e não pode ser alterado sem a reposição de fábrica do dispositivo:
       - **Não supervisionado** – capacidades de gestão limitadas
       - **Supervisionado** – ativa mais opções de gestão e desativa o Bloqueio de Ativação por predefinição
   - **Bloquear perfil de inscrição para o dispositivo** – definido durante a ativação e não pode ser alterado sem uma reposição de fábrica
       - **Desativar** – permite que o perfil de gestão seja removido do menu **Definições**
       - **Ativar** – (é necessário o **Modo de Preparação** = **Supervisionado**) desativa a opção de menu nas Definições do iOS para remover o perfil de gestão
   - **Opções do Assistente de Configuração** – estas definições opcionais podem ser configuradas mais tarde no menu **Definições** de iOS.
     - **Código de Acesso** – pedido de código de acesso durante a ativação. Peça sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação)
       - **Serviços de Localização** – se ativado, o Assistente de Configuração solicita o serviço durante a ativação
       - **Restaurar** – se estiver ativado, o Assistente de Configuração solicita a cópia de segurança de iCloud durante a ativação
       - **ID Apple** – se estiver ativado, o iOS irá pedir aos utilizadores um ID Apple quando o Intune tenta instalar uma aplicação sem um ID. É necessário um ID Apple para transferir aplicações iOS da App Store, incluindo as instaladas pelo Intune.
       - **Termos e Condições** – se ativado, o Assistente de Configuração solicita aos utilizadores que aceitem os termos e condições da Apple durante a ativação
       - **Touch ID** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
       - **Apple Pay** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
       - **Zoom** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
       - **Siri** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
       - **Enviar dados de diagnóstico para a Apple** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
   - **Ativar a gestão adicional do Apple Configurator** – defina como **Não Permitir** para impedir a sincronização de ficheiros com o iTunes ou a gestão através do Apple Configurator. É recomendado selecionar **Não Permitir**, exportar qualquer configuração adicional do Apple Configurator e, em seguida, implementar como um perfil de configuração iOS Personalizada através do Intune, em vez de utilizar esta definição para permitir a implementação manual com ou sem um certificado.
      - **Não Permitir** – impede o dispositivo de comunicar através de USB (desativa o emparelhamento)
      - **Permitir** – permite a um dispositivo comunicar através de ligação USB para qualquer PC ou Mac
      - **Requer certificado** – permite o emparelhamento com um Mac, com um certificado importado para o perfil de inscrição

### <a name="assign-the-profile-to-devices"></a>Atribuir o perfil a dispositivos

1. Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com) aceda a **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione **Atribuir**.

2. Selecione os dispositivos aos quais quer atribuir o perfil que criou. Pode selecionar **Todos os dispositivos** ou selecionar dispositivos específicos e, em seguida, selecionar **Adicionar**.

> [!Important]
> Atualmente, o Intune permite-lhe designar um perfil de inscrição de dispositivos "predefinido", o que significa que os novos números de série são atribuídos automaticamente a esse perfil predefinido quando sincronizar novos números de série com o serviço DEP da Apple. Quando o seu inquilino for migrado para o novo portal do Azure num futuro próximo, deixará de poder predefinir um perfil e de ter números de série atribuídos automaticamente a esse perfil. Em vez disso, terá de atribuir números de série a um perfil específico. [Saiba mais](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="assign-dep-devices-for-management"></a>Atribuir Dispositivos DEP para Gestão

1. Aceda ao [Portal do Programa de Registo de Dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa.

2. Aceda a **Programa de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.

3. Especifique como irá **Escolher Dispositivos**, fornecer informações sobre o dispositivo e especificar detalhes pelo **Número de Série**e **Número da Encomenda**do dispositivo, ou como **Carregar Ficheiro CSV**.

4. Selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado para o Microsoft Intune e, em seguida, selecione **OK**.

### <a name="synchronize-dep-managed-devices"></a>Sincronizar Dispositivos Geridos por DEP

Este passo sincroniza dispositivos com o serviço DEP da Apple e faz com que os dispositivos sejam apresentados na consola do Intune.

1. Como utilizador administrativo, abra a [Consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS** &gt; **Programa de Inscrição de Dispositivos** e, em seguida, selecione **Sincronizar agora**. É enviado um pedido de sincronização para a Apple.

2. Para ver dispositivos geridos por DEP após a sincronização, na [Consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Grupos** &gt; **Todos os Dispositivos** &gt; **Dispositivos da Empresa Pré-inscritos** &gt; **Por Número de Série iOS**. Na área de trabalho **By iOS Serial Number (Por Número de Série iOS)**, o **State (Estado)** dos dispositivos geridos indica "Not contacted" ("Não contactado") até o dispositivo ser ligado e executar o Assistente de Configuração para inscrever o dispositivo.

   Para estar em conformidade com os termos da Apple para o tráfego DEP aceitável, o Intune impõe as seguintes restrições:

   - Uma sincronização completa do DEP não pode ser executada mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza cada número de série que a Apple tenha atribuído ao Intune, quer o número tenha sido ou não sincronizado anteriormente. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.

   - São atribuídos 10 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.

### <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Os dispositivos pertencentes à empresa podem agora ser distribuídos pelos utilizadores. Quando um dispositivo iOS é ativado, será inscrito para gestão pelo Intune. O limite de dispositivos do utilizador aplica-se a dispositivos geridos por DEP.

>[!NOTE]
>Se um utilizador tentar inscrever um dispositivo DEP, mas tiver excedido o limite de dispositivos, a inscrição falhará silenciosamente sem avisar o utilizador.

## <a name="changes-to-intune-group-assignments"></a>Alterações às atribuições de grupo do Intune

A partir de abril de 2017, a gestão de grupos de dispositivos mudará para o Azure Active Directory. Após a transição para grupos do Azure Active Directory, a atribuição de grupo não será apresentada nas opções do Perfil de Inscrição Empresarial. Uma vez que esta alteração vai ser implementada durante alguns meses, poderá não estar disponível de imediato. Depois de mudar para o novo portal, as atribuições de grupos de dispositivos dinâmicas podem ser definidas com base nos nomes de Perfil de Inscrição Empresarial.

Após a migração, para cada grupo de dispositivos do Intune previamente atribuído por um perfil de Inscrição de Dispositivos da Empresa, será criado um grupo de dispositivos dinâmicos correspondente no Azure AD com base no nome do perfil de Inscrição de Dispositivos da Empresa. Os novos nomes do perfil têm o formato *EnrollmentProfile:&lt;nome do perfil associado&gt;*. Este processo garante que os dispositivos previamente atribuídos a um grupo de dispositivos serão inscritos de forma automática no grupo com a política e as aplicações implementadas.

A criação automática de grupos ocorre apenas uma vez, durante a migração dos grupos. Após a migração, os administradores do Intune têm de criar grupos através do portal do Azure. Para obter detalhes sobre como isso afeta a inscrição de dispositivos iOS pertencentes à empresa, veja [Changes to Automatic Grouping for Corporate Pre-enrolled iOS Devices (Alterações ao Agrupamento Automático para Dispositivos iOS Pré-Inscritos Empresariais)](https://blogs.technet.microsoft.com/intunesupport/2017/04/19/changes-to-automatic-grouping-for-corporate-pre-enrolled-ios-devices/).

Além disso, [Saiba mais sobre os grupos do Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).

### <a name="see-also"></a>Consulte também
[Pré-requisitos para inscrever dispositivos](prerequisites-for-enrollment.md)
