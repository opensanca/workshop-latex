# Introdução ao LaTeX

- Quem eu sou
- Conteúdo do curso
- Público-alvo
- Objetivos: não é ensinar todos os mínimos detalhes técnicos do LaTeX, mas
  focar em sua utilização. Ou seja, ao invés de ficar pensando em detalhes
  primeiro, vamos fazer exercícios! Também vamos aprender muita tipografia
  nessa aventura.

Esta apresentação ainda está em sua versão beta.

## História e filosofia

- Donald Knuth nasceu em Milwaukee, Wisconsin, em 1938.
- Seu pai tinha uma pequena editora, por isso conhecia as tradições da
  tipografia.
- Na Caltech, foi contratado como professor associado. Começou a escrever um
  livro sobre compiladores, mas logo notou que o escopo da obra seria muito
  maior. Planejou um livro de 12 capítulos que seria chamado *The Art of
  Computer Programming*.
- 1977: segunda edição do segundo volume do TAoCP não agradou Knuth
- ASCII não foi projetado para publicar livros
- Pelos próximos 10 anos, ele trabalha no TeX
- TeX: tau epsilon chi
- [TeXBook](http://www.ctex.org/documents/shredder/src/texbook.pdf)
- Leslie Lamport criou uma série de macros para usar o TeX, conhecidas como
  LaTeX.

## O básico de LaTeX

O LaTeX é uma linguagem de marcação de texto, como o HTML ou o Markdown. Isso
significa que você deve dizer ao computador como o texto deve ser formatado,
mas quem faz o trabalho sujo não é você. O LaTeX é bastante *semântico*, mais
do que as linguagens anteriores. O que o comando a seguir deve fazer?

    \section{Introdução}

Em geral, os comandos que utilizaremos em LaTeX começam com uma barra ` \ `,
seguida pelo nome do comando. Comandos podem ter argumentos, como no caso
acima.

## hello-world.tex

Vamos abrir o arquivo `hello-world.tex` e aprender como documentos são
organizados no LaTeX. Tudo o que está entre `\begin{document}` e
`\end{document}` será impresso pelo LaTeX. O que vem antes dessa parte é
conhecido como preâmbulo. O preâmbulo deste documento é apenas
`\documentclass{article}`. Perguntar o que o público acredita que este
comandos significa.

Agora, vamos compilar nosso documento. Utilizaremos o comando `lualatex`, que é
apenas uma das maneiras de compilar um documento utilizando o LaTeX. Também
quero demonstrar outros métodos (online, por exemplo). Escolhemos o `lualatex`
por seu suporte de fontes externas e Unicode.

O que acontece se eu adicionar o comando `\section{Introdução}` antes do
texto?

Agora, vamos mudar a classe do nosso documento para `minimal`. O que isso
significa? Quais classes existem além de `article` e `minimal`? O que acontece
com `\section` quando eu mudo para a classe `minimal`?

Perguntar, aliás, o que são aquelas linhas que começam com `%` no topo do
arquivo, e por que não são impressas no documento final?

### Exercício

Compilar o arquivo `hello-world.tex` com sucesso.

## simbolos-reservados.tex

Como veremos no decorrer de nosso curso, os símbolos a seguir estão reservados
para o uso do LaTeX:

    # $ % ^ & _ { } ~ \

Devemos escapá-los para que sejam impresso da maneira correta:

    \# \$ \% \^{} \& \_ \{ \} \~{} \textbackslash

### Exercício

O arquivo `simbolos-reservados.tex` não escapa os símbolos acima. Corrija o
problema e compile o arquivo corretamente.

## espaco-branco.tex

No arquivo `espaco-branco.tex` temos dois parágrafos do começo de *O guia do
mochileiro das galáxias.*

Mostrar o espaço em branco que existe para o público. Perguntar o que eles
esperam que aconteça quando eu compilar o documento.

Múltiplos espaços em branco no LaTeX são ignorados: apenas um espaço em branco
é colocado entre as palavras. Assim, é difícil errar e acabar com espaçamento
a mais.

Para criar um novo parágrafo, devemos deixar um espaço em branco entre as
linhas. Novas linhas são ignoradas: para inserir uma linha, `\newline` ou `\\`.

### Exercício

`espaco-branco-exercicio.tex`. Arrumar o arquivo, deixando os
espaços e parágrafos corretos.

Notar que nem tudo funcionará perfeitamente. Qual problemas encontramos? Sim,
os diacríticos não apareceram corretamente. Alguém saberia o motivo?

## poliglota-exercicio.tex

Ao compilar o documento `espaco-branco.tex`, nós vemos que muitos caracteres
como o “é” de “além” não foram impressos. Isso acontece porque o LaTeX, nas
configurações mais básicas, não suporta diacríticos e outros símbolos.
Precisamos carregar nosso primeiro *pacote* para resolver isso.

Existem várias coisas que não são possíveis com o LaTeX básico — ao menos não
trivialmente — mas durante sua vida como usuário desse sistema você descobrirá
dezenas de pacotes muito úteis, que tornam tarefas tediosas e difíceis muito
mais agradáveis de resolver. Para carregar um pacote, usamos a seguinte
sintaxe no *preâmbulo* do nosso arquivo:

    \usepackage[opções]{pacote}

Para resolver o problema de diacríticos faltando em nosso documento,
utilizaremos o pacote `polyglossia`. Ele é uma alternativa para o antigo
pacote `babel` que funciona melhor com o luaLaTeX. Algumas das capacidades do
`polyglossia` são:

- ajustar calendário datas de acordo com a língua
- ajustar convenções tipográficas para a língua escolhida
- hifenização
- strings do documento (como em `\today`)

Para carregar as configurações para o nosso idioma, devemos usar o comando:

    \setdefaultlanguage{brazil}

### Exercício

Adicionar o pacote `polyglossia` abaixo do `\documentclass` e compilar o
arquivo.

Quando o exercício terminar, **mostrar o CTAN e como encontrar documentação
para os pacotes.** Mostrar a documentação do `polyglossia` como exemplo.

## artigo.tex

Agora, vamos olhar para um documento um pouco mais complexo, mas também mais
típico. `artigo.tex` demonstra alguns conceitos interessantes em LaTeX.  Vamos
começar pela organização de um aquivo `.tex`. Basicamente, ele é dividido em um
*preâmbulo* no qual estão os pacotes e opções que utilizaremos e o *documento
em si,* que começa a partir do comando `\begin{document}`.

### Preâmbulo: classes e suas opções

Vamos explorar o preâmbulo para começar. A primeira linha que chama nossa atenção é:

    \documentclass[11pt,a4paper,oneside]{article}

Anteriormente discutimos duas classes LaTeX: `article` e `minimal`. Mas existem
muitas outras classes. Por exemplo:

- `article`: para escrever artigos
- `report`: para escrever relatórios
- `book`: para livros
- `letter`: para redigir letras
- `memoir`: baseada na classe book, traz vários comandos úteis
- `beamer`: para apresentações de slide

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

**Compilar o mesmo documento com várias opções diferentes e mostrar os
resultados.**

### Preâmbulo: pacotes e comandos para o título

Após o `\documentclass`, três pacotes são carregados: `polyglossia, blindtext`
e `hyperref`. Olhando o código-fonte, o que os dois últimos pacotes devem
fazer? **Mudar o conteúdo do comando `\author` para o seguinte:**

    \author{Rafael Beraldo \\[1cm]
    \href{mailto:rberaldo@cabaladada.org}{\textless rberaldo@cabaladada.org \textgreater}

O que será impresso agora?

### O documento em si

No corpo do documento, entre `\begin{document}` e `\end{document}` existem
vários comandos interessantes. **Discutir o significado de `\frenchspacing` e
ensinar também o comando `\subsection`.**

### Compilação e arquivos auxiliares

**Compilar o arquivo e mostrar a quantidade de arquivos que foram produzidos.**
A quantidade de arquivos produzidos é sempre muito grande, mas a maior parte
pode ser deletada sem problemas.

Compiladores LaTeX passam apenas uma vez pelo documento, produzindo o PDF
durante a compilação. Mas eles não pulam por todo o código, portanto certas
operações introduzem outros arquivos que guardam informações que serão usadas
mais tarde. Aqui vai uma lista de arquivos auxiliares:
https://en.wikibooks.org/wiki/LaTeX/Basics#Ancillary_files

Para evitar que tantos arquivos sejam mantidos, podemos utilizar o comando
`latexmk -c`.

### Exercício

Transformar o arquivo `artigo-exercicio.tex` em um arquivo LaTeX e compilá-lo.
Mostrar o arquivo resolvido na tela de discutir, primeiro, como implementá-lo
com a plateia.

## fontes.tex

Originalmente, o TeX foi projetado para utilizar o sistema MetaFont, também
projetado pelo Prof. Donald Knuth. Os sistemas mais populares atualmente são,
porém, o Truetype `(ttf)` e OpenType `(otf)`. Antes de aprender a trabalhar com
fontes, seus estilos e tamanhos, gostaria de contar rapidamente a história das
fontes no TeX.

### Fontes e codificação no início do TeX

![A tabela ASCII](imagens/ascii-chart.png "A tabela ASCII")

Mesmo para o olhar leigo, a tabela ASCII deve parecer terrivelmente incompleta.
Dos 128 caracteres possíveis (2^7), apenas 95 são imprimíveis, e não há uma
letra sequer que seja acentuada. Quando o Prof. Donald Knuth criou a primeira
codificação das fontes do TeX, conhecida como `OT1` (Old Text 1), ela também
contava com apenas 7 bits, com a maioria dos caracteres advindos da tabela
ASCII. Naquela época, se o usuário desejasse inserir uma palavra com acentos,
era necessário escrever o seguinte:

    Eur\'{i}pides

O TeX sobrepunha os acentos às letras, conseguindo um resultado visualmente
perfeito. Essa técnica ainda é usada por usuários de LaTeX para quem os
caracteres inclusos na ASCII são suficientes. Ela não vem sem seus problemas,
como:

- Palavras acentuadas não são hifenizadas.
- Não é possível buscar palavras acentuadas no output — muito menos
  copiá-las.
- Não é possível representar outros sistemas de escrita — como o alfabeto
  cirílico, o sistema de escrita árabe, caracteres chineses etc.

Em 1990, no Encontro Anual Geral do TUG (TeX User Group) em Cork, Irlanda, um
grupo de usuários especificou uma codificação com 256 glifos que cobriam a
maior parte das línguas do Oeste da Europa, bem como algumas línguas do Leste.
Essa codificação ficou conhecida como `T1`.

Quando comecei a aprender LaTeX, a recomendação era utilizar os seguintes
pacotes no preâmbulo para escrever textos em português:

    \usepackage[utf8]{inputenc}
    \usepackage[T1]{fontenc}

Felizmente, hoje existe uma solução mais simples e abrangente.

### UTF-8, UTF-16, UTF-32, Unicode, WTF?

O Unicode é um padrão que começou no fim da década de 1980 e hoje tem mais de
120 000 caracteres. O objetivo é codificar a maior parte dos sistemas de
escrita do mundo, bem como outros símbolos.

O Unicode é, no fundo, uma tabela que dá endereços aos caracteres. O trabalho
fica, geralmente, para o UTF-8 — que pode usar até 4 bytes para representar
qualquer caractere Unicode, e é mais comumente usado porque é compatível com a
tabela ASCII. Outras codificações, como o UTF-16 (que divide o espaço do
Unicode em duas sequências de 16 bits) ou o UTF-32.

O pacote sobre o qual aprendemos mais no começo deste workshop, `polyglossia`,
carrega um outro pacote chamado `fontspec`, sobre o qual falaremos agora. Por
motivos de clareza, incluiremos uma chamada a esse pacote a partir de agora em
nosso código. Antes de revelarmos a mágica, aprenderemos um pouco sobre a
história de como chegamos a ele.

Para carregar o pacote `fontspec`, basta adicionar o comando
`\usepackage{fontspec}` ao preâmbulo do documento. A codificação utilizada,
automaticamente, é a `TU`: TeX Unicode. Aprenderemos mais sobre esse pacote no
decorrer desse exercício.

### Itálicos, negritos e outros tipos

Fontes geralmente vêm em famílias que contém diversos tipos: romanas maiúsculas
e minúsculas, itálicos, negritos e versaletes, além dos algorismos de título e
texto. A fonte usada por padrão no LaTeX, chamada de Computer Modern e
projetada pelo próprio Knuth, é bastante completa nesse respeito. Para acessar
esses tipos, temos os comandos a seguir à nossa disposição.

- `\emph{}`: itálico quando em texto romano, romando quando em texto itálico
- `\textbf{}`: negrito
- `\textsc{}`: versaletes (em inglês: *small caps*)
- `\texttt{}`: fonte de teletipo

### Tamanhos

Assim como diferentes tipos carregam diferentes significados, os tamanhos das
fontes também devem revelar alguma intenção semântica. Os tamanhos também devem
ter alguma relação entre si: uma escala.

O LaTeX leva essas questões em consideração automaticamente quando usamos
comandos como `\section`, por exemplo. Nós também podemos acessar esses
tamanhos utilizando os seguintes comandos:

- `\tiny`: 5pt
- `\scriptsize`: 7pt
- `\footnotesize`: 8pt
- `\small`: 9pt
- `\normalsize`: 10pt
- `\large`: 12pt
- `\Large`: 14pt
- `\LARGE`: 17pt
- `\huge`: 20pt
- `\Huge`: 25pt

Tenha em mente que os valores acima valem apenas para as classes quem vem por
padrão no LaTeX e quando o valor de `normalsize` é igual a 10pt. Outras classes
podem trazer outros valores, de acordo com a decisão de seu designer. Além
disso, é importante dizer que o tamanho do ponto no TeX é diferente do tamanho
usado atualmente pela maior parte dos programas. Quando Knuth projetou o
sistema, a editoração digital não era comum e muito menos acessível. Durante a
infância em Milwaukee, Wisconsin, seu pai era dono de uma editora. Assim, Knuth
cresceu dentro da tradição anglo-saxã de tipografia, que define um ponto como
0.35145980 mm. No entanto, com o advento do PostScript da Adobe, o ponto foi
redefinido para 0.3527 mm (1/72 in).

### Selecionar fontes diferentes

Uma das maiores vantagens de utilizar o `fontspec` é o comando de seleção de
fontes. Antigamente, era necessário carregar um pacote que implementasse a
fonte desejada em MetaFont. Hoje, é possível usar arquivos `ttf` e `otf`.

Para selecionar uma fonte instalada no sistema nos diretórios padrões, basta
usar o comando:

    \setmainfont{Linux Libertine}

Caso você esteja trabalhando com um dos editores online de LaTeX, é possível
fazer o upload das fontes para o serviço e especificar o caminho. Por exemplo:

    \setmainfont{Linux Libertine}[
      Path = fonts/
    ]

Uma funcionalidade muitas vezes ignorada sobre as fontes são as ligaduras. Elas
acontecem em sequências de caracteres que colidem naturalmente e são uma
tradição tipográfica muito antiga, que ganhamos de graça usando o LaTeX.

### Exercício

Vamos resolver `fontes-exercicio.tex`.

## layouts-pagina.tex

Usando a solução do exercício anterior, vamos mudar a opção de classe
`onecolumn` para `twocolumn` e visualizar o efeito dessa mudança no layout da
página. Também carregaremos o pacote `showframe`. **Mostrar como as margens são
muito maiores.** Parece uma perda de papel — e é — mas existe um motivo por
trás de margens são grandes: quando lemos uma linha longa demais, perdemos a
noção de onde ela havia começado. O tamanho de linha ideal fica por volta de 66
caracteres, incluindo espaços. É por isso que jornais são divididos em tantas
colunas. Para resolver esse problema das margens, existem algumas soluções:

- Dividir o texto em duas colunas (melhor solução)
- Carregar o pacote `fullpage`
- Carregar o pacote `fullpage` com espaçamento grande entre as linhas (como
  exige a ABNT).

Para arrumar o espaçamento entre as linhas, devemos utilizar o pacote
`setspace`. Ele vem com os seguintes comandos:

- `\singlespacing`
- `\onehalfspacing`
- `\doublespacing`

Quando você utilizar o comando `\onehalfspacing`, por exemplo, o documento
seguirá esse espaçamento até que outro espaçamento seja especificado.

Outro fator que influencia o layout da página é seu estilo. O LaTeX vem com
dois comandos, `\pagestyle{}` e `\thispagestyle{}`, que aceitam os seguintes
argumentos:

- `empty`: sem texto no cabeçalho e no rodapé
- `plain`: cabeçalho limpo, mas o número da página aparece centralizado no
  rodapé
- `headings`: rodapé limpo, informações como o nome da seção e número da página
  aparecem no cabeçalho

Existem outras opções e comandos que nos permitem customizar o conteúdo do
cabeçalho e do rodapé, mas não trataremos deles nesse workshop.

### Exercício

Em `layouts-pagina-exercicio.tex`, vamos começar a escrever um certificado de
conclusão do workshop. No momento, não vamos nos preocupar com a posição exata
do texto no papel. Algumas ideias de como implementar:

- Um certificado em modo de paisagem é muito mais legal
- Quais seriam os tamanhos dos diferentes textos? Qual a relação hierárquica
  entre eles? Justifique sua decisão.

A ideia para este exercício foi tirada do livro *LaTeX Tutorials: a Primer*.

## posicao-texto.tex

Se quisermos que nosso certificado fique mais parecido com um de verdade,
precisamos aprender a colocar nosso texto nas regiões do papel que desejamos.
Por padrão, as caixas de texto em LaTeX são justificadas, mas há outras opções
comuns como textos centralizados, alinhados à esquerda ou à direita.

Para determinar a posição horizontal do texto, precisamos encontrar nosso
primeiro *ambiente.* Na verdade, um dos primeiros construtos que encontramos em
nossa jornada foi o ambiente `document`, delimitado por dois comandos: `\begin`
e `\end`.

O ambiente `center`, com o nome sugere, se encarrega de centralizar texto na
página:

    \begin{center}
      Este texto será centralizado.
    \end{center}

De maneira similar, os ambiente `flushleft` e `flushright` alinham texto ao
lado esquerdo e direito do papel, respectivamente.

Além disso, é possível controlar o espaço dentro de uma linha com o comando
`\hspace{comprimento}`, por exemplo:

    Essa frase\hspace{1.5cm} está esticada.

Algumas unidades que o LaTeX reconhece são:

- `mm`
- `cm`
- `in`
- `pt`
- `em` (comprimento da letra “m”)
- `ex` (altura da letra “x”)
- `\textheight` e `\textwidth` (altura e comprimento da corpo do texto)
- `\pageheight` e `\pagewidth` (altura e comprimento da página toda)

Ainda é possível utilizar o comando `\hfill`, que preenche todo o espaço
disponível na linha:

    Começo\hfill meio\hfill fim

Finalmente, o espaço vertical entre os parágrafos pode ser controlado da mesma
maneira, com os comandos `\vspace{comprimento}` e `\vfill`.

### Exercício

`posicao-texto-exercicio.tex` continua o exercício anterior, finalizando nosso
certificado.

## listas.tex

Nas próximas seções, discutiremos vários outros ambientes. A segunda classe de
ambientes quem vêm por padrão com o LaTeX são `itemize`, `enumerate` e
`description`. Quem adivinha para o que elas servem?

    \begin{itemize}
      \item O ambiente \code{itemize} é geralmente usado para listas cuja ordem
      não é importante.
      \item A numeração que listas do tipo \code{enumerate} trazem pode indicar
      os passos necessários para completar uma tarefa, ou sua ordem de
      importância.
      \item A lista do tipo \code{description} é excelente para explicar
      conceitos relacionados. Que oportunidade perdida de usá-la!
    \end{itemize}

Vamos abrir o arquivo `listas.tex` e brincar com alguns conceitos. Como podemos
criar listas dentro de listas? Qual o resultado que você espera? E quanto à
lista `description`: como devemos adicionar as descrições aos itens?

### O pacote `enumerate`

Uma maneira muito elegante de customizar suas listas ordenadas é o pacote
[`enumerate`](https://www.ctan.org/pkg/enumerate). Ele adiciona um argumento
adicional ao ambiente de mesmo nome, permitindo customizar a lista facilmente:

    \begin{itemize}[A)]
    \item Tales de Mileto
    \item Pitágoras
    \item Xenófanes
    \item Empédocles
    \item Aristóteles
    \end{itemize}

### Exercício

Vamos editar uma lista de ingredientes para uma receita de panqueca em
`listas-exercicio.tex`. Há um problema: os contadores resetam quando uma lista
é terminada. Podemos criar um novo contador `\newcounter{ingredients}` e, ao
fim da primeira lista, salvar o valor de `enumi` com
`\setcounter{ingredients}{\value{enumi}}`. No começo da lista que queremos
continuar, podemos usar o comando `\setcounter{enumi}{\value{ingredients}}`.

## citacoes-versos.tex

Dois ambientes úteis para citações são `quote` e `quotation`. O primeiro é útil
para uma ou várias citações curtas. O segundo é melhor para citações longas,
pois os parágrafos são indentados.

Nos slides, exemplos de citação e poemas. Não faremos um exercício.

## tabelas.tex

Tabelas podem ser um assunto complicado em LaTeX, mas isso nem sempre precisa
ser verdade. Para começar, não devemos tentar imitar a abordagem de programas
WYSIWYG quando o assunto são as tabelas. Vejamos um exemplo:

    \begin{tabular}{lcr}
    1 & 2 & 3\\
    4 & 5 & 6\\
    7 & 8 & 9
    \end{tabular}

O ambiente `tabular` não deve ser encarado simplesmente como uma maneira de
fazer tabelas, mas primeiramente de alinhar textos na horizontal e na vertical.
Sua sintaxe é `\begin{tabular}{alinhamentos}`. Os valores de alinhamento
básicos são `c` (centro), `l` (esquerda) e `r` (direita). É possível, também,
especificar linhas verticais com `|` e parágrafos com tamanhos definidos com
`p{comprimento}` (alinhado ao topo), `m{comprimento}` (alinhado no meio) e
`b{comprimento}` (alinhado em baixo).

Linhas horizontais podem ser especificadas com `\hline`:

    \begin{tabular}{l|c|r}
    \hline
    1 & 2 & 3\\
    4 & 5 & 6\\
    7 & 8 & 9\\
    \hline
    \end{tabular}

Linhas, sejam elas horizontais ou verticais, devem ser usadas com moderação. O
objetivo da tabela é passar informação, portanto o texto deve ser o enfoque
central. É melhor deixar que a informação respire, do que cercá-la. Nas
palavras do Robert Bringhurst, em *Elementos do Estilo Tipográfico:*

> Assim como o texto, as tabelas ficam canhestras quando abordadas de forma
> puramente técnica. Boas soluções tipográficas não costumam surgir em resposta
> a perguntas do tipo “Como posso enfiar essa quantidade de caracteres naquele
> tanto de espaço?”. (p. 81)

Veremos alguns exemplos de tabelas empregando essas ideias em `tabelas.tex`:

- A sintaxe do ambiente `tabular`
- Como fazer tabelas que respiram e dão ênfase ao conteúdo
- Quebras de linhas em tabelas
- O pacote [`booktabs`](https://www.ctan.org/pkg/booktabs)
- O comando `\multicolumn`
- O pacote [`longtable`](https://www.ctan.org/pkg/longtable) e o comando
  `\endhead`; existem outros comandos que não exploraremos aqui

### Exercício

Resolver `tabelas-exercicio.tex`.

### Flutuando com `table`

Até agora, temos colocado nossas tabelas em meio ao texto usando o ambiente
`tabular`. É muito comum, no entanto, colocar tabelas em páginas dedicadas,
para que não atrapalhem o fluxo do texto. O LaTeX é capaz de fazer isso usando
uma abstração conhecida como *float*.

Em LaTeX, os dois ambiente do tipo float mais comuns são `table` e `figure`:

    \begin{table}[posição]
      …
    \end{table}

As posições possíveis são:

- `h`: aqui (here)
- `t`: topo da página
- `b`: base da página
- `p`: página dedicada a floats
- `!`: sobrescreva as restrições de float

O padrão é `tbp`.

Nossa primeira tabela poderia ser reescrita desta maneira:

    \begin{table}
      \centering
      \begin{tabular}{lcr}
      1 & 2 & 3\\
      4 & 5 & 6\\
      7 & 8 & 9
      \end{tabular}
      \caption{Números de 1 a 9}
      \label{tab:numerosUmNove}
    \end{table}

Três comandos a notar: `\centering` pode ser usado ao invés do ambiente
`center`, pois seu escopo estará limitado; `caption{legenda}` pode ser usado
para adicionar uma legenda à tabela e `\label{referencia}` permite que
referenciemos a tabela usando `\ref{referencia}`.

### Exercício

`tabelas-questionario-exercicio.tex` é uma tabela por conta dos presentes.
Vamos entrevistar dois vizinhos e perguntar os últimos livros, artigos, filmes
ou séries que viram e criar uma tabela.

### Ferramentas

As tabelas que discutimos durante esta introdução não precisaram de muito
espaço horizontal. No entanto, há ocasiões nas quais desejamos escrever uma
tabela com tamanho dinâmico e que tome a página toda. Para isso, existe o
pacote [`tabularx`](https://www.ctan.org/pkg/tabularx), que define um novo
ambiente que aceita o alinhamento `X`, que é flexível.

Como em tudo em LaTeX, quantidade de pacotes e detalhes que podemos discutir é
grande demais para este pequeno workshop. Deixo aqui alguns links úteis:

- [Tutorial do Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Tables), do qual
  tiramos muitas ideias
- [Descrição de vários pacotes para tabelas, seus usos e
  conflitos](http://tex.stackexchange.com/q/12672)
- [Lista de ferramentas para ajudar a criação de
  tabelas](http://tex.stackexchange.com/q/49414)
- [Table Generator](http://www.tablesgenerator.com/)
- [Table Editor](http://truben.no/table/)

## imagens.tex

É possível importar gráficos em formatos como `png` e `jpg` usando o pacote
`graphicx`. O pacote inclui uma série de comandos para redimensionar e
rotacionar textos e gráficos, bem como o comando `\includegraphics`.

    \includegraphics[opções]{imagem}

O comando aceita uma série de opções. Durante este curso, veremos:

- `width` e `height`: para controlar o comprimento e altura da imagem. Aceita
  valores como `\textwidth` e `\pageheight`
- `keepaspectratio`: um valor booleano
- `scale`: por exemplo, o valor de 0.5 reduz a imagem pela metade

Geralmente, usamos o ambiente `figure`, que funciona de maneira muito similar
ao `table`:

    \begin{figure}
      \centering
      \includegraphics{imagem}
      \caption{Uma imagem de exemplo}
      \label{fig:imagem}
    \end{figure}

Demonstraremos esses conceitos no arquivo `imagens.tex`. Vamos aprender a
colocar duas imagens lado-a-lado com o ambiente `minipage`. É importante
mencionar que, em alguns casos, é necessário rodar o comando `lualatex` mais de
uma vez para que o documento compile corretamente. Como vimos anteriormente,
documentos são compilados em apenas uma passada, geralmente gerando arquivos
como `aux`, `log` etc. Eles precisam ser lidos para que referências e
bibliografias apareçam corretamente.  Nesses casos, podemos usar o comando
`latexmk --lualatex`.

### Exercício:

Copiar a solução do exercício anterior para `imagens-exercicio.tex`. Adicionar
uma imagem de sua escolha para ilustrar os resultados do questionário. Algumas
ideias são: uma foto do pôster do filme, uma capa de livro, ou foto do
entrevistado!

## matematica.tex

Uma das principais vocação do LaTeX é a matemática. Até agora, temos trabalhado
no chamado “modo de texto”. No “modo de matemática”, a maneira como o LaTeX
compreende o que estamos digitando muda consideravelmente. Por exemplo, letras
comuns são tratadas como variáveis.

O modo de matemática vem em dois sabores: *inline* e *displayed*. O primeiro é
útil quando queremos falar sobre várias variáveis em uma mesma linha. O segundo
cria um novo parágrafo. Os comandos para acessar esses modos são:

- Inline: `\begin{math} … \end{math}` ou `\( … \)`
- Displayed: `\begin{displaymath} … \end{displaymath}` ou `\[ … \]`
- Displayed com equações numeradas: `\begin{equation} … \end{equation}`

Há uma infinidade de comandos para descrever matemática, portanto não seria
possível ver todos eles nesse workshop. Porém, vamos explorar rapidamente os
principais conceitos que devem deixar a vida de quem quer aprender muito mais fácil.

Para uma lista relativamente completa, recomendamos o [artigo sobre LaTeX na
Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Mathematics).

### Símbolos

Em nossos teclados, há vários símbolos usados na notação matemática. Por
exemplo:

    + - = ! / ( ) [ ] < > | ' :

No modo de matemática, o LaTeX os trata da maneira correta. Para outros
símbolos que não estão em nosso teclado, existem comandos:

    2 \times 2 = 4

### Letras gregas

Há comandos fáceis de lembrar para acessar letras gregas:

    \alpha, \beta, \pi

### Operadores

Funções trigonométricas, logaritmos e exponenciais, limites, módulo etc. são
alguns dos operadores que já estão definidos por padrão.

    \cos (2\theta) = \cos^2 \theta - \sin^2 \theta

    \log xy = \log x + \log y

A Cifra de César funciona da seguinte maneira:

    E_n(x) = (x + n) \bmod 26

### Potências e subscritos

Potências são representadas com acentos circunflexos, `2^8`. Subscritos são
representados com underlines, `a_b`. Como em muitos outros casos no modo de
matemática, é possível agrupar valores usando chaves `{}`: `2^{32}`.

    f(n) = 4n + n^2

### Frações

O comando `\frac{numerador}{denominador}` cria frações:

    F = G \frac{m_1 m_2}{d^2}

É possível colocar frações dentro de frações:

    \frac{\frac{1}{x}+\frac{1}{y}}{y-z}


### Raízes

O comando `\sqrt{n}` permite escrever raízes:

    \sqrt{10^2} = 10

    \sqrt[3]{\frac{a}{b}}

### Exercício

Em `matematica-exercicio.tex`, reproduza a equação que está nos slides.

## abntex2.tex

A descrição oficial do [abnTeX2](http://www.abntex.net.br/) segue abaixo:

> O abnTeX2, evolução do abnTeX (ABsurd Norms for TeX), é uma suíte para LaTeX
> que atende os requisitos das normas da ABNT (Associação Brasileira de Normas
> Técnicas) para elaboração de documentos técnicos e científicos brasileiros,
> como artigos científicos, relatórios técnicos, trabalhos acadêmicos como
> teses, dissertações, projetos de pesquisa e outros documentos do gênero.
>
> A suíte abnTeX2 é composta por uma classe, por pacotes de citação e de
> formatação de estilos bibliográficos, por exemplos, modelos de documentos e
> por uma ampla documentação.

Para utilizar o abnTeX2, devemos utilizar a classe `abntex2`:
`\documentclass{abntex2}`. A classe implementa uma série de comandos novos:

- `\titulo`
- `\autor`
- `\orientador`
- `\instituicao`
- `\imprimircapa`
- `citacao` (ambiente)

Entre outros. Não faremos um exercício de abnTeX2, portanto vamos explorar
juntos a anatomia de uma monografia ficcional. Ver o
[manual](http://repositorios.cpai.unb.br/ctan/macros/latex/contrib/abntex2/doc/abntex2.pdf)
para mais informações sobre a organização do arquivo.

## abntex2-example.bib

O que não eu teria dado por esse tipo de ajuda na época! Mais uma seção de live
coding nos aguarda. Desta vez, aprenderemos a criar uma bibliografia.
Bibliografias em LaTeX não são tão complicadas quanto parecem. A ideia é a
seguinte: em seu diretório, há um arquivo `bib` que contém uma entrada
bibliográfica. Por exemplo:

    @article{greenwade93,
      author  = "George D. Greenwade",
      title   = "The {C}omprehensive {T}ex {A}rchive {N}etwork ({CTAN})",
      year    = "1993",
      journal = "TUGBoat",
      volume  = "14",
      number  = "3",
      pages   = "342--351"
    }

No arquivo principal, no local em que desejamos incluir a bibliografia, usamos
o comando `\bibliography{arquivo}`. No decorrer do texto, podemos utilizar os
comandos `\cite[p.~20]{greenwade93}` e `\citeonline` para fazer referência à
entrada bibliográfica desejada. Um arquivo `bst` fica responsável pelo estilo
correto da citação e da bibliografia.

Mão na massa!

## tipografia.tex

Gostaria de dar uma pausa para discutir e ilustrar alguns pontos importantes
sobre tipografia. Um dos principais motivos para se usar o LaTeX é justamente
sua qualidade tipográfica, portanto faz sentindo honrar essa arte.

Robert Bringhurst diz que a tipografia “existe para honrar seu conteúdo” (p.
23). Que ela deve ser como uma “estátua transparente”, que nos atrai para o
texto mas é imediatamente invisível, pois não chama atenção para si. Em outras
palavras, ela é bastante sutil. Vamos nos ater a estas sutilezas por um
momento.

### Pacote `microtype`

O pacote `microtype` mexe nos espaços entre as palavras, lida com a protusão de
caracteres perto da margem direita, bem como cuida da expansão de fontes.

**Mostrar [o manual do
`microtype`](http://mirrors.ctan.org/macros/latex/contrib/microtype/microtype.pdf),
que tem exemplos de suas funcionalidades.**

### Pontução

É importante entender a distinção entre quatro símbolos similares, mas que têm
funções muito diferentes. São eles:

- O travessão (—)
- A meia-risca (–)
- O hífen (-)
- O sinal de menos (−)

O travessão é utilizado para iniciar diálogos e separar frases diferentes. No
LaTeX, é acessível com o comando `---`. A meia-risca liga valores extremos de
uma série, como 1–10, A–Z e a Ponte Rio–Niterói. Pode ser escrita como `--` no
LaTeX. Já o hífen, que é o sinal que temos no teclado, conecta palavras como
guarda-chuva.

Também devemos conhecer os símbolos corretos para fazer as aspas. Em LaTeX,
podemos usar aspas “Unicode” ou o comando ```` para começar as aspas e `''`
para terminar.

Finalmente, reticências não são três pontos finais. Em LaTeX, podemos usar o
comando `\ldots` ou colocar reticências Unicode: …

### Espaços duros

Em LaTeX, podemos usar o til `~` para criar um espaço inquebrável entre duas
palavras. Isso é extremamente útil em casos como estes:

- `20~mil pessoas`
- `Sr.~Mário`
- `página~10`

### A classe `memoir`

Quem se interessou por essas dicas, dê uma olhada na classe
[`memoir`](https://www.ctan.org/pkg/memoir). Ela foi criada com essas questões
tipográficas em mente e vem com uma série de melhorias em relação às classes
padrão.

### Dica: textos e palavras em outras línguas

O pacote `polyglossia`, como o nome sugere, suporta várias línguas ao mesmo tempo por meio do comando `\setotherlanguages`. Por exemplo:

    …
    \usepackage{polyglossia}
    \setmainlanguage{brazil}
    \setotherlanguages{english}
    …
    \textenglish{This is a sentence in English, and it'll be hyphenized in the
    correct way!}

O `polyglossia` também disponibiliza um ambiente com o nome da língua:

    \begin{english}
    My long text.
    \end{english}

### Dica: crie macros semânticas

É possível criar macros com o LaTeX. Vejamos um exemplo bem simples:

    \newcommand{\filename}[1]{\texttt{#1}}

Assim, ao invés de usar o comando `\texttt` para se referir ao nome de um
arquivo, podemos usar o comando `\filename`, que é muito mais intuitivo.

### Dica: pacote `minted` para código fonte

O pacote [`minted`](https://www.ctan.org/pkg/minted) permite ao autor de um
documento incluir exemplos de código-fonte em seu arquivo. Existe um ambiente,
`minted`:

    \begin{minted}[autogobble,breaklines]{latex}
      \section{Introdução}
    \end{minted}

E também um comando para inserção *inline*: `\mintinline`.

## Referências

- [Post no reddit sobre a tipografia do TAoCP antes do TeX]
  (https://www.reddit.com/r/compsci/comments/2ksmde/what_did_the_art_of_computer_programming_look/)
- [Guia do Wikibooks](https://en.wikibooks.org/wiki/LaTeX)
- [História da codificação de
  fontes](http://www.lasca.ic.unicamp.br/pub/ctan/macros/latex/doc/encguide.pdf)
- [LaTeX Tutorials: a
  Primer](https://www.tug.org/twg/mactex/tutorials/ltxprimer-1.0.pdf)
- Elementos do Estilo Tipográfico versão 3.0, por Robert Bringhurst. Cosac
  Naify, 2008.
