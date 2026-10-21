# Portable Laser

this is the full build guide for my portable laser it covers the components circuit connections and setup you need to build a small portable laser using a ky-008 laser module a 3.7v li-ion battery a tp4056 usb-c charging module and a switch

the idea behind this project is pretty simple the battery powers the laser and the tp4056 module lets me recharge the battery thru usb-c

the switch is used to turn laser on and off while the tp4056 module handles the battery charging

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/1a18dfbf-19a7-41f3-b905-b7f7df13c260" />
<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/17326cdd-ee53-4641-bbd8-47471d3fbc01" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/5bd9a6b6-5d2f-4b6a-b4b6-0e8ba351dfbd" />

## features

- portable laser build
- ky-008 laser module
- 3.3v to 5v supply range for the laser module i used
- 3.7v nominal li-ion battery
- 2200mah battery capacity
- usb-c charging
- tp4056 charging module with battery protection
- on off switch
- compact and easy to build design
- no microcontroller or code needed

## bom bill of materials

| component | quantity | price (inr) | price (usd) | purchase link |
|---|:---:|---:|---:|---|
| ky-008 laser module | 1 | ₹145 | $1.53 | [amazon india](https://www.amazon.in/Transmitter-Compatible-ESP8266-Raspberry-Electronics/dp/B0H2M5YPGD) |
| 3.7v 18650 li-ion battery 1200mah | 1 | ₹70 | $0.74 | [robocraze](https://robocraze.com/products/3-7v-1200mah-18650-battery?variant=44016221126880) |
| tp4056 usb-c charging module with protection | 1 | ₹20 | $0.21 | [robu.in](https://robu.in/product/tp4056-1a-li-ion-lithium-battery-charging-module-with-current-protection-type-c/) |
| 18650 battery holder | 1 | ₹18 | $0.19 | [flyrobo](https://www.flyrobo.in/18650-lithium-battery-holder-for-battery-1-x-18650-cell) |
| on off switch | 1 | ₹9 | $0.10 | [robu.in](https://robu.in/product/1-month-warranty-585/) |
| 3d printed enclosure | 1 | none | none | self made |

## circuit diagram

here are the basic circuit connections i used as reference while putting everything together

<img width="1520" height="964" alt="image" src="https://github.com/user-attachments/assets/ca23e1ef-7971-454f-a43d-31d6601abb6b" />

### main connections

battery to tp4056

| battery | tp4056 |
|---------|--------|
| positive | b+ |
| negative | b- |

tp4056 to ky-008 laser module

| tp4056 | connection |
|--------|------------|
| out+ | ky-008 vcc |
| out- | switch then ky-008 gnd |

i connected the switch in series with ground wire so when its open the circuit breaks and laser turns off you can also put the switch on the positive wire if that makes wiring easier for you

use the out+ and out- terminals to power the laser if your tp4056 board have built in protection the b+ and b- terminals are only for the battery

make sure the battery charging module and laser are connected with correct polarity always check the labels on your actual modules before powering anything

## cad model

<img width="972" height="614" alt="image" src="https://github.com/user-attachments/assets/0a96c6e4-fe47-41d6-a1a9-09a80561b1da" />
<img width="868" height="582" alt="image" src="https://github.com/user-attachments/assets/2017bcf5-fbb3-4a02-93e2-76453783a4db" />

you might notice some components overlap in the cad model but that was on purpose some of the models i exported were not accurate to the actual components i had so i had to overlap few parts to make everything fit properly in real life

## how to build this

step 1 get all the components listed in the bom the main parts are the ky-008 laser module a 3.7v li-ion battery a usb-c tp4056 charging module with protection and a switch

step 2 connect the battery to the tp4056 module positive terminal goes to b+ and negative terminal goes to b-

step 3 connect the ky-008 laser module to the protected output of tp4056 connect out+ to the laser vcc pin

step 4 connect the switch in series between out- and the laser gnd pin check that switch works properly and fully breaks the circuit when its turned off

step 5 double check all connections and polarity before you connect the battery make sure theres no loose wires or exposed connections that can accidentally touch each other

step 6 turn on the switch and see if laser works never look directly into the laser aperture or point it at anyone

step 7 when battery needs charging connect a suitable usb-c power source to the tp4056 module and follow the charging indicators for your particular board

step 8 dont assume the laser can stay on while battery is charging disconnect it during charging unless you confirmed that your board supports powering a load while charging

step 9 once everything works secure the components inside the enclosure make sure battery dont move around and no exposed wires can touch each other

## power supply

this build use a single cell li-ion battery with nominal voltage of 3.7v

the battery voltage changes depending on how much charge is left

| battery state | approximate voltage |
|---------------|---------------------:|
| fully charged | 4.2v |
| nominal voltage | 3.7v |
| nearly discharged | depends on the battery and protection cutoff |

the ky-008 module used in this build is specified for 3.3v to 5v supply check the specs of your own module before connecting it because different versions may have different requirements

## battery life

the battery capacity is 2200mah but actual runtime depends on how much current the particular ky-008 module draws and how much of the battery capacity is actually usable

you can get a rough runtime estimate by dividing the usable battery capacity in mah by the average current draw in ma this only give an estimate because battery condition voltage and circuit losses can also affect the runtime

i havent measured the actual current draw of this build yet so i cant give an exact runtime right now

## charging

the tp4056 usb-c module is used to recharge the single cell li-ion battery

- connect the battery to b+ and b-
- use a suitable usb-c power source for charging
- check that your board includes battery protection
- the tp4056 charging ic alone does not give complete battery protection
- never short the battery terminals
- dont leave a damaged or unusually hot battery charging unattended
- disconnect the laser while charging unless you confirmed the board supports load sharing

## known issues

1. actual runtime depends on how much current the laser module draws
2. different ky-008 modules may have different specifications
3. battery voltage changes as it charges and discharges
4. wrong polarity can damage the laser module or charging board
5. the switch must be wired correctly in series with gnd to break the circuit
6. the tp4056 charging ic alone does not give complete battery protection
7. not every tp4056 board support powering a load while charging
8. loose wires can cause on and off operation or short circuits
9. a damaged or unsuitable battery can be unsafe to charge or use
10. actual charging current depends on the particular tp4056 board and its configuration

## safety notes

- never look directly into the laser aperture
- never point the laser at another person or an animal
- never point the laser at vehicles aircraft or their operators
- avoid pointing the laser at mirrors or other shiny surfaces
- keep the laser away from children and store it safely
- disconnect the power before changing any wiring
- double check the polarity before connecting the battery
- dont short circuit puncture crush or overheat the li-ion battery
- use a suitable charger and never use a swollen damaged or leaking battery
- keep the circuit insulated so exposed wires cant touch each other and cause a short circuit

## working principle

the working principle is pretty straightforward the li-ion battery supplies power to the circuit and the tp4056 module let the battery be recharged thru its usb-c port

when the switch is closed the circuit is complete and power reach the ky-008 laser module when the switch is open the circuit breaks and laser turns off

the basic flow looks like this

li-ion battery
↓
tp4056 protected output
↓
switch
↓
ky-008 laser module
↓
laser output

the tp4056 handles battery charging the switch controls the laser and whole build works without a microcontroller or any code

## final result

the idea behind this project is simple a 3.7v li-ion battery powers the ky-008 laser module the usb-c tp4056 module makes the battery rechargeable and a switch lets me turn the laser on and off

its a small project but it brings together some useful basics like electronics battery powered circuits li-ion charging and simple switching

working video https://youtube.com/shorts/vNFvSqzoJ1I
