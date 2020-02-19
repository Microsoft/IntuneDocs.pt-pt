---
title: Resolução de problemas de gestão de aplicações móveis
titleSuffix: Microsoft Intune
description: Este tópico descreve algumas dicas de resolução de problemas para implementações de Acesso Condicional.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7214c4d262c332933e88af2cc158870bd844c5d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415458"
---
# <a name="troubleshoot-mobile-application-management"></a>Resolução de problemas de gestão de aplicações móveis

Este tópico fornece soluções para problemas comuns que ocorreram ao utilizar a Intune App Protection (também referida como MAM ou gestão de aplicações móveis).

Se estas informações não resolverem o problema, veja [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](../fundamentals/get-support.md) para ver mais formas de ajuda.

## <a name="common-it-administrator-issues"></a>Problemas de administrador de TI comuns

Estas são questões comuns que um administrador de TI pode experimentar ao utilizar políticas de proteção de aplicações Intune.

| Problema | Description | Resolução |
| -- | -- | -- |
| A política não está a ser aplicada ao Skype para Empresas | A política de proteção de aplicações sem inscrição de dispositivos, criada no portal do Azure, não está a ser aplicada à aplicação Skype para Empresas nos dispositivos iOS e Android. | O Skype para Empresas tem de ser configurado para autenticação moderna.  Siga as instruções em [Enable your tenant for modern authentication (Ativar o seu inquilino para autenticação moderna – em inglês)](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para configurar a autenticação moderna para o Skype. |
| A política das aplicações do Office não está a ser aplicada | As políticas de proteção de aplicações não estão a ser aplicadas a nenhuma [aplicação do Office suportada](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) para nenhum utilizador. | Confirme que o utilizador tem licença para o Intune e que as aplicações do Office são visadas por uma política de proteção de aplicações implementada. Pode demorar até 8 horas para que seja aplicada uma política de proteção de aplicações recentemente implementada. |
| O administrador não consegue configurar a política de proteção de aplicações no Portal do Azure | O utilizador administrador de TI não pode configurar as políticas de proteção de aplicações no portal Azure. | As seguintes funções de utilizador têm acesso ao portal Azure: <ul><li>Administrador global, que pode instalar no centro de administração da [Microsoft 365](https://admin.microsoft.com/)</li><li>Proprietário, que pode instalar no [portal Azure.](https://portal.azure.com/)</li><li>Colaborador, que pode instalar no [portal Azure.](https://portal.azure.com/)</li></ul> Consulte o [controlo de administração baseado em Role (RBAC) com](../fundamentals/role-based-access-control.md) o Microsoft Intune para ajudar a configurar estas funções.|
|Há contas de utilizador em falta em relatórios de política de proteção de aplicações | Os relatórios de consola de administração não mostram as contas de utilizador nas quais a política de proteção de aplicações foi recentemente implementada. | Se um utilizador foi recentemente visado por uma política de proteção de aplicações, pode demorar até 24 horas para esse utilizador ser apresentado em relatórios como um utilizador visado. |
| As alterações à política não estão a ser aplicadas | A aplicação das alterações e atualizações à política de proteção de aplicações pode demorar até 8 horas a entrar em vigor. | Caso aplicável, o utilizador final pode terminar sessão na aplicação e voltar a iniciar sessão para forçar a sincronização com o serviço. |
| A política de proteção de aplicações não está a funcionar com o DEP | A política de proteção de aplicações não está a ser aplicada a dispositivos DEP da Apple. | Confirme que está a utilizar a Afinidade do Utilizador com o Programa de Inscrição de Dispositivos (DEP) da Apple. A Afinidade de Utilizador é necessária para qualquer aplicação que exija autenticação do utilizador no DEP. <br><br>Consulte automaticamente [os dispositivos iOS de inscrição automática com o Programa de Inscrição](../enrollment/device-enrollment-program-enroll-ios.md) de Dispositivos da Apple para obter mais informações sobre a inscrição no iOS DEP.|
| A política de transferência de dados não está a funcionar com o iOS | A **app Permitir transferir dados para outras apps** e permitir que a app receba dados de outras políticas de **aplicações** não gere com sucesso a transferência de dados no iOS/iPadOS. | Ver [como gerir a transferência de dados entre aplicações iOS no Microsoft Intune](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>Problemas comuns do utilizador final

Os problemas comuns do utilizador final encontram-se divididos nas seguintes categorias:

* **Cenários de utilização normais**: Um utilizador final pode experimentar estes cenários em aplicações que têm uma política de proteção de aplicações Intune. Estes não são verdadeiros problemas, mas podem ser interpretados como erros.

* **Diálogos de utilização normais**: Estes são diálogos de utilização que um utilizador final pode ver em aplicações que têm uma política de proteção de aplicações Intune. Estas mensagens e caixas de diálogo **não** são indicativas de erros.

* **Mensagens de erro e diálogos**: Estas são mensagens de erro e diálogos que um utilizador final pode ver em aplicações que têm uma política de proteção de aplicações Intune. Muitas vezes, estas caixas de diálogo e mensagens de erro indicam que o administrador de TI cometeu um erro ou que existe um erro na proteção de aplicações do Intune.

### <a name="normal-usage-scenarios"></a>Cenários de utilização normal

Platform | Cenário | Explicação |
---| --- | --- |
iOS | O utilizador final pode utilizar a extensão de partilha do iOS para abrir dados escolares ou profissionais em aplicações não geridas, mesmo com a política de transferência de dados definida para **Apenas aplicações geridas** ou **Nenhuma aplicação.** Isto não resulta numa fuga de dados? | A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por esse motivo, **o Intune encripta os dados "empresariais" antes de os partilhar fora da aplicação**. Para o confirmar, pode tentar abrir o ficheiro "empresarial" fora da aplicação gerida. O ficheiro deverá estar encriptado, e não deverá ser possível abri-lo fora da aplicação gerida.
iOS | Porque é que o utilizador final **é solicitado para instalar a aplicação Microsoft Authenticator** | Isto é necessário quando o Acesso Condicional baseado na aplicação é aplicado, ver [Exigir aplicação de cliente aprovada](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access).
Android | Porque é que o utilizador final **tem de instalar a aplicação Portal da Empresa** mesmo que eu esteja a utilizar a proteção de aplicações de MAM sem inscrição de dispositivos?  | No Android, uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. **Embora a aplicação Portal da Empresa seja sempre obrigatória, a inscrição dos dispositivos não é necessária**. Para proteger aplicações sem inscrição, o utilizador final só precisa de ter a aplicação Portal da Empresa instalada no dispositivo.
iOS/Android | Política de Proteção de Aplicações não aplicada no projeto de e-mail na app Outlook | Uma vez que o Outlook suporta o contexto corporativo e pessoal, não aplica a MAM no projeto de e-mail.
iOS/Android | Política de Proteção de Aplicações não aplicada em novos documentos no WXP (Word,Excel,PowerPoint) | Uma vez que a WXP suporta o contexto corporativo e pessoal, não aplica a MAM em novos documentos até que sejam guardados num local corporativo identificado como o OneDrive.
iOS/Android | Apps que não permitem salvar o armazenamento local quando a política está ativada | O comportamento da App para esta definição é controlado pelo Desenvolvedor de Aplicações.
Android | Android tem mais restrições do que iOS sobre o que aplicações "nativas" podem aceder a conteúdos protegidos mAM | O Android é uma plataforma aberta e a associação de aplicações "nativas" pode ser alterada pelo utilizador final para aplicações potencialmente inseguras. Aplicar [exceções à política](app-protection-policies-exception.md) de transferência de dados para isentar aplicações específicas.
Android | A Proteção de Informação Azure (AIP) pode guardar como PDF quando salvar como é evitado | A AIP honra a política de MAM para "Desativar a impressão" quando é utilizado o Save as PDF.
iOS | Abrir anexos PDF na aplicação Outlook falha com "Action Not Allowed | Isto pode ocorrer se o utilizador não tiver autenticado o Acrobat Reader para Intune, ou tiver usado a impressão digital para autenticar a sua organização. Abra previamente o Acrobat Reader e autenticar usando credenciais UPN.


### <a name="normal-usage-dialogs"></a>Caixas de diálogo de utilização normal

Platform | Mensagem ou caixa de diálogo | Explicação |
--- | --- | --- |
iOS, Android | **Início de Sessão**: para proteger os respetivos dados, a sua organização tem de gerir esta aplicação. Para concluir esta ação, inicie sessão com a sua conta escolar ou profissional. | O utilizador final deve iniciar sessão com o seu trabalho ou conta escolar para utilizar esta aplicação, que requer uma política de proteção de aplicações. Para que a política se aplique, o utilizador deve autenticar-se contra o Diretório Ativo Azure.
iOS, Android |**Reinício Necessário**: a sua organização está agora a proteger os respetivos dados nesta aplicação. Tem de reiniciar a aplicação para continuar. | A aplicação acaba de receber uma política de proteção de aplicações Intune e deve reiniciar para que a política se aplique.
iOS, Android |**Ação Não Permitida**: a sua organização só lhe permite abrir dados escolares ou profissionais nesta aplicação. | O administrador de TI definiu a política **Permitir que a aplicação receba dados de outras aplicações** para **Apenas aplicações geridas**. Por isso, o utilizador final só pode transferir dados para esta aplicação a partir de outras aplicações que tenham uma política de proteção de aplicações.
iOS, Android |**Ação Não Permitida**: a sua organização só lhe permite transferir os respetivos dados para outras aplicações geridas. | O administrador de TI definiu a política **Permitir que a aplicação transfira dados para outras aplicações** para **Apenas aplicações geridas**. Por isso, o utilizador final só pode transferir dados desta aplicação para outras aplicações que tenham uma política de proteção de aplicações.
iOS, Android |**Alerta de Eliminação**: a sua organização removeu os respetivos dados associados a esta aplicação. Para continuar, reinicie a aplicação. | O administrador de TI iniciou uma eliminação de aplicações através da proteção de aplicações do Intune.
Android | **Aplicação Portal da Empresa necessária**: para utilizar a sua conta escolar ou profissional com esta aplicação, tem de instalar a aplicação Portal da Empresa do Intune. Clique em "Ir à loja" para continuar. | No Android, uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. **Embora a aplicação Portal da Empresa seja sempre obrigatória, a inscrição dos dispositivos não é necessária**. Para proteger aplicações sem inscrição, o utilizador final só precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

### <a name="error-messages-and-dialogs-on-ios"></a>Caixas de diálogo e mensagens de erro no iOS

Caixa de diálogo ou mensagem de erro | Causa | Remediação |
-- | --- | --- |
**Aplicação Não Configurada**: esta aplicação não foi configurada para ser utilizada. Contacte o seu administrador de TI para obter ajuda. | Falha na deteção de uma política de proteção de aplicações necessária para a aplicação. |Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Bem-vindo ao Browser Gerido do Intune**: esta aplicação funciona melhor quando gerido pelo Microsoft Intune. Sempre pode utilizar esta aplicação para procurar na web e, quando é gerido pelo Microsoft Intune obter acesso a funcionalidades de proteção de dados adicionais. | Falha na deteção de uma política de proteção de aplicações necessária para a aplicação Intune Managed Browser. <br><br>O utilizador pode continuar a utilizar a aplicação para procurar na web, mas a aplicação não é gerida pelo Intune. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se à aplicação Browser Gerido do Intune.
**Início de Sessão Falhou**: neste momento não podemos iniciar a sua sessão. Tente novamente mais tarde. | Falha ao inscrever o utilizador no serviço MAM após o utilizador tentar iniciar sessão com a respetiva conta profissional ou escolar. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Conta Não Configurada**: a sua organização não configurou a sua conta para aceder aos dados profissionais ou escolares. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Certifique-se de que a conta do utilizador tem uma licença Intune atribuída no centro de administração da [Microsoft 365](https://admin.microsoft.com).
**Dispositivo Não Compatível**: não pode utilizar esta aplicação porque está a utilizar um dispositivo desbloqueado por jailbreak. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo desbloqueado por jailbreak. | Repor as predefinições de fábrica do dispositivo. Siga [estas instruções](https://support.apple.com/HT201274) a partir do site de suporte da Apple.
**Ligação de Internet Obrigatória**: tem de estar ligado à Internet para verificar que pode utilizar esta aplicação. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Falha Desconhecida**: tente reiniciar esta aplicação. Se o problema persistir, entre em contacto com seu administrador de TI. | Ocorreu uma falha desconhecida. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie um bilhete de [apoio](../fundamentals/get-support.md#create-an-online-support-ticket) com intune.
**Aceder aos Dados da sua Organização**: a conta escolar ou profissional que especificou não tem acesso a esta aplicação. Poderá ter de iniciar sessão com uma conta diferente. Contacte o seu administrador de TI para obter ajuda. | O Intune deteta que o utilizador tentou iniciar sessão com uma segunda conta profissional ou escolar que é diferente da conta inscrita na MAM para o dispositivo. Apenas uma conta escolar ou profissional pode ser gerida pelo MAM, uma vez por dispositivo. | Peça ao utilizador que inicie sessão na conta cujo nome de utilizador encontra-se pré-preenchido no ecrã de início de sessão. Pode ser necessário [configurar a definição UPN do utilizador para Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). <br> <br> Em alternativa, o utilizador pode iniciar sessão com a nova conta escolar ou profissional e remover a conta existente inscrita na MAM.
**Problema de Ligação**: ocorreu um problema de ligação inesperado. Verifique a sua ligação e tente novamente.  |  Falha inesperada. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie um bilhete de [apoio](../fundamentals/get-support.md#create-an-online-support-ticket) com intune.
**Alerta**: esta aplicação já não pode ser utilizada. Contacte o seu administrador de TI para obter mais informações. | Falha ao validar o certificado da aplicação. | Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.
**Erro**: esta aplicação encontrou um problema e tem de fechar. Se o erro persistir, contacte o administrador de TI. | Falha ao ler o PIN da aplicação MAM a partir da Keychain do iOS da Apple. | Reinicie o dispositivo. Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.

### <a name="error-messages-and-dialogs-on-android"></a>Caixas de diálogo e mensagens de erro no Android

Mensagem de erro/caixa de diálogo | Causa | Remediação |
-- | --- | --- |
**Aplicação não configurada**: esta aplicação não foi configurada para ser utilizada. Contacte o seu administrador de TI para obter ajuda. | Falha na deteção de uma política de proteção de aplicações necessária para a aplicação. |Confirme que é implementada uma política de proteção de aplicações Android no grupo de segurança do utilizador e que a mesma visa esta aplicação.
**Falhou o início da aplicação**: ocorreu um problema ao iniciar a aplicação. Tente atualizar a aplicação ou a aplicação Portal da Empresa do Intune. Se precisar de ajuda, contacte o administrador de TI. | O Intune detetou a política de proteção de aplicação válida para a aplicação, mas a aplicação está a falhar durante a inicialização da MAM. | Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a aplicação Portal da Empresa do Intune está instalada e atualizada no dispositivo. <br><br> Se o erro persistir, utilize a aplicação Portal da Empresa para enviar registos para Intune ou criar um bilhete de [apoio](../fundamentals/get-support.md#create-an-online-support-ticket).
**Não foram encontradas aplicações**: não existem aplicações neste dispositivo que a sua organização permita abrir este conteúdo. Contacte o seu administrador de TI para obter ajuda. | O utilizador tentou abrir dados de trabalho ou de escola com outra aplicação, mas o Intune não localizou quaisquer outras aplicações geridas que estão autorizadas a abrir os dados. | Confirme que uma política de proteção de aplicações Android é implementada na segurança do utilizador e destina-se, pelo menos, a uma outra aplicação preparada para MAM que pode abrir os dados em questão.
**Início de sessão falhou**: tente iniciar sessão novamente. Se este problema persistir, entre em contacto com seu administrador de TI. | Falha ao autenticar a conta com a qual o utilizador tentou iniciar sessão. | Confirme que o utilizador iniciou sessão com a conta profissional ou escolar que já está inscrita no serviço MAM do Intune (a primeira conta escolar ou profissional com que iniciou sessão com êxito para esta aplicação). <br><br> Limpe os dados da aplicação. <br><br> Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a versão do Portal da Empresa está atualizada.
**Ligação de Internet obrigatória**: tem de estar ligado à Internet para verificar que pode utilizar esta aplicação. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Dispositivo não conforme**: não pode utilizar esta aplicação porque está a utilizar um dispositivo desbloqueado por rooting. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo com root. | Repor as predefinições de fábrica do dispositivo.
**Conta não configurada**: esta aplicação tem de ser gerida pelo Microsoft Intune, mas a sua conta não foi configurada. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Certifique-se de que a conta do utilizador tem uma licença Intune atribuída no centro de administração da [Microsoft 365](https://admin.microsoft.com).
**Não é possível registar a aplicação**: esta aplicação tem de ser gerida pelo Microsoft Intune, mas não foi possível registar esta aplicação neste momento. Contacte o seu administrador de TI para obter ajuda. | Falha ao inscrever automaticamente a aplicação com o serviço MAM quando é precisa a política de proteção de aplicações. | Limpe os dados da aplicação. <br><br> Envie registos para Intune através da aplicação Portal da Empresa ou preencha um bilhete de apoio. Para mais informações, consulte [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).

## <a name="next-steps"></a>Próximos passos

- [Validar a configuração de gestão de aplicações móveis](app-protection-policies-validate.md)
- Saiba como usar ficheiros de registo para resolver problemas na política de Proteção de Aplicações Intune, consulte [https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)
- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](../fundamentals/help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](../known-issues.md).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
