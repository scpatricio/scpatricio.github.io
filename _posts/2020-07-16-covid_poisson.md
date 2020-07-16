---
title: "how can i modeling the covid pandemic?"
date: 2020-07-16
tags: [statistic, modeling]
header:
  image: "/images/likelihood/head.jpeg"
excerpt: "what is it?"
---

Se voce ainda nao percebeu, nós estamos em meio a uma pandemia (até
agora a maior deste século), e com uma doença numa escala global vem o
acesso à uma quantidade massiva de dados. E o que queremos fazer com
isso? Modelagem! Óbvio.

Então sim, neste post irei comentar um pouco sobre a modelagem dos dados
da covid, especialmente do ponto de vista teórico, e também falar um
pouquinho sobre os problemas que podemos ter quando tentamos modelar os
dados do Brasil.

Para começar, vamos definir que *Y*<sub>*t*</sub> representa o número
total de casos no dia *t*, onde representa a quantidade de dias desde o
primeiro caso. E considerar que 𝔼(*Y*<sub>*t*</sub>) = *λ*(*t*) , ou
seja, em média teremos que *Y*<sub>*t*</sub> assume um valor *λ*(*t*).

Agora vamos conversar um pouco sobre *λ*(*t*). Podemos assumir que
*λ*(*t*) = *N*<sub>0</sub>*F*(*t*), onde *F*(*t*) é alguma distribuição
acumulada. Podemos assumir várias formas para *F*(*t*), tudo depende dos
dados e do comportamento da pandemia em outros países que já passaram
por ela.

Mais especificamente, teremos que a distribuição acumulada *F*(*t*) está
associada a um parâmetro *θ* ∈ *Θ*, que teremos que estimar. Então,
agora temos
*λ*(*t*; *θ*, *N*<sub>0</sub>) = *N*<sub>0</sub>*F*(*t*; *θ*), e o que
nos resta é estimar o parâmetro
*θ*<sup>\*</sup> = (*N*<sub>0</sub>, *θ*)′. Essa estimativa pode ser
realizada de várias formas, deixa eu comentar alguma delas.

A primeira delas é buscar o valor mais pausível de *θ*<sup>\*</sup>
minimizando a distancia entre 𝔼(*Y*<sub>*t*</sub>) e
*λ*(*t*; *θ*, *N*<sub>0</sub>), o famoso método de mínimos quadrados. O
problema de usar esse método destes dados, é que ele modela apenas a
média, ignorando o fato de que a variância de *Y*<sub>*t*</sub> aumenta
junto com a média, ou seja, quanto maior o valor obervado de
*Y*<sub>*t*</sub>, maior será sua variância.

Uma forma de contornar esse problema é utilizar o método de mínimos
quadrados ponderados e minimzar a distancia entre
*Y*<sub>*t*</sub>/*λ*(*t*; *θ*, *N*<sub>0</sub>). Esse método acaba
estabilizando a variação observada nos dados, mas por fim estamos
modelando apenas a variação dos dados, ao invés da média em si, já que
assim temos 𝔼\[*Y*<sub>*t*</sub>/*λ*(*t*; *θ*, *N*<sub>0</sub>)\] = 1.

Entao uma forma de modelarmos a média e variação dos dados ao mesmo
tempo, é assumir que *Y*<sub>*t*</sub> possua distribuissão poisson com
parâmetro *λ*(*t*; *θ*, *N*<sub>0</sub>) - normalmente usamos a notação
*Y*<sub>*t*</sub> ∼ *P**o**i**s*(*λ*(*t*; *θ*, *N*<sub>0</sub>)) -
porque daí temos que
𝔼(*Y*<sub>*t*</sub>) = 𝕍𝔸ℝ(*Y*<sub>*t*</sub>) = *λ*(*t*; *θ*, *N*<sub>0</sub>),
ou seja, consideramos que a variância aumenta junto com a média dos
valores observados, mais especificamente, aumenta na mesma proporção.

Então, assumindo
*Y*<sub>*t*</sub> ∼ *P**o**i**s*(*λ*(*t*; *θ*, *N*<sub>0</sub>)),
podemos estimar *θ*<sup>\*</sup> = (*N*<sub>0</sub>, *θ*)′ via o método
de máxima verossimilhança. Então vamos à ele:

Como assumidos que
*Y*<sub>*t*</sub> ∼ *P**o**i**s*(*λ*(*t*; *θ*, *N*<sub>0</sub>)),
assumimos que

$$
\\mathbb{P}(Y\_t = k) = \\frac{exp\\{ -\\lambda(t; \\theta, N\_0)\\}\[\\lambda(t; \\theta, N\_0)\]^k}{k!},
$$
e consequentemente, a função de verossmilhança vai ser dada por:

$$
L(\\theta, N\_0; Y\_t = y\_t) = \\prod\_{t =0}^n \\frac{exp\\{ -\\lambda(t; \\theta, N\_0)\\}\[\\lambda(t; \\theta, N\_0)\]^{y\_t}}{y\_t!}.
$$

Simples, né?! Então vamos à estimação via máxima verossimilhança., que é
basicamente maximizar
*L*(*θ*, *N*<sub>0</sub>; *Y*<sub>*t*</sub> = *y*<sub>*t*</sub>) ou
ℓ(*θ*, *N*<sub>0</sub>; *Y*<sub>*t*</sub> = *y*<sub>*t*</sub>) = log *L*(*θ*, *N*<sub>0</sub>; *Y*<sub>*t*</sub> = *y*<sub>*t*</sub>),
que é dada por

$$
\\hat{\\theta}\* = \\max\_{\\theta^\* = (\\theta, N\_0)'}\\sum\_{t=0}^n y\_t \\log \[\\lambda(t; \\theta, N\_0)\] - \\lambda(t; \\theta, N\_0).
$$
Pronto, agora é só inserir os dados, e maximizar. Todo o problema
complexo de modelagem foi resumido à um problema de otimização.

Pontos interessantes
--------------------

Ok, digamos que já estimamos o vator de parãmetros
*θ*<sup>\*</sup> = (*θ*, *N*<sub>0</sub>)′. Vamos responder algumas
perguntas de interesse:

### No final, quantas pessoas serão contaminadas?

Ah, essa pergunta é simples de responder ! Basta tomarmos o limite
quando *t* → ∞. Dessa forma, temos
lim<sub>*t* → ∞</sub>*λ*(*t*; *θ*, *N*<sub>0</sub>) = lim<sub>*t* → ∞</sub>*N*<sub>0</sub>*F*(*t*; *θ*) = *N*<sub>0</sub>.
Então no final da pandemia teremos *N*<sub>0</sub> pessoas contaminadas.

### Como eu faço previsão?

Então, a previsão é mais simples do que você imagina. Se voce quiser
fazer a previsão para o tempo *t* + *k*, basta tomar como previsão o
valor esperado de *Y*<sub>*t* + *k*</sub> dado os dados que já
observamos {*Y*<sub>*k*</sub> : *k* = 0, …, *t*}, ou seja,
𝔼\[*Y*<sub>*t* + 1</sub>|{*Y*<sub>*k*</sub> : *k* = 0, …, *t*}\] = *λ*(*t* + *k*; *θ*, *N*<sub>0</sub>)
.

### Como calculo a taxa de reprodutibilidade (*R*<sub>0</sub>)?

No tempo *t*, podemos definir o *R*<sub>0</sub> como sendo
$$
R\_0 = \\frac{\\lambda(t; \\theta, N\_0)-\\lambda(t-1; \\theta, N\_0)}{\\lambda(t-1; \\theta, N\_0)}.
$$

### E o número médio de novos casos?

Então, esse também é bem simples, é apenas a diferença no valor esperado
de *Y* nos tempos *t* + *k* e *t* + *k* − 1:
*n*<sub>*t* + *k*</sub> = 𝔼\[*Y*<sub>*t* + *k*</sub> − *Y*<sub>*t* + *k* − 1</sub>\] = *λ*(*t* + *k*; *θ*, *N*<sub>0</sub>) − *λ*(*t* + *k* − 1; *θ*, *N*<sub>0</sub>)

Bom, espero que você tenha conseguido entender a ideia por trás desta
modelagem. Podemos usar-la não somente para modelar os dados de novos
casos, mas também a contagem de óbitos. E isso não se restringe à dados
de pandemias, mas existem vários outros problemas que podem ser
abordados dessa forma, inclusive quando fazemos inferencia estatística
utilizando tábuas de vida, o que é muito comum na demografia e também em
ciencias atuariais.

Mas voltando à falar da pandemia, especificamente sobre os dados do
Brasil. Querer representar o comportamento da pandemia no Brasil apenas
com um modelo, é um tanto quanto pretencioso. O Brasil é um país com
dimensões continentais e extremamente heterogênio. Essa heterogeneidade
faz com que um único modelo não seja capaz de representar a dinâmica
comportamental da COVID-19 no Brasil, por isso o recomendado é utilizar
um modelo de misturas para modelar esses dados, e considerar as regiões,
ou estados, como clusteres, atribuíndo à eles sua própria curva
epidemiológica.

Neste post eu quis apenas apresentar uma forma de modelar esses dados e
fazer previsões. Em breve farei mais um post com um hands-on nos dodos.
Vejo você lá !
