---
title: "Benefícios do SDK da aplicação do Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: 3abf566831348de11f718370d6267e3ff4355bfb


---

# Descrição Geral do SDK da Aplicação do Intune
O SDK da Aplicação Intune está disponível para as plataformas iOS e Android e permite funcionalidades de gestão de aplicações móveis com o Microsoft Intune. Além disso, esforçamo-nos para reduzir a quantidade de alterações de código necessárias do programador. Vai descobrir que pode ativar maioria das funcionalidades SDK sem alterar o comportamento da sua aplicação. Para uma melhor experiência de utilizador final e administrador de TI, pode utilizar os APIs para personalizar o comportamento da aplicação para funcionalidades que requerem participação na aplicação. Assim que tiver a aplicação ativada, os administradores de TI podem implementar políticas em aplicações geridas pelo Intune e tirar partido destas funcionalidades para proteger os dados empresariais.

## Funcionalidades Normais

### Controlar a capacidade dos utilizadores moverem documentos empresariais
Os administradores de TI podem controlar o reposicionamento de ficheiros dos documentos empresariais em aplicações geridas pelo Intune. Por exemplo, podem implementar uma política que desative as aplicações de cópia de segurança de ficheiros de efetuarem uma cópia de segurança dos dados empresariais para a nuvem.

### Configurar restrições da área de transferência
Os administradores de TI podem configurar o comportamento da área de transferência nas aplicações geridas pelo Intune. Por exemplo, podem implementar uma política para que os utilizadores finais não possam utilizar a área de transferência para cortar/copiar de uma aplicação gerida pelo Intune e colar numa aplicação não gerida.

### Configurar restrições de captura de ecrã
Os administradores de TI podem impedir os utilizadores de capturar o ecrã se for apresentada uma aplicação gerida pelo Intune. A aplicação desta restrição impede a captura e a disponibilização de conteúdo empresarial confidencial. Esta funcionalidade só está disponível para dispositivos android.

### Impor encriptação nos dados guardados
Os administradores de TI podem impor uma política que assegure que os dados guardados no dispositivo pela aplicação são encriptados.

### Apagar dados empresariais remotamente
Os administradores de TI podem apagar dados empresariais remotamente a partir de uma aplicação gerida pelo Intune quando a inscrição do dispositivo for anulada no Microsoft Intune. Esta funcionalidade baseia-se na identidade e irá eliminar apenas os ficheiros relacionados com a identidade empresarial do utilizador final. Para tal, a funcionalidade requer a participação da aplicação. A aplicação pode especificar a identidade na qual deve ocorrer a eliminação com segundo as definições de utilizador. Na ausência destas definições de utilizador especificadas da aplicação, o comportamento predefinido é apagar o diretório da aplicação e notificar o utilizador final que o acesso aos recursos empresariais foi removido.

### Impor a utilização de um browser gerido
Os administradores de TI podem impor a utilização de um browser gerido quando abrir ligações a partir de aplicações geridas pelo Intune. A utilização do browser gerido pelo Microsoft Intune ajuda a garantir que as ligações que aparecem nos e-mails (que estão num cliente de correio gerido pelo Intune) são mantidas dentro do domínio das aplicações geridas pelo Intune.

### Impor uma política de PIN
Os administradores de TI podem impor uma política de PIN quando uma aplicação gerida pelo Intune é iniciada. Esta política ajuda a garantir que os utilizadores finais que inscreveram os dispositivos no Microsoft Intune são os mesmos utilizadores que estão a iniciar as aplicações. Quando os utilizadores finais configuram o PIN, o SDK da Aplicação do Intune utiliza o Azure Active Directory para verificar as credenciais dos utilizadores finais em relação às credenciais de inscrição de dispositivos.

### Exigir que os utilizadores introduzam credenciais antes de poderem iniciar a aplicações
Os administradores de TI podem exigir que os utilizadores introduzam as credenciais antes dos utilizadores poderem iniciar uma aplicação gerida  O SDK da Aplicação Intune utiliza o Azure Active Directory para fornecer uma experiência de início de sessão único, em que as credenciais, uma vez introduzidas, são reutilizadas para inícios de sessão subsequentes. Também é suportada a autenticação de soluções de gestão de identidades [federadas com o Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### Verificar o estado de funcionamento e a conformidade do dispositivo
Os administradores de TI podem verificar o estado de funcionamento e a conformidade do dispositivo com políticas empresariais antes de os utilizadores finais acederem a aplicações geridas pelo Intune. Na plataforma iOS, esta política verifica se o dispositivo tem jailbreak. Na plataforma Android, esta política verifica se o dispositivo tem root.

## Pré-visualização de Funcionalidades
O SDK da Aplicação Microsoft Intune inclui várias funcionalidades que estão em "pré-visualização". Pode começar a integrar APIs de pré-visualização, mas apenas para fins de teste. Tenha em atenção que estas pré-visualizações são adicionadas a cenários existentes em vez de substituírem cenários existentes.

### Suporte de várias identidades do SDK da Aplicação Microsoft Intune
O suporte de várias identidades é uma funcionalidade que permite a coexistência de contas geridas por políticas (empresariais) e não geridas (pessoais) numa única aplicação.

### Exemplo de um cenário de várias identidades
Muitos utilizadores configuram as contas de e-mail empresariais e pessoais na aplicação Outlook para iOS e Android. Quando um utilizador acede aos dados na respetiva conta empresarial, o administrador de TI tem de ter a certeza de que a gestão de políticas de MAM será aplicada. No entanto, quando um utilizador está a aceder a uma conta de e-mail pessoal, esses dados devem estar fora do controlo do administrador de TI. O Microsoft Intune permite isto ao direcionar a política de gestão para a conta empresarial apenas na aplicação. Esta funcionalidade de várias identidades ajuda a resolver o problema de proteção de dados que as organizações estão a enfrentar com dispositivos e aplicações que suportam contas pessoais e profissionais.

### Como suportar várias identidades
As APIs de pré-visualização permitem especificar um Nome Principal de Utilizador (UPN) com operações de dados específicas, tais como operações da área de transferência e operações de ficheiros. O SDK da Aplicação Microsoft Intune utiliza o UPN para corresponder a chamada efetuada ao UPN utilizado para inscrever o dispositivo no serviço Microsoft Intune. Se os UPNs corresponderem, a chamada é tratada como uma chamada de "dados empresariais" e os dados estão protegidos; se os UPNs não corresponderem, a chamada é tratada como uma chamada de "dados pessoais" e os dados não estão protegidos.

### Gestão de aplicações sem inscrição de dispositivos
Muitos utilizadores com dispositivos pessoais pretendem ver e utilizar os dados empresariais sem inscrever o respetivo dispositivo pessoal num produto de Gestão de Dispositivos Móveis (MDM). Uma vez que a inscrição MDM requer controlo global do dispositivo, os utilizadores hesitam em fornecer esse controlo global do seu próprio dispositivo pessoal à empresa.

A gestão de aplicações sem inscrição de dispositivos permite ao serviço Microsoft Intune implementar a política de MAM diretamente numa aplicação, sem depender de um canal de MDM para implementar a política. Uma vez que não é preciso nenhum canal MDM, a inscrição MDM não é necessária.




<!--HONumber=Jun16_HO4-->


