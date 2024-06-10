# VSDSquadron Mini Research Internship
###   Task 4 ---> Project Description
## Project : 4-bit SERIAL IN PARALLEL OUT [SIPO] Shift Register
#### INTRODUCTION:
* In the realm of digital electronics, serial-in parallel-out (SIPO) shift registers play a pivotal role in various applications, offering efficient data transfer and storage capabilities. These registers form a fundamental component in digital systems, facilitating the conversion of serial data streams into parallel data outputs.<br/>
* The essence of SIPO shift registers lies in their ability to receive data serially, bit by bit, and then distribute this data in parallel fashion across multiple output lines simultaneously. This process enables the expansion of available output ports, effectively increasing the capacity for data transmission and manipulation within a digital circuit.<br/>
#### REQUIRED COMPONENTS:
* VSD SQUADRON MINI BOARD
* LED x4
* RESISTORS [220 OHM]x4
* JUMPER WIRES
* POWER SUPPLY
* BREAD BOARD

### CIRCUIT LAYOUT:
![Screenshot 2024-06-10 220042](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/cb23df9c-b5ae-4f2c-95fb-bda51a24a965)
<br/>
### PIN CONNECTION:
![Screenshot 2024-06-10 221456](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/36d09db8-7885-4863-a484-1b818049f253)
<br/>
#### CURRENT SERIAL DATA PATTERN:
![Screenshot 2024-06-10 213644](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/0b4440b3-5f59-4b8c-b1e1-8def2af8bcb6)
<br/>
### CODE:
```
#include <ch32v00x.h>

#define BIT0_PIN GPIO_Pin_4 // Bit 0 output (PD4)
#define BIT1_PIN GPIO_Pin_5 // Bit 1 output (PD5)
#define BIT2_PIN GPIO_Pin_6 // Bit 2 output (PD6)
#define BIT3_PIN GPIO_Pin_3 // Bit 3 output (PD3)
#define GPIO_PORT GPIOD // GPIO port for all the above pins

void GPIO_Config(void) {
    // Enable the clock for GPIOD
   RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);

    // Configure PD4, PD5, PD6, and PD3 as outputs
    GPIO_InitTypeDef GPIO_InitStructure;
    GPIO_InitStructure.GPIO_Pin = BIT0_PIN | BIT1_PIN | BIT2_PIN | BIT3_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Push-pull output
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIO_PORT, &GPIO_InitStructure);
}

void outputBits(uint8_t data) {
    // Set or reset each GPIO pin according to the corresponding bit in the data
    if (data & 0x01) {
        GPIO_SetBits(GPIO_PORT, BIT0_PIN);
    } else {
        GPIO_ResetBits(GPIO_PORT, BIT0_PIN);
    }
    if (data & 0x02) {
        GPIO_SetBits(GPIO_PORT, BIT1_PIN);
    } else {
        GPIO_ResetBits(GPIO_PORT, BIT1_PIN);
    }
    if (data & 0x04) {
        GPIO_SetBits(GPIO_PORT, BIT2_PIN);
    } else {
        GPIO_ResetBits(GPIO_PORT, BIT2_PIN);
    }
    if (data & 0x08) {
        GPIO_SetBits(GPIO_PORT, BIT3_PIN);
    } else {
        GPIO_ResetBits(GPIO_PORT, BIT3_PIN);
    }
}

int main() {
    SystemCoreClockUpdate();
    Delay_Init();

    // Initialize the GPIO for the output bits
    GPIO_Config();

    uint8_t patterns[] = {0x0, 0x1, 0x3, 0x7, 0xF, 0xE, 0xC, 0x8};
    uint8_t pattern_count = sizeof(patterns) / sizeof(patterns[0]);
    uint8_t current_pattern = 0;

    while (1) {
        // Output the current pattern to the GPIO pins
        outputBits(patterns[current_pattern]);

        // Move to the next pattern
        current_pattern++;
        if (current_pattern >= pattern_count) {
            current_pattern = 0;
        }

        Delay_Ms(2000); // Delay for visualization
    }

    return 0;
}
```

## WORKING VIDEO:

https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/a32d18aa-2afc-4837-9ed5-f2d1a3819f46

### CHANGING PATTERN:
#### NEW PATTERN:
![Screenshot 2024-06-10 235134](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/8df1878f-52a2-4836-bfe7-625131c7ecba)
<br/>

