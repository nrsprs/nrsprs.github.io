+++
title = "DirtBot"
weight = 1
+++

![DirtBot Iso w/ Labels](/images/dirtbot/dirtbot_labels.png)

*DirtBot Isometric Technical Diagram*

Dirtbot is my bachelor's senior design capstone project, a system aimed at removing the time consuming manual labor from the seed sowing process by automating the creation of filled seed plug trays.

### Project Overview:

The project was a short 15 weeks before graduation, on a limited budget, with 3 team members (most were groups of 5, we got unlucky). My team's job was to take a set of design requirements, create a design, and build a prototype that implemented our design.

DirtBot uses a two stage dispensing assembly: a hopper deposits a portion of the of the soil mass to the auger, which dispenses it into each plug tray. The auger moves on the Y-Axis while the tray moves on the X-Axis. 

The class was to write a comprehensive paper on the engineering analysis, design tools, and testing performed to prove that our attempted solution was a comprehensive answer to the problem. At the end of the semester, we had an open-floor demo day showing off our prototypes and a poster detailing how it works.

![Presentation Poster](/images/dirtbot/DirtBot%20Presentation%20Poster.png)
*Team DirtBot's poster - Poster Design by me, DirtBot graphic logo by Madi Lachut*

My role as the software and electrical engineer on the project was to create the software architecture, wiring layout, program and test each mechanism, and assemble the electrical hardware.

The base concept is a "seed plug tray filling machine," but we renamed the project to DirtBot in spirit of the naming scheme used in RIT's robotics club of a name with "bot" appended, like CatBot, or CouchBot.

Our design is inspired by the two axis motion gantry system of 3D printers, which enables a dispensing tool head to release material onto any position in a known coordinate space. Instead of dispensing molten plastic, DirtBot dispenses dirt (and could dispense seeds, but didn't). 

The project is developed for Arduino AVR systems, the source code is on my github [[HERE]](https://github.com/nrsprs/dirtbot).

### Software Overview:

![Class Diagram](/images/dirtbot/class_diagram.png)

The software is a really straightforward state machine that runs a startup sequence, fetches some user data from the HMI, and then the runtime routine.

Subsystem Function Breakdown:
* Interface (HMI):
    * Start sequence
    * End sequence
    * Interrupts / E-Stop
    * Program configuration
* Motion Control:
    * Encoder position tracking
    * Limit switch debounce
    * Subsystems:
        * Auger
        * Hopper
        * X-Axis
        * Y-Axis

These systems have a lot of header files, as I made the entre project in a very object-oriented approach with each header file working as a method for an object that is represented by a hardware component. The auger has the function runAuger(), for which the respective stepper and encoder instances are sent to. 

The stepper, encoder, or switch objects don't do anything themselves, but are used to call cleaner, more unit-testable functions. This made it very easy to have only one portion of DirtBot working at a time, write one subsystem, assemble and test it, and not have to worry about anything else. 

There is a huge benefit to doing this because it enables complexity that most of my peers's capstone projects cannot have (due to software limitations). DirtBot is just programed to move to a position in a 2D coordinate space and iterate for each position. If there were a requirement to, let's say read and execute g-code, I could easily write an interpreter and functions to execute common g-code commands, such as G0-4 or G6, which could be written as functions that accept stepper & encoder objects as parameters. This modularity is a serious benefit.

![HMI](/images/dirtbot/hmi.png)
*The DirtBot human machine interface with a push button encoder knob and 32 character backlit LCD*

Ardunio is a pretty easy microcontroller to develop on, though there is a difficulty to development because there is no port passthrough that enables debugging, so you have to manually debug using print statements to serial or by visualizing outputs in hardware, like a LCD display.

Despite the debugging and lack of built-in tests, programming using the PlatformIO extension on VSCode worked really well. I could build and flash using Code, then view the output in the serial monitor extension. 

### Hardware Overview:

![Complete assembly](/images/dirtbot/complete_assy.jpg)
*Complete DirtBot assembly the night before presentations*

DirtBot uses an Ardunio MEGA and 4 stepper motors, DM320T stepper drivers, and a 32 char backlit LCD display. The frame is extruded aluminum and most of the designed parts are printed.

The parts are designed in Fusion 360 and printed on Prusa Mk4 and Elegoo Neptune 3 printers.

![Carrier assembly](/images/dirtbot/carrier.png)
*Carrier Assembly*
