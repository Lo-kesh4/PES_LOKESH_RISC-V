# PES_LOKESH_RISC-V
<details>

<summary><b> DAY 3 - Digital Logic with TL-verilog and Makerchip </b></summary>

+ Combinational logic in TL-Verilog using Makerchip
  - Welcome
  - Introduction To Logic Gates
  - Basic Mux Implementation And Introduction To Makerchip
  - Labs For Combinational Logic
+ Sequential logic
  - Introduction To Sequential Logic And Counter Lab
  - Sequential Calculator Lab
+ Pipelined logic
  - Pipelined Logic And Re-Timing
  - Pipeline Logic Advantages And Demo In Platform
  - Lab On Error Conditions Within Computation Pipeline
  - Lab On 2-Cycle Calculator
+ Validity
  - Introduction To Validity And Its Advantages
  - Lab On Validity And Valid When Condition
  - Lab To Compute Total Distance
  - Lab on 2-cycle Calculator with Validity
  - Calulator Single Value Memory Lab
+ Wrap-up
  - Introduction To Hierarchy Concept
  
<details>

<summary><b> LAB WORK </b></summary> 

### Combinational logic in TL-Verilog using Makerchip
Refer to the github repository [https://github.com/stevehoover/RISC-V_MYTH_Workshop](https://github.com/stevehoover/RISC-V_MYTH_Workshop) for the preceding labs.

The basic logic gates are NOT, AND, OR, XOR, NAND, NOR and XNOR. These can be used to make all combinational logic circuits. 
![CL](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/35c2e7a0-dd4b-44da-9b35-3dc9e4df6b45)


For example a mulitplexer or a mux. We can implement it using a ternary operator in verilog.
Go to [makerchip.com](https://myth.makerchip.com/) and launch the makerchip ide.

+ Getting used to the makerchip platform

  ![1](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/e8e8e77a-c264-4f2a-a561-2a0cb3b362a1)

  
+ Inverter.
  A) Inverter
     1. Open "Examples" (under "Tutorials").
     2. Load "Default Template".
     3. Make an inverter.
        On line 16, in place of: //...
        (Preserve 3-space indentation, no tabs)
        type:
        ```$out = $in1;```
     4. Compile ("E" menu) & Explore
  ![inv](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/b12da6bd-8c13-4937-8264-39ad03935298)

+ Vector
  $out[4:0] creates a “vector” of 5 bits.
  Arithmetic operators operate on vectors as binary numbers.
  1.Try:
  ```$out[4:0] = $in1[3:0] + $in2[3:0];```
  
  ![Vector](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/cadf2a27-1422-4f11-9725-272a5d96601b)

+ MUX
  
  ![sel](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/29fa2d17-611d-4bb9-9e46-41ec4eda9be7)

####  Combinational calculator
  1. Implement this.
  2. Use:
        ```$val1[31:0] = $rand1[3:0] ;```
        ```$val2[31:0] = $rand2[3:0] ;```
        for inputs to keep values small.
  4. We’ll return to this, so “Save as new project”, bookmark, and open a new Makerchip IDE in a new tab.

  ![calu](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/169da563-c02f-4e9d-8447-d03b097a1935)


#### Sequential Logic
Sequential logic is sequenced by a clock signal. The circuit is constructed to enter a known state in response to a reset signal. The sequential circuit in its entirety can be viewed as a state machine.

+ Fibonacci series
  ![Screenshot from 2023-10-12 11-18-28](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/b992d6b5-c959-4213-9774-43d5027f9640)

+ Counter
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/137b90b7-c9c2-4d64-9ec6-6afa1b16c061)

  
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/a72ddd80-13fc-4cd5-89ad-772772a0cf6c)
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/84ffd54e-27e9-4167-8cdc-4afc171d4d9b)

####  Sequential Calculator
  A real calculator remembers the last result, and uses it for the next calculation.
  1. Return to the calculator.
  2. Update the calculator to perform a new calculation each cycle where
     ```$val1[31:0] ```= the result of the previous calculation.
  3. Reset $out to zero.
  4. Copy code and save outside of Makerchip (just to be safe).
     
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/d8d33754-ccf7-468f-9ce3-844191343d87)

  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/929ac455-1738-448e-b5f1-061fa184eadd)

+ A Simple Pipeline through Pythogoren 
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/75924b35-6615-4778-bd30-69e7367d2238)

## Identifiers and Types
   Type of an identifier determined by symbol prefix and case/delimitation style.
   
   First token must start with two alpha chars. These determine delimitation style
   1. ```$lower_case```: pipe signal
   2. ```$CamelCase```: state signal (technically, this is “Pascal case”)
   3. ```$UPPER_CASE```: keyword signal
      
  Numbers end tokens (after alphas)
   1. ```$base64_value```: good
   2. ```$bad_name_5```: bad
      
  Numeric identifiers
  1. ```>>1```: ahead by 1
     
+ Fibonacci Series in a Pipeline
  
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/2578382d-161f-4c6a-bfaf-11f386594532)

  ```
  |fib
         @1
            $num[31:0] = *reset ? 1 : (>>1$num + >>2$num);
  ```
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/efe5d404-6d5a-4a13-a5ee-bc44bb7e7bc6)

  Pipline
  
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/d9b0bda7-7840-4f3e-bed2-e9c900e65811)
  
  which ORs together (||) various error conditions that can occur within a computation pipeline.
  
####  Counter and Calculator in Pipeline
  1. Put calculator and counter in stage @1 of a |calc pipeline.
  2. Check log, diagram, and waveform.
  3. Confirm save.
  Note:1. The ```$reset = *reset``` expression should be moved under the pipeline and pipestage as well.
       2. At this point, be sure to use the Calculator Starter Code from the github repo(stevehoover).
     
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/8db6e546-b4c1-4a24-b493-16e412dfa6f8)


#### Cycle Calculator
  At high frequency, we might need to calculate every other cycle.
  1. Change alignment of $out (to calculate every other cycle).
  2. Change counter to single-bit (to indicate every other cycle).
  3. Connect $valid (to clear alternate outputs).
  4. Retime mux to @2 (to ease timing; no functional change).
  5. Verify behavior in waveform.
  6. Save.
     
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/8753b18a-e64c-4827-8a6f-b8e675feca49)

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/acde37fa-4fb3-4649-906f-969230733411)

## Validity 
Validity provides:
  + Easier debug
  + Cleaner design
  + Better error checking
  + Automated clock gating
#### Clock Gating
Motivation: 
  + Clock signals are distributed to EVERY flip-flop.
  + Clocks toggle twice per cycle.
  + This consumes power.
    
Clock gating avoids toggling clock signals.

TL-Verilog can produce fine-grained gating (or enables).

#### Total Distance (Makerchip walkthrough)

  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/03f2b167-e9f3-4d5b-ad58-b677a859a786)

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/485d9c01-7ef4-434f-9aa3-6219063c6b8b)

### 2-Cycle Calculator with Validity
  
  1. Use:
        $valid_or_reset = $valid || $reset;
     as a when condition for calculation instead of zeroing $out.

     ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/335d2653-0007-4cb8-bb24-e0d5da9966fe)

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/d5f83e77-d74b-4abf-85f4-b87f9f395a35)

### Calculator with Single-Value Memory
  Calculators support “mem” and “recall”, to remember and recall a value.
  1. Extend $op to 3 bits.
  2. Verify behavior in waveform.
  3. Add memory MUX.
  4. Select recall value in output MUX.
      
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/5857f39b-d5ba-4eaa-804d-aedb64c308c8)

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/5637ca20-c356-4da2-9f01-11157332b6a8)

</details>
</details>
<details>

<summary><b> DAY 4 : Basic RISC-V CPU Micro Architecture </b></summary>

+ Introduction to Simple RISC-V Micro-architecture
  - Micro-architecture of Single Cycle RISC-V CPU
  - Starting Point Code for RISC-V Labs Part-1
  - Starting Point Code for RISC-V Labs Part-2
+ Fetch and decode
  - Implementation Plan and Lab for PC
  - Lab For Instruction Fetch Logic
  - Lab For RV Instruction Types IRSBJU Decode Logic
  - Lab For Instruction Immediate Decode Logic For RV-ISBUJ
  - Lab To Decode other Fields of Instructions For RV-ISBUJ
  - Lab To Decode Instruction Field Based on Instr Type RV-ISBUJ
  - Lab To Decode Individual Instruction
+ RISC-V control logic
  - Lab For Register File Read Part-1
  - Lab For Register File Read Part-2
  - Lab For ALU Operations For add/addi
  - Lab For Register File Write
  - Concept of Array And Register File Details
  - Lab For Implementing Branch Instructions
  - Lab For Completing Branch Instruction Implementation
  - Lab To Create Simple Testbench

<details>

<summary><b> LAB WORK </b></summary>
### Introduction to Simple RISC-V Micro-architecture

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/f047327a-90a8-4235-b357-a355fabb1d60)

### Implementation Plan

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/8d4206c6-1eee-4e77-80f7-9520e23bc231)


The **program counter** is a pointer to the instruction memory. The output of the **instruction memory** is the memory itself which we decode using the **decode block**. Decoding gives us Rs, Rd and immediate values. These are operated on using the **ALU**. **Data memory** is also present for read and write operations.

For the consecutive labs, we will use the "RISC-V lab starting point code" from [https://github.com/stevehoover/RISC-V_MYTH_Workshop](https://github.com/stevehoover/RISC-V_MYTH_Workshop). 

Use the following links : [risc-v-starting-code-1](https://myth.makerchip.com/sandbox?code_url=https:%2F%2Fraw.githubusercontent.com%2Fstevehoover%2FRISC-V_MYTH_Workshop%2Fmaster%2Frisc-v_shell.tlv#)

#### Risc-V-Starting Code
![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/bcb5d217-10cc-4767-8334-5ec1eb234f2d)

Review code containing (or including):
1. A simple RISC-V assembler.
2. An instruction memory containing the sum 1..9 test program.
3. Commented code for register ﬁle and memory.
4. Visualization.

#### 1. Program Counter

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/00f80722-ee0e-4b52-ae7d-d10a22ecade7)

Reset $pc[31:0] to 0 if previous instruction was a “reset instruction” (>>1$reset), and increment by 1 instruction (32’d4 bytes) thereafter. (We’ll add branch support later.)

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/a3d80be9-1b6f-4f20-8a83-b42a2aad5c3e)

Check PC value in simulation and conﬁrm save. PC’s after reset should be 0, 4, 8, ...

#### 2. Instruction Fetch

1. Uncomment //m4+imem(@1), and //m4+cpu_viz(@4) compile, and observe log errors.
2. ```imem```expects inputs:
    + In: ```$imem_rd_en``` (read enable)
    + In: ```$imem_rd_addr [M4_IMEM_INDEX_CNT-1:0]``` and provides output:
    + Out: ```$imem_rd_data[31:0]```
![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/a16ee32d-df5a-4b40-8ef4-b3b3b01968c9)

3. Connect imem interface to read into ```$instr[31:0]``` addressed by ```$pc[M4_IMEM_INDEX_CNT+1:2]``` enabled every cycle after reset.
4. Check ```$instr``` in simulation and conﬁrm save.

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/e35ca3cb-4628-47eb-96b7-369ebef269d4)

#### 3. Instruction Decode

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/515cded5-aa44-4c24-a0eb-8ba817e83103)

#### 4. Instruction Decode with Validity

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/a4d5e7a3-09dc-441e-a67c-18daa412754f)

#### 5. Individual Instruction decode

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/59abdfef-35a5-4182-98cc-e0ef8526d0c8)


#### 6. Register file read

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/f0d91b95-95ee-4f61-81e8-f28a7ac6727a)

#### 7. Arthemetic Logic Unit

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/845da358-3d72-4b6a-83e5-864bcbd17c3e)

#### 8. Register File Write

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/f1104fec-cebe-4ad3-b628-cb0aa8b248c5)

#### 9. Branch Instructions

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/3a2ffd40-8cdd-49dc-bfe7-6cf12647c1ea)

#### 10. Testbench to check functionality

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/d583ec38-60f8-4043-b9ed-d153377ed277)


</details>
</details>
<details>

<summary><b> DAY 5 - Complete Pipelined RISC-V CPU micro-architecture </b></summary>

+ Pipelining the CPU
  - Introduction To Control Flow Hazard And Read After Write Hazard
  - Lab To Create 3-Cycle Valid Signal
  - Lab To Code 3-Cycle RISC-V To Take Care Of Invalid Cycles
  - Lab To Modify 3-Cycle RISC-V To Distribute Logic
+ Solutions to Pipeline Hazards
  - Lab For Register File Bypass To Address Rd-After-Wr Hazard
  - Lab For Branches To Correct The Branch Target Path
  - Lab To Complete Instruction Decode Except Fence, Ecall, Ebreak
  - Lab To Code Complete ALU
+ Load/Store Instructions and Completing RISC-V CPU
  - Introduction To Load Store Instructions And Lab To Redirect Loads
  - Lab To Load Data From Memory To Register File
  - Lab To Instantiate Data Memory To The CPU
  - Lab To Add Stores And Loads To The Test Program
  - Lab To Add Control Logic For Jump Instructions
  - Wrap Up

<details>
<summary><b> Lab Work </b></summary>

