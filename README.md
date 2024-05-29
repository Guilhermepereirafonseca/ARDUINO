# ARDUINO
<img src="https://static-00.iconduck.com/assets.00/arduino-icon-2048x1397-pmu0lemh.png" width="190px">

## CONCEITOS DA LINGUAGEM DO ARDUINO (**C/C++**)
### 📘 VOID SETUP
<h3> Aqui voce define os pinos e entrada e saída de dados, todos os comandos serão executados uma unica vez. Vale lembrar que antes do mesmo você define as variaveis
VEJA O EXEMPLO ABAIXO:

![Arduino](https://github.com/Guilhermepereirafonseca/ARDUINO/assets/169271268/7a41614d-5727-4678-85e3-341af7bb5379)  
</h3>

### 📘 VOID LOOP
<h3>Aqui tudo ficará em loop, fazendo assim todas as açoes/automações que você fará no Arduino funcione (TOME CUIDADO NESSA PARTE)

![Arduino2](https://github.com/Guilhermepereirafonseca/ARDUINO/assets/169271268/a3b0951f-a167-480b-927c-25d4f6006c44)

</h3>

## SOBRE OS PROJETOS

### 🤖 Ligando um LED com um BOTÃO [{repository}](https://github.com/Guilhermepereirafonseca/ARDUINO/tree/main/ETEC_ARDUINO/BOTAO_LED):
- Definindo as variáveis
```c++

int pinBotao = 2;
int estadoBotao = 0;
int interruptor = 0;

```
- Definindo os pinos no **void setup**
```c++

void setup(){
 pinMode(pinBotao, INPUT);
 pinMode(3, OUTPUT);
}

```
- Defindo o estado do botão e dando as condições
void loop(){
```c++

estadoBotao = digitalRead(pinBotao);
  
  if(estadoBotao == HIGH) {
    interruptor = !interruptor;
     delay(200);
  }
  if(interruptor == 1) {
    digitalWrite (3, HIGH); 
	}else{
    digitalWrite(3, LOW);
    }
}

```

### 🤖 Fazendo um SEMÁFORO DUPLO [{repository}](https://github.com/Guilhermepereirafonseca/ARDUINO/tree/main/ETEC_ARDUINO/SEM%C3%81FORO_DUPLO):
- Definindo as variavéis para **semáforo 1** e **semáforo 2**
```c++

// semaforo 1

int ledVermelho1 = 2;
int ledAmarelo1 = 3;
int ledVerde1 = 4;

// semaforo 2

int ledVermelho2 = 7;
int ledAmarelo2 = 6;
int ledVerde2 = 5;

```
- Definindo no void setup os pinos de cada semáforo
```c++
void setup() {
	
 pinMode (ledVermelho1, OUTPUT);
 pinMode (ledAmarelo1, OUTPUT);
 pinMode (ledVerde1, OUTPUT);
 pinMode (ledVermelho2, OUTPUT); 
 pinMode (ledAmarelo2, OUTPUT);
 pinMode (ledVerde2, OUTPUT);

}
```
- Definindo cada semáforo como ligado ou desligado, **conforme o fluxo da vida real**
```c++

void loop() {
	
 digitalWrite (ledVerde1, HIGH);
 digitalWrite (ledVermelho2, HIGH);
  delay(1000);
 digitalWrite (ledVerde1, LOW);
 digitalWrite (ledAmarelo1, HIGH);
  delay(1000);
 digitalWrite (ledAmarelo1, LOW);
 digitalWrite (ledVermelho1, HIGH);
 digitalWrite (ledVerde2, HIGH);
 digitalWrite (ledVermelho1, LOW);
  delay(1000);
 digitalWrite (ledVerde2, LOW);
 digitalWrite (ledAmarelo2, HIGH);
  delay(1000);
 digitalWrite (ledAmarelo2, LOW);
 digitalWrite (ledVermelho1, LOW);	
}
```

### 🤖 Usando PWM com LED RGB [{repository}](https://github.com/Guilhermepereirafonseca/ARDUINO/tree/main/ETEC_ARDUINO/PWM_RGB_BUTTON):
- Definindo as variáveis
```c++

// LED RGB
// suas cores funcionam entre 0 e 255, igual o PWM!;

int vermelho = 3;
int azul = 5;
int verde = 6;
int pinBotao = 2;
int estadoBotao = 0; // se foi pressionado ou não
int cor = 0;
```
- Defindo cada pino como OUTPUT, menos o BOTÃO (INPUT)
```c++

void setup(){
 pinMode(vermelho, OUTPUT); // 3 ~
 pinMode(azul, OUTPUT); // 5 ~
 pinMode(verde, OUTPUT); // 6 ~
 pinMode(pinBotao, INPUT);
}
```
- Definindo cada toque do BOTÃO com **IF**
```c++

void loop(){
  // BOTÃO
 estadoBotao = digitalRead(pinBotao); 
   if(estadoBotao == HIGH){
    cor++;
  } if(cor == 4){
    cor = 0;
  }
  delay(200);
  if(cor == 0){
    digitalWrite(vermelho, 255);
    digitalWrite(verde, 0);
    digitalWrite(azul, 0);
  } if(cor == 1){
    digitalWrite(vermelho, 0);
    digitalWrite(verde, 255);
    digitalWrite(azul, 0);
  } if(cor == 2){
    digitalWrite(vermelho, 0);
    digitalWrite(verde, 0);
    digitalWrite(azul, 255);
  } if(cor == 3){
    digitalWrite(vermelho, 0);
    digitalWrite(verde, 0);
    digitalWrite(azul, 0);
  }
}
```
### 🤖 FOTORERSISTOR (LDR) [{repository}](https://github.com/Guilhermepereirafonseca/ARDUINO/tree/main/ETEC_ARDUINO/LDR_4_LEDS)
- Definindo as variáveis analógicas
```c++

int ldr = A0; // Analógico
int valorLDR = 0; // valor inicial
int led = 6; // ~6
int pouca = 3; // ~3
int media = 4; // ~4
int muita = 5; // ~5
```
- Ativando o MONITOR SERIAl com Serial.begin, e definindo os PINOS como saída (OUTPUT)
```c++

void setup(){
 Serial.begin(9600); //velocidade de transmissão (maior mais rápido)
 // Definindo pinos como saída
 pinMode(led, OUTPUT);
 pinMode(pouca, OUTPUT);
 pinMode(media, OUTPUT);
 pinMode(muita, OUTPUT);
}
```
- Lendo o valorLDR, mostrando no MONITOR SERIAL e fazendo condições com **IF**
```c++

void loop(){
  valorLDR = analogRead(ldr); // lendo
  Serial.print("O valor do LDR eh: "); // Será exibido
  Serial.println(valorLDR); // mostrando o valor
  
  int valorNovo = map(valorLDR,0,1023,255,0);
   analogWrite(led, valorNovo); // Lendo
  
  // Aqui o valor está em pouca luminosidade
  if(valorLDR <= 840){
   digitalWrite(pouca, HIGH);
   digitalWrite(media, LOW);
   digitalWrite(muita, LOW);
  }
  // Aqui o valor está em pouca e media luminosidade
  if(valorLDR <= 950 and valorLDR >= 900){
   digitalWrite(pouca, HIGH);
   digitalWrite(media, HIGH);
   digitalWrite(muita, LOW);
  }
  // Aqui acende os anteriores, está em muita luminosidade
  if(valorLDR >= 960){
   digitalWrite(pouca, HIGH);
   digitalWrite(media, HIGH);
   digitalWrite(muita, HIGH);
  }
}
```

### 🤖 SENSOR DE TEMPERATURA (LM35 | TM36) [{repository}](https://github.com/Guilhermepereirafonseca/ARDUINO/tree/main/ETEC_ARDUINO/Sensor_de_Temperatura)
- Definindo as variáveis, uma como float que será convertida
```c++

int pinLM35 = A0;
float temp = 0;
int led = 2;
```
- Ativando o MONITOR SERIAL, definindo o pino do LED
```c++

void setup(){
  Serial.begin(9600);
  pinMode(led, OUTPUT);
}
```
- Criando uma variável e fazendo ela ler e converter para graus Celsius (C°)
```c++
temp = (float(analogRead(pinLM35))*5/(1023)/0.01)-50; // Convertendo para temperatura(C°)
```
- Mostrando na tela o valor da Temperatura e dando uma condição simples para acender o LED quando for maior que **30°**, caso seja menor desligue o mesmo.
```c++

Serial.print("O valor da Temperatura eh: ");
  Serial.println(temp); // exibindo o valor
  	delay(200); // dando um tempo para visualizar
  
  // acendendo o led quando for maior ou igual a 30:
  if(temp >= 30){
   digitalWrite(led, HIGH);
  } else {
   digitalWrite(led, LOW);
  }
```
