---
# required metadata

title: Novidades | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novidades do Microsoft Intune

## Abril de 2016
Todas estas funcionalidades também são suportadas em clientes híbridos (Configuration Manager com o Intune).
### Gestão de aplicações
- **Conformidade de utilizadores MAM.**
Agora, pode ver o [estado](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) das suas políticas de gestão de aplicações para qualquer utilizador no inquilino do Azure Active Directory (AAD). Isto inclui:
   - Dispositivos
   - Aplicações no dispositivo

   Valores de estado:

   **Com entrada dada**: indica que a política foi implementada para o utilizador, e a aplicação foi utilizada no contexto profissional, e recebeu com êxito a política.

    **Sem entrada dada:** indica que a política foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto profissional desde então.


- **Controlos de MAM para impedir a sincronização de contactos do Outlook (Android).**
Uma nova definição está disponível para a [gestão de aplicações móveis](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sem inscrição de dispositivos. Esta definição permite impedir que uma aplicação sincronize contactos com o livro de endereços nativo em dispositivos Android. Quando esta definição estiver ativada, as aplicações visadas já não poderão guardar contactos no livro de endereços nativo. Quando esta definição estiver desativada, as aplicações visadas poderão guardar contactos no livro de endereços nativo. Quando [elimina remotamente os dados de um dispositivo ou aplicação](wipe-managed-company-app-data-with-Microsoft-Intune.md), os contactos que já tenham sido guardados no livro de endereços nativo serão removidos. Esta nova definição é suportada inicialmente pela aplicação Outlook em dispositivos Android.

### Gestão de dispositivos
- **Identificação de números de telefone para dispositivos pertencentes à empresa.** Os telefones que são classificados como "Empresa" estão agora identificados com o respetivo número de telefone completo quando, por exemplo, executa um relatório de inventário de dispositivos móveis. Os números de telefone BYOD continuam a ser mascarados com ****, com apenas os 4 últimos dígitos apresentados.


### Atualizações ao portal da empresa
Aplicação Portal da Empresa para Android Os utilizadores que não inscreveram o seu dispositivo no Intune e que não tenham o certificado correto instalado não poderão iniciar sessão na aplicação Portal da Empresa para Android e verão a mensagem “You cannot sign in because your device is missing a required certificate.” A mensagem inclui uma ligação "How to resolve this" na qual os utilizadores podem tocar para ver instruções para instalar o certificado.

Para ver os passos que os utilizadores finais têm de seguir para resolver o problema, consulte [O dispositivo tem um certificado necessário em falta](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing) Aplicação Portal da Empresa para iOS

Foi adicionado suporte para a ação «puxe para atualizar» para atualizar o conteúdo do ecrã principal, que inclui as aplicações listadas, os dispositivos listados e informações contacto de TI. A ação «puxe para atualizar» não verifica se existem informações de conformidade ou de política, o que pode ser efetuado selecionando o mosaico relativo ao seu dispositivo atual e tocando no botão **Sincronizar**. Aplicação Portal da Empresa para Windows 10 Mobile e Windows Phone 8.1

Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência de instalação de aplicações melhorada.

* Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para consultar as instruções do utilizador final, consulte [Sincronizar o dispositivo manualmente para acelerar a instalação de aplicações](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually) Web site do Portal da Empresa
* Quando os utilizadores do Windows 10 Mobile e Windows Phone 8.1 estiverem a instalar aplicações de linha de negócio, irão ver agora os seguintes estados novos, que fornecem mais detalhes sobre o estado da instalação:

**A aguardar sincronização do dispositivo** – o utilizador tocou em "Instalar" e o dispositivo tenta agora sincronizar com a infraestrutura do Intune. A sincronização é necessária para que a instalação possa ser concluída.

### A mensagem "A aguardar sincronização do dispositivo" é também uma ligação na qual os utilizadores podem tocar para ver [instruções](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre como sincronizar manualmente o dispositivo com o Intune se o processo de sincronização estiver a demorar muito tempo ou ficar parado.

****A transferir** – o pedido de transferência do utilizador está a ser processado e o dispositivo está a transferir e a instalar a aplicação.** Antes de estes estados terem sido adicionados, os utilizadores ficavam confusos se a instalação de uma aplicação demorava muito tempo, porque viam apenas um estado "A instalar", o qual podia permanecer no ecrã durante horas. Adicionar os novos estados significa que, em vez de contactar o suporte, os utilizadores podem agora tocar na ligação "A aguardar sincronização do dispositivo" e seguir as instruções para forçar a continuação do processo de sincronização. Novidades futuras  Alterações às contas de Gestores de Inscrição de Dispositivos. Para melhorar o desempenho e o dimensionamento, o Intune irá deixar de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação Portal da Empresa.  Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa.

O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.


## Além disso, o Intune irá preterir a utilização de contas DEM com o Programa de Inscrição de Dispositivos Apple ou a ferramenta Apple Configurator.
Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.



### Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.
* [Mantenha-se informado sobre desenvolvimentos futuros do Intune com o [plano Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)](http://go.microsoft.com/fwlink/?LinkID=273882)


<!--HONumber=May16_HO2-->


