```c++
// LED RGB
// suas cores funcionam entre 0 e 255, igual o PWM!;

int vermelho = 3;
int azul = 5;
int verde = 6;
int pinBotao = 2;
int estadoBotao = 0; // se foi pressionado ou não
int cor = 0;

void setup(){
 pinMode(vermelho, OUTPUT); // 3 ~
 pinMode(azul, OUTPUT); // 5 ~
 pinMode(verde, OUTPUT); // 6 ~
 pinMode(pinBotao, INPUT);
}

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
