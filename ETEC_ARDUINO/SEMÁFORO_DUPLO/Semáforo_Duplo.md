```c++
// semaforo 1

int ledVermelho1 = 2;
int ledAmarelo1 = 3;
int ledVerde1 = 4;

// semaforo 2

int ledVermelho2 = 7;
int ledAmarelo2 = 6;
int ledVerde2 = 5;

void setup() {
	
 pinMode (ledVermelho1, OUTPUT);
 pinMode (ledAmarelo1, OUTPUT);
 pinMode (ledVerde1, OUTPUT);
 pinMode (ledVermelho2, OUTPUT); 
 pinMode (ledAmarelo2, OUTPUT);
 pinMode (ledVerde2, OUTPUT);

}

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
