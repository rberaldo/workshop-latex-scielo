# Introdução ao LaTeX para o SciELO: dia 1

- Quem eu sou
- Conteúdo do curso
- Público-alvo
- Para quem é o LaTeX?
- Objetivos:

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

Assim, os arquivos-fonte `.tex` não são textos formatados, mas aquivos em texto
plano. Isso meramente significa que o arquivo contém apenas os 95 caracteres
ASCII imprimíveis (UTF-8 também está se tornando lugar comum).

## Exemplo: um artigo

Vamos abrir nosso primeiro arquivo `.tex`, localizado em
[`exemplos/artigo.tex`](exemplos/artigo.tex).

Nesse arquivo, veremos:

- Estrutura e capacidades de um documento LaTeX
- Compilação usando lualatex
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

Aqui teremos um exercício.
