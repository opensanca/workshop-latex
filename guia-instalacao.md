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

## GNU/Linux

No GNU/Linux, você deve instalar o TeX Live. Os comandos baixo instalam os
pacotes mais completos.

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
[MiKTeX](http://miktex.org/). O MiKTeX inclui um IDE chamado TeXworks. Para
mais informações, veja o [manual do projeto](http://docs.miktex.org/manual/)
(em inglês).

## OS X

Para OS X, o TUG (Tex Users Group) disponibiliza a distribuição
[MacTeX](https://tug.org/mactex/), que inclui uma série de aplicativos GUI como
o IDE TeXshop. Para mais ajuda, veja [esta
seção](https://www.tug.org/mactex/gettinghelp.html) no site do MacTeX.

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
