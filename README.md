# Portable Laser

This is the whole build guide for my **portable laser**. It has the component list, circuit connections and setup information needed to make your own small portable laser using a **KY-008 laser module, a 3.7V Li-ion battery, a TP4056 USB-C charging module and a switch**.

The main idea behind this project is to build a compact, battery-powered laser using a **KY-008 laser module**. The battery supplies power to the laser, while the TP4056 module is used to recharge the battery through USB-C.

The switch turns the laser on and off, while the TP4056 charging module manages battery charging.

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/1a18dfbf-19a7-41f3-b905-b7f7df13c260" />
<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/17326cdd-ee53-4641-bbd8-47471d3fbc01" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/5bd9a6b6-5d2f-4b6a-b4b6-0e8ba351dfbd" />


## Features

- Portable laser build
- KY-008 laser module
- 3.3V–5V laser module supply range (as specified for the module used)
- 3.7V nominal Li-ion battery
- 2200mAh battery capacity
- USB-C charging
- TP4056 charging module with battery protection
- On/off switch
- Compact and easy-to-build design
- No code required

## BOM – Bill of Materials

| Component | Quantity | Price | Purpose | Purchase Link |
|-----------|:--------:|-------:|---------|:-------------:|
| KY-008 Laser Module | 1 | — | Laser output | Not provided |
| 3.7V Li-ion Battery, 2200mAh | 1 | — | Power source | Not provided |
| TP4056 USB-C Charging Module with Protection | 1 | — | Charging and battery protection | Not provided |
| On/Off Switch | 1 | — | Turns the laser on and off | Not provided |
| Jumper Wires | As required | — | Electrical connections | — |
| Enclosure | As required | — | Protects and holds the components | Self made |

## Circuit Diagram

I have added the basic connections below. You can use them as a reference while wiring your own portable laser.

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

The switch is connected in series with the ground wire, so opening the switch breaks the circuit and turns the laser off. The switch can also be placed in series with the positive output wire if that is easier for your wiring layout.

Use the **OUT+ and OUT−** terminals to power the laser when your TP4056 board has protection circuitry. The B+ and B− terminals are for the battery.

The battery, charging board and laser must be connected with the correct polarity. Check the labels on your exact modules before powering the circuit.

## CAD Model

<img width="972" height="614" alt="image" src="https://github.com/user-attachments/assets/0a96c6e4-fe47-41d6-a1a9-09a80561b1da" />
<img width="868" height="582" alt="image" src="https://github.com/user-attachments/assets/2017bcf5-fbb3-4a02-93e2-76453783a4db" />

you might see some components overlapping but actuallly thats done on purpose like they models i exported some where not accurate
so the models fits the reall life components i had to overlap them

## How to Build this...

**step 1:** First get all the components mentioned in the BOM. The main parts required are the KY-008 laser module, a 3.7V 2200mAh Li-ion battery, a USB-C TP4056 charging module with protection and a switch.

**step 2:** Connect the battery to the TP4056 module. Connect battery positive to B+ and battery negative to B−.

**step 3:** Connect the KY-008 laser module to the protected output of the TP4056. Connect OUT+ to the laser VCC pin.

**step 4:** Connect the switch in series between OUT− and the laser GND pin. Make sure the switch opens and closes the circuit correctly.

**step 5:** Check all connections and polarity before inserting or connecting the battery. Make sure there are no loose wires or exposed connections that could short together.

**step 6:** Turn the switch on and check that the laser works. Do not look into the laser aperture or point it at anyone.

**step 7:** To recharge the battery, connect a suitable USB-C power source to the TP4056 module. Follow the charging indicators and instructions for your exact board.

**step 8:** Do not assume that the laser can remain powered while charging. Disconnect the laser during charging unless you have verified that your particular board supports powering a load while charging.

**step 9:** Finally, secure the components inside a suitable enclosure. Make sure the battery cannot move around and that no bare wires can touch each other.

## Power Supply

The build uses a single-cell Li-ion battery with a nominal voltage of 3.7V.

The approximate battery voltage changes as it charges and discharges:

| Battery state | Approximate voltage |
|---------------|---------------------:|
| Fully charged | 4.2V |
| Nominal voltage | 3.7V |
| Nearly discharged | Depends on the battery and protection cutoff |

The KY-008 module used in this build is specified for a 3.3V–5V supply. Check the markings and specifications of your own module before connecting it.

## Battery Life

The battery capacity is **2200mAh**, but the actual runtime depends on the current drawn by the particular KY-008 module and the usable capacity of the battery.

You can estimate runtime by dividing the usable battery capacity in mAh by the average current draw in mA. The result is only an estimate, since battery condition, voltage and circuit losses also affect runtime.

The actual current draw has not been measured for this build, so an exact runtime cannot be specified.

## Charging

The TP4056 USB-C module is used to charge the single-cell Li-ion battery.

- Connect the battery to B+ and B−.
- Use a suitable USB-C power source for charging.
- Check that the board includes battery-protection circuitry.
- The TP4056 charging IC by itself does not provide complete battery protection.
- Do not short the battery terminals.
- Do not leave a damaged or unusually hot battery charging unattended.
- Disconnect the laser while charging unless the board has been verified to support load sharing.

## Known Issues

1. The actual runtime depends on the current drawn by the laser module.
2. Different KY-008 modules may have different specifications.
3. The battery voltage changes as the battery charges and discharges.
4. Incorrect polarity can damage the laser module or charging board.
5. A switch connected in series with GND must be wired correctly to interrupt the circuit.
6. The TP4056 charging IC alone does not provide complete battery protection.
7. Not every TP4056 board supports powering a load while charging.
8. Loose wires can cause intermittent operation or a short circuit.
9. A damaged or unsuitable battery can be unsafe to charge or use.
10. The actual charging current depends on the particular TP4056 board and its configuration.

## Safety Notes

- Never look directly into the laser aperture.
- Never point the laser at another person or an animal.
- Never point the laser at vehicles, aircraft or their operators.
- Avoid aiming the laser at mirrors or other reflective surfaces.
- Keep the laser away from children and store it securely.
- Disconnect power before changing the wiring.
- Check polarity before connecting the battery.
- Do not short-circuit, puncture, crush or overheat the Li-ion battery.
- Use a suitable charger and do not use a swollen, damaged or leaking battery.
- Keep the circuit insulated so that exposed wires cannot touch or short together.

## Working Principle

The Li-ion battery supplies power to the circuit.

The TP4056 module is connected to the battery and allows it to be recharged through its USB-C port. When the switch is closed, the circuit is completed and power reaches the KY-008 laser module.

When the switch is open, the circuit is interrupted and the laser turns off.

The basic flow is:

Li-ion Battery

   ↓
   
TP4056 Protected Output

   ↓
   
Switch

   ↓
   
KY-008 Laser Module

   ↓
   
Laser Output

The TP4056 is used for charging the battery. The switch controls the laser circuit, and no microcontroller or code is required for this build.

## Final Result

The whole idea is pretty simple — a 3.7V Li-ion battery powers the KY-008 laser module, while a USB-C TP4056 module makes the battery rechargeable and a switch turns the laser on and off.

It is a compact introduction to **basic electronics, battery-powered circuits, Li-ion charging and simple switching**, all combined into one project.

Working video: https://youtube.com/shorts/vNFvSqzoJ1I
