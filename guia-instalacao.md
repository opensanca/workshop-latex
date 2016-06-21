# Como obter o LaTeX

Arquivos do tipo `.tex` podem ser abertos em qualquer editor de texto. No
entanto, para que você possa compilar esses arquivos em `.pdf`, por exemplo, é
necessário instalar o que é conhecido como uma distribuição LaTeX. A
distribuição que você deve usar varia de acordo com sua plataforma. Este guia
não é exaustivo, porém as distribuições indicadas abaixo são as mais populares
para cada plataforma.

## Sumário

- [GNU/Linux](#gnulinux)
  - [Ubuntu e Debian](#ubuntu-e-debian)
  - [Fedora](#fedora)
  - [Arch](#arch)
  - [Gentoo](#gentoo)
  - [IDEs](#ides)
- [Windows](#windows)
- [OS X](#os-x)
- [Editores web](#editores-web)
- [Testando a instalação](#testando-a-instalação)

## GNU/Linux

No GNU/Linux, você deve instalar o TeX Live. Os comandos baixo instalam os
pacotes mais completos, isto é, que contém o maior número de pacotes
(extensões) incluídas no TeX Live. Selecionamos as distribuições mais
populares. Caso sua distribuição não esteja nesta lista, consulte seu manual ou
wiki, ou entre em contato com nosso canal no Slack:
[#latex](https://opensanca.slack.com/archives/latex).

### Ubuntu e Debian

    sudo apt-get install texlive-full

### Fedora

    sudo dnf install texlive-scheme-full

### Arch

    sudo pacman -S texlive-most

### Gentoo

    sudo emerge --ask texlive

### IDEs

O TeX Live não incluiu uma ferramenta GUI por padrão, mas as opções para
usuários de GNU/Linux são muitas. Embora essa lista não seja exaustiva, minha
experiência diz que as IDEs abaixo são as mais populares.

- [Gummi; the simple LaTeX editor](https://github.com/alexandervdm/gummi) (GTK)
- [Kile](http://kile.sourceforge.net/) (qt)
- [LaTeXila](https://wiki.gnome.org/Apps/LaTeXila) (GTK)
- [LyX](http://www.lyx.org/)

## Windows

Para computadores rodando Windows, a distribuição mais popular é o
[MiKTeX](http://miktex.org/). O MiKTeX inclui um IDE chamado TeXworks.

### Instalação e configuração do MiKTeX

1. Vá até [miktex.org/download](http://miktex.org/download) e escolha a opção
   _other downloads_ para baixar o [Basic MiKTeX 64-bit Net
   Installer](http://mirrors.ctan.org/systems/win32/miktex/setup/basic-miktex-2.9.5997-x64.exe).

2. Instale o MiKTeX usando as opções padrão.

3. Essa instalação do MiKTeX é bastante básica. Não há suporte para a línguas
   portuguesa, por exemplo, e vários pacotes — que são como extensões do LaTeX
   — não estão instalados. A seguir, vamos instalar praticamente todos os
   pacotes extras. Para isso, a partir do menu Iniciar abra _MiKTeX 2.9 →
   Maintenance (Admin) → MiKTeX Settings (Admin)_.

   ![Tela inicial do MiKTeX Settings](img/guia-instalacao/miktex-config-1.png
   "Tela inicial do MiKTeX Settings")

4. Clique na aba _Packages_. Note que várias categorias, como _Applications_ e
   _Fonts_ estão selecionadas, mas a caixa está acinzentada. Isso significa que
   essa categoria está apenas parcialmente instalada.

   ![Aba Packages com várias categorias instaladas
   parcialmente](img/guia-instalacao/miktex-config-2.png "Aba Packages com
   várias categorias instaladas parcialmente")

5. Selecione as categorias _Applications, BibTeX, Fonts, Formats, Language
   Support, MiKTeX 2.9 executables, MiKTeX 2.9 packages_ e _Uncategorized_,
   como na imagem abaixo, e clique em _OK_.

   ![Quase todas as categorias foram selecionadas para
   instalação](img/guia-instalacao/miktex-config-3.png "Quase todas as
   categorias foram selecionadas para instalação")

6. O MiKTeX irá avisar que muitos pacotes serão instalados. Clique em _Proceed_
   para continuar.

   ![Diálogo dizendo quantos pacotes serão
   instalados](img/guia-instalacao/miktex-config-4.png "Diálogo dizendo quantos
   pacotes serão instalados")

7. O processo de instalação irá começar. A instalação pode durar algumas horas,
   dependendo da velocidade da sua conexão. 

   ![Janela com o progresso da instalação dos
   pacotes](img/guia-instalacao/miktex-config-5.png "Janela com o progresso da
   instalação dos pacotes")

8. Quando a instalação estiver completa, abra o TeXworks, o IDE que vem por
   padrão com a distribuição MiKTeX. No canto superior esquerdo, há um botão
   verde que compila o documento. Ao eu lado, uma caixa para escolher o
   programa que será usado para compilar o arquivo. Para nosso curso, usaremos
   o LuaLaTeX, conforme destacado em vermelho na figura abaixo.

   ![É necessário mudar o programa de compilação de pdfLaTeX para
   LuaLaTeX](img/guia-instalacao/texworks.png "É necessário mudar o
   programa de compilação de pdfLaTeX para LuaLaTeX")

7. Copie o código abaixo no TeXworks e clique no botão verde para compilar.

    \documentclass{article}
    \usepackage{polyglossia,blindtext,hyperref,fontspec,microtype,graphicx,
    enumerate,mathtools}
    \setdefaultlanguage{brazil}

    \begin{document}
    Olá, mundo. Hoje é \today.
    \end{document}

   Um PDF deve aparecer, como na figura abaixo:

   ![Documento compilado ao lado do código-fonte no
   TeXworks](img/guia-instalacao/compilacao.png "Documento compilado ao
   lado do código-fonte no TeXworks")

Em caso de dúvidas, consulte [nosso canal no Slack do
opensanca](https://opensanca.slack.com/archives/latex).

## OS X

Para OS X, o TUG (Tex Users Group) disponibiliza a distribuição
[MacTeX](https://tug.org/mactex/), que inclui uma série de aplicativos GUI como
o IDE TeXshop. Para mais ajuda, veja [esta
seção](https://www.tug.org/mactex/gettinghelp.html) no site do MacTeX.

O usuário Malte Helmhold criou um [tutorial no
YouTube](https://www.youtube.com/watch?v=WvGQ2Mrhf7g) ensinando a instalar o
MacTeX.

## Editores web

Existem vários editores online de LaTeX. Os primeiros resultados no Google
incluem:

- [Overleaf](https://www.overleaf.com) (plano grátis começa com 100mb)
- [Papeeria](http://papeeria.com/) (plano grátis permite um projeto ativo por
  vez)
- [ShareLaTeX](https://www.sharelatex.com/) (plano grátis para apenas um
  colaborador)

Para nosso curso, usaremos o Overleaf. Escolhi apenas um editor para padronizar
a experiência durante o curso. Você pode se cadastrar no serviço em
[overleaf.com/signup](https://www.overleaf.com/signup). Também temos um código
de referral para começar com 100mb a mais em
[overleaf.com/signup?ref=348ee7dc367e](https://www.overleaf.com/signup?ref=348ee7dc367e).

## Testando a instalação

Para testar sua instalação, compile o seguinte arquivo, que contém todos os
pacotes que utilizaremos em nosso curso. É necessário utilizar o LuaLaTeX para
que a compilação seja bem-sucedida.

    \documentclass{article}
    \usepackage{polyglossia,blindtext,hyperref,fontspec,microtype,graphicx,
    enumerate,mathtools}
    \setdefaultlanguage{brazil}

    \begin{document}
    Olá, mundo. Hoje é \today.
    \end{document}

Em caso de dúvidas, consulte [nosso canal no Slack do
opensanca](https://opensanca.slack.com/archives/latex).
