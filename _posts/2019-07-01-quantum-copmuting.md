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

$$
\left(\begin{array}{c} 
1\\
0
\end{array}\right)
$$ 

E o Qbit Um(0) por esse outro vetor: 

$$
\left(\begin{array}{c} 
0\\
1
\end{array}\right)
$$ 

Agora as coisas começam a ficar mais parecidas com uma copmutação tradicional.

Com cbits conseguimos fazer 4 operações clássicas:
> 1. Identidade : 1->1, 0->0;
> 2. Negação : 1->0, 0->1;
> 3. Contatante 0 : 1->0, 0->0;
> 4. Contante 1 : 1->1, 0->1.

E podemos escrever essas operações como matrizes para aplica-las aos qbits:

> 1. Identidade:

  $$
  \left(\begin{array}{cc} 
  1 & 0\\
  0 & -1
  \end{array}\right)
  \left(\begin{array}{c} 
  1\\ 
  0
  \end{array}\right)
  $$ 