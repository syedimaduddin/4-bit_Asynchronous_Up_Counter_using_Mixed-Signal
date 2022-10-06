# Mixed Signal Circuit Design and Simulation Marathon

## 4-Bit Asynchronous Up Counter using Mixed Signal

- [Abstract](#abstract)
- [Reference Circuit Diagram](#reference-circuit-diagram)
- [Reference Waveform](#reference-waveform)
- [Circuit Details](#circuit-details)
- [Truth Table](#truth-table)
- [Software Used](#software-used)
  - [eSim](#esim)
  - [NgSpice](#ngspice)
  - [Makerchip](#makerchip)
  - [Verilator](#verilator)
- [Circuit Diagram in eSim](#circuit-diagram-in-esim)
- [Verilog Code](#verilog-code)
- [Makerchip](#makerchip-1)
- [Makerchip Plots](#makerchip-plots)
- [Netlists](#netlists)
- [NgSpice Plots](#ngspice-plots)
- [GAW Plots](#gaw-plots)
- [Steps to run generate NgVeri Model](#steps-to-run-generate-ngveri-model)
- [Steps to run this project](#steps-to-run-this-project)
- [References](#references)
- [Acknowlegdements](#acknowlegdements)
- [Author](#author)

## Abstract

In recent years, asynchronous counters have gained
popularity due to their low power consumption and low noise
emissions. Furthermore, they are used as frequency dividers,
as divide-by-N counters. This project involves designing a 4-bit
asynchronous up counter. The circuit will consist of T flip-flops,
a multivibrator and an Analog to Digital Converter (ADC), used
as an interface between digital and analog signal. The emphasis
of the project is to design a mixed signal circuit of a 4-bit
asynchronous up counter. The T flip-flops are for designing a
digital circuit written in Verilog and the multivibrator is for
designing an analog circuit

## Reference Circuit Diagram

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Counter_using_Mixed-Signal/blob/main/Circuit%20Images/Circuit%20Design.png)

## Reference Waveform

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Counter_using_Mixed-Signal/blob/main/Circuit%20Images/Waveform.png)

## Circuit Details

A 4-bit Asynchronous up counter contains four T flip-flops
(digital block) and a multivibrator (analog block) as shown
in Reference Circuit Diagram. It counts from 0 to 2<sup>4</sup>-1, i.e. 15. All flip-flops
have their T-input connected to 1. In each flip-flop, the output
changes asynchronously on the negative edges of its clocks. In
the first T flip-flop, the clock signal is directly applied, which
is a multivibrator signal converted to digital by ADC. When
the clock signal is on a negative edge, the output of the first
T flip-flop toggles. A second T flip-flop is controlled by the
output of the first T flip-flop. Thus, every negative edge of the
output of the first T flip-flop toggles the output of the second
T flip-flop. In the same way, the third and fourth T flip-flops
toggle for every negative edge of clock of the second and third
T flip-flops, respectively
</br>
In the case of T flip-flops, assume the initial status from
rightmost to leftmost is Q<sub>3</sub>Q<sub>2</sub>Q<sub>1</sub>Q<sub>0</sub>=0000. Here, Q<sub>3</sub> & Q<sub>0</sub> are MSB & LSB respectively. In Reference Waveform, we can see the output
waveforms of Q<sub>0</sub>, Q<sub>1</sub>, Q<sub>2</sub>, and Q<sub>3</sub>, and the working of the
4-bit asynchronous up counter is described in Truth Table.

## Truth Table

| No of negative edge of Clock | Q<sub>0</sub> (LSB) | Q<sub>1</sub> | Q<sub>2</sub> | Q<sub>3</sub> (MSB) |
| ---------------------------- | ------------------- | ------------- | ------------- | ------------------- |
| 0                            | 0                   | 0             | 0             | 0                   |
| 1                            | 1                   | 0             | 0             | 0                   |
| 2                            | 0                   | 1             | 0             | 0                   |
| 3                            | 1                   | 1             | 0             | 0                   |
| 4                            | 0                   | 0             | 1             | 0                   |
| 5                            | 1                   | 0             | 1             | 0                   |
| 6                            | 0                   | 1             | 1             | 0                   |
| 7                            | 1                   | 1             | 1             | 0                   |
| 8                            | 0                   | 0             | 0             | 1                   |
| 9                            | 1                   | 0             | 0             | 1                   |
| 10                           | 0                   | 1             | 0             | 1                   |
| 11                           | 1                   | 1             | 0             | 1                   |
| 12                           | 0                   | 0             | 1             | 1                   |
| 13                           | 1                   | 0             | 1             | 1                   |
| 14                           | 0                   | 1             | 1             | 1                   |
| 15                           | 1                   | 1             | 1             | 1                   |
| 16                           | 0                   | 0             | 0             | 0                   |

## Software Used

### eSim

It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD.
</br>
For more details refer:
</br>
https://esim.fossee.in/home

### NgSpice

It is an Open Source Software for Spice Simulations. For more details refer:
</br>
http://ngspice.sourceforge.net/docs.html

### Makerchip

It is an Online Web Browser IDE for Verilog/System-verilog/TL-Verilog Simulation. Refer
</br> https://www.makerchip.com/

### Verilator

It is a tool which converts Verilog code to C++ objects. Refer:
https://www.veripool.org/verilator/

## Circuit Diagram in eSim

The following is the schematic in eSim:
![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Circuit%20Images/Schematic%20in%20esim.png)

## Verilog Code

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Verilog%20Files/Verilog%20Code%20Image.jpg)

## Makerchip

```
\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/  /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/  /* verilator lint_off WIDTHCONCAT*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/ 

//Your Verilog/System Verilog Code Starts Here:
module tff ( input clk, input rstn, input t, output reg q);  
  
  always @ (posedge clk) begin  
    if (!rstn)  
      q <= 0;  
    else  
        if (t)  
            q <= ~q;  
        else  
            q <= q;  
  end  
endmodule  

//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  rstn;//input
		logic  t;//input
		logic  q;//output
//The $random() can be replaced if user wants to assign values
		assign rstn = $random();
		assign t = $random();
		tff tff(.clk(clk), .rstn(rstn), .t(t), .q(q));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule

```

## Makerchip Plots

![image]()

## Netlists

![image]()

## NgSpice Plots

![image]()

## Steps to run generate NgVeri Model

1. Open eSim
2. Run NgVeri-Makerchip
3. Add top level verilog file in Makerchip Tab
4. Click on NgVeri tab
5. Add dependency files
6. Click on Run Verilog to NgSpice Converter
7. Debug if any errors
8. Model created successfully

## Steps to run this project

1. Open a new terminal
2. Clone this project using the following command:</br>
   `git clone https://github.com/syedimaduddin/4-bit_Asynchronous_Counter_using_Mixed-Signal.git`</br>
3. Change directory:</br>
   `cd eSim Project Files/`</br>
4. Run ngspice:</br>
   `ngspice file_name.cir.out`</br>
5. To run the project in eSim:

- Run eSim</br>
- Load the project</br>
- Open eeSchema</br>

## References

1. Digital Electronics: 4 Bit Asynchronous Up Counter, Neso Academy, https://www.youtube.com/watch?v=eEeBh8jfDjg
2. LTspice tutorial 13 : Design and simulation of multivibrator circuit using op-amp, Circuit Generator, https://youtu.be/Zch8gf0l-sI

## Acknowlegdements

1. FOSSEE, IIT Bombay
2. Steve Hoover, Founder, Redwood EDA
3. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
4. Sumanto Kar, eSim Team, FOSSEE

# Author

[Syed Imaduddin](https://github.com/syedimaduddin), B.Tech Electronics Engineering, Zakir Husain College of Engineering and Technology (ZHCET), Aligarh Muslim University(AMU), Aligarh.
