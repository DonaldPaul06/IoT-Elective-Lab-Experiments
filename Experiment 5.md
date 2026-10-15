## Experiment 5 — Raspberry Pi Switch Controlled LED

**Aim:** To interface a push-button switch with Raspberry Pi GPIO and control an LED based on switch input using Python.

**Components Required:**

| Component | Quantity |
|-----------|----------|
| Raspberry Pi 3 / 4 | 1 |
| LED (Red / Green) | 1 |
| Resistor 220Ω | 1 |
| Push-Button Switch | 1 |
| Breadboard | 1 |
| Jumper Wires (Female–Male) | 6 |

**Circuit Connections:**

| RPi Pin | Component |
|---------|-----------|
| GPIO17 (BCM) — Pin 11 | LED Anode (+) via 220Ω resistor |
| GND — Pin 6 | LED Cathode (−) |
| GPIO18 (BCM) — Pin 12 | Push-button terminal 1 |
| GND — Pin 14 | Push-button terminal 2 |

```
RPi GPIO17 ──── 220Ω ──── LED(+) ──── LED(−) ──── GND
RPi GPIO18 ──── Button ──── GND      (Input, Pull-Up enabled in software)
```

**Code (Python):**
```python
import RPi.GPIO as GPIO
import time

LED_PIN    = 17  # BCM
BUTTON_PIN = 18  # BCM

GPIO.setmode(GPIO.BCM)
GPIO.setup(LED_PIN, GPIO.OUT)
GPIO.setup(BUTTON_PIN, GPIO.IN, pull_up_down=GPIO.PUD_UP)  # Pull-up resistor

try:
    while True:
        button_state = GPIO.input(BUTTON_PIN)

        if button_state == GPIO.LOW:        # Button pressed
            GPIO.output(LED_PIN, GPIO.HIGH) # LED ON
        else:
            GPIO.output(LED_PIN, GPIO.LOW)  # LED OFF

        time.sleep(0.05)  # Small delay to reduce CPU usage

except KeyboardInterrupt:
    print("Program stopped")

finally:
    GPIO.cleanup()
```

**Procedure:**
1. Connect the LED to GPIO17 through a 220Ω resistor, cathode to GND.
2. Connect one terminal of the push-button to GPIO18 and the other to GND.
3. Open the Raspberry Pi terminal: `nano switch_led.py`
4. Enter the code, save and run: `python3 switch_led.py`
5. Press and hold the push-button — observe the LED turning ON.
6. Release the button — observe the LED turning OFF.
7. Press **Ctrl+C** to stop.

**Result:** The LED turns ON when the push-button is pressed and turns OFF when released, confirming successful GPIO digital input reading using internal pull-up resistor and output control on Raspberry Pi using Python.


