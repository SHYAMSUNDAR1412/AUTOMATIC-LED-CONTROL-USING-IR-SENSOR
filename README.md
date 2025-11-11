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
  <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/97416402-9595-4a11-aac6-e05e61b3e832" />


2. Click **File → New STM32 Project**.
   <img width="1000" height="620" alt="image" src="https://github.com/user-attachments/assets/0c5deb4b-e1a4-4397-8736-06a6598f18a8" />

3. Select the **target microcontroller** or board and click **Next**.
  <img width="1074" height="645" alt="image" src="https://github.com/user-attachments/assets/5ab607ef-6063-458f-a658-458ccb48d5b3" />



4. Name the project.
  <img width="993" height="601" alt="image" src="https://github.com/user-attachments/assets/b71e5279-cf69-41b5-83d4-f99f73079357" />

5. The corresponding `.ioc` file will be generated automatically.
  <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/c39ae85a-8e3b-4d44-9072-cf9456eb2355" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
 <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/c8c1308c-5f1e-4c2b-90bf-e9ccc9effbb5" />
 <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/2dbc9cc2-1069-4807-989e-8b2a387bf148" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/0ac7d5c3-ec29-4e65-bcae-e17c0493ac57" />

8. Edit the generated main program as required.
  <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/c510f7da-353e-4d10-8afb-fad7e4562edc" />
  <img width="1104" height="621" alt="image" src="https://github.com/user-attachments/assets/7fd6fb06-8719-4b26-8640-388a4c6b93d1" />


9. Click **Project → Build All**.
<img width="1069" height="599" alt="image" src="https://github.com/user-attachments/assets/195b4ead-4823-4a8f-97c8-ef1d383bd903" />

10. Link the **HEX file** using the post-build process.
   <img width="1069" height="639" alt="image" src="https://github.com/user-attachments/assets/a0ec054d-e5d5-4def-ac85-9277d8d97c7d" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1000" height="545" alt="image" src="https://github.com/user-attachments/assets/c22b5bf0-16ed-47b1-8ba5-4a9c4270e50f" />

12 . Click **Run** to execute the program.
    <img width="1000" height="545" alt="image" src="https://github.com/user-attachments/assets/955c79f9-b9fc-4b71-a770-165675218cd2" />

    
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
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/5e6bb4e3-5166-43b7-a09f-34ad327b61fd" />


CASE 2: LED OFF
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/18603ae7-d446-4559-87cb-d46152e46521" />


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




