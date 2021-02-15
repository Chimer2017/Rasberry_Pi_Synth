# Sounds and Waves

The sound that we hear is nothing more than the reverberation of air in our eardrums. In essence, a wave of input is passed into our ears and then we hear things. Computer audio works along with similar principles. Sounds are constructed from waves of varying shapes and frequencies and amplitudes. The result is a sound that can be layered and filtered with other sounds to create something similar to music. The idea for this project was to get a chance to explore the waves that make the foundational layer of the music. The different shaped waves and how its variables such as amplitude and period affect the final audio output.

# The Project

The project was an exploration of waveform and sound. This took place through both visual and audio output. The project is a device that allows a user to control and vary the shape of a wave and its associated variables. On-screen, the user sees the effects of these manipulations through the varying shape of the wave on the screen.

# How Was It Built?
## Materials:
- ESP-32 Chip
- Raspberry Pi 3B+
- 2 Moment Buttons
- 1 Switch
- 1 LED Light
- 1 Analog Joystick

Several resistors ( for wiring up buttons) 
## Hardware

The hardware side was focused on building out the correct circuit to be able to process user inputs on the joystick, moment buttons, and switch. Everything in the circuit was independently wired. There are no connections in the series. The exact method of wiring was taken from the ESP-32 tutorial.

## Software

Once everything was wired up, it was time to begin processing the input from the hardware. It was first important to see if all the hardware was providing reliable information. This was checked the observing the serial monitor available in the Arduino IDE. Once inputs from the hardware were validated, the software could be built around the input stream.

First, the input stream was cleaned and trimmed of whitespace and leading characters. The inputs were split and associated with their respective input mechanism, whether that be a joystick or a moment button. Except for the joystick, the values from the input methods are either 1 or 0. A "1" represents its inert or default state while a "0" represents the activity or dynamic state. The joystick however provides 3 different input streams. There is analog data from the x and y axis movement of the button as well as z-axis pressing of the button. The x and y-axis data range from 0 to 4095 while the z-axis data acts like a button, either 0 or 1 based on if the joystick is being pressed or not. 

Once all the inputs were processed and stored, it was possible to connect them as triggers for events in the software. I decided to use Processing for Pi. In processing, there is an infinite loop where the majority of the code goes. In this section, I placed several event listeners for each input method. For example, if the first button is pressed, then turn on the LED. This type of programming paradigm was used to complete this project. 

The specifics for the software are as follow.  There is an animation function that draws the respective wave on-screen with default amplitude and frequency. Movment of the joystick up or down directly affects the amplitude. Movement of the joystick left or right will affect the period of the wave. Pressing down on the joystick or the yellow moment button will alter the density of the wave on the screen. The switch and green moment buttons are used to change between different wave shapes. There are a total of 3 different states with respective waves: sine wave, square wave, and sawtooth wave. The green moment button is also used for adding a momentary triangle wave burst as a fun addition while performing.



## Enclosure

After everything was wired up and ready to go, it was time to put the device into an enclosure that would allow for safe and consistent use. I also wanted something fun and bright. I found an untouched converse shoe box, It was bright orange and had cutouts on the sides the fit the wires perfectly. There was plenty of space in the box to fit both the Raspberry Pi and the ESP-32 with a breadboard. 

I cut some holes for the button and joysticks. 

  

## Challenges

There were a number of challenges. The first major challenge was being able to switch between 3 states with only a binary switch. This was solved by adding in the required input from the green button when pressing the switch to get to state 3. Otherwise, the switch goes between state 1 ad state 2.

The other challenge was figuring out how to animate square and sawtooth waves. While sine waves are supported as math functions in processing, I had to do a bit of research on creating accurate math functions to depict square and sawtooth waves.

The last obstacle was audio. My project had a visual and audio component. During prototyping, I used my laptop instead of the Rasberry Pi. My laptop has built-in speakers. Then, on Sunday, with everything complete and ready to transfer to the Rasberry Pi, I realized the Pi has no built-in speakers. The easy solution would be to purchase USB speakers and connect them to the PI. However, there was not enough time for that, so for the performance, I had to bypass the Pi and use my laptop as the processor. I also included a video of the performance with the Pi but no sound.



