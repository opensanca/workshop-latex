# Workshop: Introdução ao LaTeX (working title)

- Quem eu sou
- Conteúdo do curso
- Público-alvo
- Objetivos: não é ensinar todos os mínimos detalhes técnicos do LaTeX, mas
- focar em sua utilização. Ou seja, ao invés de ficar pensando em detalhes
- primeiro, vamos fazer exercícios! Também vamos aprender muita tipografia
    nessa aventura.

## História e filosofia

(Ideias: 

- vídeo do algorítimo de tipografia
- filosofia
- história do TAoCP
- )

Com o advento dos computadores, não demorou para que livros, artigos e outros
documentos começassem a ser editados digitalmente (TODO: pesquisar história da
tipografia digital). Acontece que a tabela ANSII nunca foi pensada com a
tradição tipográfica em mente, mas sim levando em conta as limitações dos
sistemas computacionais.

## Mão na massa

O LaTeX é uma linguagem de marcação de texto, como o HTML ou o Markdown. Isso
significa que você deve dizer ao computador como o texto deve ser formatado,
mas quem faz o trabalho sujo não é você. O LaTeX é bastante *semântico*, mais
do que as linguagens anteriores. O que o comando a seguir deve fazer?

    \section{Introdução}

Em geral, os comandos que utilizaremos em LaTeX começam com uma barra ` \ `,
seguida pelo nome do comando. Comandos podem ter argumentos, como no caso
acima.

### hello-world.tex

Vamos abrir o arquivo `hello-world.tex` e aprender como documentos são
organizados no LaTeX. Tudo o que está entre `\begin{document}` e
`\end{document}` será impresso pelo LaTeX. O que vem antes dessa parte é
conhecido como preâmbulo. O preâmbulo deste documento é apenas
`\documentclass{article}`. Perguntar o que o público acredita que este
comandos significa.

Agora, vamos compilar nosso documento. Utilizaremos o comando `lualatex`, que
é apenas uma das maneiras de compilar um documento utilizando o LaTeX. Também
quero demonstrar outros métodos (online, por exemplo). A escolha do `lualatex`
é justificada porque esse é o método moderno de compilar LaTeX, uma vez que
ele suporta fontes OpenType e Unicode.

O que acontece se eu adicionar o comando `\section{Introdução}` antes do
texto?

Agora, vamos mudar a classe do nosso documento para `minimal`. O que isso
significa? Quais classes existem além de `article` e `minimal`? O que acontece
com `\section` quando eu mudo para a classe `minimal`?

TODO: adicionar mais informações sobre classes e suas opções, como `a4paper` e
`11pt`;

Perguntar, aliás, o que são aquelas linhas que começam com `%` no topo do
arquivo, e por que não são impressas no documento final?

*Exercício* compilar o arquivo hello-world.tex com sucesso.

### espaco-branco.tex

Aqui temos dois parágrafos do começo de _O guia do mochileiro das galáxias._

Mostrar o espaço em branco que existe para o público. Perguntar o que eles
esperam que aconteça quando eu compilar o documento.

Múltiplos espaços em branco no LaTeX são ignorados: apenas um espaço em branco
é colocado entre as palavras. Assim, é difícil errar e acabar com espaçamento
a mais. Essa é apenas uma das milhares de maneiras nas quais o LaTeX é
inteligente. 

Para criar um novo parágrafo, devemos deixar um espaço em branco entre as
linhas. Novas linhas são ignoradas: para inserir uma linha, `\newline` ou `\\`.

*Exercício:* `espaco-branco-exercicio.tex`. Arrumar o arquivo, deixando os
espaços e parágrafos corretos. *TODO: exercício em si.*

Notar que nem tudo funcionará perfeitamente. Qual problemas encontramos? Sim,
os diacríticos não apareceram corretamente. Alguém saberia o motivo?

### poliglota-exercicio.tex

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

*Exercício*: adicionar o pacote `polyglossia` abaixo do `\documentclass` e
compilar o arquivo.

Quando o exercício terminar, mostrar o CTAN e como encontrar documentação para
os pacotes. Mostrar a documentação do `polyglossia` como exemplo.

### artigo-exercicio.tex

Agora, vamos olhar para um documento um pouco mais complexo, mas também mais
típico. `artigo-exemplo.tex` demonstra alguns conceitos interessantes em LaTeX.
Vamos começar pela organização de um aquivo `.tex`. Basicamente, ele é dividido
em um *preâmbulo* no qual estão os pacotes e opções que utilizaremos e o
*documento em si,* que começa a partir do comando `\begin{document}`.

Vamos explorar o preâmbulo para começar. A primeira linha que chama nossa atenção é:

    \documentclass[11pt,a4paper,oneside]{article}

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

Compilar o mesmo documento com várias opções diferentes e mostrar os
resultados.

Após o `\documentclass`, três pacotes são carregados: `polyglossia, blindtext`
e `hyperref`. Olhando o código-fonte, o que os dois últimos pacotes devem
fazer? Mudar o conteúdo do comando `\author` para o seguinte:

    \author{Rafael Beraldo \\
    \href{mailto:rberaldo@cabaladada.org}{\textless rberaldo@cabaladada.org \textgreater}

O que será impresso agora?

Agora, vamos adicionar o pacote `microtype` e ver quais diferenças encontramos.
Explicar que o `microtype` mexe nos espaços entre as palavras, lida com a
protusão de caracteres perto da margem direita, bem como cuida da expansão de
fontes.

Mostrar [o manual do
`microtype`](http://mirrors.ctan.org/macros/latex/contrib/microtype/microtype.pdf),
que tem exemplos de suas funcionalidades.

No corpo do documento, entre `\begin{document}` e `\end{document}` existem
vários comandos interessantes. Discutir o significado de `\frenchspacing` e
ensinar também o comando `\subsection`.

Compilar o arquivo e mostrar a quantidade de arquivos que foram produzidos. A
quantidade de arquivos produzidos é sempre muito grande, mas a maior parte pode
ser deletada sem problemas.

Compiladores LaTeX passam apenas uma vez pelo documento, produzindo o PDF
durante a compilação. Mas eles não pulam por todo o código, portanto certas
operações introduzem outros arquivos que guardam informações que serão usadas
mais tarde. Aqui vai uma lista de arquivos auxiliares:
https://en.wikibooks.org/wiki/LaTeX/Basics#Ancillary_files

Para evitar que tantos arquivos sejam mantidos, podemos utilizar o comando
`latexmk -c`. 

*Exercício*: transformar o arquivo `artigo-exercicio.tex` em um arquivo LaTeX e
compilá-lo. Mostrar o arquivo resolvido na tela de discutir, primeiro, como
implementá-lo com a plateia.

## ABNT
## Referências

- [Post no reddit sobre a tipografia do TAoCP antes do TeX:]
  (https://www.reddit.com/r/compsci/comments/2ksmde/what_did_the_art_of_computer_programming_look/)
- [Guia do Wikibooks](https://en.wikibooks.org/wiki/LaTeX)
