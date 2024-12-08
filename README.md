STC programmator to flash hex firmare

This repo contains kicad electrical scheme, pcb design and description.

The electrical scheme and PCB design are a Kicad files. 

# Programmator usage
Programmator used with USB-2-TTL adapter. CHG340g is used as USB-2-TTL adapter.

![CHG340g](/images/ch340g.jpeg)

CHG340g connect to PC USB port, programmator is placed between CGH340g and STC MCU. 

# Electrical sheme

![Programmator scheme](/images/STC15_programmator_scheme.png)

Scheme contains to important parts: TxD-RxD part and VCC part.

## TxD-RxD part
The principle of c

## VCC part
The MCU is powered via USB-2-TTL adapter. MCU GND connect to USB adapter GND.
USB adapter +5V connected to button SW1 and jumper JP1.

If the jumper JP1 is shorted, the microcontroller runs the loaded firmware and cannot be programmed.
In firmware download mode, the jumper is open and power is supplied only when the SW1 button is pressed and held.

Capacitors C1-C3 debounce of the SW1 button. In the classic programmator scheme only one 47mF polaraized capacitor is placed. 
But i have only 100mF capasitors and connect it in a chain to get 50mF capacity.    

# PCB design
![PCB front](/images/STC15_programmator_front.jpg)

![PCB back](/images/STC15_programmator_back.jpg)
