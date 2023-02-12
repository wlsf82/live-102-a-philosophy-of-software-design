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

### Bandeiras vermelhas - _red flags_

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
> “Dependências levam à amplificação da mudança e alta carga cognitiva. A obscuridade cria desconhecidos desconhecidos (o que você não sabe que não sabe) e também contribui à carga cognitiva. Se pudermos encontrar técnicas para minimizar dependências e obscuridade, então poderemos reduzir a complexidade do software.”

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

TBD.