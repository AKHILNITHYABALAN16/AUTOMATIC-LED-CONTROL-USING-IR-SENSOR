# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1200" alt="Screenshot (64)" src="https://github.com/user-attachments/assets/6aed1a84-6937-4f03-b03e-56651f488dd6" />

2. Click **File → New STM32 Project**.
  <img width="1920" height="1200" alt="Screenshot (67)" src="https://github.com/user-attachments/assets/0564262d-0aab-4fe3-b9b0-cf2ee8db43c8" />
  <img width="1920" height="1200" alt="Screenshot (81)" src="https://github.com/user-attachments/assets/0bc35bbc-52a6-4f73-88a8-9e40714dc005" />

3. Select the **target microcontroller** or board and click **Next**.
  <img width="1920" height="1200" alt="Screenshot (92)" src="https://github.com/user-attachments/assets/033e430d-e5ec-41f3-917e-c488266b94a2" />

4. Name the project.
   <img width="1920" height="1200" alt="Screenshot (93)" src="https://github.com/user-attachments/assets/b7ac3358-ce64-4c13-86fe-e718a031b866" />

  
6. The corresponding `.ioc` file will be generated automatically.
  <img width="1920" height="1200" alt="Screenshot (94)" src="https://github.com/user-attachments/assets/c647375a-2d02-4357-bba1-2d8530593576" />
<img width="1920" height="1200" alt="Screenshot (95)" src="https://github.com/user-attachments/assets/23527eb0-cec8-483a-b536-742313f20cfd" />


7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1920" height="1200" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/8381b056-65ae-4437-aa90-af9ed5bbfa94" />



8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="1920" height="1200" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/f22321f8-47c3-41ec-ae3f-963d661593b5" />

 
9. Edit the generated main program as required.
   <img width="1920" height="1200" alt="Screenshot (97)" src="https://github.com/user-attachments/assets/017d95a7-d553-4407-869d-b7e23541da29" />
<img width="1920" height="1200" alt="Screenshot (101)" src="https://github.com/user-attachments/assets/d0c5ac57-766a-46b0-b975-f3739cc59331" />

10. Click **Project → Build All**.
    <img width="1920" height="1200" alt="Screenshot (101)" src="https://github.com/user-attachments/assets/98340c96-4d23-448b-8c26-7a8121458535" />


11. Link the **HEX file** using the post-build process.
   <img width="1421" height="403" alt="image" src="https://github.com/user-attachments/assets/0b7edf70-2ec1-4358-9caf-7d99556a2d8c" />

12. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1920" height="1200" alt="Screenshot (101)" src="https://github.com/user-attachments/assets/baba83f9-9504-4687-bdaa-c5ea97f2997c" />


13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-11-11 at 20 33 49_b39823f3](https://github.com/user-attachments/assets/347c84f6-0a94-43e9-ad60-748b7355cdaa)


CASE 2: LED OFF
![WhatsApp Image 2025-11-11 at 20 33 50_25703eb1](https://github.com/user-attachments/assets/7906dbe3-a125-4525-b642-5df64318dac2)

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




