# Arduino LED and Infrared Sensor Project

## Componentes Utilizados
- Arduino Uno
- Sensor de infravermelho PIR
- LEDs (vermelho, amarelo)
- Buzzer
- Protoboard e cabos jumper

## Conexões
1. Conecte o pino VCC do sensor PIR ao pino 5V.
2. Conecte o pino GND do sensor ao GND.
3. O pino de saída do sensor PIR deve ir ao pino digital D7.
4. Conecte os LEDs aos pinos digitais D8 e D9, com resistores em série.
5. Conecte o buzzer ao pino digital D3.


## Como Funciona
- O sensor PIR detecta calor.
- Quando o sensor detecta calor, um som é emitido pelo buzzer e os LEDs piscam alternadamente.

## Código
```
int pino_D0 = 7;  // Pino de entrada para detecção
int buzzerPin = 3;  // Pino do buzzer
int ledPin_1 = 8;   // LED 1
int ledPin_2 = 9;   // LED 2

void setup() {
  Serial.begin(9600);

  pinMode(pino_D0, INPUT);       // Configurar pino de entrada
  pinMode(buzzerPin, OUTPUT);    // Configurar pino do buzzer
  pinMode(ledPin_1, OUTPUT);     // Configurar pino do LED 1
  pinMode(ledPin_2, OUTPUT);     // Configurar pino do LED 2
}

void loop() {
  int valor_d = digitalRead(pino_D0);
  Serial.print("Porta digital: ");
  Serial.println(valor_d);

  if (valor_d != 1) {
    Serial.println("Fogo detectado !!!");
  }

  // Controle do buzzer
  if (valor_d != 1) {
    digitalWrite(buzzerPin, HIGH);
  } else {
    digitalWrite(buzzerPin, LOW);
  }

  // Controle do LED 1
  if (valor_d != 1) {
    digitalWrite(ledPin_1, HIGH);
    delay(50);
    digitalWrite(ledPin_1, LOW);
    delay(50);
  } else {
    digitalWrite(ledPin_1, LOW);
  }

  // Controle do LED 2
  if (valor_d != 1) {
    digitalWrite(ledPin_2, LOW);
    delay(500);
    digitalWrite(ledPin_2, HIGH);
    delay(50);
  } else {
    digitalWrite(ledPin_2, LOW);
  }

  delay(500);  // Atraso geral
}
```
## Esquema do projeto

![t725](https://github.com/user-attachments/assets/180dbde5-b400-47b6-92de-01f983b98b7d)

## Projeto no simulador Tinkercad

https://www.tinkercad.com/things/0WnnJ8fC8kX-sensor-infra-vermelho
