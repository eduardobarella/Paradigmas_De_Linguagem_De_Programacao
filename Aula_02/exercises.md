[exercises.md](https://github.com/user-attachments/files/31846730/exercises.md)
# Lista de Exercícios — Evolução das Principais Linguagens de Programação

Disciplina: Paradigmas de Linguagens de Programação  
Referência: Sebesta, Capítulo 2

---

## Questão 1

Dizer que a genealogia  das linguagens é uma escada de progresso seria o mesmo que dizer que cada linguagem nova elimina e supera a anterior. Mas não é isso que acontece. Fortran e COBOL surgiram praticamente na mesma época e continuam em uso até hoje, cada uma no seu nicho. Nenhuma substituiu a outra porque foram criadas para domínios completamente diferentes.

Dois fatores explicam por que uma linguagem pode influenciar outra sem substituí-la:

O primeiro é o domínio de aplicação. Quando uma linguagem é criada para resolver um tipo específico de problema, ela desenvolve características que fazem sentido naquele contexto. Fortran foi pensada para cálculo científico, então suas estruturas de dados e operações refletem isso. COBOL foi pensada para processamento de dados comerciais, então sua sintaxe e seus registros refletem outra realidade. Uma pode influenciar a outra em detalhes de projeto, mas nenhuma vai substituir a outra enquanto os domínios forem diferentes.

O segundo fator é o custo de migração. Quando uma linguagem está enraizada em sistemas críticos há décadas, a ideia de reescrevê-los em algo novo é inviável financeiramente e tecnicamente. Então o que acontece é que novas linguagens surgem ao lado das antigas, muitas vezes absorvendo conceitos delas sem eliminá-las. COBOL ainda processa boa parte das transações bancárias do mundo, mesmo sendo considerada "antiga" por muito tempo.

---

## Questão 2

Plankalkül foi desenvolvida por Konrad Zuse entre 1943 e 1945, mas nunca chegou a ser implementada em sua época. O contexto da Segunda Guerra Mundial e o isolamento científico da Alemanha impediram que ela fosse conhecida ou usada. Mesmo assim, ela ocupa um lugar importante na história das linguagens porque demonstrou que era possível pensar em programação de forma abstrata e sistemática, bem antes de existir hardware capaz de executar algo assim.

Três recursos que ela antecipou:

O primeiro foi o uso de estruturas de dados compostas. Zuse já previa a possibilidade de organizar dados em hierarquias, algo que só se tornaria comum em outras linguagens décadas depois.

O segundo foi a atribuição com verificação de tipos. As variáveis tinham tipos associados, o que antecipava a ideia de que inconsistências de dados deveriam ser detectadas antes da execução.

O terceiro foi a previsão de iteração e subrotinas, ou seja, a repetição controlada e a separação do código em blocos reutilizáveis.

Das três, a mais importante é provavelmente a primeira. Estruturas de dados compostas são fundamentais porque permitem que o programador organize as informações de acordo com o problema, e não de acordo com as limitações físicas da memória. Sem isso, qualquer dado mais complexo precisa ser desmontado manualmente em endereços individuais, o que torna o código ilegível e difícil de manter. Zuse enxergou essa necessidade em 1945, o que é notável considerando que os computadores da época mal existiam como conceito consolidado.

---

## Questão 3

Os três sistemas representam tentativas distintas de resolver o problema de programar máquinas sem escrever tudo em código de máquina diretamente.

Short Code (1949) enfrentava o problema de que escrever em código de máquina era lento e propenso a erros. A solução foi criar um conjunto de códigos de duas letras que o programador usava, e que eram interpretados em tempo de execução, linha por linha.

Speedcoding (1953) atacava um problema diferente: a IBM 701 não tinha suporte de hardware para aritmética de ponto flutuante. A solução foi um interpretador que simulava essas operações via software, permitindo que o programador escrevesse expressões matemáticas sem se preocupar com o hardware.

O sistema A de Grace Hopper (1951 a 1953) lidava com o retrabalho de montar sub-rotinas manualmente toda vez que eram necessárias. A solução foi criar uma biblioteca de sub-rotinas que podia ser carregada e combinada automaticamente, gerando código de máquina como resultado.

Chamá-los de compiladores modernos seria impreciso porque nenhum deles fazia o que um compilador moderno faz. Short Code e Speedcoding eram interpretadores: traduziam e executavam instrução por instrução durante a execução, sem gerar nenhum programa de máquina independente. Isso os tornava muito lentos. O sistema A chegava mais perto, porque gerava código de máquina, mas operava sobre chamadas a sub-rotinas prontas, não sobre uma linguagem com expressões, tipos e estruturas de controle. Um compilador moderno analisa léxico, sintaxe e semântica, otimiza o código e gera executável. Esses três sistemas resolviam partes isoladas desse problema, não o problema como um todo.

---

## Questão 4

Quando Backus e sua equipe propuseram o Fortran em 1954, a resistência era grande. A crença dominante entre programadores era que qualquer código gerado por um tradutor automático seria inferior ao que um programador experiente escreveria à mão em código de máquina. E isso não era preconceito sem fundamento: computadores eram caros, lentos e escassos, e desperdiçar ciclos de clock tinha custo real.

O projeto Fortran foi concebido para atacar esse argumento de frente. A equipe investiu mais esforço no otimizador do que em qualquer outra parte do compilador. O objetivo era explícito: gerar código comparável ao produzido manualmente. Sem isso, ninguém adotaria a linguagem, independentemente de qualquer outra vantagem.

A relação entre os três fatores fica clara aqui. O desempenho era a única métrica que os programadores respeitavam. O custo de programação, ou seja, o tempo humano gasto escrevendo e depurando código de máquina, era visto como algo secundário, porque o hardware era o recurso escasso. Fortran virou esse argumento: se o compilador gera código bom o suficiente, você pode escrever dez vezes mais rápido e ainda ter performance aceitável. Quando os primeiros benchmarks confirmaram isso, a adoção veio rápido.

O caso do Fortran estabeleceu um padrão que se repete até hoje: toda nova abstração de programação precisa provar que o custo de abstração vale a economia de esforço humano. A prova precisou ser empírica, não teórica.

---

## Questão 5

Fortran e Lisp surgiram quase na mesma época, mas parecem vir de mundos completamente diferentes, porque de fato vêm.

Fortran foi criada para computação científica e numérica: física, engenharia, meteorologia. O dado central é o número, em geral organizado em arrays ou matrizes. O estilo de computação é imperativo: você descreve uma sequência de operações que transforma valores numéricos, usando loops explícitos e variáveis de estado.

Lisp surgiu no contexto de inteligência artificial e processamento simbólico. O dado central não é o número, mas a lista, que pode conter tanto dados quanto código. Isso é o que se chama de homoiconicidade: em Lisp, código e dado têm a mesma representação, o que permite ao programa manipular a si mesmo. O estilo de computação é funcional: problemas são resolvidos por composição de funções e recursão, sem estado mutável intermediário.

A diferença mais profunda está justamente aí. Em Fortran, dado é algo a ser calculado. Em Lisp, dado é algo a ser interpretado e transformado simbolicamente. Representar um problema de xadrez, um teorema lógico ou uma estrutura de linguagem natural é natural em Lisp e completamente fora do escopo de Fortran.

---

## Questão 6

ALGOL 60 nunca dominou o mercado. Nos Estados Unidos, Fortran e COBOL já estavam consolidados, e a IBM não tinha interesse em promover uma alternativa. Além disso, a especificação de ALGOL 60 deixou entrada e saída sem padronização, o que tornava a portabilidade real mais difícil do que parecia no papel.

Mesmo assim, ALGOL 60 é provavelmente a linguagem mais influente na história do projeto de linguagens. Três contribuições que ultrapassaram sua irrelevância comercial:

A primeira foi o escopo léxico e a estrutura de bloco. A ideia de que variáveis existem dentro de blocos delimitados e que seu escopo é determinado estaticamente pela estrutura do código é a base de praticamente toda linguagem imperativa moderna. C, Pascal, Java, Python herdam isso diretamente de ALGOL 60.

A segunda foi o uso de BNF para definir a sintaxe da linguagem. ALGOL 60 foi a primeira linguagem a ter sua gramática descrita formalmente usando a Backus-Naur Form. Desde então, toda linguagem de programação especifica sua sintaxe dessa forma, e toda disciplina de teoria de linguagens usa essa notação.

A terceira foi a passagem de parâmetros por nome, que, embora raramente usada hoje, gerou o conceito de thunk, que reaparece em linguagens funcionais como Haskell na forma de avaliação preguiçosa.

Uma linguagem pode ser muito influente sem dominar o mercado porque mercado e inovação técnica respondem a forças diferentes. Mercado responde a custo, suporte institucional e inércia. Inovação responde à qualidade das ideias. As ideias de ALGOL 60 eram boas o suficiente para que todos os seus competidores as adotassem ao longo do tempo, às vezes sem crédito explícito.

---

## Questão 7

COBOL foi criada em 1959 a partir de uma demanda explícita do Departamento de Defesa americano: uma linguagem para processamento de dados comerciais que não-programadores pudessem ler e validar. Esse requisito moldou cada decisão de design.

A legibilidade extrema de COBOL não é um defeito histórico, é uma feature pensada para o domínio. Comandos como MOVE SALARY TO NET-PAY foram escolhas deliberadas para que gerentes, auditores e analistas de negócios pudessem verificar se o código fazia o que o contrato dizia. Isso é radicalmente diferente de Fortran, onde expressões matemáticas compactas eram valorizadas. O público-alvo era completamente diferente.

Os registros hierárquicos também refletem o domínio. Dados comerciais são naturalmente estruturados: um cliente tem nome, endereço e conta; uma conta tem saldo e histórico. COBOL introduziu itens de dados com níveis numerados que permitiam descrever essa hierarquia diretamente. Essa representação antecipou o que hoje chamamos de structs ou objetos simples.

A relação com FLOW-MATIC é de herança direta. FLOW-MATIC, desenvolvida pela própria Grace Hopper em 1955, foi a primeira linguagem de alto nível orientada a negócios e em inglês. COBOL absorveu sua filosofia de legibilidade e parte de sua sintaxe. A diferença é que COBOL foi criada por um comitê multi-institucional, o que lhe deu padronização e adoção que FLOW-MATIC nunca alcançou.

---

## Questão 8

Basic e PL/I surgiram com objetivos parecidos no nível da intenção: ampliar o acesso à programação. Mas as apostas que fizeram para chegar lá foram opostas.

Basic foi criada em 1964 por Kemeny e Kurtz em Dartmouth para estudantes sem formação técnica. O objetivo era que qualquer aluno de qualquer área pudesse escrever seus próprios programas. O compromisso de projeto foi a simplicidade radical: Basic sacrificou quase tudo (tipos complexos, estruturas de controle sofisticadas, modularização) em troca de uma curva de aprendizado mínima. O resultado é uma linguagem fácil de começar e muito difícil de escalar. Programas Basic grandes se tornavam rapidamente ilegíveis, principalmente pelo uso indiscriminado do GOTO.

PL/I surgiu da IBM como resposta a um problema diferente: Fortran servia ao computador científico, COBOL ao mundo comercial, e os programadores de cada área precisavam aprender linguagens separadas. A ideia era criar uma linguagem só que abrangesse os dois domínios e mais. O compromisso foi a abrangência excessiva: PL/I incluía tantos recursos que nenhum compilador jamais a implementou por completo. Era poderosa demais para ser simples e complexa demais para ser amplamente adotada.

O contraste revela uma tensão real no projeto de linguagens: amplitude de domínio e coerência conceitual raramente coexistem no mesmo grau. Basic escolheu coerência pela simplificação extrema. PL/I tentou amplitude e perdeu em complexidade incontrolável.

---

## Questão 9

APL, SNOBOL e SIMULA 67 são três linguagens dos anos 1960 que seguiram direções muito distintas e deixaram contribuições que sobrevivem até hoje.

APL, criada por Ken Iverson em 1962, foi desenvolvida para computação matricial e vetorial com uma notação matemática extremamente densa. Seu foco era expressar operações complexas sobre arrays inteiros em poucas linhas, usando símbolos especiais. A contribuição duradoura de APL é a ideia de operações sobre arrays como primitivas da linguagem, em vez de loops explícitos. Essa ideia está na base do NumPy em Python, do MATLAB e do R: quando você soma dois vetores com A + B sem escrever um loop, está usando o que APL estabeleceu.

SNOBOL, criada nos Bell Labs em 1962, foi pensada para processamento de strings e reconhecimento de padrões. Seu mecanismo de casamento de padrões era integrado à linguagem como operação de primeira classe. A contribuição duradoura é exatamente esse conceito de pattern matching, que é ancestral das expressões regulares modernas e do casamento de padrões em linguagens funcionais como Haskell e Erlang.

SIMULA 67, criada por Nygaard e Dahl na Noruega em 1967, foi desenvolvida para simulação de sistemas discretos: filas, redes, processos industriais. Para modelar entidades independentes com estado próprio e comportamento, os autores criaram o conceito de classe como molde e objeto como instância. A contribuição duradoura é a invenção do paradigma orientado a objetos. Smalltalk, C++, Java e Python têm raízes diretas em SIMULA 67.

---

## Questão 10

Ortogonalidade em projeto de linguagens significa que as primitivas da linguagem podem ser combinadas livremente, sem restrições arbitrárias ou casos especiais. Um conjunto de construções é ortogonal quando cada uma faz exatamente uma coisa e qualquer combinação entre elas é válida e tem comportamento previsível.

ALGOL 68 foi projetada com ortogonalidade como princípio central. Nela, tudo é um valor: expressões, declarações e até estruturas de controle retornam valores. Qualquer construção pode aparecer onde um valor é esperado. Isso cria regularidade real: há pouquíssimos casos especiais, e quem conhece as regras gerais consegue prever o comportamento de qualquer combinação.

Mas regularidade não é a mesma coisa que simplicidade. ALGOL 68 é amplamente considerada difícil de aprender e de implementar, justamente por causa dessa ortogonalidade agressiva. Quando não há restrições, o programador precisa lidar mentalmente com um espaço enorme de combinações possíveis. A ausência de casos especiais não reduz a carga cognitiva: ela a redistribui.

C é um bom contraponto: é menos ortogonal que ALGOL 68, mas mais fácil de usar no dia a dia, porque o número de padrões que o programador precisa dominar é menor. A restrição, nesse caso, serve ao usuário.

A conclusão é que ortogonalidade é uma propriedade que beneficia principalmente o projetista da linguagem e quem vai implementá-la. Para o usuário, o que importa mais é previsibilidade e economia cognitiva, que podem ou não vir da ortogonalidade.

---

## Questão 11

A cadeia ALGOL, Pascal e C representa a linhagem imperativa mais direta da história das linguagens.

ALGOL 60 estabeleceu os fundamentos: escopo léxico, estrutura de bloco, BNF para especificação de sintaxe. Niklaus Wirth participou dos debates em torno de ALGOL e, insatisfeito com a complexidade do resultado, criou Pascal em 1970 como uma linguagem mais limpa e disciplinada para uso pedagógico. Pascal herdou o escopo léxico e a estrutura de bloco de ALGOL, mas impôs tipagem mais rígida e eliminou ambiguidades.

C foi criada em 1972 por Dennis Ritchie nos Bell Labs para escrever o Unix. Ela compartilha com Pascal a herança estrutural de ALGOL, mas segue uma filosofia diferente: Pascal enforça disciplina, C dá liberdade. C trocou a tipagem estrita por acesso direto à memória e flexibilidade total, o que a tornou ideal para sistemas operacionais e programação de baixo nível. A influência de Pascal sobre C existe, mas é mais de contraste do que de herança direta.

Prolog, criada por Colmerauer em 1972, representa a ruptura com essa linhagem toda. Toda a cadeia ALGOL, Pascal, C é imperativa: o programador descreve como o computador deve executar os passos para chegar a um resultado. O foco está na sequência de instruções e no estado das variáveis.

Prolog é declarativa e lógica: o programador descreve o que é verdadeiro sobre o problema, e o mecanismo de inferência determina como encontrar soluções. Não há sequência de passos explícita, não há variáveis de estado mutável. O programa é uma base de conhecimento, e executar é fazer inferência sobre essa base.

---

## Questão 12

Uma pequena base Prolog em linguagem natural:

```prolog
% Fato 1
pai(joao, maria).

% Fato 2
mae(maria, pedro).

% Regra: X é avô de Z se X é pai de Y e Y é mãe de Z
avo(X, Z) :- pai(X, Y), mae(Y, Z).

% Consulta
?- avo(joao, Quem).
% Resposta: Quem = pedro
```

Por que isso representa programação lógica e não apenas armazenamento de dados?

Um banco de dados relacional também armazena fatos e permite consultas. A diferença está na regra e no mecanismo de inferência. A regra `avo(X, Z) :- pai(X, Y), mae(Y, Z)` não é uma query pré-definida: é uma declaração lógica. Ela diz que, para quaisquer X e Z, X é avô de Z se existir algum Y tal que X é pai de Y e Y é mãe de Z. É uma afirmação sobre o mundo, não um procedimento.

Quando a consulta é feita, o Prolog não executa um algoritmo que o programador escreveu. Ele usa unificação, que é casamento de padrões, e backtracking, que é tentativa e retrocesso, para derivar a resposta a partir dos fatos e regras. O programador nunca disse como procurar: disse o que é verdadeiro. O motor de inferência fez o resto.

É isso que diferencia programação lógica: o programa é uma teoria, e computar é raciocinar sobre essa teoria.

---

## Questão 13

Ada foi desenvolvida entre 1975 e 1983 a partir de uma constatação do Departamento de Defesa americano: o governo gastava bilhões mantendo software em dezenas de linguagens diferentes, muito dele embarcado em sistemas onde um erro podia ter consequências irreversíveis. A solução foi projetar uma linguagem que tornasse certas categorias de erro impossíveis de escrever.

A tipagem forte de Ada vai além da verificação de tipos básica. Tipos distintos com a mesma representação interna não são intercambiáveis sem conversão explícita. Uma temperatura em Celsius e uma em Fahrenheit podem ser ambas valores reais, mas Ada permite declarar tipos distintos e o compilador rejeita qualquer mistura acidental. Em sistemas onde unidades físicas são críticas, isso elimina uma classe inteira de bugs.

Os pacotes separam especificação e implementação de forma explícita. A interface pública de um módulo é visível para quem o usa; a implementação fica encapsulada. Em sistemas grandes desenvolvidos por equipes diferentes, essa separação é essencial para controlar dependências. Mudanças internas não afetam o código que usa o módulo, desde que a interface seja mantida.

A concorrência foi integrada diretamente na linguagem através de tasks e rendezvous, em vez de ser delegada a bibliotecas externas. Sistemas embarcados e de tempo real precisam lidar com múltiplos processos simultâneos com garantias de temporização. Deixar isso para o sistema operacional ou para bibliotecas de terceiros introduzia variabilidade e dependências que Ada queria eliminar.

Os quatro elementos formam um conjunto coerente: tipagem evita erros de dados, pacotes evitam erros de interface, concorrência nativa evita erros de temporização, e tudo junto serve a um único objetivo que é confiabilidade em domínios onde falhar não é opção.

---

## Questão 14

Smalltalk, C++ e Java representam três interpretações diferentes do que significa programar orientado a objetos.

Smalltalk, desenvolvida na Xerox PARC por Alan Kay a partir de 1972, é orientação a objetos em sua forma mais radical. Tudo é objeto: números, classes, métodos, o próprio ambiente de execução. A única forma de comunicação entre objetos é a troca de mensagens. Não há tipos primitivos fora da hierarquia de objetos, não há manipulação direta de memória. Smalltalk implementou pela primeira vez o trio completo de encapsulamento, herança e polimorfismo, além de permitir que o programa inspecione e modifique a si mesmo em tempo de execução.

C++, criada por Bjarne Stroustrup nos Bell Labs em 1983, tomou uma direção oposta em termos de pureza. O objetivo era adicionar classes e herança ao C sem abandonar nenhuma de suas características: acesso direto à memória, tipos primitivos não-objeto, performance máxima e zero overhead para features não utilizadas. O compromisso com C foi a decisão mais consequente de C++: garantiu adoção imediata por programadores já acostumados ao C, mas produziu uma linguagem de enorme complexidade, com herança múltipla, ponteiros brutos, gerenciamento manual de memória e comportamento indefinido em várias situações.

Java, lançada pela Sun em 1995, aprendeu com os problemas de C++. Eliminou ponteiros brutos, gerenciamento manual de memória com garbage collection, e herança múltipla de implementação. Mas sua inovação central foi a Java Virtual Machine: o código Java é compilado para bytecode, um formato intermediário que roda em qualquer máquina com uma JVM instalada. A portabilidade era o problema que C e C++ nunca resolveram de forma satisfatória: compilar para Windows gerava um binário diferente de compilar para Unix. Java resolveu isso ao custo de uma camada de abstração a mais, que com o tempo foi otimizada por compiladores JIT.

---

## Questão 15

Java foi concebida originalmente como Oak em 1991 para dispositivos eletrônicos embarcados: controles remotos, televisores interativos, eletrodomésticos. A ideia era uma linguagem portável, segura e de baixo consumo para hardware variado e com memória limitada. O projeto fracassou nesse domínio porque a TV interativa não decolou e o hardware da época tinha recursos insuficientes.

Em 1995, a Web estava crescendo rapidamente. Páginas eram estáticas, navegadores eram simples, e havia demanda por conteúdo dinâmico e interativo. A Sun percebeu que as características que tornavam Java boa para dispositivos embarcados eram exatamente as que a Web precisava: portabilidade entre hardwares diferentes, execução em ambiente isolado e seguro, código compacto. Os Java Applets, pequenos programas Java embutidos em páginas HTML e executados pelo navegador, foram a resposta.

A adoção foi rápida. Java se tornou a linguagem da Web no final dos anos 1990 e, com isso, construiu um ecossistema de desenvolvedores, ferramentas e frameworks que a tornaram dominante também no backend corporativo, muito além do contexto Web para o qual havia sido reposicionada.

O caso ilustra que uma linguagem não é boa ou ruim em abstrato. Ela é mais ou menos adequada para o problema do momento. Quando o problema muda, linguagens antes periféricas podem se tornar centrais. Python passou pelo mesmo processo: criada como linguagem pedagógica nos anos 1990, tornou-se dominante em ciência de dados e machine learning nos anos 2010, não porque mudou muito, mas porque o contexto ao redor dela mudou radicalmente.

---

## Questão 16

O rótulo "linguagem de scripting" agrupa linguagens muito diferentes. Comparar pelos três eixos deixa isso mais claro.

Perl (1987) foi criada para processamento de texto e administração de sistemas Unix. Suas estruturas de dados centrais são escalares, arrays e hashes, com expressões regulares integradas à linguagem. A implementação é interpretada, com foco em expressividade compacta, o que levou ao princípio de que há mais de uma forma de fazer a mesma coisa.

JavaScript (1995) foi criada para interatividade em páginas Web no navegador. Seus objetos funcionam como dicionários dinâmicos, e o sistema de herança é baseado em protótipos, não em classes no sentido tradicional. A implementação original era interpretada, mas os motores modernos como V8 usam JIT e chegam a performance próxima de linguagens compiladas.

PHP (1994) foi criada especificamente para geração de HTML dinâmico no servidor. Seus arrays associativos unificam lista e dicionário em uma única estrutura. O modelo de execução é por requisição HTTP: cada request inicia e termina um processo isolado, o que simplifica o raciocínio sobre estado mas tem implicações de performance.

Python (1991) foi criada como linguagem pedagógica de propósito geral. Listas, dicionários, tuplas e sets são tipos de primeira classe com sintaxe direta. A implementação padrão é o CPython, que gera bytecode. O princípio é o oposto do Perl: há uma forma óbvia de fazer cada coisa.

Ruby (1995) foi criada com foco em produtividade e expressividade. Tudo é objeto, incluindo inteiros e nil. Blocos e closures são primitivas da linguagem. A adoção em larga escala veio principalmente pelo framework Ruby on Rails.

Lua (1993) foi criada especificamente como linguagem de extensão para aplicações escritas em C. Tem uma única estrutura de dados, a table, que funciona como array, dicionário e objeto ao mesmo tempo. Seu bytecode é extremamente compacto e a integração com C é um objetivo central de design. Lua não foi pensada para ser uma linguagem principal, e é exatamente por isso que ela é diferente de todas as outras desta lista.

---

## Questão 17

C# foi lançada em 2000 como parte da plataforma .NET da Microsoft e claramente aprendeu com Java, mas tomou decisões distintas em vários pontos.

A primeira diferença relevante é o tratamento de propriedades. Em Java, o padrão para encapsular um campo é criar métodos getX() e setX() explicitamente, o que resulta em código repetitivo que polui a interface das classes. C# introduziu properties como construção nativa da linguagem:

```csharp
public string Nome { get; set; }
```

O problema que isso resolve vai além da verbosidade. Em Java, a diferença entre acessar um campo público e chamar um método getter é visível no código que usa a classe. Se você decide encapsular um campo depois, precisa refatorar tudo que o acessa. Em C#, properties têm sintaxe de campo mas semântica de método, então você pode adicionar lógica de validação ou transformação ao getter e ao setter sem alterar nenhum código cliente.

A segunda diferença relevante é o suporte nativo a delegates e eventos. Em Java, antes do Java 8, implementar um callback ou um padrão de eventos exigia criar interfaces e classes anônimas, gerando muito boilerplate para algo extremamente comum em sistemas com interface gráfica ou arquiteturas orientadas a eventos. C# introduziu delegates, que são referências tipadas a métodos, e eventos como construções da própria linguagem. O resultado é que o padrão Observer, que em Java exige uma quantidade significativa de código de suporte, pode ser expresso diretamente em C# sem estrutura adicional.

---

## Questão 18

XSLT e JSP são linguagens híbridas que combinam marcação e programação, mas em direções opostas.

XSLT recebe como entrada um documento XML e aplica regras de transformação para produzir uma saída em qualquer formato texto: HTML, outro XML, CSV, texto simples. O processamento é declarativo: o programador define templates que descrevem o que produzir para cada nó do documento de entrada, usando XPath para navegar pela estrutura. XSLT é híbrida porque sua própria sintaxe é XML válido. O programa é simultaneamente um documento XML bem-formado e um conjunto de regras de transformação. Não há separação visual entre código e marcação: tudo é XML.

JSP vai na direção oposta. A entrada é uma requisição HTTP com dados de contexto. O documento base é HTML, e ilhas de código Java são embutidas nele usando tags especiais. O servidor de aplicação compila o JSP em um servlet Java, que processa a lógica e gera o HTML final enviado ao navegador. JSP é híbrida porque mistura template de apresentação com lógica de programação no mesmo arquivo: HTML define a estrutura visual, e o código Java entre as tags define o comportamento.

As duas podem ser chamadas de linguagens híbridas porque em ambas a fronteira entre marcação e código é porosa por design, não por acidente. Em XSLT, a marcação é o código. Em JSP, o código está dentro da marcação.

---

## Questão 19

```
1957  FORTRAN [imperativo/procedural]
        |
        |-- prova que compiladores geram código eficiente
        |
1960  ALGOL 60 [imperativo/estruturado]
        |
        |-- herança de escopo léxico e estrutura de bloco
        |                           |
        |                           |-- BNF como padrão de especificação de sintaxe
        |                           |   (influência sobre todas as linguagens seguintes)
        |
1960  LISP [funcional]              |
        |                           |
        |-- lambda, recursão,       |
        |   listas como dado        |
        |   e código                |
        |                         PROLOG [lógico] (1972)
        |-- avaliação simbólica      |
            como herança conceitual  |-- unificação e inferência
            para Haskell, Scheme     |   como modelo de execução
                                     |
1970  PASCAL [imperativo/estruturado]
        |
        |-- reação ao ALGOL: tipagem mais rígida, pedagogia
        |
1972  C [imperativo/sistemas]
        |
        |-- liberdade e acesso ao hardware
        |   em contraste com a disciplina de Pascal
        |
1967  SIMULA 67 [orientado a objetos]
        |
        |-- classes, objetos, herança como primitivas
        |
1972  SMALLTALK [orientado a objetos puro]
        |
        |-- radicalização do OO: tudo é objeto, tudo é mensagem
        |-- influência filosófica sobre Ruby
        |
1983  C++ [imperativo + OO]
        |
        |-- OO enxertado sobre C
        |   sem abrir mão de performance e compatibilidade
        |
1999  XSLT [declarativo/transformacional]
        |
        |-- herança conceitual do LISP:
            transformação por substituição de padrões

Paradigmas representados: imperativo, funcional, lógico, orientado a objetos, declarativo
```

Tipos de influência mapeados:
- Fortran → ALGOL 60: prova empírica de viabilidade de compiladores
- ALGOL 60 → Pascal → C: herança estrutural transformada progressivamente
- ALGOL 60 → comunidade teórica: BNF como padrão universal
- Lisp → linguagens funcionais: recursão e funções de primeira classe
- Lisp → XSLT: transformação declarativa baseada em padrões
- SIMULA 67 → Smalltalk → C++ / Java: cadeia do paradigma OO
- Prolog: ruptura com a linhagem imperativa, raízes na lógica matemática

---

## Questão 20

O cenário exige quatro componentes com requisitos radicalmente diferentes: simulação numérica, regras declarativas, interface Web interativa e firmware embarcado.

Para o motor de simulação numérica, a escolha mais adequada é Python com NumPy e SciPy, com rotinas críticas em Fortran ou C. Fortran foi criado especificamente para computação científica e numérica, e décadas de trabalho em otimização de compiladores o tornaram referência em performance para álgebra linear e simulações. Python se tornou o padrão em ciência de dados não pela velocidade do interpretador, mas pela qualidade das bibliotecas numéricas, que internamente chamam rotinas Fortran e C. A combinação é justificada historicamente porque replica o que a comunidade científica já estabeleceu: Python para orquestração e análise, Fortran ou C para os loops críticos onde performance é medida.

Para o módulo de regras declarativas, a família mais adequada é Prolog ou sistemas derivados de motores de inferência. Prolog foi criado por Colmerauer em 1972 exatamente para representar conhecimento e derivar conclusões a partir de fatos e regras. Em domínios onde as regras mudam com frequência e precisam ser legíveis por especialistas de negócio, a separação entre o que é verdadeiro e como inferir é uma vantagem arquitetural direta da proposta original de Prolog. Para equipes corporativas, Drools em Java oferece motor de regras com melhor integração ao ecossistema existente.

Para a interface Web interativa, a escolha é TypeScript com um framework moderno no frontend e Python ou Node.js no backend. JavaScript foi criado em 1995 especificamente para interatividade no navegador e é a única linguagem nativa do cliente Web. A história dos Java Applets e de outras tentativas de substituir JavaScript no browser mostra que o ecossistema e o suporte nativo do navegador são decisivos. TypeScript adiciona tipagem estática ao JavaScript sem abandonar esse ecossistema.

Para o firmware embarcado em microcontrolador de baixo custo, a escolha é C. C foi criado para escrever o Unix e seu princípio de zero overhead, onde você paga apenas pelas features que usa, com acesso direto à memória, o torna a escolha dominante em sistemas embarcados desde os anos 1970. Nenhuma linguagem posterior conseguiu substituí-lo de forma generalizada em hardware com recursos muito restritos.

Dois trade-offs que a equipe precisa enfrentar:

O primeiro é entre performance e produtividade no módulo científico. Usar Python com NumPy é muito mais produtivo do que escrever tudo em Fortran: o ecossistema de bibliotecas, a facilidade de prototipagem e as ferramentas de visualização reduzem o tempo de desenvolvimento significativamente. Mas em simulações que rodam por horas, a diferença de performance entre Python puro e Fortran otimizado nos loops internos pode ser de uma ou duas ordens de magnitude. Isso exige identificar os gargalos com profiling e reescrever apenas as partes críticas em Fortran ou C, o que implica manter desenvolvedores com habilidades em duas linguagens e gerenciar a fronteira de integração entre elas.

O segundo é entre expressividade e interoperabilidade no módulo de regras. Prolog é a linguagem mais adequada para expressar lógica de inferência complexa, mas é uma escolha periférica no ecossistema corporativo. A integração com Python ou Java não é trivial, a curva de aprendizado é íngreme para quem veio do paradigma imperativo, e o suporte de longo prazo em termos de ferramentas e contratação é limitado. Drools em Java oferece um motor de regras menos expressivo que Prolog, mas com integração natural ao ecossistema existente e suporte comercial. A equipe precisa escolher entre expressividade máxima e manutenibilidade de longo prazo.

---

*Referência: Sebesta — Concepts of Programming Languages, Capítulo 2.*
