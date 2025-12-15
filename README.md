# Exam: PSoC. Shift Register 74HC595**

**Author (team):** [Bugir Liza]<br>

## **Prerequisites**

- PSoC Creator IDE 4.4
- PSoC 5LP Development Kit (CY8CKIT-059)
- 74HC595 Shift Register IC
- 8x LEDs with 220Ω resistors
- Breadboard and connecting wires
- Serial Terminal Software (Tera Term/PuTTY)

## **Compilation**

Build and program using PSoC Creator IDE. Project compiles without errors or warnings.

## **Installation**

No installation required beyond standard PSoC Creator setup.

## **Usage**

### **Hardware Connection:**
```
PSoC 5LP → 74HC595 → LEDs
─────────────────────────────────────────
P2.0 (Digital Output) → DS (Pin 14)
P2.1 (Digital Output) → SHCP (Pin 11)  
P2.2 (Digital Output) → STCP (Pin 12)
PSoC 5V → VCC (Pin 16)
PSoC GND → GND (Pin 8), OE (Pin 13)
MR (Pin 10) → VCC (via 10kΩ pull-up)
Q0-Q7 (Pins 15,1-7) → LEDs (with 220Ω resistors)
```

### **Operation:**
1. Open serial terminal (Tera Term/PuTTY) at 115200 baud, 8N1
2. Observe test patterns in format:
   ```
   === 74HC595 Test ===
   Test 1: Pattern 0xAA
   LEDs 0,2,4,6 should be ON
   Binary: 10101010
   
   Test 2: Pattern 0x55
   LEDs 1,3,5,7 should be ON
   Binary: 01010101
   ```
3. Visual verification with LED patterns:
   - Alternating ON/OFF (0xAA)
   - Complementary pattern (0x55)
   - All LEDs ON (0xFF)
   - All LEDs OFF (0x00)
   - Walking LED animation

## **Results**

implemented 8-bit shift register control system with:

- **Port Expansion**: Controls 8 LEDs with only 3 microcontroller pins
- **Multiple Test Patterns**: 5 distinct test scenarios with visual verification
- **Real-time Binary Display**: Serial output shows binary representation
- **Stable Operation**: No data corruption or timing issues
- **Accurate Timing**: Meets 74HC595 datasheet requirements

```c
// Main functions:
- Write_To_74HC595(uint8_t data) // Core shift register driver
- GPIO_Init() // Pin initialization
- UART communication functions
- Binary display utilities
- Comprehensive test patterns
```

## **Future Improvements**

1. **Hardware SPI Integration**: Replace software timing with PSoC's SPI peripheral
2. **Cascading Support**: Connect multiple 74HC595 for 16+ outputs
3. **Graphical Interface**: Add PC application for pattern control
4. **Real-time Control**: Accept pattern commands via UART
5. **PWM Dimming**: Implement brightness control for LEDs
