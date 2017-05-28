# Introdução ao LaTeX para o SciELO

- Quem eu sou
- Conteúdo do curso
- Público-alvo
- Para quem é o LaTeX?
- Objetivos

## História e filosofia

Mais tarde.

## LaTeX: uma linguagem de marcação

Assim como HTML, XML ou Markdown, o LaTeX é uma linguagem de _markup_ (marcação
de texto). Em outras palavras, o usuário instrui o computador sobre como o
texto deve ser formatado e o programa segue as instruções. Ao contrário das
linguagens anteriores, o LaTeX é mais *semântico*. Por exemplo, o que os
comandos a seguir devem fazer?

    \section{Introdução}
    \tableofcontents

Muito embora você talvez nunca tenha visto um comando em LaTeX, fica claro que
o primeiro indica o começo de uma seção e o segundo, insere o sumário. Logo
veremos como esses comandos geram elementos visuais. Assim, os arquivos-fonte
`.tex` não são textos formatados, mas aquivos em texto plano.  Isso meramente
significa que o arquivo contém apenas os 95 caracteres ASCII imprimíveis (UTF-8
também está se tornando lugar comum).

## Exemplo: um artigo

Para entender como comandos se transformam no produto final, abriremos nosso
primeiro arquivo `.tex`, localizado em [`exemplos/artigo.tex`](exemplos/artigo.tex).

Nesse arquivo, veremos:

- Estrutura e capacidades de um documento LaTeX
- Compilação usando `lualatex` (e `pdflatex`)
- Comandos: `\section, \LaTeX, \tableofcontents, \url`
- Classes: `article`, `minimal` e seu efeito em `\section`
- Erros de compilação
- Arquivos auxiliares e o comando `latexmk -c`

## Comandos do LaTeX

Comandos simples, como `\tableofcontents`, devem estar separados do texto por
espaço em branco. Por exemplo:

```latex
\tableofcontents Embora isso funcione, o próximo exemplo ganha mais pontos por
estilo e ajuda na leitura do código. Por quê?
```

```latex
\tableofcontents
Esse exemplo é melhor, mas como espaço em branco não faz diferença, talvez
valesse a pena colocar mais uma linha entre o parágrafo e o comando.
```

Há, também, comandos que aceitam argumentos, como `\section{Introdução}`.
Argumentos sempre ficam entre `{ chaves }`:

```latex
\section{Introdução}\label{introducao}Este exemplo funciona, mas o código não é
muito legível. O resultado será perfeito, entretanto.
```

Vamos voltar ao arquivo [`exemplos/artigo.tex`](exemplos/artigo.tex) para
aprender na prática sobre esses comandos.

### Espaço em branco

Em LaTeX, múltiplos espaços em branco (espaços, TABs, novas linhas) são
condensados para apenas _um_ espaço em branco. Assim, o exemplo a seguir terá o
mesmo efeito do anterior:

```latex
\section      {Introdução}
        \label{introducao}

        Este exemplo funciona, mas o código não é
muito legível.      O resultado será perfeito, entretanto.
```

Voltemos a [`exemplos/artigo.tex`](exemplos/artigo.tex) para aprender mais
sobre espaços em branco e como usá-lo para tornar o código mais legível.

Agora, vamos a [`exercicios/espaco-branco.tex`](exercicios/espaco-branco.tex) e
resolver o problema proposto nos comentários. Quando o arquivo for compilado a
primeira vez, haverá um problema de hifenização. Por quê?

## Símbolos especiais

### Aspas

Em LaTeX, não usamos as chamadas “aspas burras” _("aspas burras")_:

```latex
``Devemos abrir aspas com dois acentos graves e fechar com duas aspas
simples.''
```

### Hífen, travessão e a meia-risca

Existe uma diferença entre o hífen, o travessão e a meia-risca:

```latex
Leve um guarda-chuva --- ouvi na rádio que pode chover entre 10h--13h.
```

### Caracteres reservados

Como veremos no decorrer de nosso curso, os símbolos a seguir estão reservados
para o uso do LaTeX:

```latex
# $ % ^ & _ { } ~ \
```

Devemos escapá-los para que sejam impresso da maneira correta:

```latex
\# \$ \% \^{} \& \_ \{ \} \~{} \textbackslash
```

[`exercicios/caracteres-reservados.tex`](exercicios/caracteres-reservados.tex)
não escapa os símbolos acima. Corrija o problema e compile o arquivo
corretamente.

## Pacotes

Em alguns exercícios, vimos que a hifenização estava errada. Por padrão, o
LaTeX é configurado para hifenizar de acordo com a língua inglesa. Para
resolver esse problema, devemos carregar nosso primeiro _pacote_.

Existem várias coisas que não são possíveis com o LaTeX básico — ao menos não
trivialmente — mas durante sua vida como usuário desse sistema você descobrirá
dezenas de pacotes muito úteis, que tornam tarefas tediosas e difíceis muito
mais agradáveis de resolver. Para carregar um pacote, usamos a seguinte sintaxe
no _preâmbulo_ do nosso arquivo:

```latex
\usepackage[opções]{pacote}
```

Para resolver o problema da localização do nosso arquivo, utilizaremos o pacote
`polyglossia`:

```latex
\usepackage{polyglossia}
  \setdefaultlanguage{brazil}
```

Algumas das capacidades do `polyglossia` são:

- Ajustar calendário datas de acordo com a língua
- Ajustar convenções tipográficas para a língua escolhida
- Hifenização
- Strings do documento (como em `\today`)

Em [`exercicios/pacotes.tex`](exercicios/pacotes.tex), treinaremos como
carregar pacotes.

Quando o exercício terminar, mostrar o [CTAN](https://ctan.org) e como
encontrar documentação para os pacotes. Mostrar a documentação do `polyglossia`
como exemplo.

## Preâmbulo do documento

Voltaremos ao documento [`exemplos/artigo.tex`](exemplos/artigo.tex) uma vez
mais, para aprender mais sobre classes de documento.

Documentos LaTeX são divididos em duas partes: o _preâmbulo_ e o documento em
si. Na primeira parte, a primeira linha que nos chama a atenção é:

```latex
\documentclass[11pt,a4paper,oneside]{article}
```
Anteriormente discutimos duas classes LaTeX: article e minimal. Por exemplo:

- `article`: para escrever artigos
- `report`: para escrever relatórios
- `book`: para livros
- `letter`: para redigir letras
- `memoir`: baseada na classe book, traz vários comandos úteis
- `beamer`: para apresentações de slide

Além dessas classes padrão, existem outras disponíveis para download.

O que são essas palavras entre os dois colchetes? São opções que a classe
`article` nos fornece por padrão. É bastante útil conhecer quais são as opções
da classe que você decidiu utilizar. O que a primeira opção, `11pt` deve
significar? Repetir para todas elas e explicar seus resultados. Aqui estão as
opções de classe mais comuns:

- `10pt, 11pt, 12pt`
- `a4paper, letterpaper, ...`
- `fleqn`: equações são alinhadas à esquerda ao invés de seres centralizadas.
- `leqno`: a numeração das equações fica à esquerda ao invés da direita.
- `titlepage, notitlepage`
- `twocolumn`
- `twoside, oneside`: arruma as margens para a impressão nos dois lados do
  papel ou apenas um.
- `landscape`: o documento é impresso em formato paisagem.
- `openright, openany`: não funciona com a classe `article`, pois ela não
  fornece o comando `chapter`.
- `draft`: indica problemas de hifenização e justificação imprimindo um pequeno
  quadrado na margem direita. Também suprime a colocação das imagens, colocando
  um quadro em branco em seu lugar. O tempo de compilação é bem menor.

Vamos abrir [`exemplos/artigo.tex`](exemplos/artigo.tex) para testar as classes
e opções acima. Veremos também os comandos `\title`, `\author` e `\date`.


