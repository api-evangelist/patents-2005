---

title: Embedded device for implementing a boot process on a host
abstract: An embedded device, for implementing a boot process on a host, is provided. This embedded device includes servers supporting various industry-standard Internet protocols and services related to the boot process. This embedded device also includes a storage medium that stores boot options for multiple Operating Systems (OSs). In addition, this embedded device includes a user-friendly interface for configuring the servers for the boot process.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07650490&OS=07650490&RS=07650490
owner: Augmentix Corporation
number: 07650490
owner_city: Austin
owner_country: US
publication_date: 20051230
---
The present invention relates generally to booting of a computer. More specifically it relates to booting of a computer using Pre boot eXecution Environment PXE .

Pre boot execution Environment is an Intel Wired for Management WfM capability that enables a boot of a computer from a server over a network. A computer that has to be booted is hereinafter referred as a host. To standardize interactions between the host and the server industry standard Internet protocols and services such as Transmission Control Protocol Internet Protocol TCP IP Dynamic Host Configuration Protocol DHCP and Trivial File Transfer Protocol TFTP are used.

In existing techniques of booting a host via the PXE various servers that support the protocols and services related to the PXE are deployed on a network. However a set up is required to deploy the servers on the network. In addition it is required that these servers are configured corresponding to an operating system that has to be loaded on the host. However an improper configuration may lead to an inconsistent boot of the host.

In light of the foregoing discussion there exists a need for a PXE boot server that is capable of booting a host without a need for any external server and set up on a network. The PXE boot server needs to be capable of booting the host in a consistent manner.

The present invention provides an embedded device for implementing a boot process on a host. An object of the present invention is to provide a Pre boot execution Environment PXE boot server that is capable of booting the host.

Another object of the present invention is to provide the PXE boot server on an embedded device which does not require any external server and set up on a network. This minimizes manual intervention required for configuration of external servers on the network.

Yet another object of the present invention is to provide a simple user interface for configuring the PXE boot from remote locations.

In order to achieve the foregoing objectives and in accordance with the purpose of the various embodiments of the present invention as broadly described herein the present invention provides an embedded device for implementing a PXE boot on a host to which the embedded device is attached. The embedded device includes servers supporting various industry standard Internet protocols and services related to the PXE boot. In addition the embedded device configures the servers on its own to provide an Operating System OS that has to be loaded on the host. Consequently the embedded device provides a consistent PXE boot process to the host.

Apart from the servers the embedded device includes a storage medium to store boot options for various OSs. This makes the embedded device capable of providing the complete PXE boot process to the host.

Further the embedded device includes a user interface for configuring the PXE boot from remote locations. Based on an OS selected by a user the embedded device configures its servers automatically thereby providing a simple configuration interface.

Embodiments of the present invention provide an embedded device for implementing a boot process on a host. In the description herein for embodiments of the present invention numerous specific details are provided such as examples of components and or methods to provide a thorough understanding of embodiments of the present invention. One skilled in the relevant art will recognize however that an embodiment of the present invention can be practiced without one or more of the specific details or with other apparatus systems assemblies methods components materials parts and or the like. In other instances well known structures materials or operations are not specifically shown or described in detail in order to avoid obscuring aspects of embodiments of the present invention.

Embodiments of the present invention provide an embedded device that is capable of booting a host to which the embedded device is attached. The embedded device includes a microprocessor a storage medium and a communication medium. The microprocessor includes servers supporting Internet protocols and services related to the boot process. The storage medium stores boot options corresponding to various OSs. The communication medium provides an interface between the embedded device and the host. The communication medium is connected to a communication bus on the host. In accordance with various embodiments of the present invention this embedded device is an add on Peripheral Component Interconnect PCI card.

In accordance with various embodiments of the present invention embedded device includes a microprocessor a storage medium and a communication medium . Microprocessor includes various servers supporting Internet protocols and services related to the PXE boot such as Dynamic Host Configuration Protocol DHCP Trivial File Transfer Protocol TFTP Network File System NFS and Server Message Block Common Internet File System SMB CIFS . Further microprocessor is connected to storage medium which includes boot options corresponding to various Operating Systems OSs . Examples of storage medium include but are not limited to a flash memory and a micro drive. Details regarding microprocessor and storage medium have been described in conjunction with respectively.

Further microprocessor is connected to communication medium . Communication medium provides an interface between embedded device and host . In accordance with various embodiments of the present invention communication medium includes an Ethernet controller. Further embedded device includes a local device driver to provide an interface between the Ethernet controller and a local OS running on microprocessor .

In accordance with various embodiments of the present invention embedded device includes a PXE Read Only Memory ROM which is connected to the Ethernet controller. PXE ROM includes a PXE loader to initiate the PXE boot. The PXE loader loads the executable code of PXE program into the memory of host and schedules it for execution.

In accordance with various embodiments of the present invention embedded device is connected to a communication bus which is included in host . Examples of communication bus include but are not limited to a PCI bus a PCI extended PCI X bus and a PCI Express bus.

Management interface is used to select an OS to be loaded for booting host in accordance with various embodiments of the present invention. Management interface can include any of the following a web Application Programming Interface API a Secure Shell SSH API and a Hardware Platform Interface HPI API.

DHCP server responds to DHCP requests made by host during the PXE boot. The DHCP requests include configuration parameters specific to the PXE boot. These configuration parameters can include an Internet Protocol IP address to be used by host an IP address of a TFTP server the name of a GRUB file etc. In accordance with various embodiments of the present invention DHCP server allocates an IP address to host during the PXE boot. In accordance with various embodiments of the present invention embedded device has an IP address of its own. Once the IP address is assigned to host embedded device specifies itself as the TFTP server. In order to specify itself as the TFTP server embedded device provides the IP address of its own to host through DHCP protocol in accordance with various embodiments of the present invention.

Further TFTP server responds to TFTP requests made by host during the PXE boot. In accordance with various embodiments of the present invention TFTP server provides PXE GRUB and configuration files corresponding to the selected OS to host . PXE GRUB is a multi boot bootloader that is capable of loading multiple OSs on host .

Network File System server responds to NFS requests made by host during the PXE boot. Similarly SMB CIFS server responds to SMB CIFS requests made by host during the PXE boot. Depending on the OS to be loaded either NFS server or SMB CIFS server can provide a Root File System RFS to host .

In accordance with various embodiments of the present invention DHCP server TFTP server NFS server and SMB CIFS server respond to the requests from host through communication medium .

In accordance with an embodiment of the present invention embedded device can include an Ethernet connector which provides a connection to an Ethernet network. Therefore microprocessor on embedded device can access resources on the Ethernet network during the PXE boot of host . In accordance with an embodiment of the present invention embedded device can act as a network device on the Ethernet network and can be accessed from remote locations.

Next at step embedded device configures DHCP server TFTP server and NFS server to boot host with the OS selected at step . At step embedded device directs host to reboot. In accordance with various embodiments of the present invention embedded device directs host to reboot by power cycling. Once directed host begins to reboot. Thereafter at step a Basic Input Output System BIOS of host loads the PXE loader provided by PXE ROM which initiates the PXE boot.

At step the PXE loader requests boot information from embedded device . In response to this request at step embedded device assigns an IP address to host using the DHCP protocol. Thereafter at step embedded device specifies itself as the TFTP server for the PXE boot. At step the PXE loader requests an executable image from TFTP server on embedded device . In response to this request at step TFTP server delivers PXE GRUB to host . Next at step PXE GRUB requests a GRUB configuration file for the selected OS from TFTP server . In response to this request at step TFTP server delivers the requested GRUB configuration file. Next at step PXE GRUB begins loading the selected OS.

At step PXE GRUB requests a kernel of the selected OS. In response to this request at step TFTP server delivers the requested kernel. Next at step PXE GRUB requests an init RAM disk for loading the selected OS. In response to this request at step TFTP server delivers the requested init RAM disk. Once the requested init RAM disk is delivered the kernel execution begins. At step the kernel requests mount of RFS. In response to this request at step NFS server delivers the requested RFS. The kernel simultaneously completes the boot sequence. The PXE boot is completed when the RFS is delivered completely.

Various embodiments of the present invention embed the functionality of an entire PXE boot server into embedded device . Embedded device contains servers that support all the protocols related to the PXE boot. Therefore there is no need to set up external servers. Further embedded device configures the servers on its own according to an OS that has to be loaded on host . Consequently embedded device provides a consistent PXE boot process to host .

Further embedded device includes storage medium that stores boot images for multiple OSs. Therefore it enables a PXE boot even when host has no storage of its own. Further embedded device can be used to boot a diagnostic program into host if host cannot load its OS due to hardware or software failure. Furthermore it can be used to install an OS into host if host has a clean hard disk. This makes embedded device capable of providing all the functions of a completely self sufficient PXE boot server to host .

The only requirement is for host to be configured to boot through the PXE protocol. No other special configuration is required for host . If host is configured to boot through the PXE protocol communication to embedded device is established through communication medium . Thereafter embedded device controls the boot sequence completely. Further embedded device includes DHCP server which is capable of configuring host for the PXE boot.

Moreover embedded device can be managed from remote locations. Various embodiments of the present invention provide remote reboot and OS selection through a user friendly management interface . Based on an OS selected by a user embedded device configures its servers automatically thereby providing a simple configuration interface.

Embedded device as described in the present invention or any of its components may be embodied in the form of a computer system. Typical examples of a computer system include a general purpose computer a programmed microprocessor a micro controller a peripheral integrated circuit element and other devices or arrangements of devices that are capable of implementing the acts constituting the method of the present invention.

The computer system comprises a computer an input device a display unit the Internet and a microprocessor. The microprocessor is connected to a communication bus. The computer also comprises a memory which may include a RAM and a ROM. The computer system also comprises a storage device which can be a hard disk drive or a removable storage drive such as a floppy disk drive an optical disk drive a flash memory and so forth. The storage device can also be other similar means for loading computer programs or other instructions into the computer system.

The computer system executes a set of instructions that are stored in one or more storage elements in order to process input data. These storage elements may also hold data or other information as desired and may also be in the form of an information source or a physical memory element in the processing machine.

The set of instructions may include various commands instructing the processing machine to perform specific tasks such as the acts constituting the method of the present invention. The set of instructions may be in the form of a software program and the software may be in various forms such as system software or application software. Further the software may be in the form of a collection of separate programs a program module with a larger program or a portion of a program module. The software may also include modular programming in the form of object oriented programming. The processing of input data by the processing machine may be in response to user commands to results of previous processing or in response to a request made by another processing machine.

While various embodiments of the present invention have been illustrated and described it will be clear that the present invention is not limited only to these embodiments. Numerous modifications changes variations substitutions and equivalents will be apparent to those skilled in the art without departing from the spirit and scope of the present invention as described in the claims.

