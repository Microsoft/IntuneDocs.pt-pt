---
title: Resolver problemas de inscrição de dispositivos
titleSuffix: Microsoft Intune
description: Sugestões para resolver problemas de inscrição de dispositivos no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06a8bd8d0a46b7d7eed8efb4cb8b4c2d4e21f77d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509288"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Resolver problemas de inscrição de dispositivos no Microsoft Intune

Este artigo fornece sugestões para resolução de problemas [inscrição de dispositivos](device-enrollment.md) problemas. Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](get-support.md) para ver mais formas de obter ajuda.


## <a name="initial-troubleshooting-steps"></a>Passos iniciais de resolução de problemas

Antes de iniciar a resolução de problemas, certifique-se de que configurou o Intune corretamente para permitir a inscrição. Pode ler sobre estes requisitos de configuração em:

-   [Preparar a inscrição de dispositivos no Microsoft Intune](setup-steps.md)
-   [Configurar a gestão de dispositivos iOS e Mac](ios-enroll.md)
-   [Configurar a gestão de dispositivos Windows](windows-enroll.md)
-   [Configurar a gestão de dispositivos Android](android-enroll.md) –não são precisos passos adicionais

Também pode confirmar que a hora e a data no dispositivo do utilizador estão definidas corretamente:

1. Reinicie o dispositivo.
2. Confirme que a data e a hora estão definidas para próximo da hora padrão de GMT (+ ou - 12 horas) para o fuso horário do utilizador final.
3. Desinstale e reinstale o portal da empresa do Intune (se aplicável).

Os utilizadores de dispositivos geridos podem recolher registos de inscrição e de diagnóstico para que possa analisá-los. Pode encontrar instruções de utilizador para recolher os registos em:

- [Enviar erros de inscrição de dispositivos Android para o seu administrador de TI](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Enviar erros de dispositivos iOS para o seu administrador de TI](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Problemas de inscrição gerais
Estes problemas podem ocorrer em todas as plataformas de dispositivos.

### <a name="device-cap-reached"></a>Máximo de dispositivos atingido
**Problema:** Um utilizador recebe um erro durante a inscrição (como **Portal da empresa temporariamente indisponível**) e o dmpdownloader. log no Configuration Manager contém o erro **DeviceCapReached**.

**Resolução:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Verificar número de dispositivos inscritos e permitidos

Verifique se o utilizador não possui um número de dispositivos atribuídos superior ao máximo permitido ao seguir estes passos:

1. No Intune, selecione **Inscrição de dispositivos** > **Restrições de inscrição** > **Restrições de limite de dispositivos**. Observe o valor apresentado na coluna **Limite de dispositivos**.

2. No Intune, selecione **Utilizadores** > **Todos os utilizadores** > selecione o utilizador > **Dispositivos**. Observe o número de dispositivos inscritos.

3. Se o número de dispositivos inscritos do utilizador for igual à respetiva restrição de limite de dispositivos, o utilizador não poderá inscrever mais dispositivos até:
    - [Os dispositivos existentes serem removidos](devices-wipe.md) ou
    - Aumentar o limite de dispositivos ao [definir restrições de dispositivos](enrollment-restrictions-set.md#set-device-limit-restrictions).

Para evitar atingir limites de dispositivos, certifique-se de que remove os registos de dispositivos obsoletos.

> [!NOTE]
> 
> Pode evitar o limite máximo de inscrições de dispositivos com a conta Gestor de Inscrição de Dispositivos, conforme descrito em [Enroll corporate-owned devices with the Device Enrollment Manager in Microsoft Intune (Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune)](device-enrollment-manager-enroll.md).
> 
> A inscrição de uma conta de utilizador adicionada à conta Gestores de Inscrição de Dispositivos não pode ser concluída quando a política de Acesso Condicional é imposta para o início de sessão desse utilizador específico.

### <a name="company-portal-temporarily-unavailable"></a>Portal da Empresa Temporariamente Indisponível
**Problema:** Os utilizadores recebem um **Portal da empresa temporariamente indisponível** erro no dispositivo.

**Resolução:**

1.  Remova a aplicação Portal da Empresa do Intune do dispositivo.

2.  No dispositivo, abra o browser, navegue para [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) e experimente um início de sessão do utilizador.

3.  Se o utilizador não conseguir iniciar sessão, deverá experimentar outra rede.

4.  Se não conseguir, confirme se as credenciais do utilizador foram sincronizadas corretamente com o Azure Active Directory.

5.  Se o utilizador iniciar sessão com êxito, um dispositivo iOS pedirá para instalar a aplicação Portal da Empresa do Intune e inscrever. Num dispositivo Android, terá de instalar manualmente a aplicação Portal da Empresa do Intune, podendo a seguir repetir a inscrição.

### <a name="mdm-authority-not-defined"></a>Autoridade de MDM não definida
**Problema:** Um utilizador recebe uma **autoridade MDM não definida** erro.

**Resolução:**

1.  Verifique se a Autoridade MDM foi [definida adequadamente](mdm-authority-set.md).
    
2.  Confirme se as credenciais do utilizador foram sincronizadas corretamente com o Azure Active Directory. Pode verificar se o UPN do utilizador corresponde ao informações do Active Directory no Centro de administração do Microsoft 365.
    Se o UPN não corresponder às informações do Active Directory:

    1.  Desative o DirSync no servidor local.

    2.  Elimine o utilizador sem correspondência da lista de utilizadores **Portal de Contas do Intune**.

    3.  Aguarde cerca de uma hora para permitir que o serviço do Azure remova os dados incorretos.

    4.  Ative novamente o DirSync e verifique se o utilizador está agora sincronizado corretamente.

3.  Num cenário em que esteja a utilizar o System Center Configuration Manager com o Intune, verifique se o utilizador tem um ID de Utilizador de Cloud válido:

    1.  Abra o SQL Management Studio.

    2.  Ligue à BD adequada.

    3.  Abra a pasta de bases de dados e localize e abra a pasta **CM_DBName**, em que DBName é o nome da base de dados do cliente.

    4.  Na parte superior, escolha **Nova Consulta** e execute as seguintes consultas:

        -   Para ver todos os utilizadores: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Para ver Utilizadores Específicos, utilize a consulta seguinte, em que %testuser1% é um marcador de posição para o username@domain.com do utilizador que pretende procurar: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Depois de escrever a consulta, selecione **!Execute**.
        Depois de devolvidos os resultados, procure o ID clouduser.  Se não for encontrado nenhum ID, o utilizador não está licenciado para utilizar o Intune.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Não é possível criar a política ou inscrever dispositivos se o nome da empresa incluir carateres especiais
**Problema:** Não é possível criar a política ou inscrever dispositivos.

**Resolução:** Na [Centro de administração do Microsoft 365](https://admin.microsoft.com/), remova os carateres especiais do nome da empresa e guardar as informações da empresa.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Não é possível iniciar sessão ou inscrever dispositivos quando tem vários domínios verificados
**Problema:** Esse problema pode ocorrer quando adiciona um segundo domínio verificado ao seu AD FS. Os utilizadores com o sufixo de nome principal de utilizador (UPN) do segundo domínio podem não conseguir iniciar sessão nos portais ou inscrever dispositivos.


<strong>Resolução:</strong> Os clientes do Microsoft Office 365 são necessários para implementar uma instância separada do AD FS 2.0 serviço de Federação para cada sufixo se eles:
- utilizarem o início de sessão único (SSO) através do AD FS 2.0 e
- tiverem vários domínios de nível superior para sufixos de UPN dos utilizadores dentro da respetiva organização (por exemplo, @contoso.com ou @fabrikam.com).


Um [rollup para o AD FS 2.0](http://support.microsoft.com/kb/2607496) funciona em conjunto com o comutador <strong>SupportMultipleDomain</strong> para permitir que o servidor do AD FS suporte este cenário sem necessitar de servidores do AD FS 2.0 adicionais. Para obter mais informações, veja [este blogue](https://blogs.technet.microsoft.uucom/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Problemas do Android

### <a name="android-enrollment-errors"></a>Erros de inscrição de dispositivos Android

A seguinte tabela indica os erros que os utilizadores finais poderão ver ao inscrever dispositivos Android no Intune.

|Mensagem de erro|Problema|Resolução|
|---|---|---|
|**O administrador de TI tem de lhe atribuir uma licença para obter acesso**<br>O seu administrador de TI ainda não lhe deu acesso para utilizar esta aplicação. Obtenha ajuda do seu administrador de TI ou tente novamente mais tarde.|Não é possível inscrever o dispositivo porque a conta do utilizador não tem a licença necessária.|Antes de os utilizadores poderem inscrever os respetivos dispositivos, é preciso que lhes tenha sido atribuída a licença necessária. Esta mensagem indica que têm o tipo de licença errado para a autoridade de gestão de dispositivos móveis. Por exemplo, verão este erro se as seguintes situações se verificarem:<ol><li>O Intune foi definido como a autoridade de gestão de dispositivos móveis</li><li>Estão a utilizar uma licença do System Center 2012 R2 Configuration Manager.</li></ol>Para obter mais informações, veja [Atribuir licenças do Intune às suas contas de utilizador](/intune/licenses-assign).|
|**O administrador de TI tem de definir a autoridade MDM**<br>Reparámos que o seu administrador de TI não definiu uma autoridade MDM. Obtenha ajuda do seu administrador de TI ou tente novamente mais tarde.|A autoridade de gestão de dispositivos móveis não foi definida.|A autoridade de gestão de dispositivos móveis não foi definida no Intune. Saiba mais sobre como [definir a autoridade de gestão de dispositivos móveis](/intune/mdm-authority-set).|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Os dispositivos não conseguem registar com o serviço Intune e são apresentados como em "Mau estado de funcionamento" na consola de administração do Intune
**Problema:** Alguns dispositivos Samsung que executem versões Android 4.4.x e 5.x poderão deixar de entrada no serviço Intune. Se os dispositivos não fizerem o registo:

- Não podem receber políticas, aplicações e comandos remotos a partir do serviço do Intune.
- Mostram o Estado de Gestão **Mau estado de funcionamento** na consola do administrador.
- Os utilizadores protegidos por políticas de acesso condicional podem perder o acesso a recursos empresariais.

O software Samsung Smart Manager, incluído em determinados dispositivos Samsung, pode desativar o Portal da Empresa do Intune e os respetivos componentes. Quando o Portal da Empresa está num estado desativado, este não pode ser executado em segundo plano e não pode contactar o serviço do Intune.

**Resolução n.º 1:**

Informe os utilizadores para iniciarem manualmente a aplicação Portal da Empresa. Depois de a aplicação reiniciar, o dispositivo faz o registo com o serviço do Intune.

> [!IMPORTANT]
> Abrir a aplicação Portal da Empresa manualmente é uma solução temporária, uma vez que o Samsung Smart Manager poderá desativar novamente a aplicação Portal da Empresa.

**Resolução n.º 2:**

Informe os utilizadores para tentarem atualizar para Android 6.0. O problema da desativação não ocorre em dispositivos com Android 6.0. Para verificar se está disponível uma atualização, aceda a **Definições** > **Acerca do dispositivo** > **Transferir atualizações manualmente** e siga as instruções.

**Resolução n.º 3:**

Se a Resolução n.º 2 não funcionar, solicite aos seus utilizadores que sigam estes passos para fazer com o que o Smart Manager exclua a aplicação Portal da Empresa:

1. Inicie a aplicação Smart Manager no dispositivo.

   ![Selecione o ícone do Smart Manager no dispositivo](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Escolha o mosaico **Bateria**.

   ![Selecione o mosaico Bateria](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. Em **Poupança de energia da aplicação** ou **Otimização da aplicação**, selecione **Detalhes**.

   ![Selecionar Detalhes em Poupança de energia da aplicação ou Otimização da aplicação](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. Escolha **Portal da Empresa** da lista de aplicações.

   ![Selecionar o Portal da Empresa da lista de aplicações](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Marque **Desativado**.

   ![Selecionar Desativado na caixa de diálogo Otimização da aplicação](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. Em **Poupança de energia da aplicação** ou **Otimização da aplicação**, confirme que o Portal da Empresa está desativado.

   ![Confirmar que o Portal da Empresa está desativado](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Falha na instalação do perfil
**Problema:** Um utilizador recebe uma **falha na instalação do perfil** erro num dispositivo Android.

**Resolução:**

1.  Confirme que foi atribuída ao utilizador uma licença adequada para a versão do serviço Intune que estiver a utilizar.

2.  Confirme se o dispositivo já está inscrito noutro fornecedor de MDM.

3. Confirme se o dispositivo tem um perfil de gestão instalado.

4.  Confirme que o Chrome para Android é o browser predefinido e que os cookies estão ativados.

### <a name="android-certificate-issues"></a>Problemas de certificados do Android

**Problema**: Os utilizadores recebem a mensagem seguinte no respetivo dispositivo: *Não consigo iniciar sessão porque o dispositivo está em falta um certificado necessário.*

**Resolução 1**:

O utilizador poderá conseguir obter o certificado em falta ao seguir as instruções em [O dispositivo tem um certificado necessário em falta](/intune-user-help/your-device-is-missing-a-required-certificate-android). Se o erro persistir, tente a Resolução 2.

**Resolução 2**:

Após introduzir as credenciais empresariais e ser redirecionado para o início de sessão federado, os utilizadores ainda poderão ver o erro de certificado em falta. Neste caso, o erro pode significar que um certificado intermédio está em falta no seu servidor de Serviços de Federação do Active Directory (AD FS)

O erro de certificado ocorre porque os dispositivos Android exigem que os certificados intermédios sejam incluídos num [hello do Servidor SSL](https://technet.microsoft.com/library/cc783349.aspx). Atualmente, um servidor predefinido do AD FS ou a instalação do servidor Proxy do AD FS envia apenas o certificado SSL de serviço do AD FS na resposta hello do servidor SSL ao hello do Cliente SSL.

Para corrigir o problema, importe os certificados para os Certificados dos Computadores Pessoais no servidor do AD FS ou nos proxies da seguinte forma:

1.  No ADFS e em servidores proxy, clique com o botão direito do rato em **Iniciar** > **Executar** > **certlm.msc** para iniciar a Consola de Gestão de Certificados de Computador Local.
2.  Expanda **Pessoal** e escolha **Certificados**.
3.  Localize o certificado para a comunicação de serviço do AD FS (um certificado assinado publicamente) e faça duplo clique para ver as respetivas propriedades.
4.  Escolha o separador **Caminho de Certificação** para ver os certificados principais do certificado.
5.  Em cada certificado principal, escolha **Ver Certificado**.
6.  Selecione **Detalhes** > **Copiar para o ficheiro…**.
7.  Siga as instruções do assistente para exportar ou guardar a chave pública do certificado principal numa localização do ficheiro à sua escolha.
8.  Clique com botão direito do rato em **Certificados** > **Todas as Tarefas** > **Importar**.
9.  Siga as instruções do assistente para importar os certificados principais para **Computador Local\Pessoal\Certificados**.
10. Reinicie os servidores do AD FS.
11. Repita os passos acima em todos os servidores do AD FS e do proxy.

Para verificar se a instalação do certificado foi feita corretamente, pode utilizar a ferramenta de diagnóstico disponível em [https://www.digicert.com/help/](https://www.digicert.com/help/). Na caixa **Endereço do Servidor**, introduza o FQDN do servidor do ADFS (IE: sts.contso.com) e clique em **Verificar Servidor**.

**Para validar que o certificado foi instalado corretamente**:

Os passos seguintes descrevem apenas um dos vários métodos e ferramentas que pode utilizar para validar que o certificado está instalado corretamente.

1. Aceda à [ferramenta gratuita Digicert](ttps://www.digicert.com/help/).
2. Introduza o nome de domínio completamente qualificado do servidor do AD FS (por exemplo, sts.contoso.com) e selecione **VERIFICAR SERVIDOR**.

Se o certificado de Servidor estiver corretamente instalado, verá todas as marcas de verificação nos resultados. Se existir o problema acima, vê um X vermelho nas secções do relatório "Correspondências de Nome de Certificado" e "Certificado SSL está corretamente instalado".


## <a name="ios-issues"></a>Problemas do iOS

### <a name="ios-enrollment-errors"></a>Erros de inscrição do iOS
A tabela seguinte indica os erros que os utilizadores finais poderão ver ao inscrever dispositivos iOS no Intune.

|Mensagem de erro|Problema|Resolução|
|-------------|-----|----------|
|NoEnrollmentPolicy|Nenhuma política de inscrição encontrada|Verifique se todos os pré-requisitos de inscrição, como o certificado do Serviço Apple Push Notification (APNs), foram configurados e se a opção "iOS como plataforma" está ativada. Para obter instruções, veja [Configurar a gestão de dispositivos iOS e Mac](ios-enroll.md).|
|DeviceCapReached|Já existem demasiados dispositivos móveis inscritos.|O utilizador tem de remover um dos respetivos dispositivos móveis atualmente inscritos do Portal da Empresa antes de inscrever outro. Consulte as instruções para o tipo de dispositivo que está a utilizar: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Existe um problema com o certificado que permite que o dispositivo móvel comunique com a rede da sua empresa.<br /><br />|O Serviço Apple Push Notification (APNs) disponibiliza um canal para entrar em contacto com os dispositivos iOS inscritos. A inscrição irá falhar e será apresentada esta mensagem se:<ul><li>Os passos para obter um certificado do APNs não foram concluídos ou</li><li>O certificado do APNs tiver expirado.</li></ul>Reveja as informações sobre como configurar utilizadores em [Sincronizar o Active Directory e adicionar utilizadores ao Intune](users-add.md) e em [Organizar utilizadores e dispositivos](groups-add.md).|
|AccountNotOnboarded|Existe um problema com o certificado que permite que o dispositivo móvel comunique com a rede da sua empresa.<br /><br />|O Serviço Apple Push Notification (APNs) disponibiliza um canal para entrar em contacto com os dispositivos iOS inscritos. A inscrição irá falhar e será apresentada esta mensagem se:<ul><li>Os passos para obter um certificado do APNs não foram concluídos ou</li><li>O certificado do APNs tiver expirado.</li></ul>Para obter mais informações, reveja [Configurar a gestão de iOS e Mac com o Microsoft Intune](ios-enroll.md).|
|DeviceTypeNotSupported|O utilizador poderá ter tentado inscrever-se através de um dispositivo não iOS. O tipo de dispositivo móvel que está a tentar inscrever não é suportado.<br /><br />Confirme que o dispositivo está a executar a versão 8.0 do iOS ou posterior.<br /><br />|Certifique-se de que o dispositivo do utilizador está a executar a versão 8.0 do iOS ou posterior.|
|UserLicenseTypeInvalid|O dispositivo não pode ser inscrito porque a sua conta de utilizador ainda não é um membro de um grupo de utilizadores necessário.<br /><br />|Para poderem inscrever os dispositivos, os utilizadores têm de ser membros do grupo de utilizadores correto. Esta mensagem indica que têm o tipo de licença errado para a autoridade de gestão de dispositivos móveis. Por exemplo, verão este erro se as seguintes situações se verificarem:<ol><li>O Intune foi definido como a autoridade de gestão de dispositivos móveis</li><li>Estão a utilizar uma licença do System Center 2012 R2 Configuration Manager.</li></ol>Reveja os seguintes artigos para obter mais informações:<br /><br />Veja [Configurar a gestão de iOS e Mac com o Microsoft Intune](ios-enroll.md) e as informações sobre como configurar utilizadores em [Sincronizar o Active Directory e adicionar utilizadores ao Intune](users-add.md) e [Organizar utilizadores e dispositivos](groups-add.md).|
|MdmAuthorityNotDefined|A autoridade de gestão de dispositivos móveis não foi definida.<br /><br />|A autoridade de gestão de dispositivos móveis não foi definida no Intune.<br /><br />Reveja #1 o primeiro item no "passo 6: Inscrever dispositivos móveis e instalar aplicações"secção [começar com uma avaliação de 30 dias do Microsoft Intune](free-trial-sign-up.md).|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>Os dispositivos estão inativos ou a consola de administração não consegue comunicar com os mesmos
**Problema:** os dispositivos iOS não estão a dar entrada no serviço do Intune. Os dispositivos têm de dar entrada no serviço periodicamente para manter o acesso aos recursos empresariais protegidos. Se os dispositivos não derem entrada:

- Não podem receber políticas, aplicações e comandos remotos a partir do serviço do Intune.
- Mostram o Estado de Gestão **Mau estado de funcionamento** na consola do administrador.
- Os utilizadores protegidos por políticas de acesso condicional podem perder o acesso a recursos empresariais.

**Resolução:** Partilhe as seguintes resoluções com os utilizadores finais para ajudá-los a recuperar o acesso aos recursos empresariais.

Quando os utilizadores iniciam a aplicação Portal da Empresa para iOS, esta saberá se o dispositivo tiver perdido o contacto com o Intune. Se a aplicação detetar que não existe contacto, tentará automaticamente sincronizar com o Intune para voltar a ligar-se (os utilizadores verão a notificação inline **A tentar sincronizar…** ).

  ![Notificação A tentar sincronizar](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Se a sincronização for efetuada com êxito, verá uma notificação inline a informar **Sincronização efetuada com êxito** na aplicação Portal da Empresa para iOS, o que indica que o seu dispositivo está em bom estado.

  ![Notificação Sincronização efetuada com êxito](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Se a sincronização não for efetuada com êxito, os utilizadores verão uma notificação inline a informar que **Não é possível sincronizar** na aplicação Portal da Empresa para iOS.

  ![Notificação Não é possível sincronizar](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

Para resolver o problema, os utilizadores têm de selecionar o botão **Configurar**, que se encontra à direita da notificação **Não é possível sincronizar**. O botão Configurar direciona os utilizadores para o ecrã do fluxo Configuração de Acesso à Empresa, onde podem seguir as instruções para inscrever o dispositivo.

  ![Ecrã Configuração de Acesso à Empresa](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

Após a inscrição, os dispositivos regressam a um bom estado e recuperam o acesso aos recursos da empresa.

### <a name="verify-ws-trust-13-is-enabled"></a>Confirmar se WS-Trust 1.3 está ativado
**Problema**: os dispositivos iOS do Programa de Registo de Aparelho (DEP) não podem ser inscritos

Inscrever dispositivos DEP com afinidade de utilizador requer a ativação de um ponto final de Nome de Utilizador/Misto WS-Trust 1.3 para pedir os tokens de utilizador. O Active Directory ativa este ponto final por predefinição. Para obter uma lista dos pontos finais ativados, utilize o cmdlet Get-AdfsEndpoint do PowerShell e procure o ponto final de confiança/13/Nome de Utilizador Misto. Por exemplo:

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Para obter mais informações, veja [a documentação do Get-AdfsEndpoint](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Para obter mais informações, veja o artigo [Práticas recomendadas para proteger os Serviços de Federação do Active Directory](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Para ajuda em determinar se o Nome de Utilizador/Misto WS-Trust 1.3 está ativado no seu fornecedor de federação de identidade:
- entre em contacto com Suporte da Microsoft se utilizar o AD FS
- contacte o fornecedor de identidade de terceiros.


### <a name="profile-installation-failed"></a>Falha na instalação do perfil
**Problema:** Um utilizador recebe uma **falha na instalação do perfil** erro num dispositivo iOS.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Passos de resolução de problemas para a falha na instalação do perfil

1.  Confirme que foi atribuída ao utilizador uma licença adequada para a versão do serviço Intune que estiver a utilizar.

2.  Confirme se o dispositivo já está inscrito noutro fornecedor de MDM.

3. Confirme se o dispositivo já tem um perfil de gestão instalado.

4.  Navegue para [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) e tente instalar o perfil quando lhe for pedido.

5.  Confirme que o Safari para iOS é o browser predefinido e que os cookies estão ativados.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Os dispositivos iOS inscritos não aparecem na consola ao utilizar o System Center Configuration Manager com o Intune
**Problema:** Utilizador inscreve o dispositivo iOS, mas não aparecer na consola de administração do Configuration Manager. O dispositivo não indica que foi inscrito. Causas possíveis:

- O Conector do Microsoft Intune no seu site do Configuration Manager não está a comunicar com o serviço do Intune.
- O componente Gestão de Dados de Deteção (ddm) ou o componente Gestor de Estado (statmgr) não está a processar as mensagens do serviço Intune.
- Pode ter transferido o certificado MDM a partir de uma conta e utilizado o certificado noutra conta.


**Resolução:** Reveja os seguintes ficheiros de registo para possíveis erros:

- dmpdownloader.log
- ddm.log
- statmgr.log

Em breve, serão adicionados alguns exemplos sobre o que deve procurar nestes ficheiros de registo.


### <a name="users-ios-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>O dispositivo iOS do utilizador está bloqueado num ecrã de inscrição há mais de 10 minutos

**Problema**: Um dispositivo de inscrição pode ficar bloqueado em qualquer um dos dois ecrãs:
- A aguardar uma configuração final da "Microsoft"
- Aplicação de Acesso Guiado indisponível. Contacte o administrador.

Este problema pode acontecer se:
- existir uma falha temporária nos serviços da Apple ou
- a inscrição de iOS estiver definida para utilizar tokens VPP conforme apresentado na tabela, mas ocorrer um problema com o token VPP.

| Definições de inscrição | Valor |
| ---- | ---- |
| Plataforma | iOS |
| Afinidade de Utilizador | Inscrever com a Afinidade de Utilizador |
|Autenticar com o Portal da Empresa em vez do Assistente de Configuração da Apple | Sim |
| Instalar o Portal da Empresa com VPP | Utilizar token: endereço do token |
| Executar o Portal da Empresa no Modo de Aplicação Única até à autenticação | Sim |

**Resolução**: Para corrigir o problema, tem de:
1. Determinar se existe um problema com o token VPP e corrigi-lo.
2. Identificar quais os dispositivos que estão bloqueados.
3. Apagar os dispositivos afetados.
4. Indicar ao utilizador que deve reiniciar o processo de inscrição.

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>Determinar se existe um problema com o token VPP
1. Aceda a **Intune** > **Inscrição de dispositivos** > **Inscrição Apple** > **Tokens de programa de inscrição** > nome do token > **Perfis** > nome do perfil > **Gerir** > **Propriedades**.
2. Reveja as propriedades para ver se são apresentados erros semelhantes aos seguintes:
    - Este token expirou.
    - Este token está sem licenças do Portal da Empresa.
    - Este token está a ser utilizado por outro serviço.
    - Este token está a ser utilizado por outro inquilino.
    - Este token foi eliminado.
3. Corrija os problemas do token.

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>Identificar quais os dispositivos que estão bloqueados pelo token de VPP
1. Aceda a **Intune** > **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > nome do token > **Dispositivos**.
2. Filtre a coluna **Estado do perfil** por **Bloqueado**.
3. Anote os números de série de todos os dispositivos que estão **Bloqueados**.

#### <a name="remotely-wipe-the-blocked-devices"></a>Apagar remotamente os dispositivos bloqueados
Depois de ter resolvido os problemas com o token VPP, tem de apagar os dispositivos que estão bloqueados.
1. Aceda a **Intune** > **Dispositivos** > **Todos os dispositivos** > **Colunas** > **Número de série** > **Aplicar**. 
2. Para cada dispositivo bloqueado, selecione-o na lista **Todos os dispositivos** e, em seguida, selecione **Apagar** > **Sim**.

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>Indique aos utilizadores que devem reiniciar o processo de inscrição
Depois de apagar os dispositivos bloqueados, pode indicar aos utilizadores que devem reiniciar o processo de inscrição.

## <a name="macos-issues"></a>Problemas do macOS

### <a name="macos-enrollment-errors"></a>Erros de inscrição do macOS
**Mensagem de erro 1:** *Parece que está a utilizar uma máquina virtual. Certifique-se de que configurou totalmente a sua máquina virtual, incluindo o número de série e o modelo de hardware. Se não se tratar de uma máquina virtual, contacte o suporte.*  

**Mensagem de erro 2:** *Estamos a ter problemas ao seu dispositivo gerido. Este problema pode ocorrer se estiver a utilizar uma máquina virtual, se tiver um número de série restrito ou se este dispositivo já estiver atribuído a outra pessoa. Saiba como resolver estes problemas ou contacte o suporte da sua empresa.*

**Problema:** Esta mensagem pode ser um resultado de qualquer um dos seguintes motivos:  
* Uma máquina virtual macOS (VM) não foi configurada corretamente  
* Ativou as restrições de dispositivos que necessitam que o dispositivo seja propriedade da empresa ou que tenha um número de série do dispositivo registado no Intune  
* O dispositivo já foi inscrito e continua atribuído a outra pessoa no Intune  

**Resolução:** Em primeiro lugar, contacte o seu utilizador para determinar qual dos problemas afeta o respetivo dispositivo. Em seguida, conclua a mais relevante das seguintes soluções:
* Se o utilizador estiver a inscrever uma VM para teste, certifique-se de que foi totalmente configurada para que o Intune possa reconhecer o respetivo número de série e modelo de hardware. Saiba mais sobre como [configurar VMs](macos-enroll.md#enroll-virtual-macos-machines-for-testing) no Intune.  
* Se a sua organização ativou as restrições de inscrição que bloqueiam dispositivos macOS pessoais, tem de [adicionar o número de série do dispositivo pessoal](corporate-identifiers-add.md#manually-enter-corporate-identifiers) manualmente ao Intune.  
* Se o dispositivo continuar atribuído a outro utilizador no Intune, o proprietário anterior não utilizou a aplicação Portal da Empresa para o remover ou repor. Para limpar o registo de dispositivo obsoleto do Intune:  

    1. Aceda ao [Intune no portal do Azure](https://portal.manage.microsoft.com) e inicie sessão com as suas credenciais administrativas.
    2. Aceda a Intune > **Dispositivos** > **Todos os dispositivos**.  
    3. Localize o dispositivo com o problema de inscrição. Procure pelo nome do dispositivo ou Endereço MAC/HW para restringir os seus resultados.
    4. Selecione o dispositivo > **Eliminar**. Elimine todas as outras entradas associadas ao dispositivo.  

## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Problemas quando utiliza o System Center Configuration Manager com o Intune
### <a name="mobile-devices-disappear"></a>Os dispositivos móveis desaparecem
**Problema:** Depois de inscrever com êxito um dispositivo móvel para o Configuration Manager, este desaparece da coleção de dispositivos móveis. No entanto, o dispositivo ainda tem o Perfil de Gestão e está listado no Gateway CSS.

**Resolução:** Este problema pode ocorrer porque:
- Tem um processo personalizado a remover dispositivos não associados ao domínio ou 
- o utilizador retirou o dispositivo da subscrição.
Para validar e verificar que processo ou conta de utilizador removeu o dispositivo da consola do Configuration Manager, execute os passos seguintes.

#### <a name="check-how-device-was-removed"></a>Verificar como o dispositivo foi removido

1.  Na consola de administração do Configuration Manager, selecione **Monitorização** &gt; **Estado do Sistema** &gt; **Consultas de Mensagens de Estado**.

2.  Clique com o botão direito do rato em **Recursos Membros da Coleção Eliminados Manualmente** e selecione **Mostrar Mensagens**.

3.  Escolha uma data/hora adequada ou as últimas 12 horas.

4.  Localize o dispositivo em questão e reveja a forma como foi removido. O exemplo abaixo mostra que a conta SCCMInstall eliminou o dispositivo através de uma Aplicação Desconhecida.

    ![Captura de ecrã do diagnóstico de eliminação do dispositivo](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Verifique se o Configuration Manager tem uma tarefa agendada, script ou outro processo que possa estar a remover automaticamente dispositivos não associados ao domínio, móveis ou relacionados.

### <a name="other-ios-enrollment-errors"></a>Outros erros de inscrição do iOS
É fornecida uma lista dos erros de inscrição de dispositivos iOS na nossa documentação, em [Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune) (Resolução de problemas de inscrição de dispositivos iOS no Microsoft Intune).

## <a name="pc-issues"></a>Problemas do PC

|Mensagem de erro|Problema|Resolução|
|---|---|---|
|**O administrador de TI tem de lhe atribuir uma licença para obter acesso**<br>O seu administrador de TI ainda não lhe deu acesso para utilizar esta aplicação. Obtenha ajuda do seu administrador de TI ou tente novamente mais tarde.|Não é possível inscrever o dispositivo porque a conta do utilizador não tem a licença necessária.|Antes de os utilizadores poderem inscrever os respetivos dispositivos, é preciso que lhes tenha sido atribuída a licença necessária. Esta mensagem indica que têm o tipo de licença errado para a autoridade de gestão de dispositivos móveis. Por exemplo, verão este erro se as seguintes situações se verificarem: <ol><li>O Intune foi definido como a autoridade de gestão de dispositivos móveis</li><li>Estão a utilizar uma licença do System Center 2012 R2 Configuration Manager.</li></ol>Saiba mais sobre como [atribuir licenças do Intune às contas de utilizador](https://docs.microsoft.com/intune/licenses-assign).|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>O computador já está inscrito - Erro hr 0x8007064c
**Problema:** A inscrição falha com o erro **o computador já está inscrito**. O registo de inscrição mostra o erro **hr 0x8007064c**.

Esta falha pode ocorrer porque o computador:
- foi anteriormente inscrito ou
- tem a imagem clonada de um computador que já tinha sido inscrito.
O certificado de conta da conta anterior ainda está presente no computador.

**Resolução:**

1. No menu **Início**, escreva **Executar** -> **MMC**.
1. Selecione **Ficheiro** > **Adicionar/Remover Snap-ins**.
1. Faça duplo clique em **Certificados**, selecione **Conta de computador** > **Seguinte** e selecione **Computador Local**.
1. Faça duplo clique em **Certificados (Computador local)** e selecione **Certificados Pessoais**.
1. Procure o certificado do Intune emitido por Sc_Online_Issuing e elimine-o, se estiver presente.
1. Se a seguinte chave de registo existir, elimine-o: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** e todas as sub-chaves.
1. Tente voltar a inscrever.
1. Se o PC ainda não é possível inscrever, procure e elimine esta chave, se existir: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Tente voltar a inscrever.

    > [!IMPORTANT]
    > Esta secção, método ou tarefa contém passos que indicam como modificar o registo. No entanto, poderão ocorrer problemas graves se modificar o registo incorretamente. Por isso, certifique-se de que segue estes passos cuidadosamente. Para maior proteção, faça uma cópia de segurança do registo antes de o modificar. Em seguida, pode restaurar o registo se ocorrer um problema.
    > Para obter mais informações sobre como criar cópias de segurança e restaurar o registo, leia o artigo [Como fazer cópias de segurança e restaurar o registo no Windows](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>Códigos de erros de inscrição gerais

|Código de erro|Possível problema|Resolução sugerida|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |O relógio no computador cliente não está definido com a hora correta.|Certifique-se de que o relógio e o fuso horário no computador cliente estão definidos com a hora e fuso horário corretos.|
|0x80240438, 0x80CF0438, 0x80CF402C|não é possível ligar ao serviço Intune. Verifique as definições de proxy do cliente.|Certifique-se de que o Intune suporta a configuração de proxy no computador cliente. Certifique-se de que o computador cliente tem acesso à Internet.|
|0x80240438, 0x80CF0438|As definições de proxy no Internet Explorer e no Sistema Local não estão configuradas.|não é possível ligar ao serviço Intune. Verifique as definições de proxy do cliente. Certifique-se de que o Intune suporta a configuração de proxy no computador cliente. Certifique-se de que o computador cliente tem acesso à Internet.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|O pacote de inscrição está desatualizado.|Transfira e instale o pacote de software de cliente atual a partir da área de trabalho Administração .|
|0x80043002, 0x80CF3002|A conta está em modo de manutenção.|Não pode inscrever novos computadores cliente quando a conta estiver em modo de manutenção. Para ver as definições da sua conta, inicie sessão na conta.|
|0x80043003, 0x80CF3003|A conta foi eliminada.|Verifique se a sua conta e subscrição do Intune ainda estão ativas. Para ver as definições da sua conta, inicie sessão na conta.|
|0x80043005, 0x80CF3005|O computador cliente foi extinguido.|Aguarde algumas horas, remova todas as antigas versões do software de cliente do computador e, em seguida, tente instalar o software de cliente novamente.|
|0x80043006, 0x80CF3006|O número máximo de estações permitidas para a conta foi atingido.|A sua organização tem de comprar licenças adicionais para que possa inscrever mais computadores cliente no serviço.|
|0x80043007, 0x80CF3007|Não foi possível localizar o ficheiro de certificado na mesma pasta que o programa do instalador.|Extraia todos os ficheiros antes de iniciar a instalação. Não mude o nome ou a localização de nenhum dos ficheiros extraídos: todos os ficheiros têm de estar na mesma pasta ou a instalação irá falhar.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|O software não pode ser instalado porque existe um reinício pendente do computador cliente.|Reinicie o computador e, em seguida, tente instalar o software de cliente novamente.|
|0x80070032|Um ou mais pré-requisitos para a instalação do software de cliente não foram encontrados no computador cliente.|Certifique-se de que todas as atualizações necessárias estão instaladas no computador cliente e, em seguida, tente instalar o software de cliente novamente.|
|0x80043008, 0x80CF3008|Falha ao iniciar o serviço Microsoft Online Management Update.|Contacte o Suporte da Microsoft, conforme descrito em [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](get-support.md).|
|0x80043009, 0x80CF3009|O computador cliente já está inscrito no serviço.|Tem de extinguir o computador cliente para o poder inscrever novamente no serviço.|
|0x8004300B, 0x80CF300B|Não é possível executar o pacote de instalação do software de cliente porque a versão do Windows que está a ser executada no cliente não é suportada.|O Intune não suporta a versão do Windows que está a ser executada no computador cliente.|
|0xAB2|O Windows Installer não conseguiu aceder ao tempo de execução de VBScript de uma ação personalizada.|Este erro é causado por uma ação personalizada baseada em DLLs (Dynamic-Link Libraries). Quando a DLL de resolução de problemas, poderá ter de utilizar as ferramentas descritas [KB198038 do suporte da Microsoft: Ferramentas úteis para problemas de implantação e pacote](https://support.microsoft.com/kb/198038).|
|0x80cf0440|A ligação ao ponto final do serviço foi terminada.|A conta de avaliação ou paga está suspensa. Crie uma nova conta de avaliação ou paga e volte a inscrever.|




### <a name="next-steps"></a>Passos Seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](get-support.md).
