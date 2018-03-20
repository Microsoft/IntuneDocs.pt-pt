---
title: "Definições de dispositivo partilhado do Intune para a aplicação Sala de Aula do iOS"
titlesuffix: Azure portal
description: "Saiba quais são as definições do Intune que pode utilizar para controlar as definições da aplicação Sala de Aula em dispositivos iOS.\""
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6dc373f831b574abf7d63e97935a379e731422
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-configure-intune-education-settings-for-shared-ipad-devices"></a>Como configurar definições de educação do Intune para dispositivos iPad partilhados

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune suporta a aplicação Sala de Aula para iOS, que ajuda os professores a orientar a aprendizagem e a controlar os dispositivos dos estudantes na sala de aula. Além da aplicação Sala de Aula, a Apple suporta a possibilidade de configurar os dispositivos iPad dos estudantes de forma a que múltiplos estudantes possam partilhar um único dispositivo. Este documento fornece-lhe orientações para alcançar este objetivo com o Intune.

Para obter informações sobre como configurar dispositivos iPad (1:1) dedicados para utilizar a aplicação Sala de Aula, veja [Como configurar as definições do Intune para a aplicação Sala de Aula do iOS](education-settings-configure-ios.md).

## <a name="before-you-start"></a>Antes de começar

Os pré-requisitos para utilizar as funcionalidades do iPad partilhado são:

- Configurar o [Apple School Manager](apple-school-manager-set-up-ios.md) e o [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617).
- Como parte da configuração do Apple School Manager, configure os [Apple IDs geridos](http://help.apple.com/schoolmanager/#/tes78b477c81) dos estudantes. [Saiba mais informações sobre os Apple IDs geridos](https://support.apple.com/HT205918).
- Crie um perfil de inscrição para os números de série do dispositivo sincronizadas a partir do Apple School Manager.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Passo 1 – Importar os seus dados escolares para o Azure Active Directory

Utilize o School Data Sync (SDS) da Microsoft para importar os registos escolares de um SIS (Sistema de Informações de Estudantes) existente para o Azure Active Directory (Azure AD).
O SDS sincroniza as informações a partir do SIS e armazena-as no Azure AD. O Azure AD é um sistema de gestão da Microsoft que o ajuda a organizar os utilizadores e os dispositivos. Em seguida, pode utilizar estes dados para o ajudar a gerir os seus alunos e turmas. [Saiba mais sobre como implementar o SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Como importar dados através do SDS

Pode importar informações para o SDS através de um dos seguintes métodos:

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

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
5. No painel de perfis, selecione **Criar perfil**.
6. No painel **Criar perfil**, introduza um **Nome** e uma **Descrição** para o perfil de educação do iOS.
7. Na lista pendente **Plataforma**, selecione **iOS**.
8. Na lista pendente **Tipo de perfil**, escolha **Educação**.
9. Escolha **Definições** > **Configurar**.

Em seguida, precisa de certificados para estabelecer uma relação de fidedignidade entre os iPads do professor e dos estudantes. Os certificados são utilizados para autenticar de forma silenciosa e sem problemas as ligações entre os dispositivos, sem ter de introduzir os nomes de utilizador nem palavras-passe.

>[!Important]
>Os certificados de professor e estudante que utiliza têm de ser emitidos por autoridades de certificação (ACs) diferentes. Tem de criar duas ACs subordinadas novas ligadas à sua infraestrutura de certificados existente; uma para os professores e outra para os estudantes.

Os perfis de educação do iOS só suportam certificados PFX. Os certificados SCEP não são suportados.

Os certificados que cria têm de suportar a autenticação de servidor, além da autenticação de utilizador.

### <a name="configure-teacher-certificates"></a>Configurar os certificados do professor

No painel **Educação**, selecione **Certificados do professor**.

#### <a name="configure-teacher-root-certificate"></a>Configurar o certificado de raiz do professor

Em **Certificado de raiz do professor**, escolha o botão Procurar para selecionar o certificado de raiz do professor com a extensão .cer (DER ou codificado por Base64) ou .P7B (com ou sem cadeia completa).

#### <a name="configure-teacher-pkcs12-certificate"></a>Configurar o certificado do professor PKCS#12

Em **Certificado do professor PKCS#12**, configure os seguintes valores:

- **Formato do nome do requerente** – o Intune atribui automaticamente um prefixo ao nome comum do certificado (**líder** para o certificado do professor e **membro** para o certificado de estudante).
- **Autoridade de certificação** – uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma.
- **Nome da autoridade de certificação** – introduza o nome da autoridade de certificação.
- **Nome do modelo de certificado** – introduza o nome de um modelo de certificado que tenha sido adicionado a uma AC emissora.
- **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
- **Período de validade do certificado** – especifique o tempo restante até o certificado expirar. Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor também tem de ser inferior ao período de validade restante do certificado da AC emissora.

Quando concluir a configuração dos certificados do professor, selecione **OK**.

### <a name="configure-student-certificates"></a>Configurar os certificados de estudante

1. No painel **Educação**, selecione **Certificados de estudante**.
2. No painel **Certificados de estudante**, na lista de tipos de **Certificados de dispositivos de estudante**, selecione **iPad partilhado**.

#### <a name="configure-student-root-certificate"></a>Configurar o certificado de raiz do estudante

Em **Certificado de raiz do dispositivo**, selecione o botão Procurar para selecionar o certificado de raiz do estudante com a extensão .cer (DER ou codificado por Base64) ou .P7B (com ou sem cadeia completa).

#### <a name="configure-device-pkcs12-certificate"></a>Configurar o certificado do dispositivo PKCS#12

Em **Certificado PKCS#12 do estudante**, configure os seguintes valores:

- **Formato do nome do requerente** – o Intune atribui automaticamente um prefixo ao nome comum do certificado (líder para o certificado do professor e membro para o certificado do dispositivo).
- **Autoridade de certificação** – uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma.
- **Nome da autoridade de certificação** – introduza o nome da autoridade de certificação.
- **Nome do modelo de certificado** – introduza o nome de um modelo de certificado que tenha sido adicionado a uma AC emissora.
- **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
- **Período de validade do certificado** – especifique o tempo restante até o certificado expirar. Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor também tem de ser inferior ao período de validade restante do certificado da AC emissora.

Quando concluir a configuração dos certificados, selecione **OK**.

### <a name="complete-certificate-setup"></a>Concluir Configuração de Certificado

1. No painel **Educação**, selecione **OK**.
2. No painel **Criar perfil**, selecione **Criar**.

O perfil será criado e apresentado no painel Lista de perfis.

## <a name="step-3---create-a-device-category"></a>Passo 3 – criar uma categoria de dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Inscrição de dispositivos**.
4. No painel **Inscrição de dispositivos – Descrição geral**, selecione **Categorias de dispositivos**.
5. No painel **Inscrição de dispositivos – Categorias de dispositivos**, selecione **Criar**.
6. No painel **Criar categoria de dispositivos**, introduza um **Nome** e uma **Descrição** para a categoria.
7. No painel **Criar categoria de dispositivos**, selecione **Criar**.

A categoria de dispositivos é criada no painel **Inscrição – Categorias de Dispositivos**.

## <a name="step-4--create-a-dynamic-group"></a>Passo 4 – criar um grupo dinâmico

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Grupos**.
4. No painel **Utilizadores e Grupos – Todos os Grupos**, selecione **Novo grupo**.
5. No painel **Grupo**, selecione um **Tipo de grupo** e, em seguida, introduza um **Nome** e uma **Descrição** para o grupo.
6. Na lista pendente **Tipo de associação**, selecione **Dispositivo Dinâmico**.
7. Selecione **Membros de dispositivo dinâmicos** para criar regras de associação de grupo.
8. No painel **Regras de associação dinâmica**:
1. Selecione **deviceCategory** na lista pendente **Adicionar dispositivos onde**.
2. Selecione **É igual a**.
3. Introduza a categoria de dispositivos que criou na caixa de texto em branco.
9. No painel **Regras de associação dinâmica**, selecione **Adicionar consulta**.
10. No painel **Grupo**, selecione **Criar**.

O grupo dinâmico é criado no painel **Utilizadores e Grupos – Todos os Grupos**.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>Passo 5 – atribuir um dispositivo a uma categoria (Carrinhos)

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. No painel **Dispositivos – Todos os dispositivos**, selecione um dispositivo.
6. No painel de dispositivos, selecione **Propriedades**.
7. No painel de propriedades do dispositivo, introduza a categoria de dispositivos na caixa de texto **Categoria de dispositivos**.
8. No painel do dispositivo, selecione **Guardar**.

O dispositivo está agora associado à categoria de dispositivos. Repita este processo para todos os dispositivos que pretender associar à categoria de dispositivos que criou.

## <a name="step-6--create-classroom-profiles"></a>Passo 6 – criar perfis de sala de aula

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
4. No painel **Configuração do dispositivo**, selecione **Gerir** > **Perfis do Carrinho**.
5. No painel de perfis, selecione **Criar Perfil**.
6. No painel **Criar Associação**, introduza um **Nome** e uma **Descrição**.
7. Selecione a opção **Selecionar Classes** > **Configurar** para associar grupos ao Perfil do Carrinho.
8. Selecione as turmas a incluir no Perfil do Carrinho e, em seguida, selecione **Selecionar**. 
9. Selecione a opção **Selecionar Carrinhos** > **Configurar** para associar grupos ao Perfil do Carrinho.
10. Selecione os grupos a incluir no Perfil do Carrinho e, em seguida, selecione **Selecionar**.
11. No painel **Criar Associação**, selecione **Guardar** para guardar o Perfil do Carrinho.

O perfil será criado e apresentado no painel Lista de perfis.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>Passo 7 – atribuir o Perfil do Carrinho a turmas

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
4. No painel **Configuração do dispositivo**, selecione **Monitorizar** > **Estado da atribuição**.
5. No painel **Estado da atribuição**, selecione o **Perfil do Carrinho** que criou.
6. No painel **Perfil do Carrinho**, selecione **Atribuições** e, em **Incluir**, selecione **Selecionar grupos para incluir**.
7. Selecione as turmas para as quais será direcionado o perfil do carrinho (não selecione um grupo) e, em seguida, selecione **Selecionar**. 
8. Quando terminar, selecione **Guardar**.

A atribuição fica concluída e o Intune implementa o perfil de Sala de Aula aos dispositivos visados com base na atribuição de sala de aula.

## <a name="next-steps"></a>Passos Seguintes

Agora, os estudantes podem partilhar dispositivos entre si e selecionar qualquer iPad numa sala de aula, iniciar sessão com um PIN e personalizá-lo com os seus conteúdos. Para obter mais informações sobre iPads Partilhados, veja o [site da Apple](https://www.apple.com/education/it/).
