---
title: 'Computação Quântica para Cientistas da Computação'
date: 2019-06-14
permalink: /posts/2019/06/quant-comp/
tags:
  - Computação Quantica
  - Matemática
  - Computação
---

Escrevi esse post para pessoas que possuem alguma noção de computação e querem saber o que acontece dentro de um computador quântico, porém assim como eu se deparou com muita física e mesmo depois de lerem muito e assistirem vários vídeos ainda não acharam o que estavam procurando. Como funciona um computador quântico na perspectiva computacional, e não física.

# Computação Quântica

Em janeiro de 2019 a [IBM](https://www.ibm.com)  anunciou seu primeiro, e até então único, computador quântico "comercial". Bom, então agora que ele exite, toda nossa criptografia foi ameaçada e vamos resolver problemas que só sonhávamos em resolver... mas não é bem assim. O IBM Q System One, com seus 20 qbits(ainda vamos chegar lá), está mais para um símbolo. Ele não consegue superar um computador tradicional em problemas úteis, e mesmo que você queira um programa não útil rodadando em um computador quântico só para ver como é, isso pode se tornar uma tarefa bem difícil. E não digo pelo acesso à um computador quantico, a IBM disponibiliza um para qualquer pessoa usar no [IBM Q Experience](https://www.research.ibm.com/ibm-q/), o problema é entender o modelo de computação dele o suficiente para contruir um algoritmo e significar os resultados do seu programa.

# Como ele funciona

### Qbits 

Em um computador tradicional trabalhamos com bits, a menor unidade de mémoria que pode representar um Zero(0) ou um Um(1). No computador quantico temos o bit quântico, que também pode representar um Zero(0) ou um Um(1). Vamos chamar o bit clássico de cbit e o bit quântico de qbit.

Podemos dizer que o Qbit Zero(0) é representado pelo vetor abaixo:

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}" title="\begin{pmatrix} 0\\ 1 \end{pmatrix}" /> ou  em uma notação um pouco diferente $\|0>$

E o Qbit Um(1) por esse outro vetor: 

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}" title="\begin{pmatrix} 0\\ 1 \end{pmatrix}" /> ou  em uma notação um pouco diferente $\|1>$

Agora as coisas começam a ficar mais parecidas com uma copmutação tradicional.

Com cbits conseguimos fazer 4 operações clássicas:
1. Identidade: $f(x) = x$
2. Negação: $f(x) = \neg x$
3. Constatante 0: $f(x) = 0$
4. Constante 1: $f(x) = 1$

E podemos escrever essas operações como matrizes para aplica-las aos qbits:

1. Identidade:

O Qbit 0 continua 0 e o Qbit 1 continua 1

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;1&space;&&space;0\\&space;0&space;&&space;1&space;\end{pmatrix}&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}" title="Identidade 0" /> ou <img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;1&space;&&space;0\\&space;0&space;&&space;1&space;\end{pmatrix}&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}" title="Identidade 1" />

2. Negação:

O Qbit 0 se torna 1 e o Qbit 1 se torna 0

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;0&space;&&space;1\\&space;1&space;&&space;0&space;\end{pmatrix}&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}" title="Negação 0" /> ou <img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;0&space;&&space;1\\&space;1&space;&&space;0&space;\end{pmatrix}&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}" title="Negaçao 1" />

3. Constatante 0:

O Qbit 0 continua 0 e o Qbit 1 se torna 0

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;1&space;&&space;1\\&space;0&space;&&space;0&space;\end{pmatrix}&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}" title="Negação 0" /> ou <img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;1&space;&&space;1\\&space;0&space;&&space;0&space;\end{pmatrix}&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}" title="Negaçao 1" />

4. Constatante 1:

O Qbit 0 se torna 0 e o Qbit 1 continua 1

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;0&space;&&space;0\\&space;1&space;&&space;1&space;\end{pmatrix}&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}" title="Negação 0" /> ou <img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;0&space;&&space;0\\&space;1&space;&&space;1&space;\end{pmatrix}&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}" title="Negaçao 1" />


Vamos dar guardar essas 4 operações retornamos para elas mais tarde. Agora precisamos saber entender o conceito de Computação Reversível. 

No resumo, significa que se você sabe a operação que foi realizada e o resultado dessa operação, você consegue descobrir a entrada que foi utilizada. Um bom exemplo seria: se temos a operação de negação realizada e o resultado for 1, então a entrada tem que ser 0

$ \neg X = 1 \Leftrightarrow X = 0 $

Seguindo essa lógica percebemos que as operações de Identidade e Negação são reversíveis e as de Constante não!

Outra coisa importante de saber agora é que a computação quântica use exclusivamente operações que são reversíveis, e que todas os operadores quânticos são seus próprios inversos. Então se você aplicar um operador à uma entrada e novamente ao resultado, o resultado da segunda operação vai ser a própria entrada

$ f(f(X)) = X $

A operação de Negação é um bom exemplo para isso também

$ \neg(\neg X) = X $

Ok, sabendo de tudo isso vamos estudar outra operação, o [produto de tensores](https://en.wikipedia.org/wiki/Tensor_product). No resumo ela funciona seguindo a regra abaixo, pelo menos para os propósitos dessse blog.

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;X_0\\&space;X_1&space;\end{pmatrix}&space;\otimes&space;\begin{pmatrix}&space;Y_0\\&space;Y_1&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;X_0*Y_0\\&space;X_0*Y_1\\&space;X_1*Y_0\\&space;X_1*Y_1\\&space;\end{pmatrix}" title="\begin{pmatrix} X_0\\ X_1 \end{pmatrix} \otimes \begin{pmatrix} Y_0\\ Y_1 \end{pmatrix} = \begin{pmatrix} X_0*Y_0\\ X_0*Y_1\\ X_1*Y_0\\ X_1*Y_1\\ \end{pmatrix}" />

<img src="https://latex.codecogs.com/png.latex?\inline&space;\begin{pmatrix}&space;X_0\\&space;X_1&space;\end{pmatrix}&space;\otimes&space;\begin{pmatrix}&space;Y_0\\&space;Y_1&space;\end{pmatrix}&space;\otimes&space;\begin{pmatrix}&space;Z_0\\&space;Z_1&space;\end{pmatrix}&space;=&space;\begin{pmatrix}&space;X_0*Y_0*Z_0\\&space;X_0*Y_0*Z_1\\&space;X_0*Y_1*Z_0\\&space;X_0*Y_1*Z_1\\&space;X_1*Y_0*Z_0\\&space;X_1*Y_0*Z_1\\&space;X_1*Y_1*Z_0\\&space;X_1*Y_1*Z_1&space;\end{pmatrix}" title="\begin{pmatrix} X_0\\ X_1 \end{pmatrix} \otimes \begin{pmatrix} Y_0\\ Y_1 \end{pmatrix} \otimes \begin{pmatrix} Z_0\\ Z_1 \end{pmatrix} = \begin{pmatrix} X_0*Y_0*Z_0\\ X_0*Y_0*Z_1\\ X_0*Y_1*Z_0\\ X_0*Y_1*Z_1\\ X_1*Y_0*Z_0\\ X_1*Y_0*Z_1\\ X_1*Y_1*Z_0\\ X_1*Y_1*Z_1 \end{pmatrix}" />

E pra que precisamos saber disso ? Bom, na computação tradicional é fácil representar um valor com dois cbits, mas na computação quântica representar um valor com dois qbits é um pouco diferente. O valor de dois qbits `|01>` é o produto de tensores entre os qbits `|0>` e `|1>`


` |01> = |0>\otimes|1> `