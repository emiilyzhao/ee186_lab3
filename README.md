# ee186_lab2

## Getting Ready

**I2C addresses**

accelerometer: 0011001b
magnetometer: 0011110b

**Sub-address**

SUB is the byte sent after the device address, and selects which register
inside the chip is being written / read. This differs from the I2C address, 
which picks which chip on the bus you're talking to. The I2C address is the 
first byte sent after START, whereas SUB is the second one. The address is
fixed in hardware the SUB can be chosen using the register map in the manual.

**CTRL1 register address**

Address: 	0100001 (0x20) <- only 7 bits b/c top bit is auto-increment flag
Written to: 	01010111 (0x57)

CTRL_REG1_A is at address 0x20. 
Writing 0x57 sets ODR = 0101 (100 Hz) and enables the X, Y and Z axes (Zen = Yen = Xen = 1).

**Reading acceleration data from axes**

OUT_X_L_A: 	0101000 (0x28)
OUT_X_H_A:      0101001 (0x29)
OUT_Y_L_A:      0101010 (0x2A)
OUT_Y_H_A:      0101011 (0x2B)

## Writing the Driver 
