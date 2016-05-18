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
arquivo, e por que não são imprimidas no documento final?

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

- artigo.tex mostra a organização de um arquivo LaTeX típico.
- opções de documentclass
- mais exemplos de pacotes
- page styles
- common filetypes

## ABNT
## Referências

- post no reddit sobre a tipografia do TAoCP antes do TeX:
  https://www.reddit.com/r/compsci/comments/2ksmde/what_did_the_art_of_computer_programming_look/
