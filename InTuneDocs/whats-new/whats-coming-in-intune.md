---
title: "A edição antecipada | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c4b0f15456a9f24c95954d669a17c63f96a459
ms.openlocfilehash: 273016d4fe114bbe60e9cebc06e89584c8f91f0b


---

# Novidades futuras do Microsoft Intune - Outubro
O **Edição Antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Esteja atento a novas atualizações de Novidades futuras.

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

### Gerir a impressão a partir de aplicações geridas através de políticas de MAM
Já pode evitar a impressão de dados da empresa a partir de aplicações com políticas de MDM. Esta definição está disponível no [Portal do Azure](..deployuse/create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) e é suportada em dispositivos [iOS](..deployuse/ios-mam-policy-settings) e [Android](..deployuse/android-mam-policy-settings).
<!--TFS 1014328-->

### Novo Portal da Empresa do Microsoft Intune disponível para dispositivos com o Windows 10
A Microsoft está a lançar um novo Portal da Empresa do Microsoft Intune para dispositivos com o Windows 10. Esta aplicação, que tira partido do novo formato do Windows 10 Universal, irá oferecer ao utilizador uma experiência atualizada na aplicação e experiências idênticas em todos os dispositivos, PC e dispositivos móveis semelhantes com o Windows 10, permitindo que todos tenham a mesma funcionalidade atual.

A nova aplicação também irá permitir aos utilizadores tirarem partido de funcionalidades de plataforma adicionais, como o início de sessão único (SSO) e a autenticação baseada em certificados em dispositivos com o Windows 10. A aplicação será disponibilizada como uma atualização das instalações existentes do Portal da Empresa do Windows 8.1 e do Portal da Empresa do Windows Phone 8.1 a partir da Loja Windows.
<!--TFS 1016502-->

### Suporte do Android for Work

O Intune faz agora parte do [Programa Android for Work](https://enterprise.google.com/android/partners/). Iremos começar a implementar suporte para as funcionalidades do Android for Work no Intune a partir deste mês.

[Leia o anúncio da Microsoft sobre o suporte do Intune para o Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

<!---This month, some newly provisioned Intune tenants will start seeing the Android for Work features. We will announce later when existing tenants will begin to see this feature.--->
<!--TFS 1043303-->

### Compatibilidade do Android Samsung KNOX com o Intune

Determinados modelos do telemóvel Samsung Galaxy Ace não podem ser geridos pelo Intune como dispositivos Samsung KNOX. Ao inscrever estes dispositivos com o Intune, serão geridos como dispositivos Android padrão.
Os números dos modelos afetados são:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Não é necessária nenhuma ação adicional sua ou dos utilizadores finais.
Para obter mais informações, visite o site do [Samsung KNOX](https://www.samsungknox.com).

<!--TFS 1173566 iX blurb provided by Barry; requires PM signoff

### Multi-factor authentication for Android and iOS enrollment

In addition to Windows 8.1 and later, administrators can now enable multi-factor authentication for Android and iOS devices in the Microsoft Intune Enrollment application. -->    

### A aplicação do Portal da Empresa para Windows 8 foi preterida; o suporte para as plataformas do Windows Phone 8 e do Windows RT está a ser preterido
A partir de outubro de 2016, o Microsoft Intune irá preterir o suporte para o Portal da Empresa do Windows Phone 8. O Microsoft Intune irá também preterir o suporte para a plataforma do Windows Phone 8 e do Windows RT. Como resultado, não será capaz de inscrever ou atualizar dispositivos Windows Phone 8 e Windows RT.

Pode continuar a gerir dispositivos Windows Phone 8, Windows RT e Windows 8 que já tenham sido inscritos. Atualize dispositivos Windows Phone 8 e Windows 8 para Windows Phone 8.1 e Windows 8.1, e utilize as aplicações do Portal da Empresa para Windows 8.1 e Windows Phone 8.1 correspondentes para continuar a distribuir aplicações para estes dispositivos, sem interrupções.

A partir de novembro de 2016, iremos preterir o suporte para o Portal da Empresa do Windows Phone 8.
<!--TFS 1255391-->

### Acesso condicional para a gestão de aplicações móveis
Agora pode criar uma política de acesso condicional para bloquear o acesso de aplicações móveis não geridas ao [Exchange Online](..deployuse/restrict-access-to-exchange-online-with-microsoft-intune.md) e ao [SharePoint Online](..deployuse/restrict-access-to-sharepoint-online-with-microsoft-intune.md). Pode bloquear as aplicações e clientes de correio incorporados que não tenham o MAM ativado com o SDK da Aplicação do Intune.  Isto pode ser feito ao criar uma política de acesso condicional e ao especificar as aplicações que pretende que tenham acesso ao Exchange Online e ao SharePoint Online através do portal do Azure.
<!--TFS 1317673-->

<!--TFS 1318014; awaiting approval in notes as to whether to proceed

### "Default" policy is deprecated

To minimize unintentionally assigned profiles, Intune is removing support for the "default" Corporate Device Enrollment profile for Apple Device Enrollment Program (DEP) device serial numbers in the new Azure console. Serial numbers synchronized from an Apple DEP account will initially have no Corporate Device Enrollment profile assigned.  A profile must be assigned manually after synchronization. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

<!--TFS 1318023; awaiting approval in notes as to whether to proceed

### Deprecation of row-by-row iOS Details review for iOS device CSV uploads

In order to streamline uploading IMEI numbers for Corporate devices and Apple serial numbers for Configurator enrollment, Intune is removing the row by row review of hardware identifiers already found in the system. This review allows the IT Pro to accept associated Details from the CSV to overwrite the existing details for a hardware identifier already in the system. The review will be replaced by a single option to automatically overwrite Details for all hardware identifiers or ignore new details for existing identifiers. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

### Integração com a Lookout para a proteção de dispositivos iOS
Em outubro, a Microsoft está a integrar a solução de proteção da Lookout contra ameaças que afetam dispositivos móveis para proteger dispositivos móveis iOS através da deteção de malware, aplicações de risco e muito mais. A solução da Lookout ajuda-o a determinar o nível da ameaça, que é configurável. Pode criar uma regra de política de conformidade no Intune para determinar a conformidade dos dispositivos com base na avaliação de riscos feita pela Lookout. Ao utilizar políticas de acesso condicional, pode permitir ou bloquear o acesso a recursos da sua empresa com base no estado de conformidade do dispositivo.

Os utilizadores finais de dispositivos em não conformidade iOS receberão um pedido para os inscrever e terão de instalar a aplicação Lookout for Work nos seus dispositivos, ativar a aplicação e corrigir as ameaças comunicadas na mesma para obterem acesso aos dados da empresa.
<!--TFS 1319493-->

### SDK da Aplicação do Intune e Ferramenta de Encapsulamento para Android
Pode utilizar a Ferramenta de Encapsulamento de Aplicações do Intune ou o SDK da Aplicação do Intune para ativar as suas aplicações para que utilizem políticas de gestão de aplicações móveis do Intune (MAM). As novas atualizações da Ferramenta de Encapsulamento de Aplicações e o SDK irão incluir:

* Suporte para Android N
* Suporte para políticas de MAM do Intune sem necessidade da inscrição de dispositivos
* Suporte para aplicações Android baseado em Xamarin

Pode testar o MAM sem inscrição de dispositivos e o suporte do Xamarin na pré-visualização pública da Ferramenta de Encapsulamento de Aplicações Android aqui: [https://github.com/msintuneappsdk/intune-app-wrapper-android-preview](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview)
<!--TFS 1319511; please create new TFS entry for WN text associated with this TFS item-->

<!--TFS 1319613; no iX review on PM text blurb

### Private preview customers using MAM Conditional Access will have their policies reset

Due to changes in the policy structure for Conditional Access for Mobile App Management, any existing policies that were set by customers through the private preview will be removed. Customers will need to set new policies once the change is made. The timing will coincide with the October service update.
-->

### Consulte também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.



<!--HONumber=Oct16_HO1-->


