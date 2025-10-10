# Sensor Infravermelho com Arduino 🔥

Um sistema simples e eficiente de detecção de movimento com sensor PIR, LEDs indicadores e um buzzer de alerta. Esse projeto utiliza o Arduino Uno para interpretar o sinal do sensor de infravermelho e acionar alarmes visuais e sonoros, simulando um sistema básico de segurança ou detecção de presença.

O circuito detecta calor (como o de uma pessoa passando em frente ao sensor) e, quando isso acontece, o buzzer é acionado e os LEDs piscam alternadamente, criando um efeito de alerta. É um ótimo exemplo de como sensores e atuadores podem ser combinados para formar sistemas inteligentes e responsivos.

## Materiais⚙️

<img width="50%" alt="Imagem do WhatsApp de 2025-10-03 à(s) 09 33 01_cddcb55d" src="https://github.com/user-attachments/assets/3f77a627-d851-4330-9950-50b881c2ad48" />

* Arduino Uno
* Sensor de infravermelho PIR
* LEDs (vermelho, amarelo)
* Buzzer
* Resistor de 220Ω (x2)

**OBS:** Também é necessário fios de cobre e protobord.

## Conexões⚡️

| **Componente**   | **Pino no Arduino** | **Descrição**                          |
| ---------------- | ------------------- | -------------------------------------- |
| Sensor PIR (VCC) | 5V                  | Alimentação do sensor                  |
| Sensor PIR (GND) | GND                 | Terra do circuito                      |
| Sensor PIR (OUT) | D7                  | Saída digital do sensor                |
| LED Vermelho     | D8                  | LED indicador 1 (via resistor de 220Ω) |
| LED Amarelo      | D9                  | LED indicador 2 (via resistor de 220Ω) |
| Buzzer           | D3                  | Emite o som de alerta                  |




## Funcionamento🤖

Quando o sensor PIR detecta movimento ou calor, ele envia um sinal HIGH (1) para o Arduino. O programa então aciona o buzzer e faz com que os LEDs pisquem rapidamente, simulando uma situação de alarme.
Se não houver detecção, o sistema permanece em repouso, com LEDs e buzzer desligados.
É uma base que pode ser expandida para projetos maiores, como sistemas de segurança, alarmes automáticos ou dispositivos IoT.

## Montagem🔌

![t725](https://github.com/user-attachments/assets/180dbde5-b400-47b6-92de-01f983b98b7d)

A montagem é bem direta. Conecte o sensor PIR à protoboard e ligue seu pino VCC ao 5V, GND ao terra (GND) e o pino de saída (OUT) ao pino digital 7 do Arduino.
Em seguida, posicione os dois LEDs: conecte o LED vermelho ao pino 8 e o LED amarelo ao pino 9, cada um com seu resistor de 220Ω em série antes de ir para o GND.
Por fim, conecte o buzzer ao pino 3, com o outro terminal indo ao GND.
Após isso, basta enviar o código e observar o sistema funcionando — quando o sensor detectar calor, os LEDs piscarão e o buzzer emitirá um som de alerta.

## Código💻
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

## Projeto no TinkerCAD❗

https://www.tinkercad.com/things/0WnnJ8fC8kX-sensor-infra-vermelho
