<h1 align="center"> 🫀 Pulse Manager Tutorial</h1>

<h4 align="center">A description of how to recreate the hardware needed to use the <a href="https://github.com/benholland1024/pulse-manager">pulse-manager</a> software.</h4>

<br/><hr/><br/>

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/overview_diagram.png?raw=true" />

<h2>Contents</h2>

 1. <a href="#supplies">**Required tools and supplies**</a>
 2. <a href="#cardiovascular-model">**The cardiovascular model**</a>
    - 2.1. Print the heart
    - 2.2. Print the heart casing
    - 2.3. Assemble compliance chamber
    - 2.4. Assemble tubing and sensors
 3. [**The air pump**](#air-pump)
    - 3.1. Create inflatable pockets
    - 3.2. Attach tubing to valves and air source
 4. [**The Raspberry Pi controller**](#rpi)
    - 4.1. Print case for RPi screen
    - 4.2. Set up RPi with a keyboard and mouse
    - 4.3. Set up the pulse-manager software
    - 4.4. Circuitry
 5. [**Testing**](#testing)
    - 5.1. Testing the screen interface

<br/><hr/><br/>

<h2 id="supplies">1. Required tools and supplies</h2>

The following tools were used:
 - An [Anycubic Photon Mono M5s](https://store.anycubic.com/products/photon-mono-m5s?srsltid=AfmBOoo6R4wCbVnCGKRZ7tQgiQt0xwVnhSDFUFg9_NGr83IOjvOBaMKt) 3d printer, and the slicer software
 - The [SolidWorks software](https://www.solidworks.com/), provided by the University of Akron, running on a Windows computer
 - A <a href="https://www.amazon.com/dp/B0067FFW6E">dental vacuum former</a>
 - A <a href="https://www.amazon.com/dp/B075L6K1KM">heat press</a>
 - A <a href="https://www.amazon.com/dp/B07RZV2DW8">soldering iron</a>
 - A <a href="https://www.amazon.com/dp/B07PPRDBM5">step drill bit</a> that goes up to 1.375 inch at least
 - A <a href="https://www.homedepot.com/p/310230031">drill press</a>
   - _Provided to us by the University of Akron. This must be big enough to fit the compliance chamber, ~13cm, plus the step bit_

The following supplies were used:
 - 3d printing supplies:
   - <a href="https://store.anycubic.com/products/high-speed-resin">Anycubic high speed resin</a>
   - <a href="https://www.amazon.com/dp/B08RWMMVCH">Superflex 80A printing resin</a>
   - <a href="https://www.amazon.com/dp/B08GJTGPYQ">Siraya Tech high-temp resin</a>
   - Isopropyl alcohol to clean the prints.
 - Electronics: 
   - An <a href="https://www.amazon.com/dp/B07PBF6DX5/">Endoscopic camera</a> (optional)
   - USB-c converter for RPi for camera (optional)
   - A <a href="https://www.amazon.com/dp/B0899VXM8F">Raspberry Pi</a> and its <a href="https://www.amazon.com/dp/B07TYQRXTK"> power supply</a>
   - A [microusb to HDMI socket](https://www.amazon.com/dp/B09LYPXPH6) converter, if using HDMI and a RPI 4 or 5
   - A [microsd card](https://www.amazon.com/dp/B0B7NXBM6P) for RPi memory.
   - A <a href="https://www.amazon.com/dp/B00GFAN498">Wifi USB dongle</a>for the Raspberry Pi (or ethernet)
   - A <a href="https://www.raspberrypi.com/products/raspberry-pi-touch-display/">touchscreen for the RPi</a>
     - _Or, a keyboard mouse and screen, if preferred._
   - An <a href="https://www.amazon.com/dp/B00NAY3RB2">analog to digital converter</a> circuit component
   - Three <a href="https://www.digikey.com/en/products/detail/sensata-crydom/CMX60D10/221843">Crydom</a> relays (CMX60D10)
   - Three <a href="https://www.mcmaster.com/2555N12/">solenoid valves</a> (Clippard, EV-P-10-25-A0-v)
   - A <a href="https://www.amazon.com/dp/B07QNN2GRV">flow meter</a> (Digiten)
   - Three <a href="https://www.digikey.com/en/products/detail/nxp-usa-inc./MPVZ5004GW7U/1168374">pressure sensors (MPVZ5004GW7U)</a>
   - A custom PCB from JCLPCB
   - A <a href="https://www.amazon.com/dp/B0852HX9HV/">12 volt power supply and its wire adapter</a>

   - Some <a href="https://www.amazon.com/dp/B01N0VNNKO">solder</a>
 - Tubing:
   - 10 ft of <a href="https://www.mcmaster.com/5233K72/">1 inch I.D. PVC tubing</a>
   - 10 ft of <a href="https://www.mcmaster.com/5233K56/">1/4 inch I.D. PVC tubing</a>
     - _to connect to the <a href="https://www.grainger.com/product/55NW90">pressurized air spigot</a> on our chem hood_
   - 10 ft of <a href="https://www.mcmaster.com/5233K404/">1/8 inch I.D. PVC tubing</a> for air valves + inflatable pockets
   - 10 ft of <a href="https://www.mcmaster.com/5233K415/">5mm I.D. PVC tubing</a> for connecting pressure sensors.
     - _We used some tubing we had, which I measure as about 5mm I.D. - it stretches over the pressure sensor, which is made for 5.59mm_
 - Tubing reducers:
   - 1 <a href="https://www.amazon.com/dp/B08JCCP63D">1/4 to 1/8 barbed tube reducer</a> for air supply
   - 3 5mm to 1/8 inch barbed tube reducer (this must be modelled + printed)
 - Other tubing connectors:
   - 2 <a href="https://www.mcmaster.com/5372K377/">1 inch elbow connectors</a>
   - 5ish <a href="https://www.mcmaster.com/5372K627/">1 inch T connectors</a>
   - 5 <a href="https://www.amazon.com/dp/B08JCS1W24">1/8 inch T connectors</a>
   - 6 <a href="https://www.mcmaster.com/5117K83/">1/8 inch barb to 10-32 threaded connectors</a> for air valves
   - 1 1 inch to 1 inch thread adapter (like <a href="https://www.amazon.com/dp/B0BQGJCCRP">this</a> but with 1" on both ends - I found it at home depot).
     - This is optional! Used with a <a href="https://www.amazon.com/Spears-PVC-THREADED-CAPS-1in/dp/B000VYJ4UC">1 inch plastic pvc cap</a> to make a removable entrance.
 - Inflatable pocket material
   - 80A shore polyether film, 0.012 inches in thickness from <a href="https://www.americanpolyfilm.com/polyether-tpu-film">American Polyfilm</a>
   - <a href="https://www.amazon.com/dp/">PVC adhesive</a> (maybe not necessary?)
 - Compliance chamber materials:
   - <a href="https://www.amazon.com/dp/B0006O1ICE">JB weld steel adhesive</a>
   - A disposable mixing dish and disposible brush (or popsicle stick) to apply the adhesive.
   - A <a href="https://www.mcmaster.com/3999T7/">clear jar</a> for the compliance chamber
   - Some <a href="https://www.amazon.com/dp/B0BXWJDBNS/">220 grit sandpaper</a>
 - Misc:
   - Zip ties, to seal the heart structure casing

While testing the system, the following was used:
 - Bread boards
 - Pin wires
 - LEDs
 - A multimeter


<br/><hr/><br/>

<h2 id="cardiovascular-model">2. The cardiovascular model</h2>
<h3 id="print-the-heart"> 2.1. Print the heart</h3>

The heart structure requirements:
 - It should be flexible, so it can be compressed to simulate systole.
 - It should have two openings, which can make watertight connections with the tubing. Barbs were used for this. Our tubing was 1.25" in O.D.
 - Optionally, it may have a smaller opening to accomodate the endoscopic camera. This also must be watertight when the camera is inserted. 
 - It should have a volume that approximates the volume of the left ventricle at diastole (~100mL). The volume of a cone was used to roughly estimate this.

The flexible heart Solidworks file is available for download [here](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/heartStruct25mm.SLDPRT) and the STL [here](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/heartStruct25mm.STL). The steps to create the model in Solidworks are:
 1. Sketch a cross section of half the heart structure wall (excluding the openings) with the desired volume. <img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/images/HeartStruct_step1_sketch.png?raw=true" width="150px">
 2. Use the "revolve boss/base" tool around the y axis.
 3. Create a new reference plane from the "Top" plane, near where the holes will be made.
 4. Create another reference plane rotated about 30deg, which will be the angle of the holes.
 5. Sketch the outer diameter of the holes, I used 37.55mm. Extrude boss/base that sketch so it sticks out about 20mm.
 6. Sketch the inner diamter of the holes, 32.25mm (.5mm bigger than 1.25"). Make an extruded cut to create the holes.
 7. Create a plane perpendicular to the one last created.
 8. Switch the view to "hidden lines visible" and sketch a cross section of one of the barbs, which should be 0.5mm by 4mm.
 9. Create a different sketch on the same plane, and draw a line through the center of the cylinder.
 10. Revolve the barb around the center line to create one barb.
 11. Use linear pattern to create 3 more barbs, evenly spaced.
 12. Repeat steps 4-11 to create a second hole (or use the "mirror pattern" tool).

Save this file as a .STL, and import it into the AnyCubic Slicer software. 

Position it in the center of the print bed, on its side, with the holes facing the top and bottom. This minimizes the risk of suction cupping. 

Add supports using the "support only on platform" button. 

Click the "slice" button. Save the slice file to a flash drive to generate a .pm5 slice file. Print the model with <a href="https://www.amazon.com/dp/B08RWMMVCH">Superflex 80A printing resin</a>.

<br/>

<h3 id="print-the-casing"> 2.1. Print the heart casing</h3>

The heart structure casing requirements:
 - It should fit around the shape of the heart structure, with space for the uninflated inflatable pockets.
 - It should be rigid, so that the inflatable pockets inflate inward, squeezing the heart
 - It should have holes for the tubing of the inflatable pockets.
 - Optionally, it may have a hole for the endoscopic camera.
 - It should be printed in two halves which can be adhered together around the heart.

Below is a picture of the heart structure in the heart casing, with the inflatable pockets, to make the goal more clear. The heart casing halves are the blue solid structures:

<img src="https://github.com/user-attachments/assets/43e9324f-ac47-42d2-9388-1d2985f69682" width="150px">


The Solidworks and STL files for the heart casing halves are available here: 
[half1.sldprt](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/PocketFrameHalf1.SLDPRT),
[half1.stl](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/PocketFrameHalf1.STL)
[half2.sldprt](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/PocketFrameHalf2.SLDPRT)
[half2.stl](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/PocketFrameHalf2.STL)
They were made using similar methods to the heart structure model. The differences are:
 - The case halves are larger, which affects the first sketch and the sizes of the holes.
 - The case halves are halved, of course. This can be done by only rotating the initial sketch 180deg. 
 - They have holes for the inflatable pockets, made via vertical extruded cuts, repeated via the radial pattern tool. 
 - Optionally, they have holes for the endoscopic camera. 
 - Optionally, they have snap-fit joints to adhere the two halves. I couldn't get these to work, and used zip ties instead. 

Export these files, add supports in the slicer, and save it. Print these with <a href="https://store.anycubic.com/products/high-speed-resin">Anycubic high speed resin</a>, OR using <a href="https://www.amazon.com/dp/B0C8NTLYKB">Anycubic high clear resin</a> if you want to see the liquid inside the frame. The high clear resin is harder to print with, requiring ~8 seconds per layer.

<br/>

<h3 id="compliance-chamber"> 2.3. Assemble compliance chamber</h3>

The compliance chamber requirements:
 - It must be a clear chamber, so the water level can be determined.
 - It must have two holes, each with an airtight connection to the large tubing.
 - It must be both air and water tight, both at the holes and at the top opening.

Two connectors must be printed - see the files [ComplianceConnector.sldprt](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/ComplianceConnector_25mm.SLDPRT) and [ComplianceConnector.stl](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/ComplianceConnector_25mm.STL).  These act as gaskets.  The inner diameter of these is 31.8mm, with 0.5mm barbs, to fit the 1.25 inch (31.75mm) tubing. The outer diameter is 34.94mm, to fit into the hole we'll drill, which will be 1.375 inches (34.925mm) in diameter. Also note that the flat surface is curved to fit around the radius of the clear jar, which is 125mm in diameter. 

Print two of these using the [high speed resin](https://store.anycubic.com/products/high-speed-resin). Once printed, ensure they can snugly hold the tubing. 

Use the step drill bit to drill two 1.375 inch holes into the [clear jar](https://www.mcmaster.com/3999T7/), on opposite sides, about halfway up. 

Insert the connectors into the holes, making sure they fit snugly against the side of the jar. 

Use the 220 grit sandpaper to smooth the jar around both holes, where the connector will be placed. Then, use 220 grit sandpaper to smooth the connector, on the surface that will touch the jar. Make sure these surfaces are smooth. Then clean these surfaces with isopropyl alcohol and water, and let them dry.

Using gloves, a disposable dish, and a popsicle stick (or some disposable brush), mix the [JB Weld Steel Adhesive](https://www.amazon.com/dp/B0006O1ICE) properly and paint a semi-thick coat evenly on the connectors, where they'll meet the jar. 

Balance the jar on one of the connectors, and place something heavy on the other connector, to let the adhesive cure. Below is a picture of the compliance chamber curing. 

<img src="https://github.com/user-attachments/assets/1b4718a3-4490-4195-ad99-3645737ce645" width="150px">


Leave the compliance chamber like this for 24 hours. Then, check to make sure the chamber is waterproof. 

<br/>

<h3 id="tubing-and-sensors"> 2.4. Assemble tubing and sensors</h3>

The tubing assembly requirements:
 - Tubing must connect the heart structure and compliance chamber, in a loop.
 - Artificial aortic and mitral valves must be placed in the appropriate places.
 - 3 pressure sensors must be placed in the appropriate places.
 - A flow sensor must be placed in the appropriate place.
 - The entire cardiovascular loop must be watertight.
 - The tension from the tubing must not damage the heart structure!

The appropriate places for the valves and sensors can be seen on the diagram below, from [this paper by Rodriguez](https://www.semanticscholar.org/paper/Redesign-and-performance-evaluation-of-a-cardiac-Rodriguez/98711b67d424e339e281634dccae912807a91a78).

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/images/Rodriguez_pulseDuplicatorDiagram.png?raw=true" width="150px" />

The complete set up uses 1" I.D. tubing, 90 degree connectors, T connectors, 3d printed reducer connectors, smaller tubing, the pressure sensors, and the flow rate sensor. A picture of the set up is shown below. 

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/cardiovascular-model/images/PulseDuplicatorSetup.jpg?raw=true" width="150px" />

<br/><hr/><br/>

<h2 id="air-pump">3. The air pump</h2>

<h3 id="inflatable-pockets"> 3.1. Create inflatable pockets</h3>

The infatable pocket requirements:
 - These must be hollow, inflatable, and airtight.
 - These must be in a shape compatible with the heart structure.
 - These must have tubes connected to them, for inflation.

The idea for inflatable pockets was taken directly from [this paper](https://www.science.org/doi/full/10.1126/scirobotics.ade2184) by Goswami. 

First, two negative mold halves must be modeled and printed. Here are some general steps for modeling these in Solidworks:
 1. Start by modeling the pocket shape.
    - The pocket should wrap 80 degrees around the heart structure, and the inner face should press the structure inward. Reference pictures can be found in Dr. Goswami's paper.
    - Sketch a cross section of the pocket and revolve boss/base it 80 degrees.
    - This file is available here: [inflatable_pockets.sldprt](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/inflatable_pockets.SLDPRT). There's no need to print this.
 2. Create a new assembly from the inflatable pocket model.
 3. In that assembly, create two new parts, both rectangular prisms. These will be the mold halves, and should be of dimensions that cover the inflatable pocket model.
    - Use mates to push the two halves together, and position them on top of the pocket model.
    - Edit one of the halves in the assembly (right click on it, click "edit part").
    - On the top bar, click "Insert → Features → Cavity". Click the intersecting pocket part. Adjust the parts if needed.
    - Repeat this procedure on the second half.
 4. Save the two negative parts. You can find these files here:
[negative1.sldprt](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/inflatable_pockets_negative1.SLDPRT)
[negative1.stl](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/inflatable_pockets_negative1.STL)
[negative2.sldprt](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/inflatable_pockets_negative2.SLDPRT)
[negative2.stl](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/inflatable_pockets_negative2.STL)
    - The [assembly file](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/mould_maker.SLDASM) is also available if you're curious.
 5. **NOTE:** I forgot to add some small air holes in these molds! You should edit these parts to do that, so the vacuum former will work better. I added these holes with a drill afterwards, which cracked the molds and required using resin to fix.
   
Print the two negative mold STLs using <a href="https://www.amazon.com/dp/B08GJTGPYQ">Siraya Tech high-temp resin</a>. This resin is hard to print with -- if you're printing at room temperature, print with 90 seconds per bottom layer, 6 bottom layers, and 18 seconds per regular layer. 

Once you have the two negative molds, get the 80A polyethylene film from <a href="https://www.americanpolyfilm.com/polyether-tpu-film">American Polyfilm</a> and cut squares that are the right size for the <a href="https://www.amazon.com/dp/B0067FFW6E">dental vacuum former</a>.  Place the first mold in the former, load the film (I used 2 sheets at once), heat it for ~2 minutes, then switch to the vacuum to create the shape of half a pocket. **NOTE**: This is where the holes in the molds matter. Carefully extract the pocket half, removing the ball bearings. Repeat that procedure with the other negative mold.

You should now have two halves of a pocket. Put these halves back in the molds and push them together. Cut off any excess film -- this film will melt if it touches the heat press, causing toxic fumes and a mess of melted plastic. Place the two molds into the <a href="https://www.amazon.com/dp/B075L6K1KM">heat press</a> and heat it to 160 degrees C. Sandwich the heat press, and leave it there for 15 minutes or so before turning the heat press off. Once cool, take out the pocket, and check whether it's airtight. 

Finally, cut a length of 1/8" I.D. tubing (5-10cm). Cut a hole in the convex side of the pocket and insert the tube, ensuring it's positioned correctly to fit in the heart structure casing. Glue the tube in place -- I first used <a href="https://www.amazon.com/dp/">PVC adhesive</a>, and once dry, painted some of the <a href="https://www.amazon.com/dp/B08RWMMVCH">Superflex 80A printing resin</a> onto the pockets and cured them. I'm not sure if the PVC adhesive is necessary.

Blow into the tubing to check if the pockets are airtight. Getting these airtight was hard and seemed to require a bit of luck, and several rounds of the Superflex resin.

Create 4 pockets this way. The same 2 negative mold halves can be reused, of course. 

The final product is pictured below, placed in the heart structure casing.

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/images/pockets.jpg?raw=true" width="150px" />

<br/>

<h3 id="air-source"> 3.2. Attach tubing to valves and air source</h3>

The picture below shows the set up for the air tubing. _(This picture shows an earlier version of the heart structure casing -- ignore that.)_ 

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/air-pump/images/airflow.jpg?raw=true" width="150px" />

Note that the black tubing shown in the bottom attaches to a source of compressed air. 

Also note that two of the air valves release the air to the atmosphere. This prevents pressure build up, which can disconnect the tubing. 

<br/><hr/><br/>

<h2 id="rpi">4. The Raspberry Pi controller</h2>

<h3 id="rpi-case"> 4.1. Print case for RPi screen</h3>

In retrospect, I'm not sure if the <a href="https://www.raspberrypi.com/products/raspberry-pi-touch-display/">touchscreen</a> was the best choice. It could be replaced with a monitor, keyboard and mouse for easier control and a larger screen - although it would then take up more space. 

If you're using the touch screen, you should print a display case. I found basic models [here](https://www.printables.com/model/18153-raspberry-pi-7-inch-touchscreen-display-case/files), and also used [this deep version](https://www.printables.com/model/151799-raspberry-pi-deep-7-inch-touchscreen-display-case) of the case. 

Ultimately, I plan to create a custom case based on the ones above, that can accomodate the added sensors.  My plan is shown in the image below.

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/rpi/images/case_plans.jpg?raw=true" width="150px" />

<br/>

<h3 id="rpi-setup"> 4.2. Set up RPi with a keyboard and mouse</h3>

Get the microsd card and plug it into a computer (not the RPi, yet). [Install the Raspberry Pi OS](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up/2) onto the SD card. 

Now plug the SD card into the RPi. Plug the RPi into power. Follow the instructions to plug in the touchscreen, and/or use HDMI to display the RPi on a screen, and connect a mouse and keyboard. 

The computer should boot up! If you're using the touchscreen, the screen is likely upside down compared to what you want -- click the RPi menu icon, then "Preferences → Screen Configuration". Right click the touch screen and click "Orientation → Inverted", then click "apply" and "ok". 

Next I like to go to "Preferences → Appearance Settings", then the "Taskbar" tab, and make the position on the bottom. You can set the taskbar "location" here too, if using two screens. Then in the System tab, I set the theme to dark. 

The keyboard may need configured to US instead of British (or else you may get a £ when you want a $, among other issues.) Open a command line and type `sudo raspi-config`.  In "localisation options", update both the keyboard and timezone. This info came from [here](https://forums.raspberrypi.com/viewtopic.php?t=69752). The displayed clock still might not work, which is acceptable to me. 

You must enable SPI as well. Enter `sudo raspi-config`, go to "Interface Options", "SPI", then hit "Yes" to enable.

You'll need to connect to wifi, using the wifi usb dongle (or ethernet). If you're a U of Akron student, there's a guide to connecting to Eduroam on Linux [here](https://www.uakron.edu/it/connecting-to-the-network.dot). 

<br/>

<h3 id="software"> 4.3. Set up the pulse-manager software</h3>

Now we can install the software. Open up a command line. You'll need the `git` command, which should be installed. Enter `git -v` to make sure you don't get an error. Install the [pulse-manager repo](https://github.com/benholland1024/pulse-manager) wherever you'd like.  These commands are what I use:

```bash
mkdir github
cd github/
git clone https://github.com/benholland1024/pulse-manager.git
cd pulse-manager/
```

The software uses Python, so make sure you have that installed by running `python -version` and ensuring there's no error.  
Python needs some packages installed. Install them by running: 

```bash
sudo pip install -r requirements.txt --break-system-packages
```

To edit the software, open the main menu, then click "Programming → Geany". On the top menu bar, click "Project → New...". Enter the following, replacing "benholland" with your username:

| Prompt     | What to write                          |
|------------|----------------------------------------|
| Name:      | pulse-manager                          |
| Filename:  | /home/benholland/pulse-manager         |
| Base path: | /home/benholland/github/pulse-manager/ |

Click "create". Now click "Tools → Plugin Manager", check "File Browser", and click "close". Now at the top of the panel on the left, click the right arrow button until the word "Files" is highlighted -- you should see all the files in the project! 

Click "Document → Indent Type → Spaces" and "Document → Indent Width → 2". 

_(I know this set up is a pain but you only have to do it once, and Geany is pretty good otherwise.)_

In the bottom panel of Geany, click the down arrow until it says "terminal".  Type "pwd" to make sure you're in the `pulse-duplicator` project folder. (Navigate there using `cd` if not). 

Now, you should be able to run the app! Try this: 

```bash
python app.py
```

If you get an [error about edge detection](), you may need to run these two commands:
```bash
sudo apt remove python3-rpi.gpio
sudo apt install python3-rpi-lgpio
```
Then try `python app.py` again. 

If the window opens but says "Error: 404", open `app.py` and ensure the line which includes `eel.init(os.path.abspath` has the correct file path for the project. 

<br/>

With the app working, you can make a shortcut to open the app. Create a new file.

```bash
nano ~/Desktop/pulse-manager.sh
```

Now add this text:
```bash
#!/bin/bash
/home/benholland/github/pulse-manager/app.py
```

Save the file (ctrl-x, "y"). Now make it executable:

```bash
chmod +x pulse-manager.sh
```

Now you can double click this file to start the app!

<br/>

<h3 id="circuitry"> 4.4. Circuitry</h3>

The RPi needs to have its pins attached correctly to the sensors and solenoid valves. 

I first did this using breadboards and pin connectors. I recommend using these tools if any modifications are being made.

Once the breadboard system was working, I used the free software [KiCad](https://www.kicad.org/) to create a circuit schematic -- see the first image below.  Then a PCB design was created from that schematic, see the second picture.  

<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/rpi/images/pulse_dup_schematic.png?raw=true" width="150px" />
<img src="https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/rpi/images/pulse_dup_pcb.png?raw=true" width="150px" />

The files for these schematics are available [here](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/assets/rpi/pulse_duplicator_circuit_files.zip).  Download that zip file and extract it.  The files should open in KiCad.

You'll need to order the PCB. I used the company [JLCPCB](https://jlcpcb.com/). In that zip file, there's another zip file called "gerber.zip".  You can upload that to the JLCPCB website to order the pcb.  

Or, if you change the PCB, follow [this](https://jlcpcb.com/help/article/how-to-generate-gerber-and-drill-files-in-kicad-7) to create a new gerber zip file, to be ordered.

<br/><hr/><br/>

<h2 id="testing">5. Testing</h2>

<br/> 

<h3 id="test-the-screen"> 5.1. Testing the screen interface</h3>




<br/><br/><br/><br/>





