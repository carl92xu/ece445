# Carl Xu - ECE 445 Lab Notebook

## 2/6/2024
### First TA Meeting
We met with our TA for the first time, settled on a weekly TA meeting time for the rest of the project, and signed our lab checkout sheet. We were assigned our locker, and discussed about the class schedules. Then we showed our TA out deaft design plan, including a block diagram, high level requirement, and what we should do first next. 


## 2/13/2024
### Second TA Meeting
We got some feedback for our Proposal:
 - Change one of the high-level requirement to be motion detection
 - Improve block diagram
 - Combine small subsystems
 - Display clock times
 - Overview
 - Exclude component number
 - Tolerance analysis
 - Add more ethics and safety


## 2/20/2024
### Third TA Meeting
 - Discussed our plan for the coming week. 
 - Advice and suggestions on the up coming Design Review.
	 - Use powerpoint to make our presentation clearer.
	 - Include block diagram, high-level requirement, background
	 - Physical design
	 - Cost analysis
	 - Schematics
 - Project Proposal regrade is due this Friday.


## 2/25/2024
### Weekly Group Meeting - Design Review
We met up briefly to discuss how we are going to do tomorrow's presentation, what to put on the slides and what not, and distributed work. After that, we worked on it separately, preparing slides and writing scripts. 


## 2/26/2024
### Design Review Presentation
We prepared powerpoint slides for the presentation, and all prepared our script, so the presentaion went pretty good, and we got some feedback from out TA and our professor. 


## 3/5/2024
### Weekly TA Meeting
This is our last TA meeting before the spring break, we are reminded that we should have components and first-iteration PCBs ordered since it would be the perfect time to wait for them to arrive. We should also probably order multiple versions' of our PCB at the same time, so that we could test them together right after the break, and we could iterate through them faster. 

We also got some feedback from on our Design Document and Design Reivew:

 - How to test our proximity sensor?
 - Block diagram:
    - 5V point from nowhere
    - 3.6V point to nowhere
    -  connect all lines
- Visual aid is too simple, we need more detained graph subsystem
- Add more implementation details, eg. 
	- What regulators we are gonna use? 
	- What sensors we are gonna use? 
	- What types of signals?
	- Where to send the signals 
- List steps user can follow to regenerate the desired outcome
- Add more supporting material, include graph or other stuff to help people understand the design
- Include example or pseudocode for software part
- Include all the datasheets we referred to
- Avoid vague language


## 3/25/2024
### PCB Design
First meeting after the spring break. We discussed how components are going to talk to each other, and started connecting wires in our CAD design. 


## 3/26/2024
### Weekly TA Meeting
 - Office Hour go find Jason for coding/software help 
 - Microchip programming pin - using for inputting code onto the chip 
 - 3-4 weeks left until final demo  


## 4/2/2024
### Weekly TA Meeting & Office Hour
We went to Jason’s office hour, and discussed the feasibility of continuing working with PIC16 microcontroller.

Then we went to our weekly TA meeting,  updated each other with the information we have right now and our plan on going forward, and got some advice on our current situation:

-   Start working on the coding side while waiting for the PCBs to arrive
-   ESP32 transceiver:
	-   dock as host
	-   the others as device
	-   use bluetooth
-   how to go from PIC to ESP32:
	-   ESP put into SPI slave mode
	-   there might be Arduino function to help
	-   SPI works with memory map
	-   google how to program SPI interface


## 4/3/2024
### Microcontroller
We have done some research on our choice of microcontroller, PIC16, and realized that it has to be programmed in Assembly, which none of us are familiar with, and there were little information online. After TAs suggestion, we decided to switch to a more modern and popular chip, ESP32.


## 4/6/2024
### Components Arrived
Most of our components arrived by today, and Nava went ahead to soldier ESP32 chip onto the PCB, but we realized that it is way too small, plus we have no way of testing it. So we decided to purchase ESP32 dev module so that we could test code on breadboards first, and they also have bluetooth and wifi built in, saving us a lot of work connecting new components.

  

## 4/7/2024
### Wi-Fi Connection
We discovered some websites on how to utilize the wifi module on ESP32. We settled on a library called ESP32Now. We can specify the MAC addresses to make them talk them talk to each other. The dock is serving as the hub, and relays messages to each other. We have conducted a lot of testing on it, and made sure that all 3 subsystems can all talk to each other.


## 4/9/2024
### Weekly TA Meeting
Updated our progress to our TA, and got some advice back:
-   Make sure things run on the breadboard first
-   Order things this week
-   Prepare for the mock demo


## 4/10/2024
### Alarm, IR Sensor, and 7-Segment Display
We connected alarm, motion sensor to a ESP32, and wrote code for them separately. We tested their functionality, and they work as intended.

Then we also started working on the 7-segment dimply for our clock, and it was significantly harder, and not a lot of information is available online. We mapped all the pins between ESP32 and the display, and checked that they are correct. Debugged for a few hours and did not make any progress. We are thinking about changing to a different, simpler 7-segment display, but we will debug more tomorrow.


## 4/11/2024
### Debug 7-Segment Display
I continued debugging for the display, while my teammates are working on other stuff. I figured out the problem is that some of the pins on ESP32 is constantly outputting low or high, and that messes up the display. So I connected them to new pins and remapped them in the code, now the display works as intended.


## 4/14/2024
### Test Toothbrush Module
My teammates wrote some code for the accelerometer and assembled the toothbrush module on a breadboard, so we are testing this today. Everything is working as intended. Then we incorporated the wifi transmission code into the toothbrush as well, and now it can communicate with the dock.
  

## 4/15/2024
### Combine Code
We wrote differently functions all separately, even when they are for the same module, so that it is easier for us to test individual functionalities. Now we combine them all together. Since everything runs in the main loop in Arduino environment, it is relatively easy to combine them, we could just stack them together one after another. After that, we did some testing to make sure that they all still work the same.


## 4/16/2024
### Mock Demo
We met up 2 hours before the mock demo to set up everything, and make sure that they still work. Also, we worked a little bit on buttons as we will need it for our dock.

During the mock demo, we show our TA what we have right now, and demonstrated all the functionalities we got to work till this point. He then gave us some advice on how we should proceed:
-   Get everything to work on breadboards
-   Separate 3 modules onto 3 breadboards to be clearer
-   Try to have something on the PCB
-   For Final Presentation:
	-   Print out handouts
	-   Prepare what to present
	-   Introduce ourselves and our project
	-   Challenges we faced
	-   What did we change since design doc


## 4/23/2024
### Finishing Up
My teammates wrote some more logic for our dock since it is our most complicated part and needs a lot of logic to control all 3 parts. It is causing some issues with stuff we had working before. So we stepped through the code, and identified where the issue is. We then wired up the buttons we need for the dock, and programmed for them too to fulfill our high-level requirements.

Me and Eric also did thorough testing to make sure that we hit all the requirements, and everything works as intended, then we took a video of the working breadboard version. While Nava kept working on soldering PCB components, and trying to make it happen.


## 4/24/2024
### Final Demo
40 minutes before the demo, we realized the soldering damaged the ESP32 for the speaker module, as we are re-using parts. We quickly cut it off the PCB, taped the speaker to the ESP32 so that the pins can still touch. We finished fixing it 2 minutes before the demo, and we completed the demo smoothly.


## 4/29/2024
### Final Presentation
We each prepared our slide separately, and got together few ours before our presentation to rehearse and get some final testing data for the presentation.
