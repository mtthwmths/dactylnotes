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
- 
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