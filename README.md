# Bebedouro para pets automatizado

## Sistemas Embarcados - 1º Semestre - 2022
---

### Integrantes do grupo: 

- Abner Santos
- Elionay Santos
- Erick Gabriel
- Larissa Michelin
- Luiz Henrique
---

## Sumário

1.	Descrição do projeto
2.	Lista de materiais
3.	Montagem
4.	Código-fonte
5.	Conclusão
---

## 1. Descrição do projeto

  A ideia do projeto se originou devido a dificuldade de suprir uma das necessidades básicas dos nossos pets quando estivermos ausentes, com um dispositivo de abastecimento de água automático conseguimos resolver essa questão que se da devido ao consumo imprevisível durante o dia. Sendo um dispositivo compacto e de simples manuseio, pode ser alocada em diversos lugares da residência e habitats externos, tornando-o útil para diversas espécies de animais domésticos ou de pequeno porte.  Por meio dessa tecnologia, visamos trazer praticidade e bem-estar tanto na vida dos animais quanto aos seus donos.

---

 ## 2. Lista dos materiais
 
  - Placa arduino Leonardo ATMega32U4;
  - Módulo rele 1 canal;
  - Sensor de nível de água analógico;
  - Pastilha termoelétrica *Peltier*;
  - 2 Solenoides 12V;
  - Fonte 12V;
  - Galão de água -10 litros;
  - Suporte para o galão;
  - Comedouro -plástico.
  - Mangueira de silicone;
  - Jumpers;
  - Caixa organizadora de PVC;
---

## 3. Montagem
#### Montagem no simulador Tinkercad:
 ![](/Imagens/montagem.png)                     
 
 
#### Organização dos componentes dentro da caixa de PVC:
![](/Imagens/caixa.jpeg)                       

#### Estrutura:
![](./Imagens/estrutura.jpeg)                         

---

## 4. Código fonte

```
int boia = 7;
int sensorNivel = A0;
int rele1 = 11;
int rele2 = 10;


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

// Monitoramento serial
Serial.println(" ");
Serial.print("Valor BOIA: ");
Serial.println(valorBoia);
Serial.print("Nível da água: ");
Serial.println(valorSensor);
Serial.print("Rele 1: ");
Serial.println(rele1);
Serial.print("Rele 2: ");
Serial.println(rele2);

// Controle do reabastecimento do reservatório
if(valorBoia == HIGH){ 
  digitalWrite(rele1,LOW);
  
} 
else{
  digitalWrite(rele1,HIGH);
}

// Controle do reabastecimento do bebedouro
if(valorSensor > 310){ 
  digitalWrite(rele2,LOW);
  
} 
else{
  digitalWrite(rele2,HIGH);
  
}


delay(100);
}

```
---

## 5. Conclusão

 O arduino controla o funcionamento do rele como esperado, assim a válvula libera e bloqueia a passagem da água com o auxílio dos sensores para que essa ação seja realizada no momento certo, abastecendo o recipiente do cachorro. Como o dispositivo é automatizado, deixamos seu depósito de água ligado diretamente á uma torneira para que não se faça necessária a ação de abastecimento.

 O projeto atendeu a nossa expectativas, sendo um dispositivo de fato funcional e prático, podendo ser replicado por pessoas com rotinas agitadas e alocado em diversos locais da residência.
