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

+ Combinational calculator
  1. Implement this.
  2. Use:
        ```$val1[31:0] = $rand1[3:0] ;```
        ```$val2[31:0] = $rand2[3:0] ;```
        for inputs to keep values small.
  4. We’ll return to this, so “Save as new project”, bookmark, and open a new Makerchip IDE in a new tab.

  ![calu](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/169da563-c02f-4e9d-8447-d03b097a1935)


### Sequential Logic
Sequential logic is sequenced by a clock signal. The circuit is constructed to enter a known state in response to a reset signal. The sequential circuit in its entirety can be viewed as a state machine.

+ Fibonacci series
  ![Screenshot from 2023-10-12 11-18-28](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/b992d6b5-c959-4213-9774-43d5027f9640)

+ Counter
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/137b90b7-c9c2-4d64-9ec6-6afa1b16c061)

  
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/a72ddd80-13fc-4cd5-89ad-772772a0cf6c)
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/84ffd54e-27e9-4167-8cdc-4afc171d4d9b)

+ Sequential Calculator
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
      2. ```$CamelCase```: state signal (technically, this is
             “Pascal case”)
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
  
+ Counter and Calculator in Pipeline
  1. Put calculator and counter in stage @1 of a |calc pipeline.
  2. Check log, diagram, and waveform.
  3. Confirm save.
  Note:1. The ```$reset = *reset``` expression should be moved under the pipeline and pipestage as well.
       2. At this point, be sure to use the Calculator Starter Code from the github repo(stevehoover).
     
  ![Screenshot from 2023-10-12 16-18-47](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/3370513f-7c07-4dae-bac7-8f808efcc1c6)

+ Cycle Calculator
  At high frequency, we might need to calculate every other cycle.
     1. Change alignment of $out (to calculate every other cycle).
     2. Change counter to single-bit (to indicate every other cycle).
     3. Connect $valid (to clear alternate outputs).
     4. Retime mux to @2 (to ease timing; no functional change).
     5. Verify behavior in waveform.
     6. Save.
  ![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/8753b18a-e64c-4827-8a6f-b8e675feca49)

![image](https://github.com/Lo-kesh4/PES_LOKESH_RISC-V/assets/131575546/acde37fa-4fb3-4649-906f-969230733411)

