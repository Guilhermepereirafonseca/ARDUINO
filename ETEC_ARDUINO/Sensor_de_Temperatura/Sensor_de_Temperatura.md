```c++
int pinLM35 = A0;
float temp = 0;
int led = 2;

void setup(){
  Serial.begin(9600);
  pinMode(led, OUTPUT);
}

void loop(){
  temp = (float(analogRead(pinLM35))*5/(1023)/0.01)-50; // Convertendo para temperatura(Cº)
  
  Serial.print("O valor da Temperatura eh: ");
  Serial.println(temp); // exibindo o valor
  	delay(200); // dando um tempo para visualizar
  
  // acendendo o led quando for maior ou igual a 30:
  if(temp >= 30){
   digitalWrite(led, HIGH);
  } else {
   digitalWrite(led, LOW);
  }
}
```
