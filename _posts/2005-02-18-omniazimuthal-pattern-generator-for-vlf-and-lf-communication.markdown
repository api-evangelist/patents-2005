---

title: Omni-azimuthal pattern generator for VLF and LF communication
abstract: A relative phase shift is induced in the signals of a pair of identical orthogonal antennas such that when the signals are combined the signals are 90 degrees out of phase. This is done in order to eliminate the null along the axis between the two dipole moments of the antennas such that the system has equally good reception from all azimuth angles over a broad range of frequencies. The phase shift is accomplished with the use of single pole operational amplifier circuits whose pole frequencies are adjusted by means of a potentiometer prior to implementation of the antenna system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07106269&OS=07106269&RS=07106269
owner: The United States of America as represented by the Secretary of the Navy
number: 07106269
owner_city: Washington
owner_country: US
publication_date: 20050218
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without the payment of any royalties thereon or therefore.

The present invention relates to antennas and more specifically to the elimination of the null along the axis coincident with the dipole moment of an antenna.

Electrically small antennas possess a pattern in azimuth that has a null along an axis coincident with the dipole moment of the antenna. This null renders the antenna blind along that axis. If two antennas are used and the signals are combined a null occurs along an axis between the two dipole moments. An ideal antenna system would be one capable of rendering equally good reception from all azimuth angles without a null in the antenna pattern s .

It is possible to remove the null in the azimuthal response of a pair of identical orthogonal antennas by combining the two signals together ninety degrees out of phase. Adding the two signals in phase only causes the null in the azimuth pattern to shift to a position midway between the dipole moments of the two antennas.

In the past it has been quite easy to introduce a 90 degree phase shift at only a single frequency by the use of a simple single pole electrical network. The disadvantage is that over a broad range of frequencies the user has to retune the circuit every time the frequency of operation changes. The challenge is to accomplish a ninety degree phase shift between two identical orthogonal antenna signals and be able to do so over a broad range of frequencies for example from 10 kHz to 200 kHz without exceeding a 3 dB pattern deformation.

It is a general purpose and object of the present invention to generate an antenna pattern that does not change as a function of azimuth angle but has equally good reception from all azimuth angles.

It is an additional purpose to generate such an omniazimuthal antenna pattern over a broad range of frequencies in a manner that does not require manual retuning or adjustment.

These objects are accomplished through the introduction of a relative phase shift in a pair of identical orthogonally mounted loop antennas whereby operational amplifier circuits in a network within the antenna system are all single pole circuits with the pole frequency of the single pole circuits being adjustable by means of a potentiometer.

The omni azimuthal pattern generator is designed to work with the AN BRA 34 V and OE 538 BRC VLF LF loop antennas. It is not however limited as such and can be scaled and applied to other frequency ranges of interest. Inside each of these antennas are two identical orthogonally mounted loop antennas called the Fore Aft F A and Athwart ATH loops. Referring now to the equivalent representation of the identical orthogonal antennas F A and ATH is illustrated. The outputs of each of these antennas is amplified in the antenna housing and presented as a balanced twisted pair transmission line.

Referring now to there is illustrated a block diagram of the four stages of the omni azimuthal pattern generator . The first stage is the differential driver stage . The two balanced twisted pair transmission lines from the orthogonal antennas F A and ATH enter the omni azimuthal pattern generator at the differential driver stage at the points denoted F A HI F A LO ATH HI ATH LO . The next stage is the all pass network so called because it has approximately unity gain over a wide frequency range. The all pass network introduces a relative phase shift of 90 degrees between the two antenna signals. The signals are then combined in the combiner stage . In the final stage the drive stage the combined signal is amplified. The resulting output of the omni azimuthal pattern generator is an OMNI HI signal and an OMNI LO signal.

Referring now to there is illustrated a circuit diagram of the differential driver stage . Operational amplifiers and and associated resistors serve as isolation amplifiers and to convert the balanced input into an unbalanced signal for subsequent conditioning.

Referring now to and there is illustrated in a single building block circuit of the active all pass network consisting of an operational amplifier a potentiometer R a resistor R a capacitor Cand other circuit elements. In there is illustrated the entire all pass network consisting of two parallel sets of three of the single building block circuits in series labeled B to B. As stated above the active all pass network introduces a relative phase shift of 90 degrees between the F A leg of the circuit along the top three building block circuits B B B and the ATH leg of the circuit along the bottom three building block circuits B B and B. A relative rather than absolute phase shift is sufficient since the absolute phases of the signals are unimportant. The building block circuits B to B in the all pass network are all single pole circuits with the pole frequency being adjustable by means of a potentiometer R.

By cascading the several building block circuits the phase shift from input to output of each leg of the all pass network can be derived as follows 2 arc tan 2 2 arc tan 4 2 arc tan 6 2 2 arc tan 1 2 arc tan 3 2 arc tan 5 2 

Here the pN represent the pole frequencies of each of the six building block circuits B to B of the all pass network. The pole frequencies in these equations are expressed as angular frequencies. When the two signals are subtracted the resulting phase difference between the F A and ATH legs of the all pass network will be 2 arc tan 1 arc tan 2 arc tan 3 arc tan 4 arc tan 5 arc tan 6 4 

By proper selection of the pole frequencies of each of the building block circuits B to B it is possible to tailor this response to provide a value of that is close to 90 degrees over the frequency band of interest.

Potentiometers Rare utilized in B through B to calibrate the all pass network before it is used. This is critical to ensure that the pole frequencies are correctly set so that proper operation of the circuit over the VLF LF band is maintained. The test points TP to TP in allow a dual channel digitizing oscilloscope not shown to be connected in order to set the pole frequencies precisely by means of the potentiometers Rin B to B.

Referring to there is illustrated the circuit diagram for the combiner stage . The operational amplifier combines the outputs from the all pass network .

Referring to there is illustrated the circuit diagram for the drive stage . The driver and associated components provide a balanced 50 Ohm output in the form of an OMNI HI and OMNI LO signal.

The advantages of the present invention over the prior art are that the current invention is more lightweight. It is more compact than prior art devices. It does not require elaborate external drive circuitry. It uses no moving parts and requires no user intervention to operate.

