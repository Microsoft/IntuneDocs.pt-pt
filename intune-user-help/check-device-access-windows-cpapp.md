---
title: Verificar o acesso do dispositivo | Microsoft Docs
description: Verifique o acesso do dispositivo para saber se o dispositivo cumpre os requisitos e é capaz de aceder aos recursos do trabalho ou da escola.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49075fd750ade6aaa412d551f4177822b52ce7f2
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490097"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Verificar o acesso a partir da aplicação Portal da Empresa para Windows

Certifique-se de que o dispositivo tem acesso aos recursos de trabalho ou escolares. 

As organizações impõem requisitos, &ndash;como limites de encriptação e palavra-passe&ndash;, para garantir que apenas dispositivos fidedignos e seguros acedem aos respetivos dados. Os dispositivos geridos têm de cumprir e manter estes requisitos para aceder aos recursos da organização.

A ação **Check access** (Verificar acesso) avalia as definições do dispositivo e o respetivo estado de acesso. A página **Device details** (Detalhes do dispositivo) lista as definições que precisa de ajustar para recuperar o acesso. 

Conclua os passos neste artigo para verificar o acesso da aplicação Portal da Empresa para Windows.  

## <a name="check-access-from-device-details-page"></a>Verificar o acesso a partir da página Device details (Detalhes do dispositivo)  
1. Abra a aplicação Portal da Empresa para Windows e aceda a **My Devices** (Os Meus Dispositivos).  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, home page, com destaque da secção My Devices (Os Meus Dispositivos).](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Selecione um dispositivo.  
3. Na página **Device details** (Detalhes do dispositivo), selecione **Check access** (Verificar acesso). A aplicação sincroniza o seu dispositivo com os requisitos atuais da sua organização e verifica se o dispositivo os reúne. Esta verificação pode demorar alguns minutos.  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque do botão Check Access (Verificar Acesso).](./media/1809_CheckAccess_Checking_Status.png) 

4. Veja a atualização de estado. Irá mostrar que o dispositivo **Can access your organization's resources** (Pode aceder aos recursos da sua organização) ou **Cannot access your organization's resources** (Não pode aceder aos recursos da sua organização).  

   ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque da secção Status (Estado).](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Se o dispositivo não puder aceder aos recursos, vá para o alerta na parte superior da página. Clique em **More** (Mais) para expandir os respetivos detalhes. Clique em **Less** (Menos) para fechá-los.  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque do alerta na parte superior da página.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Quando aplicável, a mensagem mostra ligações de ajuda adicionais e ações de remediação. Selecione uma ou mais destas opções para iniciar a resolução de problemas imediatamente. As ações de resolução, sincronização e contacto descritas abaixo só estão visíveis ao utilizar o Portal da Empresa no dispositivo afetado.  

     * A opção **How to resolve this** (Como resolver este problema) abre um artigo de ajuda relevante, se disponível.  
     * A opção **Resolve** (Resolver) redireciona-o para a definição no seu dispositivo.  
     * A opção **Sync** (Sincronizar) avalia o seu dispositivo para se certificar de que corresponde aos requisitos da sua organização.  
     * A opção **Contact IT** (Contactar Equipa de TI) redireciona-o para as informações de contacto da sua equipa de TI.   
 
6. Depois de atualizar as definições, clique em **Check access** (Verificar acesso) para confirmar o estado do seu dispositivo.  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque da secção Status (Estado).](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Verificar o acesso a partir do menu de contexto do dispositivo  
1. Abra a aplicação Portal da Empresa para Windows e aceda a **My Devices** (Os Meus Dispositivos).  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, home page, com destaque da secção My Devices (Os Meus Dispositivos).](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Clique com o botão direito do rato ou mantenha premido qualquer dispositivo para abrir o respetivo [menu de contexto](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, home page. O menu de contexto do dispositivo está visível na secção **My Devices** (Os Meus Dispositivos) da página e mostra as ações "Rename" (Mudar o nome), "Remove" (Remover) e "Check access" (Verificar acesso).](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Selecione **Check access** (Verificar acesso). A aplicação sincroniza o seu dispositivo com os requisitos atuais da sua organização e verifica se o dispositivo os reúne. Esta verificação pode demorar alguns minutos.  
 
4. É apresentada uma mensagem abaixo do dispositivo para o informar que o dispositivo **Can access company resources** (Pode aceder aos recursos da empresa) ou **Can't access company resources** (Não pode aceder aos recursos da empresa). 

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque da secção Status (Estado).](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Se o dispositivo não puder aceder aos recursos, selecione o dispositivo.  
6. Na página **Device details** (Detalhes do dispositivo), vá para o alerta na parte superior da página. Clique em **More** (Mais) para expandir os respetivos detalhes. Clique em **Less** (Menos) para fechá-los.  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque do alerta na parte superior da página.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Quando aplicável, a mensagem mostra ligações de ajuda adicionais e ações de remediação. Selecione uma ou mais destas opções para iniciar a resolução de problemas imediatamente. As ações de resolução, sincronização e contacto descritas abaixo só estão visíveis ao utilizar o Portal da Empresa no dispositivo afetado.  

     * A opção **How to resolve this** (Como resolver este problema) abre um artigo de ajuda relevante, se disponível.  
     * A opção **Resolve** (Resolver) redireciona-o para a definição no seu dispositivo.  
     * A opção **Sync** (Sincronizar) avalia o seu dispositivo para se certificar de que corresponde aos requisitos da sua organização.  
     * A opção **Contact IT** (Contactar Equipa de TI) redireciona-o para as informações de contacto da sua equipa de TI.    

7. Depois de atualizar as definições, clique em **Check access** (Verificar acesso) na parte inferior da página.  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, página Device details (Detalhes do dispositivo), com destaque da ação Check access (Verificar acesso).](./media/1809_CheckAccess_Device_details_button.png) 


Precisa de mais ajuda? Encontre as informações de contacto do suporte da empresa no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
