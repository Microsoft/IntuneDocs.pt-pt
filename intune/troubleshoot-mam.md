---
title: Resolução de problemas de gestão de aplicações móveis
titleSuffix: Microsoft Intune
description: Este tópico descreve algumas sugestões de resolução de problemas para implementações de acesso condicional.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc7b7f56060ff90cc7b9df6cb8700c163d78e8f5
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61515624"
---
# <a name="troubleshoot-mobile-application-management"></a>Resolução de problemas de gestão de aplicações móveis

Este tópico fornece soluções para problemas comuns que ocorreram ao utilizar a gestão de aplicações móveis do Intune.

Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](get-support.md) para ver mais formas de obter ajuda.

## <a name="common-it-administrator-issues"></a>Problemas de administrador de TI comuns

Estes são os problemas comuns que um administrador de TI poderá experienciar ao utilizar políticas de proteção de aplicações do Intune.

| Problema | Descrição | Resolução |
| -- | -- | -- |
| A política não está a ser aplicada ao Skype para Empresas | A política de proteção de aplicações sem inscrição de dispositivos, criada no portal do Azure, não está a ser aplicada à aplicação Skype para Empresas nos dispositivos iOS e Android. | O Skype para Empresas tem de ser configurado para autenticação moderna.  Siga as instruções em [Enable your tenant for modern authentication (Ativar o seu inquilino para autenticação moderna – em inglês)](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para configurar a autenticação moderna para o Skype. |
| A política das aplicações do Office não está a ser aplicada | As políticas de proteção de aplicações não estão a ser aplicadas a nenhuma [aplicação do Office suportada](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) para nenhum utilizador. | Confirme que o utilizador tem licença para o Intune e que as aplicações do Office são visadas por uma política de proteção de aplicações implementada. Pode demorar até 8 horas para que seja aplicada uma política de proteção de aplicações recentemente implementada. |
| O administrador não consegue configurar a política de proteção de aplicações no Portal do Azure | O utilizador de administração de TI não consegue configurar políticas de proteção de aplicações no Portal do Azure. | As seguintes funções de utilizador têm acesso ao Portal do Azure: <ul><li>Administrador global, que pode configurar no [Centro de administração do Microsoft 365](https://admin.microsoft.com/)</li><li>Proprietário, que pode configurar no [Portal do Azure](https://portal.azure.com/).</li><li>Contribuinte, que pode configurar no [Portal do Azure](https://portal.azure.com/).</li></ul> Consulte a [controlo de administração baseada em funções (RBAC) com o Microsoft Intune](role-based-access-control.md) para obter ajuda a configurar estas funções.|
|Há contas de utilizador em falta em relatórios de política de proteção de aplicações | Os relatórios de consola de administração não mostram as contas de utilizador nas quais a política de proteção de aplicações foi recentemente implementada. | Se um utilizador foi recentemente visado por uma política de proteção de aplicações, pode demorar até 24 horas para esse utilizador ser apresentado em relatórios como um utilizador visado. |
| As alterações à política não estão a ser aplicadas | A aplicação das alterações e atualizações à política de proteção de aplicações pode demorar até 8 horas a entrar em vigor. | Caso aplicável, o utilizador final pode terminar sessão na aplicação e voltar a iniciar sessão para forçar a sincronização com o serviço. |
| A política de proteção de aplicações não está a funcionar com o DEP | A política de proteção de aplicações não está a ser aplicada a dispositivos DEP da Apple. | Confirme que está a utilizar a Afinidade do Utilizador com o Programa de Inscrição de Dispositivos (DEP) da Apple. A Afinidade de Utilizador é necessária para qualquer aplicação que exija autenticação do utilizador no DEP. <br><br>Consulte a [inscrever automaticamente dispositivos iOS com o programa de inscrição de dispositivos da Apple](device-enrollment-program-enroll-ios.md) para obter mais informações sobre a inscrição do DEP para iOS.|
| A política de transferência de dados não está a funcionar com o iOS | As políticas **Permitir que a aplicação transfira dados para outras aplicações** e **Permitir que a aplicação receba dados de outras aplicações** não gerem com êxito a transferência de dados no iOS. | Ver [como gerir a transferência de dados entre aplicações iOS no Microsoft Intune](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>Problemas comuns do utilizador final

Os problemas comuns do utilizador final encontram-se divididos nas seguintes categorias:

* **Cenários de utilização normal**: Um usuário final poderá deparar-se nestes cenários em aplicações que tenham uma política de proteção de aplicações do Intune. Estes não são verdadeiros problemas, mas podem ser interpretados como erros.

* **Caixas de diálogo de utilização normal**: Estes são caixas de diálogo de utilização que utilizadores finais poderão ver em aplicações que têm uma política de proteção de aplicações do Intune. Estas mensagens e caixas de diálogo **não** são indicativas de erros.

* **Mensagens de erro e caixas de diálogo**: Estas são as mensagens de erro e caixas de diálogo que utilizadores finais poderão ver em aplicações que têm uma política de proteção de aplicações do Intune. Muitas vezes, estas caixas de diálogo e mensagens de erro indicam que o administrador de TI cometeu um erro ou que existe um erro na proteção de aplicações do Intune.

### <a name="normal-usage-scenarios"></a>Cenários de utilização normal

Plataforma | Cenário | Explicação |
---| --- | --- |
iOS | O utilizador final pode utilizar a extensão de partilha do iOS para abrir dados escolares ou profissionais em aplicações não geridas, mesmo com a política de transferência de dados definida para **Apenas aplicações geridas** ou **Nenhuma aplicação.** Isto não resulta numa fuga de dados? | A política de proteção de aplicações do Intune não consegue controlar a extensão de partilha do iOS se o dispositivo não for gerido. Por esse motivo, **o Intune encripta os dados "empresariais" antes de os partilhar fora da aplicação**. Para o confirmar, pode tentar abrir o ficheiro "empresarial" fora da aplicação gerida. O ficheiro deverá estar encriptado, e não deverá ser possível abri-lo fora da aplicação gerida.
Android | Porque é que o utilizador final **tem de instalar a aplicação Portal da Empresa** mesmo que eu esteja a utilizar a proteção de aplicações de MAM sem inscrição de dispositivos?  | No Android, uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. **Embora a aplicação Portal da Empresa seja sempre obrigatória, a inscrição dos dispositivos não é necessária**. Para proteger aplicações sem inscrição, o utilizador final só precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

### <a name="normal-usage-dialogs"></a>Caixas de diálogo de utilização normal

Plataforma | Mensagem ou caixa de diálogo | Explicação |
--- | --- | --- |
iOS, Android | **Início de sessão**: Para proteger seus dados, a sua organização precisa de gerir esta aplicação. Para concluir esta ação, inicie sessão com a sua conta escolar ou profissional. | O utilizador final tem de iniciar sessão com a respetiva conta escolar ou profissional para poder utilizar esta aplicação, que requer uma política de proteção de aplicações. Por ordem para a política seja aplicada, o utilizador tem de ser autenticado relativamente ao Azure Active Directory.
iOS, Android |**Reinício necessário**: Sua organização está agora a proteger os dados nesta aplicação. Tem de reiniciar a aplicação para continuar. | A aplicação acabou de receber uma política de proteção de aplicações do Intune e tem de reiniciar para que a política seja aplicada.
iOS, Android |**Ação não é permitida**: Sua organização só lhe permite abrir dados escolares ou profissionais nesta aplicação. | O administrador de TI definiu a política **Permitir que a aplicação receba dados de outras aplicações** para **Apenas aplicações geridas**. Por conseguinte, o utilizador final só pode transferir dados para esta aplicação a partir de outras aplicações que têm uma política de proteção de aplicações.
iOS, Android |**Ação não é permitida**: Sua organização só permite transferir os respetivos dados para outras aplicações geridas. | O administrador de TI definiu a política **Permitir que a aplicação transfira dados para outras aplicações** para **Apenas aplicações geridas**. Por conseguinte, o utilizador final só pode transferir dados para fora desta aplicação para outras aplicações que têm uma política de proteção de aplicações.
iOS, Android |**Alerta de eliminação**: Sua organização removeu os respetivos dados associados esta aplicação. Para continuar, reinicie a aplicação. | O administrador de TI iniciou uma eliminação de aplicações através da proteção de aplicações do Intune.
Android | **Necessárias do Portal da empresa**: Para utilizar a sua conta escolar ou profissional com esta aplicação, tem de instalar a aplicação Portal da empresa do Intune. Clique em "Ir para a loja" para continuar. | No Android, uma grande parte da funcionalidade de proteção de aplicações está incorporada na aplicação Portal da Empresa. **Embora a aplicação Portal da Empresa seja sempre obrigatória, a inscrição dos dispositivos não é necessária**. Para proteger aplicações sem inscrição, o utilizador final só precisa de ter a aplicação Portal da Empresa instalada no dispositivo.

### <a name="error-messages-and-dialogs-on-ios"></a>Caixas de diálogo e mensagens de erro no iOS

Caixa de diálogo ou mensagem de erro | Causa | Remediação |
-- | --- | --- |
**Aplicação não configurada**: Esta aplicação não foi configurada para utilizar. Contacte o seu administrador de TI para obter ajuda. | Falha ao detetar a uma política de proteção de aplicações obrigatória para a aplicação. |Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Bem-vindo ao Browser gerido do Intune**: Esta aplicação funciona melhor quando gerido pelo Microsoft Intune. Sempre pode utilizar esta aplicação para procurar na web e, quando é gerido pelo Microsoft Intune obter acesso a funcionalidades de proteção de dados adicionais. | Falha ao detetar a uma política de proteção de aplicações obrigatória para a aplicação de Browser gerido do Intune. <br><br>O utilizador pode continuar a utilizar a aplicação para procurar na web, mas a aplicação não é gerida pelo Intune. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se à aplicação Browser Gerido do Intune.
**Início de sessão falhada**: Nós não é possível iniciar a sua sessão neste momento. Tente novamente mais tarde. | Falha ao inscrever o utilizador no serviço MAM após o utilizador tentar iniciar sessão com a respetiva conta profissional ou escolar. | Confirme que uma política de proteção de aplicações iOS é implementada para o grupo de segurança do utilizador e destina-se a esta aplicação.
**Conta não configurada**: Sua organização não definiu a sua conta para aceder aos dados escolares ou profissionais. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Certifique-se a conta de utilizador tem uma licença do Intune atribuída a [Centro de administração do Microsoft 365](https://admin.microsoft.com).
**Dispositivos não conformes**: Não é possível utilizar esta aplicação porque está a utilizar um dispositivo desbloqueado por jailbreak. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo desbloqueado por jailbreak. | Repor as predefinições de fábrica do dispositivo. Siga [estas instruções](https://support.apple.com/HT201274) a partir do site de suporte da Apple.
**Ligação de Internet obrigatória**: Tem de estar ligado à Internet para verificar que pode utilizar esta aplicação. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Falha desconhecida**: Tente reiniciar esta aplicação. Se o problema persistir, entre em contacto com seu administrador de TI. | Ocorreu uma falha desconhecida. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie uma [pedido de suporte](get-support.md#create-an-online-support-ticket) com o Intune.
**Aceder aos dados da sua organização**: A conta escolar ou profissional que especificou não tem acesso a esta aplicação. Poderá ter de iniciar sessão com uma conta diferente. Contacte o seu administrador de TI para obter ajuda. | O Intune deteta que o utilizador tentou iniciar sessão com uma segunda conta profissional ou escolar que é diferente da conta inscrita na MAM para o dispositivo. Apenas uma conta escolar ou profissional pode ser gerida pelo MAM, uma vez por dispositivo. | Peça ao utilizador que inicie sessão na conta cujo nome de utilizador encontra-se pré-preenchido no ecrã de início de sessão. <br> <br> Em alternativa, o utilizador pode iniciar sessão com a nova conta escolar ou profissional e remover a conta existente inscrita na MAM.
**Problema de ligação**: Ocorreu um problema de ligação inesperado. Verifique a sua ligação e tente novamente.  |  Falha inesperada. | Aguarde algum tempo e tente novamente. Se o erro persistir, crie uma [pedido de suporte](get-support.md#create-an-online-support-ticket) com o Intune.
**Alerta**: Esta aplicação já não pode ser utilizada. Contacte o seu administrador de TI para obter mais informações. | Falha ao validar o certificado da aplicação. | Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.
**Erro**: Esta aplicação encontrou um problema e tem de fechar. Se o erro persistir, contacte o administrador de TI. | Falha ao ler o PIN da aplicação MAM a partir da Keychain do iOS da Apple. | Reinicie o dispositivo. Confirme que a versão da aplicação está atualizada. <br><br> Reinstale a aplicação.

### <a name="error-messages-and-dialogs-on-android"></a>Caixas de diálogo e mensagens de erro no Android

Mensagem de erro/caixa de diálogo | Causa | Remediação |
-- | --- | --- |
**Aplicação não configurada**: Esta aplicação não foi configurada para utilizar. Contacte o seu administrador de TI para obter ajuda. | Falha ao detetar a uma política de proteção de aplicações obrigatória para a aplicação. |Confirme que é implementada uma política de proteção de aplicações Android no grupo de segurança do utilizador e que a mesma visa esta aplicação.
**Iniciação da aplicação com falha**: Ocorreu um problema ao iniciar a sua aplicação. Tente atualizar a aplicação ou a aplicação Portal da Empresa do Intune. Se precisar de ajuda, contacte o administrador de TI. | O Intune detetou a política de proteção de aplicação válida para a aplicação, mas a aplicação está a falhar durante a inicialização da MAM. | Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a aplicação Portal da Empresa do Intune está instalada e atualizada no dispositivo. <br><br> Se o erro persistir, utilize a aplicação Portal da empresa para enviar registos ao Intune ou criar um [pedido de suporte](get-support.md#create-an-online-support-ticket).
**Não foram encontradas aplicações**: Não existem aplicações neste dispositivo que sua organização permita para abrir este conteúdo. Contacte o seu administrador de TI para obter ajuda. | O utilizador tentou abrir dados de trabalho ou de escola com outra aplicação, mas o Intune não localizou quaisquer outras aplicações geridas que estão autorizadas a abrir os dados. | Confirme que uma política de proteção de aplicações Android é implementada na segurança do utilizador e destina-se, pelo menos, a uma outra aplicação preparada para MAM que pode abrir os dados em questão.
**Início de sessão falhada**: Tente iniciar sessão novamente. Se este problema persistir, entre em contacto com seu administrador de TI. | Falha ao autenticar a conta com a qual o utilizador tentou iniciar sessão. | Confirme que o utilizador iniciou sessão com a conta profissional ou escolar que já está inscrita no serviço MAM do Intune (a primeira conta escolar ou profissional com que iniciou sessão com êxito para esta aplicação). <br><br> Limpe os dados da aplicação. <br><br> Confirme que a versão da aplicação está atualizada. <br><br> Confirme que a versão do Portal da Empresa está atualizada.
**Ligação de Internet obrigatória**: Tem de estar ligado à Internet para verificar que pode utilizar esta aplicação. | O dispositivo não está ligado à Internet. | Ligue o dispositivo a uma rede Wi-Fi ou de Dados.
**Dispositivo como incompatível**: Não é possível utilizar esta aplicação porque está a utilizar um dispositivo desbloqueado por rooting. Contacte o seu administrador de TI para obter ajuda. | O Intune detetou que o utilizador está num dispositivo com root. | Repor as predefinições de fábrica do dispositivo.
**Conta não configurada**: Esta aplicação tem de ser gerenciada pelo Microsoft Intune, mas a sua conta não foi configurada. Contacte o seu administrador de TI para obter ajuda. | A conta de utilizador não tem uma licença Direta A do Intune. | Certifique-se a conta de utilizador tem uma licença do Intune atribuída a [Centro de administração do Microsoft 365](https://admin.microsoft.com).
**Não é possível registar a aplicação**: Esta aplicação tem de ser gerenciada pelo Microsoft Intune, mas não foi possível registar esta aplicação neste momento. Contacte o seu administrador de TI para obter ajuda. | Falha ao inscrever automaticamente a aplicação com o serviço MAM quando é precisa a política de proteção de aplicações. | Limpe os dados da aplicação. <br><br> Enviar registos ao Intune através da aplicação do Portal da empresa ou um pedido de suporte de ficheiros. Para obter mais informações, consulte [como obter suporte para o Microsoft Intune](get-support.md).

## <a name="next-steps"></a>Passos Seguintes

- [Validar a configuração de gestão de aplicações móveis](app-protection-policies-validate.md)
- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](known-issues.md).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](get-support.md).
