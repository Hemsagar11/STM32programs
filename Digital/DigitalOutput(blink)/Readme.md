## Blink Program in STM32
- Blinking the on-board led is one of the easiest and begginer friendly program to get you started with STM32 Programming.

**Boards Used:** NUCLEO-F767ZI, B-L475EIOT01A1

### Instructions:
1. Create a new project in STM32cubeIDE and in the pinout configuration palette, set GPIO mode as OUPUT for the pins connected to on-board LEDs.
2. These pins can be know by refering the usermanual of the boards [B-L475E](https://www.st.com/resource/en/user_manual/um2153-discovery-kit-for-iot-node-multichannel-communication-with-stm32l4-stmicroelectronics.pdf) ,
[NUCLEO-F7](https://www.st.com/resource/en/user_manual/um1974-stm32-nucleo144-boards-mb1137-stmicroelectronics.pdf)
3. Thes pins can also be seen in the UI in the IDE if "set default peripherals" was given a yes!.
4. Generate the code and inside the while HAL_GPIO_Writepin() function is used to set the value to the GPIO output pin along with a certain amount of delay.
```
    HAL_GPIO_WritePin(LED2_GPIO_Port,LED2_Pin,GPIO_PIN_SET); // set the pin HIGH i.e. ON the LED 
	HAL_Delay(500);
	HAL_GPIO_WritePin(LD3_GPIO_Port,LD3_Pin,pin_status);
	HAL_Delay(500); // set the pin LOW i.e. OFF the LED 
```
- Alternatively, we can use HAL_GPIO_TogglePin() function to SET or RESET the GPIO pin.
```
    HAL_GPIO_TogglePin(GPIOB,GPIO_PIN_7);
	HAL_Delay(2000);
```

### Output:
