# Experiment-08- Encoders-and-decoders 
### AIM: To implement 8 to 3 Encoder and  3to8 Decoder using verilog and validate its outputs
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## Encoders
Binary code of N digits can be used to store 2N distinct elements of coded information. This is what encoders and decoders are used for. Encoders convert 2N lines of input into a code of N bits and Decoders decode the N bits into 2N lines.

1. Encoders –
An encoder is a combinational circuit that converts binary information in the form of a 2N input lines into N output lines, which represent N bit code for the input. For simple encoders, it is assumed that only one input line is active at a time.

As an example, let’s consider Octal to Binary encoder. As shown in the following figure, an octal-to-binary encoder takes 8 input lines and generates 3 output lines.

![image](https://user-images.githubusercontent.com/36288975/171543588-bc0746df-a173-4b35-989e-5fb7d385fe8a.png)
## Figure -01 3 to 8 Encoder 


Implementation –

X = D4 + D5 + D6 + D7
Y = D2 +D3 + D6 + D7
Z = D1 + D3 + D5 + D7 
Hence, the encoder can be realised with OR gates as follows:


![image](https://user-images.githubusercontent.com/36288975/171543740-68403b82-aa93-4c98-9343-f32b14885a2e.png)
## Figure -02 3 to 8 Encoder implenentation 

 ### Decoders 
A decoder does the opposite job of an encoder. It is a combinational circuit that converts n lines of input into 2n lines of output.

Let’s take an example of 3-to-8 line decoder.
Implementation –
D0 is high when X = 0, Y = 0 and Z = 0. Hence,

D0 = X’ Y’ Z’ 
Similarly,

D1 = X’ Y’ Z
D2 = X’ Y Z’
D3 = X’ Y Z
D4 = X Y’ Z’
D5 = X Y’ Z
D6 = X Y Z’
D7 = X Y Z 


![image](https://user-images.githubusercontent.com/36288975/171543978-ee2d0671-2846-40a1-8705-507fd6287a49.png)
## Figure -03 8 to 3 Decoder 



![image](https://user-images.githubusercontent.com/36288975/171543866-5a6eace6-8683-49d7-9c4f-a7cb30ec3035.png)
## Figure -04 8 to 3 Decoder implementation 

### Procedure
Step-1: create module encoder and decoder.

Step-2: Get inputs and outputs for encoders and decoders.

Step-3: perform or operation for encoder and and logic for decoders.

Step-4: perform RTL LOGIC and get waveform.

Step-5: End the module.

### PROGRAM 
```
/*
Program for Endocers and Decoders  and verify its truth table in quartus using Verilog programming.
Developed by: ARAVIND SAMY .P
RegisterNumber:  212222230011
*/

ENCONDER:

module encoder(d0,d1,d2,d3,d4,d5,d6,d7,x,y,z);
input d0,d1,d2,d3,d4,d5,d6,d7;
output x,y,z;
or(x,d4,d5,d6,d7);
or(y,d2,d3,d6,d7);
or(z,d1,d3,d5,d7);

DENCODER:

module decoder(x,y,z,d0,d1,d2,d3,d4,d5,d6,d7);
input x,y,z;
output d0,d1,d2,d3,d4,d5,d6,d7;
wire xbar,ybar,zbar;
not(xbar,x);
not(ybar,y);
not(zbar,z);
and(d0,xbar,ybar,zbar);
and(d1,xbar,ybar,z);
and(d2,xbar,y,zbar);
and(d3,xbar,y,z);
and(d4,x,ybar,z);
and(d5,x,ybar,z);
and(d6,x,y,zbar);
and(d7,x,y,z);
endmodule
```

### RTL LOGIC  

## ENCODER:

![ENCODER](https://github.com/Aravindsamy04/Experiment-08-Encoders-and-decoders-/assets/113497037/3cf57309-be55-4000-a449-4bafc50c0867)

## DECODER:

![DECODER](https://github.com/Aravindsamy04/Experiment-08-Encoders-and-decoders-/assets/113497037/9b6b7d5c-1ed7-4765-99ea-708e344dbb61)

### TIMING DIGRAMS  

## ENCODER:

![TIMENC](https://github.com/Aravindsamy04/Experiment-08-Encoders-and-decoders-/assets/113497037/bcd68201-3930-497a-acf4-3582f27fb67a)

## DECODER:

![TIMDEC](https://github.com/Aravindsamy04/Experiment-08-Encoders-and-decoders-/assets/113497037/4b45ba4f-3f3c-4191-869a-83bbc9b6a84e)

### TRUTH TABLE 

## ENCODER:

![TRUENC](https://github.com/Aravindsamy04/Experiment-08-Encoders-and-decoders-/assets/113497037/ad0b882b-c67a-4123-9a99-05a046620748)

## DECODER:

![TRUDEC](https://github.com/Aravindsamy04/Experiment-08-Encoders-and-decoders-/assets/113497037/a00f15d2-fc49-46ba-97c3-2c4851257f2c)

### RESULTS 
Thus, 8 to 3 Encoder and 3 to 8 Decoder is implemented using verilog and its outputs is validated.
