# Repository for Group 2 CyberTap
CyberTap, the network tap of the future. <br>

# What is CyberTap?
CyberTap is a high throughput hardware network tap designed for industrial control systems closed off from the internet. Other network monitoring solutions are software based and over utilize the CPU, which could theoretically result in packet loss. Packet loss is particularly undesirable in the context of the high data throughput involved in industrial control systems, especially when said systems directly rely on input data. CyberTap will be able to collect Operational Technology (OT) network packets, parse and generate metadata for all relevant network protocols of a system, and store the collected packets and generated metadata in storage. The product will be implemented on a Field Programmable Gate Array (FPGA) to utilize their ability to quickly process large data loads. The final deliverable will contain the following: A simulated high-data-volume OT network using 2 Raspberry Pis and a network switch, an FPGA  that sniffs, parses, and outputs the packet data coming from the SPAN port of the switch, a solid state drive that contains the outputted metadata, and a web application for querying the drive and displaying the metadata.

# Getting Started
In order to get CyberTap up and running, first configure a SPAN port on the desired network switch. This is the port that CyberTap will be connected to. Next, plug the PYNQ into a computer via microUSB-USB connection and plug in the power plug, and connect to the SPAN port via ethernet, and then switch on the power switch. After this, Go to your computer's network device settings and create a network adapter with a manually set IPv4 address set to that of the board (in our case, 192.168.137.15, with a subnet mask of 255.255.0.0). Then, navigate to the device's IP and port (default if unchanged on the board settings) in your web browser. You'll be greeted with a Jupyter notebook login screen. The default login information is username: Xilinx, password: Xilinx123. Next, in Jupyter notebook start a new console. In the console, navigate to the directory PYNQ/Jupyter_Notebooks and run the script main.sh. To then run the web application, follow the instructions in the software report of the wiki pages and run node server.js. Then you should navigate to localhost:8080/main.html in your browser. CyberTap should now be sniffing, parsing, storing, and displaying on the web app all packets going through the configured network switch.

# How It Works Diagram
<p align="center">
<img src="./how-it-works.png" width="55%" />
</p>

# Who Are We? The History of CyberTap.
In the summer of 2019, Felipe Dale Figeman asked his employers at Cybereason if they had an idea for a year long project. Thus, CyberTap was born. The group formed and agreed to build a hardware based network tap. <br> <br>
Felipe Dale Figeman. Email: fdale@bu.edu <br>
Felipe is a Computer Engineering major that has taken classes such as Embedded Systems, Cloud Computing, and Operating Systems. His role is focused on packet sniffing and being able to connect the Pis and FPGA so the FPGA may receive the packets to parse. <br> <br>
Alex Fatyga. Email: afatyga@bu.edu <br>
Alex is a Computer Engineering major that has taken classes such as Operating Systems, Smart and Connected Systems, and CS Software Engineering. Her role is focused on the front end and receiving packet information into the front end.  She will also be working on hosting of the web application from the PYNQ board. <br> <br>
Evan Lang. Email: evanlang@bu.edu <br>
Evan is a Computer Engineering major that has taken classes such as Digital VLSI Design, Electronics and Computer Architecture. Evan created, generated, and tested the Microblaze processor used to operate the ethernet controller and run the server on the FPGA. He used Vivado SDK to create and test the echo server used as a template for the project. He will be taking the main role in packet parsing next semester. <br> <br>
Noah Malhi. Email: malhin@bu.edu <br>
Noah is a Computer Engineering major that has taken classes such as Embedded Systems, Operating Systems, and High Performance Programming. Noah is focused on simulating the network activity with the Raspberry Pis and writing the packet information to SD and SSD. Noah has also assisted in the first semester’s efforts to sniffing the packets on the Nexys A7 from the network switch. <br> <br>
Justin Morgan. Email: justinfm@bu.edu <br>
Justin is a Computer Engineering major that has taken classes such as Smart and Connected Systems and Operating Systems and has prior networking experience. Justin’s role is to work on the packet logic after the parsing of the protocols. He will deal with generation of metadata. Justin will also assist in writing from FPGA to the external SSD.

# GitHub Info
PYNQ_sniff holds all files that we run on the PYNQ and is the most up to date <br>
front_end holds server.js and main.html which is the web application. server.js reads in the csv file and uses socket io to send it over to main.html to be added to the table
