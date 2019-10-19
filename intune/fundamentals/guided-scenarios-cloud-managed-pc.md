---
title: Cenário guiado – área de trabalho moderna gerenciada pela nuvem
titleSuffix: Microsoft Intune
description: Saiba mais sobre o cenário guiado para configurar e configurar uma área de trabalho moderna básica no portal de gerenciamento de dispositivos Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c29035feeb8b35921a5837699fe0f58a3516f4a1
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585901"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Cenário guiado – área de trabalho moderna gerenciada pela nuvem

A área de trabalho moderna é a plataforma de produtividade de ponta para o operador de informações. O Office 365 ProPlus e o Windows 10 são os principais componentes do desktop moderno, juntamente com as linhas de base de segurança mais recentes para a proteção avançada contra ameaças do Windows 10 e do Windows Defender. 

O gerenciamento da área de trabalho moderna da nuvem traz o benefício adicional das ações remotas de toda a Internet. O gerenciamento de nuvem utiliza as políticas de gerenciamento de dispositivo do Windows Mobile incorporadas e remove dependências na diretiva de grupo Active Directory local. 

Se você quiser avaliar uma área de trabalho moderna gerenciada pela nuvem em sua própria organização, esse cenário guiado predefine todas as configurações necessárias para uma implantação básica. Neste cenário guiado, você criará um ambiente seguro no qual poderá experimentar os recursos de gerenciamento de dispositivos do Intune. 

## <a name="prerequisites"></a>Pré-requisitos
- [Definir a autoridade de MDM para o Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) – a configuração de autoridade de gerenciamento de dispositivo móvel (MDM) determina como você gerencia seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.
- M356 E3 mínimo (ou M365 E5 para obter a melhor segurança)
- Dispositivo Windows 10 1903 (registrado com o Windows AutoPilot para a melhor experiência do usuário final)
- Permissões de administrador do Intune necessárias para concluir este cenário guiado:
  - Configuração de dispositivo ler, criar, excluir, atribuir e atualizar
  - Programas de registro ler dispositivo, ler perfil, criar perfil, atribuir perfil, excluir perfil
  - Aplicativos móveis ler, criar, excluir, atribuir e atualizar
  - Leitura e atualização da organização
  - Linhas de base de segurança ler, criar, excluir, atribuir e atualizar
  - Política define leitura, criação, exclusão, atribuição e atualização

## <a name="step-1---introduction"></a>Etapa 1-Introdução

Usando esse cenário guiado, você configurará um usuário de teste, registrará um dispositivo no Intune e implantará o dispositivo com as configurações recomendadas pelo Intune, bem como o Windows 10 e o Office ProPlus. Seu dispositivo também será configurado para a proteção avançada contra ameaças do Microsoft defender, se você optar por [habilitar essa proteção no Intune](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). O usuário que você configurar e o dispositivo que você registrar será adicionado a um novo grupo de segurança e será configurado com as configurações recomendadas para segurança e produtividade. 

### <a name="what-you-will-need-to-continue"></a>O que será necessário para continuar

Você deve fornecer o dispositivo de teste e o usuário de teste neste cenário guiado. Certifique-se de concluir as seguintes tarefas:
- Configure uma conta de usuário de teste no Azure Active Directory.
- Crie um dispositivo de teste executando o Windows 10, versão 1903 ou posterior.
- Adicional [Registre o dispositivo de teste com o Windows AutoPilot](~/enrollment/enrollment-autopilot.md#add-devices).
- Adicional Habilite [a identidade visual da página de entrada Azure Active Directory de sua organização](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Etapa 2 – usuário

Escolha um usuário para configurar no dispositivo. Essa pessoa será o usuário principal do dispositivo.

Se você quiser adicionar mais usuários ou dispositivos a essa configuração, basta adicionar os usuários e dispositivos aos grupos de segurança do AAD gerados pelo assistente. Ao contrário de outros cenários orientados, você não precisa executar o assistente mais de uma vez, pois a configuração não é personalizável. Basta adicionar mais usuários e dispositivos aos grupos do AAD criados. Depois de concluir o assistente, você poderá exibir o grupo gerado com as políticas recomendadas implantadas. 

## <a name="step-3---device"></a>Etapa 3-dispositivo

Verifique se o dispositivo está executando o Windows 10, versão 1903 ou posterior.  O usuário primário precisará configurar o dispositivo quando ele for recebê-lo. Há duas opções de instalação disponíveis para o usuário. 

### <a name="option-a--windows-autopilot"></a>Opção A – piloto automático do Windows
O Windows AutoPilot automatiza a configuração de novos dispositivos para que os usuários possam configurá-los prontos para uso, sem assistência. Se o dispositivo já estiver registrado com o Windows AutoPilot, selecione-o por seu número de série. Para obter mais informações sobre como usar o Windows AutoPilot, consulte [registrar dispositivo com o piloto automático do Windows (opcional)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-auto-pilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Opção B – registro manual do dispositivo
Os usuários irão configurar manualmente e registrar seus novos dispositivos no gerenciamento de dispositivos móveis. Depois de concluir este cenário, redefina o dispositivo e forneça ao usuário primário as instruções de registro para dispositivos Windows. Para obter mais informações, consulte [unir um dispositivo Windows 10 ao Azure ad durante a experiência da primeira execução](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Etapa 4-examinar + criar

A etapa final permite que você examine um resumo das configurações que você configurou. Depois de revisar suas escolhas, clique em **implantar** para concluir o cenário guiado. Depois que o cenário guiado for concluído, uma tabela de recursos será exibida. Você pode editar esses recursos mais tarde, no entanto, depois de sair do modo de exibição de resumo, a tabela não será salva.

> [!IMPORTANT]
> Depois que o cenário guiado for concluído, ele exibirá um resumo. Você pode modificar os recursos listados no resumo posteriormente, no entanto, a tabela que está exibindo esses recurso não será salva.

### <a name="verification"></a>Verificação
1. Verificar se o escopo de usuário do MDM atribuído está selecionado
    - Verifique se o [escopo do usuário do MDM](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) é:
        - Defina como **todos** para o aplicativo **Microsoft Intune** ou,
        - Defina como **alguns**. Além disso, adicione o grupo de usuários criado por este cenário guiado.
2. Verifique se o usuário selecionado é capaz de ingressar dispositivos no Azure Active Directory.
    - Verifique se o ingresso no AAD é:
        - Definir como **todos** ou,
        - Defina como **alguns**. Além disso, adicione o grupo de usuários criado por este cenário guiado.
3. Siga as etapas apropriadas no dispositivo para associá-lo ao Azure AD com base no seguinte:
    - Com o AutoPilot. Para obter mais informações, consulte [modo controlado pelo usuário do Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Sem o piloto automático: para obter mais informações, consulte [unir um dispositivo Windows 10 ao Azure ad durante a experiência de primeira execução](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>O que acontece quando eu clico em implantar?
O usuário e o dispositivo serão adicionados a novos grupos de segurança. Eles também serão configurados com as configurações recomendadas do Intune para segurança e produtividade no trabalho ou na escola. Depois que o usuário ingressar no dispositivo no Azure AD, os aplicativos e configurações adicionais serão adicionados ao dispositivo. Para saber mais sobre essas configurações adicionais, consulte [início rápido: registrar seu dispositivo Windows 10](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Informações adicionais

### <a name="register-device-with-windows-auto-pilot-optional"></a>Registrar dispositivo com o piloto automático do Windows (opcional)

Opcionalmente, você pode optar por usar um dispositivo de piloto automático registrado. Para o piloto automático, esse cenário guiado atribuirá um perfil de implantação do AutoPilot e o profile de página de status de registro. O perfil de implantação do piloto automático será configurado da seguinte maneira:
- Modo controlado pelo usuário – ou seja, exigir que o usuário final Insira nome de usuário e senha durante a instalação do Windows.
- Ingresso no Azure AD.
- Personalizar a instalação do Windows:
  - Ocultar a tela termos de licenciamento de software da Microsoft
  - Ocultar configurações de privacidade 
  - Criar o perfil local do usuário sem privilégios de administrador local
  - Ocultar as opções de alterar conta na página de entrada corporativa

A página de status de registro será configurada para ser habilitada somente para dispositivos de piloto automático e não bloqueará a espera de todos os aplicativos serem instalados.

O cenário guiado também atribuirá o usuário ao dispositivo do piloto automático selecionado para uma experiência de instalação personalizada.

#### <a name="post-requisites"></a>Pós-requisitos
Depois que o usuário ingressar no dispositivo para Azure Active Directory, as seguintes configurações serão aplicadas ao dispositivo:
1. O Office 365 ProPlus será instalado automaticamente no PC gerenciado por nuvem. Ele inclui os aplicativos com os quais você está familiarizado, incluindo acesso, Excel, OneNote, Outlook, PowerPoint, Publicador, Skype for Business e Word. Você pode usar esses aplicativos para se conectar aos serviços do Office 365, como o SharePoint Online, o Exchange Online e o Skype for Business online. O Office 365 ProPlus é atualizado regularmente com novos recursos, ao contrário de versões que não são de assinatura do Office. Para obter uma lista dos novos recursos, consulte Novidades do Office 365.
2. As linhas de base de segurança do Windows serão instaladas no PC gerenciado por nuvem. Se você tiver configurado a proteção avançada contra ameaças do Microsoft defender, o cenário guiado também definirá as configurações de linha de base para o defender. A proteção avançada contra ameaças do defender fornece uma nova camada de pós-violação de proteção à pilha de segurança do Windows 10. Com uma combinação de tecnologia de cliente incorporada ao Windows 10 e um serviço de nuvem robusto, ela ajudará a detectar ameaças que o fizeram além de outras defesas. 

## <a name="next-steps"></a>Próximos passos

- Se você estiver usando a detecção avançada de ameaças do Windows Defender, crie uma [política de conformidade do Intune](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) para exigir a análise de ameaças do defender para atender à conformidade.
- Crie uma [política de acesso condicional com base no dispositivo](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) para bloquear o acesso se o dispositivo não atender à conformidade do Intune.
