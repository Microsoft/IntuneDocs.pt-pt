---
title: Definições de Wi-Fi para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de Wi-Fi com as definições de Wi-Fi para dispositivos com o Windows 10 ou posterior no Microsoft Intune. Pode configurar as Definições básicas ou as definições de nível empresarial.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/8/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bbd90b5a317629bd5b4d87b619d89023053518d
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884247"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Adicionar definições de Wi-Fi para dispositivos Windows 10 e posteriores no Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos com o Windows 10 e posterior. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic-profile"></a>Perfil básico

- **Tipo de Wi-Fi**: Selecione **Básico**. 

- **Nome do Wi-Fi (SSID)** : Abreviação do identificador do conjunto de serviços. Este valor é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores só veem o **Nome da ligação** configurado por si quando selecionam a ligação.

- **Nome da conexão**: Insira um nome amigável para esta conexão Wi-Fi. O texto que introduziu é o nome que os utilizadores veem quando procuram as ligações disponíveis no respetivo dispositivo.

- **Conectar automaticamente quando estiver no intervalo**: Quando **Sim**, os dispositivos se conectam automaticamente quando estão no alcance desta rede. Se **Não**, os dispositivos não ligam automaticamente.

  - **Conecte-se a uma rede preferencial, se disponível**: Se os dispositivos estiverem no intervalo de uma rede mais preferencial, escolha **Sim** para usar a rede preferencial. Selecione **Não** para utilizar a rede Wi-Fi neste perfil de configuração.

    Por exemplo, cria uma rede Wi-Fi **ContosoCorp** e utiliza a **ContosoCorp** neste perfil de configuração. Também tem uma rede Wi-Fi **ContosoGuest** ao alcance. Quando os seus dispositivos empresariais estiverem ao alcance, pretende que os mesmos liguem automaticamente à **ContosoCorp**. Neste cenário, defina a propriedade **Ligar à rede mais preferida, se estiver disponível** para **Não**.

  - **Conecte-se a essa rede, mesmo quando ela não estiver transmitindo seu SSID**: Escolha **Sim** para que o perfil de configuração se conecte automaticamente à sua rede, mesmo quando a rede estiver oculta (ou seja, seu SSID não é transmitido publicamente). Selecione **Não** se não quiser que este perfil de configuração se ligue à sua rede oculta.

- **Limite de conexão limitada**: Um administrador pode escolher como o tráfego da rede é medido. Com base nesta definição, as aplicações podem ajustar o respetivo comportamento de tráfego de rede. As opções são:

  - **Irrestrito**: Predefinição. A ligação não é limitada e não há restrições sobre o tráfego.
  - **Corrigido**: Use esta opção se a rede estiver configurada com limite fixo para o tráfego de rede. Uma vez atingido este limite, o acesso à rede será proibido.
  - **Variável**: Usado esta opção se o tráfego de rede for cobrado por byte (custo por byte).

- **Tipo de segurança sem fio**: Insira o protocolo de segurança usado para autenticar dispositivos na sua rede. Suas opções são:
  - **Abrir (sem autenticação)** : Use esta opção somente se a rede não for segura.
  - **WPA/WPA2-Pessoal**: Uma opção mais segura e normalmente é usada para conectividade Wi-Fi. Para obter mais segurança, também pode introduzir uma chave pré-partilhada, palavra-passe ou chave de rede. 

    - **Chave pré-compartilhada** (PSK): Opcional. Apresentado quando seleciona **WPA/WPA2-Personal** como o tipo de segurança. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK. Introduza uma cadeia de carateres que tenha entre 8 e 64 carateres. Se a sua palavra-passe ou chave de rede tiver 64 carateres, introduza os carateres hexadecimais.
    
      > [!NOTE]
      > Ao guardar o perfil Wi-Fi, o valor PSK que introduziu não é apresentado por motivos de segurança. A marca d'água da chave pré-partilhada continua a mostrar a indicação **Não configurado**, apesar de o PSK estar guardado no perfil. Para alterar o PSK, introduza uma nova chave e guarde o perfil. Se guardar o PSK, edite a política, deixe o PSK em branco e o PSK existente continuará a ser utilizado.

- **Configurações de proxy da empresa**: Escolha usar as configurações de proxy na sua organização. As opções são:
  - **Nenhum**: Nenhuma configuração de proxy está configurada.
  - **Configurar manualmente**: Insira o **endereço IP do servidor proxy** e seu **número de porta**.
  - **Configurar automaticamente**: Insira a URL apontando para um script PAC (configuração automática de proxy). Por exemplo, introduza `http://proxy.contoso.com/proxy.pac`.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="enterprise-profile"></a>Perfil empresarial

- **Tipo de Wi-Fi**: Escolha **Enterprise**. 

- **Nome do Wi-Fi (SSID)** : Abreviação do identificador do conjunto de serviços. Este valor é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores só veem o **Nome da ligação** configurado por si quando selecionam a ligação.

- **Nome da conexão**: Insira um nome amigável para esta conexão Wi-Fi. O texto que introduziu é o nome que os utilizadores veem quando procuram as ligações disponíveis no respetivo dispositivo.

- **Conectar automaticamente quando estiver no intervalo**: Quando **Sim**, os dispositivos se conectam automaticamente quando estão no alcance desta rede. Se **Não**, os dispositivos não ligam automaticamente.
  - **Conecte-se a uma rede preferencial, se disponível**: Se os dispositivos estiverem no intervalo de uma rede mais preferencial, escolha **Sim** para usar a rede preferencial. Selecione **Não** para utilizar a rede Wi-Fi neste perfil de configuração.

    Por exemplo, cria uma rede Wi-Fi **ContosoCorp** e utiliza a **ContosoCorp** neste perfil de configuração. Também tem uma rede Wi-Fi **ContosoGuest** ao alcance. Quando os seus dispositivos empresariais estiverem ao alcance, pretende que os mesmos liguem automaticamente à **ContosoCorp**. Neste cenário, defina a propriedade **Ligar à rede mais preferida, se estiver disponível** para **Não**.

  - **Conecte-se a essa rede, mesmo quando ela não estiver transmitindo seu SSID**: Escolha **Sim** para que o perfil de configuração se conecte automaticamente à sua rede, mesmo quando a rede estiver oculta (ou seja, seu SSID não é transmitido publicamente). Selecione **Não** se não quiser que este perfil de configuração se ligue à sua rede oculta.

- **Limite de conexão limitada**: Um administrador pode escolher como o tráfego da rede é medido. Com base nesta definição, as aplicações podem ajustar o respetivo comportamento de tráfego de rede. As opções são:

  - **Irrestrito**: Predefinição. A ligação não é limitada e não há restrições sobre o tráfego.
  - **Corrigido**: Use esta opção se a rede estiver configurada com limite fixo para o tráfego de rede. Uma vez atingido este limite, o acesso à rede será proibido.
  - **Variável**: Usado esta opção se o tráfego de rede for custado por byte.

- **SSO (logon único)** : Permite configurar o SSO (logon único), onde as credenciais são compartilhadas para o computador e a entrada da rede Wi-Fi. Suas opções são:
  - **Desabilitar**: Desabilita o comportamento de SSO. O utilizador tem de efetuar a autenticação na rede separadamente.
  - **Habilitar antes do usuário entrar no dispositivo**: Use o SSO para autenticar na rede logo antes do processo de entrada do usuário.
  - **Habilitar após o usuário entrar no dispositivo**: Use o SSO para autenticar a rede imediatamente após a conclusão do processo de entrada do usuário.
  - **Tempo máximo para autenticar antes do tempo limite**: Insira o número máximo de segundos a aguardar antes de autenticar na rede, de 1-120 segundos.
  - **Permitir que o Windows solicite credenciais de autenticação adicionais ao usuário**: Escolher **Sim** permite que o sistema Windows solicite credenciais adicionais ao usuário se o método de autenticação exigir. Selecione **Não** para ocultar estes pedidos.

- **Habilitar cache de PMK (chave mestra de par)** : Selecione **Sim** para armazenar em cache o PMK usado na autenticação. Geralmente, esta colocação em cache permite autenticar a rede de forma a concluir mais rapidamente. Selecione **Não** para forçar o handshake de autenticação sempre que ligar à rede Wi-Fi.

  - **Tempo máximo em que um PMK é armazenado no cache**: Insira o número de minutos em que uma PMK (chave mestra de par) é armazenada no cache, de 5-1440 minutos.
  - **Número máximo de PMKs armazenados no cache**: Insira o número de chaves armazenadas no cache, de 1-255.

- **Habilitar pré-autenticação**: A pré-autenticação permite que o perfil se autentique em todos os pontos de acesso da rede no perfil antes de se conectar. Ao deslocar-se entre pontos de acesso, a pré-autenticação volta a ligar o utilizador ou os dispositivos mais rapidamente. Selecione **Sim** para o perfil autenticar todos os pontos de acesso desta rede que estejam ao alcance. Selecione **Não** para exigir que o utilizador ou dispositivo autentique cada ponto de acesso separadamente.

  - **Máximo de tentativas de pré-autenticação**: Insira o número de tentativas de autenticidade, de 1-16.

- **Tipo de EAP**: Escolha o tipo EAP (Extensible Authentication Protocol) para autenticar conexões sem fio seguras. As opções são:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **PEAP Protegido** (PEAP)

    **Definições adicionais de EAP-TLS, EAP-TTLS e PEAP**:
    
    > [!NOTE]
    > Atualmente, apenas os perfis de certificado SCEP são suportados quando utiliza um tipo de EAP. Os perfis de certificado PKCS não são suportados. Sempre que for pedido a um utilizador para introduzir um certificado, certifique-se de que seleciona um certificado SCEP.

    - **Fidedignidade do Servidor**  

      **Nomes de servidor de certificado**: Use com tipos EAP **EAP-TLS**, **EAP-TTLS**ou **PEAP** . Introduza um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) confiável. Se introduzir estas informações, pode ignorar a caixa de diálogo de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.  

      **Certificado raiz para validação do servidor**: Use com tipos EAP **EAP-TLS**, **EAP-TTLS**ou **PEAP** . Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação.  

      **Privacidade de identidade (identidade externa)** : Use com o tipo de EAP **PEAP** . Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.  

    - **Autenticação de Cliente**

      **Certificado do cliente para autenticação de cliente (certificado de identidade)** : Use com o tipo de EAP **EAP-TLS** . Selecione o perfil de certificado utilizado para autenticar a ligação.

      **Método de autenticação**: Use com o tipo de EAP **EAP-TTLS** . Selecione o método de autenticação da ligação:  

      - **Certificados**: Selecione o certificado de cliente que é o certificado de identidade apresentado ao servidor.
      - **Nome de usuário e senha**: Insira um método **não EAP (identidade interna)** para autenticação. As opções são:

        - **Palavra-passe não encriptada (PAP)**
        - **Protocolo CHAP (Challenge Handshake)**
        - **Microsoft CHAP (MS-CHAP)**
        - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      **Privacidade de identidade (identidade externa)** : Use com o tipo de EAP **EAP-TTLS** . Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Configurações de proxy da empresa**: Escolha usar as configurações de proxy na sua organização. As opções são:
  - **Nenhum**: Nenhuma configuração de proxy está configurada.
  - **Configurar manualmente**: Insira o **endereço IP do servidor proxy** e seu **número de porta**.
  - **Configurar automaticamente**: Insira a URL que aponta para um script PAC (configuração automática de proxy). Por exemplo, introduza `http://proxy.contoso.com/proxy.pac`.

- **Forçar o perfil de Wi-Fi a estar em conformidade com o padrão FIPS (FIPS)** : Escolha **Sim** ao validar em relação ao padrão FIPS 140-2. Esta norma é necessária para todas as agências governamentais federais dos EUA que utilizem sistemas de segurança baseados em criptografia para proteger informações confidenciais, mas não classificadas, armazenadas digitalmente. Selecione **Não** se não pretender a conformidade com a norma FIPS.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="use-an-imported-settings-file"></a>Utilizar um ficheiro de definições importadas

Para as definições não disponíveis no Intune, pode exportar definições de Wi-Fi de outro dispositivo com Windows. Esta exportação cria um ficheiro XML com todas as definições. Em seguida, importe este ficheiro para o Intune e utilize-o como o perfil de Wi-Fi. Veja [Exportar e importar definições de Wi-Fi para dispositivos com Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Passos seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

- Veja as definições disponíveis para o [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
- [Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas
