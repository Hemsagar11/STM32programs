## Getting a digital input
 - I have used the on board *User Button* to get input as 1 or 0 (that's digital basically!) and control the onboard LED's LD2 & LD3.

 **Board Used:** NUCLEO-F767ZI

### Instructions:
1. Assuming the board is connected to the PC, open up STM32cubeIDE and create a new STM32 project by selecting the board from board selector option.
2. After the GUI is initialized, Configure LED and Button GPIO pins such as,
    - Button is named as userButton(any name can be given) and it is connected to the PC13 pin.
        - GPIO mode is set to Input mode.
        - No push-up and pull-down is set.
    - LED's are initialsed with names and in Output GPIO mode.
3. Generate the code and inside the while loop in the main file add the logic to turn on or turn off the LED's based on the userButton input.
The logic used in my code:
```
    isButtonPressed = HAL_GPIO_ReadPin(userButton_GPIO_Port, userButton_Pin);
	if(isButtonPressed){
		HAL_GPIO_WritePin(LD2_GPIO_Port, LD2_Pin, GPIO_PIN_SET);
		HAL_Delay(250);
		HAL_GPIO_WritePin(LD3_GPIO_Port, LD3_Pin, GPIO_PIN_RESET);
		HAL_Delay(250);
	}
	else{
		HAL_GPIO_WritePin(LD2_GPIO_Port, LD2_Pin, GPIO_PIN_RESET);
		HAL_Delay(250);
		HAL_GPIO_WritePin(LD3_GPIO_Port, LD3_Pin, GPIO_PIN_SET);
		HAL_Delay(250);
	}
```
According to this,
LD2 i.e LED2 will turn on when the button is pressed while LD3 will be turned off. And when the button is released LD2 will be turned off but LD3 will be turned on.

Complete code is at: ./Core/Src/main.c

Output:
<img src="../Assets/digitalinput.mp4"></img>
