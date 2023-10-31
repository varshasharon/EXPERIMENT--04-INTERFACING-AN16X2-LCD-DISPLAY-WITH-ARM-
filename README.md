```
Name: E. Varsha Sharon
Register Number: 212222100058
```

# EXPERIMENT 04 INTERFACING AN 16X2 LCD DISPLAY WITH ARM AND DISPLAY STRING


 ## Aim: 
 To Interface a 16X2 LCD display to ARM controller, and simulate it in Proteus 
## Components required: 
STM32 CUBE IDE, Proteus 8 simulator .
## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

What is an ARM7 Processor?
ARM7 processor is commonly used in embedded system applications. Also, it is a balance among classic as well as new-Cortex sequence. This processor is tremendous in finding the resources existing on the internet with excellence documentation offered by NXP Semiconductors. It suits completely for an apprentice to obtain in detail hardware & software design implementation.
 STM32F401xB STM32F401xC ARM® Cortex®-M4 32b MCU+FPU, 105 DMIPS, 256KB Flash/64KB RAM, 11 TIMs, 1 ADC, 11 comm.
interfaces Datasheet - production data Features
• Core: ARM® 32-bit Cortex®-M4 CPU with FPU, Adaptive real-time accelerator (ART Accelerator™) allowing 0-wait state execution from Flash memory, frequency up to 84 MHz, memory protection unit, 105 DMIPS/ 1.
25 DMIPS/MHz (Dhrystone 2.
1), and DSP instructions
• Memories – Up to 256 Kbytes of Flash memory – Up to 64 Kbytes of SRAM


   ## LCD 16X2 
   16×2 LCD is named so because; it has 16 Columns and 2 Rows. There are a lot of combinations available like,
   8×1, 8×2, 10×2, 16×1, etc. But the most used one is the 16*2 LCD, hence we are using it here.

All the above mentioned LCD display will have 16 Pins and the programming approach is also the same and hence the choice is left to you. 
Below is the Pinout and Pin Description of 16x2 LCD Module:

<image src="https://user-images.githubusercontent.com/36288975/233858086-7b1a88a2-f941-475c-86c2-b3bae68bdf7e.png" width=450, height=450>

<image src="https://user-images.githubusercontent.com/36288975/233857710-541ac1c2-786c-4dfc-b7b5-e3a4868a9cb6.png" width=450, height=450>

<image src="https://user-images.githubusercontent.com/36288975/233857733-05df5dbf-1a1e-479e-85bb-8014a39ad878.png" width=450, height=450>

4-bit and 8-bit Mode of LCD:

The LCD can work in two different modes, namely the 4-bit mode and the 8-bit mode. In 4 bit mode we send the data nibble by nibble, first upper nibble and then lower nibble. For those of you who don’t know what a nibble is: a nibble is a group of four bits, so the lower four bits (D0-D3) of a byte form the lower nibble while the upper four bits (D4-D7) of a byte form the higher nibble. This enables us to send 8 bit data.

Whereas in 8 bit mode we can send the 8-bit data directly in one stroke since we use all the 8 data lines.

 8-bit mode is faster and flawless than 4-bit mode. But the major drawback is that it needs 8 data lines connected to the microcontroller. This will make us run out of I/O pins on our MCU, so 4-bit mode is widely used. No control pins are used to set these modes. 
 LCD Commands:

There are some preset commands instructions in LCD, which we need to send to LCD through some microcontroller. Some important command instructions are given below:

Hex Code

Command to LCD Instruction Register

0F

LCD ON, cursor ON

01

Clear display screen

02

Return home

04

Decrement cursor (shift cursor to left)

06

Increment cursor (shift cursor to right)

05

Shift display right

07

Shift display left

0E

Display ON, cursor blinking

80

Force cursor to beginning of first line

C0

Force cursor to beginning of second line

38

2 lines and 5×7 matrix

83

Cursor line 1 position 3

3C

Activate second line

08

Display OFF, cursor OFF

C1

Jump to second line, position 1

OC

Display ON, cursor OFF

C1

Jump to second line, position 1

C2

Jump to second line, position 2
 
## Procedure:
1. When you select STM 32 CUBE IDE, the screen below will show up. 
 
2. Select the New STM 32 Project option under FILE. 

3. Choose the target to be programmed, then click the next button. 

4. Choose the program's title. 

5. An automated equivalent IOC file will be created.
   
6. Choose the necessary pins to setup, such as gipo, in or out, USART, or necessary settings. 

7.Press Ctrl+S to automatically produce all C programmes. 

8. Modify the software as necessary 

9. Include the LCD 16x2 library files as needed, create the programme, utilise the project, and build  

10. once the project is bulild 

11. click on debug option 

12.  Creating Proteus project and running the simulation

13. Create a new Proteus project and place STM32F40xx i.e. the same MCU for which the project was created in STM32Cube IDE. 

14. After creation of the circuit as per requirement
  
16. click on debug and simulate using simulation

## CIRCUIT DIAGRAM 
<image src="https://user-images.githubusercontent.com/36288975/233857974-bda6200e-4f88-4e7b-b189-4da80210fa23.png" width=450, height=450>


## STM 32 CUBE PROGRAM :
```

#include "main.h"
#include "lcd.h"
MX_GPIO_Init();
  /* USER CODE BEGIN 2 */
  Lcd_PortType ports[]={GPIOA,GPIOA,GPIOA,GPIOA};
  Lcd_PinType pins[]={GPIO_PIN_3,GPIO_PIN_2,GPIO_PIN_1,GPIO_PIN_0};
  Lcd_HandleTypeDef lcd;
  lcd = Lcd_create(ports,pins,GPIOB,GPIO_PIN_0,GPIOB,GPIO_PIN_1,LCD_4_BIT_MODE);
  Lcd_cursor(&lcd,0,0);
  Lcd_string(&lcd,"Varsha");
  Lcd_cursor(&lcd,1,0);
  Lcd_string(&lcd,"212222100058");
```


## Output screen shots of proteus  :
 
<image src="https://github.com/varshasharon/EXPERIMENT--04-INTERFACING-AN16X2-LCD-DISPLAY-WITH-ARM-/assets/98278161/9d2ce46f-8144-45b7-aeba-cad2fc55b637" width=450, height=450>

 ## CIRCUIT DIAGRAM (EXPORT THE GRAPHICS TO PDF AND ADD THE SCREEN SHOT HERE): 
<image src="https://github.com/varshasharon/EXPERIMENT--04-INTERFACING-AN16X2-LCD-DISPLAY-WITH-ARM-/assets/98278161/743dea07-4435-4657-bc2c-5dcdd0d9b94e" width=450, height=450>

 
## Result :
Interfacing a lcd display with ARM microcontroller are simulated in proteus and the results are verified.

