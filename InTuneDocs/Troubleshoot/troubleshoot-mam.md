---
title: "Resolução de problemas de gestão de aplicações móveis | Documentos da Microsoft"
description: "Este tópico descreve algumas sugestões de resolução de problemas para implementações de acesso condicional."
keywords: 
author: NathBarn
ms.author: oldang
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: d50a5751a5afd987196336e9443dc5a429a283fd
ms.openlocfilehash: b333c0f5097fec38bf0dd78726a028fd7aaccd2f


---

# <a name="troubleshoot-mobile-application-management"></a>Resolução de problemas de gestão de aplicações móveis

Se tiver problemas com a gestão de aplicações móveis, pode começar aqui. Este tópico contém alguns problemas comuns e as perguntas que pode ter e proporciona soluções e respostas.

## <a name="common-it-administrator-issues"></a>Problemas de administrador de TI comuns

1. **Problema:** a política de proteção de aplicações sem a inscrição de dispositivos, criada no portal do Azure, não se está a aplicar à aplicação Skype para Empresas nos dispositivos iOS e Android.

  **Resolução**: o Skype para Empresas tem de ser configurado para autenticação moderna.  Siga as instruções em [Enable your tenant for modern authentication (Ativar o seu inquilino para autenticação moderna – em inglês)](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para configurar a autenticação moderna para o Skype.

2. **Problema:** as políticas de proteção de aplicações não se estão a aplicar a qualquer [ aplicação do Office suportada](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) para qualquer utilizador.

  **Resolução**: confirmar que o utilizador está licenciado para o Intune e as aplicações do Office são visadas por uma política de proteção de aplicações implementada. Pode demorar até 8 horas para que seja aplicada uma política de proteção de aplicações recentemente implementada.

3. **Problema:** o utilizador de administração de TI não consegue configurar políticas de proteção de aplicações no Portal do Azure.

  **Resolução**:

  As seguintes funções de utilizador têm acesso ao Portal do Azure:

  - Administrador global, que pode configurar no [Portal do Office](http://portal.office.com/)
  - Proprietário, que pode configurar no [Portal do Azure](https://portal.azure.com/).
  - Contribuinte, que pode configurar no [Portal do Azure](https://portal.azure.com/).<br>

  Consulte [Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) para obter ajuda para configurar estas funções.

4. **Problema:** os relatórios de consola de administração não mostram a(s) conta(s) de utilizador às quais a política de proteção de aplicações foi recentemente implementada.

  **Resolução**: se um utilizador foi recentemente visado por uma política de proteção de aplicações, pode demorar até 24 horas para esse utilizador ser apresentado em relatórios como um utilizador visado.

5. **Problema:** as alterações/atualizações de políticas podem demorar até 8 horas para serem aplicadas.  

  **Resolução**: o utilizador final pode terminar sessão na aplicação e voltar a iniciar sessão para forçar a sincronização com o serviço.  

6. **Problema:** a política de proteção de aplicações não se está a aplicar a dispositivos DEP da Apple.

  **Resolução**: confirme que está a utilizar a Afinidade do Utilizador com o Programa de Inscrição de Dispositivos Apple (DEP). A Afinidade de Utilizador é necessária para qualquer aplicação que exija autenticação do utilizador no DEP.
Consulte [Inscrever dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md) para obter mais informações sobre a inscrição do DEP para iOS.

## <a name="common-end-user-issues"></a>Problemas comuns do utilizador final

### <a name="issues-on-ios"></a>Problemas de iOS

Mensagem de erro/caixa de diálogo | Causa | Remediação |
-- | --- | --- |
**Aplicação Não Configurada**: esta aplicação não foi configurada para ser utilizada. Contacte o seu administrador de TI para obter ajuda. | Falha ao detetar a política de proteção de aplicações obrigatória para a aplicação. |Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Bem-vindo ao Browser Gerido do Intune**: esta aplicação funciona melhor quando gerido pelo Microsoft Intune. Sempre pode utilizar esta aplicação para procurar na web e, quando é gerido pelo Microsoft Intune obter acesso a funcionalidades de proteção de dados adicionais. | Falha ao detetar a política de proteção de aplicações obrigatória para a aplicação Browser Gerido do Intune. <br><br>O utilizador pode continuar a utilizar a aplicação para procurar na web, mas a aplicação não é gerida pelo Intune. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se à aplicação Browser Gerido do Intune.
**Início de Sessão Falhou**: neste momento não podemos iniciar a sua sessão. Tente novamente mais tarde. | Falha ao inscrever o utilizador no serviço MAM após o utilizador tentar iniciar sessão com a respetiva conta profissional ou escolar. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Conta Não Configurada**: a sua organização não configurou a sua conta para aceder aos dados profissionais ou escolares. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Confirme que a conta de utilizador tem uma licença do Intune atribuída ao [portal do Office](http://portal.office.com).
**Dispositivo Não Compatível**: não pode utilizar esta aplicação porque está a utilizar um dispositivo desbloqueado por jailbreak. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo desbloqueado por jailbreak. | Repor as predefinições de fábrica do dispositivo. Siga [estas instruções](https://support.apple.com/en-us/HT201274) a partir do site de suporte da Apple.
**Ligação de Internet Obrigatória**: tem de estar ligado à Internet para verificar que pode utilizar esta aplicação. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Falha Desconhecida**: tente reiniciar esta aplicação. Se o problema persistir, entre em contacto com seu administrador de TI. | Ocorreu uma falha desconhecida. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie um pedido de suporte com o Intune [aqui](/how-to-get-support-for-microsoft-intune.md).
**Aceder aos Dados da sua Organização**: a conta escolar ou profissional que especificou não tem acesso a esta aplicação. Poderá ter de iniciar sessão com uma conta diferente. Contacte o seu administrador de TI para obter ajuda. | O Intune deteta que o utilizador tentou iniciar sessão com uma segunda conta profissional ou escolar que é diferente da conta inscrita na MAM para o dispositivo. Apenas uma conta escolar ou profissional pode ser gerida pelo MAM, uma vez por dispositivo. | Peça ao utilizador que inicie sessão na conta cujo nome de utilizador encontra-se pré-preenchido no ecrã de início de sessão. <br> <br> Em alternativa, o utilizador pode iniciar sessão com a nova conta escolar ou profissional e remover a conta existente inscrita na MAM.
**Problema de Ligação**: ocorreu um problema de ligação inesperado. Verifique a sua ligação e tente novamente.  |  Falha inesperada. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie um pedido de suporte com o Intune [aqui](/how-to-get-support-for-microsoft-intune.md).
**Alerta**: esta aplicação já não pode ser utilizada. Contacte o seu administrador de TI para obter mais informações. | Falha ao validar o certificado da aplicação. | Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.
**Erro**: esta aplicação encontrou um problema e tem de fechar. Se o erro persistir, contacte o administrador de TI. | Falha ao ler o PIN da aplicação MAM a partir da Keychain do iOS da Apple. | Reinicie o dispositivo. Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.


### <a name="issues-on-android"></a>Problemas no Android

Mensagem de erro/caixa de diálogo | Causa | Remediação |
-- | --- | --- |
**Aplicação não configurada**: esta aplicação não foi configurada para ser utilizada. Contacte o seu administrador de TI para obter ajuda. | Falha ao detetar a política de proteção de aplicações obrigatória para a aplicação. |Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Falhou o início da aplicação**: ocorreu um problema ao iniciar a aplicação. Tente atualizar a aplicação ou a aplicação de Portal da Empresa do Intune. Se precisar de ajuda, contacte o administrador de TI. | O Intune detetou a política de proteção de aplicação válida para a aplicação, mas a aplicação está a falhar durante a inicialização da MAM. | Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a aplicação de Portal da Empresa do Intune está instalada e atualizada no dispositivo. <br><br> Se o erro persistir, utilize a aplicação de Portal da Empresa para enviar os registos para o Intune ou criar um pedido de suporte [aqui](/how-to-get-support-for-microsoft-intune.md).
**Não foram encontradas aplicações**: não existem aplicações neste dispositivo que a sua organização permita abrir este conteúdo. Contacte o seu administrador de TI para obter ajuda. | O utilizador tentou abrir dados de trabalho ou de escola com outra aplicação, mas o Intune não localizou quaisquer outras aplicações geridas que estão autorizadas a abrir os dados. | Confirme que uma política de proteção de aplicações Android é implementada na segurança do utilizador e destina-se, pelo menos, a uma outra aplicação preparada para MAM que pode abrir os dados em questão.
**Início de sessão falhou**: tente iniciar sessão novamente. Se este problema persistir, entre em contacto com seu administrador de TI. | Falha ao autenticar a conta com a qual o utilizador tentou iniciar sessão. | Confirme que o utilizador iniciou sessão com a conta profissional ou escolar que já está inscrita no serviço MAM do Intune (a primeira conta escolar ou profissional com que iniciou sessão com êxito para esta aplicação). <br><br> Limpe os dados da aplicação. <br><br> Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a versão do Portal da Empresa está atualizada.
**Ligação de Internet obrigatória**: tem de estar ligado à Internet para verificar que pode utilizar esta aplicação. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Dispositivo não compatível**: não pode utilizar esta aplicação porque está a utilizar um dispositivo com root. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo com root. | Repor as predefinições de fábrica do dispositivo.
**Conta não configurada**: esta aplicação tem de ser gerida pelo Microsoft Intune, mas a sua conta não foi configurada. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Confirme que a conta de utilizador tem uma licença do Intune atribuída ao [portal do Office](http://portal.office.com).
**Não é possível registar a aplicação**: esta aplicação tem de ser gerida pelo Microsoft Intune, mas não foi possível registar esta aplicação neste momento. Contacte o seu administrador de TI para obter ajuda. | Falha ao inscrever automaticamente a aplicação com o serviço MAM quando é precisa a política de proteção de aplicações. | Limpe os dados da aplicação. <br><br> Envie os registos ao Intune através da aplicação de Portal da Empresa ou de um pedido de suporte de ficheiro [aqui](/how-to-get-support-for-microsoft-intune.md).





### <a name="see-also"></a>Consulte também
- [Validar a configuração de gestão de aplicações móveis](../deploy-use/validate-mobile-application-management.md)
- [Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


