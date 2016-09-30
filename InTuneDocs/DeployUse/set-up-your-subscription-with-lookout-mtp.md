---
title: "Configurar a sua subscrição com o Lookout MTP | Microsoft Intune"
description: "Este tópico fornece detalhes sobre como configurar o Lookout MTP."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2196ff03975df1f8969e1522f7af459343694d
ms.openlocfilehash: 530a34c7c75a4fa73cbb62873e2d28883b91b57e


---

# Configurar a sua subscrição do Lookout Mobile Threat Protection
Para preparar a sua subscrição de modo a integrar o serviço Lookout MTP, o suporte do Lookout (enterprisesupport@lookout.com) precisa das seguintes informações sobre a sua subscrição do Azure Active Directory (Azure AD). 

* **ID de Inquilino do Azure AD**
* **ID do Objeto de Grupo do Azure AD** para acesso **total** à consola do Lookout MTP
* **ID do Objeto de Grupo do Azure AD** para acesso **restrito** à consola do Lookout MTP (opcional)

Utilize a secção seguinte para reunir as informações que deve fornecer à equipa de suporte do Lookout.  

## Obter informações do Azure AD
### ID de inquilino do Azure AD
Inicie sessão no [portal de gestão do Azure AD](https://manage.windowsazure.com) e selecione a sua subscrição. 

![captura de ecrã da página do Azure AD que apresenta o nome do inquilino](../media/mtp/aad_tenant_name.png) Ao escolher o nome da sua subscrição, o URL resultante incluirá o ID de subscrição.  Se tiver dificuldades em localizar o seu ID de subscrição, consulte este [artigo do suporte da Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) para obter sugestões para saber o seu ID de subscrição.   
### Obter o ID de Grupo do Azure AD
A consola do Lookout MTP suporta 2 níveis de acesso:  
* **Acesso Total:** os administradores do Azure AD podem criar um grupo para utilizadores que terão Acesso Total e criar, opcionalmente, outro grupo para os utilizadores que terão Acesso Restrito.  Apenas os utilizadores incluídos nestes grupos poderão iniciar sessão na **Consola do Lookout MTP**.
* **Acesso Restrito:** os utilizadores neste grupo não têm acesso a vários módulos de configuração e inscrição da consola do Lookout MTP e têm acesso só de leitura ao módulo **Política de Segurança** da consola do Lookout MTP.  

Para obter mais detalhes sobre as permissões, consulte [este artigo](https://personal.support.lookout.com/hc/en-us/articles/114094105653) no site do Lookout.

O **ID de Objeto de Grupo** encontra-se na página **Propriedades** do grupo na **consola de gestão do Azure AD**.

![captura de ecrã da página de propriedades com o campo ID de Grupo destacado](../media/mtp/aad_group_object_id.png)

Quando tiver recolhido estas informações, contacte o suporte do Lookout (e-mail: enterprisesupport@lookout.com).

O Suporte do Lookout irá utilizar o seu contacto principal para integrar a sua subscrição e criar a sua conta do Lookout MTP Enterprise utilizando as informações que recolheu.


## Configurar a sua subscrição com o Lookout MTP
### Passo 1: configurar o MTP
Após o suporte do Lookout criar a sua conta do Lookout MTP Enterprise, pode iniciar sessão na consola do Lookout MTP.   Será enviado um e-mail do Lookout para o contacto principal da sua empresa com uma ligação para o URL de início de sessão: https://aad.lookout.com/les?action=consent

Tem de utilizar uma conta com a função de Administrador Global do Azure AD ao iniciar sessão na consola do Lookout MTP pela primeira vez. O Lookout MTP requer que efetue esta ação de modo a registar o inquilino do Azure AD.   Os inícios de sessão posteriores não requerem que o utilizador tenha este nível de privilégio do Azure AD.  Neste primeiro início de sessão, é apresentada uma página de consentimento. Selecione **Aceitar** para concluir o registo.

![captura de ecrã da página de primeiro início de sessão da consola do Lookout MTP](../media/mtp/lookout_mtp_initial_login.png) Ao aceitar e dar o seu consentimento, será redirecionado para a Consola do Lookout MTP. Os inícios de sessão posteriores após o registo inicial podem ser efetuados utilizando o URL:  https://aad.lookout.com

Consulte o [artigo de resolução de problemas](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration) caso se depare com problemas de início de sessão.

Os passos seguintes descrevem as tarefas que tem de realizar para concluir a configuração do Lookout MTP na [Consola do Lookout MTP](https://aad.lookout.com).

### Passo 2: configurar o conector do Intune

1.  Na consola do Lookout MTP, aceda ao módulo **Sistema**, selecione o separador **Conectores** e, em seguida, selecione **Intune**.

  ![captura de ecrã da consola do Lookout MTP com o separador Conectores aberto e a opção Intune destacada](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  Na opção Definições da Ligação, configure a frequência do heartbeat em minutos.  O seu conector do Intune está pronto.  

  ![captura de ecrã do separador Definições da Ligação com o campo de frequência do heartbeat configurado](../media/mtp/lookout-mtp-connection-settings.png)

### Passo 3: configurar grupos de inscrição
Na opção **Gestão de Inscrições**, defina um conjunto de utilizadores cujos dispositivos devem ser inscritos no Lookout. A melhor prática é começar por um grupo de utilizadores pequeno para testar e familiarizar-se com o processo de integração.  Quando estiver satisfeito com o resultado dos testes, pode alargar a inscrição a grupos de utilizadores adicionais.

Para começar a criar grupos de inscrição, primeiro defina um grupo de segurança do Azure AD com um conjunto inicial de utilizadores adequado para inscrever no Lookout MTP. Quando tiver criado o grupo no Azure AD, na Consola do Lookout MTP, aceda à opção **Gestão de Inscrições** e adicione o grupo de segurança do Azure AD a inscrever no campo **Nome(s) a Apresentar**.

Assim que um utilizador for adicionado a um grupo de inscrição, todos os seus dispositivos identificados e suportados no Azure AD serão inscritos e poderão ser ativados no Lookout MTP.  Quando um utilizador abrir pela primeira vez a aplicação Lookout for Work no seu dispositivo suportado, o dispositivo é ativado no Lookout MTP.
![captura de ecrã da página de inscrição do conector do Intune](../media/mtp/lookout-mtp-enrollment.png)

A melhor prática é utilizar a predefinição (5 minutos) para o intervalo de tempo para verificar novos dispositivos.

>[!IMPORTANT]
> O nome a apresentar é sensível a maiúsculas e minúsculas.  Utilize o **Nome a Apresentar** conforme apresentado na página **Propriedades** do grupo de segurança do portal do Azure. Repare que na imagem abaixo da página **Propriedades** do grupo de segurança, o Nome a Apresentar encontra-se em maiúsculas e minúsculas.  No entanto, o título encontra-se apenas em minúsculas e não deve ser introduzido desta forma na consola do Lookout MTP.
>![captura de ecrã do portal do Azure, serviço Azure Active Directory, página de propriedades](../media/mtp/aad-group-display-name.png)

A versão atual apresenta as seguintes limitações:  
* Não existe uma forma de validação para os nomes a apresentar de um grupo.  Certifique-se de que utiliza o texto que introduziu no campo **NOME A APRESENTAR** apresentado no portal do Azure no grupo de segurança do Azure AD.
* A criação de grupos dentro de outros grupos não é atualmente suportada.  Os grupos de segurança do Azure AD especificados podem conter apenas utilizadores e não grupos aninhados.


### Passo 4: configurar a sincronização do estado
Na opção **Sincronização do Estado**, especifique o tipo de dados que devem ser enviados para o Intune.  Atualmente, tem de ativar o estado do dispositivo e o estado da ameaça para que a integração do Intune no Lookout possa funcionar corretamente.  Ambos os estados já se encontram ativados por predefinição.
### Passo 5: configurar as informações dos destinatários de e-mails de relatórios de erros
Na opção **Gestão de Erros**, introduza o endereço de e-mail que deve receber os relatórios de erros.

![Captura de ecrã da página de gestão de erros do conector do Intune](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Passo 6: configurar as notificações por e-mail
Se pretender receber alertas por e-mail relativos a ameaças, inicie sessão na [consola do Lookout MTP](https://aad.lookout.com) com a conta de utilizador que deve receber as notificações. No separador **Preferências** do módulo **Sistema**, selecione as notificações pretendidas e defina as mesmas como **ATIVADO**. Guarde as suas alterações.

![Captura de ecrã da página de preferências a apresentar a conta de utilizador](../media/mtp/lookout-mtp-email-notifications.png) Se pretende deixar de receber notificações por e-mail, defina as mesmas como **DESATIVADO** e guarde as suas alterações.
### Passo 7: configurar a classificação de ameaças
O Lookout MTP classifica ameaças a dispositivos móveis de vários tipos. As [classificações de ameaças do Lookout MTP](http://personal.support.lookout.com/hc/en-us/articles/114094130693) apresentam níveis de risco predefinidos inerentes às mesmas. Estas classificações podem ser alteradas a qualquer momento de forma a ajustá-las aos requisitos da sua empresa.

![captura de ecrã da página de políticas a apresentar ameaças e as respetivas classificações](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Os níveis de risco aqui especificados são um aspeto importante do MTP, uma vez que a integração do Intune calcula a conformidade dos dispositivos de acordo com estes níveis de risco durante a sua execução. Por outras palavras, o administrador do Intune define uma regra na sua política para identificar se um dispositivo não está conforme, caso o mesmo apresente uma ameaça ativa com um nível mínimo de risco alto, médio ou baixo. A política de classificação de ameaças no MTP ativa diretamente o cálculo da conformidade do dispositivo no Intune.

## Monitorizar as inscrições
Quando a configuração estiver concluída, o Lookout MTP inicia uma consulta no Azure AD para detetar dispositivos que correspondam aos grupos de inscrição especificados.  Poderá encontrar informações sobre os dispositivos inscritos no módulo Dispositivos.  O estado inicial dos dispositivos é apresentado como Pendente.  O estado dos dispositivos é alterado assim que a aplicação Lookout for Work for instalada, aberta e ativada nos mesmos.  Para obter detalhes sobre como instalar a aplicação Lookout for Work no dispositivo pretendido, consulte o tópico [Configurar e implementar as aplicações Lookout for Work](configure-and-deploy-lookout-for-work-apps.md).
## Passos seguintes
[Ativar a ligação do Lookout MTP ao Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Sep16_HO3-->


