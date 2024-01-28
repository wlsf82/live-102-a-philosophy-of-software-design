# Live TAT - Uma filosofia de design de software

Anotações sobre o livro [_A philosophy of Software Design_](https://www.amazon.com/Philosophy-Software-Design-2nd/dp/173210221X/), do autor John Ousterhout, o qual é professor do curso de ciência da computação na universidade de Stanford, nos Estados Unidos da América.

## Prefácio

> “O problema mais fundamental da ciência da computação é a decomposição de problemas: como pegar um problema complexo e dividí-lo em partes que podem ser resolvidas de forma independente.”
>
> “Há certa evidência científica um desempenho excepcional em vários campos está mais relacionado com prática de alta-qualidade do que habilidade nata“. Referência ao livro Talent is Overrated.
>
>“A habilidade de design é o que separa grande programadores da média.”

### Abordagem

> “Em uma classe de Inglês, estudantes usam um processo iterativo, onde eles escrevem um rascunho, recebem feedback, e então, reescrevem para fazer melhorias. No curso CS190, os estudantes desenvolvem um substancial pedaço de software do zero. Então, eles passam por extensas revisões de código para identificar problemas de design e revisam seus projetos para corrigir tais problemas. Isso ajuda aos estudantes verem como seus códigos podem ser melhorados aplicando princípios de design.”
>
> “É difícil para os estudantes entender idéias abstratas. Eles aprendem melhor escrevendo código, cometendo erros e percebendo como seus erros e subsequentes correções se relacionam aos princípios.”
>
> “Eu já li um considerável montante de código escrito por outras pessoas, o que me expês à uma variedade de abordagens, boas e ruins.“
>
> “Uma conversa sobre design de software.”
>
> “O objetivo principal é reduzir a complexidade.”

## Capítulo 1 - Introdução (É tudo uma questão de complexidade)

> “A maior limitação na escrita de software está em nossa habilidade de entender o sistema que estamos criando. A medida que o programa evolui e adquire novas funcionalidades, ele se torna complicado, com sutis dependências entre seus componentes. Com o tempo, a complexidade acumula e fica cada vez mais difícil para os/as programadores(as) se manterem atualizados com todos os fatores relevantes enquanto eles modificam o sistema. Isso desacelera o desenvolvimento e gera bugs, o que desacelera o desenvolvimento ainda mais e aumenta seus custos. A complexidade cresce inevitavelmente ao longo da vida de qualquer programa. Quanto maior for o programa, e quanto maior for o número de pessoas que trabalham no mesmo, mais difícil de gerenciar a complexidade.”
>
> “A complexidade vai aumentar de qualquer forma ao longo do tempo, apesar de nossos melhores esforços, mas um design simples nos permite construir sistemas grandes e poderosos antes que a complexidade se torne um incômodo.”
>
> “Elimine a complexidade tornando o código mais simples e óbvio.”
>
> “A segunda abordagem para combater a complexidade é encapsular a mesma, de forma que os/as programadores(as) possam no sistema sem a necessidade de serem expostas à sua complexidade de uma só vez.”
>
> “Design modular”
>
> “O design de software é um processo contínuo que abrange todo o ciclo de vida de um software.”
>
> “Não é possível visualizar com clareza o suficiente o design de um sistema grande a fim de entender todas suas implicações, até você construir alguma coisa.”
>
> “O design inicial terá vários problemas. Tais problemas não são aparentes até que a implemtação tenha começado.”
>

### Desenvolvimento ágil

> “O design inicial é focado em um pequeno pedaço da funcionalidade principal. Este pedaço é desenhado, implementado e verificado. Problemas com o design original são encontrados e corrigidos, e algumas novas funcionalidades são desenhadas, implementadas e verificadas. Cada iteração expõe problemas sobre o design existente, os quais são corrigidos antes do início do próximo grupo de funcionalidades serem desenhadas. Ao espalhar o design dessa forma, problemas com o design inicial podem ser corrigidos enquanto o sistema ainda é pequeno; novas funcionalidades se beneficiam da experiência ganha durante o desenvolvimento de prévias funcionalidades e então elas tem menos problemas.”
>
> “A abordagem incremental funciona para software pois software é maleável o suficiente para permitir significativas mudanças de design durante a implementação.”
>
> “Desenvolvimento incremental significa que o design do software nunca está pronto. O design acontece continuamente ao longo da vida de um sistema.”
>
> “Desenvolvimento incremental também significa redesign contínuo. O design inicial para um sistema ou componente na maioria das vezes não é o melhor; a experiência inevitavelmente mostra melhores formas de fazer as coisas.”

### Objetivos do Livro

> 1) “O que significa complexidade, por que isso é importante e como você pode reconhecer quando um programa tem complexidade desnecessária?”
>
> 2) “Técnicas que você pode usar durante o processo de desenvolvimento de software para minimizar a complexidade.”
>
> “Quando você lê o código dos outros, pense sobre… como isso se relaciona com a complexidade do código.”

#### Sinal de alerta - _red flag_

> “Quanto mais alternativas você tentar antes de corrigir um problema, mais você aprenderá.”
>
>“Indo longe demais”
>
> “Reconheça quando você estiver exagerando com uma coisa boa.”

## Capítulo 2 - A natureza da complexidade

> “A habilidade em reconhecer complexidade é uma habilidade de design crucial.”
>
> “É mais fácil dizer que um design é simples do que criar um design simples, mas uma vez que você reconhece que um sistema é muito complicado, você pode usar tal habilidade para guiá-lo(a) em direção à simplicidade.”

### Definição de complexidade

> “Complexidade é qualquer coisa relacionada com a estrutura do software que torna difícil entendê-lo e modificá-lo.”
>
> “A complexidade é mais aparece para os leitores do que os escritores. Se você escreve um pedaço de código e ele parece simples para você, mas outra pessoas o consideram complexo, então ele é complexo.”
>
> “O seu trabalho como desenvolvedor(a) não é somente criar código com o qual você pode trabalhar facilmente, mas criar código com o qual outros possam também trabalhar facilmente.”

### Sintomas da complexidade

> “Amplificação da mudança: o primeiro sintoma da complexidade é quando uma mudança que parece trivial requer modificações em códigos em diferentes partes do sistema.”
>
> “Um dos objetivos de um bom design é reduzir a quantidade de código que é afetada por cada decisão de design, para que mudanças de design não exijam mudanças em várias partes do código.”
>
> “Carga cognitiva: Quanto um(a) desenvolvedor(a) precisa saber para concluir uma tarefa.”
>
> “Algumas vezes, uma abordagem que exige mais linhas de código é na verdade mais simples, por reduzir a carga cognitiva.”
>
> “O que não sabemos que não sabemos: das três manifestações de complexidade, o que não sabemos que não sabemos são as piores. Algo que você não sabe que não sabe significa que há algo que você precisa saber, no entanto, não há outra forma de você descobrir o que é, ou mesmo se há um problema. Você não descobrirá até que os bugs apareçam depois de fazer uma alteração.”

### Causas da complexidade

> “Dependências e obscuridade”
>
> “Uma dependência existe quanto um pedaço do código não pode ser entendido ou modificado de forma isolada; o código se relaciona de alguma forma com outro código, e o outro código deve ser considerado e/ou modificado se o código que queremos mudar realmente muda.”
>
> “A segunda causa da complexidade é a obscuridade. A obscuridade ocorre quando partes importantes não são óbvias… Exemplo: um nome de variável que é tão genérico que não trás informações úteis. Ou, a documentação para uma variável nãoespecifica sua unidade, não deixando outra forma de descobrir é procurar no código por outras lugares que à usam. A obscuridade está frequentemente relacionada com dependências, quando não é óbvio que uma dependência existe.”
>
> “Se um sistema tem um design limpo e óbvio, então necessitará de menos documentação. A necessidade de muita documentação é frequentemente uma bandeira vermelha de que o design não está certo. A melhor forma de reduzir a obscuridade é simplificar o design do sistema.”
>
> “Dependências levam à amplificação da mudança e alta carga cognitiva. A obscuridade cria incgógitas desconhecidas (o que você não sabe que não sabe) e também contribui à carga cognitiva. Se pudermos encontrar técnicas para minimizar dependências e obscuridade, então poderemos reduzir a complexidade do software.”

### A complexidade é incremental

> “A complexidade acumula rapidamente.”

### Conclusão

> “O ponto principal é que a complexidade torna mais difícil e arriscado modificar uma base de código existente.”

## Capítulo 3 - Código funcionando não é o suficiente

> "Se você quer um bom design, você deve ter uma abordagem mais estratégica, onde você investe tempo em produzir um design limpo e corrigir problemas."

### Programação tática

> "A programacão tática torna praticamente impossível produzir um bom design do sistema."
>
> "A complexidade é incremental."

### Programação estratégica

> "Código funcionando não é o suficiente. Não é aceitável introduzir complexidades a fim de terminar uma tarefa mais rápido. O mais importante é a estrutura de longo-prazo do sistema."
>
> "O seu trabalho mais importante como desenvolvedor(a) é facilitar as futuras extensões."
>
> "O seu principal objetivo deve ser produzir um bom design, que também funciona. Isto é programação estratégica."
>
> "A programação estratégica requer uma mentalidade de investimento."
>
> "Tais investimentos irão torná-lo(a) um pouco mais lento(a) no curto-prazo, mas irão torná-lo(a) mais rápido(a) no longo-prazo."
>
> "A escrita de documentação é outro exemplo de um investimento proativo."
>
> "Não importa o quanto você investe no início, inevitavelmente haverão erros em suas decisões de design. Com o tempo, tais erros se tornarão óbvios. Quando você descobre um problema de design, não ignore-o ou faça um remendo; Invista um pouco mais de tempo em corrigí-lo. Se você programa de forma estratégica, continuamente você fará pequenas melhorias no design do sistema.

### Quanto investir?

> "O design ideal tende a surgir em pedaços."
>
> "Sugiro gastar entre 10 e 20% do tempo total de desenvolvimento em investimentos."
>
> "Seu projeto inicial irá levar de 10 a 20% mais tempo do que iria se você usasse uma abordagem puramente tática. O tempo extra irá resultar em um melhor design de software e você vai começar a experimentar os benefícios em alguns meses. Não demorará muito para que você esteja desenvolvendo 10 a 20% mais rápido do que você estaria se tivesse programado taticamente. Neste ponto, seus investimentos vem de graça."

### _Startups_ e investimentos

> "Um dos mais importantes fatores para o sucesso de uma empresa é a qualidade dos seus engenheiros. A melhor forma de reduzir custos de desenvolvimento é contratar grandes desenvolvedores(as)."
>
> "Os melhores engenheiros se preocupam profundamente com um bom design."
>
> "Ênfase em alta-qualidade e bom design."
>
> "Construir produtos sofisticados que resolvem problemas complexos com um software confiável."
>
> "É muito mais divertido trabalhar em uma empresa que se preocupa com design de software e tem uma base de código limpa."

### Conclusão

> "A abordagem mais efetiva é aquela onde todo engenheiro faz pequenos investimentos contínuos em um bom design.

## Capítulo 4 - Módulos devem ser profundos

Uma das técnicas mais importantes para gerenciar a complexidade do software é projetar sistemas de modo que os/as desenvolvedores/as só precisem enfrentar uma pequena fração da complexidade geral em um determinado momento.

### Design modular

No design modular, um sistema de software é decomposto em uma coleção de módulos relativamente independentes.

O objetivo do design modular é minimizar as dependências entre os módulos. Para gerenciar dependências, pensamos em cada módulo em duas partes: uma interface e uma implementação. A interface consiste em tudo que um/uma desenvolvedor/ad trabalhando em um módulo diferente deve saber para usar o módulo determinado.

A interface descreve o que o módulo faz, mas não como o faz. A implementação consiste no código que cumpre as promessas feitas pela interface.

Um/uma desenvolvedor/a não deve precisar entender as implementações de um módulo diferente daquele em que está trabalhando.

Um módulo é qualquer unidade de código que possui uma interface e uma implementação.

Os melhores módulos são aqueles cujas interfaces são muito mais simples que suas implementações.

Uma interface simples minimiza a complexidade que um módulo impõe ao resto do sistema.

Se um módulo for modificado de uma forma que não altere sua interface, nenhum outro módulo será afetado pelas modificações. Se a interface de um módulo for muito mais simples que sua implementação, haverá muitos aspectos do módulo que poderão ser alterados sem afetar outros módulos.

### O que é uma interface?

A interface formal de um método é sua assinatura, que inclui os nomes e tipos de seus parâmetros, o tipo de seu valor de retorno e informações sobre exceções lançadas pelo método.

A interface formal de uma classe consiste na assinatura de todos os seus métodos públicos, além dos nomes e tipos de quaisquer variáveis públicas.

Um dos benefícios de uma interface claramente especificada é que ela indica exatamente o que os desenvolvedores precisam saber para usar o módulo associado. Isso ajuda a eliminar as “incógnitas desconhecidas”.

### Abstrações

Uma abstração é uma visão simplificada de qualquer entidade, que omite detalhes sem importância. As abstrações são úteis porque tornam mais fácil pensar e manipular coisas complexas.

Na programação modular, cada módulo fornece uma abstração na forma de sua interface. A interface apresenta uma visão simplificada da funcionalidade do módulo; os detalhes da implementação não são importantes do ponto de vista da abstração do módulo, portanto são omitidos da interface.

A palavra “sem importância” é crucial. Quanto mais detalhes sem importância forem omitidos de uma abstração, melhor.

Uma abstração pode dar errado de duas maneiras. Primeiro, pode incluir detalhes que não são realmente importantes; o que aumenta a carga cognitiva dos/as desenvolvedores/as que usam a abstração. A segunda é a obscuridade: os/as desenvolvedores/as que olham apenas para a abstração não terão todas as informações necessárias para usar a abstração corretamente.

A chave para projetar abstrações é entender o que é importante e procurar designs que minimizem a quantidade de informações importantes.

### Módulos profundos

Os melhores módulos são aqueles que fornecem funcionalidades poderosas, mas possuem interfaces mais simples.

Os melhores módulos são profundos: eles permitem que muitas funcionalidades sejam acessadas por meio de uma interface simples. Um módulo superficial é aquele com uma interface relativamente complexa, mas sem muita funcionalidade: não esconde muita complexidade.

Os melhores módulos são profundos: eles possuem muitas funcionalidades escondidas atrás de uma interface simples. Um módulo profundo é uma boa abstração porque apenas uma pequena fração de sua complexidade interna é visível para seus usuários.

A profundidade dos módulos é uma forma de pensar sobre custo versus benefício. O custo de um módulo (em termos de complexidade do sistema) é a sua interface. A interface de um módulo representa a complexidade que o módulo impõe ao resto do sistema: os menores são aqueles com maior benefício e menor custo. Interfaces são boas, mas interfaces maiores não são necessariamente melhores!

Módulos profundos, como Unix I/O e _garbade collectors_, fornecem abstrações poderosas porque são fáceis de usar, mas ocultam uma complexidade significativa de implementação.

### Módulos superficiais

Um módulo superficial é aquele cuja interface é relativamente complexa em comparação com a funcionalidade que fornece.

A complexidade de uma interface de lista vinculada é quase tão grande quanto a complexidade de sua implementação.

Exemplo:

```
private void addNullValueForAttribute(String attribute) {
    data.put(attribute null);
}
```

São necessários ainda mais pressionamentos de tecla para invocar o método do que seria necessário para manipular a variável de dados diretamente. O método adiciona complexidade (na forma de uma nova interface para os/as desenvolvedores/as aprenderem), mas não oferece benefícios compensatórios.

#### Sinal de alerta (_red flag_): módulos superficiais

> Um módulo superficial é aquele cuja interface é complicada em relação à funcionalidade que fornece. Módulos superficiais não ajudam muito na batalha contra a complexidade, porque o benefício que eles oferecem (não ter que aprender como funcionam internamente) é anulado pelo custo de aprendizado e uso de suas interfaces. Módulos pequenos tendem a ser superficiais.

### Classitis

Freqüentemente, os/as alunos/as aprendem que a coisa mais importante no design de classes é dividir classes maiores em classes menores. O mesmo conselho é frequentemente dado sobre métodos.

Essa abordagem resulta em um grande número de classes e métodos superficiais, que adicionam complexidade geral ao sistema.

O extremo da abordagem “as classes devem ser pequenas” é uma síndrome que chamo de classitis.

Classes pequenas também resultam em um estilo de programação detalhado, devido ao padrão exigido para cada classe.

### Exemplos: Java e Unix I/O

As interfaces devem ser projetadas para tornar o caso comum o mais simples possível.

### Conclusão

Ao separar a interface de um módulo de sua implementação, podemos ocultar a complexidade da implementação do resto do sistema. Os usuários de um módulo precisam apenas entender a abstração fornecida por sua interface. A questão mais importante no design de classes e outros módulos é torná-los profundos, para que tenham interfaces simples para os casos de uso comuns, mas ainda assim forneçam funcionalidades significativas. Isso maximiza a quantidade de complexidade oculta.

## Capítulo 5 - Ocultação (e vazamento) de informações

Técnicas para a criação de módulos profundos

### Ocultação de informações

A técnica mais importante para obter módulos profundos é ocultar informações.

A ideia básica é que cada módulo encapsula alguns conhecimentos, que representam decisões de design. O conhecimento está embutido na implementação do módulo, mas não aparece em sua interface, portanto não é visível para outros módulos.

Exemplo:

- Como analisar documentos JSON

As informações ocultas incluem estruturas de dados e algoritmos relacionados ao mecanismo.

A ocultação de informações reduz a complexidade de duas maneiras. Primeiro, simplifica a interface para um módulo. A interface reflete uma visão mais simples e abstrata da funcionalidade do módulo e oculta os detalhes; isso reduz a carga cognitiva dos/as desenvolvedores/as que usam o módulo. Em segundo lugar, a ocultação de informações facilita a evolução do sistema. Se uma informação estiver oculta, não há dependências dessa informação fora do módulo que contém a informação, portanto, uma alteração de design relacionada a essa informação afetará apenas um módulo.

Ao projetar um novo módulo, você deve pensar cuidadosamente sobre quais informações podem estar ocultas nesse módulo. Se você puder ocultar mais informações, também poderá simplificar a interface do módulo, e isso torna o módulo mais profundo.

Nota: ocultar variáveis e métodos em uma classe declarando-os privados não é a mesma coisa que ocultar informações. Elementos privados podem ajudar na ocultação de informações, pois impossibilitam que os itens sejam acessados diretamente de fora da classe. No entanto, as informações sobre o item privado ainda podem ser expostas por meio de métodos públicos, como métodos _getter_ e _setter_. Quando isso acontece, a natureza e o uso das variáveis ficam tão expostos como se as variáveis fossem públicas.

A melhor forma de ocultar informações é quando as informações ficam totalmente ocultas dentro de um módulo, de forma que sejam irrelevantes e invisíveis para os usuários do módulo.

### Vazamento de informação

O oposto de ocultar informações é o vazamento de informações. O vazamento de informações ocorre quando uma decisão de design é refletida em vários módulos. Isto cria uma dependência entre os módulos: qualquer alteração nessa decisão de design exigirá alterações em todos os módulos envolvidos.

Interfaces mais simples tendem a se correlacionar com uma melhor ocultação de informações.

O vazamento de informações é um dos sinais de alerta mais importantes no design de software. Uma das melhores habilidades que você pode aprender como designer de software é um alto nível de sensibilidade ao vazamento de informações.

Se as classes afetadas forem relativamente pequenas e estiverem intimamente ligadas às informações vazadas, pode fazer sentido fundi-las em uma única classe. Outra abordagem possível é extrair as informações de todas as classes afetadas e criar uma nova classe que encapsule apenas essas informações. No entanto, essa abordagem só será eficaz se você encontrar uma interface simples que abstraia os detalhes.

### Decomposição temporal

Na decomposição temporal, a estrutura de um sistema corresponde à ordem temporal em que as operações ocorrerão.

#### Sinal de alerta (_red flag_):

> O vazamento de informações ocorre quando o mesmo conhecimento é usado em vários locais, como duas classes diferentes que entendem o formato de um determinado tipo de arquivo.

É fácil cair na armadilha da decomposição temporal, porque a ordem em que as operações devem ocorrer geralmente está em sua mente quando você codifica. Entretanto, a maioria das decisões de design se manifesta em vários momentos diferentes ao longo da vida da aplicação; como resultado, a decomposição temporal muitas vezes resulta em vazamento de informações.

Ao projetar módulos, concentre-se no conhecimento necessário para executar cada tarefa, não na ordem em que as tarefas ocorrem.

#### Sinal de alerta (_red flag_):

> Na decomposição temporal, a ordem de execução é refletida na estrutura do código: operações que acontecem em momentos diferentes estão em métodos e classes diferentes. Se o mesmo conhecimento for usado em diferentes pontos da execução, ele será codificado em vários locais, resultando em vazamento de informações.

### Exemplo: muitas classes

O erro mais comum cometido pelos alunos foi dividir seu código em um grande número de classes superficiais, o que levou ao vazamento de informações entre as classes.

Muitas vezes, a ocultação de informações pode ser melhorada tornando a classe um pouco maior. Uma razão para fazer isso é reunir todo o código relacionado a um recurso específico, de modo que a classe resultante contenha tudo relacionado a esse recurso.

### Exemplo: Tratamento de parâmetros HTTP

A ocultação de informações resultou em APIs mais simples para o código usando o módulo HTTP.

É importante evitar ao máximo expor estruturas de dados internas.

### Exemplo: padrões em respostas HTTP

O erro mais comum cometido pelos alunos nesta área foi a definição inadequada de padrões.

Os padrões ilustram o princípio de que as interfaces devem ser projetadas para tornar o caso comum o mais simples possível. Eles também são um exemplo de ocultação parcial de informações: no caso normal, o _caller_ não precisa estar ciente da existência do item padrão. Nos raros casos em que um _caller_ precisa substituir um padrão, ele terá que saber o valor e poderá invocar um método especial para modificá-lo.

Sempre que possível, as classes devem “fazer a coisa certa” sem serem explicitamente solicitadas. Os padrões são um exemplo disso.

Os melhores recursos são aqueles que você obtém sem saber que eles existem.

#### Sinal de alerta (_red flag_):

> Se a API do recurso comumente usado forçar os usuários a aprender sobre outros recursos que raramente são usados, isso aumentará a carga cognitiva dos usuários que não precisam dos recursos raramente usados.

### Informações escondidas dentro de uma classe

Tente projetar os métodos privados dentro de uma classe de modo que cada método encapsule alguma informação ou capacidade e oculte-a do resto da classe. Além disso, tente minimizar o número de locais onde cada variável de instância é usada. Algumas variáveis podem precisar ser acessadas amplamente em toda a classe, mas outras podem ser necessárias apenas em alguns lugares; se você puder reduzir o número de locais onde uma variável é usada, eliminará dependências dentro da classe e reduzirá sua complexidade.

### Indo longe demais

Se as informações forem necessárias fora do módulo, você não deverá ocultá-las.

Como um/uma "designer" de software, seu objetivo deve ser minimizar a quantidade de informações necessárias fora de um módulo; por exemplo, se um módulo puder ajustar automaticamente sua configuração, isso é melhor do que expor parâmetros de configuração. Mas é importante reconhecer quais informações são necessárias fora de um módulo e garantir que elas sejam expostas.

### Conclusão

A ocultação de informações e os módulos profundos estão intimamente relacionados. Se um módulo oculta muitas informações, isso tende a aumentar a quantidade de funcionalidades fornecidas pelo módulo, ao mesmo tempo que reduz sua interface. Isso torna o módulo mais profundo. Por outro lado, se um módulo não oculta muitas informações, então ele não possui muitas funcionalidades ou possui uma interface complexa; de qualquer forma, o módulo é superficial.

Ao decompor um sistema em módulos, procure não se deixar influenciar pela ordem em que as operações ocorrerão em tempo de execução; isso o/a conduzirá ao caminho da decomposição temporal, o que resultará em vazamento de informações e módulos superficiais. Em vez disso, pense nos diferentes conhecimentos necessários para realizar as tarefas de sua aplicação e projete cada módulo para encapsular alguns desses conhecimentos. Isso produzirá um design limpo e simples com módulos profundos.

## Capítulo 6 - Módulos de uso geral são mais profundos

Uma das decisões mais comuns que você enfrentará ao projetar um novo módulo é implementá-lo de maneira geral ou especial. Alguns poderão argumentar que se deve adoptar uma abordagem de objetivo geral, na qual se implementa um mecanismo que pode ser usado para resolver uma vasta gama de problemas, e não apenas aqueles que são importantes hoje em dia. Neste caso, o novo mecanismo poderá encontrar utilizações imprevistas no futuro, poupando assim tempo.

Por outro lado, sabemos que é difícil prever as necessidades futuras de um sistema de software; portanto, uma solução de uso geral pode incluir recursos que nunca serão realmente necessários. Além disso, se você implementar algo de propósito muito geral, pode não ser um bom trabalho para resolver o problema específico que você tem hoje. Como resultado, alguns podem argumentar que é melhor focar nas necessidades de hoje, construindo apenas o que você sabe que precisa e especializando-o para a forma como você planeja usá-lo hoje. Se você adotar uma abordagem de propósito especial e descobrir usos adicionais posteriormente, poderá sempre refatorá-la para torná-la de uso geral. A abordagem de propósito especial parece consistente com uma abordagem incremental ao desenvolvimento de software.

### Torne as aulas de uso geral

O ponto ideal é implementar novos módulos de uma forma um tanto geral. A frase "de uma forma um tanto geral" significa que a funcionalidade do módulo deve refletir suas necessidades atuais, mas sua interface não. Em vez disso, a interface deve ser geral o suficiente para suportar múltiplos usos. Essa interface deve ser fácil de usar para as necessidades atuais, sem estar vinculada especificamente a elas.

O benefício mais importante (e talvez surpreendente) da abordagem de propósito geral é que ela resulta em interfaces mais simples e profundas do que uma abordagem de propósito especial. A abordagem de uso geral também pode economizar tempo no futuro, se você reutilizar a classe para outros fins. No entanto, mesmo que os módulos sejam utilizados apenas para o seu propósito original, a abordagem de propósito geral é ainda melhor devido à sua simplicidade.

### Exemplo: classificando texto para um editor

Os alunos provavelmente pensaram que seria mais fácil implementar a interface do usuário se os métodos da classe texto correspondessem aos recursos visíveis aos usuários. Na realidade, porém, essa especialização proporcionou poucos benefícios para o código da interface do usuário e criou uma alta carga cognitiva para os/as desenvolvedores/as que trabalham na interface do usuário ou na classe de texto.

Muitos dos métodos, como `delete`, foram invocados apenas em um único local.

Um dos objetivos do design de classes é permitir que cada classe seja desenvolvida de forma independente.

### Uma API de uso mais geral

Com a API de texto de uso geral, o código para implementar a interface do usuário é um pouco mais longo do que com a abordagem original usando uma API de texto especializada. No entanto, o novo código é mais óbvio que o código antigo.

A abordagem de propósito geral tem menos código geral do que a abordagem especializada, pois substitui um grande número de métodos de propósito especial na classe de texto por um número menor de métodos de propósito geral.

### A generalidade leva a uma melhor ocultação de informações

Colocar o método na classe de texto apenas torna mais difícil para os/as desenvolvedores/as de interface de usuário obter as informações de que precisam.

Quando os detalhes são importantes, é melhor torná-los explícitos e tão óbvios quanto possível.

### Perguntas para se questionar a si mesmo

**Qual é a interface mais simples que cobrirá todas as minhas necessidades atuais?** Se você reduzir o número de métodos em uma API sem reduzir seus recursos gerais, provavelmente estará criando métodos de uso mais geral.

Reduzir o número de métodos só faz sentido desde que a API de cada método individual permaneça simples.

**Em quantas situações esse método será utilizado?** Se um método for projetado para um uso específico, isso é um sinal de alerta de que ele pode ter um propósito muito especial.

**Esta API é fácil de usar para minhas necessidades atuais?** Esta pergunta pode ajudá-lo/a a determinar quando você foi longe demais ao tornar uma API simples e de uso geral. Se você tiver que escrever muito código adicional para usar uma classe para seu propósito atual, isso é um sinal de alerta de que a interface não fornece a funcionalidade correta.

### Conclusão

As interfaces de uso geral têm muitas vantagens sobre as de uso especial. Elas tendem a ser mais simples, com menos métodos mais profundos. Eles também fornecem uma separação mais limpa entre as classes. Tornar seus módulos de uso geral é uma das melhores maneiras de reduzir a complexidade geral do sistema.
