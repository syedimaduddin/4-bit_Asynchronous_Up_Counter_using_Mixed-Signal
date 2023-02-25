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
- [Steps to run generate NgVeri Model](#steps-to-run-generate-ngveri-model)
- [Steps to run this project](#steps-to-run-this-project)
- [References](#references)
- [Acknowlegdements](#acknowlegdements)
- [Author](#author)

## Abstract

Asynchronous counters have recently gained popularity due to their low power consumption and low noise emissions. Furthermore, they are used as frequency dividers, as divide-by-N counters. This project involves the design of a 4-bit asynchronous up counter using eSim and Ngspice tools. Specifically, it focuses on the development of a mixed signal circuit for a 4-bit asynchronous up counter. There are T flip-flops, a ring oscillator, an Analog to Digital Converter (ADC), and a Digital to Analog Converter (DAC) in the circuit. This design uses Verilog for the T flip-flops and Sky130 components for the ring oscillator.

## Reference Circuit Diagram

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Circuit_Images/Circuit_Design.png)

## Reference Waveform

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Circuit_Images/Waveform.png)

## Circuit Details

A 4-bit Asynchronous up counter contains four T flip-flops (digital block) and a ring oscillator (analog block) as shown in the Reference Circuit Diagram. It counts from 0 to 2<sup>4</sup>-1, i.e. 15. All flip-flops have their T-input connected to 1. In each flip-flop, the output changes asynchronously on the negative edges of its clocks. In the first T flip-flop, the clock signal is directly applied, which is a ring oscillator signal converted to digital by ADC. When the clock signal is on a negative edge, the output of the first T flip-flop toggles. A second T flip-flop is controlled by the output of the first T flip-flop. Thus, every negative edge of the output of the first T flip-flop toggles the output of the second T flip-flop. In the same way, the third and fourth T flip-flops toggle for every negative edge of clock of the second and third T flip-flops, respectively.
</br>
In the case of T flip-flops, assume the initial status from rightmost to leftmost is Q<sub>3</sub>Q<sub>2</sub>Q<sub>1</sub>Q<sub>0</sub>=0000. Here, Q<sub>3</sub> & Q<sub>0</sub> are MSB & LSB respectively. In the Reference Waveform, we can see the output waveforms of Q<sub>0</sub>, Q<sub>1</sub>, Q<sub>2</sub>, and Q<sub>3</sub>, and the working of the 4-bit asynchronous up counter is described in Truth Table.

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
![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Circuit_Images/Schematic_in_esim.png)

## Verilog Code

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Verilog_Files/Verilog_Code_Image.jpg)

## Makerchip

```
\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/  /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/  /* verilator lint_off WIDTHCONCAT*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/

//Your Verilog/System Verilog Code Starts Here:
module imad_tff ( input clk, input rstn, input t, output reg q);  
  
  always @ (negedge clk) begin  
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
		imad_tff imad_tff(.clk(clk), .rstn(rstn), .t(t), .q(q));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule
```

## Makerchip Plots

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Verilog_Files/Makerchip_Plot.jpg)

## Netlists





```
* d:\imad_work_folder\vlsi\competitions\mixed_signal_competition(24.sept.2022)\github_repo\asynchronous-counter-4_bit\esim_project_files\four_bit_async_counter_syed_imaduddin\four_bit_async_counter_syed_imaduddin.cir

.include "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130_fd_pr__model__r+c.model.spice"
.lib "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130.lib.spice" tt
.include "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130_fd_pr__model__linear.model.spice"
.include "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130_fd_pr__model__pnp.model.spice"
.include "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130_fd_pr__model__inductors.model.spice"
.include "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130_fd_pr__model__diode_pw2nd_11v0.model.spice"
.include "D:\FOSSEE\eSim\library\sky130_fd_pr\models\sky130_fd_pr__model__diode_pd2nw_11v0.model.spice"
v1 in gnd  dc 1.8
* u3  in plot_v1
v2  rst gnd pulse(0 1.8 0.1m 0.1m 0.1m 1000 200)
* u7  q0 plot_v1
* u8  q1 plot_v1
* u10  q2 plot_v1
* u11  q3 plot_v1
* u12  clk rst t net-_u12-pad4_ net-_u12-pad5_ net-_u12-pad6_ adc_bridge_3
* u13  net-_u13-pad1_ net-_u13-pad2_ net-_u13-pad3_ net-_u13-pad4_ q0 q1 q2 q3 dac_bridge_4
* u14  clk plot_v1
* u1  rst plot_v1
* u2  t plot_v1
* s c m o d e
xsc8 gnd q3 in sky130_fd_pr__res_generic_pd L=5.2 W=1
xsc7 gnd q2 in sky130_fd_pr__res_generic_pd L=5.2 W=1
xsc6 gnd q1 in sky130_fd_pr__res_generic_pd L=5.2 W=1
xsc5 gnd q0 in sky130_fd_pr__res_generic_pd L=5.2 W=1
xsc2 net-_sc1-pad1_ clk gnd gnd sky130_fd_pr__nfet_01v8 
xsc1 net-_sc1-pad1_ clk in in sky130_fd_pr__pfet_01v8 
xsc9 net-_sc10-pad1_ net-_sc1-pad1_ gnd gnd sky130_fd_pr__nfet_01v8 
xsc4 net-_sc10-pad1_ net-_sc1-pad1_ in in sky130_fd_pr__pfet_01v8 
xsc12 clk net-_sc10-pad1_ gnd gnd sky130_fd_pr__nfet_01v8 
xsc11 clk net-_sc10-pad1_ in in sky130_fd_pr__pfet_01v8 
xsc3 net-_sc1-pad1_ gnd sky130_fd_pr__cap_mim_m3_1 W=10000 L=10000 MF=1
xsc10 net-_sc10-pad1_ gnd sky130_fd_pr__cap_mim_m3_1 W=10000 L=10000 MF=1
xsc13 clk gnd sky130_fd_pr__cap_mim_m3_1 W=10000 L=10000 MF=1
v3  t gnd pulse(0 1.8 0.1m 0.1m 0.1m 1000 200)
* u4  net-_u12-pad4_ net-_u12-pad5_ net-_u12-pad6_ net-_u13-pad1_ imad_tff
* u5  net-_u13-pad1_ net-_u12-pad5_ net-_u12-pad6_ net-_u13-pad2_ imad_tff
* u6  net-_u13-pad2_ net-_u12-pad5_ net-_u12-pad6_ net-_u13-pad3_ imad_tff
* u9  net-_u13-pad3_ net-_u12-pad5_ net-_u12-pad6_ net-_u13-pad4_ imad_tff
a1 [clk rst t ] [net-_u12-pad4_ net-_u12-pad5_ net-_u12-pad6_ ] u12
a2 [net-_u13-pad1_ net-_u13-pad2_ net-_u13-pad3_ net-_u13-pad4_ ] [q0 q1 q2 q3 ] u13
a3 [net-_u12-pad4_ ] [net-_u12-pad5_ ] [net-_u12-pad6_ ] [net-_u13-pad1_ ] u4
a4 [net-_u13-pad1_ ] [net-_u12-pad5_ ] [net-_u12-pad6_ ] [net-_u13-pad2_ ] u5
a5 [net-_u13-pad2_ ] [net-_u12-pad5_ ] [net-_u12-pad6_ ] [net-_u13-pad3_ ] u6
a6 [net-_u13-pad3_ ] [net-_u12-pad5_ ] [net-_u12-pad6_ ] [net-_u13-pad4_ ] u9
* Schematic Name:                             adc_bridge_3, NgSpice Name: adc_bridge
.model u12 adc_bridge(in_low=1.0 in_high=2.0 rise_delay=1.0e-9 fall_delay=1.0e-9 ) 
* Schematic Name:                             dac_bridge_4, NgSpice Name: dac_bridge
.model u13 dac_bridge(out_low=0.0 out_high=5.0 out_undef=0.5 input_load=1.0e-12 t_rise=1.0e-9 t_fall=1.0e-9 ) 
* Schematic Name:                             imad_tff, NgSpice Name: imad_tff
.model u4 imad_tff(rise_delay=1.0e-9 fall_delay=1.0e-9 input_load=1.0e-12 instance_id=1 ) 
* Schematic Name:                             imad_tff, NgSpice Name: imad_tff
.model u5 imad_tff(rise_delay=1.0e-9 fall_delay=1.0e-9 input_load=1.0e-12 instance_id=1 ) 
* Schematic Name:                             imad_tff, NgSpice Name: imad_tff
.model u6 imad_tff(rise_delay=1.0e-9 fall_delay=1.0e-9 input_load=1.0e-12 instance_id=1 ) 
* Schematic Name:                             imad_tff, NgSpice Name: imad_tff
.model u9 imad_tff(rise_delay=1.0e-9 fall_delay=1.0e-9 input_load=1.0e-12 instance_id=1 ) 
.tran 10e-03 2.5e-00 0e-00

* Control Statements 
.control
run
print allv > plot_data_v.txt
print alli > plot_data_i.txt
plot v(in)
plot v(q0)
plot v(q1)
plot v(q2)
plot v(q3)
plot v(clk)
plot v(rst)
plot v(t)
.endc
.end
```


## NgSpice Plots

![image](https://github.com/syedimaduddin/4-bit_Asynchronous_Up_Counter_using_Mixed-Signal/blob/main/Circuit_Images/Waveform_in_ngspice.png)

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
   `cd eSim_Project_Files/four_bit_async_counter_Syed_Imaduddin/`</br>
4. Run ngspice:</br>
   `ngspice four_bit_async_counter_Syed_Imaduddin.cir.out`</br>
5. To run the project in eSim:
	- Run eSim</br>
	- Load the project</br>
	- Open eeSchema</br>

## References

1. Digital Electronics: 4 Bit Asynchronous Up Counter, Neso Academy, https://www.youtube.com/watch?v=eEeBh8jfDjg
2. Cadence Tutorial for Ring Oscillator with Parametric sweep, GoldLighT Technologies Pvt. Ltd., https://youtu.be/t5emusIwI70

## Acknowlegdements

1. FOSSEE, IIT Bombay, https://fossee.in/
2. Steve Hoover, Founder, Redwood EDA
3. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
4. Sumanto Kar, eSim Team, FOSSEE
5. Indian Institute of Technology Bombay, http://iitb.ac.in/
6. Google, https://www.google.co.in/
7. Spoken Tutorial, https://spoken-tutorial.org/
8. VLSI System Design, https://www.vlsisystemdesign.com/
9. Chips to Startup (C2S), https://www.c2s.gov.in/

# Author

[Syed Imaduddin](https://github.com/syedimaduddin), B.Tech Electronics Engineering, Zakir Husain College of Engineering and Technology (ZHCET), Aligarh Muslim University(AMU), Aligarh.
