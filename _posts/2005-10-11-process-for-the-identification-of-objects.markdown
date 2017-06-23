---

title: Process for the identification of objects
abstract: The invention is a process for identifying an unknown object. In detail, the process includes the steps of: 1) compiling data on selected features on a plurality of segments of a plurality of known objects; 2) illuminating the unknown object with a laser radar system; 3) dividing the unknown object into a plurality segments corresponding to each of the segments of the known objects; 4) sequentially measuring selected features of each of the plurality of segments of the unknown object; and 5) comparing the sequentially measuring selected features of each of the plurality of segments of the unknown object to the selected features on the plurality of segments of the plurality of known objects.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07627170&OS=07627170&RS=07627170
owner: Northrop Grumman Corporation
number: 07627170
owner_city: Los Angeles
owner_country: US
publication_date: 20051011
---
This invention was made under US Government Contract No. FZ6830 01 D 002 issued by the US Air Force dated March 2004. Therefore the US Government has the rights to the invention granted thereunder.

The invention relates to the field of identification of objects such as structures and vehicles and in particular to a process for the identification of structures and vehicles using laser radars.

The identification of targets under battlefield conditions is a major problem. Of course direct visual contact by trained personnel is the most accurate but this exposes them to possible attack and significantly increases personnel workload. Thus in recent years the use of unmanned surveillance vehicles particularly unmanned aircraft have been used for battlefield surveillance. However to avoid constant monitoring of the unmanned vehicle they are being equipped with autonomous systems that identify and classify potential targets and only inform the remotely located operator when such a target is identified.

Traditional Laser radar identification techniques have limitations in identification of articulated targets because of the large number of potential target states due to the large number of potential target articulation variations and pose. The utility of invariant features for the model based matching of the entire target will reduce the search space but will not yield reliable estimates of target identification and pose. One approach is use a laser radar system to map the vehicle and record invariant parameters. These observed parameters are compared to those stored in a data base to find a match. However this method has proved to be cumbersome to implement because the whole structure typically vehicles such as tanks or missile launchers had to be compared to every other structure in the data base.

Thus it is a primary object of the invention to provide a process for the identification of objects without human intervention.

It is another primary object of the invention to provide a process for the identification of unknown objects without human intervention that uses a laser radar for illumination.

It is a further object of the invention to provide a process for the identification of objects without human intervention that uses a laser radar for illumination and which provides optimum identification with minimum computing time.

The invention is a process for identifying an unknown object. In detail the process includes the steps of 

The novel features which are believed to be characteristic of the invention both as to its organization and method of operation together with further objects and advantages thereof will be better understood from the following description in connection with the accompanying drawings in which the presently preferred embodiment of the invention is illustrated by way of example. It is to be expressly understood however that the drawings are for purposes of illustration and description only and are not intended as a definition of the limits of the invention.

The invention is a process for identifying potential targets by means of a laser radar system that does not require human involvement. It is designed for use on an unmanned surveillance vehicle. This process is used after the vehicle has determined that a potential target exists.

In surveillance mission the unmanned vehicle is sent to a target area based on cues from intelligence gathered or cues from other long range surveillance platforms. Due to target location error and potential target movements the unmanned vehicle needs perform its own search upon arrival to the target area using wide footprint sensors such as Synthetic Aperture Radar SAR or wide field of view Infrared Sensor. Upon detection of potential regions of interest ROIs the Laser Radar sensor is then cued to these ROIs to re acquire and identify the target and select the appropriate aim point to enhance weapon effectiveness and reduce fratricide due to enemy fire.

Thus once the normal vectors for the two points P Q are determined the other invariant features are determined. Only those invariants that have normal vectors between two points between 80 and 100 degrees are used. This will significantly reduce computational complexity and reduce the classification ambiguities due to excessive data.

Referring to the library is loaded into a computer on an aircraft having a laser radar . When an object of interest for example the tank shown in but unknown to the computer on broad the aircraft the computer will analyze the object in the following manner. Preferably the aircraft should be at a 30 to 60 degree depression angle to the unknown object.

In the first case no further processing is required. In the second and third case the process can be terminated with a conclusion of no identification possible. Some targets are very similar such BTR 60 BTR70 and BTR 80 trucks . The classifier based on the laser radar resolution may not be capable to detect adequate details to discriminate among these target types. Therefore if the classification belongs to an ambiguous class then there will be a request for refined sensor resolution. A sensor modality change is requested to change resolution and re image and re segment the target area again. The segmented target is then fed to the software to resolve ambiguity among the similar targets. The corresponding model of the target with the computed articulation state is used to render the model using the sensor parameter file and Irma system Government multi sensor simulation that is used to simulate target signatures from target models and sensor parameters . The simulated target signature is compared with the sensed target for final validation.

Additionally the process starting at Step can be repeated starting with the top segment and working downward to achieve a higher confidence level. It may also establish the identification of a target object when the process measures from the top down. This is because the bottom segment may be obscured by mud or foliage.

The process can also be used to assess battle damage or variation to a given target segment by computing a transformation which consists of rotation and translation to compare the target piece to the model piece. The transformation equation is 9 Where 

Thus it can be seen that the process can be used to identify object of interest such as vehicles missile launchers. Tests results provided in C and D have confirmed that the process can identify a great many objects with great accuracy. Note that certain results that have been encircled and identified by numerals A B C and D indicate very low probabilities of error in the 10 percent range.

While the invention has been described with reference to a particular embodiment it should be understood that the embodiment is merely illustrative as there are numerous variations and modifications which may be made by those skilled in the art. Thus the invention is to be construed as being limited only by the spirit and scope of the appended claims.

