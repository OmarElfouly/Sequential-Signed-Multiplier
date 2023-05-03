# Digital Design I - Project II - Sequential Signed Multiplier
## Project members:
- Ahmed Ali
- Omar Elfouly
- Bavly Remon
- Omar Anwar

## Demo 1
Dr. Shalan's unisgned multiplier, found in "Lectures 19-21: RTL & ASM Charts" slide 5, was used while designing our circuit.

### Control Signals:
- LI => Loads the negative register and shift registers with their values simultaniously.
- EDD => Enable double dabble process which involves loading registers.
- EShift => Enables shift registers (i.e. causes them to shift a single bit L/R).
- PSel => if its a zero register P is reset else its given the value of P + SHL_Register.
- LP => a load signal that determines whether or not a value is loaded to register P.
- DS => display signal that determines which digits are displayed on the 7 seg. It choses between 4 states: Display only dashes, display rightmost digits, display center digits, display leftmost digits.

### Black boxes:
- Double dabble => it's a function that converts a binary value into its BCD equivlant. In our case it converts 14 bits into 5x4bit BCD thats then passed on to the display function. DDready is passed to the control unit in order to allow for the CU to know when the double dabble algorithim is done.
- Display => function that chooses which BCD digits to display based on the control signal DS. In our case it chooses 3x4bit BCD from the total 5x4bit BCD provided from the double dabble. It will output 12'b1 if ds is in dash state else it will output the BCD values to be displayed. 
- 7 segment function => takes the BCD digits provided by the Display and displays them on the three rightmost 7 segment displays on the FPGA, and takes the output of the Neg Reg, which contains information about whether or not the product is negative or not, and displays a negative sign on the leftmost 7 segment display if it is negative, nothing if not.
