---
title: Resolução de problemas de gestão de aplicações móveis
titleSuffix: Microsoft Intune
description: Este tópico descreve algumas dicas de solução de problemas para implantações de acesso condicional.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a272da470e206279e68077ce80324183c7a8227
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940463"
---
# <a name="troubleshoot-mobile-application-management"></a>Resolução de problemas de gestão de aplicações móveis

Este tópico fornece soluções para problemas comuns que ocorreram ao usar Proteção de Aplicativo do Intune (também conhecido como gerenciamento de aplicativo móvel ou MAM).

Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md) para ver mais formas de obter ajuda.

## <a name="common-it-administrator-issues"></a>Problemas de administrador de TI comuns

Esses são problemas comuns que um administrador de ti pode enfrentar ao usar as políticas de proteção de aplicativo do Intune.

| Problema | Descrição | Resolução |
| -- | -- | -- |
| A política não está a ser aplicada ao Skype para Empresas | A política de proteção de aplicações sem inscrição de dispositivos, criada no portal do Azure, não está a ser aplicada à aplicação Skype para Empresas nos dispositivos iOS e Android. | O Skype para Empresas tem de ser configurado para autenticação moderna.  Siga as instruções em [Enable your tenant for modern authentication (Ativar o seu inquilino para autenticação moderna – em inglês)](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para configurar a autenticação moderna para o Skype. |
| A política das aplicações do Office não está a ser aplicada | As políticas de proteção de aplicações não estão a ser aplicadas a nenhuma [aplicação do Office suportada](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) para nenhum utilizador. | Confirme que o utilizador tem licença para o Intune e que as aplicações do Office são visadas por uma política de proteção de aplicações implementada. Pode demorar até 8 horas para que seja aplicada uma política de proteção de aplicações recentemente implementada. |
| O administrador não consegue configurar a política de proteção de aplicações no Portal do Azure | O usuário administrador de ti não pode configurar políticas de proteção de aplicativo no portal do Azure. | As seguintes funções de usuário têm acesso ao portal do Azure: <ul><li>Administrador global, que pode ser configurado no centro de [administração Microsoft 365](https://admin.microsoft.com/)</li><li>Proprietário, que pode ser configurado na [portal do Azure](https://portal.azure.com/).</li><li>Colaborador, que pode ser configurado na [portal do Azure](https://portal.azure.com/).</li></ul> Consulte [RBAC (controle de administração baseada em função) com Microsoft Intune](../fundamentals/role-based-access-control.md) para obter ajuda sobre como configurar essas funções.|
|Há contas de utilizador em falta em relatórios de política de proteção de aplicações | Os relatórios de consola de administração não mostram as contas de utilizador nas quais a política de proteção de aplicações foi recentemente implementada. | Se um utilizador foi recentemente visado por uma política de proteção de aplicações, pode demorar até 24 horas para esse utilizador ser apresentado em relatórios como um utilizador visado. |
| As alterações à política não estão a ser aplicadas | A aplicação das alterações e atualizações à política de proteção de aplicações pode demorar até 8 horas a entrar em vigor. | Caso aplicável, o utilizador final pode terminar sessão na aplicação e voltar a iniciar sessão para forçar a sincronização com o serviço. |
| A política de proteção de aplicações não está a funcionar com o DEP | A política de proteção de aplicações não está a ser aplicada a dispositivos DEP da Apple. | Confirme que está a utilizar a Afinidade do Utilizador com o Programa de Inscrição de Dispositivos (DEP) da Apple. A Afinidade de Utilizador é necessária para qualquer aplicação que exija autenticação do utilizador no DEP. <br><br>Consulte [registrar automaticamente dispositivos IOS com o programa de registro de dispositivos da Apple](../enrollment/device-enrollment-program-enroll-ios.md) para obter mais informações sobre o registro de DEP do Ios.|
| A política de transferência de dados não está a funcionar com o iOS | As políticas **Permitir que a aplicação transfira dados para outras aplicações** e **Permitir que a aplicação receba dados de outras aplicações** não gerem com êxito a transferência de dados no iOS. | Consulte [como gerenciar a transferência de dados entre aplicativos do Ios no Microsoft Intune](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>Problemas comuns do utilizador final

Os problemas comuns do utilizador final encontram-se divididos nas seguintes categorias:

* **Cenários de uso normal**: Um usuário final pode experimentar esses cenários em aplicativos que têm uma política de proteção de aplicativo do Intune. Estes não são verdadeiros problemas, mas podem ser interpretados como erros.

* **Caixas de diálogo de uso normal**: São caixas de diálogo de uso que um usuário final pode ver em aplicativos que têm uma política de proteção de aplicativo do Intune. Estas mensagens e caixas de diálogo **não** são indicativas de erros.

* **Mensagens de erro e caixas de diálogo**: Essas são mensagens de erro e caixas de diálogo que um usuário final pode ver em aplicativos que têm uma política de proteção de aplicativo do Intune. Muitas vezes, estas caixas de diálogo e mensagens de erro indicam que o administrador de TI cometeu um erro ou que existe um erro na proteção de aplicações do Intune.

### <a name="normal-usage-scenarios"></a>Cenários de utilização normal

Plataforma | Cenário | Explicação |
---| --- | --- |
iOS | O utilizador final pode utilizar a extensão de partilha do iOS para abrir dados escolares ou profissionais em aplicações não geridas, mesmo com a política de transferência de dados definida para **Apenas aplicações geridas** ou **Nenhuma aplicação.** Isto não resulta numa fuga de dados? | A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por esse motivo, **o Intune encripta os dados "empresariais" antes de os partilhar fora da aplicação**. Para o confirmar, pode tentar abrir o ficheiro "empresarial" fora da aplicação gerida. O ficheiro deverá estar encriptado, e não deverá ser possível abri-lo fora da aplicação gerida.
iOS | Por que o usuário final é **solicitado a instalar o aplicativo Microsoft Authenticator** | Isso é necessário quando o acesso condicional baseado no aplicativo é aplicado, consulte [exigir aplicativo cliente aprovado](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access).
Android | Porque é que o utilizador final **tem de instalar a aplicação Portal da Empresa** mesmo que eu esteja a utilizar a proteção de aplicações de MAM sem inscrição de dispositivos?  | No Android, uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. **Embora a aplicação Portal da Empresa seja sempre obrigatória, a inscrição dos dispositivos não é necessária**. Para proteger aplicações sem inscrição, o utilizador final só precisa de ter a aplicação Portal da Empresa instalada no dispositivo.
iOS/Android | Política de proteção de aplicativo não aplicada em email de rascunho no aplicativo Outlook | Como o Outlook dá suporte ao contexto corporativo e pessoal, ele não impõe o MAM no email de rascunho.
iOS/Android | Política de proteção de aplicativo não aplicada em novos documentos no WXP (Word, Excel, PowerPoint) | Como o WXP dá suporte ao contexto corporativo e pessoal, ele não impõe o MAM em novos documentos até que eles sejam salvos em um local corporativo identificado, como o OneDrive.
iOS/Android | Aplicativos que não permitem salvar como no armazenamento local quando a política está habilitada | O comportamento do aplicativo para essa configuração é controlado pelo desenvolvedor do aplicativo.
Android | O Android tem mais restrições do que iOS em quais aplicativos "nativos" podem acessar conteúdo protegido por MAM | O Android é uma plataforma aberta e a associação de aplicativo "nativa" pode ser alterada pelo usuário final para aplicativos potencialmente não seguros. Aplicar [exceções de política de transferência de dados](app-protection-policies-exception.md) para isentar aplicativos específicos.
Android | A AIP (proteção de informações do Azure) pode salvar como PDF quando salvar como é impedido | AIP honra a política de MAM para ' desabilitar impressão ' quando salvar como PDF for usado.
iOS | A abertura de anexos em PDF no aplicativo Outlook falha com "ação não permitida | Isso pode ocorrer se o usuário não tiver sido autenticado no Acrobat Reader para Intune ou tiver usado impressão digital para se autenticar em sua organização. Abra o Acrobat Reader com antecedência e autentique usando credenciais UPN.


### <a name="normal-usage-dialogs"></a>Caixas de diálogo de utilização normal

Plataforma | Mensagem ou caixa de diálogo | Explicação |
--- | --- | --- |
iOS, Android | **Entrada**: Para proteger seus dados, sua organização precisa gerenciar este aplicativo. Para concluir esta ação, inicie sessão com a sua conta escolar ou profissional. | O usuário final deve entrar com sua conta corporativa ou de estudante para usar esse aplicativo, o que requer uma política de proteção de aplicativo. Para que a política seja aplicada, o usuário deve se autenticar no Azure Active Directory.
iOS, Android |**Reinicialização necessária**: Sua organização agora está protegendo seus dados neste aplicativo. Tem de reiniciar a aplicação para continuar. | O aplicativo acabou de receber uma política de proteção de aplicativo do Intune e deve ser reiniciado para que a política seja aplicada.
iOS, Android |**Ação não permitida**: Sua organização só permite que você abra dados corporativos ou de estudante neste aplicativo. | O administrador de TI definiu a política **Permitir que a aplicação receba dados de outras aplicações** para **Apenas aplicações geridas**. Portanto, o usuário final só pode transferir dados para esse aplicativo de outros aplicativos que têm uma política de proteção de aplicativo.
iOS, Android |**Ação não permitida**: Sua organização só permite que você transfira seus dados para outros aplicativos gerenciados. | O administrador de TI definiu a política **Permitir que a aplicação transfira dados para outras aplicações** para **Apenas aplicações geridas**. Portanto, o usuário final só pode transferir dados para fora desse aplicativo para outros aplicativos que têm uma política de proteção de aplicativo.
iOS, Android |**Apagar alerta**: Sua organização removeu seus dados associados a este aplicativo. Para continuar, reinicie a aplicação. | O administrador de TI iniciou uma eliminação de aplicações através da proteção de aplicações do Intune.
Android | **Portal da empresa necessário**: Para usar sua conta corporativa ou de estudante com este aplicativo, você deve instalar o aplicativo Portal da Empresa do Intune. Clique em "ir para armazenar" para continuar. | No Android, uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. **Embora a aplicação Portal da Empresa seja sempre obrigatória, a inscrição dos dispositivos não é necessária**. Para proteger aplicações sem inscrição, o utilizador final só precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

### <a name="error-messages-and-dialogs-on-ios"></a>Caixas de diálogo e mensagens de erro no iOS

Caixa de diálogo ou mensagem de erro | Causa | Remediação |
-- | --- | --- |
**Aplicativo não configurado**: Este aplicativo não foi configurado para uso. Contacte o seu administrador de TI para obter ajuda. | Falha ao detectar uma política de proteção de aplicativo necessária para o aplicativo. |Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Bem-vindo ao Intune Managed browser**: Esse aplicativo funciona melhor quando gerenciado por Microsoft Intune. Sempre pode utilizar esta aplicação para procurar na web e, quando é gerido pelo Microsoft Intune obter acesso a funcionalidades de proteção de dados adicionais. | Falha ao detectar uma política de proteção de aplicativo necessária para o aplicativo Intune Managed Browser. <br><br>O utilizador pode continuar a utilizar a aplicação para procurar na web, mas a aplicação não é gerida pelo Intune. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se à aplicação Browser Gerido do Intune.
**Falha ao entrar**: Não é possível conectá-lo agora. Tente novamente mais tarde. | Falha ao inscrever o utilizador no serviço MAM após o utilizador tentar iniciar sessão com a respetiva conta profissional ou escolar. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Conta não configurada**: Sua organização não configurou sua conta para acessar dados corporativos ou de estudante. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Verifique se a conta do usuário tem uma licença do Intune atribuída no [centro de administração Microsoft 365](https://admin.microsoft.com).
**Dispositivo não compatível**: Este aplicativo não pode ser usado porque você está usando um dispositivo com jailbreak. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo desbloqueado por jailbreak. | Repor as predefinições de fábrica do dispositivo. Siga [estas instruções](https://support.apple.com/HT201274) a partir do site de suporte da Apple.
**Conexão com a Internet necessária**: Você deve estar conectado à Internet para verificar se você pode usar este aplicativo. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Falha desconhecida**: Tente reiniciar este aplicativo. Se o problema persistir, entre em contacto com seu administrador de TI. | Ocorreu uma falha desconhecida. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie um [tíquete de suporte](../fundamentals/get-support.md#create-an-online-support-ticket) com o Intune.
**Acessando os dados da sua organização**: A conta corporativa ou de estudante especificada não tem acesso a este aplicativo. Poderá ter de iniciar sessão com uma conta diferente. Contacte o seu administrador de TI para obter ajuda. | O Intune deteta que o utilizador tentou iniciar sessão com uma segunda conta profissional ou escolar que é diferente da conta inscrita na MAM para o dispositivo. Apenas uma conta escolar ou profissional pode ser gerida pelo MAM, uma vez por dispositivo. | Peça ao utilizador que inicie sessão na conta cujo nome de utilizador encontra-se pré-preenchido no ecrã de início de sessão. Talvez seja necessário [definir a configuração de UPN do usuário para o Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). <br> <br> Em alternativa, o utilizador pode iniciar sessão com a nova conta escolar ou profissional e remover a conta existente inscrita na MAM.
**Problema de conexão**: Ocorreu um problema de conexão inesperado. Verifique a sua ligação e tente novamente.  |  Falha inesperada. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie um [tíquete de suporte](../fundamentals/get-support.md#create-an-online-support-ticket) com o Intune.
**Alerta**: Este aplicativo não pode mais ser usado. Contacte o seu administrador de TI para obter mais informações. | Falha ao validar o certificado da aplicação. | Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.
**Erro**: Este aplicativo encontrou um problema e deve ser fechado. Se o erro persistir, contacte o administrador de TI. | Falha ao ler o PIN da aplicação MAM a partir da Keychain do iOS da Apple. | Reinicie o dispositivo. Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.

### <a name="error-messages-and-dialogs-on-android"></a>Caixas de diálogo e mensagens de erro no Android

Mensagem de erro/caixa de diálogo | Causa | Remediação |
-- | --- | --- |
**Aplicativo não configurado**: Este aplicativo não foi configurado para uso. Contacte o seu administrador de TI para obter ajuda. | Falha ao detectar uma política de proteção de aplicativo necessária para o aplicativo. |Confirme que é implementada uma política de proteção de aplicações Android no grupo de segurança do utilizador e que a mesma visa esta aplicação.
**Falha ao iniciar o aplicativo**: Houve um problema ao iniciar seu aplicativo. Tente atualizar a aplicação ou a aplicação Portal da Empresa do Intune. Se precisar de ajuda, contacte o administrador de TI. | O Intune detetou a política de proteção de aplicação válida para a aplicação, mas a aplicação está a falhar durante a inicialização da MAM. | Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a aplicação Portal da Empresa do Intune está instalada e atualizada no dispositivo. <br><br> Se o erro persistir, use o aplicativo Portal da Empresa para enviar logs ao Intune ou criar um [tíquete de suporte](../fundamentals/get-support.md#create-an-online-support-ticket).
**Nenhum aplicativo encontrado**: Não há aplicativos neste dispositivo que sua organização permita abrir este conteúdo. Contacte o seu administrador de TI para obter ajuda. | O utilizador tentou abrir dados de trabalho ou de escola com outra aplicação, mas o Intune não localizou quaisquer outras aplicações geridas que estão autorizadas a abrir os dados. | Confirme que uma política de proteção de aplicações Android é implementada na segurança do utilizador e destina-se, pelo menos, a uma outra aplicação preparada para MAM que pode abrir os dados em questão.
**Falha ao entrar**: Tente entrar novamente. Se este problema persistir, entre em contacto com seu administrador de TI. | Falha ao autenticar a conta com a qual o utilizador tentou iniciar sessão. | Confirme que o utilizador iniciou sessão com a conta profissional ou escolar que já está inscrita no serviço MAM do Intune (a primeira conta escolar ou profissional com que iniciou sessão com êxito para esta aplicação). <br><br> Limpe os dados da aplicação. <br><br> Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a versão do Portal da Empresa está atualizada.
**Conexão com a Internet necessária**: Você deve estar conectado à Internet para verificar se você pode usar este aplicativo. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Dispositivo não compatível**: Este aplicativo não pode ser usado porque você está usando um dispositivo com raiz. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo com root. | Repor as predefinições de fábrica do dispositivo.
**Conta não configurada**: Esse aplicativo deve ser gerenciado pelo Microsoft Intune, mas sua conta não foi configurada. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Verifique se a conta do usuário tem uma licença do Intune atribuída no [centro de administração Microsoft 365](https://admin.microsoft.com).
**Não é possível registrar o aplicativo**: Esse aplicativo deve ser gerenciado pelo Microsoft Intune, mas não foi possível registrar esse aplicativo no momento. Contacte o seu administrador de TI para obter ajuda. | Falha ao inscrever automaticamente a aplicação com o serviço MAM quando é precisa a política de proteção de aplicações. | Limpe os dados da aplicação. <br><br> Envie logs para o Intune por meio do aplicativo Portal da Empresa ou arquivo um tíquete de suporte. Para obter mais informações, consulte [como obter suporte para Microsoft Intune](../fundamentals/get-support.md).

## <a name="next-steps"></a>Passos seguintes

- [Validar a configuração de gestão de aplicações móveis](app-protection-policies-validate.md)
- Saiba como usar arquivos de log para solucionar problemas de Proteção de Aplicativo do Intune política, consulte[https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)
- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](../fundamentals/help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](../known-issues.md).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
