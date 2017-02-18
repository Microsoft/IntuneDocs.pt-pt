---
title: "Configurar a sua subscrição para o Lookout | Documentos da Microsoft"
description: "Este tópico fornece detalhes sobre como configurar a proteção contra ameaças de dispositivos do Lookout."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 53862e49c922b75b414fd5aceec3bba2b10299a6
ms.openlocfilehash: a61cbc076167dfaffeb1af82d78654f2bb7f7721


---

# <a name="set-up-your-subscription-for-lookout-device-threat-protection"></a>Configurar a sua subscrição para a proteção contra ameaças de dispositivos do Lookout

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Os seguintes passos são necessários para configurar a proteção contra ameaças de dispositivos do Lookout:

| #        |Passo  |
| ------------- |:-------------|
| 1 | [Recolher informações do Azure AD](#collect-azure-ad-information) |
| 2 | [Configurar a sua subscrição](#configure-your-subscription) |
| 3 | [Configurar grupos de inscrição](#configure-enrollment-groups) |
| 4 | [Configurar a sincronização do estado](#configure-state-sync) |
| 5 | [Configurar as informações dos destinatários de e-mails de relatórios de erros](#configure-error-report-email-recipient-information) |
| 6 | [Configurar definições de inscrição](#configure-enrollment-settings) |
| 7 | [Configurar notificações de e-mail](#configure-email-notifications) |
| 8 | [Configurar a classificação de ameaças](#configure-threat-classification) |
| 1 | [Monitorizar as inscrições](#watching-enrollment) |


> [!IMPORTANT]
> Um inquilino do Lookout Mobile Endpoint Security que ainda não esteja associado ao seu inquilino do Azure AD não pode ser utilizado na integração com o Azure AD e o Intune. Contacte o suporte do Lookout para criar um novo inquilino do Lookout Mobile Endpoint Security. Utilize o novo inquilino para integrar os seus utilizadores do Azure AD.

## <a name="collect-azure-ad-information"></a>Recolher informações do Azure AD
O seu inquilino do Lookout Mobile Endpoint Security será associado à sua subscrição do Azure AD para integrar o Lookout com o Intune. Para ativar a subscrição do serviço de proteção contra ameaças do Lookout, o suporte do Lookout (enterprisesupport@lookout.com) precisa das seguintes informações:  

* **ID de Inquilino do Azure AD**
* **ID de Objeto de Grupo do Azure AD** para acesso **total** à consola do Lookout
* **ID de Objeto de Grupo do Azure AD** acesso **restrito** à consola do Lookout (opcional)

Utilize os seguintes passos para reunir as informações que deve fornecer à equipa de suporte do Lookout.

1. Inicie sessão no [portal de gestão do Azure AD](https://manage.windowsazure.com) e selecione a sua subscrição. 
  ![captura de ecrã da página do Azure AD a mostrar o nome do inquilino](../media/mtp/aad_tenant_name.png)
2. Quando selecionar o nome da sua subscrição, o URL resultante irá incluir o ID de subscrição.  Se tiver dificuldades em localizar o seu ID de subscrição, consulte este [artigo do suporte da Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) para obter sugestões para saber o seu ID de subscrição. 
3. Localize o ID de Grupo do Azure AD. A consola do Lookout suporta 2 níveis de acesso:  
  * **Acesso Total:** os administradores do Azure AD podem criar um grupo para utilizadores que terão Acesso Total e criar, opcionalmente, outro grupo para os utilizadores que terão Acesso Restrito.  Apenas os utilizadores nestes grupos poderão iniciar sessão na **consola do Lookout**.
  * **Acesso Restrito:** os utilizadores neste grupo não têm acesso a vários módulos de configuração e inscrição da consola do Lookout e têm acesso só de leitura ao módulo **Política de Segurança** da consola do Lookout.  

  Para obter mais detalhes sobre as permissões, consulte [este artigo](https://personal.support.lookout.com/hc/en-us/articles/114094105653) no site do Lookout.

  O **ID de Objeto de Grupo** encontra-se na página **Propriedades** do grupo na **consola de gestão do Azure AD**.

  ![captura de ecrã da página de propriedades com o campo ID de Grupo destacado](../media/mtp/aad_group_object_id.png)

4. Quando tiver recolhido estas informações, contacte o suporte do Lookout (e-mail: enterprisesupport@lookout.com). O Suporte do Lookout irá utilizar o seu contacto principal para integrar a sua subscrição e criar a sua conta do Lookout Enterprise com as informações que recolheu.

## <a name="configure-your-subscription"></a>Configurar a sua subscrição
1. Após o suporte do Lookout criar a sua conta do Lookout Enterprise, será enviado um e-mail do Lookout para o contacto principal da sua empresa, com uma ligação para o URL de início de sessão: https://aad.lookout.com/les?action=consent.

2.  O primeiro início de sessão na consola do Lookout tem de ser efetuado por uma conta de utilizador com a função de Administrador Global do Azure AD para registar o seu inquilino do Azure AD. Posteriormente, não será necessário este nível de privilégio do Azure AD para iniciar sessão. É apresentada uma página de consentimento. Selecione **Aceitar** para concluir o registo.

  ![captura de ecrã da página do primeiro início de sessão na consola do Lookout](../media/mtp/lookout_mtp_initial_login.png) Ao aceitar e dar o seu consentimento, será redirecionado para a Consola do Lookout.

  Consulte a [resolução de problemas de integração do Lookout](https://docs.microsoft.com/intune/troubleshoot/troubleshooting-lookout-integration) para obter ajuda com problemas de início de sessão.

3.  Na [Consola do Lookout](https://aad.lookout.com), no módulo **Sistema**, selecione o separador **Conectores** e selecione **Intune**.

  ![captura de ecrã da consola do Lookout com o separador Conectores aberto e a opção Intune destacada](../media/mtp/lookout_mtp_setup-intune-connector.png)

4.  Aceda a **Conectores** > **Definições de Ligação** e especifique a **Frequência do Heartbeat**.

  ![captura de ecrã do separador Definições da Ligação com o campo de frequência do heartbeat configurado](../media/mtp/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Configurar grupos de inscrição
1. Como boa prática, crie um grupo de segurança do Azure AD no [portal de gestão do Azure AD](https://manage.windowsazure.com) com um número reduzido de utilizadores para testar a integração do Lookout.

  Todos os dispositivos de utilizadores suportados pelo Lookout e inscritos no Intune num grupo de inscrição no Azure AD que estão identificados e suportados serão inscritos e poderão ser ativados na proteção contra ameaças de dispositivos do Lookout.

2. Na [Consola do Lookout](https://aad.lookout.com), a partir do módulo **Sistema**, selecione o separador **Conectores** e selecione **Gestão de Inscrições** para definir um conjunto de utilizadores cujos dispositivos devam ser inscritos com o Lookout. Adicione o grupo de segurança do Azure AD **Nome a Apresentar** para inscrição.

  ![captura de ecrã da página de inscrição do conector do Intune](../media/mtp/lookout-mtp-enrollment.png)

  >[!IMPORTANT]
  > O **Nome a Apresentar** é sensível a maiúsculas e minúsculas, conforme apresentado nas **Propriedades** do grupo de segurança no portal do Azure. Conforme apresentado na página abaixo, o **Nome a Apresentar** do grupo de segurança tem todas as palavras a começar por maiúscula; por sua vez, o título é todo em minúsculas. Na consola do Lookout, faça corresponder as maiúsculas do **Nome a Apresentar** para o grupo de segurança.
  >![captura de ecrã do portal do Azure, serviço Azure Active Directory, página de propriedades](../media/mtp/aad-group-display-name.png)

  A melhor prática é utilizar a predefinição (5 minutos) para o intervalo de tempo para verificar novos dispositivos.

  **Limitações atuais:**
  * O Lookout não consegue validar nomes a apresentar de grupos.  Certifique-se de que o campo **NOME A APRESENTAR** no portal do Azure corresponde exatamente ao grupo de segurança do Azure AD.
  * A criação de grupos aninhados não é suportada.  Os grupos de segurança do Azure AD utilizados no Lookout têm de conter apenas utilizadores. Não podem conter outros grupos.

3.  Após um grupo ser adicionado, quando um utilizador voltar a abrir a aplicação Lookout for Work no seu dispositivo suportado, o dispositivo será ativado no Lookout.

4.  Quando estiver satisfeito com os resultados, alargue a inscrição a grupos de utilizadores adicionais.

## <a name="configure-state-sync"></a>Configurar a sincronização do estado
Na opção **Sincronização do Estado**, especifique o tipo de dados que devem ser enviados para o Intune.  O estado do dispositivo e o estado da ameaça são necessários para que a integração do Intune no Lookout possa funcionar corretamente.  Ambos os estados já se encontram ativados por predefinição.

## <a name="configure-error-report-email-recipient-information"></a>Configurar as informações dos destinatários de e-mails de relatórios de erros
Na opção **Gestão de Erros**, introduza o endereço de e-mail que deve receber os relatórios de erros.

![Captura de ecrã da página de gestão de erros do conector do Intune](../media/mtp/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>configurar definições de inscrição
No módulo **System**, na página **Connectors**, especifique o número de dias decorridos antes de um dispositivo ser considerado como estando desligado.  Considera-se que os dispositivos desligados não se encontram em conformidade e o acesso à aplicações da empresa a partir dos mesmos será bloqueado com base nas políticas de acesso condicional do Intune. Pode especificar valores entre 1 e 90 dias.

![](../media/mtp/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Configurar notificações de e-mail
Se quiser receber alertas de e-mail de ameaças, inicie sessão na [consola do Lookout](https://aad.lookout.com) com a conta de utilizador que deverá receber notificações. No separador **Preferências** do módulo **Sistema**, selecione os níveis de ameaças que devem acionar notificações e defina-os como **ATIVADO**. Guarde as suas alterações.

![captura de ecrã da página de preferências a apresentar a conta de utilizador](../media/mtp/lookout-mtp-email-notifications.png) Se pretende deixar de receber notificações por e-mail, defina as mesmas como **DESATIVADO** e guarde as suas alterações.

### <a name="configure-threat-classification"></a>Configurar a classificação de ameaças
A proteção contra ameaças de dispositivos do Lookout classifica ameaças contra dispositivos móveis de vários tipos. As [classificações de ameaças do Lookout](http://personal.support.lookout.com/hc/en-us/articles/114094130693) apresentam níveis de risco predefinidos inerentes às mesmas. Estas classificações podem ser alteradas a qualquer momento de forma a ajustá-las aos requisitos da sua empresa.

![captura de ecrã da página de políticas a apresentar ameaças e as respetivas classificações](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Os níveis de risco são um aspeto importante da proteção contra ameaças de dispositivos, uma vez que a integração do Intune calcula a conformidade dos dispositivos de acordo com estes níveis de risco durante a sua execução. O administrador do Intune define uma regra na política para identificar se um dispositivo não está conforme, caso o mesmo apresente uma ameaça ativa com um nível mínimo de risco **Alto**, **Médio** ou **Baixo**. A política de classificação de ameaças na proteção contra ameaças de dispositivos do Lookout afeta diretamente o cálculo da conformidade do dispositivo no Intune.

## <a name="watching-enrollment"></a>Monitorizar as inscrições
Quando a configuração estiver concluída, a proteção contra ameaças de dispositivos do Lookout inicia uma consulta no Azure AD para detetar dispositivos que correspondam aos grupos de inscrição especificados.  Poderá encontrar informações sobre os dispositivos inscritos no módulo Dispositivos.  O estado inicial dos dispositivos é apresentado como Pendente.  O estado dos dispositivos é alterado assim que a aplicação Lookout for Work for instalada, aberta e ativada nos mesmos.  Para obter detalhes sobre como instalar a aplicação Lookout for Work no dispositivo pretendido, consulte o tópico [Configurar e implementar as aplicações Lookout for Work](configure-and-deploy-lookout-for-work-apps.md).
## <a name="next-steps"></a>Passos seguintes
[Ativar a ligação do Lookout MTP ao Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Jan17_HO2-->

