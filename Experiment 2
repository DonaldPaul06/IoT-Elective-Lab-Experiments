# Experiment 2: Controlling an LED using a Push Button on Wokwi

## Aim
To interface a push button with a microcontroller (ESP32/Arduino) and control the ON/OFF state of an LED based on button presses, using the Wokwi online simulation platform.

## Components Required

| S.No | Component            | Quantity | Specification              |
|------|-----------------------|----------|------------------------------|
| 1    | Microcontroller Board  | 1        | ESP32 / Arduino Uno         |
| 2    | LED                    | 1        | Any color, 5mm               |
| 3    | Resistor (LED)         | 1        | 220 Ω (current limiting)     |
| 4    | Push Button            | 1        | Momentary push button        |
| 5    | Resistor (Button)      | 1        | 10 kΩ (pull-down, if not using internal pull-up) |
| 6    | Connecting Wires       | As needed| Jumper wires                  |
| 7    | Breadboard             | 1        | Half/Full size                |
| 8    | Wokwi Simulator        | -        | Online platform (wokwi.com)  |

## Theory
A push button is a simple input device that closes or opens a circuit when pressed. When connected to a GPIO pin configured as an input, the microcontroller can read its state (HIGH or LOW) and use that to control an output device like an LED.

Two common wiring approaches:
- **Pull-down configuration**: Button connects GPIO to VCC when pressed; a 10 kΩ resistor pulls the pin LOW when not pressed.
- **Internal pull-up configuration**: `INPUT_PULLUP` mode is used in software, GPIO reads HIGH normally and goes LOW when the button connects it to GND — no external resistor needed for the button.

In this experiment, pressing the button toggles or controls the LED state.

## Circuit Diagram
- **LED**: Anode → GPIO pin (e.g., GPIO 2) through 220 Ω resistor; Cathode → GND.
- **Push Button (using internal pull-up)**: One terminal → GPIO pin (e.g., GPIO 4); Other terminal → GND.

## Procedure
1. Open [Wokwi](https://wokwi.com) and create a new **ESP32 / Arduino Uno** project.
2. Add an LED with a 220 Ω resistor, and a push button, from the components panel.
3. Connect the LED's anode to a digital GPIO pin (e.g., GPIO 2) through the resistor, and cathode to GND.
4. Connect one terminal of the push button to a digital GPIO pin (e.g., GPIO 4) and the other terminal to GND.
5. Write the Arduino code to configure the button pin as `INPUT_PULLUP` and the LED pin as `OUTPUT`.
6. In the loop, read the button state — if pressed (LOW), turn the LED ON; if not pressed (HIGH), turn the LED OFF.
7. Upload/run the code in the Wokwi simulator.
8. Click the push button in the simulation and observe the LED turning ON while pressed and OFF when released.

## Code
```cpp
#define LED_PIN 2
#define BUTTON_PIN 4

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {      // Button pressed
    digitalWrite(LED_PIN, HIGH); // LED ON
  } else {                       // Button not pressed
    digitalWrite(LED_PIN, LOW);  // LED OFF
  }
}
```

### Optional: Toggle Version (button press toggles LED state)
```cpp
#define LED_PIN 2
#define BUTTON_PIN 4

bool ledState = false;
bool lastButtonState = HIGH;

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
}

void loop() {
  bool currentButtonState = digitalRead(BUTTON_PIN);

  // Detect a press (HIGH -> LOW transition)
  if (currentButtonState == LOW && lastButtonState == HIGH) {
    ledState = !ledState;
    digitalWrite(LED_PIN, ledState);
    delay(50); // simple debounce
  }

  lastButtonState = currentButtonState;
}
```

## Result
The push button was successfully interfaced with the microcontroller on the Wokwi platform, and the LED's ON/OFF state was controlled based on button presses, verifying digital input reading using `digitalRead()` and its use in controlling a digital output.
