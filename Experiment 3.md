## Experiment 3 — ESP32 LCD Display

**Aim:** To interface a 16×2 LCD display (I2C) with ESP32 and display text messages on both lines.

**Components Required:**

| Component | Quantity |
|-----------|----------|
| ESP32 Development Board | 1 |
| 16×2 LCD with I2C Module | 1 |
| Breadboard | 1 |
| Jumper Wires | 4 |
| USB Cable | 1 |

**Circuit Connections:**

| ESP32 Pin | I2C LCD Pin |
|-----------|-------------|
| 3.3V / 5V | VCC |
| GND | GND |
| GPIO21 (SDA) | SDA |
| GPIO22 (SCL) | SCL |

```
ESP32          I2C LCD Module
3.3V  ─────── VCC
GND   ─────── GND
GPIO21 ─────── SDA
GPIO22 ─────── SCL
```

**Library Required:** `LiquidCrystal_I2C` (Install via Arduino IDE → Library Manager)

**Code:**
```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Set I2C address (0x27 or 0x3F — check with I2C scanner)
LiquidCrystal_I2C lcd(0x27, 16, 2);

int counter = 0;

void setup() {
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("  JECC IoT Lab  ");
}

void loop() {
  lcd.setCursor(0, 1);
  lcd.print("Count: ");
  lcd.print(counter);
  lcd.print("   ");   // Clear trailing digits
  counter++;
  delay(1000);
}
```

**Procedure:**
1. Connect the I2C LCD module to ESP32 as per the circuit (SDA → GPIO21, SCL → GPIO22).
2. Open Arduino IDE, install the `LiquidCrystal_I2C` library.
3. Upload the code and observe the LCD display.
4. Line 1 should show **"JECC IoT Lab"** and Line 2 should show a live count incrementing every second.
5. If the display does not show text, adjust the contrast potentiometer on the I2C module.

**Result:** The 16×2 LCD displays "JECC IoT Lab" on Line 1 and a live incrementing counter on Line 2, confirming successful I2C communication between ESP32 and the LCD module.

![ESP32 LCD Display](https://github.com/DonaldPaul06/IoT-Elective-Lab-Experiments/blob/main/Images/Experiment%203.jpg)
---

