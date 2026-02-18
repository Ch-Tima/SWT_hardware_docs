## 08.08
<b>NOTHING IS WORKING :)</b></p>
<b>Nothing seems to have burned out, but there's no image on the screen, and it looks like the STM32 isn't starting.</b>

## 09.10
### Several errors found in the schematic::
- Need to connect GND/VCC to `BTN_UP|BTN_DOWN` the other way around, otherwise the logic in the code would need to be changed, which isn't very logical (i.e., 0 — button pressed, and 1 — button not pressed).
- In `U1.2`, capacitors `C15/4/5/7/8` are connected in series (open circuit), which is incorrect. For this reason, nothing will work.

        Need to place them between VCC - CX - VDD_X, and the second pin of CX to GND.
        
            VCC ________ VDD_X
                    |
                   CXX 
                    |
                   GND

    - `LED_WORK1` is connected to `PC13`, but `PC13` is used when _RTC_ is enabled. Therefore, the pin needs to be changed to another one, otherwise the LED will always be on.

    - The display wouldn't start for several reasons:
    I don't know why, but if you pull _RST_ up to VCC through a `10kOhm` resistor, the display starts, although this isn't mentioned in the documentation. But if you look at the [description](../../display/LX12864B5-1.pdf) of a similar display [GMG12864-072C](../../display/GMG12864-072C%20SERIES%20Spec.pdf), it says there:

                5. PIN ASSIGNMENT
                    |PIN|SYMBOL|  Descriptions  |
                    ...
                    | 2 | RST  | ...When RST is not used, connect the pin to VDD.
                    ...
                page 4
        
        - `C14` was replaced from _20pF_ to _68pF_ for better operation.

## 15.10
    When powered via SWD, sharp jumps in temperature readings on 'T1' were observed, so a `470uF 16V` capacitor was added to the GND/VCC pins — this helped partially.

## 16.10

### 20:00
    Connected the battery (LJB 602030 3.7V 300mAH 1.11Wh) 
    The watch showed 85% charge.

### 21:40
    The watch showed 80% charge

## 17.10 
### 01:00
    The watch showed 77% charge.

### 10:45
    The watch showed 65% charge.

### 17:36
    The watch showed 63% charge.

## 18.10 
### 11:XX
    The watch showed 50% charge. *This entry was made from memory because something went wrong after this point.

### 12:09 
    Almost nothing is visible on the screen. At first glance, the watch isn't working, but the date hasn't reset. When connecting the charger, it showed 20% charge, then it rose to 53%, after which it started rising about 1% every 10 seconds.

    Connected the KWS-MX18L in series (inline) 5V | 0.230A | 21.9 Ohm

    When turning on the backlight: 5V | 0.231A | 21.9 Ohm

    After 74%, the charge level rises slowly.

### 12:32
    Charge level 79% 
    Charging continues 
    5V | 0.232A | 59mAh | 302mWh

### 12:40
    Charge level 81% 
    Charging continues 
    5V | 0.232A | 93mAh | 470mWh 
    There is 3.36V on the GND/VCC pins. 
    Also, overestimated data from the thermistor is observed, specifically a temperature of 27C when the real temperature is 20C.


### 12:53:33
    The watch showed 85% charge. 
    5V | 0.232A | 137mAh | 696mWh 
    No overheating is observed.

### 12:53:56
    The watch showed 75% battery charge. 
    Charging disconnected.


### 12:54:36
    The watch showed 72% charge. 
    Notes: the watch shows a temperature of 25C, the error is decreasing.
### 12:58:43 
    The watch showed 70% charge. 
    Notes: the watch shows a temperature of +22C, the error is only one degree — this is already an acceptable value.
### 16:34
    Charge is 64%, temperature 20.3C, which matches reality.

### 22:14
    The watch showed 62% charge.

_The thermistor and ADC themselves are working correctly. The error is most likely due to the conversion from 5V to 3.3V, the fault being on the SC662K side. Need to replace the voltage regulator and introduce correction values in the code during charging._

## 19.10
### 10:40 
    The watch showed 48% charge.

### 11:30
    The watch showed 49% charge. 
    Something is wrong.

### 12:04
    The watch showed 50% charge. 
    What the... why is the charge increasing? 
    Notes: The backlight barely lights up. 
    Probably the 470 Ohm current limiter is too much, it can be reduced. 
    And it's better to use a MOSFET instead of the 2N3904. The voltage on GND/VCC (used during programming) is 3.1V. 
    The voltage on the battery is 3.37V. The backlight is getting 2.5V.

### 12:16
    The watch showed 50% charge. If you measure at any GND and VCC points, the voltage is 3.06V. But if you measure at the battery contacts, it will be 3.33V. The temperature from the thermistor is 22.8C — within the permissible error range of ~1C. The problem is most likely in the SC662K. After all, at 3.3V it would be better to connect directly, and at 4V via the SC662K, or find a smarter voltage regulator.

### 12:29 
    The charge level is rising — 51%, but there is no charging.\_@-@_/ 
    Most likely, the problem is with the voltage regulation or in the code.
    

### 12:45 
    Full reset (everything cleared), power turned off, and one of the power supply capacitors was removed. 

    *This capacitor is not in the schematic, it was added because strong voltage spikes were observed. 
    
    *A 470 µF 16V capacitor was added to the GND/VCC pins at the SWD pins.

### 12:48
    The watch showed: 52% charge and temperature 23.3C. 
    No sharp voltage spikes in the data. 
    Real temperature is 21.6C. 2.7V on any GND and VCC. 
    On the battery: 3.02V.

### 12:53
    The watch showed: 53% charge and temperature 23.3C.
### 12:55
    Power disconnected.
### 12:57
    When measuring, the voltage on the desoldered battery is 3.1V. 
    Due to the absence of an observer and the risk of deep discharge, the test is terminated.