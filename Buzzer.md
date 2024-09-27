A continuación, te proporciono el código que implementa esta lógica. El **sensor de inclinación** encenderá un **LED** y, al mismo tiempo, activará un **buzzer**.

### Código Arduino:
```cpp
// Declaración de pines
int ledPin = 13;        // Pin del LED
int buzzerPin = 9;      // Pin del Buzzer
int inPinSensor = 7;    // Pin del sensor de inclinación
int valueSensor = 0;    // Valor del sensor de inclinación

void setup() {
  // Configuración de los pines
  pinMode(ledPin, OUTPUT);        // Inicializa el pin 13 como salida para el LED
  pinMode(buzzerPin, OUTPUT);     // Inicializa el pin 9 como salida para el Buzzer
  pinMode(inPinSensor, INPUT);    // Inicializa el pin 7 como entrada para el sensor de inclinación
}

void loop() {
  // Leer el valor del sensor de inclinación
  valueSensor = digitalRead(inPinSensor);
  
  // Si el sensor se inclina (se activa)
  if (valueSensor == HIGH) {
    digitalWrite(ledPin, HIGH);  // Enciende el LED
    digitalWrite(buzzerPin, HIGH); // Activa el buzzer
  } else {
    digitalWrite(ledPin, LOW);   // Apaga el LED
    digitalWrite(buzzerPin, LOW);  // Apaga el buzzer
  }
}
```

### Explicación:
1. **Sensor de inclinación**: Detecta si está inclinado o no (cuando `valueSensor == HIGH`).
2. **LED**: Se enciende cuando el sensor detecta inclinación.
3. **Buzzer**: Se activa al mismo tiempo que el LED.
4. **Desactivación**: Cuando el sensor deja de estar inclinado (`valueSensor == LOW`), tanto el LED como el buzzer se apagan.

### Pines utilizados:
- **Pin 13** para el **LED**.
- **Pin 9** para el **buzzer**.
- **Pin 7** para el **sensor de inclinación**.

### Funcionamiento:
- Cuando el sensor de inclinación detecta un cambio (inclinación), el LED y el buzzer se encienden.
- Si el sensor vuelve a su posición normal (no inclinado), ambos se apagan.

Prueba este código con los componentes conectados a los pines correctos y verifica si funciona como esperas.
