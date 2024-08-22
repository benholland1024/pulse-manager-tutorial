<h1 align="center"> 🫀 Pulse Manager Tutorial</h1>

<h4 align="center">A description of how to recreate the hardware needed to use the <a href="https://github.com/benholland1024/pulse-manager">pulse-manager</a> software.</h4>

<br/><hr/><br/>

<h2>Contents</h2>

 1. <a href="#supplies">**Required tools and supplies**</a>
 2. <a href="#cardiovascular-model">**The cardiovascular model**</a>
    - 2.1. Print the heart
    - 2.2. Print the heart casing
    - 2.3. Assemble compliance chamber
    - 2.4. Assemble tubing and sensors
 3. **The air pump**
    - 3.1. Create inflatable pockets
    - 3.2. Attach tubing to valves and air source
 4. **The Raspberry Pi controller**
    - 4.1. Print case for RPi screen
    - 4.2. Set up RPi with a keyboard and mouse
    - 4.3. Circuitry
    - 4.4. Set up the pulse-manager software
 5. **Testing**

<br/><hr/><br/>

<h2 id="supplies">1. Required tools and supplies</h2>

The following tools were used:
 - An <a href="https://store.anycubic.com/products/photon-mono-m5s?srsltid=AfmBOoo6R4wCbVnCGKRZ7tQgiQt0xwVnhSDFUFg9_NGr83IOjvOBaMKt">Anycubic Photon Mono M5s</a> 3d printer, and the slicer software
 - The <a href="https://www.solidworks.com/">SolidWorks software</a>, provided by the University of Akron, running on a Windows computer
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
   - An <a href="https://www.amazon.com/dp/B07PBF6DX5/">Endoscopic camera</a>
   - A <a href="https://www.amazon.com/dp/B0899VXM8F">Raspberry Pi</a> and its <a href="https://www.amazon.com/dp/B07TYQRXTK"> power supply</a>
   - A <a href="https://www.raspberrypi.com/products/raspberry-pi-touch-display/">touchscreen for the RPi</a>
     - _Or, a keyboard mouse and screen, if preferred_
   - An <a href="https://www.amazon.com/dp/B00NAY3RB2">analog to digital converter</a> circuit component
   - Three <a href="https://www.digikey.com/en/products/detail/sensata-crydom/CMX60D10/221843">Crydom</a> relays (CMX60D10)
   - Three <a href="https://www.mcmaster.com/2555N12/">solenoid valves</a> (Clippard, EV-P-10-25-A0-v)
   - A <a href="https://www.amazon.com/dp/B07QNN2GRV">flow meter</a> (Digiten)
   - Three <a href="https://www.digikey.com/en/products/detail/nxp-usa-inc./MPVZ5004GW7U/1168374">pressure sensors (MPVZ5004GW7U)</a>
   - A custom PCB from JCLPCB
   - A <a href="https://www.amazon.com/dp/B0852HX9HV/">12 volt power supply and its wire adapter</a>
   - A <a href="https://www.amazon.com/dp/B00GFAN498">Wifi USB dongle</a>for the Raspberry Pi
   - USB-c converter for RPi for camera (maybe not necessary?)
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
   - <a href="https://www.americanpolyfilm.com/polyether-tpu-film">TPU sheets</a>
   - <a href="https://www.amazon.com/dp/">PVC adhesive</a> (maybe not necessary?)
 - Compliance chamber materials:
   - <a href="https://www.amazon.com/dp/B0006O1ICE">JB weld steel adhesive</a>
   - A disposable mixing dish and disposible brush (or popsicle stick) to apply the adhesive.
   - A <a href="https://www.mcmaster.com/3999T7/">clear jar</a> for the compliance chamber
   - Some <a href="https://www.amazon.com/dp/B0BXWJDBNS/">220 grit sandpaper</a>

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
 1. Sketch a cross section of half the heart structure wall (excluding the openings) with the desired volume.
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

Balance the jar on one of the connectors, and place something heavy on the other connector, to let the adhesive cure. Leave the compliance chamber like this for 24 hours. Then, check to make sure the chamber is waterproof. 

<br/>

<h3 id="tubing-and-sensors"> 2.4. Assemble tubing and sensors</h3>

The tubing assembly requirements:
 - Tubing must connect the heart structure and compliance chamber, in a loop.
 - Artificial aortic and mitral valves must be placed in the appropriate places.
 - 3 pressure sensors must be placed in the appropriate places.
 - A flow sensor must be placed in the appropriate place.
 - The entire cardiovascular loop must be watertight.
 - The tension from the tubing must not damage the heart structure!

<br/><hr/><br/>

<h2 id="cardiovascular-model">2. The cardiovascular model</h2>











