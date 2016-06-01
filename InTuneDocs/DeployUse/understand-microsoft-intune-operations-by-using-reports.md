---
# required metadata

title: Compreender as operações através de relatórios | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Compreender as operações do Microsoft Intune através de relatórios
Utilize as informações neste tópico para o ajudar a criar e a gerir relatórios do Microsoft Intune que fornecem informações sobre o software, o hardware e as licenças de software na sua organização.

## Utilizar Relatórios
Os relatórios do Intune fornecem informações sobre o software, o hardware e as licenças de software na sua organização. Os relatórios podem ajudar a confirmar as suas necessidades atuais e a prever despesas futuras. A área de trabalho **Relatórios** fornece as ferramentas para criar e gerir relatórios. Para obter mais informações sobre relatórios, veja [Compreender as operações do Microsoft Intune através da utilização de relatórios](understand-microsoft-intune-operations-by-using-reports.md)

### Tipos de relatório

|Tipo de relatório|Descrição|
|---------------|---------------|
|**Relatórios de atualizações**|Apresentam as atualizações de software que ocorreram nos computadores na sua organização, para além das atualizações que falharam, que estão pendentes ou que são necessárias. Para obter mais informações sobre atualizações de software, veja [Keep Windows PCs up to date with software updates in Microsoft Intune (Manter os PCs Windows atualizados com atualizações de software no Microsoft Intune)](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|
|**Relatórios de Software Detetado**|Apresentam o software instalado em computadores na sua organização que inclui as versões do software. Pode filtrar as informações apresentadas com base no fabricante do software e na categoria do software. Pode expandir as atualizações na lista para mostrar mais detalhes (como os computadores em que estão instaladas) ao clicar na seta direcional junto ao item da lista.<br /><br />Ao extinguir computadores ou alterar as respetivas associações a grupos no Intune, pode demorar alguns minutos até que estas alterações sejam refletidas no relatório de software detetado. Para dados de inventário de software mais exatos, aguarde alguns minutos após extinguir computadores ou alterar as respetivas associações a grupos antes de executar um relatório de software detetado que inclua esses computadores.|
|**Relatórios de Inventário de Computadores**|Apresentam informações sobre computadores geridos na sua organização. Utilize este relatório para planear aquisições de hardware e para saber mais sobre as necessidades de hardware de utilizadores na sua organização. Para obter mais informações sobre como trabalhar com computadores geridos, veja [Manage Windows PCs with Microsoft Intune (Gerir PCs Windows com o Microsoft Intune)](manage-windows-pcs-with-microsoft-intune.md)|
|**Relatórios de Inventário de Dispositivos Móveis**|Apresentam informações sobre os dispositivos móveis na sua organização. Pode filtrar as informações que são apresentadas com base nos grupos, se o dispositivo foi desbloqueado por jailbreak ou rooting e por sistema operativo.|
|**Relatórios de Compra de Licenças**|Apresentam os títulos de todo o software licenciado em grupos de licenças específicos, com base nos respetivos contratos de licenciamento. Se as informações de licenciamento de software não forem atualizadas há mais de 24 horas, estas são atualizadas ao gerar um relatório de licenças. Um relatório de licenças não é um cálculo exato dos títulos de software que estão a ser utilizados ou prova da conformidade com os contratos. O relatório é uma ferramenta que o pode ajudar a tomar decisões de licenciamento para a sua organização. O Intune pode não detetar alguns produtos que podem deter uma licença de volume da Microsoft. Os filtros disponíveis são:<br /><br />**Todos os contratos** mostra todos os produtos de software licenciados geridos pelo Intune.<br /><br />**Contratos de licenciamento em volume** - Mostra apenas os produtos de software do VLSC.<br /><br />**Outros contratos de licenciamento de software** - Mostra produtos de software que são geridos fora do VLSC.|
|**Relatórios de instalação de licenças**|Comparam o software instalado em computadores na sua organização com a sua cobertura de licenças atual de acordo com o Centro de Serviços de Licenciamento em Volume (VLSC). Os filtros incluem:<br /><br />**Todos os contratos** mostra todos os produtos de software licenciados geridos pelo Intune.<br /><br />**Contratos de licenciamento em volume** - Mostra apenas os produtos de software do VLSC.<br /><br />**Outros contratos de licenciamento de software** - Mostra produtos de software que são geridos fora do VLSC.|
|**Relatórios de Termos e Condições**|Mostra se os utilizadores aceitaram os termos e condições que implementou e que versão aceitaram. É possível especificar até 10 utilizadores cujas aceitações de quaisquer termos e condições que lhes foram implementados são apresentadas ou mostrar o estado de aceitação relativamente a um determinado termo implementado nos mesmos.|
|**Relatórios de Aplicações Não Compatíveis**|Apresentam informações sobre os utilizadores que têm aplicações instaladas que fazem parte das suas listas de aplicações compatíveis e não compatíveis. Utilize este relatório para encontrar utilizadores e dispositivos não compatíveis com as políticas de aplicações da sua empresa.|
|**Relatórios de Conformidade de Certificados**|Apresentam os certificados emitidos a utilizadores e dispositivos através de SCEP ou de PKCS #12 (.PFX). Utilize este relatório para localizar certificados que foram emitidos, que expiraram ou que foram revogados.|
|**Relatórios de Histórico de Dispositivos**|Apresentam um registo histórico das ações de extinção e eliminação. Utilize este relatório para ver quem iniciou ações nos dispositivos anteriormente.|
|**Relatório de Hardware do Mac OS X**|Apresenta detalhes de hardware para todos os dispositivos Mac OS X inscritos nos grupos selecionados. Para obter informações sobre o inventário recolhido a partir destes dispositivos, veja [Understand your devices with inventory in Microsoft Intune (Compreender os seus dispositivos com o inventário no Microsoft Intune)](understand-your-devices-with-inventory-in-microsoft-intune.md)|
|**Relatório de Software do Mac OS X**|Apresenta o software instalado em todos os dispositivos Mac OS X nos grupos selecionados. Este relatório lista o nome do software (como ID de pacote), o nome da versão abreviada (ou amigável), a versão e o número de dispositivos com o software instalado.|

#### Para criar um relatório

1.  Na consola de administração do Intune, clique em **Relatórios** e, em seguida, clique no tipo de relatório que pretende gerar, descrito na tabela acima.

2.  Na página **Criar Novo Relatório** , aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar que apenas o software publicado pela Microsoft seja apresentado no relatório de software detetado.

3.  Clique em **Ver Relatório** para abrir o relatório numa nova janela.

Para ordenar o relatório por qualquer uma das colunas apresentadas, clique no cabeçalho da coluna. Adicionalmente, alguns relatórios permitem expandir itens na lista para apresentar mais detalhes.

## Mais ações de relatórios
Os relatórios suportam também as seguintes ações:

|Ação|Mais informações|
|----------|--------------------|
|**Imprimir**|Num relatório aberto, clique no ícone imprimir e siga as instruções.|
|**Exportar**|Num relatório aberto, clique no ícone exportar e siga as instruções. Pode exportar um relatório para o formato de ficheiro de valores separados por vírgulas (.csv) ou HTML.|
|**Guardar**|Na página **Criar Novo Relatório** , cada utilizador pode guardar até 100 relatórios. Configure os parâmetros de relatórios conforme os seus requisitos e, em seguida, clique em **Guardar**ou em **Guardar Como** se pretender utilizar um nome diferente.|
|**Carregamento**|Na página **Criar Novo Relatório** , clique em **Carregar** para obter conjuntos de parâmetros de relatórios guardados anteriormente.|
|**Eliminar**|Na área de trabalho **Relatórios** , selecione o tipo de relatório pretendido, clique em **Carregar**e, em seguida, na lista de relatórios, clique no ícone eliminar (x) junto ao relatório.|

## Consulte Também
[Monitorização e relatórios com o Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)



<!--HONumber=May16_HO2-->


