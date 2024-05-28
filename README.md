# SOS Business Card PCB

This project was conceived for the [Hackaday 2024 Business Card Contest](https://hackaday.io/contest/195949-2024-business-card-contest). The idea was to create a logical circuit from discrete components that would generate an SOS signal in Morse code. I wanted to make this project a learning experience for creating logical circuits in a simple and practical way.

## Logical Circuit Design

Morse code has following rules for signaling:

- dot is 1 time unit
- dash is 3 time units
- the space between symbols of the same letter is 1 time unit
- the space between words is 7 time units.

Following these rules SOS signal timing diagram will look like this:
![wavedrome](Design/Wavedrom/waveform.png)

> Diagram is made with [wavedrom online tool](https://wavedrom.com/editor.html). You can import json file from `Design/Wavedrom` for modifications.

We see that 34 independent logical states are needed. This introduces a problem as we could reduce logical circuit complexity by using 32 states instead as it will require 5 inputs for our truth table $(2^5=32)$.

I decided to violate last Morse code signaling rule and use 5 time units for spacing between words instead of 7. Now we can generate our logical circuit, I'm using [Logism](http://www.cburch.com/logisim/) for that. It can take truth table as input and generate logical circuit.

You can find Logism circuit files in `Design/Logism` directory. Generated circuit is not perfect and can be improved manually (by removing duplicated components and changing number of inputs for logical gates).

Final result:

![logism](Design/Logism/simulation.gif)
