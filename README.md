# Tyri_light
This project is about replacing original electronic in Tyri light composed from LEDs 1010 with own LED driver based on XLsemi IC named XL6006 and 20/30W power LED. 
Whole project is designed in [Altium Designer](https://www.altium.com/ "Altium Designer"). Schematic and pcb is in folder [hw](https://github.com/Jend4s/Tyri_light/tree/main/hw). Photos of design, production and final product are in [pics](https://github.com/Joint1k/Tyri_light/tree/main/pics) folder. 

# Main components
## XL6006
The XL6006 is fixed frequency (180kHz) PWM Boost (step-up) LED constant current regulator with wide input voltage range from 5 V to 32 V and maximum boost output, up to 60V. Maximal switching current capability, acocording to datasheet ([XL6006 datasheet](https://github.com/Jend4s/Tyri_light/tree/main/Datasheets/XL6006.pdf "XL6006 datasheet")) is 5 Amps. Regulator contains internal power MOSFET and build in Soft-Start function, Frequency compensation, Thermal shutdown function, and Current limit function. It is available in TO263-5L package.

The electric wiring of the regulator is based on recommended datasheet schematic from page 9, figure 11: 
<p align = "center">
<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/schmdatasheet.png?raw=true" width="600">
</p>

That is circuit with OVP function which can limited output voltage with zener diode connected to the FB pin. Zener diode voltage is choosed by recommended LED voltage $\times 1.3$. So it is based on this equation:

$$V_{DZ} = {1.3 \cdot V{OUT}}$$

The output current depend again on LED type and corect value is calculated from equation:
$$I_{LED} = \frac{0.22}{RS}$$

## 20/30 W power LED
It is classical powerfull LED with COB chip. Nominal power depends on type, but used LED is 20 or 30 W which is about 1800 to 3000 lumens.

# Own design
Whole DC/DC current regulator is designed for 20 W LED so the _RS_ resistor is around 360 $m\Omega$. It is a possible use a 30 W LED ~~but that is **NOT** tested yet~~ and it is required change the _RS_ resistor to lower resistance around 250 $m\Omega$. Under the XL6006 is no solder mask so here is a naked polygon with HASL. Function of this naked area is the heatsink for the DC/DC regulator. So it is need to place here a thermal paste or silicone pad. And beware this polygon is connected to the _SW_ pin of the regulator so don´t shorted with the GND or another pin otherwise whole DC/DC regulator can be irretrievably damaged.

And why pcb´s have white solder mask? Because light absorption which is little smaller than with green or other color.   

# Tyri light
<b>
<p align = "center">
<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/tyrilight1010.jpg?raw=true" width="600">
</p>
<p align = "center">
Fig.1 - Tyri light
</p>
<br/>
<br/>
<div id="image-table">
    <table>
	    <tr>
    	    <td style="padding:10px">
        	    <img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/3Dwithout2TOP.PNG?raw=true" width="400">
      	    </td>
            <td style="padding:10px">
            	<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/PCBwithoutTOP.png?raw=true" width="400">
            </td> 
        </tr>
    </table>
            <p align = "center">
            Fig.2 - TOP side of PCB - 3D visualization and fabricated PCB w/o components.
            </p>  
</div>
<br/>
<br/>
<div id="image-table">
    <table>
	    <tr>
    	    <td style="padding:10px">
        	    <img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/3Dwithout2BOT.PNG?raw=true" width="400">
      	    </td>
            <td style="padding:10px">
            	<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/PCBwithout2BOT.PNG?raw=true" width="400">
            </td> 
        </tr>
    </table>
            <p align = "center">
            Fig.3 - BOT side of PCB - 3D visualization and fabricated PCB w/o components.
            </p>  
</div>
<br/>
<br/>
<div id="image-table">
    <table>
	    <tr>
    	    <td style="padding:10px">
        	    <img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/3Dwith2.PNG?raw=true" width="400">
      	    </td>
            <td style="padding:10px">
            	<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/PCBwithTOP.png?raw=true" width="400">
            </td> 
        </tr>
    </table>
            <p align = "center">
            Fig.4 - TOP side of PCB - 3D visualization and fabricated PCB w/ components.
            </p>  
</div>
<br/>
<br/>
<div id="image-table">
    <table>
	    <tr>
    	    <td style="padding:10px">
        	    <img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/pcbOrigTOP.png?raw=true" width="400">
      	    </td>
            <td style="padding:10px">
            	<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/PCBwithTOP.png?raw=true" width="400">
            </td> 
        </tr>
    </table>
            <p align = "center">
            Fig.5 - TOP side of both PCB: LEFT is original, RIGHT is new.
            </p>  
</div>
<br/>
<br/>
<b>
<p align = "center">
<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/TyriLightInstall.png?raw=true" width="600">
</p>
<p align = "center">
Fig.6 - Tyri light w/ instaled new PCB.
</p>
</b>
<br/>
<br/>
</b>

# Measurements
It was made some basic measurements for comparsion of old and new design for two voltages. Basically for 12 volts and then for 14 volt. Why for 14 V? Because this voltage is basically more commone in 12 V car electric system when engine running and car alternator starts charging carbattery and power all systems in car. New design is more energy consumption but on other hand is more powerfull light source then original. 

## Power consuption:
| Voltage (V) | ORIGINAL (A) | NEW (A) |
| :---  |     :---: |      ---: |
| 12 | 1.323 | 3.174 |
| 14 | 1.106 | 2.580 |

## Temperature @VSUP = 14V:

| Time (min) | ORIGINAL (°C) | NEW (°C) |
| :---  |     :---: |      ---: |
| 0  | 25  | 25 |
| 5  | 35  | 47 |
| 10 | 40  | 54 |
| 15 | 45  | 60 |

Temperature of NEW pcb was measured on critical places like XL6006, inductor, LED, electrolytic capacitors and heatsink in 15th minute.

| Component | Temp (°C) |
| :---  |   :---: |
| XL6006 | 60 | 
| Inductor | 55 | 
| Capacitors | 43 | 
| LED | 60 | 
| Heatsink | 58 | 

<br/>
<br/>
<div id="image-table">
    <table>
	    <tr>
    	    <td style="padding:10px">
        	    <img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/OrigoLight.jpg?raw=true" width="400">
      	    </td>
            <td style="padding:10px">
            	<img src="https://github.com/Jend4s/Tyri_light/blob/main/pics/NewLight.jpg?raw=true" width="400">
            </td> 
        </tr>
    </table>
            <p align = "center">
            Fig.7 - Comparsion of both lights: LEFT is original, RIGHT is new. Distance 1.5 m from wall.
            </p>  
</div>
<br/>
<br/>

# Conclusion
 What say in conclusion? This project was basically spontaneous idea. Because i have this light in my inventory after repair but the emitted light of original LEDs were so weak so i don´t used it. After a year or so i made some cleanup in workshop and i found them. So i made this little project. All this was made in two sleepless nights. In last words i must thanks to [JLCPCB](https://jlcpcb.com/) for quality PCB´s and [LCSC](https://lcsc.com/) for all components.
 
 
