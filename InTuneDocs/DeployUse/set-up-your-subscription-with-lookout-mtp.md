---
title: "Configurar a sua subscrição para o Lookout | Microsoft Intune"
description: "Este tópico fornece detalhes sobre como configurar a proteção contra ameaças de dispositivos do Lookout."
keywords: 
author: karthikaraman
ms.author: karaman
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
ms.sourcegitcommit: de65f43ac83b25fa2dd1dacd2a7807668c2b6e9a
ms.openlocfilehash: fa3230e1faf24bdbbd7e84a211ca95c1fd0fadfd


---

# Configurar a sua subscrição para a proteção contra ameaças de dispositivos do Lookout
Para preparar a sua subscrição para integrar o serviço de proteção contra ameaças de dispositivos do Lookout, o suporte do Lookout (enterprisesupport@lookout.com) irá precisar das seguintes informações sobre a sua subscrição do Azure Active Directory (Azure AD). 

* **ID de Inquilino do Azure AD**
* **ID de Objeto de Grupo do Azure AD** para acesso **total** à consola do Lookout
* **ID de Objeto de Grupo do Azure AD** acesso **restrito** à consola do Lookout (opcional)

Utilize a secção seguinte para reunir as informações que deve fornecer à equipa de suporte do Lookout.  

## Obter informações do Azure AD
### ID de inquilino do Azure AD
Inicie sessão no [portal de gestão do Azure AD](https://manage.windowsazure.com) e selecione a sua subscrição. 

![captura de ecrã da página do Azure AD que apresenta o nome do inquilino](../media/mtp/aad_tenant_name.png) Ao escolher o nome da sua subscrição, o URL resultante incluirá o ID de subscrição.  Se tiver dificuldades em localizar o seu ID de subscrição, consulte este [artigo do suporte da Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) para obter sugestões para saber o seu ID de subscrição.   
### ID de Grupo do Azure AD
A consola do Lookout suporta 2 níveis de acesso:  
* **Acesso Total:** os administradores do Azure AD podem criar um grupo para utilizadores que terão Acesso Total e criar, opcionalmente, outro grupo para os utilizadores que terão Acesso Restrito.  Apenas os utilizadores nestes grupos poderão iniciar sessão na **consola do Lookout**.
* **Acesso Restrito:** os utilizadores neste grupo não têm acesso a vários módulos de configuração e inscrição da consola do Lookout e têm acesso só de leitura ao módulo **Política de Segurança** da consola do Lookout.  

Para obter mais detalhes sobre as permissões, consulte [este artigo](https://personal.support.lookout.com/hc/en-us/articles/114094105653) no site do Lookout.

O **ID de Objeto de Grupo** encontra-se na página **Propriedades** do grupo na **consola de gestão do Azure AD**.

![captura de ecrã da página de propriedades com o campo ID de Grupo destacado](../media/mtp/aad_group_object_id.png)

Quando tiver recolhido estas informações, contacte o suporte do Lookout (e-mail: enterprisesupport@lookout.com).

O Suporte do Lookout irá utilizar o seu contacto principal para integrar a sua subscrição e criar a sua conta do Lookout Enterprise com as informações que recolheu.


## Configurar a sua subscrição para a proteção contra ameaças de dispositivos do Lookout
### Passo 1: configurar a proteção contra ameaças de dispositivos
Após o suporte do Lookout criar a sua conta do Lookout Enterprise, pode iniciar sessão na consola do Lookout.   Será enviado um e-mail do Lookout para o contacto principal da sua empresa com uma ligação para o URL de início de sessão: https://aad.lookout.com/les?action=consent

Tem de utilizar uma conta de utilizador com a função de Administrador Global do Azure AD ao iniciar sessão pela primeira vez na consola do Lookout, uma vez que o Lookout precisa destas informações para registar o seu inquilino do Azure AD.   Os inícios de sessão posteriores não requerem que o utilizador tenha este nível de privilégio do Azure AD.  Neste primeiro início de sessão, é apresentada uma página de consentimento. Selecione **Aceitar** para concluir o registo.

![captura de ecrã da página do primeiro início de sessão na consola do Lookout](../media/mtp/lookout_mtp_initial_login.png) Ao aceitar e dar o seu consentimento, será redirecionado para a Consola do Lookout. Os inícios de sessão posteriores após o registo inicial podem ser efetuados utilizando o URL:  https://aad.lookout.com

Consulte o [artigo de resolução de problemas](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration) caso se depare com problemas de início de sessão.

Os passos seguintes descrevem as tarefas que tem de realizar para concluir a configuração do Lookout na [Consola do Lookout](https://aad.lookout.com).

### Passo 2: configurar o conector do Intune

1.  Na consola do Lookout, a partir do módulo **System**, selecione o separador **Connectors**, e selecione **Intune**.

  ![captura de ecrã da consola do Lookout com o separador Conectores aberto e a opção Intune destacada](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  Na opção Definições da Ligação, configure a frequência do heartbeat em minutos.  O seu conector do Intune está pronto.  

  ![captura de ecrã do separador Definições da Ligação com o campo de frequência do heartbeat configurado](../media/mtp/lookout-mtp-connection-settings.png)

### Passo 3: configurar grupos de inscrição
Na opção **Gestão de Inscrições**, defina um conjunto de utilizadores cujos dispositivos devem ser inscritos no Lookout. A melhor prática é começar por um grupo de utilizadores pequeno para testar e familiarizar-se com o processo de integração.  Quando estiver satisfeito com o resultado dos testes, pode alargar a inscrição a grupos de utilizadores adicionais.

Para começar a criar grupos de inscrição, primeiro defina um grupo de segurança do Azure AD com um conjunto inicial de utilizadores adequado para a inscrição na proteção contra ameaças de dispositivos do Lookout. Quando tiver criado o grupo no Azure AD, na Consola do Lookout, aceda à opção **Gestão de Inscrições** e adicione o grupo de segurança do Azure AD a inscrever no campo **Nome(s) a Apresentar**.

Assim que um utilizador for adicionado a um grupo de inscrição, todos os seus dispositivos identificados e suportados no Azure AD serão inscritos e poderão ser ativados na proteção contra ameaças de dispositivos do Lookout.  Quando um utilizador abrir pela primeira vez a aplicação Lookout for Work no seu dispositivo suportado, o dispositivo é ativado no Lookout.

![captura de ecrã da página de inscrição do conector do Intune](../media/mtp/lookout-mtp-enrollment.png)

A melhor prática é utilizar a predefinição (5 minutos) para o intervalo de tempo para verificar novos dispositivos.

>[!IMPORTANT]
> O nome a apresentar é sensível a maiúsculas e minúsculas.  Utilize o **Nome a Apresentar** conforme apresentado na página **Propriedades** do grupo de segurança do portal do Azure. Repare que na imagem abaixo da página **Propriedades** do grupo de segurança, o Nome a Apresentar encontra-se em maiúsculas e minúsculas.  No entanto, o título é apresentado em minúsculas e não deve ser introduzido desta forma na consola do Lookout.
>![captura de ecrã do portal do Azure, serviço Azure Active Directory, página de propriedades](../media/mtp/aad-group-display-name.png)

A versão atual apresenta as seguintes limitações:  
* Não existe uma forma de validação para os nomes a apresentar de um grupo.  Certifique-se de que utiliza o texto que introduziu no campo **NOME A APRESENTAR** apresentado no portal do Azure no grupo de segurança do Azure AD.
* A criação de grupos dentro de outros grupos não é atualmente suportada.  Os grupos de segurança do Azure AD especificados podem conter apenas utilizadores e não grupos aninhados.


### Passo 4: configurar a sincronização do estado
Na opção **Sincronização do Estado**, especifique o tipo de dados que devem ser enviados para o Intune.  Atualmente, tem de ativar o estado do dispositivo e o estado da ameaça para que a integração do Intune no Lookout possa funcionar corretamente.  Ambos os estados já se encontram ativados por predefinição.
### Passo 5: configurar as informações dos destinatários de e-mails de relatórios de erros
Na opção **Gestão de Erros**, introduza o endereço de e-mail que deve receber os relatórios de erros.

![Captura de ecrã da página de gestão de erros do conector do Intune](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Passo 6: configurar definições de inscrição
No módulo **System**, na página **Connectors**, especifique o número de dias decorridos antes de um dispositivo ser considerado como estando desligado.  Considera-se que os dispositivos desligados não se encontram em conformidade e o acesso à aplicações da empresa a partir dos mesmos será bloqueado com base nas políticas de acesso condicional do Intune. Pode especificar valores entre 1 e 90 dias.

![](../media/mtp/lookout-console-enrollment-settings.png)

### Passo 7: configurar notificações de e-mail
Caso pretenda receber alertas de e-mail de ameaças, inicie sessão na [consola do Lookout](https://aad.lookout.com) com a conta de utilizador que deverá receber as notificações. No separador **Preferências** do módulo **Sistema**, selecione as notificações pretendidas e defina as mesmas como **ATIVADO**. Guarde as suas alterações.

![Captura de ecrã da página de preferências a apresentar a conta de utilizador](../media/mtp/lookout-mtp-email-notifications.png) Se pretende deixar de receber notificações por e-mail, defina as mesmas como **DESATIVADO** e guarde as suas alterações.
### Passo 8: configurar a classificação de ameaças
A proteção contra ameaças de dispositivos do Lookout classifica ameaças contra dispositivos móveis de vários tipos. As [classificações de ameaças do Lookout](http://personal.support.lookout.com/hc/en-us/articles/114094130693) apresentam níveis de risco predefinidos inerentes às mesmas. Estas classificações podem ser alteradas a qualquer momento de forma a ajustá-las aos requisitos da sua empresa.

![captura de ecrã da página de políticas a apresentar ameaças e as respetivas classificações](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Os níveis de risco aqui especificados são um aspeto importante da proteção contra ameaças de dispositivos, uma vez que a integração do Intune calcula a conformidade dos dispositivos de acordo com estes níveis de risco durante a sua execução. Por outras palavras, o administrador do Intune define uma regra na sua política para identificar se um dispositivo não está conforme, caso o mesmo apresente uma ameaça ativa com um nível mínimo de risco alto, médio ou baixo. A política de classificação de ameaças na proteção contra ameaças de dispositivos do Lookout afeta diretamente o cálculo da conformidade do dispositivo no Intune.

## Monitorizar as inscrições
Quando a configuração estiver concluída, a proteção contra ameaças de dispositivos do Lookout inicia uma consulta no Azure AD para detetar dispositivos que correspondam aos grupos de inscrição especificados.  Poderá encontrar informações sobre os dispositivos inscritos no módulo Dispositivos.  O estado inicial dos dispositivos é apresentado como Pendente.  O estado dos dispositivos é alterado assim que a aplicação Lookout for Work for instalada, aberta e ativada nos mesmos.  Para obter detalhes sobre como instalar a aplicação Lookout for Work no dispositivo pretendido, consulte o tópico [Configurar e implementar as aplicações Lookout for Work](configure-and-deploy-lookout-for-work-apps.md).
## Passos seguintes
[Ativar a ligação do Lookout MTP ao Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Oct16_HO2-->


