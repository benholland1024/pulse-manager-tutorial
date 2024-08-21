<h1 align="center"> 🫀 Pulse Manager Tutorial</h1>

<h4 align="center">A description of how to recreate the hardware needed to use the <a href="https://github.com/benholland1024/pulse-manager">pulse-manager</a> software.</h4>

<hr/>

<h2>Contents</h2>

 1. Required tools and supplies
 2. The cardiovascular model
    - Print the heart + case
    - Assemble compliance chamber
    - Assemble tubing and sensors
 3. The air pump
    - Create inflatable pockets
    - Attach tubing to valves and air source
 4. The Raspberry Pi controller
    - Print case for RPi screen
    - Set up RPi with a keyboard and mouse
    - Circuitry
    - Set up the pulse-manager software
 5. Testing

<hr/>

<h2>Required tools and supplies</h2>

The following tools were used:
 - <a href="https://store.anycubic.com/products/photon-mono-m5s?srsltid=AfmBOoo6R4wCbVnCGKRZ7tQgiQt0xwVnhSDFUFg9_NGr83IOjvOBaMKt">Anycubic Photon Mono M5s</a>
 - <a href="https://www.solidworks.com/">SolidWorks software</a>, provided by the University of Akron, running on a Windows computer.
 - <a href="https://www.amazon.com/dp/B0067FFW6E">Dental vacuum former</a>
 - <a href="https://www.amazon.com/dp/B075L6K1KM">Heat press</a>

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
<h2></h2>
