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

Em janeiro de 2019 a [IBM](https://www.ibm.com)  anunciou seu primeiro, e até então único, computador quântico "comercial". Bom, então agora que ele existe, toda nossa criptografia foi ameaçada e vamos resolver problemas que só sonhávamos em resolver... mas não é bem assim. O IBM Q System One, com seus 20 qbits(ainda vamos chegar lá), está mais para um símbolo. Ele não consegue superar um computador tradicional em problemas úteis, e mesmo que você queira um programa não útil rodadando em um computador quântico só para ver como é, isso pode se tornar uma tarefa bem difícil. E não digo pelo acesso à um computador quantico, a IBM disponibiliza um para qualquer pessoa usar no [IBM Q Experience](https://www.research.ibm.com/ibm-q/), o problema é entender o modelo de computação dele o suficiente para contruir um algoritmo e significar os resultados do seu programa.

Para isso vamos passar por alguns conceitos nesse post.

## Qbits 

Em um computador tradicional trabalhamos com bits, a menor unidade de mémoria que pode representar um Zero(0) ou um Um(1). No computador quantico temos o bit quântico, que também pode representar um Zero(0) ou um Um(1). Vamos chamar o bit clássico de cbit e o bit quântico de qbit.

Podemos dizer que o Qbit Zero(0) é representado pelo vetor abaixo:

<img src="https://latex.codecogs.com/png.latex?\inline&space;\dpi{200}&space;\tiny&space;\begin{pmatrix}&space;1\\&space;0&space;\end{pmatrix}" title="\begin{pmatrix} 0\\ 1 \end{pmatrix}" /> ou  em uma notação um pouco diferente `|0>`

E o Qbit Um(1) por esse outro vetor: 

<img src="https://latex.codecogs.com/png.latex?\inline&space;\dpi{200}&space;\tiny&space;\begin{pmatrix}&space;0\\&space;1&space;\end{pmatrix}" title="\begin{pmatrix} 0\\ 1 \end{pmatrix}" /> ou  em uma notação um pouco diferente `|1>`

Agora as coisas começam a ficar mais parecidas com uma copmutação tradicional.

## Operações com bits

Com cbits conseguimos fazer 4 operações clássicas:
1. Identidade: $f(x) = x$
2. Negação: $f(x) = \neg x$
3. Constatante 0: $f(x) = 0$
4. Constante 1: $f(x) = 1$

E podemos escrever essas operações como matrizes para aplica-las aos qbits:

**Identidade**:

O Qbit 0 continua 0 e o Qbit 1 continua 1

![](/images/blog_quantum/id0.png)
ou
![](/images/blog_quantum/id1.png)


**Negação**:

O Qbit 0 se torna 1 e o Qbit 1 se torna 0

![](/images/blog_quantum/not0.png)
ou ![](/images/blog_quantum/not1.png)

**Constatante 0**:

O Qbit 0 continua 0 e o Qbit 1 se torna 0

![](/images/blog_quantum/const00.png)
ou ![](/images/blog_quantum/const01.png)


**Constatante 1**:

O Qbit 0 se torna 1 e o Qbit 1 continua 1

![](/images/blog_quantum/const10.png)
ou ![](/images/blog_quantum/const11.png)


Vamos dar guardar essas 4 operações retornamos para elas mais tarde. 

## Computação Reversível

Agora precisamos saber entender o conceito de Computação Reversível. 

No resumo, significa que se você sabe a operação que foi realizada e o resultado dessa operação, você consegue descobrir a entrada que foi utilizada. Um bom exemplo seria: se temos a operação de negação realizada e o resultado for 1, então a entrada tem que ser 0

$ \neg X = 1 \Leftrightarrow X = 0 $

Seguindo essa lógica percebemos que as operações de Identidade e Negação são reversíveis e as de Constante não!

Outra coisa importante de saber agora é que a computação quântica use exclusivamente operações que são reversíveis, e que todas os operadores quânticos são seus próprios inversos. Então se você aplicar um operador à uma entrada e novamente ao resultado, o resultado da segunda operação vai ser a própria entrada

$ f(f(X)) = X $

A operação de Negação é um bom exemplo para isso também

$ \neg(\neg X) = X $

## Produto de tensores 

Ok, sabendo de tudo isso vamos estudar outra operação, o [produto de tensores](https://en.wikipedia.org/wiki/Tensor_product). No resumo ela funciona seguindo a regra abaixo, pelo menos para os propósitos dessse blog.

![](/images/blog_quantum/tensor2.png)


![](/images/blog_quantum/tensor3.png)


E pra que precisamos saber disso ? Bom, na computação tradicional conseguimos representar um valor com dois ou mais cbits (`00`, `011`, `1110`), mas na computação quântica representar um valor com dois qbits é um pouco diferente. O valor de dois qbits `|10>` é o produto de tensores entre os qbits `|1>` e `|0>`


$ \|10> = \|0>\otimes\|1> $

ou, na forma matricial

![](/images/blog_quantum/tensor10.png)


o que também vale para uma quantidade maior de qbits

![](/images/blog_quantum/tensor100.png)


E essa também é uma operação reversível, dado um vetor `|10>` podemos fatora-los nos qbits `|1>` e `|0>`.

## Operação CNot

Uma operação bem útil com bits é a negação condicional, também chamada de CNot. Ela recebe dois bits, um de controle e um é a entrada. Caso o bit de controle seja 1, a entrafa é negada, caso o bit de controle seja zero, a entrada continua igual.
Assim como as outras operações, ela pode ser representada como uma matriz

![](/images/blog_quantum/cnot.png)

![](/images/blog_quantum/cnot01.png)

![](/images/blog_quantum/cnot11.png)


Como podemos ver, essa operação além de ser reversível é a sua própria inversa.

![](/images/blog_quantum/cnot10.png)

E assim como na computação tradicional a porta NAND é usada para construir operações mais complexas e interessantes, usaremos o CNOT para contruir operações mais interessantes e complexas na computação quântica.

### Recapitulando 

- Aprendemos a representar bits na forma vetorial
- Aprendemos a fazer operações nesses bits com multiplicações 
- Sabemos que a computação quântica só usa operações reversíveis, e essas operações - são seus próprios inversos
- Aprendemos que estados com mais de um bit são o produto de tensores entres os bits individuais.
- E por fim aprendemos o CNOT


## Qbits e Superposição

Um qbit é representado por um vetor ![](/images/blog_quantum/qbit.png) onde **a** e **b** são números complexos e $\left \| a \right \|^2 + \left \| b \right \|^2 = 1$

os vetores ![](/images/blog_quantum/qbit0.png) e ![](/images/blog_quantum/qbit1.png) que vimos até agora se encaixam nessa definição.

Mas não se preocupe com a parte complexa desses números, neste blog só vamos usar números reais :)

Outros exemplos de Qbits são:

![](/images/blog_quantum/tiposqbits.png)

Mas se ![](/images/blog_quantum/qbit0.png) significa 0 e ![](/images/blog_quantum/qbit1.png) significa 1, o que seria ![](/images/blog_quantum/qbits.png) ? Ele é um qbit em superposição

Quando temos essa superposição, signica que ele é tanto 0 quanto 1, e nesse estado é como se a computação esteja sendo feita tanto para 0 quanto para 1. Mas isso não é um resultado útil neh ? Ao final de toda computação quantica precisamos passar nossos qbits por uma operação de medição, que colapsa esse qbit ou para 0 ou para 1.

Um qbit ![](/images/blog_quantum/qbit.png) colapsa para 0 com probabilidade $\left \| a \right \|^2$ e colapsa para 1 com probabilidade $\left \| b \right \|^2$.

Então quando falamos que o qbit ![](/images/blog_quantum/qbit1.png) significa 1, na verdade estavamos dizendo que ele tem probabilidade 0 de colapsar para o valor 0 tem probabilidade 1 de colapsar para o valor 1 quando for medido.

Um qbit ![](/images/blog_quantum/qbit1.png) tem probabilidade 0.5 de colapsar para 0 e probabilidade 0.5 de colapsar para 1.

Note também que podemos ter multiplos qbits em superposição usando o produto de tensores

![](/images/blog_quantum/qbits2.png)

como $\left \| \frac{1}{2} \right \|^2 = \frac{1}{4}$, e $\frac{1}{4}+\frac{1}{4}+\frac{1}{4}+\frac{1}{4} = 1$, esse qbit tem probabilidade 1/4 de colapsar para $\left\|00\right>$, $\left\|01\right>$, $\left\|10\right>$, $\left\|11\right>$.