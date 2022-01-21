+++
title = "Suavização de rótulos"
date = 2021-09-15
template = "ensaio.html"
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

Redes neurais artificiais profundas são modelos com uma enorme **capacidade** de expressar relações existentes nos dados. Ao mesmo tempo que isso confere poder e as tornam úteis para as mais variadas e complexas tarefas, parte dessas relações podem ser apenas "ruídos". Em outras palavras, coincidências podem ser confundidas pelos modelos como sendo relações verdadeiras, o que acaba sendo algo comum principalmente quando o conjunto de dados é pequeno ou a amostragem tem vieses ocultos significativos. A consequência mais direta desse tipo de problema é identificada na forma de sobreajuste (*overfitting*). No entanto, há consequências mais sutis como o **excesso de confiança** do modelo (*overconfidence*).

O <u>excesso</u> de confiança está relacionado a uma estimativa ruim da **incerteza** do resultado. Um bom modelo, não é apenas o que erra pouco durante os testes, mas aquele que diz o quão certo ou incerto ele está sobre aquele resultado. :calibração:

O label-smoothing, ou suavização dos rótulos, é uma técnica de regularização aplicada para reduzir tanto a ocorrência de *overfitting* quanto do excesso de confiança.

## Explicação intuitiva

Durante o treinamento de modelos para tarefas de classificação é comum que os dados utilizados tenham o label ( \\( y \\) ) da classe a qual pertencem, sendo \\( y \in \{0, 1\} \\) para classificação binária ou no formato de um vetor *one-hot encoding* para classificação em uma dentre múltiplas classes. Esse modo de representação contém, além da classe, a confiança sobre aquele rótulo - "Eu tenho **certeza** que é A ( \\( y=1 \\) )" ou "Eu tenho **certeza** que <u>não</u> é A ( \\( y=0 \\) )". Logo, além da classe correta, fornecemos durante o treinamento a informação de absoluta certeza ou de nenhuma incerteza.

Consequentemente, podemos reduzir possíveis excessos de confiança do modelo através dos rótulos. Para fazermos isso, o que anteriormente era certeza passa a conter uma leve incerteza - "Eu estou **quase certo** que é A ( \\( y=0.9 \\) )" ou "Eu estou **quase certo** que <u>não</u> é A ( \\( y=0.1 \\) )". Isso é a suavização dos rótulos ou *label smoothing*! Esse tipo de representação dos rótulos é chamada de *soft* (*softlabel*), enquanto a tradicional, apenas com 0s e 1s, é a *hard*.

## Detalhamento

Origem e uso básico

Incerteza derivada de especialistas

Destilação

Aplicação em ranqueamento



**side note** No livro *Deep Learning* (Goodfellow, Courville, Bengio) dizem que a técnica de suavização dos rótulos 
