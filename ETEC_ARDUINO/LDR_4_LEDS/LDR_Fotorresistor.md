```c++
// map(valor,0,1023,0,255) [minimo para maximo]

int ldr = A0; // Analógico
int valorLDR = 0; // valor inicial
int led = 6; // ~6
int pouca = 3; // ~3
int media = 4; // ~4
int muita = 5; // ~5

void setup(){
 Serial.begin(9600); //velocidade de transmissão (maior mais rápido)
 // Definindo pinos como saída
 pinMode(led, OUTPUT);
 pinMode(pouca, OUTPUT);
 pinMode(media, OUTPUT);
 pinMode(muita, OUTPUT);
}

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
