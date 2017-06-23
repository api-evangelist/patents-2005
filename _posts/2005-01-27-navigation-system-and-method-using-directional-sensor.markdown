---

title: Navigation system and method using directional sensor
abstract: An apparatus for determining a position includes a source which transmits a signal having a source position and a transmission time coded therein. A sensor having a directional beam pattern is positioned at the location of interest. A signal processor steers the directional beam pattern of the sensor in order to determine the direction to the signal source. A sensor processor uses a clock to find a receipt time of the signal. The transmission time and source position is decoded from the signal. The position of interest is calculated from the receipt time, transmission time, direction, and source position. A method is also provided.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07106658&OS=07106658&RS=07106658
owner: The United States of America represented by the Secretary of the Navy
number: 07106658
owner_city: Washington
owner_country: US
publication_date: 20050127
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without the payment of any royalties thereon or therefor.

This invention relates to a method and apparatus for vehicle navigation. More specifically the invention relates to a method and apparatus for obtaining navigational information in an underwater vehicle using a single vector sensor on the vehicle and a single transducer positioned in the environment.

Obtaining precise navigational coordinates is a longstanding problem in underwater vehicles. Conventional global positioning systems GPS rely on radio wave reception from satellites to establish navigational coordinates but bodies of water block all but the lowest radio frequencies. Accordingly underwater vehicles must either surface an antenna or find some other method for obtaining navigational information.

Acoustic pressure sensing hydrophones are commonly used in manned and unmanned underwater vehicle applications. These non directional sensors receive sound equally from all directions. To obtain directivity the hydrophones are configured in an array consisting of many elements. The array assembly feeds acoustic information to signal processors for creating beam patterns that have directionality. The directionality of the beam is controlled by the relative size of the array to an acoustic wavelength. Thus higher frequency acoustic wavelengths are used to increase the directionality. The useful frequency band of the array in a small vehicle such as an unmanned vehicle is limited to high frequencies however these high frequencies attenuate over a short distance thereby reducing the useful navigation capabilities.

Acoustic vector sensors have been developed which measure non directional acoustic pressure and vector acoustic velocity components of an acoustic signal. Three vector acoustic velocity components are measured orthogonally. These vector components can be electronically steered to provide increased or decreased sensitivity at a given location.

One current underwater navigational system uses a single omnidirectional pressure sensor on a vehicle and four transponders. Utilizing technology known as hyperbolic multilateration one can get an x y z position fix from the range to each transponder. This technique is similar to that used in the Global Positioning System GPS . However the system is limited to a relatively high frequency 7 kHz to 40 kHz which reduces the operational range from the transducers.

Another current navigational system uses a high frequency array of sensors on the vehicle. Two transponders must be positioned in the environment to get an x y and z position fix. Triangulation is used to obtain directional information to the transponders. The frequency used is greater than 20 kHz limiting the range. This system is expensive because of the needed array.

Another known navigational system utilizes a GPS buoy which acts as a relay to communicate to underwater vehicles by using an acoustic communication link. This system requires deployment of the GPS buoy within communication range of the underwater vehicle. The GPS buoy is further limited by the existing surface sea state.

This invention provides an apparatus for determining a position. The invention includes a source which transmits a signal having a source position and a transmission time coded in the signal. A sensor having a directional beam pattern is positioned at the location of interest. A signal processor steers the directional beam pattern of the sensor in order to determine the direction to the signal source. A sensor processor uses a clock to find a receipt time of the signal received by the sensor and decodes the transmission time and source position from the signal. The position of interest is calculated from the receipt time transmission time direction and source position. A method is also provided.

As provided this invention utilizes low frequency sensors to determine the position of an acoustic source in order to estimate the range bearing and elevation angle of the source from the directional receiver.

As an alternative the null of the beam pattern can be steered toward the transponder . This may be advantageous because the null represents a sharp signal reduction whereas the signal fades gradually on either side of lobe . The bearing and elevation of the steered null are the bearing and elevation from the vehicle to the transponder. is shown in two dimensions for clarity but this analysis will be preferably applied using three dimensions.

The received signal is decoded at the sensor processor to find the known location of the transponder and the time of transmission. The range from the sensor to the transponder can be calculated from the difference between the sensor processor clock and the time of transmission. Salinity and temperature information at the sensor the source or both to enhance the accuracy of the calculation by more accurately providing the speed of sound in the environment. The vehicle s position is calculated from the known transponder coordinates the range the bearing angle and the elevation angle.

The transponder can transmit its signal using any known modulation selected from phase modulation frequency modulation amplitude modulation or intensity modulation. Multiple transponders can be provided having different modulations. The transponders can transmit information other than coordinates and time. The transponders can be positioned on the surface bottom or intermediate in the environment. A drifting or mobile transponder can receive GPS information from a satellite and encode this information for transmission.

