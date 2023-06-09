# Electronics Learning Notes
- MIT intro to compsci and EE:
	- https://ocw.mit.edu/courses/6-01sc-introduction-to-electrical-engineering-and-computer-science-i-spring-2011/pages/syllabus/
- good instructional site with videos and write-ups.
	- https://theengineeringmindset.com/
	
# Keyboard Notes
## IO expander
- I have a MCP23018 from the first round of Dactyl attempts
- has two GPIO ports (GPIOA, GPIOB) that each have 8 IO pads
    - in the original Ergodox, A is columns and B is rows
    - TODO: is A listening or is B listening? 
    - my keyboard has diodes on the "rows" so the column has to be driven high. I think this means the Rows are to be "listened to" since they are going to be low until the current comes through from the column.
- this means B is inputs and A is outputs
- output pads are open-drain, basically means the pad value can be driven to ground or left floating
    - TODO: wait, what?
- does the MCP23018 require a 2.2k ohm resistor from the SCL/SDA to VCC?
	- taken from the robot-electronics article:
		- This is just two wires, called SCL and SDA. 
		- SCL is the clock line. 
			- It is used to synchronize all data transfers over the I2C bus. 
		- SDA is the data line. 
		- The SCL & SDA lines are connected to all devices on the I2C bus. 
		- There needs to be a third wire which is just the ground or 0 volts. 
		- There may also be a 5volt wire which is how power will be distributed to the devices. 
		- Both SCL and SDA lines are "open drain" drivers. 
			- What this means is that the chip can drive its output low, but it cannot drive it high. 
			- For the line to be able to go high you must provide pull-up resistors to the 5v supply. 
				- There should be a resistor from the SCL line to the 5v line and another from the SDA line to the 5v line. 
				- You only need one set of pull-up resistors for the whole I2C bus, not for each device. 
				- The value of the resistors is not critical. I have seen anything from 1k8 (1800 ohms) to 47k (47000 ohms) used. 
				- 1k8, 4k7 and 10k are common values, but anything in this range should work OK. 
				- I recommend 1k8 as this gives you the best performance. 
				- If the resistors are missing, the SCL and SDA lines will always be low - nearly 0 volts - __and the I2C bus will not work__.
				
### IO expander links
- http://rubensm.com/debugging-mcp23018-on-ergodox-original-keyboard/
    - debugging article about mcp23018 on ergodox
    - has code for debugging on arduino. code in article.
- https://www.etsy.com/shop/TheBigSkree
    - shop for flexy pcbs and keeb stuff. u/alakuu on reddit.
- https://github.com/FREEWING-JP/qmk_firmware/tree/freewing/master_all/keyboards/handwired/freewing/test_expand_io_i2c
    - super basic video about expanding gpio, but simple projects are great for learning something like this...
- https://github.com/makersdigest/T05-MCP23017-GPIO-Expander
    - also a video, but this one more about specifically hooking the 23017 to an arduino.
- https://github.com/adereth/dactyl-keyboard/tree/master/qmk-guide
    - matt adereth is a wizard. He invented the dactyl based on the kinesis and used clojure to do it... it's beyond impressive to me.
- https://joedevivo.com/2017-05-20-building-a-qmk-dactyl
    - how to burn out the teensy's bootloader (same :disappointed: )
- https://www.youtube.com/watch?v=OJSOEStpPIo
	- a great video about using oleds with qmk.
- https://github.com/adereth/dactyl-keyboard/blob/master/guide/README.org#wiring
	- no really, matt adereth is a wizard...
- https://www.reddit.com/r/ErgoMechKeyboards/comments/hlh5to/prototype_keeps_killing_mcp23018/
	- suspect that the capacitor discussion in here will be important
	- also, the mcp in this project is using pull up resistors.
- https://learn.sparkfun.com/tutorials/pull-up-resistors/all
- https://learn.adafruit.com/working-with-i2c-devices/pull-up-resistors
- https://www.pjrc.com/teensy/td_libs_Wire.html
- https://www.build-electronic-circuits.com/pull-up-resistor/
	- default is 10kohm, but it's not that simple
- https://github.com/pierrechevalier83/ferris
	- how about a keyboard that is already using a promicro+mcp23018 setup...
- https://www.robot-electronics.co.uk/i2c-tutorial
	- ferris reccommended i2c article
- https://stackoverflow.com/questions/8438349/what-does-mean-in-c
	- let's talk about bit shifting
- https://en.wikipedia.org/wiki/Bit_field
	- bit shifting 2: electric bitaloo
- https://www.youtube.com/watch?v=fDKUq38H2jk
	- basic bit shifting example if binary isn't your thing. ~5 minutes
- https://github.com/qmk/qmk_firmware/blob/master/docs/reference_info_json.md
	- how config.h rules.mk and info.json work. thanks qmk docs people for the docs.
- https://github.com/qmk/qmk_firmware/blob/master/docs/custom_quantum_functions.md
	- old dactyl firmware had matrix_(init/scan)_quantum() calls, but that's not allowed anymore.
	- changed the code to say 'user' instead of 'quantum'... maybe it works, maybe my house burns down...
- https://deskthority.net/viewtopic.php?f=7&t=8448&start=
	- used this to get the pinout for the pro micro that I used in my firmware. config.h? not sure which file, but I think that's right.

