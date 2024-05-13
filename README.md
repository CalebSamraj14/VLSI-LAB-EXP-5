# VLSI-LAB-EXP-5
SIMULATION AND IMPLEMENTATION OF FINITE STATE MACHINE

AIM: To simulate and synthesis finite state machine using vivado2023.3.

**APPARATUS REQUIRED:**

vivado 2023.3

PIN DIAGRAM :

![WhatsApp Image 2024-05-13 at 19 38 27_c7ae12a7](https://github.com/CalebSamraj14/VLSI-LAB-EXP-5/assets/163808923/3c5af62b-53b4-485a-bf69-e7297f7aa887)


**PROCEDURE:**


1.Open Vivado: Launch Xilinx Vivado software on your computer.

2.Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3.Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4.Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5.Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6.Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7.Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8.Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9.View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
Logic Diagram :

![image](https://github.com/navaneethans/VLSI-LAB-EXP-5/assets/6987778/34ec5d63-2b3b-4511-81ef-99f4572d5869)

TRUTH TABLE:

![WhatsApp Image 2024-05-13 at 19 38 27_b7d3be50](https://github.com/CalebSamraj14/VLSI-LAB-EXP-5/assets/163808923/99426ded-9783-4df8-9a0d-abe10872b781)


VERILOG CODE:
~~~
module Sequence_Detector_Moore(clock,reset,sequence_in,detector_out);
input clock, reset, sequence_in; 
output reg detector_out; 
parameter  S0=2'b00,S1=2'b01,S2=2'b10,S3=2'b11;
reg [1:0] current_state, next_state; 
// sequential memory of the Moore FSM
always @(posedge clock, posedge reset)
begin
 if(reset==1) 
 current_state <= S0;
 else
 current_state <= next_state; 
end 
// to determine next state 
always @(current_state,sequence_in)
begin
 case(current_state) 
 	S0:begin
		if(sequence_in==1)
   			next_state = S1;
  		else
   			next_state = S0;
 	   end
 	S1:begin
if(sequence_in==0)
   			next_state = S2;
  		else
   			next_state = S1;
 	   end
S2:begin
  	if(sequence_in==1)
   		next_state = S3;
 	 else
   		next_state = S0;
    end 
  S3:begin
  	if(sequence_in==0)
   		next_state = S0;
  	else
   		next_state = S1;
     end
	default:next_state = S0;
endcase
end
// to determine the output of the Moore FSM, output only depends on current state
always @(current_state)
begin 
 case(current_state) 
 	S0:   detector_out = 0;
 	S1:   detector_out = 0;
 	S2:  detector_out = 0;
 	S3:  detector_out = 1;
 	default:  detector_out = 0;
 endcase
end 
endmodule
~~~

OUTPUT:

![WhatsApp Image 2024-05-13 at 19 38 28_88970653](https://github.com/CalebSamraj14/VLSI-LAB-EXP-5/assets/163808923/9fa836fe-7def-4186-915f-39a35223dfb6)


![fsm11](https://github.com/CalebSamraj14/VLSI-LAB-EXP-5/assets/163808923/89457bfc-2a68-47e9-8a46-f26c4fbcb487)


RESULT:

Thus the simulate and synthesis finite state machine using vivado2023.3 is verified



