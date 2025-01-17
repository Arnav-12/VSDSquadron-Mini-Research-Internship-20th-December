# VSDSquadron-Mini-Research-Internship-20th-December

As part of my internship, I'm currently working with the **VSDSquadron Mini RISC-V Development Kit**, a robust platform built on the RISC-V architecture. This project offers an opportunity to dive into embedded systems, exploring how RISC-V integrates into various development workflows. I'm gaining practical, hands-on experience with its core features while applying cutting-edge techniques in embedded system design.

## TASK 1 - RISC-V Toolchain Setup and Lab Task Execution

### LAB-1

### The first task assigned was to write a C program that calculates the sum of numbers from 1 to n using gEDIT as a Text Editor.

![s1](https://github.com/user-attachments/assets/b135d537-d85e-4c8a-8d83-4d548490c80f)

![s2](https://github.com/user-attachments/assets/c6db5a35-10b1-418f-8644-b8ebcda08b0b)

### **Ouput generated** : Sum of numbers from 1 to 5 is `15`

![s3](https://github.com/user-attachments/assets/d3c023ef-f651-4496-84f5-d7a0f97fc911)

### Main File Depicting the Assembly instructions

![s4](https://github.com/user-attachments/assets/e57f90cf-d636-444c-9506-cb202f5862a9)

![s5](https://github.com/user-attachments/assets/e33b502c-1e4b-4dce-a14a-b5633fba165c)

### The Number of instructions with `-O1` method

![s6](https://github.com/user-attachments/assets/eac2867e-a8ce-444d-8d1b-6f90e2577073)

### The Number of instructions with `-Ofast` method

![s7](https://github.com/user-attachments/assets/7c1bdcd6-5b14-4dad-a368-b5bd90f59972)

## TASK 2 - **SPIKE Simulation with Optimization Levels `(-O1 vs -Ofast)`**  

### Basic Theory:  

The SPIKE simulator is a RISC-V ISA (Instruction Set Architecture) simulator used to test and validate RISC-V compiled programs. In this task, a simple C program is written, compiled using the RISC-V GCC toolchain, and executed on SPIKE. The behavior of the program is observed with two different optimization levels:  

1. **-O1 (Basic Optimization):** Focuses on reducing code size and improving execution speed without extensive optimization.  
2. **-Ofast (Aggressive Optimization):** Applies all -O3 optimizations along with additional aggressive techniques for maximum performance, potentially sacrificing strict standard compliance.  

### Verifying the C code with n=100 with spike simulation

![s10](https://github.com/user-attachments/assets/a22e4fa3-bfb7-4a2a-9eeb-38eb98a37cdd)

### Using spike commands for debugging of instructions

![s11](https://github.com/user-attachments/assets/0faaaadf-ef9a-4e03-86a4-f76c58440937)

### After implementations of instruction the sp value gets reduced by factor a hexadecimal fector of 10

![s9](https://github.com/user-attachments/assets/9b8d108a-f069-47af-8eae-2538c64314a5)

## TASK 3 - **Analysis of RISC-V Instruction Types and 32-bit Encodings**  

### Objective:  

1. Study RISC-V documentation to list the characteristics of R, I, S, B, U, and J instruction types.  
2. Extract 15 unique RISC-V instructions from the `riscv-objdump` of an application program.  
3. Decode the exact 32-bit binary patterns of these instructions and identify their instruction type.  
4. Upload the identified 32-bit patterns and instruction analysis to the GitHub repository.  

### RISC-V ISA

A RISC-V ISA is defined as a base integer ISA, which must be present in any implementation, plus
optional extensions to the base ISA. The base integer ISAs are very similar to that of the early RISC
processors except with no branch delay slots and with support for optional variable-length instruction
encodings. A base is carefully restricted to a minimal set of instructions sufficient to provide a RISC-V ISA is defined as a base integer ISA, which must be present in any implementation, plus
optional extensions to the base ISA. The base integer ISAs are very similar to that of the early RISC
processors except with no branch delay slots and with support for optional variable-length instruction
encodings.

### Types of Instruction Formats in RISC-V

RISC-V instructions are organized into five main types based on how operands and data are accessed and manipulated.

RISC-V Instruction Types `(R, I, S, B, U, J)`
RISC-V instructions are categorized into six main types, each with a specific format for accessing and manipulating operands. The structure of these instructions includes fields like opcode, rd, rs1, rs2, and immediate values, which allow for flexible operation encoding.

1. `R-Type (Register-Register)` Instruction

Purpose:-

The R-Type format is used for operations that involve two source registers and a destination register. These instructions typically perform arithmetic or logical operations, where data is read from two registers, processed, and stored in a third register.

Fields:-

1.opcode (7 bits): Determines the type of operation (e.g., integer arithmetic, floating-point arithmetic).

2.funct3 (3 bits): Adds further specificity to the operation, helping distinguish between similar instructions (e.g., add vs. sub).

3.funct7 (7 bits): Additional control bits that refine the operation further (e.g., indicating shifts or subtractions).

4.rs1 (5 bits): First source register, providing one operand.

5.rs2 (5 bits): Second source register, providing the other operand.

6.rd (5 bits): Destination register where the result is stored.

![s12](https://github.com/user-attachments/assets/640d75a7-bc13-462c-b8c4-2595a93282c9)

2. `I-Type (Immediate)` Instruction
   
Purpose:-

I-Type instructions perform operations that involve one register and an immediate (constant) value. This type is often used for load instructions, arithmetic with a constant, and setting register values with immediate values.

Fields:-

1.opcode (7 bits): Specifies the operation (e.g., load, arithmetic with an immediate).

2.funct3 (3 bits): Determines the specific operation within the immediate class (e.g., addi for add-immediate, andi for bitwise AND).

3.rs1 (5 bits): Source register that provides the operand.

4.rd (5 bits): Destination register for the result.

5.Immediate (12 bits): Constant value used as an operand, signed or zero-extended depending on the operation.

![s13](https://github.com/user-attachments/assets/4dfe14dc-f1ca-428d-a5a2-fb560a4dc3f7)

3. `S-Type (Store)` Instruction
   
Purpose:-

S-Type instructions are used for store operations, where data from a register is written to memory. The address is calculated by adding an immediate value to a base address provided by a register.

Fields:-

1.opcode (7 bits): Specifies the store operation (e.g., sw for store word).

2.funct3 (3 bits): Defines the type of store operation (e.g., word, byte).

3.rs1 (5 bits): Register holding the base address for the store.

4.rs2 (5 bits): Source register containing the data to store.

5.Immediate (12 bits): Split into two parts (5 bits and 7 bits), represents the offset added to the base address to get the effective memory location.

![s14](https://github.com/user-attachments/assets/1b598915-095c-4079-b8ab-3a00d039d8cc)

4. `B-Type (Branch)` Instruction
   
Purpose:-

B-Type instructions enable conditional branching, allowing the program to jump to a different location based on the result of a comparison. This comparison is between two registers, with a branch taken if the specified condition is met.

Fields:-

1.opcode (7 bits): Indicates a branch operation.

2.funct3 (3 bits): Specifies the type of comparison (e.g., equal, not equal, less than).

3.rs1 (5 bits): First source register for comparison.

4.rs2 (5 bits): Second source register for comparison.

5.Immediate (12 bits): Offset added to the program counter (PC) if the branch is taken. This offset is split into multiple parts within the instruction encoding.

![s15](https://github.com/user-attachments/assets/22afde3f-b7dd-4e5e-b58f-2f3673dc89bd)

5. `U-Type (Upper Immediate)` Instruction
   
Purpose:-

U-Type instructions are used to load a 20-bit immediate value into the upper 20 bits of a register, typically for setting larger immediate values or addresses. This format is often used with instructions that deal with high-order constants.

Fields:-

1.opcode (7 bits): Indicates an upper immediate operation (e.g., lui for Load Upper Immediate).

2.rd (5 bits): Destination register for the immediate value.

3.Immediate (20 bits): The upper 20-bit immediate value to load, with the lower 12 bits of the register typically cleared.

![s16](https://github.com/user-attachments/assets/af9c25d9-c176-4c5c-abc0-56d6fc1e8d3f)

6. `J-Type (Jump) Instruction
   
Purpose:-

J-Type instructions support unconditional jumps to an address computed by adding an immediate value to the current program counter (PC). They are often used for function calls and unconditional jumps.

Fields:-

1.opcode (7 bits): Indicates a jump operation (e.g., jal for Jump and Link).

2.rd (5 bits): Destination register to store the return address (PC + 4).

3.Immediate (20 bits): Offset added to the current PC to get the jump target address. The immediate field is split across the instruction format.

![s17](https://github.com/user-attachments/assets/020d6eab-55d0-4b90-8684-087299ab076a)

### Examples

1. **`lui a0, 0x21`**  
   - **Type**: U-Type
   - **Description**: Load upper immediate 0x21 into `a0`.
   - **Encoding**: `0x02100537`

2. **`addi sp, sp, -16`**  
   - **Type**: I-Type
   - **Description**: Subtract 16 from the stack pointer (sp).
   - **Encoding**: `0xff110113`

3. **`li a2, 15`**  
   - **Type**: I-Type
   - **Description**: Load immediate 15 into `a2`. (This is usually a pseudo-instruction translated into `addi a2, x0, 15`).
   - **Encoding**: `0x00f00113`

4. **`sd ra, 8(sp)`**  
   - **Type**: S-Type
   - **Description**: Store doubleword of return address `ra` at `sp + 8`.
   - **Encoding**: `0x00a13023`

5. **`ld ra, 8(sp)`**  
   - **Type**: I-Type
   - **Description**: Load doubleword from `sp + 8` into `ra`.
   - **Encoding**: `0x00a13003`

6. **`auipc a5, 0xffff0`**  
   - **Type**: U-Type
   - **Description**: Load upper immediate `0xffff0` into `a5`, then add the program counter.
   - **Encoding**: `0xffff0537`

7. **`add a3, a4, a2`**  
   - **Type**: R-Type
   - **Description**: Add `a4` and `a2` and store result in `a3`.
   - **Encoding**: `0x00c202b3`

8. **`sub a1, a0, a2`**  
   - **Type**: R-Type
   - **Description**: Subtract `a2` from `a0`, store result in `a1`.
   - **Encoding**: `0x40a20333`

9. **`jal x1, 12`**  
   - **Type**: J-Type
   - **Description**: Jump to address `PC + 12`, store return address in `x1`.
   - **Encoding**: `0x0000006f`

10. **`jalr x0, x1, 0`**  
    - **Type**: I-Type
    - **Description**: Jump to address in `x1`, store return address in `x0`.
    - **Encoding**: `0x000080e7`

11. **`slli a5, a5, 2`**  
    - **Type**: I-Type
    - **Description**: Shift `a5` left by 2 bits and store result in `a5`.
    - **Encoding**: `0x0022b193`

12. **`bne a2, a3, -4`**  
    - **Type**: B-Type
    - **Description**: Branch if `a2` is not equal to `a3`, with offset -4.
    - **Encoding**: `0xfff2dfe3`

13. **`and a4, a3, a2`**  
    - **Type**: R-Type
    - **Description**: Perform bitwise AND on `a3` and `a2`, store result in `a4`.
    - **Encoding**: `0x00c2e2b3`

14. **`or a5, a4, a3`**  
    - **Type**: R-Type
    - **Description**: Perform bitwise OR on `a4` and `a3`, store result in `a5`.
    - **Encoding**: `0x00e2f2b3`

15. **`xor a6, a4, a3`**  
    - **Type**: R-Type
    - **Description**: Perform bitwise XOR on `a4` and `a3`, store result in `a6`.
    - **Encoding**: `0x00e2f333`

### Summary of 15 RISC-V Instructions with 32-Bit Encoding:-

| Assembly Instruction   | Instruction Type | Encoding (Hexadecimal) |
|------------------------|------------------|-------------------------|
| `lui a0, 0x21`         | U-Type          | `0x02100537`           |
| `addi sp, sp, -16`     | I-Type          | `0xff110113`           |
| `li a2, 15`            | I-Type          | `0x00f00113`           |
| `sd ra, 8(sp)`         | S-Type          | `0x00a13023`           |
| `ld ra, 8(sp)`         | I-Type          | `0x00a13003`           |
| `auipc a5, 0xffff0`    | U-Type          | `0xffff0537`           |
| `add a3, a4, a2`       | R-Type          | `0x00c202b3`           |
| `sub a1, a0, a2`       | R-Type          | `0x40a20333`           |
| `jal x1, 12`           | J-Type          | `0x0000006f`           |
| `jalr x0, x1, 0`       | I-Type          | `0x000080e7`           |
| `slli a5, a5, 2`       | I-Type          | `0x0022b193`           |
| `bne a2, a3, -4`       | B-Type          | `0xfff2dfe3`           |
| `and a4, a3, a2`       | R-Type          | `0x00c2e2b3`           |
| `or a5, a4, a3`        | R-Type          | `0x00e2f2b3`           |
| `xor a6, a4, a3`       | R-Type          | `0x00e2f333`           |

# TASK 4 - **Functional Simulation of RISC-V Core Using Verilog**  

### Objective:  

1. Perform functional simulation using the provided RISC-V core Verilog netlist and testbench.  
2. Execute specified commands to test various functionalities of the core.  
3. Capture waveform snapshots showcasing the simulation results.  
4. Upload the waveform snapshots and observations to the GitHub repository for documentation and reference.

### How to Open GTKWave for Functional Simulation  

Follow the steps below to clone the repository, simulate the RISC-V core, and open GTKWave for waveform analysis:  

1. **Clone the GitHub Repository:**  
   ```bash  
   git clone https://github.com/vinayrayapati/rv32i.git 
   ```  

2. **Navigate to the Project Directory:**  
   ```bash  
   cd rv32i  
   ```  

3. **Compile the Verilog Files:**  
   ```bash  
   iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v  
   ```  

4. **Run the Simulation:**  
   ```bash  
   ./iiitb_rv32i  
   ```
   
![s18](https://github.com/user-attachments/assets/d740ebc7-3d28-401c-8acb-05d6fb377732)

### Visualizing the Waveform in GTKWave  

Once the simulation generates the `.vcd` (Value Change Dump) file, follow these steps to visualize the waveform in GTKWave:  

1. **Run GTKWave with the Generated .vcd File:**  
   ```bash  
   gtkwave iiitb_rv321.vcd  
   ```  

![s19](https://github.com/user-attachments/assets/dc636826-99b4-4da6-816a-d70eb1c82259)

## Below is the Screenshots of the Wave generated:-

![s20](https://github.com/user-attachments/assets/af619a90-d085-4ae0-aefe-f73bfb153bb1)

![s21](https://github.com/user-attachments/assets/2980f6b7-e645-4ff7-85a7-3c87ace811a6)


![s22](https://github.com/user-attachments/assets/506e1cb8-4d25-41a2-a006-09d9b002c799)


![s23](https://github.com/user-attachments/assets/26d4787a-7273-4101-beb0-a8c03410db73)


![s24](https://github.com/user-attachments/assets/e31c835d-6184-4cc7-ba7a-057fe0183f0a)


![s25](https://github.com/user-attachments/assets/8b787a5d-2289-444e-a719-916e85ba6cda)


![s26](https://github.com/user-attachments/assets/ccef042c-ac00-4170-aa3c-a82a69b0c2f5)


![s27](https://github.com/user-attachments/assets/255e41dc-4250-48a7-a443-430fa5148d65)


![s28](https://github.com/user-attachments/assets/f8d0463d-2143-4747-85eb-835c4e08d9aa)


![s29](https://github.com/user-attachments/assets/c1957708-0d9f-4bcb-90ac-e4276efe6dde)


![s30](https://github.com/user-attachments/assets/0d0c2004-6890-439a-8033-027337f4b986)

# **TASK 5 - MotionBuzzer**  

## **Project Overview**

The **MotionBuzzer** system detects motion using a PIR sensor. In its default state (no motion detected), a LED is activated to signal alert status. When motion is detected, LED turns off,the buzzer turns on to indicate motion. This configuration can be used for scenarios where maintaining attention during idle states is critical, such as securing restricted zones or monitoring for unauthorized absence of movement.

## **Components Required**

1. **VSD Board (CH32V00x microcontroller)** – 1  
2. **PIR Sensor** – 1  
3. **Buzzer** – 1  
4. **1 LED** – 1  
5. **Breadboard** – 1  
6. **Jumper Wires** – 7+  

## **Circuit Diagram**

![Screenshot 2025-01-15 165831](https://github.com/user-attachments/assets/a1e056c9-75b5-4cf9-8157-2f4a5efbdbb9)

## **Code**

```#include <ch32v00x.h>
#include <debug.h>

#define BLINKY_GPIO_PORT GPIOD
#define Buzzer_GPIO_PIN GPIO_Pin_6  // Buzzer for motion detected (PD6)
#define LED1_GPIO_PIN GPIO_Pin_2  // LED for no motion detected (PD2)
#define PIR_GPIO_PIN GPIO_Pin_3  // PIR sensor output connected to GPIO Pin 3 (PD3)

#define BLINKY_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)

void NMI_Handler(void) __attribute__((interrupt("WCH-Interrupt-fast")));
void HardFault_Handler(void) __attribute__((interrupt("WCH-Interrupt-fast")));
void Delay_Init(void);
void Delay_Ms(uint32_t n);
void CheckPirStatus(void);

int main(void)
{
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
    SystemCoreClockUpdate();
    Delay_Init();

    GPIO_InitTypeDef GPIO_InitStructure = {0};

    BLINKY_CLOCK_ENABLE;

    // Initialize LED1 and Buzzer
    GPIO_InitStructure.GPIO_Pin = LED1_GPIO_PIN | BUZZER_GPIO_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    // Configure PIR sensor input pin
    GPIO_InitStructure.GPIO_Pin = PIR_GPIO_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU; // Input with pull-up
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    while (1)
    {
        CheckPirStatus();
        Delay_Ms(1000);
    }
}

void CheckPirStatus() {
    uint8_t pirStatus = GPIO_ReadInputDataBit(GPIOD, PIR_GPIO_PIN);

    if (pirStatus == 1) {
        GPIO_WriteBit(GPIOD, LED1_GPIO_PIN, SET);  // Turn on LED1
        GPIO_WriteBit(GPIOD, BUZZER_GPIO_PIN, RESET); // Turn off Buzzer
    } else {
        GPIO_WriteBit(GPIOD, LED1_GPIO_PIN, RESET); // Turn off LED1
        GPIO_WriteBit(GPIOD, BUZZER_GPIO_PIN, SET);   // Turn on Buzzer
    }
}

void NMI_Handler(void) 
{
    // Handle non-maskable interrupt 
}

void HardFault_Handler(void)
{
    while (1)
    {
        // Handle hard fault 
    }
}

void Delay_Ms(uint32_t ms)
{
    volatile uint32_t count = ms * 8000;  
    while (count--) {
        __asm__("nop"); // No operation for delay
    }
}
```

## **Hardware Connections Table**

| **Component**   | **VSD Board Pin** | **Breadboard Pin** | **Connections**                     |
|-----------------|------------------|-------------------|--------------------------------------|
| **PIR Sensor**  | PD3 (GPIO Pin 3)  | OUT                | Motion detection signal              |
|                 | GND               | GND                | Ground                               |
|                 | VCC               | 5V                 | Power supply                         |
| **Buzzer**      | PD2 (GPIO Pin 2)  | Positive terminal  | Active when **motion** is detected   |
|                 | GND               | Negative terminal  | Ground                               |
| **LED**         | PD6 (GPIO Pin 6)  | Anode              | Active when **no motion** is detected   |
|                 | GND               | Cathode            | Ground                               |


## **Explanation of Connections**
- The **PIR sensor** output connects to **PD3**, which reads motion detection status.  
- The **LED** is connected to **PD2** and lights up when **motion is not detected**.   
- The **Buzzer** is connected to **PD6** and becomes **active** when the **motion** detected.  
- Power is supplied to the PIR sensor through **5V** on the VSD board.  
- All ground connections link to a common ground bus.

This configuration ensures proper indication of both states:
- **No motion detected**: The **LED** is on.  
- **Motion detected**: The **LED** turns off, and the **buzzer** turns on.

## **Application Video** 

https://drive.google.com/file/d/1QyBLt-G4fQeWcV6rZNaY-xBcR66yYNoH/view?usp=drive_link
