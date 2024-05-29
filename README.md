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

### Ligando um LED com um BOTÃO:
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

### Fazendo um SEMÁFORO DUPLO:
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
