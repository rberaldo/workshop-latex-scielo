# Introdução ao LaTeX para o SciELO: dia 1

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

[`exercicio/caracteres-reservados.tex`](exercicio/caracteres-reservados.tex)
não escapa os símbolos acima. Corrija o problema e compile o arquivo
corretamente.
