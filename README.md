#include <GyverBME280.h>                      // Подключение библиотеки
#include <Servo.h>                            // Подключение бИблиотеки с моторчиком
GyverBME280 bme;
Servo servo1;
// Создание обьекта bme

void setup() {
  servo1.attach(5);
  Serial.begin(9600);                         // Запуск последовательного порта
  bme.begin();                                // Если доп. настройки не нужны  - инициализируем датчик
}

void loop() {
  float pressure = bme.readPressure();        // Читаем давление в [Па]
  Serial.print("Pressure: ");
  Serial.print(pressureToAltitude(pressure)); // Выводим высоту в [м над ур. моря]
  Serial.println(" cm");
  Serial.println("");
  delay(11);
}
