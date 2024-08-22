<h1 align="center"> 🫀 Pulse Manager Tutorial</h1>

<h4 align="center">A description of how to recreate the hardware needed to use the <a href="https://github.com/benholland1024/pulse-manager">pulse-manager</a> software.</h4>

<br/><hr/><br/>

<h2>Contents</h2>

 1. <a href="#supplies">**Required tools and supplies**</a>
 2. **The cardiovascular model**
    - 2.1. Print the heart + case
    - 2.2. Assemble compliance chamber
    - 2.3. Assemble tubing and sensors
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

The following supplies were used:
 - Resins:
   - <a href="https://store.anycubic.com/products/high-speed-resin?srsltid=AfmBOooOMM5i6VAxBmYBslaz3VqEcGTLrc5fxPaAbTTxGhNPXFPJ3_7-">Anycubic high speed resin</a>
   - <a href="https://www.amazon.com/dp/B08RWMMVCH">Superflex 80A printing resin</a>
   - <a href="https://www.amazon.com/dp/B08GJTGPYQ">Siraya Tech high-temp resin</a>
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
   - <a href="https://www.amazon.com/dp/B0006O1ICE">JB weld adhesive</a>
   - A jar for the compliance chamber

While testing the system, the following was used:
 - Bread boards
 - Pin wires
 - LEDs
 - A multimeter


<br/><hr/><br/>

<h2 id="supplies">2. The cardiovascular model</h2>
<h3 id="print-the-heart"> 2.1. Print the heart + case</h3>

The heart structure must have the following traits:
 - It should be flexible, so it can be compressed to simulate systole.
 - It should have two openings, which can make watertight connections with the tubing. Barbs were used for this. Our tubing was 1.25" in O.D.
 - Optionally, it may have a smaller opening to accomodate the endoscopic camera. This also must be watertight when the camera is inserted. 
 - It should have a volume that approximates the volume of the left ventricle at diastole (~100mL). The volume of a cone was used to roughly estimate this.

The flexible heart structure was modeled in Solidworks. The model is available for download [here](https://github.com/benholland1024/pulse-manager-tutorial/blob/main/heartStruct25mm.SLDPRT). The steps to create the model were:
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



<h3 id="compliance-chamber"> 2.2. Assemble compliance chamber</h3>
<h3 id="tubing-and-sensors"> 2.3. Assemble tubing and sensors</h3>













