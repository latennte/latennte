+++
template = "ensaio.html"
title = "Suavização de rótulos"
description = "A suavização de rótulos é uma técnica de regularização que atua controlando a tendência ao excesso de confiança observado em redes neurais profundas."  
date = 2021-09-15
updated = 2022-03-15
description = "Seu modelo está errando por excesso de confiança? Suavizar os rótulos pode ajudar."
[extra]
status = "em progresso"
uncertainty = "baixa"
+++

<!-- 
* TODO Tópicos
- [] Overfitting
- [] Overconfident
  + [] Incerteza
  + [] Probabilidade
  + [] Origem dessa incerteza
- [] Explicação intuitiva
  + [] O que é label-smoothing?
- [] Benefícios
- [] Formas de se atribuir as probabilidades
- [] Aplicações além da classificação  
 -->

## Motivação

Redes neurais artificiais profundas são modelos com enorme **capacidade** de expressar relações existentes nos dados. Ao mesmo tempo que isso confere poder e as tornam úteis para tarefas complexas e variadas, parte dessas relações podem ser apenas "ruídos". Em outras palavras, coincidências podem ser confundidas pelos modelos como sendo relações verdadeiras, o que acaba sendo algo comum principalmente quando o conjunto de dados é pequeno ou a amostra contém vieses significativos. A consequência mais direta desse tipo de problema aparece na forma de sobre-ajuste (*overfitting*). No entanto, há consequências mais sutis como o **excesso de confiança** do modelo (*overconfidence*). 
<!-- <aside>Observação</aside>  -->

O excesso de confiança está relacionado a uma estimativa ruim da **incerteza** do modelo sobre o resultado. Um bom modelo, não é apenas aquele que erra pouco durante os testes, mas o que diz o quão certo ou incerto ele está sobre o resultado apresentado.

A técnica de suavização dos rótulos (*label-smoothing*) é um método de regularização aplicado com o objetivo de reduzir tanto a ocorrência de sobre-ajuste quanto o excesso de confiança do modelo.

## Explicação intuitiva

Durante o treinamento de modelos para tarefas de classificação é comum que os dados utilizados tenham o rótulo $y$ da classe a qual pertencem, sendo $ y \in \\{0, 1\\} $ para classificação binária ou no formato de um vetor *one-hot encoding* para classificação em uma dentre múltiplas classes. Esse modo de representação contém, além da classe, a confiança sobre aquele rótulo - "Eu tenho **certeza** que é A $(y=1)$" ou "Eu tenho **certeza** que **não** é A $(y=0)$". Assim, além da classe correta, fornecemos durante o treinamento a informação de absoluta certeza ou, dito de outra forma, nenhuma incerteza.

Consequentemente, podemos reduzir possíveis excessos de confiança do modelo através dos rótulos. Para fazermos isso, o que anteriormente era certeza passa a conter uma leve incerteza - "Eu estou **quase certo** que é A $(y=0.9)$" ou "Eu estou **quase certo** que <u>não</u> é A $(y=0.1)$". Isso é a suavização dos rótulos ou *label smoothing*! Esse tipo de representação dos rótulos é chamada de suave (*soft*), enquanto a tradicional, apenas com 0s e 1s, é a rígida (*hard*).

**inserir imagem*

## Detalhamento

<aside>A Inception-v3 foi desenvolvida para ser aplicada na classificação de imagens do dataset ImageNet. Como o dataset possui 1000 classes temos $K=1000$.</aside>

Na literatura, a referência primária da técnica de suavização de rótulos é o trabalho de [Szegedy et al. (2016)](https://arxiv.org/abs/1512.00567). Nesse trabalho, no qual é descrita a arquitetura da rede neural Inception-v3, os autores suavizaram os rótulos uniformemente. Assim, a classe correta de uma entrada $x$ tinha um rótulo $y = 1 - \epsilon + \frac{\epsilon}{K}$ e cada uma das outras 999 classes incorretas $(K-1)$ possuiam o rótulo $\frac{\epsilon}{K}$.  


Incerteza derivada de especialistas

Destilação

Aplicação em ranqueamento

$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

\\[ y \in \\{0, 1\\} \\]


<aside>No livro *Deep Learning* (Goodfellow, Courville, Bengio) dizem que a técnica de suavização dos rótulos.</aside>

## Referências

Szegedy, C., Vanhoucke, V., Ioffe, S., Shlens, J., & Wojna, Z. (2015). Rethinking the Inception Architecture for Computer Vision. arXiv:1512.00567 [cs]. [link](http://arxiv.org/abs/1512.00567)


