---

title: Through-the-wall frequency stepped imaging system utilizing near field multiple antenna positions, clutter rejection and corrections for frequency dependent wall effects
abstract: Lower resolution and clutter-prone two-tone CW radars can have the displayed images dramatically improved by three techniques involved in the subject invention. The three techniques involved are the stepping of each of the multiple radars for readings at multiple frequencies, weighting the results to compensate for wall-induced distortions and differential image processing. In one embodiment, weights for each frequency counteract the distortion produced by particular wall. For differential image processing, temporal snapshots of the images are subtracted one from the other such that the result is only due to moving objects, thus to provide a dramatic display of the presence and position of moving individuals behind a wall.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07307575&OS=07307575&RS=07307575
owner: BAE Systems Information and Electronic Systems Integration Inc.
number: 07307575
owner_city: Nashua
owner_country: US
publication_date: 20050620
---
This application is a continuation in part of U.S. patent application Ser. No. PCT US2004 036446 filed Nov. 2 2004 entitled Dual Frequency Through the wall Motion Detection and Ranging Using Difference Based Estimation Technique which is a continuation in part of U.S. patent application Ser. No. PCT US2004 030116 filed Sep. 14 2004 the contents of which are incorporated herein by reference.

The invention was made with United States Government support under Contract Grant No. N39998 97 C 5216. The United States Government has certain rights in this invention.

This invention relates to through the wall sensors and more particularly to the improvement on accuracy for those through the wall sensors using two tone CW radars by frequency stepping the radars weighting the results and detecting motion through differential image formation techniques.

As described in PCT Patent Application Ser. No. US2004 036446 filed Nov. 2 2004 entitled Dual Frequency Through the wall Motion Detection and Ranging Using Difference Based Estimation Technique invented by Paul Zemany and Eldon Sutphin and as described in patent application Ser. No. 11 121 787 filed May 3 2005 multiple dual frequency radars spaced about a building have been used to localize the position of a moving individual in the building so as to provide information about the whereabouts of personnel whether it is for the purpose of rescue such as for firefighters EMTs and the like or to pinpoint enemy personnel in a building.

The above patent applications incorporated herein by reference and assigned to the assignee hereof describe the use of a multi tone set of radars that detect and define the range to a moving object behind a wall with triangulation techniques used to detect and track the moving object as it moves within the building or behind a wall.

Multi tone CW radars are used in which the two tones are fairly close together with it being possible by analyzing the returns from moving objects to determine the range of the object to the various radar transmitters. By using multiple transmitters one can triangulate to be able to pinpoint the individual within the structure from the outside of the structure.

While the systems described in the above mentioned patent applications work very well to detect the presence of a moving object and to detect its range and in fact its location various problems nonetheless exist due to a number of factors not the least of which is the fact that the wall of an edifice of building has material that differently affects radar beams at different frequencies due to the frequency dependent difference in attenuation. It will be appreciated that in synthetic aperture radars the angular resolution is given by d where is the wavelength and d is the length of the baseline on which the measurement is to be made. However resolution is critically dependent on pulse shape and with pulse shape altered by wall materials image resolution is adversely affected. There is therefore a requirement to take into account wall density and material to improve image accuracy.

Note that with both range and angle information 2D representation consisting of range and azimuth pixels can be formed. Note also that if the baseline has both horizontal and vertical extent 3D representation is possible. In this case each cell represents range azimuth and elevation. However without correction these representations will be fuzzy due to the alteration of the pulse shape as the pulses pass through the wall.

In general frequency bandwidth provides range resolution and the baseline geometry provides angle resolution. The quality and or details contained in the image depends on the bandwidth baseline range wall distortions wall uniformity and wall absorption. In addition the quality of the image depends on the position accuracy and velocity measurements.

Thus due to the variability of wall transmissivity the range measurements are coarse at best and it is only with difficulty that one can establish an accurate range to a moving object behind a wall.

If use could be made of the fact that the interaction of objects and RF energy is linear in the amplitude domain one could potentially improve upon range accuracy by adding the amplitude response caused by a first signal to the amplitude response caused by a second signal to get the response caused by a signal that is the sum of both signals. As will be seen because of this linearity in amplitude it would be possible to use a set of closely spaced frequency stepped CW measurements taken at widely different frequencies and closely spaced points to provide improved resolution.

Moreover all of the above multi tone through the wall radars require object movement to obtain range. There are however returns from non moving objects that complicate analysis of the returns. Thus artifacts from non moving objects can corrupt the display of returns from moving objects.

Thus while it is indeed useful to be able to ascertain whether or not a person is within a building due to the detection of their movement and while it is also useful to pinpoint to the extent possible their position and track using multiple multi tone CW radars there is nonetheless a requirement to obtain more precise measurements and more accurate tracks while at the same time distinguishing other artifacts in the room such as chairs desk tables and lamps etc. These artifacts are in general non moving so that theoretically one should be able to distinguish a moving object from one that is not.

In the subject invention a through the wall frequency stepped imaging system uses near field multiple antenna positions clutter rejection and corrections for frequency dependent wall effects to improve accuracy and readability of through the wall CW radars. The subject system uses frequency stepped radars to obtain multiple readings at different frequencies with the more frequencies sampled the higher the location accuracy. Secondly a weighting system is provided that corrects range measurements for the characteristics of the particular wall. Thirdly a differential image technique rejects clutter that is the result of returns from non moving objects.

More particularly in order to ameliorate the effects of different wall thicknesses and materials the system steps the frequency of the radars and applies a weight for each frequency to correct for pulse distortions through the wall. The result is that the subject system minimizes the problem of the dispersive frequency dependent effects of the wall. When using stepped frequencies one must compensate for wall induced effects at each frequency because in typical broadband pulses there is a considerable difference between what happens at the low end of the pulse frequency spectrum and the high end.

In the subject frequency stepping system one applies a correction for each frequency step that inverse weights the effect of the wall and resharpens the pulse. The result is a much better defined range since the result for each of the stepped frequencies in maximized with the process being performed at each antenna position. Thus the system is able to obtain better range measurements from which the system triangulates and renders an indication of the position of a moving individual.

In one embodiment the optimal weights as a function of frequency are determined knowing wall thickness and the index of refraction of the wall. These can either be input from measurements or be estimated.

Alternatively an auto focus system is provided in which trial wall thicknesses and indices are input to an auto focus program. When focus has been achieved that wall thickness and index leading to the focus condition yield the wall thickness and index that actually exist. This wall thickness and index can then be used in the above algorithm to generate the aforementioned weights.

Having applied predetermined weights for each frequency the use of multiple frequencies for each pair presents the ability to provide an even more accurate range measurement. Note with two frequencies of the two tone radars one can obtain a range solution. With multiple two tone frequencies one can get multiple solutions for each two tone pair that can be averaged to obtain more accurate results.

Moreover multiple stepped frequencies can be used to reduce range ambiguities. For instance one pair of frequencies can be selected to be widely separated to provide fine spatial resolution. However with wide separation comes range ambiguity. However at the same time other separations can be made close together to resolve the range ambiguity.

For instance if for a given radar one chooses one of the two tones F to be 900 MHz and the other of the two tones F to be 910 MHz this provides a 15 meter range cell which is 30 meters divided by 4.

On the other hand for this radar choosing an additional frequency F to be 920 MHz this provides a 7.5 meter range cell thus improving the resolution.

One then uses the F F spread to obtain the high resolution albeit with range ambiguity. One then uses the F F spread to resolve the ambiguity.

Thus by using multiple stepped frequencies for the two tone radars one can obtain better resolution by averaging or one can get higher resolution range results using wide frequency spreads with range ambiguities resolved by narrower frequency spreads.

The net total result is improved resolution either by the weighting system or by the use of multiple frequencies and different frequency spreads.

Having improved the resolution of a two tone CW radar substantially by readings at multiple frequencies and taking into account wall effects the system goes further to subtract out clutter that is the result of returns from non moving objects. This is accomplished by producing two images at two different times and subtracting one from the other. What remains after the subtraction is only that which is due to a moving object. This permits distinguishing non moving objects such as furniture lighting and non moveable objects from moving objects such as an individual moving behind the wall.

The result is that one takes an image that has been generated using corrections for frequency dependent wall effects and provides a display in which the only returns that are displayed are the differences between two snapshots or images formed at two different times. This allows the system to process out clutter because the images that are generated result only from moving objects. It will be appreciated that the images at two different instants of time initially include all returns from objects whether they are moving or not. Since one is only interested in moving objects such as people moving in a room or behind a wall displaying only the difference between the two temporal images represents only objects that are in motion. The result is that one can readily distinguish moving objects from stationary objects.

As to range accuracy improvement processing at multiple frequencies using the above mentioned weights increases the accuracy obtainable from non compensated systems by as much as 50 .

This coupled with the ability to distinguish returns from non moving objects when rendering position provides for an exceptionally robust through the wall radar capable of localizing and tracking individuals in a very precise manner as they move behind a wall.

In summary the lower resolution and clutter prone two tone CW radars described above can have the displayed images dramatically improved by the three techniques involved in the subject invention. The three techniques involved are the stepping of each of the multiple radars for readings at multiple frequencies weighting the results to compensate for wall induced distortions and differential image processing. In one embodiment weights for each frequency counteract the distortion produced by particular wall. For differential image processing temporal snapshots of the images are subtracted one from the other such that the result is only due to moving objects thus to provide a dramatic display of the presence and position of moving individuals behind a wall.

To describe the operation of the multi tone CW radar used in the subject invention it was found that for an object exhibiting constant motion or velocity the phase shift between the two waveforms representing the phase difference between transmitted and returned waves for the two tones or frequencies is directly related to range. This is because comparing waveforms corresponding to the phase difference between the outgoing and incoming waves at the two frequencies results in a relationship between the phase shift between the two waveforms and range. For instance at zero range there is no difference in phase between the two waveforms. At a range equal to 4 one has a 180 phase shift between the two waveforms. In between for constant motion objects there is a linear relationship between phase shift and range such that by measuring phase shift between the two waveforms one can deduce range. Here is the wavelength associated with the difference in fand f or in this case one megahertz.

However in reality individuals rarely maintain a constant velocity and it can be shown that the subject system can measure range to objects having a pseudo random motion.

In order to determine range for random motion the two tone CW radar used for constant motion is used to drive a single antenna. Here continuous waves at the two frequencies fand fare simultaneously applied to the antenna. The system measures the phase difference between the returned versus transmitted energy for the first tone fand the second tone f. This results in two waveforms each specifying the temporal phase difference for the two respective tones. In the constant motion case the phase shift between these two waveforms indicates the range from the antenna to the moving object.

In order to accommodate the usual situation in which the object s motion varies over time a model based signal processing algorithm extracts range by comparing the waveform corresponding to the time sequence of phase differences for the detected returns at one of the frequencies with the predicted waveforms corresponding to the predicted phase differences for the other frequency at a number of ranges with the waveform closest to that which is detected being declared as the range to the moving object.

Due to the use of a model based system movement is not limited to constant velocity or to large movements compared to the carrier wavelength meaning that even slight hand movement can be sensed.

The model is populated by selecting the first and second tones and setting their frequencies apart by for instance one MHz. For one frequency f one samples the mixer output used to provide a signal corresponding to the phase difference between outgoing and incoming energy. The output of the mixer thus produces a time sequence waveform corresponding to the phase difference between outgoing and incoming waves at f. This fwaveform is used by a predictor involving a mathematical model that predicts the time sequence waveform for fbased on information from ffor an a specific range value. The other input to the predictor is range. The model is built up in terms of generating stored waveform templates by sequencing through a number of ranges to produce a set of range dependant templates each keyed to a given range. The time sequence waveform for fcorresponding to the phase difference between outgoing and incoming waves from real time data is then compared to the predicted time sequence waveform for fto ascertain which template and thus which range offers the best fit. Optimal search methods can be employed to obtain the range value R that gives the best fit.

Thus it is possible to determine range to the motion even if the motion is not constant or the target moves only a fraction of the carrier wavelength.

For random motion the system provides not only an indication of the existence of an individual but also determines the range to the individual by first developing range templates or using an iterative search to find the best range value and by comparing the data associated with real time returns to the templates with a matching algorithm determining range.

The range templates in one embodiment are generated by a predictor that predicts from one waveform corresponding to the phase differences for the first tone namely f the predicted phase differences for the second tone.

The predictor algorithm is based on using the time domain signal or temporal waveform corresponding to the temporal phase difference between outgoing and reflected energy at favailable from a mixer for fto predict the temporal phase difference waveform between outgoing and reflected energy at favailable as a signal produced by a mixer for f. To describe this the following are defined 2 Equation 1 2 Equation 2

The output of the mixer caused by the energy reflected from the moving target is for mixer 1 Equation 3 for mixer 2 Equation 4 obtained by substitution Equation 5 The above equation predicts waveform Y t using the difference between kand kand the range r t .

Here it can be seen that one can predict the expected temporal phase difference waveform for ffrom the measured phase difference waveform for f.

By having a predicted waveform for the temporal phase differences of f one can compare this waveform with a waveform generated from the measured actual phase differences at f 

Since the predictor generates predicted waveforms at various ranges when the waveform generated from measured data is compared with one of the predicted waveforms a match indicates the range to the moving object.

If the comparison results in a significant disparity between the two waveforms one can adjust the range input to the predictor to generate another predicted waveform for f. When this newly generated waveform is compared to the waveform associated with measured data assuming a closer match the range associated with the newly generated predicted waveform is determined to be the actual range of the moving object.

It will be appreciated that the phase shift between the waveforms replicates at intervals of 4 where in this case is the wavelength of the difference frequency. In general a difference between fand fof one MHz corresponds to a of about 300 meters. 4 thus corresponds to 75 meters and is termed a range cell. Returns from moving objects outside of the range cell that would duplicate those inside the range cell can be distinguished in terms of the amplitude of the signals returned from the moving object. Thus a much decreased amplitude return indicates a moving object in a second or third range cell.

The size of the range cell and thus the resolution of the system is determined by the separation in the two tones. One would normally want to start with a large range cell in the above example 75 meters and set the initial range cell by separating the two tones by one MHz.

If movement is ascertained within this relatively large range cell one may subsequently decide to reduce the size of the range cell to increase resolution. If one sees activity in the larger range cell one can for instance increase the separation in the two tones to 3 MHz which makes the range cells one third the original size.

Having ascertained the range cell that all activity is in one can increase the resolution of the subject system by increasing the separation between the two tones to decrease the range cell size and thus increase the resolution.

More particularly this system detects not only motion in a room but also the range of the moving object. One wants to know and locate where in the building the moving object is. If one is able to measure range this aids in that process of locating individuals in a room or behind a wall.

In order to provide range the two tone radar uses two frequencies that are fairly close together for instance one megahertz apart. One chooses two close frequencies and then looks at the output of each mixer for both frequency and frequency . By using a model that describes the differences in the frequency and frequency outputs one adjusts the range parameter for the model so that when the difference between the model predictions are minimized based on observed data collected the range that gives the best or closest agreement corresponds to the range of the moving object.

Thus at a given distance there is a two way trip that the signal has to travel with a phase shift between the transmitted and received signals corresponding to that distance. If the distance changes the phase shift will change. Since each frequency is slightly different that phase shift will change a little bit differently for the two frequencies. What the system does is to model the two way trip for each frequency. One frequency shows how the individual is moving in a non uniform way and one makes a comparison with the motion of the same individual as detected by the second frequency assuming that both frequencies monitor the same motion. The only parameter left is the range and by adjusting range when the range parameters come to the right value the models for fand fwill match and that range is a good prediction of the range of the moving object.

Referring now to in order to detect the presence of an individual constituting a moving object behind a wall a radar is provided which transmits continuous waves and through a summation device to an antenna . Antenna simultaneously projects the two waveforms at fand fas illustrated at and through wall where they meet object and are reflected backwardly as illustrated at and . The phase difference between outgoing and incoming waveforms for each of the frequencies is detected as will be discussed and in one embodiment the waveform corresponding to the temporal phase difference for tone fis coupled to a predictor . It is the purpose of predictor to predict the temporal waveform that would be expected to exist for the temporal phase difference waveform at frequency ffor an object at a known distance or range with the output of the predictor being a waveform on line . In order for predictor to operate the predictor predicts the fwaveform for a predetermined range Ras illustrated at such that for a given input waveform at one frequency a set of templates at the other frequencies corresponding to predicted waveforms at different ranges constitutes the output of predictor .

Predictor upon receiving a waveform input on input line for an initial range generates a predicted waveform for the temporal phase difference for the second tone and applies this waveform to a comparator .

As illustrated by arrow measured data in terms of the temporal phase difference waveform for tone fis applied to a waveform generator . This provides a temporal rendition of the phase difference of the outgoing and incoming waves at frequency ffrom measured data. This waveform is applied on line to comparator .

If the waveform on line and the waveform on line are sufficiently similar or agree then one declares that the range to object is the range that has been loaded into predictor to generate the predicted waveform. This range is outputted at as illustrated.

On the other hand if there is no significant agreement between the waveforms on lines and then as illustrated at unit the range associated with the predictor is changed and the process is iteratively carried out until there is a sufficient match between the waveforms on lines and . When there is such a match the range that was used in the predictor is the declared range to the moving target.

Referring to assuming that one has phase difference waveforms and that are the result of the radiation from antenna impinging up a randomly moving object behind wall then as can be seen for a location that is adjacent antenna namely at zero distance the waveforms themselves are very nearly the same.

Referring to if the moving object creating the phase difference in the returns to antenna is at a location that is 4 with being the wavelength of the tone separation in one embodiment one MHz then waveforms and are those as shown as waveforms and which are 180 phase shifted. This means that even for pseudo random motion that results in non sinusoidal waveforms and one can nonetheless establish that the distance of the object that is moving in a pseudo random fashion is at 4 away from antenna .

Referring to for waveforms and these waveforms are those that result from a pseudo random moving object at a range between zero and 4. If it were possible to measure the phase difference between these two non sinusoidal waveforms one could ascertain the distance from the antenna and therefore the range.

However and referring back to since it is not possible to accurately measure the phase shift of phase difference between waveforms and at least from inspection one generates a series of waveform templates relating to one of the tones or frequencies that would be expected at one of a plurality of ranges. This waveform is predicted from the measured waveform of the other of the frequencies or tones with the prediction algorithm being described above.

In this manner one generates a series of waveform templates at one particular frequency or tone which is what would be expected at various ranges. This is done by using the waveform associated with the other tone.

Having generated a series of such range dependent templates one then seeks to compare a waveform from measured data with the predicted waveform which his range dependent. One can use any one of a number of curve matching or best fit techniques to ascertain to which of the waveform templates the measured data corresponds. When there is a sufficient match one then declares the range to the moving object to be the range associated with the particular template to which the measured waveform was attached.

Referring to apparatus for deriving the temporal phase difference waveforms is shown in terms of a dual frequency radar although some advantage may be obtained by using more than two different frequencies. However for the present purposes radar can be characterized as including a pair of frequency sources and respectively at fand f each of which driving a power divider respectively and the outputs of which are respectively coupled to circulators and the outputs of which are in turn coupled to a summing or mixing device such as a splitter and thence to an antenna .

Power divider provides an output along line to a mixer which mixes it with an output corresponding to the returned signal from a moving object that comes out on line . The output of mixer along line is therefore the phase difference between the outgoing and incoming signals at frequency f.

Likewise for power divider one output is applied over line to a mixer which has as its other input a signal on line such that the output along line from mixer is a phase difference waveform associated with the phase difference between outgoing and incoming signals associated with f.

Microprocessor performs the functions of detecting not only motion but the range to the object in motion as described above with a motion detector and range determining unit outputting the range to the moving target be it in continuous motion or pseudo random motion.

It will be appreciated that microprocessor contains the predictor comparator and range adjustment functions that are described in connection with .

As illustrated in the measured phase difference waveforms applied to unit are illustrated at for the first tone or fand for the second tone or f. Here it will be appreciated that for these signals an object behind wall has reflected the signals such that the phase difference waveforms can be generated. The range at which the object reflects the radar energy is not known and as can be seen the phase difference waveforms are slightly different one tone to the other.

Referring to a number of waveforms and constitute a number of templates with these waveforms being the predicted fwaveforms for different ranges. In this case the ranges are separated by 10 meters.

If as is done by unit one compares the measured waveform at f namely waveform with each of these templates one ascertains that the closest match to the measured fwaveform is waveform . This leads to the declaration that the range to the object is 50 meters.

What will be seen even though the object in question may be exhibiting a pseudo random motion and even though this pseudo random motion produces phase difference waveforms that are non sinusoidal one can nevertheless with waveform matching techniques determine which of the templates is closest to the measured waveform whereby range to the object producing this waveform can be readily ascertained with high certainty.

It will be appreciated that if one has multiple two tone radar units at different positions and if one establishes the range to each of these radars by the techniques described herein one can establish the position of the moving object by triangulation or other techniques.

As mentioned hereinabove in order to get an unambiguous range determination one has to ascertain in which range cell the moving object is. This is simply accomplished by adjusting the frequency separation between the tones to establish a large enough range cell so that one with confidence can ascertain that the moving object is within the range cell. Also as mentioned before amplitude sensitive techniques can determine which range cell the object is in since the amplitude of returns from objects farther away will be considerably reduced.

What has been described hereinabove is a system for robustly detecting the presence and range of a moving object within a building or behind the walls of a structure in which a multi tone CW beam is projected through the wall and in which the range of a moving object or individual from this particular radar is determined. How to obtain instantaneous position is now described.

Assuming that one duplicates the radar of at two locations here shown at and then one projects RF energy into a surveilled area or region of interest from two different directions subtended by beam from radar and beam from radar respectively.

The result of using the two tone system of is that a band or swath of possible ranges for a moving individual from radar can be generated which locates the moving individual at any given instant of time in the area subtended by Band namely swath .

Likewise swath defines the possible positions of an individual or moving object relative to the second radar radar such that the swath of ranges is indicated by swath as Band .

From this point it is possible to detect the overlap of Band and Band at position to be able to compute the instantaneous position of the moving individual.

The use of multiple multi tone CW radar range finding systems each projecting a beam at different angles through the area to be surveilled provides not only for the range of a moving individual or object from each of the radars but also the overlap provides for the position as well.

The area of overlap is determined by the width of the various swaths which is in turn determined by the difference in frequencies of the multi tone radars it being noted that the range bands can be determined ahead of time as described hereinbefore. The range bands are to occur in the nearest zone to each of the radars such that by projecting RF energy through walls of a building or other structure from two spaced apart radars one can triangulate on the position of the moving object or individual.

In order to do so and referring now to it can be seen that radars and while projecting radar signals through a particular wall also may be used to communicate the results of the radar interrogation by modulating the selfsame signals which results are picked up at a microprocessor that carries a microwave receiver not shown .

The signals from antennas and are picked up for this purpose by antenna with the output of the receiver being coupled to an overlap detector that taking the range derived from the two radars and the position of their antennas available over line calculates the overlap area and its position relative to the positions of the two radars used in the through the wall sensing system.

The result of the overlap detection at its position is available over line coupled in one embodiment to a histogram that calculates and generates a histogram of overlaps thus to be able to determine the pathway of the moving object or individual within the surveilled area of .

This pathway namely pathway is shown by a breadcrumb trail as illustrated to indicate the path of the individual through the area behind a wall through which the RF energy is projected.

It will be appreciated that overlap detector can also provide a range indication which can be used either to indicate the detection of the presence of an individual or for other purposes.

Two or more units can provide ranges to the target. The known locations of the units are used along with the range values to produce a target location. With three units it is possible to produce a 3D location. It is not required that the beam width of the radar be narrow to get an accurate position. Only the locations of each radar unit need be known. An accurate position can be produced as long as the target is within the beam pattern of each radar.

Each dual frequency radar produces a range estimate. The range estimate has an uncertainty that is as a range dependent likelihood function P r . P r defines an arc whose center is located at the position xi yi zi of the ith radar unit. With two or more radar units a joint likelihood function L x y z P ri xi yi zi is formed. The target position is obtained by doing a search over x y z to find the peak value of L. The algorithm to do the search can be based on a number of known methods including gradient search methods.

In operational trials with a moving object behind a wall and spaced between 10 and 30 meters from the radars it has been found that the positional accuracy can be as little as one meter in terms of the overlap area of the various range swaths. This is sufficient accuracy to be able to locate a trapped firefighter a hiding enemy soldier or combatant or in fact to provide a real time track of a moving individual behind the wall or building structure.

Tests were conducted using two radars. Best results were obtained when the target was located such that the centerlines of each beam were perpendicular to each other. In this case a 2D location can be produced to an accuracy of DR in each direction. DR is the accuracy that a single radar can measure range and is roughly 1 meter at ranges of up to 20 meters for the test unit. As the angle is reduced to less than 90 the accuracy degrades as 1 Cos theta in the cross range direction.

The above description supports the notion that one can pinpoint the location of a moving individual behind a wall or in a building and to track the movement of the individual using multiple multi tone CW radars. The following describes how this system can be enhanced to improve range accuracy and therefore positional accuracy while at the same time providing a display of position that discriminates against non moving objects such as furniture light fixtures cabinets and the like.

Individual moves through the building amongst non moving objects . It is the purpose of the subject invention to robustly detect the presence of a moving individual to more accurately pinpoint his or her position and to reject clutter from radar returns that are reflected by non moving objects.

In order to triangulate on the moving individual a number of multi tone CW radars are positioned about building such that radiation from the radars penetrates walls so as to probe the interior of the building. Note that either multiple radars may be positioned about the building or a radar may be moved from one position to the next.

Regardless in order to cancel out the variable effects of wall thickness and changes in index of refraction due to the passage of pulses through the wall each of radars have their two tone frequencies stepped from a low frequency of 700 MHz to a high frequency of 2.3 GHz as illustrated at for the purpose of sharpening the pulses that are smeared out or distorted as the pulses pass through the wall. As illustrated the stepped frequency sweep provided by unit results in improved range measurements to all objects in the field of view of the radars. Note that the use of multiple frequencies in and of itself improves range accuracy. The range and the triangulation measurements are made in accordance with the aforementioned apparatus.

The purpose of stepping the frequency of each of the radars is to be able to project through walls a range of frequencies to be able to provide a set of weights here illustrated at that correct for the distortion of the pulses as they pass through the walls in both directions. This means for each frequency that post processing eliminates the distortion of a pulse as it is projected through a wall and then corrects out the wall effect for the returned pulses.

The reason that one can sharpen the pulses by removing distortion is because the wall affects the pulses differently at different frequencies. Thus lower frequencies are distorted differently from higher frequencies.

The distortion is a function of both the wall thickness and its index of refraction which depends on the material of which the wall is constructed. Since all of these parameters affect the pulses differently at different frequencies a set of weights is developed to weight the radar results to cancel out the distortion effects at each frequency.

One way to establish the weights is to take a known material and thickness and to measure the attenuation. Then knowing the attenuation one generates weights that are proportional to the inverse of the attenuation.

If one starts off with the above the weights can be refined by starting with a one dimensional image through the wall followed by the detection of a strong scatterer behind the wall. One then does a number of sub frequency sweeps. Then for each frequency sweep one obtains an amplitude of the scatterer. The ratio of the amplitudes then yields the frequency dependent attenuation. One can basically use the lowest frequency which has the lowest attenuation whereupon one can derive the weighting at other frequencies. These are then the weights used.

With all of the frequencies compensated by the weighting scheme the composite is equivalent to a sharpened pulse which improves the range accuracies by as much as 50 .

One way of obtaining the parameters for the wall material is to either physically measure them or to estimate them.

Another way to obtain the wall material parameters is to perform an auto focusing function which when an object is in focus specifies the wall thickness and index of refraction. How this is done is that one starts off with initial estimations of the index of refraction absorption and wall thickness i.e. the initial parameters. Then one forms an image after which one adjusts the parameters and reforms the image. This is repeated using a method for sharpening gradient descent to maximize image sharpness. The parameters are for the sharpest image. These parameters are then used to generate the weights. This process can be repeated i.e. forming an image and adjusting it in an iterative process to refine the weights.

Having sharpened the range results of the radars the results are rendered into images as shown at and . These images contain clutter in the sense that these images relate to both returns from moving objects and returns from non moving objects. However the images are the result of measurements taken at different times here time Tand time T. By subtracting one image from the other as illustrated at one can generate an uncluttered image whose pixels are caused only by objects in motion. The result as illustrated by display is that a pixel is a result of only reflections from moving objects with images that are the result of reflections from non moving objects canceled. As will be appreciated pixel provides an uncluttered view of moving object location.

Referring to what is shown is an expanded view of one of the radars in in which each radar includes a stepped frequency source coupled to a power divider which feeds a circulator coupled to an antenna . A signal from power divider and a signal from mixer is applied to a multiplier so as to detect the absolute phase differences for each frequency as illustrated at . Then for each antenna position one detects range to all moving objects for each frequency step as illustrated at .

It is this range for each frequency step for each antenna position that is weighted in accordance with the subject invention.

In summary the use of multiple frequencies results in better range measurements. Secondly better range measurements are obtained by using the subject weighting system. Thirdly antennas at a large number of different locations result in better triangulation. Finally the use of differential clutter rejection discriminates against returns from non moving objects.

With multiple multi tone radars frequency stepping and differential image clutter rejection one has provided an extremely robust system for detecting a moving individual behind a wall .

While the present invention has been described in connection with the preferred embodiments of the various figures it is to be understood that other similar embodiments may be used or modifications or additions may be made to the described embodiment for performing the same function of the present invention without deviating therefrom. Therefore the present invention should not be limited to any single embodiment but rather construed in breadth and scope in accordance with the recitation of the appended claims.

