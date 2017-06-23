---

title: Structure for implementation of back-illuminated CMOS or CCD imagers
abstract: A structure for implementation of back-illuminated CMOS or CCD imagers. An epitaxial silicon layer is connected with a passivation layer, acting as a junction anode. The epitaxial silicon layer converts light passing through the passivation layer and collected by the imaging structure to photoelectrons. A semiconductor well is also provided, located opposite the passivation layer with respect to the epitaxial silicon layer, acting as a junction cathode. Prior to detection, light does not pass through a dielectric separating interconnection metal layers.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07615808&OS=07615808&RS=07615808
owner: California Institute of Technology
number: 07615808
owner_city: Pasadena
owner_country: US
publication_date: 20050913
---
This application claims the benefit of U.S. provisional Patent Application Ser. No. 60 610 830 filed Sep. 17 2004 for a Back Illuminated Visible Imager by Bedabrata Pain and Thomas J Cunningham and U.S. Provisional Patent Application Ser. No. 60 610 831 filed Sep. 17 2004 for Architecture and Methods for High Efficiency Visible Imager Implementation by Bedabrata Pain the disclosure of all of which is incorporated herein by reference in its entirety. This application is also related to U.S. application Ser. No. 11 226 902 for a Method for Implementation of Back Illuminated CMOS or CCD Imagers filed on the same date of the present application also incorporated herein by reference in its entirety.

The invention described herein was made in the performance of work under a NASA contract and is subject to the provisions of Public Law 96 517 35 USC 202 in which the Contractor has elected to retain title.

Current commercial CMOS imagers are front illuminated. shows a vertical cross section of the optical collection part of a front illuminated pixel.

The photodetector comprises an ion implanted cathode on an epitaxial or substrate silicon layer that acts as the anode. The photodetector is mechanically supported by a thick about 0.5 to 0.7 mm silicon substrate in keeping with conventional VLSI micro fabrication paradigm.

The main problem of imaging with a structure as shown schematically in is the increased distance between the point where light enters the system and the silicon where light is detected i.e. converted to photoelectrons. As shown in light has to travel trough many layers of dielectric and interconnect metal layers metal bus lines suffering multiple reflections obscurations and deflections before it is actually collected by silicon. For a small sized pixel the aspect ration between the vertical distance to the photodiode width can be as high as 3 1. This is akin to shining flash light in a canyon. Due to the increased distance between the color filter micro lens and the silicon surface the device suffers from poor collection efficiency low sensitivity low quantum efficiency QE increased cross talk and poor angular response.

QE loss occurs due to a loss of optical fill factor defined as the ratio of the optical collection area to the pixel area especially as the pixel size is scaled. Poor angular response results from the increase in the aspect ratio especially as the pixel size is scaled down as well as from increased unwanted reflections and occultations at metal edges. Increased cross talk is due to a large separation determined by the ILD thickness between the silicon and color filter layers and due to lateral movement of focus point as the angle of acceptance is changed.

In other words the front side illumination structure of suffers from poor QE and angular response uniformity increased optical cross talk and stray light coupling especially as the pixel size is scaled. The addition of an anti reflection coating is nearly impossible because of the presence of multi layers with unfavorable dielectric constants and due to non planarity of the photo collection junction.

Technology scaling actually makes the problem worse since the number of metals and the thickness of ILDs increases with scaling resulting in an even higher skewing of the aspect ratio. Furthermore the introduction of low k dielectric and use of alternate metals e.g. Cu for interconnection is expected to further exacerbate the problems through increased absorption and scattering in the metal dielectric stack.

According to a first aspect a backside illuminated imaging structure is disclosed comprising a passivation layer a silicon layer connected with the passivation layer acting as a junction anode the silicon layer adapted to convert light passing through the passivation layer and collected by the imaging structure to photoelectrons a semiconductor well of a first conductivity type located opposite the passivation layer with respect to the silicon layer acting as a junction cathode and a reflector layer adapted to receive photons passing through the silicon layer and to reflect the photons back to the silicon layer.

According to a second aspect a backside illuminated imaging structure is disclosed comprising a base layer a silicon device layer connected with the base layer wherein light is absorbed in the silicon device layer through a surface of the silicon device layer not connected with the base layer without passing through the base layer and metal pads facing an illumination side of the structure and connected with the surface of the silicon device layer not connected with the base layer.

According to a third aspect a wafer is disclosed comprising a passivation layer a silicon layer connected with the passivation layer the silicon layer comprising a photodiode array adapted to convert light passing through the passivation layer inter layer dielectric connected with the silicon layer and a base connected with the inter layer dielectric.

According to a fourth aspect a light detection method is disclosed comprising providing a junction comprising a junction cathode and a silicon layer acting as a junction anode connecting a passivation layer to the silicon layer on a side of the silicon layer opposite the junction cathode inputting light to the silicon layer through the passivation layer whereby light is detected in the silicon layer and providing a reflector to receive photons passing through the silicon layer and to reflect the photons back to the silicon layer.

According to a fifth aspect an illumination method is disclosed comprising providing a base layer providing a silicon device layer having a first surface not connected with the base layer and a second surface connected with the base layer connecting metal pads with the first surface of the silicon device layer impinging light through the first surface of the silicon device layer and absorbing light in the silicon device layer.

The structure in accordance with the present disclosure is extremely planar and provides a 100 optical fill factor thus providing absence of obscurations. Since light does not have to travel through the thick ILDs to reach the anodic silicon the structure has a low aspect ratio between the vertical and lateral dimension resulting in excellent angular response and low optical crosstalk. Absence of obscurations unwanted reflections deflections and absorption enable imager development with superior angular response sensitivity and QE.

A first advantage of the structure of the present disclosure is high quantum efficiency due to the presence of a 100 fill factor notwithstanding the presence of other MOSFETs near the junction diode.

A second advantage of the structure of the present disclosure is an excellent angular response due to the direct coupling of light into silicon without the presence of obscurations and unwanted reflections from multiple metal layers and ILDs that would have been present if optical illumination would have been carried out through the ILDs as well as due to elimination of the distance between the point where the light enters the device and where it is converted into photoelectrons.

A third advantage of the structure of the present disclosure is an efficient implementation of microlens and anti reflection coatings due to the availability of a planar surface for optical collection.

Further the structure of the present disclosure allows integration of appropriate capacitors and other signal conditioning circuits for electronic shuttering ADC implementation gain ranging and so on. Still further compatibility with next generation metals e.g. Cu and low k dielectrics is provided since in the structure of the present disclosure light does not travel through the ILDs to reach the optical conversion layer.

The photodetector comprises a deep implanted n well acting as a junction cathode and a low doped epitaxial silicon layer acting as the anode. The photodetector is mechanically supported by a substrate . The substrate can be a glass or organic substrate.

Similarly to also shows metal layers for interconnection of circuits and photo detectors fabricated on the epitaxial silicon layer . The metal layers are separated and protected by inter layer dielectric ILD .

The person skilled in the art will notice that in the device according to the present disclosure the light collection point is brought closer to the photodetector.

Next to the junction cathode an additional p type implant can be added to prevent pixel to pixel crosstalk. Further a reflector layer can be embedded in the ILD to provide better red response by making the longer wavelength photons make multiple passes through the anodic silicon . The metal reflecting layer made for example of Al or Cu also prevents long wavelength red crosstalk between pixels by preventing unwanted reflections.

In this paragraph the process for fabricating the metal reflecting layer will be briefly discussed. A CMOS process comprises multiple metal stacks. One of the metal layers will be reserved for implementing the total reflecting layer . The reflecting layer allows to improve red response and red cross talk. The absorption depth of light in silicon increases with increasing of the wavelength of light. Absorption depth refers to the depth at which 63 of the incident light is absorbed and converted into photoelectrons.

The wavelength dependence of absorption is well known and is shown in . It can be seen that the absorption depth is only 0.1 m at 400 m blue light but reaches 5 m at 700 m red light .

If the device silicon is only 3 4 m thick a substantial portion of the red and near infrared light goes through the silicon unabsorbed in the back illuminated imager structure. These photons are then scattered back at different depth from different interfaces e.g. ILD based interface and are then captured by the silicon. These spurious and scattered reflections vastly diminish image quality by generating a number of image artifacts such as ghosting halo from diffuse background image blurring and etaloning.

The presence of the layer in accordance with the present disclosure eliminates these unwanted reflections. The metal reflector layer is patterned and aligned with the pixel structures to provide directed reflection suppressing spurious light coupling. Also being part of the CMOS process these reflectors reside close to the silicon surface. The layer serves two purposes. First it reflects back unabsorbed light from close to the silicon surface so that it may be quickly absorbed in the device silicon increasing the red sensitivity. Secondly by being close to the device silicon layer and providing a highly reflective surface it provides directed reflection and suppresses scattered and spurious reflection improving picture quality. The presence of a layer works best with a microlens on top that focuses the light to a small known spot.

Back illuminated imagers are known as such. As shown in those imagers are implemented with a silicon device layer functionally similar to the silicon layer of mounted on a transparent substrate with metal bonding pads residing on the frontside of the chip. The transparent substrate provides mechanical support and has therefore a thickness of several hundreds m. Light passes through the transparent substrate before getting absorbed in the silicon imager residing underneath it. Since the metal pads reside on the side opposite to that where light enters the imager a non standard packaging scheme must be used.

The structure of provides several advantages. A first advantage is that the conventional structure of light has to pass through hundreds of m of transparent material before getting absorbed in the silicon layer . This results in greatly reduced angular response and vastly degraded optical cross talk. In the structure of there is no spacer between the entrance point of light and its collection point. Elimination of the spacer is important to improved angular response and prevention of optical cross talk.

A second advantage is that the thickness of the spacer material in the conventional structure makes it impossible to apply and align color filters anti reflection coatings and or microlens. By eliminating the spacer the structure of enables very efficient color filter anti reflection coating and microlens integration both in terms of optical performance and ease of alignment.

A further advantage is that in the structure of the metal pads reside on the same side of light entrance. Thus the structure of is fully compatible with standard packaging schemes and processes enabling a low cost and reliable solution.

The above mentioned approach suffers from two limitations. First lack of appropriate etch stops results in uncontrolled p layer thickness. Etching of silicon is done either as a timed etch or through the use of a dopant selective etch stop. Since the ratio of the starting thickness of the p substrate to the final p layer thickness is very high about 50 100 it is very difficult to reliably produce the final structure right side of with uniform and accurately controlled p layer thickness. The latter approach suffers from the availability of appropriate dopant selective silicon etches.

Secondly the approach of can result in an unwanted imaging structure. Due to high temperature processing inherent in silicon micro fabrication the interface between the p substrate and the p epitaxial layer is not sharply defined as the schematic cross section of the left portion of may appear to imply. The smearing of dopants at the interface results in unwanted doping of the p layer causing a loss of imaging performance. In addition this smearing also impairs the ability to generate a p layer accurately controlled thickness since a dopant selective etch stop would have required an abrupt doping transition from the p substrate and the p epitaxial layer .

Further after thinning the interface trap density at the unterminated silicon surface is unacceptably high while a naturally formed native oxide about 20 thickness causes the surface to become positively charged. Unwanted band bending and the presence of dangling bonds result in a loss of QE and unacceptably high dark currents rendering the structure shown in incapable of being used for imaging.

Surface passivation of the structure shown in presents its own set of unique problems. Since the thinning and passivation can be being carried out as a post metallization process step high temperature 400 C. processing steps should not be allowed since the front side can already be covered with low melting point metals e.g. Al . Therefore in such cases surface passivation through implantation cannot be used since implant activation requires high temperature anneal.

To overcome this problem refractory metals and multiple polysilicon layers can be used for interconnection. However such techniques are not compatible with a CMOS process flow that uses metals with low melting points. Other passivation techniques include UV flooding flash gates MBE deposited monolayer of metal boron doping followed by high energy pulsed laser anneal low pressure oxide deposition and delta doping through molecular beam epitaxy MBE .

The above mentioned processes are complex and require non conventional tools making them incompatible with high volume silicon microfabrication and causing severe loss of reliability and yield. Thus it is typical for CCD thinning to be carried out at die level and not at the wafer level and is one of the main reasons why backside illuminated imagers could suffer from poor reproducibility yield and reliability issues.

The following paragraphs will present a method which overcomes the above problems and is equally applicable for CCD or CMOS imager implementation.

Use of a new starting material with a pre passivated silicon surface. Pre passivation is carried out by growing SiOon the silicon surface.

Use of an accurate etch stop. The structure comprises a buried oxide layer that acts as an accurate etch stop for silicon. For instance the etching rate of silicon with TMAH tetramethylammonium hydroxide at 90 C. is four orders of magnitude higher than that of SiO.

Protection of the backside silicon surface. In the process according to the present disclosure backside etching stops at the buried SiOthat sits on top of the device silicon where the imager resides . Since the device silicon is never exposed during the thinning process the silicon surface is protected from the deleterious effects of etching. Thus unlike conventional backside thinning approaches no interface traps are created on the silicon backside as a result of backside etching. Thus in the approach according to the present disclosure there is no need for post thinning passivation of the backside solving one of the major problems of backside illuminated imager implementation.

In accordance with the embodiment of instead of using a conventional bulk CMOS wafer comprising a p epitaxial layer grown on a heavily doped p type substrate a special silicon on insulator SOI wafer is used.

Although starting with a SOI wafer a conventional bulk CMOS process flow is used to generate CMOS imagers through implantation oxidation ILD metal deposition and patterning at wafer level. Any bulk CMOS process can be used for example a bulk CMOS process optimized for imaging. After CMOS fabrication the structure shown in is obtained where a device layer and ILD are also shown.

In order to prepare for backside illumination the structure is bonded to a glass wafer for mechanical support as shown in .

In the step shown in the silicon handle wafer is removed through mechanical grinding wet etching and or RIE etching reactive ion etching for example. The buried SiOlayer provides a natural etch stop generating a uniformly planar back surface.

In addition the resultant structure is self passivated since it comprises a thermally grown Si SiOinterface that will be exposed to light during imaging. Termination of silicon by the oxide layer renders additional passivation unnecessary eliminating the need for additional passivation that could not only difficult to achieve but also incompatible with standard VLSI processing. Since the passivation is automatic resulting from the use of starting material the process flow described in is fully CMOS compatible and can be carried out at the wafer level.

Furthermore since the device silicon is separated from the handle wafer through the buried oxide no unintentional doping of the device silicon occurs during CMOS processing. Thus it becomes possible to choose appropriate doping of the device silicon layer during the time of starting material selection without it being altered by processing steps. This is particularly critical since high charge collection efficiency minimization of the field free region requires lower device silicon doping that is difficult to achieve in bulk CMOS wafer that has undergone a bulk CMOS process.

Given the silicon thickness a bulk CMOS process is preferably used for fabrication of the devices in accordance with the present disclosure although the wafer is of SOI type. The use of a bulk CMOS process is advantageous since all state of the art CMOS imager processes are of the bulk CMOS type. Thus the structure in accordance with the present disclosure enables high quality CMOS imager implementation by mixing two diverse elements the application of a bulk CMOS process on a new SOI type starting material.

Turning to following a bulk CMOS process flow the imager array and the support electronics circuits are fabricated as follows. All MOS devices reside in the n well and p well that are implanted from the front side. Devices are isolated from each other by using isolation oxides thermal and or deposited in form of LOCOS or STI shallow trench isolation structures. shows an STI isolation structure with STI elements . In the process the photodiode is also formed between the n well and the p type device silicon layer.

Following the above steps the gate oxide is grown followed by MOSFET polysilicon gate deposition and patterning. The source drain S D implants N P are carried out in a self aligned fashion aligned to the respective polysilicon gates to complete the MOSFET formation. The FETs in the pixels are labeled S Select FET R Reset FET and S Source follower FET . The pixel circuit is shown in .

As shown in the cathode of the photodiode or the n well is connected to the source of the R FET. The S D implants e.g. and gates are connected by metal lines that are separated from each other and the silicon by deposited ILD stacks that are typically comprised of oxides and nitrides.

While several illustrative embodiments of the invention have been shown and described in the above description numerous variations and alternative embodiments will occur to those skilled in the art. Such variations and alternative embodiments are contemplated and can be made without departing from the scope of the invention as defined in the appended claims.

