STC programmator to upload hex firmare to MCU flash.

This repo contains kicad electrical scheme, pcb design and description.

The electrical scheme and PCB design are a Kicad files. 

![Prorgammator](/images/programmator_view.jpg)

# Programmator usage
Programmator used with USB-2-TTL adapter. CHG340g is used as USB-2-TTL adapter.

![CHG340g](/images/ch340g.jpeg)

CHG340g connect to PC USB port, programmator is placed between CGH340g and STC MCU. 

## How to connect programmator
J1 for USB adapter
 - J1 +5V pin should be connected to USB adapter +5V pin.
 - J1 GND pin should be connected to USB adapter GND pin.
 - J1 TxD pin should be connected to USB adapter TxD pin.
 - J1 RxD pin should be connected to USB adapter RxD pin.

J2 for MCU 
 - J2 +5V pin should be connected to MCU +5V pin.
 - J2 GND pin should be connected to MCU GND pin.
 - J2 TxD pin should be connected to MCU TxD pin.
 - J2 RxD pin should be connected to MCU RxD pin.

   Jumper J1 is opened.

**Inside programmator USB TxD is routed to MCU RxD and USB RxD is routed to MCU TxD pin.**

## Upload firmare from Platfromio to MCU
[Plaformio] (https://platformio.org/) is a popular embedded software development IDE based on [Visual Studio Code](https://code.visualstudio.com/).

Platfromio use [stcgal](https://github.com/grigorig/stcgal/) to upload firmware. 

Jumper J1 should be opened before uploading start. 

1. Connect USB adapter with programmator (see [How to connect programmator section](#How-to-connect-programmator)). JP1 jumper should be opened.
2. Connect programmator to MCU pins. Developer boards and many PCB designs have dedicated pins.
3. Run Platfromio and open your STC project with source code that will be compiled to firmware.
4. Connect USB adapter to PC.
5. In Platfromio start upload. The most popular way to do this is press upload button
6. Platformio open terminal panel and output upload status as a messages to it
7. Waiting for "Cycling power: done" message. Uploading process waiting.
   > Cycling power: done
8. Press and hold the SW1 button on the programmer until the download process is complete.
    
9. Uploading proccess completes with messages
>Finishing write: done
>
>Setting options: done
>
>Target UID: <MCU chipid here>

>Disconnected!
>
10. You can release the button or hold it if you want to see how the downloaded firmware works.
11. For permanently firmware execution close J1 jumper


# Electrical sheme

![Programmator scheme](/images/STC15_programmator_scheme.png)

Scheme contains to important parts: TxD-RxD part and VCC part.

## TxD-RxD part
The principle of connection between MCU and USB adapter is RxD <-> TxD.
R1 and D1 are used to eliminate parasitic power supply through the pins to the microcontroller. 

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
