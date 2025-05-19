# CCFL2LED

While working with LCD monitors, we noticed that their main issue is the CCFL (Cold Cathode Fluorescent Lamp) backlight. Since replacing these lamps is not cost-effective, we concluded that the best option is to modernize these devices with a new type of backlighting — LED (Light-Emitting Diode) backlight.

# Why is this change so important?

CCFL lamps are extremely harmful to the environment if broken, as they contain mercury, various metals, and plastics. They also have a significantly shorter lifespan and consume more power compared to LED technology (power consumption can be reduced by up to 40%). Controlling CCFLs requires complex electronics to drive an inverter that can generate up to 2kV AC. These circuits can degrade over time, leading to various failures, such as capacitor damage or degradation, which further impacts device operation.

Additionally, over time, CCFLs tend to yellow, giving the display a reddish or pinkish tint. That’s where LED strips come in — they are very easy to use, safer, more reliable, more available, cheaper, and longer-lasting.

# What are the results after the replacement?

The results were truly unexpected. We didn’t anticipate such a significant improvement in image quality — the colors became much more vibrant. There are no dark areas, and the light is evenly distributed across the screen. Efficiency increased, and power consumption was reduced by 30%.

# Plan and idea
The plan is to create an open-source, universal modular board for displays (composed of multiple parts/modules). This board currently combines several modules. For now, this is sufficient for us to recycle and upgrade monitors that arrive for recycling through the project [Поново](https://www.linkedin.com/company/ponovo/).

Here are picture of the working prototype (with the same chip tested on a 19", 22" and 24" display):


![prototip2](Images/prototip2.jpg) 


# About the Board

**Warning: This particular board has not yet been fully tested! It has only been tested using separate modules.**
 * **Power supply:** USB-C PD 12V or 12V 3A barrel jack (center-positive)
 * **LED driver:** PT4115 with parallel current sense resistors, calculated based on the [datasheet](https://www.lcsc.com/datasheet/lcsc_datasheet_1810121830_PowTech-CR-PowTech-Shanghai-PT4115B89E_C84512.pdf)
 * **Buck converter:** AP62201 ([datasheet](https://www.lcsc.com/datasheet/lcsc_datasheet_2308101545_Diodes-Incorporated-AP62201WU-7_C3194236.pdf))
 * **USB Type-C PD controller:** CH224K ([datasheet](https://www.laskakit.cz/user/related_files/ch224ds1.pdf))
<p align="center">
  <img src="pictures/Horizontal.png" width="45%" />
  <img src="pictures/Horizontal2.png" width="45%" />
</p>

# Choosing an LED strip

We recommend using a strip with 120 LEDs per meter. It’s also possible to implement the mod with a 60 LEDs/m strip, but the brightness will be noticeably lower. LED's must be 6500k color.
# Power Supply

A maximum of 36W is required (typically around 30W depending on screen size and number of LEDs). There are two input options, selectable via a switch. The USB-C Power Delivery input uses the CH224K chip configured for a 12V output, so it's crucial to ensure that your adapter supports 12V PD — otherwise, it will not work. The second input is a standard DC jack (5.5mm outer, 2.0mm inner, center-positive) with a 12V power supply.

# LED Driver

One PT4115 driver is used per side (especially important for larger screen sizes). Below is a table showing LED strip power consumption. ![TABLE](pictures/LEDtable.png) 
Also included is a table with required resistor values. ![TABLE](pictures/Rtable.png)
# Buck Converter

There are two options for the buck converter:
* Use a prebuilt LM2596 module and connect it to the board.
* Use the integrated circuit on the board — the AP62201WU-7 chip, which provides 5V for the logic board.
The maximum output power required is up to 8W at 5V.

# Modification
  **Warning: Before starting, make sure to clean the workspace and put on gloves!!!**
  
The steps we will go through in this process are:
* Carefully open the display and separate the backlight and the panel from the electronic boards.
* Continue opening the display and separate the panel from the housing, placing it in a clean area (be extremely careful during this step).
* Remove the diffusers, being careful not to mix up their order.
* Replace the CCFL (cold cathode fluorescent lamps), remove them, measure the appropriate length of LED strips, solder 30-40 cm of wire to them, and install them in place of the CCFL, then test them.
* Reinstall the diffusers and test the LED strips again to check if the diffusers have been properly returned to their place.
* Reinstall the panel (check that it is completely clean) and close that part of the display.
* Connect the LED backlight to the power supply board and link it to the display logic board.
* Test the monitor to check if all functions are working on the On-Screen Display (OSD) menu.
* Close the display and put it into operation.
- - - - 
1. **Carefully open the display and separate the backlight and the panel from the electronic boards.**

   -Be careful with the LVDS cable going to the panel
   
![step1](Images/step1.jpg)

2. **Continue opening the display and separate the panel from the housing, placing it in a clean area (be extremely careful during this step).**

![step2](Images/step2.jpg)

3. **Remove the diffusers, being careful not to mix up their order.**

![step3](Images/step3.jpg)

4. **Replace the CCFL (cold cathode fluorescent lamps), remove them, measure the appropriate length of LED strips, solder 30-40 cm of wire to them, and install them in place of the CCFL, then test them.**

![step4](Images/step4.jpg)
 
 -An example of bad backlighting
![step4_!](Images/step4_!.jpg)

5. **Reinstall the diffusers and test the LED strips again to check if the diffusers have been properly returned to their place.**

![step5](Images/step5.jpg)
  
  -Badly returned diffusers will have lines on the edges which is the case here
  ![step5_1](Images/step5_1.jpg)

6. **Reinstall the panel (check that it is completely clean) and close that part of the display.**

![step6](Images/step6.jpg)

7. **Connect the LED backlight to the power supply board and link it to the logic board of the display.**

-In this picture, the LED strips are not connected (I don't have a picture when they are connected)
![step7_1](Images/step7_1.jpg)

8. **Test the monitor to check if all functions are working on the On-Screen Display (OSD) menu.**

![step8](Images/step8.jpg)

9. **Close the display and put it into operation.**

![step9](Images/step9.jpg)


# Next Steps
  * AC/DC Converter (230V AC to 12V DC)
  * Open-source universal logic board for monitors
