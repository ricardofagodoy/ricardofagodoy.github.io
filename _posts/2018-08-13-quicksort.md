---
layout: post
title: 'Algoritmo: QuickSort'
tags: [algoritmo, quicksort]
---

 **QuickSort** é um famoso algoritmo de ordenação que apesar de ser bastante simples é realmente utilizado na prática, por exemplo, no método *sort* de [Arrays](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html) do Java 1.8.

Ele utiliza a estratégia **Divide & Conquer** que consiste em transformar um problema difícil em algo pequeno e simples de ser resolvido.

Por exemplo, ordenar um array vazio ou com apenas 1 elemento é muito fácil, nada precisa ser feito. Assim como ordenar um array com 2 valores também é bastante simples, basta compará-los e se necessário fazer uma troca de posições.

Essa estratégia é [quase](https://en.wikipedia.org/wiki/Dynamic_programming) sempre implementada com **recursão**, chamando o mesmo método diversas vezes, sempre com um problema um pouco menor que o anterior, até atingir o caso banal (condição de parada).

## Como QuickSort funciona

Dado um array de inteiros **[4, 7, 3, 1, 9, 2]**

1) É escolhido um **pivô** para ser o primeiro valor a ser colocado na posição correta. 

Vamos escolher o **4** (simplesmente por ser o primeiro).

2) Os demais valores do array são dividos em dois sub-arrays: **menores e maiores que o pivô:**

**[3, 1, 2] 4 [7, 9]**

3) A função é chamada novamente para os dois sub-arrays obtidos, e os resultados são concatenados.

**qsort([3, 1, 2]) + [4] + qsort(7, 9)**

4) O processo se repete até que a condição de parada seja atingida:

**Receber um array vazio ou com apenas 1 elemento.**

5) Quando a condição de parada for obtida dos dois lados, **os resultados serão retornados na pilha de chamadas, até a primeira função.**

6) Obtemos o array **[1, 2, 3, 4, 7, 9]**.
 
<br/>

> Veja a imagem abaixo para o array [3, 2, 1, 5, 4]:

![quicksort]({{ site.baseurl }}/assets/img/quicksort.png)

(*imagem retirada do livro [Grokking Algorithms](https://www.amazon.com/Grokking-Algorithms-illustrated-programmers-curious/dp/1617292230)*)

## Implementação

Veja uma das formas de implementar o QuickSort em JavaScript:

<script src="https://gist.github.com/ricardofagodoy/8ec12fdf4fce07c362aace2d5ec739f9.js"></script>

Você pode copiar o exemplo acima e executá-lo com **NodeJS** se quiser.

## Complexidade

Apesar de simples, o QuickSort possui um desempenho muito bom:

  Cenário     |    Big O
------------- | ----------
 Melhor/médio |   **O(n *log* n)**
    Pior      |   **O($$n^2$$)**

Desde a primeira iteração e à cada chamada com os sub-arrays, percorremos todos os valores do array recebido, ou seja, **n**.

A cada chamada recursiva, ~~em média~~ quebramos nosso problema pela metade, fazendo a **altura da pilha de chamadas ser (log n).**

![quicksort]({{ site.baseurl }}/assets/img/quicksort2.png)

(*imagem retirada do livro [Grokking Algorithms](https://www.amazon.com/Grokking-Algorithms-illustrated-programmers-curious/dp/1617292230)*)

Dessa forma, nos casos **médios e ótimos**, a complexidade é **n * log n = O (n *log* n)**.

Já no pior dos casos, o pivô escolhido é sempre um extremo, fazendo **um dos sub-arrays ser sempre vazio**. Isso ocorre ao tentar ordenar um array que já está ordenado. 

Nesse caso, haverá **n** passos na pilha de chamada: **n * n = O($$n^2$$)**.

> Para evitar esse cenário a escolha do pivô normalmente é feita de forma aleatória, sendo praticamente impossível cair no pior caso!

Vale a pena dizer ainda que existem implementações mais complexas desse algorítmo, como o [Dual-Pivot Quicksort](https://www.geeksforgeeks.org/dual-pivot-quicksort/) que garante menores chances de chegar ao pior caso.

## Finalizando

Acabamos de olhar mais a fundo o **QuickSort** clássico e não há muito mais o que dizer sobre ele. É simples, todos com certeza estudamos sobre ele na faculdade, mas é sempre bom relembrar 😎

Deixo uma sugestão do livro [**Grokking Algorithms**](https://www.amazon.com/Grokking-Algorithms-illustrated-programmers-curious/dp/1617292230) do qual retirei as imagens. Se trata de um livro que explica de forma lúdica e leve conceitos sobre estruturas de dados e algorítmos para ~~leigos e~~ desenvolvedores que querem relembrar o assunto.

**Até a próxima!**