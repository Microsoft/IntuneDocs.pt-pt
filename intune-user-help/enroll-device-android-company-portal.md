---
title: Registrar dispositivo Android com o Portal da Empresa do Intune | Microsoft Docs
description: Descreve como registrar um dispositivo Android com o Portal da Empresa do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e0a2297509d6077d6508adaab96ae6eb3cf9b28f
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856739"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrar seu dispositivo com o Portal da Empresa  
Registre seu dispositivo Android pessoal ou de propriedade corporativa para obter acesso seguro a email, aplicativos e dados da empresa. O Portal da Empresa dá suporte a dispositivos Android, incluindo Samsung Knox, executando o Android 4,4 e posterior.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> O Samsung Knox é um tipo de segurança que determinados dispositivos Samsung usam para proteção adicional, fora do que o Android nativo fornece. Para verificar se você tem um dispositivo Samsung Knox, > vá para **configurações** > **sobre dispositivo**. Se você não vir a **versão do Knox** listada, você terá um dispositivo Android nativo.

## <a name="enroll-device"></a>Inscrever o dispositivo  
Certifique-se de [instalar o aplicativo gratuito portal da empresa do Intune do Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Durante o registro, você pode ser solicitado a escolher uma categoria que melhor descreva como você usa seu dispositivo. O suporte de sua empresa usa sua resposta para verificar os aplicativos aos quais você tem acesso.  

1. Abra a aplicação Portal da Empresa e inicie sessão com a sua conta escolar ou profissional.  

2. Se for solicitado que você aceite os termos e condições da sua organização, toque em **aceitar tudo**.  

   ![Imagem de exemplo do Portal da Empresa, tela de termos, realçando o botão "aceitar tudo".](./media/accept-terms-1911.png)  


3. Examine o que a sua organização pode e não consegue ver. Em seguida, toque em **continuar**.


    ![Exemplo de imagem de Portal da Empresa, nós nos preocupamos com sua tela de privacidade, destacando o botão continuar.](./media/android-privacy-screen-1911.png)  
4. Examine o que esperar nas próximas etapas. Em seguida, toque em **Avançar**.  

    ![Exemplo de imagem de Portal da Empresa, a próxima tela, destacando o botão Avançar.](./media/android-whats-next-1911.png)  


5. Dependendo da sua versão do Android, você pode ser solicitado a permitir o acesso a determinadas partes do seu dispositivo. Esses prompts são exigidos pelo Google e não são controlados pela Microsoft.  

    Toque em **permitir** para as seguintes permissões:  
    * **Permitir que o portal da empresa faça e gerencie chamadas telefônicas**: essa permissão permite que seu dispositivo Compartilhe seu número de identidade internacional de equipamentos de estação móvel (IMEI) com o Intune, o provedor de gerenciamento de dispositivos da sua organização. É seguro permitir essa permissão. A Microsoft nunca fará ou gerenciará chamadas telefônicas.  
    * **Permitir que Portal da empresa acesse seus contatos**: essa permissão permite que o aplicativo portal da empresa crie, use e gerencie sua conta corporativa.  É seguro permitir essa permissão. A Microsoft nunca acessará seus contatos. 

    Se você negar a permissão, será solicitado novamente na próxima vez que entrar no Portal da Empresa. Para desativar essas mensagens, selecione **nunca perguntar novamente**. Para gerenciar permissões de aplicativo, vá para o aplicativo Configurações > **aplicativos** > **Portal da Empresa** > **permissões** > **telefone**.  

6. Ative o aplicativo de administrador do dispositivo. 

    Portal da Empresa precisa de permissões de administrador de dispositivo para gerenciar seu dispositivo com segurança. Ativar o aplicativo permite que sua organização identifique possíveis problemas de segurança, como tentativas repetidas com falha para desbloquear seu dispositivo e responder adequadamente.  

    ![Imagem de exemplo da tela ativar administrador do dispositivo, realçando o botão Ativar.](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> A Microsoft não controla as mensagens nesta tela. Entendemos que sua frase pode parecer um pouco drástica. Portal da Empresa não pode especificar quais restrições e acesso são relevantes para sua organização. Se você tiver dúvidas sobre como sua organização usa o aplicativo, entre em contato com o seu profissional de suporte de ti. Acesse o [site Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para localizar as informações de contato da sua organização.  


7. Seu dispositivo começa a se registrar. Se você estiver usando um dispositivo Samsung Knox, será solicitado a revisar e confirmar a política de privacidade do agente ELM primeiro.   

    ![Imagem de exemplo da tela de política de privacidade do Samsung Knox que aparece durante o registro.](./media/and-enroll-7-knox-privacy-policy.png)  

8. Na tela **configuração de acesso da empresa** , verifique se o dispositivo está registrado. Em seguida, toque em **continuar**.  

    ![Exemplo de imagem de Portal da Empresa, tela de configuração de acesso da empresa, mostrando que o dispositivo gerenciado foi concluído.](./media/update-settings-1911.png)  

9. Sua organização pode exigir que você atualize as configurações do dispositivo. Toque em **resolver** para ajustar uma configuração. Quando você terminar de atualizar as configurações, toque em **continuar**.  

   ![Exemplo de imagem de Portal da Empresa, atualizar configurações do dispositivo, realçar os botões resolver e continuar.](./media/resolve-settings-1911.png)  

10. Quando a instalação estiver concluída, toque em **concluído**.    

    ![Exemplo de imagem de Portal da Empresa, tela de configuração de acesso da empresa, mostrando a configuração concluída e realçando o botão concluído.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>Próximos passos  

Antes de tentar instalar um aplicativo escolar ou de trabalho, vá para **configurações** > **segurança**e ative **fontes desconhecidas**. Se você não ativar essa opção, verá a seguinte mensagem quando tentar instalar um aplicativo: "instalação bloqueada. Por motivos de segurança, o dispositivo está definido para bloquear as instalações de aplicações obtidas a partir de origens desconhecidas." Você pode tocar em **configurações** na mensagem para ir diretamente para **fontes desconhecidas**.  

> [!Note]
> Se a sua organização utilizar software de gestão de despesas de telecomunicações, terá de completar alguns passos adicionais antes de o dispositivo ficar totalmente inscrito. Saiba mais [aqui](enroll-your-device-with-telecom-expense-management-android.md).

Se você receber um erro ao tentar registrar seu dispositivo no Intune, poderá [enviar por email o suporte de sua empresa](send-logs-to-your-it-admin-by-email-android.md).  

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  