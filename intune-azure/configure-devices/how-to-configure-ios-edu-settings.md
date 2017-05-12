---
title: "Definições do Intune para a aplicação Sala de Aula do iOS | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições da aplicação Sala de Aula em dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 066fdacab7530122ed325238c0db3a9d3df580c9
ms.contentlocale: pt-pt
ms.lasthandoff: 05/10/2017


---


# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>Como configurar as definições do Intune para a aplicação Sala de Aula do iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="introduction"></a>Introdução
A [Sala de Aula](https://itunes.apple.com/app/id1085319084) é uma aplicação que ajuda os professores a orientar a aprendizagem e a controlar os dispositivos dos alunos numa sala de aula. Por exemplo, através da aplicação, um professor pode:

- Abrir aplicações nos dispositivos de alunos
- Bloquear e desbloquear o ecrã do iPad
- Ver o ecrã do iPad de um aluno
- Navegar nos iPads dos alunos para abrir um marcador ou um capítulo de um livro
- Apresentar o ecrã do iPad de um aluno numa Apple TV

Utilizar o perfil de dispositivo **Educação** do iOS do Intune e as informações deste tópico para o ajudar a configurar a aplicação Sala de Aula e os dispositivos nos quais a irá utilizar.

## <a name="before-you-start"></a>Antes de começar

Antes de começar a configurar estas definições, tenha em atenção o seguinte:

- Os iPads dos professores e dos alunos têm de estar inscritos no Intune
- Confirme que a aplicação [Sala de Aula da Apple](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) está instalada no dispositivo do professor. Pode fazê-lo manualmente ou com a [gestão de aplicações do Intune](../manage-apps/what-is-app-management.md).
- Tem de configurar certificados para autenticar as ligações entre os dispositivos do professor e dos alunos (veja o Passo 2)
- Os iPads do professor e dos alunos têm de estar na mesma rede Wi-Fi e ter o Bluetooth ativado
- A aplicação Sala de Aula é executada em iPads supervisionados com o iOS 9.3 ou posterior
- Nesta versão, o Intune suporta a gestão de um cenário 1:1, em que cada aluno tem o seu próprio iPad dedicado


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Passo 1 – Importar os seus dados escolares para o Azure Active Directory

Utilize o School Data Sync (SDS) da Microsoft para importar os registos escolares de um SIS (Sistema de Informações de Alunos) existente para o Azure Active Directory (Azure AD).
O SDS sincroniza as informações a partir do SIS e armazena-as no Azure AD. O Azure AD é um sistema de gestão da Microsoft que o ajuda a organizar os utilizadores e os dispositivos. Em seguida, pode utilizar estes dados para o ajudar a gerir os seus alunos e turmas. [Saiba mais sobre como implementar o SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Como importar dados através do SDS?

Pode importar informações para o SDS através de um dos seguintes procedimentos:

- [Ficheiros CSV](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) – exporte e compile manualmente os ficheiros de valores separados por vírgulas (.csv)
- [API PowerSchool](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) – um fornecedor SIS que simplifica a sincronização com o Azure AD
- [API Inteligente](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) – uma solução de gestão de identidade que se sincroniza diretamente com o Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) – um formato CSV que pode exportar e converter para se sincronizar com o Azure AD

### <a name="find-out-more"></a>Saiba mais

- [Saiba mais sobre a experiência completa de sincronização de dados escolares no local com o Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Saiba mais sobre o School Data Sync da Microsoft](https://sds.microsoft.com/)
- [Saiba mais sobre o licenciamento no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Passo 2 – Criar e atribuir um perfil de Educação do iOS no Intune

### <a name="configure-general-settings"></a>Configurar as definições gerais

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3.    No painel **Intune**, escolha **Configurar dispositivos**.
4.    No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
5.    No painel de perfis, escolha **Criar Perfil**.
6.    No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de educação do iOS.
7.    Na lista pendente **Plataforma**, selecione **iOS**.
8.    Na lista pendente **Tipo de perfil**, escolha **Educação**.
9.    Escolha **Definições** > **Configurar**.


Em seguida, precisa de certificados para estabelecer uma relação de fidedignidade entre os iPads do professor e dos alunos. Os certificados são utilizados para autenticar de forma silenciosa e sem problemas as ligações entre os dispositivos, sem ter de introduzir os nomes de utilizador nem palavras-passe.

>[!IMPORTANT]
>Os certificados do professor e dos alunos que utiliza têm de ser emitidos por autoridades de certificação (ACs) diferentes. Tem de criar duas ACs subordinadas novas ligadas à sua infraestrutura de certificados existente; uma para os professores e outra para os alunos.

Os perfis de educação do iOS suportam apenas os certificados PFX. Os certificados SCEP não são suportados.

Os certificados que cria têm de suportar a autenticação de servidor, além da autenticação de utilizador.

### <a name="configure-teacher-certificates"></a>Configurar os certificados do professor

No painel **Educação**, escolha **Certificados do professor**.

#### <a name="configure-teacher-root-certificate"></a>Configurar o certificado de raiz do professor

Em **Certificado de raiz do professor**, escolha o botão Procurar para selecionar o certificado de raiz do professor com a extensão .cer (DER ou codificado por Base64) ou .P7B (com ou sem cadeia completa).

#### <a name="configure-teacher-pkcs12-certificate"></a>Configurar o certificado do professor PKCS#12

Em **Certificado do professor PKCS#12**, configure os seguintes valores:

- **Formato do nome do requerente** – o Intune atribui automaticamente um prefixo ao nome comum do certificado (**líder** para o certificado do professor e **membro** para o certificado do aluno).
- **Autoridade de certificação** – uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. 
- **Nome da autoridade de certificação** – introduza o nome da autoridade de certificação.
- **Nome do modelo de certificado** – introduza o nome de um modelo de certificado que tenha sido adicionado a uma AC emissora. 
- **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
- **Período de validade do certificado** – especifique o tempo restante até o certificado expirar.
Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor também tem de ser inferior ao período de validade restante do certificado da AC emissora.

Quando concluir a configuração dos certificados, clique em **OK**.

### <a name="configure-student-certificates"></a>Configurar os certificados dos alunos

1.    No painel **Educação**, escolha **Certificados dos alunos**.
2.    No painel **Certificados dos alunos**, na lista de tipos de **Certificados de dispositivos de aluno**, escolha **1:1**.

#### <a name="configure-student-root-certificate"></a>Configurar o certificado de raiz dos alunos

Em **Certificado de raiz dos alunos**, escolha o botão Procurar para selecionar o certificado de raiz do aluno com a extensão .cer (DER ou codificado por Base64) ou .P7B (com ou sem cadeia completa).

#### <a name="configure-student-pkcs12-certificate"></a>Configurar o certificado dos alunos PKCS#12

Em **Certificado dos alunos PKCS#12**, configure os seguintes valores:

- **Formato do nome do requerente** – o Intune atribui automaticamente um prefixo ao nome comum do certificado (**líder** para o certificado do professor e **membro** para o certificado do aluno).
- **Autoridade de certificação** – uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. 
- **Nome da autoridade de certificação** – introduza o nome da autoridade de certificação.
- **Nome do modelo de certificado** – introduza o nome de um modelo de certificado que tenha sido adicionado a uma AC emissora. 
- **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
- **Período de validade do certificado** – especifique o tempo restante até o certificado expirar.
Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor também tem de ser inferior ao período de validade restante do certificado da AC emissora.

Quando concluir a configuração dos certificados, selecione **OK**.

## <a name="finish-up"></a>Concluir

1.    No painel **Educação**, selecione OK.
2.    No painel **Criar Perfil**, selecione **Criar**.
    
O perfil será criado e é apresentado no painel da lista de perfis.

Atribua o perfil aos dispositivos dos alunos nos grupos de sala de aula que foram criados quando sincronizou os dados escolares com o Azure AD (veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).

## <a name="next-steps"></a>Próximos passos

Agora, quando um professor utilizar a aplicação Sala de Aula, terá controlo total sobre os dispositivos dos alunos.

Para obter mais informações sobre a aplicação Sala de Aula, veja [Ajuda de Sala de Aula](https://help.apple.com/classroom/ipad/2.0/) no site da Apple.

