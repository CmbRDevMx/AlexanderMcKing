# AlexanderMcKing
Códigos y ejemplos basados en LED 

Aquí está el código que combina la lógica de los tres elementos:

1. **Sensor de inclinación**.
2. **LED** que se activa en función del sensor.
3. **Pulsador** que controlará la secuencia de activación.

Este código realiza una secuencia donde el sensor de inclinación activa el LED, y luego, con el pulsador, se puede cambiar la secuencia de activación del LED.

### Código Arduino:
```cpp
// Declaración de pines
int ledPin = 13;       // Pin del LED
int inPinSensor = 7;    // Pin del sensor de inclinación
int inPinPulsador = 8;  // Pin del pulsador
int valueSensor = 0;    // Valor del sensor de inclinación
int valuePulsador = 0;  // Valor del pulsador
int ledState = LOW;     // Estado del LED
bool activadoPorSensor = false;  // Control para secuencia del sensor y pulsador

void setup() {
  // Configuración de los pines
  pinMode(ledPin, OUTPUT);        // Inicializa el pin 13 como salida digital para el LED
  pinMode(inPinSensor, INPUT);    // Inicializa el pin 7 como entrada para el sensor
  pinMode(inPinPulsador, INPUT);  // Inicializa el pin 8 como entrada para el pulsador
}

void loop() {
  // Leer el valor del sensor de inclinación
  valueSensor = digitalRead(inPinSensor);
  
  // Si el sensor se inclina (detectar activación)
  if (valueSensor == HIGH) {
    digitalWrite(ledPin, HIGH);  // Encender LED
    activadoPorSensor = true;    // Marca que el sensor activó la secuencia
  }

  // Leer el valor del pulsador
  valuePulsador = digitalRead(inPinPulsador);

  // Si el pulsador es presionado y el sensor ha activado previamente el LED
  if (valuePulsador == HIGH && activadoPorSensor) {
    // Cambiar el estado del LED cada vez que el pulsador es presionado
    ledState = !ledState;        // Alterna el estado del LED
    digitalWrite(ledPin, ledState); // Enciende o apaga el LED dependiendo del estado
    delay(300);  // Pequeño retardo para evitar rebotes del pulsador
  }
}
```

### Explicación:

- **Sensor de inclinación**: Cuando el sensor detecta inclinación (cuando `valueSensor == HIGH`), el LED se enciende.
- **Pulsador**: Si el LED ha sido encendido por el sensor, el pulsador permite alternar el estado del LED (encendido/apagado).
- **Secuencia**: El sensor activa el LED, y luego el pulsador controla si se mantiene encendido o apagado, creando una interacción entre ambos componentes.

Prueba este código y ajusta los pines según tu montaje. ¡Déjame saber si necesitas más ajustes!
