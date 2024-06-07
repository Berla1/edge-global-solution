
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

 [![imagem-2024-05-28-000806210.png](https://i.postimg.cc/brjwpBrz/imagem-2024-05-28-000806210.png)](https://postimg.cc/LYNpVvj7)

## Lógica

O sensor fica posicionado em um ponto fixo em uma posição de cima, apontado para baixo, para medir a distância da maré em relação ao sensor. Ao ser feita a medição é possível a classificação se a maré está alta, mediana ou baixa.

A partir da captura desses dados, é possível realizar estudos que analisam durante certo período de tempo, as marés e chegar a conclusões concretas sobre a variação da maré.


| Distância | Status exibido |
|:----:| ----------------- | 
|Menor que 150cm| Maré Baixa |
|Menor que 100cm e maior que 250cm| Maré mediana | 
|Acima de 250cm| Maré Alta | 

**IMPORTANTE: As medidas apresentadas não são estimativas aproximadas**

**Código Fonte:**
```
#include <LiquidCrystal.h>
#define TRIGGER_PIN 5 // definindo trigger pin do sensor
#define ECHO_PIN 4 // definindo echo pin do sensor

LiquidCrystal lcd(12, 11, 10, 9, 8, 7, 6); // definindo portas do lcd

float velocidade = 0.0172316; // definindo variáveis
float duracao;
float distancia;

void setup(){
  pinMode(TRIGGER_PIN, OUTPUT); //define trigger pin como output
  pinMode(ECHO_PIN, INPUT); // definine echo pin como input
  lcd.begin(16,2); // inicia o display lcd
  lcd.clear(); // limpa o lcd
}

void loop(){
  digitalWrite(TRIGGER_PIN, 1); // liga o trigger pin
  digitalWrite(TRIGGER_PIN, 0); // desliga o trigger pin
  duracao = pulseIn(ECHO_PIN, 1); // recebe o sinal que veio do trigger pin
  distancia = duracao * velocidade; // calcula baseado na duracao do echo pin e na velocidade do som

  lcd.display();

  
  if(distancia < 150){ // se a distancia for maior que 150cm
 
    lcd.setCursor(0,0);
    lcd.print("Mare alta!   ");
    lcd.setCursor(0,1);
    lcd.print("Distancia CM:");
    lcd.print(distancia);   
  } 
  else if(distancia > 150 && distancia < 250){ // se a distancia estiver entre 150cm e 250cm
    lcd.setCursor(0,0); 
    lcd.print("Mare mediana!");
    lcd.setCursor(0,1);
    lcd.print("Distancia CM:");
    lcd.print(distancia);
  }
  else{ // se a distancia for maior que 250cm
  lcd.setCursor(0,0);
    lcd.print("Mare baixa!    ");
    lcd.setCursor(0,1);
    lcd.print("Distancia CM:");
    lcd.print(distancia);
  }
}
```
