# Serial Communication

This markdown article gives a brief overview on Serial Communication in Embedded Systems

### *What is an Embedded System?*</br>
By textbook definition,
> "An embedded system is a system that has embedded software and computer-hardware, which makes it a system dedicated for an application or specific part of an application or product or a part of a larger system"</br>
> -Embedded Systems: Architecture, Programming and Design by Raj Kamal


An embedded system is a combination of various hardware components such as memory, processor and ports each forming a part of a larger system which interacts with its surroundings, process data available and take necessary actions done mostly with the help of an accompanying software.

<img src="https://res.cloudinary.com/rs-designspark-live/image/upload/c_limit,w_537/f_auto/v1/article/What_is_an_embedded_system1_2c08b9a967d1374872ad430bbd8c3fb5feec0401" style="height:200px;"/>


### *Example of an embedded system...*
- Washing Machine. A washing machine has a electric motor connected to a control unit which controls the speed and duraion for which the motor rotates its drums. It has a interface unit such as a lcd display or comes with different buttons to take input from the user. The washing machine also contains various sensors and actuators used to interact with various parts of the machine. The processor along with the data and program memory and port thats communnicated with these parts form an embedded system basically embedded into the washing machine.

### *Importance of communication protocols...*
Various components in an embedded system relies on data produced by other components and efficient transfer of this data between components ensure smooth functioning of the system. There are mainly two kinds of communication: 
- Parallel communication : where multiple bits are send along parallel lines connected between two different components. This way of communication is fast but causes problem as the range of communication increases and introduces problems like [Crosstalk Noise](https://en.wikipedia.org/wiki/Crosstalk).</br>
<img src="https://circuitglobe.com/wp-content/uploads/2019/07/parallel-communication.jpg" style="height:200px;"/></br>
- Serial Communication : where a single bit is send at a time from the sender to the receiver. Various improvments have been made over years to make serial communication faster with the added benefit of low cost and long range communication. It has become the most widely used method of communication.</br>
<img src="https://www.electronicshub.org/wp-content/uploads/2017/06/Serial-Communication.jpg" style="height:200px;"/></br>

## Serial Communication Protocols:
### *What are communication protocols?*
A Communication Protocol is simply a procedure or a set of rules that are agreed upon by both sender and receiver in order to transfer data between them. Different protocols offers different speed, bandwidth, amount of data transferred, no of receivers and senders etc. These protocols can also differ in security and reliability.</br>
For ex: In Networking TCP and UDP are two protocols used to transfer data between networks. UDP transfers data without acknowledging if the data transfer was successful or not wheres in TCP The data is broken into smaller chunks called packets and the transfer of data is made reliable using acknowlegements betweeen sender and receiver to ensure the data is transferred without loss.</br>
Here we will be looking into **SPI and I2C** communication protocols used in Embedded Systems. Both are Synchronous Serial communication protocols that make use of a clock to synchronize both the sender and receiver so that the receiver knows when data is put on line by the sender. The data is transferred serially between them.</br>
_NOTE: Here we use controller to specify the device that generates the clock and thereby control the data transfer whereas Peripheral is the recepient device of that clock._</br>

## **SPI**

**SPI(Serial Peripheral Interface)** is a **full-duplex**(means data can be send in both directions between controller and  at the same time) **serial synchronous** communication protocol using 3 or 4 lines for communication.</br>

- **SCK/SCL(Serial Clock) line** : used by the Controller to provide clock signal and the Peripheral to receive it.This allows for synchronization of data transfer.
- **COPI(Controller Out Peripheral In) line** : used by controller to send output data and Peripheral to receive that data as input.
- **CIPO(Controller In Peripheral Out) line** : used by controller to receive input data send from the peripheral as output.
- **CS(Chip Select) line** (optional) : used by the controller to select a peripheral device from multiple devices.

### _How SPI works..._ </br>
Consider data(in the form of bits, one bit at a time represents by HIGH(ex:5V) or Low(ex:0V)) is put on **COPI** by Controller and on **CIPO** by the Peripheral device.</br>
The clock signal generated by the controller goes HIGH which indicates it is time to read data which is when both the controller and peripheral device takes in the data put on theri respective input lines.</br>
If there are multiple peripheral devices, the controller selects the peripheral device through its **CS** line before sending or receiving data.
<img src="https://cdn.sparkfun.com/assets/learn_tutorials/1/6/BasicSPI_Updated.jpg" style="height:200px;"/></br>
_Image from [Here](https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi/all)_ </br>

## **I2C**

**I2C(Inter Integrated Circuit)** is a **half duplex**(meaning data can be send only in one direction between controller and peripheral device at the same time) **serial synchronous** communication protocol using only 2 lines for communication.</br>

- **SCL(Serial CLock)** line: Like in SPI, it is used for synchronization of data transfer between controller and peripheral devices.
- **SDA(Serial Data)** line: is used for data carrying data between the controller and the peripheral devices.

### _How I2C data look like..._</br>
In I2C the communication is in the form of a combination of messages as shown below.
<img src="https://www.circuitbasics.com/wp-content/uploads/2016/01/Introduction-to-I2C-Message-Frame-and-Bit-2.png" style="height:200px;"/></br>
_Image from [Here](https://www.circuitbasics.com/basics-of-the-i2c-communication-protocol/)_ </br>
- **Start Condition** : Controller send this to initiate communication every time a data read/write is required.
- **Address Frame** : This contains the address to select the intended peripheral device.
- **Read/Write bit** : This bit specifies if controller is writing/reading the data to/from the peripheral.
- **ACK/NACK bit** : is send by the receiver to acknowledge if the address or data frame was received successfully.
- **Stop condition** : Controller send this to inform that the data transfer is complete.

### _How I2C works..._ </br>
You might have noticed that ther is no **CS** line in I2C. The controller instead uses address of each peripheral device to select the required one. Only the address selected device then communicates with the controller.</br>
1. The controller initiates start condition by switching SDA line from High to Low voltage before switching SCL line from High to Low.
2. The Controller then sends the peripheral device address along with the read/write bit to select the required peripheral device.
3. If the address is identified by a peripheral device, it sends an acknowledgement signal to the controller by pulling the SDA line to low voltage.
4. The Controller then send/receive data to/from the peripheral device.
5. An acknowledgement signal is send by the receiver in case of successfully receiving data.
6. The data transmission is ended by the controller by switching SCL High before switching SDA High.

<img src="https://www.circuitbasics.com/wp-content/uploads/2016/01/Introduction-to-I2C-Data-Transmission-Diagram-START-CONDITION-3.png" style="height:200px;"/></br>
_Image from [Here](https://www.circuitbasics.com/basics-of-the-i2c-communication-protocol/)_ </br>
