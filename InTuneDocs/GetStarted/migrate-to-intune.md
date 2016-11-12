---
title: Migrar para o Intune | Microsoft Intune
description: 
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 8ebe9c29f4155a2aac39b502252f3225372d374f


---

# <a name="migrate-to-intune"></a>Migrar para o Intune


A migração para o Intune a partir da sua solução de gestão de mobilidade empresarial existente poderá seguir a sequência geral de passos abaixo:

![Passos de migração para o Intune](./media/migrate-intune-steps.png)

## <a name="notify-users"></a>Notificar os utilizadores

Assim que tiver a certeza de que a implementação piloto do Intune satisfez os seus requisitos, fale com os seus utilizadores sobre a migração futura dos respetivos dispositivos para o Intune. As mensagens de e-mail, instruções e [cartazes](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) podem ajudar a definir expectativas e fornecer detalhes de inscrição sobre os passos que os utilizadores têm de executar para manter a conetividade ininterrupta para recursos e aplicações da empresa. Certifique-se que a sua equipa de suporte está pronta para ajudar os utilizadores no processo de migração.

## <a name="modify-your-existing-enterprise-mobility-management-solution"></a>Modificar a solução de gestão de mobilidade empresarial existente

Dependendo de como pretende lidar com as políticas de acesso condicional entre a solução de gestão de mobilidade empresarial existente e o Intune, poderá ter de desativar as políticas de acesso condicional existentes. Terá de desativar as políticas de acesso condicional existentes OU definir o âmbito das políticas de acesso condicional existentes de modo a que não incluam os utilizadores/dispositivos que está prestes a migrar para o Intune.  Não tenha o Intune e a sua solução de gestão de mobilidade empresarial existente a aplicar políticas de acesso condicional aos mesmos utilizadores/dispositivos.

## <a name="enable-intune-conditional-access-policy-optional"></a>Ativar a política de acesso condicional do Intune (opcional)

Se tiver decidido impor imediatamente as políticas de acesso condicional sem um período de tolerância para a migração de dispositivos, ative as políticas de acesso condicional no Intune neste passo.  Certifique-se de que esta decisão é comunicada de forma eficaz aos seus utilizadores e à sua equipa de suporte técnico.  Se os dispositivos não estiverem inscritos no Intune e não estiverem conformes com as políticas do Intune, os utilizadores não conseguirão aceder aos recursos da empresa até se inscreverem no Intune e até os dispositivos estarem em conformidade com as políticas do Intune.

## <a name="unenrolling-devices-from-your-existing-enterprise-mobility-management-solution"></a>Anular a inscrição de dispositivos da solução de gestão de mobilidade empresarial existente

É necessário anular a inscrição dos dispositivos da solução de gestão de mobilidade empresarial existente antes de inscrevê-los no Intune. A nossa recomendação é permitir que os utilizadores anulem a inscrição dos respetivos dispositivos para obterem a melhor experiência de utilizador.  Siga as instruções de anulação de inscrição do fornecedor de soluções, para se certificar de que remove corretamente os utilizadores e dispositivos da sua plataforma, assegurando a mínima interrupção possível aos seus utilizadores finais.

## <a name="enrolling-devices-in-intune"></a>Inscrever dispositivos no Intune

Os utilizadores agendados para migração devem inscrever-se imediatamente no Intune para recuperarem ou evitarem a perda de acesso aos recursos, ao e-mail e às aplicações da empresa. Se tiver configurado o acesso condicional e os utilizadores tentarem aceder ao e-mail antes de se inscreverem no Intune, o acesso é bloqueado e recebe um e-mail de inscrição. Este e-mail orienta-os para inscreverem os respetivos dispositivos no Intune.  Em alternativa, os utilizadores podem inscrever-se no Intune através da aplicação Portal da Empresa do Intune ou nativamente através do sistema operativo Windows 8.1 e Windows 10 Mobile. Consulte o artigo [O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) para obter mais orientação sobre os passos de inscrição por plataforma.

## <a name="configure-intune-conditional-access-optional"></a>Configurar o acesso condicional do Intune (opcional)

Se tiver permitido um período de tolerância para a imposição de acesso condicional, ative as políticas de acesso condicional no Intune para iniciar a imposição quando tiver terminado o período de tolerância que comunicou aos utilizadores finais. Isto irá exigir de imediato que todos os dispositivos cumpram os requisitos da política de acesso condicional do Intune.

## <a name="enroll-remaining-devices-and-users"></a>Inscrição dos restantes dispositivos e utilizadores

Agora que já ativou o acesso condicional, todos os utilizadores têm de se inscrever no Intune e cumprir as políticas de conformidade da sua organização para obterem acesso aos recursos da empresa. Se tiver migrado os seus utilizadores numa inscrição faseada (e não todos de uma só vez), repita os passos acima até que todos os dispositivos e utilizadores estejam inscritos e geridos pelo Intune.

## <a name="retire-the-previous-enterprise-mobility-management-solution"></a>Extinguir a solução de gestão de mobilidade empresarial anterior

Depois de ter migrado todos os utilizadores e dispositivos para o Intune e ter confirmado que as migrações para o Intune foram bem sucedidas, pode extinguir a solução de gestão de mobilidade empresarial anterior e/ou anular a subscrição do serviço. Siga as instruções do fornecedor de soluções para se certificar de que remove os requisitos de infraestrutura desnecessários e cancela quaisquer subscrições/licenças corretamente.

## <a name="additional-migration-resources"></a>Recursos de migração adicionais

Precisa de ajuda adicional na migração para o Intune? Disponibilizamos opções de assistência de especialistas para ajudar a garantir que a sua migração é efetuada sem problemas:

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Serviços de Consultoria da Microsoft](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Suporte técnico e não técnico do Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Fórum TechNet do Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## <a name="get-a-downloadable-copy-of-this-guide"></a>Obter uma cópia transferível deste guia

Para obter uma cópia transferível deste guia completo, visite a [TechNet Gallery](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).



<!--HONumber=Nov16_HO2-->


