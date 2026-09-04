[derivacao-gramatica-java.md](https://github.com/user-attachments/files/31847260/derivacao-gramatica-java.md)
# Aula 003 — Derivação de um Código a partir da Gramática de uma Linguagem de Programação

**Disciplina:** Paradigmas de Linguagens de Programação<br>
**Professor:** Munif Gebara Junior<br>
**Alunos:** João Miguel Silva Salvalagio, Eduardo Barella, Gabriel dos Santos, Matheus Mascarello<br>
**Linguagem escolhida:** Java

---

## Objetivo da atividade

Escolher uma linguagem de programação, obter (ou construir) um fragmento de sua gramática formal em **BNF** (Backus-Naur Form) e usar essa gramática para **derivar passo a passo** um trecho de código válido, mostrando explicitamente qual produção é aplicada em cada etapa até chegar apenas em símbolos terminais.

A linguagem escolhida foi **Java**, e o código-alvo a ser derivado é a instrução de atribuição:

```java
x = a + b;
```

A gramática usada é um recorte simplificado da **Java Language Specification (JLS)**, restrito às regras necessárias para gerar uma `ExpressionStatement` de atribuição com um `+`.

---

## 1. Terminais e não terminais utilizados

| Categoria | Símbolos |
|---|---|
| **Não terminais** | `<Statement>`, `<ExpressionStatement>`, `<StatementExpression>`, `<Assignment>`, `<LeftHandSide>`, `<AssignmentOperator>`, `<Expression>`, `<AdditiveExpression>`, `<Identifier>` |
| **Terminais** | `x`, `a`, `b`, `=`, `+`, `;` |

Em conformidade com a JLS, um **identificador** (`Identifier`) é, ele mesmo, derivado de uma cadeia de caracteres Java válidos; aqui tratamos `x`, `a` e `b` diretamente como terminais para manter a derivação legível, já que o foco é a estrutura da atribuição, não o léxico de identificadores.

---

## 2. Gramática BNF (recorte simplificado da JLS)

```bnf
<Statement>            ::= <ExpressionStatement>

<ExpressionStatement>  ::= <StatementExpression> ";"

<StatementExpression>  ::= <Assignment>

<Assignment>            ::= <LeftHandSide> <AssignmentOperator> <Expression>

<LeftHandSide>          ::= <Identifier>

<AssignmentOperator>    ::= "="

<Expression>            ::= <AdditiveExpression>

<AdditiveExpression>    ::= <Identifier>
                          |  <AdditiveExpression> "+" <Identifier>

<Identifier>             ::= "x" | "a" | "b"
```

> Observação: a JLS real define `Expression` de forma muito mais ampla (envolve `ConditionalExpression`, `AssignmentExpression`, precedência de operadores, etc.). Este recorte preserva apenas a cadeia de produções necessária para chegar em `x = a + b;`, que é o objetivo pedagógico da atividade — mostrar a mecânica da derivação, não reproduzir a especificação inteira.

---

## 3. Derivação passo a passo (derivação mais à esquerda)

Convenção: em cada passo, o não terminal substituído é destacado em **negrito**, e a produção aplicada é indicada à direita.

| Passo | Forma sentencial | Produção aplicada |
|---|---|---|
| 0 | **`<Statement>`** | símbolo inicial |
| 1 | **`<ExpressionStatement>`** | `<Statement> ::= <ExpressionStatement>` |
| 2 | **`<StatementExpression>`** `;` | `<ExpressionStatement> ::= <StatementExpression> ";"` |
| 3 | **`<Assignment>`** `;` | `<StatementExpression> ::= <Assignment>` |
| 4 | **`<LeftHandSide>`** `<AssignmentOperator>` `<Expression>` `;` | `<Assignment> ::= <LeftHandSide> <AssignmentOperator> <Expression>` |
| 5 | **`<Identifier>`** `<AssignmentOperator>` `<Expression>` `;` | `<LeftHandSide> ::= <Identifier>` |
| 6 | `x` **`<AssignmentOperator>`** `<Expression>` `;` | `<Identifier> ::= "x"` |
| 7 | `x` `=` **`<Expression>`** `;` | `<AssignmentOperator> ::= "="` |
| 8 | `x` `=` **`<AdditiveExpression>`** `;` | `<Expression> ::= <AdditiveExpression>` |
| 9 | `x` `=` **`<AdditiveExpression>`** `"+"` `<Identifier>` `;` | `<AdditiveExpression> ::= <AdditiveExpression> "+" <Identifier>` |
| 10 | `x` `=` **`<Identifier>`** `+` `<Identifier>` `;` | `<AdditiveExpression> ::= <Identifier>` |
| 11 | `x` `=` `a` `+` **`<Identifier>`** `;` | `<Identifier> ::= "a"` |
| 12 | `x` `=` `a` `+` `b` `;` | `<Identifier> ::= "b"` |

Na etapa final (passo 12), a forma sentencial é composta **apenas por símbolos terminais**, o que significa que a derivação terminou e a cadeia gerada é exatamente:

```java
x = a + b;
```

---

## 4. Árvore de derivação

```
                <Statement>
                     |
             <ExpressionStatement>
                 /          \
        <StatementExpression>   ";"
                 |
             <Assignment>
          /       |         \
  <LeftHandSide>  "="   <Expression>
        |                    |
   <Identifier>        <AdditiveExpression>
        |               /         |         \
       "x"    <AdditiveExpression> "+"  <Identifier>
                     |                        |
               <Identifier>                  "b"
                     |
                    "a"
```

Cada nó interno é um não terminal expandido por uma produção da gramática; as folhas, lidas da esquerda para a direita, formam exatamente a sentença `x = a + b;`.

---

## 5. Conclusão

A atividade mostra na prática o que a gramática formal de uma linguagem realmente faz: **define, por meio de um conjunto finito de regras de produção, todas as cadeias de símbolos terminais que são consideradas sintaticamente válidas** naquela linguagem. Partindo do símbolo inicial `<Statement>` e aplicando produções sucessivas — sempre substituindo um não terminal pelo lado direito de uma de suas regras — foi possível chegar, em 12 passos, à instrução Java `x = a + b;`.

Essa é exatamente a mecânica que um **parser** (analisador sintático) de um compilador Java realiza ao ler o código-fonte: ele não deriva do símbolo inicial até a sentença (como fizemos aqui, de forma didática), mas sim o processo inverso — parte da sentença de entrada e tenta reconstruir uma árvore de derivação válida segundo a gramática, rejeitando o código caso isso não seja possível.
