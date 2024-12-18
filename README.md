# Simulação do sistema solar

## Descrição
Esse projeto busca simular o funcionamento de um sistema solar inspirado no nosso e suas órbitas através do cálculo da interação gravitacional entre cada corpo.
Para isso, foi criado um programa em Python, que realiza uma representação visual da trajetória dos planetas em torno do Sol, utilizando valores constantes proporcionais à massa real de cada corpo.
As trajetórias foram simplificadas de forma a descrever movimentos circulares,em um único plano de movimento, em função da simplificação dos cálculos referentes.

![Screenshot da simulação](Image/SistemaSolar.png)

## Requisitos
Para executar esse projeto, será necessário possuir o [Python](https://www.python.org/) e o [pip](https://pip.pypa.io/en/stable/)
## Instalação
- Clone o repositório
```
git clone https://github.com/gustavorspires/sistema-solar-simulacao.git
cd sistema-solar-simulacao
```
- Crie e ative a venv
```
python3 -m venv .venv
source .venv/bin/activate
```
- Instale as dependências e execute o programa
```
pip install -r requirements.txt
python3 sistemaSolar.py
```
## Cálculos da Física
### Força gravitacional
Foi utilizada a Lei Universal da Gravitação de Newton para calcular a força em cada astro:

$$ \vec{F_g} = \frac{Gm_1m_2(\vec{r_2} - \vec{r_1})}{||\vec{r_2} - \vec{r_1}||^3} $$

$G$: constante gravitacional,  $m_1,r_1$ : massa e posição do astro de origem do vetor de força,  $m_2,r_2$ : massa e posição do astro interagindo com o de origem

Foram somadas os vetores de forças ativos em um astro, para calcular a força resultante nele.

### Aceleração
Utilizando a Segunda Lei de Newton é possível calcular a aceleração de um astro:

$$\vec{F_r} = m\vec{a} \therefore  \vec{a} = \frac{\vec{F_r}}{m} $$

### Velocidade Orbital 
A velocidade inicial é calculada a partir a equação da força centrípeta, considerando o movimento como uma órbita circular centrada no Sol, o sentido é perpendicular com o vetor das posições entre o astro e o Sol, no sentido horário:

$$ \frac{mv^2}{r} = \frac{GMm}{r^2} \therefore v = \sqrt{\frac{GM}{r}} $$

### Posição
Foi utilizado o Método de Integração de Verlet para o cálculo da posição:

$$\vec{r}(t+\Delta t) = \vec{r}(t) + \vec{v}(t)\Delta t + \frac{\vec{a}(t)\Delta t^2}{2}$$
$$\vec{r}(t-\Delta t) = \vec{r}(t) - \vec{v}(t)\Delta t + \frac{\vec{a}(t)\Delta t^2}{2}$$
$$\therefore$$
$$\vec{r}(t+\Delta t) = 2\vec{r}(t) -\vec{r}(t - \Delta t) + \vec{a}(t)\Delta t^2 $$

### Rapidez 
A rapidez é calculada como o módulo da variação do vetor posição no menor intervalo de tempo sendo utilizado na simulação:

$$v = \frac{||\vec{r}(t) - \vec{r}(t +\Delta t)||}{\Delta t} $$

## Integrantes
```
Gustavo Ramos Santos Pires - 15458030 - gustavo.rspires@usp.br
Daniel Jorge Manzano - 15446861 - danieljm@usp.br
Artur Kenzo Obara Kawazoe - 15652663 - arturkawazoe@usp.br
Larissa Pires Moreira Rocha Duarte - 15522358 - larissa.piresd@usp.br
Fernando Valentim Torres - 15452340 - fernandovt@usp.br
```

## Referências

(1) Bernardes, E. de S. (2024). Gravitação. 7600105 - Física Básica I. Universidade de São Paulo, São Carlos.<br>
(2) Verlet, Loup (1967). "Computer "Experiments" on Classical Fluids. I. Thermodynamical Properties of Lennard−Jones Molecules"<br>
(3) Williams, D. R. "Planetary Fact Sheet - Metric". National Aeronautics and Space Administration (NASA). Disponível em (https://nssdc.gsfc.nasa.gov/planetary/factsheet/).
