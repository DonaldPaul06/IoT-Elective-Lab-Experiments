## Experiment 4 — Raspberry Pi LED Blink

**Aim:** To write a Python program to blink an LED connected to Raspberry Pi GPIO17 (BCM) at 1 Hz frequency.

**Components Required:**

| Component | Quantity |
|-----------|----------|
| Raspberry Pi 3 / 4 | 1 |
| LED (Red / Green) | 1 |
| Resistor 220Ω | 1 |
| Breadboard | 1 |
| Jumper Wires (Female–Male) | 3 |

**Circuit Connections:**

| RPi Pin | Component |
|---------|-----------|
| GPIO17 (BCM) — Pin 11 | LED Anode (+) via 220Ω resistor |
| GND — Pin 6 | LED Cathode (−) |

```
RPi GPIO17 (Pin 11) ──── 220Ω ──── LED(+) ──── LED(−) ──── GND (Pin 6)
```

**Code (Python):**
```python
import RPi.GPIO as GPIO
import time

LED_PIN = 17  # BCM numbering

GPIO.setmode(GPIO.BCM)
GPIO.setup(LED_PIN, GPIO.OUT)

try:
    while True:
        GPIO.output(LED_PIN, GPIO.HIGH)  # LED ON
        time.sleep(0.5)
        GPIO.output(LED_PIN, GPIO.LOW)   # LED OFF
        time.sleep(0.5)

except KeyboardInterrupt:
    print("Program stopped")

finally:
    GPIO.cleanup()
```

**Procedure:**
1. Connect the LED to GPIO17 (Physical Pin 11) of Raspberry Pi through a 220Ω resistor.
2. Connect the LED cathode to GND (Physical Pin 6).
3. Open the Raspberry Pi terminal and create a file: `nano led_blink.py`
4. Type the code and save (Ctrl+X → Y → Enter).
5. Run the program: `python3 led_blink.py`
6. Observe the LED blinking. Press **Ctrl+C** to stop.

**Result:** The LED blinks continuously at 1 Hz (500 ms ON, 500 ms OFF), confirming successful GPIO output control using Python on the Raspberry Pi.

---

