int boia = 7;
int sensorNivel = A0;
int rele1 = 11;
int rele2 = 10;


String comando;
void setup() {
Serial.begin(9600);
pinMode(boia,INPUT_PULLUP);
pinMode(sensorNivel,INPUT);
pinMode(rele1,OUTPUT);
pinMode(rele2, OUTPUT);
}

void loop() {
// Leitura dos sensores
int valorBoia = digitalRead(boia);
int valorSensor = analogRead(sensorNivel);

Serial.println(" ");
Serial.print("Valor BOIA: ");
Serial.println(valorBoia);
Serial.print("Nível da água: ");
Serial.println(valorSensor);
Serial.print("Rele 1: ");
Serial.println(rele1);
Serial.print("Rele 2: ");
Serial.println(rele2);

 

// Se a boia acionar, rele1 = HIGH
if(valorBoia == HIGH){ 
  digitalWrite(rele1,LOW);
  
} 
else{
  digitalWrite(rele1,HIGH);
}

if(valorSensor > 310){ 
  digitalWrite(rele2,LOW);
  
} 
else{
  digitalWrite(rele2,HIGH);
  
}


delay(100);
}
