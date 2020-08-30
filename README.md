# 3.3V-Linear-Voltage-Regulator
Converts the Arduino Uno's 5V power supply to a fixed 3.3V output voltage.

## Introduction:
The Arduino Uno already has a 3.3V pin, but it can only provide upto 50 mA. For my purposes (esp8266), I needed to supply a constant 3.3V with current that could go as high as 170 mA.
<br><br>
The Uno's 5V pin can provide upto ~400 mA (when connected by USB). So it seems logical to use a voltage regulator to convert the Uno's 5V to 3.3V, and gain access to its higher current output. 
<br><br>
I did not have a voltage regulator on hand, so I decided to build one myself.

## Schematics:

<p align="center" style="vertical-align: top; position: relative" >
<img align="top" style="vertical-align:top" src="https://github.com/rajatKumar2000/3.3V-Linear-Voltage-Regulator/blob/master/Media/LVR_Simple.PNG" width="500"/>
</p>

This is a schematic of a linear voltage regulator, that utilizes an op-amp and an NPN BJT.
<br><br>
This circuit uses the op-amp for its negative feedback loop to maintain a steady voltage at the load. In this circuit, the load voltage will try to be the same as the reference voltage (V-Ref).
<br><br>
We could also make the load voltage a ratio of the reference voltage if we were to add a voltage divider in the node of the op-amp's inverting terminal.
<br><br>
The BJT is used to supply the load with more current than the op-amp itself could supply.
<br>

<p align="center" style="vertical-align: top; position: relative" >
<img align="top" style="vertical-align:top" src="https://github.com/rajatKumar2000/3.3V-Linear-Voltage-Regulator/blob/master/Media/LVR_simulated.gif" width="800"/>
</p>

This is a [simulation](https://www.falstad.com/circuit/circuitjs.html?ctz=CQAgjCAMB0l3BWcMBMcUHYMGZIA4UA2ATmIxAUgosgCgBzcYlEFAFirGdYUKloCGrDq3Yhs2PijHFqnePHHQUpYgmIE2BBAi5LsyBbQDuwqmjxMWF1iZB5OhKtjTgn-UxL5cWX0Ww9xBBYwdzZQt047dnMRGNYMFjpTeMwWcKlEwIzIijYA0PNaABdxSSsy73cICABaGAw2SQcdPEIwSDA8NiToDDAMHQxCFAlOnQlDWgA3Cnd43k5hkACkeahoJCoYMHVdtmImyGY7RbM58yywBguEljOUPEs6AA8aXz0RiBd08EsAZQAlgBbACuABsBMUAKYAEwAOgBncEAewEsNob10sgkLCcSAkSAKLAAagIAE6AgQAI3B0KRAGFQeTydCAHbFTErfLgcIUFA1HnEkD-Yo0ulIkko8Fi+jQ2gAJXs5l4ytYTyg4nArhgSC2G12xH2h1wJze2AJj3AEQkEAKljJlPF9MRJNoA1WPMKFGWAz48jgG0g7AcCjD8AMABk0bCQEyWezOaYHDw+CnpAEUDMKvEfKx8JqqCJsNADNsNgg7DlvTk0oF02IU97XuBlo8pJApHhZMKSbUFdCAGa0FFuECEAJF46yHXKTUhPgGQFsgAOoM5o8sE81HFIyA2IVY9i1rPoEKhcJH++3U73KE2B6PIWcIFR6NoQA) of the circuit that I have built.
<br><br>
Input Voltage is the 5V pin from the Uno. 
<br>
Reference Voltage is the 3.3V pin from the Uno.
<br><br>
In the simulation, both the input voltage and the load current are constantly changing. Despite this, the output voltage remains stable.

## Example:
