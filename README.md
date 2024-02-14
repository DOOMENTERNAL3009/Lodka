# Lodka
Proekt lodka 
#define sensor A5
int dark = 1024;
void setup() {
  pinMode(sensor, INPUT);
  pinMode(11, OUTPUT);
  analogWrite(sensor, LOW);  
  Serial.begin(9600);   // подключаем монитор порта
}

void loop() {
  // считываем данные с датчика и выводим на монитор порта
  int light = analogRead(sensor);
  float dangeros = dark -light;

  if(dangeros <=1024 && dangeros >=930){
    digitalWrite(11,LOW);
    }
    else{
      digitalWrite(11,HIGH);
      }
  Serial.print("Dangeros = ");
  Serial.println(dangeros);

  Serial.print("Light = ");
  Serial.println(light);

  // рассчитываем напряжение и выводим на монитор порта
  float u = light * 0.48 / 100;
  Serial.print("U = ");
  Serial.println(u);

  // ставим паузу и делаем перенос строки
  delay(500);
  Serial.println("");
}
