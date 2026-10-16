# Portable Laser

this is the complete build guide for my **portable laser**. it covers the components, circuit connections and setup needed to build a small portable laser using a **KY-008 laser module, a 3.7V Li-ion battery, a TP4056 USB-C charging module and a switch**.

the idea behind this project is pretty simple. the battery powers the laser, and the TP4056 module lets me recharge the battery through USB-C.

the switch is used to turn the laser on and off, while the TP4056 module handles battery charging.

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/1a18dfbf-19a7-41f3-b905-b7f7df13c260" />
<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/17326cdd-ee53-4641-bbd8-47471d3fbc01" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/5bd9a6b6-5d2f-4b6a-b4b6-0e8ba351dfbd" />

## Features

- portable laser build
- KY-008 laser module
- 3.3V–5V laser module supply range as specified for the module used
- 3.7V nominal Li-ion battery
- 2200mAh battery capacity
- USB-C charging
- TP4056 charging module with battery protection
- on/off switch
- compact and easy-to-build design
- no code required

## BOM – Bill of Materials

| Component | Quantity | Price (INR) | Price (USD) | Purchase Link |
|---|:---:|---:|---:|---|
| KY-008 Laser Module | 1 | ₹145 | $1.53 | [Amazon India](https://www.amazon.in/Transmitter-Compatible-ESP8266-Raspberry-Electronics/dp/B0H2M5YPGD) |
| 3.7V 18650 Li-ion Battery (1200mAh) | 1 | ₹70 | $0.74 | [Robocraze](https://robocraze.com/products/3-7v-1200mah-18650-battery?variant=44016221126880) |
| TP4056 USB-C Charging Module with Protection | 1 | ₹20 | $0.21 | [Robu.in](https://robu.in/product/tp4056-1a-li-ion-lithium-battery-charging-module-with-current-protection-type-c/) |
| 18650 Battery Holder | 1 | ₹18 | $0.19 | [FlyRobo](https://www.flyrobo.in/18650-lithium-battery-holder-for-battery-1-x-18650-cell) |
| On/Off Switch | 1 | ₹9 | $0.10 | [Robu.in](https://robu.in/product/1-month-warranty-585/) |
| 3D-Printed Enclosure | 1 | — | — | Self-made |

## Circuit Diagram

here are the basic circuit connections i used as a reference while putting everything together

<img width="1520" height="964" alt="image" src="https://github.com/user-attachments/assets/ca23e1ef-7971-454f-a43d-31d6601abb6b" />

### Main Connections

**Li-ion Battery → TP4056**

| Battery | TP4056 |
|---------|--------|
| Positive (+) | B+ |
| Negative (−) | B− |

**TP4056 → KY-008 Laser Module**

| TP4056 | Connection |
|--------|------------|
| OUT+ | KY-008 VCC |
| OUT− | Switch → KY-008 GND |

i connected the switch in series with the ground wire so opening it breaks the circuit and turns the laser off. you can also place the switch in the positive wire if that makes the wiring easier.

use the **OUT+ and OUT−** terminals to power the laser if your TP4056 board has built-in protection. the B+ and B− terminals are for the battery.

make sure the battery, charging module and laser are connected with the correct polarity. always check the labels on your actual modules before powering anything.

## CAD Model

<img width="972" height="614" alt="image" src="https://github.com/user-attachments/assets/0a96c6e4-fe47-41d6-a1a9-09a80561b1da" />
<img width="868" height="582" alt="image" src="https://github.com/user-attachments/assets/2017bcf5-fbb3-4a02-93e2-76453783a4db" />

you might notice that some components overlap in the CAD model, but that was intentional. some of the models i exported weren't accurate to the actual components i had, so i had to overlap a few parts to make everything fit properly in real life.

## How to Build this...

**step 1:** get all the components listed in the BOM. the main parts are the KY-008 laser module, a 3.7V Li-ion battery, a USB-C TP4056 charging module with protection and a switch.

**step 2:** connect the battery to the TP4056 module by connecting the positive terminal to B+ and the negative terminal to B−.

**step 3:** connect the KY-008 laser module to the protected output of the TP4056. connect OUT+ to the laser's VCC pin.

**step 4:** connect the switch in series between OUT− and the laser's GND pin. check that the switch works properly and completely breaks the circuit when turned off.

**step 5:** double-check all the connections and polarity before connecting the battery. make sure there are no loose wires or exposed connections that could accidentally touch each other.

**step 6:** turn on the switch and check if the laser works. never look directly into the laser aperture or point it at anyone.

**step 7:** when the battery needs charging, connect a suitable USB-C power source to the TP4056 module and follow the charging indicators for your particular board.

**step 8:** don't assume the laser can stay on while the battery is charging. disconnect it during charging unless you've confirmed that your board supports powering a load while charging.

**step 9:** once everything works, secure the components inside the enclosure. make sure the battery doesn't move around and that no exposed wires can touch each other.

## Power Supply

this build uses a single-cell Li-ion battery with a nominal voltage of 3.7V.

the battery voltage changes depending on how much charge is left

| Battery state | Approximate voltage |
|---------------|---------------------:|
| Fully charged | 4.2V |
| Nominal voltage | 3.7V |
| Nearly discharged | Depends on the battery and protection cutoff |

the KY-008 module used in this build is specified for a 3.3V–5V supply. check the specifications of your own module before connecting it, as different versions may have different requirements.

## Battery Life

the battery capacity is **2200mAh**, but the actual runtime depends on how much current the particular KY-008 module draws and how much of the battery's capacity is usable.

you can get a rough runtime estimate by dividing the usable battery capacity in mAh by the average current draw in mA. this only gives an estimate because battery condition, voltage and circuit losses can also affect the runtime.

i haven't measured the actual current draw of this build, so i can't give an exact runtime yet.

## Charging

the TP4056 USB-C module is used to recharge the single-cell Li-ion battery.

- connect the battery to B+ and B−
- use a suitable USB-C power source for charging
- check that your board includes battery protection
- the TP4056 charging IC alone does not provide complete battery protection
- never short the battery terminals
- don't leave a damaged or unusually hot battery charging unattended
- disconnect the laser while charging unless you've confirmed that the board supports load sharing

## Known Issues

1. the actual runtime depends on how much current the laser module draws
2. different KY-008 modules may have different specifications
3. the battery voltage changes as it charges and discharges
4. incorrect polarity can damage the laser module or charging board
5. the switch must be wired correctly in series with GND to interrupt the circuit
6. the TP4056 charging IC alone does not provide complete battery protection
7. not every TP4056 board supports powering a load while charging
8. loose wires can cause intermittent operation or short circuits
9. a damaged or unsuitable battery can be unsafe to charge or use
10. the actual charging current depends on the particular TP4056 board and its configuration

## Safety Notes

- never look directly into the laser aperture
- never point the laser at another person or an animal
- never point the laser at vehicles, aircraft or their operators
- avoid pointing the laser at mirrors or other reflective surfaces
- keep the laser away from children and store it safely
- disconnect the power before changing any wiring
- double-check the polarity before connecting the battery
- don't short-circuit, puncture, crush or overheat the Li-ion battery
- use a suitable charger and never use a swollen, damaged or leaking battery
- keep the circuit insulated so exposed wires cannot touch each other and cause a short circuit

## Working Principle

the working principle is pretty straightforward. the Li-ion battery supplies power to the circuit, and the TP4056 module allows the battery to be recharged through its USB-C port.

when the switch is closed, the circuit is complete and power reaches the KY-008 laser module. when the switch is open, the circuit breaks and the laser turns off.

the basic flow looks like this

Li-ion Battery

   ↓
   
TP4056 Protected Output

   ↓
   
Switch

   ↓
   
KY-008 Laser Module

   ↓
   
Laser Output

the TP4056 handles battery charging, the switch controls the laser, and the entire build works without a microcontroller or any code.

## Final Result

the idea behind this project is simple. a 3.7V Li-ion battery powers the KY-008 laser module, the USB-C TP4056 module makes the battery rechargeable, and a switch lets me turn the laser on and off.

it's a small project, but it brings together some useful basics like **electronics, battery-powered circuits, Li-ion charging and simple switching**.

Working video: https://youtube.com/shorts/vNFvSqzoJ1I
