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


