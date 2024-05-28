
# Medidor de nível de maré

Sistema de medidor de nível de maré. Através de um sensor de distância ultrassônico, o projeto busca fazer a coleta de dados sobre o nível da maré em uma região específica

## Link do projeto no tinkercad

https://www.tinkercad.com/things/kjca7DPbL3g-medidor-de-nivel-de-mare-

## Como reproduzir

Após clicar em "Iniciar Simulação", clique no sensor ultrassônico. O Tinkercad disponibiliza uma bolinha que simula a distância de um objeto, sinta-se livre para mover o "objeto" para que o display LCD seja atualizado com os valores em centímetros.

## Autores
- [Camila Feitosa](https://github.com/camfeitosa)
- [Gustavo Berlanga](https://www.github.com/berla1)
- [Vinicius Gardim](https://www.github.com/gardim1)

## Dependências

Componentes usados no circuito: 

- Arduino Uno R3
- Placa de Ensaio
- Display LCD 16x2
- Sensor de distância ultrassônico
- Jumper Cables

- [![imagem-2024-05-28-000806210.png](https://i.postimg.cc/brjwpBrz/imagem-2024-05-28-000806210.png)](https://postimg.cc/LYNpVvj7)

## Lógica

O sensor fica posicionado em um ponto fixo em uma posição de cima, apontado para baixo, para medir a distância da maré em relação ao sensor. Ao ser feita a medição é possível a classificação se a maré está alta, mediana ou baixa.

A partir da captura desses dados, é possível realizar estudos que analisam durante certo período de tempo as marés e chegar a conclusões concretas sobre a variação da maré.


| Distância | Status exibido |
|:----:| ----------------- | 
|Menor que 150cm| Maré Baixa |
|Menor que 100cm e maior que 250cm| Maré mediana | 
|Acima de 250cm| Maré Alta | 
