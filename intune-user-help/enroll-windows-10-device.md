---
title: Inscrever o dispositivo Windows 10 no Portal da empresa do Intune | Documentos da Microsoft
description: Passos de inscrição de dispositivos Windows 10 no Portal da empresa do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbb6c3b771ae768fe45bea1eecb21f7083003010
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196851"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Inscrever dispositivos Windows 10 com o Portal da empresa do Intune

Utilize o Portal da empresa do Intune para inscrever o seu dispositivo Windows 10 na gestão da sua organização. Este artigo descreve como inscrever dispositivos com Windows 10 versão 1607 e posterior e Windows 10 versão 1511 e anterior. Antes de começar, certifique-se de que [verificar a versão no seu dispositivo](windows-enrollment-company-portal.md#find-windows-10-version-number) , de modo a que pode seguir os passos corretos.  

Windows 10 é suportada em vários tipos de dispositivo, incluindo a área de trabalho, telemóvel e tablet. Os passos de inscrição são os mesmos em qualquer dispositivo que está a utilizar. No entanto, o ecrã pode parecer um pouco diferentes das imagens mostradas neste artigo.  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Inscrever com o Windows 10 versão 1607 e posterior dispositivo 
Estes passos descrevem como inscrever um dispositivo que é executado no Windows 10, versão 1607 e posterior.  

1. Aceda a **Iniciar**. Se estiver num dispositivo Windows 10 Mobile, avance para o **todas as aplicações** lista.

2. Abra o **definições** aplicação. Se a aplicação não está prontamente disponível na lista de aplicações, vá para a barra de pesquisa e o tipo "definições".

3. Selecione **Contas** > **Aceder a profiss./escolar** > **Ligar**.  


    ![Selecione Contas, Aceder a profiss./escolar](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Introduza o seu e-mail profissional ou escolar e, em seguida, selecione **Seguinte**.  


   ![Introduza a sua conta profissional ou escolar](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Inicie sessão no Intune com a sua conta profissional ou escolar.  


    ![Adicionar uma conta escolar ou profissional](./media/w10-enroll-rs1-enter-your-credentials.png)  

    , Eventualmente, verá uma mensagem que sua empresa ou escola está a registar o dispositivo.

6. Se a sua organização precisar de configurar um PIN para o Windows Hello, será solicitado para introduzir um código de verificação. Introduza o código e continua até na tela os passos para criar um PIN.  

7. Sobre o **está tudo pronto!** selecione **Concluído**. O dispositivo está agora inscrito.  

8. Para verificar a ligação, volte ao **configurações** > **contas** > **acesso profissional ou escolar**.  Agora deverá ser listada a sua conta.  


    ![Validar a definição correta da ligação](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

Continua sem aceder ao seu e-mail, ficheiros ou outros dados do trabalho ou da escola? Saiba como [resolver problemas de conta](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Inscrever com o Windows 10 versão 1511 e anterior dispositivo  
Estes passos descrevem como inscrever um dispositivo que é executado no Windows 10, versão 1511 e anterior.  

1. Aceda a **Iniciar**. Se estiver num dispositivo Windows 10 Mobile, avance para o **todas as aplicações** lista.

2. Abra o **definições** aplicação. Se a aplicação não está prontamente disponível na lista de aplicações, vá para a barra de pesquisa e o tipo "definições".

3. Selecione **contas** > **sua conta**.  


    ![Selecione A sua conta](./media/W10-enroll-2-accounts-your-account.png)  

5. Selecione **Adicionar uma conta escolar ou profissional**.  


    ![Selecione Adicionar uma conta escolar ou profissional](./media/w10-enroll-3-add-work-school-acct.png)  

6. Inicie sessão com as credenciais da sua conta profissional ou escolar.  


    ![Iniciar sessão](./media/W10-enroll-4-sign-in.png)  

Continua sem aceder ao seu e-mail, ficheiros ou outros dados do trabalho ou da escola? Saiba como [resolver problemas relacionados com a conta](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account) durante a inscrição.  

## <a name="it-administrator-support"></a>Suporte de administrador de TI   

Se for um administrador de TI e executar em problemas ao inscrever dispositivos, veja [problemas de inscrição de dispositivos de resolução de problemas do Windows no Microsoft Intune](https://support.microsoft.com/help/4469913). Este artigo lista erros comuns, suas causas e passos para resolvê-los. 

## <a name="next-steps"></a>Passos Seguintes  
Se precisar de ajuda com o Portal da empresa ou de inscrição, contacte a sua organização IT equipa de suporte. Encontrará as informações de contacto a [site do Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980). Inicie sessão para o site com a sua conta escolar ou profissional.  

 

