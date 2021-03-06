---

title: Data processing apparatus, the method and coding apparatus
abstract: From an MPEG image data (S), an MPEG2 encoder circuit () extracts a quantum scale (Qm) of each macro block (MB) which has been used for quantization of the MPEG2 in the encoding process. An activity calculation circuit () calculates an activity (Nact), based on the quantum scale (Qm), A rate control circuit () calculates a quantization parameter (QP) for each macro block (MB), based on the activity (Nact).
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07933459&OS=07933459&RS=07933459
owner: Sony Corporation
number: 07933459
owner_city: Tokyo
owner_country: JP
publication_date: 20050225
---
The present invention relates to a data processing apparatus the method and a coding apparatus for performing quantization on image data.

In recent years apparatuses based on methods such as the Moving Picture Experts Group MPEG for using image data as digital and compressing by discrete cosine transformation and other orthogonal transformations and motion compensation by using redundancy peculiar to image information for the purpose of efficiently transferring and accumulating information have been widespread both in information distribution by broadcast stations and in information receiving by general households. In the MPEG method transformation coefficients are generated by performing orthogonal transformation on image data to be coded and quantization is performed on the transformation coefficients by a predetermined quantization scale and then the quantized image data are coded.

In the MPEG method the quantization scale is determined based on a degree of complexity of an image to be coded so that the more complex the image becomes the smaller the value becomes.

Following to the MPEG method coding methods called the H.264 and JVT Joined Video Team for realizing a still higher compression rate have been proposed.

In the JVT method coding apparatus coding in the JVT method is performed after decoding image data coded by the MPEG in some cases.

When performing quantization without considering a quantization scale used in the MPEG method coding apparatus in the JVT method coding apparatus of the related art explained above there is a disadvantage that for example an extremely larger quantization scale than the quantization scale used in the MPEG method coding apparatus is selected and information held by the MPEG method is lost by rough quantization so that the image quality is deteriorated in some cases.

Inversely there is a disadvantage in the JVT method coding apparatus of the related art explained above that an extremely smaller quantization scale than the quantization scale used in the MPEG method coding apparatus is selected and a large number of bits are assigned to less information so that the coding efficiency declines without improving the image quality.

The same disadvantages may arise also in coding methods other than the MPEG method and the JVT method.

It is desired to provide a data processing apparatus the method and a coding apparatus for when performing second quantization on data to be processed and obtained by performing inverse quantization after performing first quantization suitably performing the above second quantization in terms of image quality and a coding efficiency.

To solve the above disadvantages of the related art explained above according to a first invention there is provided a data processing apparatus for performing a second quantization on data to be processed and obtained by performing inverse quantization after performing a first quantization by a first quantization scale comprising a quantization scale generation means for generating a second quantization scale based on the first quantization scale and a quantization means for performing the second quantization on the data to be processed based on the second quantization scale generated by the quantization scale generation means.

First the quantization scale generation means generates the second quantization scale based on the first quantization scale 

Next the quantization means performs the second quantization on the data to be processed based on the second quantization scale generated by the quantization scale generation means.

According to a second invention there is provided a data processing method for performing the second quantization on data to be processed and obtained by performing inverse quantization after performing the first quantization by the first quantization scale including a first step of generating a second quantization scale based on the first quantization scale and a second step of performing the second quantization on the data to be processed based on the second quantization scale generated in the first step.

According to a third invention there is provided a coding apparatus comprising a decoding means for generating decoding data by decoding coding data generated by performing coding on motion image data by the first coding method and obtained by performing the first quantization based on the first quantization scale in the coding step the quantization scale generation means for generating the second quantization scale based on the first quantization scale and a quantization means for performing second quantization on the decoding data based on the second quantization scale generated by the quantization scale generation means in a step of performing coding in a second coding method which is different from the first coding method on the decoding data generated by the decoding means.

First a decoding means generates decoding data by decoding coding data generated by performing coding on moving image data by the first coding method and obtained by performing the first quantization based on the first quantization scale in the above coding step.

Next the quantization scale generation means generates the second quantization scale based on the first quantization scale.

Next the quantization means performs the second quantization on the decoding data based on the second quantization scale generated by the quantization scale generation means in a step of coding the decoding data generated by the decoding means by a second coding method which is different from the first coding method.

According to a fourth invention there is provided a data processing apparatus for performing the second quantization on data to be processed and obtained by performing the inverse quantization after performing the first quantization by the first quantization scale comprising the quantization scale generation circuit for generating a second quantization scale based on the first quantization scale and the quantization circuit for performing the second quantization on the data to be processed based on the second quantization scale generated by the quantization scale generation circuit.

According to the present invention when performing second quantization on data to be processed and obtained by performing inverse quantization after performing the first quantization it is possible to provide a data processing apparatus the method and a coding apparatus for suitably performing the second quantization in terms of image quality and a coding efficiency.

Below a JVT method coding apparatus according to embodiments of the present invention will be explained.

First corresponding relationship of components of the present invention and components of the present embodiment will be explained.

In the present embodiment a function of generating a quantization scale based on a quantization parameter QP among functions of an activity calculation circuit a rate control circuit and a quantization circuit corresponds to a quantization scale generation means of the first and third inventions.

Also a function of performing quantization based on the quantization scale in functions of the quantization circuit in the present embodiment corresponds to a quantization means of the first and third inventions.

Also an MPEG2 decoding circuit in the present embodiment corresponds to a decoding means of the third invention.

As shown in the communication system has a coding apparatus provided on the transmission side and a decoding apparatus provided on the receiving side.

In the communication system in the coding apparatus on the transmission side after generating frame image data bit stream compressed by orthogonal transformation such as discrete cosine transformation and Karhunen Loeve transformation and motion compensation and modulating the frame image data it is transmitted via transmission media such as a satellite broadcast wave a cable TV network a telephone line network and a cellular phone network.

On the receiving side after decoding a received image signal frame image data decompressed by inverse transformation of the orthogonal transformation at the time of the above modulation and motion compensation is generated and used.

Note that the transmission media may be recording media such as an optical disk a magnetic disk and a semiconductor memory.

As shown in the coding apparatus includes for example an A D conversion circuit a picture relocating circuit a calculation circuit an orthogonal transformation circuit a quantization circuit a reversible coding circuit a buffer an inverse quantization circuit an inverse orthogonal transformation circuit a restructuring circuit a deblock filter a memory an intra prediction circuit a motion prediction compensation circuit a selection circuit an MPEG2 decoding circuit a picture type buffer memory an activity calculation circuit and a rate control circuit .

In the coding apparatus an MPEG image data S coded by the MPEG2 in the MPEG2 decoding circuit is decoded to generate image data S and the image data S is coded by the JVT method.

The MPEG2 decoding circuit extracts a quantization scale Qm first quantization scale of the present invention of each macro block MB used in quantization in the MPEG2 coding step first quantization of the present invention from the MPEG image data S and outputs to the activity calculation circuit .

The activity calculation circuit calculates an activity Nact based on the quantization scale Qm and outputs the same to the rate control circuit as will be explained later on.

The rate control circuit calculates a quantization parameter QP of each macro block MB based on the activity Nact input from the activity calculation circuit and outputs the same to the quantization circuit .

The quantization circuit performs quantization the second quantization of the present invention on the image data S by using a quantization scale the second quantization scale of the present invention determined based on the quantization parameter QP input from the rate control circuit .

In either of the MPEG2 and JVT there are non interlace scanning image data and interlace scanning image data in image data input to the coding apparatus and it is possible to select coding in unit of field data field coding and coding in unit of frame data frame coding .

In the MPEG2 frame coding may be performed on a macro block MB composed of data of 16 pixels by 16 pixels for example as shown in or field coding may be performed on each top field data and bottom field data by dividing to data of 16 pixels by 8 pixels as shown in .

Also in the JVT it is possible to select coding in unit of picture as shown in and and coding in unit of macro block as shown in .

As coding in unit of picture it is possible to select frame coding shown in and field coding shown in .

Also as coding in unit of macro block it is possible to select the case of performing frame coding or field coding in unit of single macro block and the case of performing frame coding or field coding in unit of two macro blocks MB MB pair that is data of 16 pixels by 32 pixels.

Also in the present embodiment as shown in respective macro blocks MB i and MB i 1 adjacent in the vertical direction in frame data FR m composing the image data S obtained by decoding in the MPEG2 decoding circuit are quantized based on quantization scales Qm i and Qm i 1 respectively in MPEG coding performed in the past.

The MPEG2 decoding circuit extracts the quantization scales Qm i and Qm i 1 in the step of decoding the MPEG image data S and outputs to the activity calculation circuit .

Note that each of the macro blocks MB in the MPEG image data S corresponding to the macro blocks MB i and MB i 1 includes both of the quantization scales Qm i and Qm i 1 .

Also when field coding in unit of picture by the JVT method is performed JVT image data S includes in a macro block MBjt i in a top field TF j corresponding to a macro block MBm i a quantization scale Qjt i used in the quantization as shown in . Also in a macro block MBjb i in a bottom field BF j corresponding to a macro block MBm i 1 a quantization scale Qjb i used in the quantization is included.

On the other hand furthermore when field coding in unit of macro block pair by the JVT method is performed in JVT image data S as shown in a macro block MBj i corresponding to the macro block MBm i and a macro block MBj i 1 corresponding to the macro block MBm i 1 are arranged in the same field FI j.

The macro block MBj i includes a quantization scale Qj i used in the quantization and the macro block MBj i 1 includes a quantization scale Qj i 1 used in the quantization.

The A D conversion circuit converts image data S to be coded and composed of input analog luminance signal Y and color difference signals Pb and Pr to image data S in digital and outputs the same to the picture relocating circuit .

The screen relocating circuit outputs image data S obtained by relocating image data S input from the A D conversion circuit or image data S input from the MPEG2 decoding circuit in an order of coding in accordance with the GOP group of pictures structure composed of the picture types I P and B to the calculation circuit the intra prediction circuit and the motion prediction compensation circuit .

Below in the present embodiment the case where the screen relocating circuit performs processing on image data S input from the MPEG2 decoding circuit .

The calculation circuit generates image data S indicating a difference between the image data S and prediction image data PI input from a selection circuit and outputs the same to the orthogonal transformation circuit .

The orthogonal transformation circuit performs orthogonal transformation such as discrete cosine transformation and Karhunen Loeve transformation on the image data S to generate image data for example a DCT coefficients S and outputs the same to the quantization circuit .

The quantization circuit performs quantization on the image data S based on the quantization scale regulated based on the quantization parameter QP input from the rate control circuit and in accordance with the quantization parameter QP to generate image data S and outputs the same to the reversible coding circuit and inverse quantization circuit .

The reversible coding circuit stores in the buffer image data obtained by performing variable length coding or calculation coding on the image data S.

At this time when the selection data S indicates that inter prediction coding is selected the reversible coding circuit performs coding on a motion vector MV input from the motion prediction compensation circuit and stores the same in the header data.

Alternately when selection data S indicates that intra prediction coding is selected the reversible coding circuit stores an intra prediction mode IPM input from the intra prediction circuit in the header data etc.

Also the reversible coding circuit makes the quantization scale used in quantization in the quantization circuit included in respective macro blocks MB.

The inverse quantization circuit performs inverse quantization on the image data S based on the quantization scale used in the quantization circuit and outputs the same to the inverse orthogonal transformation circuit .

The inverse orthogonal transformation circuit performs inverse orthogonal transformation corresponding to the orthogonal transformation used in the orthogonal transformation circuit on inversely quantized image data input from the inverse quantization circuit and outputs the same to the restructuring circuit .

The restructuring circuit adds prediction image data PI input from the selection circuit and image data input from the inverse orthogonal transformation circuit to generate restructuring image data and outputs the same to the deblock filter .

After eliminating block strain of image data input from the restructuring circuit the deblock filter writes the same as reference image data in the memory .

The intra prediction circuit performs intra prediction coding on the respective macro blocks MB composing image data read from the memory to generate prediction image data for example based on respective intra prediction modes regulated in advance by the JVT and detects a difference DIF between the prediction image data and the image data S.

Then the intra prediction circuit specifies an intra prediction mode corresponding to the minimum difference in the above difference generated respectively for the above plurality of intra prediction modes and outputs the specified intra prediction mode IPM to the reversible coding circuit .

Also the intra prediction circuit outputs the prediction image data PI by the specified intra prediction mode and the difference DIF to the selection circuit .

The motion prediction compensation circuit performs motion prediction processing in unit of frame data and field data on the image data S as explained with reference to and and determines a motion vector MV based on the reference image data REF read from the memory .

Namely the motion compensation circuit determines a motion vector MV to make the difference DIF between prediction image data PI regulated by the motion vector MV and the reference image data REF and the image data S minimum.

The motion prediction compensation circuit outputs the prediction image data PI and the difference DIF to the selection circuit and outputs the motion vector MV to the reversible coding circuit .

Note that the motion prediction compensation circuit performs motion prediction compensation processing on the respective frame data and field data based on picture type data PIC T read from the picture type buffer memory by applying the same picture type used in the MPEG coding.

The selection circuit compares the difference DIF input from the intra prediction circuit and the difference DIF input from the motion prediction compensation circuit .

When the selection circuit determines that the difference DIF input from the intra prediction circuit is smaller from the above comparison it selects the prediction image data PI input from the intra prediction circuit and outputs to the calculation circuit .

When the selection circuit determines that the difference DIF input from the motion prediction compensation circuit is smaller from the above comparison it selects the prediction image data PI input from the motion prediction compensation circuit and outputs to the calculation circuit .

Also the selection circuit outputs to the reversible coding circuit selection data S indicating that inter prediction coding is selected when the prediction image data PI input from the intra prediction circuit is selected while outputs to the reversible coding circuit selection data S indicating that intra prediction coding is selected when the prediction data PI input from the motion prediction compensation circuit is selected.

The MPEG2 decoding circuit receives as an input for example MPEG image data S and decodes the MPEG image data S by the MPEG2 to generate image data S and outputs the same to the screen relocating circuit .

Also the MPEG2 decoding circuit writes in the picture type buffer memory the picture type data PIC T included in a header of the image data S and indicating a picture kind of each macro block.

The MPEG2 decoding circuit extracts a quantization scale Qm of the each macro block used in the quantization in the MPEG2 coding step from the MPEG image data S in the above decoding and outputs to the activity calculation circuit .

The picture type data PIC T stored in the picture type buffer memory is read by the selection circuit and the motion prediction compensation circuit .

The activity calculation circuit calculates an activity Nact based on the quantization scale Qm input from the MPEG2 decoding circuit and outputs the same to the rate control circuit . is a view for explaining processing in the activity calculation circuit shown in when performing field coding in unit of picture as shown in in JVT coding.

Below an explanation will be made by taking as an example calculation of the activity Nact used for generating macro blocks MBjt i and MBjb t in the JVT image data S shown in .

The activity calculation circuit receives as an input a quantization scale Qm i of the macro block MBm i and a quantization scale Qm i 1 of a macro block MBm i 1 shown in from the MPEG2 decoding circuit .

The activity calculation circuit receives as an input the quantization scales Qm i and Qm i 1 as arguments of a function ft shown in the formula 1 below regulated in advance for a top field TF j and specifies a quantization scale Qa t i . Formula 1 1 1 

The activity calculation circuit receives as an input the quantization scales Qm i and Qm i 1 as arguments of a function fb shown in the formula 2 regulated in advance for a bottom field BF j and specifies a quantization scale Qa b i . Formula 2 1 2 

As the ft and fb for example as shown in the formula 3 the smaller of the quantization scales Qm i and Qm i 1 is selected and used for a function for specifying the quantization scales Qa t i and Qa b i . Formula 3 min 1 3 

Note that as the functions ft and fb for example a function for calculating the quantization scales Qa t i and Qa b i by calculation shown in the formula 4 below. Formula 4 1 1 2 4 

The activity calculation circuit calculates an average value aveQa t of quantization scales Qa t i of all block data in the top field TF j to which the macro block MBjt i belongs based on the formula 5 below.

Also the activity calculation circuit calculates an average value aveQa b of quantization scales Qa b i of all block data in the bottom field BF j to which the macro block MBjb i belongs based on the formula 6 below.

The activity calculation circuit calculates activity Nact t i by dividing the quantization scale Qa t i calculated in the step ST by the average value aveQa t calculated in the step ST for each of the macro blocks MB belonging to the top field TF j as shown in the formula 7 below. Formula 7 act ave 7 

Also the activity calculation circuit calculates activity Nact b i by dividing the quantization scale Qa b i calculated in the step ST by the average value aveQa b calculated in the step ST for each of the macro blocks MB belonging to the bottom field BF j as shown in the formula 8 below. Formula 8 act ave 8 

The activity calculation circuit outputs the activities Nact t i and Nact b i calculated in the step ST to the rate control circuit .

The rate control circuit calculates a quantization parameter QP for each macro block MB based on the activities Nact t i and Nact b i input from the activity calculation circuit and outputs the same to the quantization circuit .

Here when expressing the activities Nact t i and Nact b i by the activity Nact i a quantization parameter QP i of each macro block MB is expressed by the formulas 9 and 10 below. Note that round in the formula 9 indicates integer processing by rounding and QPr in the formula 10 is a reference quantization parameter regulated by the JVT method which is regulated for field data or frame data. Formula 9 round logact 9 Formula 10 10 

The rate control circuit outputs a quantization parameter QP i generated as explained above to the quantization circuit .

The quantization circuit performs quantization on the image data S by a quantization scale regulated in accordance with the quantization parameter QP i input from the rate control circuit to generate image data S.

Note that in the present embodiment the quantization scale is regulated to be doubled when the quantization parameter QP i increases by 6 .

The MPEG2 decoding circuit extracts a quantization scale Qm of each macro block used in quantization in an MPEG2 coding step from the MPEG image data S in the decoding above and outputs to the activity calculation circuit .

The activity calculation circuit calculates activities Nact Nact t i and Nact b i based on the quantization scale Qm input from the MPEG2 decoding circuit in the step ST and outputs the same to the rate control circuit .

The rate control circuit calculates a quantization parameter QP of each macro block MB based on the activity Nact input from the activity calculation circuit in the step ST and outputs the same to the quantization circuit .

The quantization circuit performs quantization on the image data S by a quantization scale regulated in accordance with the quantization parameter QP i input from the rate control circuit in the step ST to generate image data S.

Below an example of an overall operation of the coding apparatus when coding by the JVT method the image data S obtained by decoding the MPEG image data S will be explained.

Next the MPEG2 decoding circuit decodes the MPEG image data S to generate the image data S and outputs the same to the screen relocating circuit .

At this time the MPEG2 decoding circuit extracts a quantization scale Qm of each macro block used in quantization in the MPEG2 coding step from the MPEG image data S in the above decoding and outputs the same to the activity calculation circuit .

Then the activity calculation circuit calculates an activity Nact based on the quantization scale Qm and outputs the same to the rate control circuit .

Then the rate control circuit calculates a quantization parameter QP of each macro block MB based on the activity Nact and outputs the same to the quantization circuit .

Also intra prediction is performed in the intra prediction circuit and a difference DIF with the prediction image data PI is output to the selection circuit .

Also in the motion prediction compensation circuit motion prediction compensation processing is performed and a motion vector MV is specified and the prediction image data PI and the difference DIF are output to the selection circuit .

Then the selection circuit outputs prediction image data PI corresponding to the smaller difference DIF of the difference DIF input from the intra prediction circuit and the difference DIF input from the motion prediction compensation circuit to the calculation circuit .

Next the calculation circuit generates image data S indicating a difference between the image data S and the prediction image data PI input from the selection circuit and outputs the same to the orthogonal transformation circuit .

Next the orthogonal transformation circuit performs orthogonal transformation such as discrete cosine transformation and Karhunen Loeve transformation on the image data S to generate image data for example a DCT coefficients S and outputs the same to the quantization circuit .

Next the quantization circuit performs quantization on the image data S based on the quantization scale regulated in accordance with the quantization parameter QP based on the quantization parameter QP input from the rate control circuit and outputs the same to the reversible coding circuit and the inverse quantization circuit .

Next the reversible coding circuit stores in the buffer the image data obtained by performing variable length coding or calculation coding on the image data S.

As explained above in the coding apparatus when performing JVT coding on the image data S decoded in the MPEG2 decoding circuit a quantization parameter QP quantization scale of each macro block used for quantization of the quantization circuit based on the quantization scale Qm used for generating each macro block MBm of MPEG image data is determined.

Therefore according to the coding apparatus it is possible to perform high quality quantization with less waste in the JVT coding by considering characteristics of quantization in the MPEG coding comparing with the case of determining a quantization parameter QP to be used for quantization by the quantization circuit without using a quantization scale Qm.

Also according to the coding apparatus as explained above quantization scales Qa t i and Qa b i are generated based on the quantization scales Qm i and Qm i 1 as shown in the above formulas 3 and 4 in the activity calculation circuit and by determining a quantization scale to be used in the quantization circuit based thereon it is possible to prevent selecting an extremely larger or smaller quantization scale than the quantization scale used in the MPEG method coding in quantization in the JVT method coding.

Therefore according to the coding apparatus it is possible to perform suitable quantization in the quantization circuit in terms of image quality and a coding efficiency. Namely it is possible to prevent in the JVT coding a wasteful loss of information held in MPEG coding or assignment of an unnecessarily large amount of bits to information already lost in the MPEG coding.

In the above first embodiment an explanation was made on the processing of the activity calculation circuit shown in in the case of performing field coding in unit of picture as shown in .

In the present embodiment an explanation will be made on processing of the activity calculation circuit shown in when performing field coding in unit of micro block as shown in .

Below calculation of activity Nact of macro blocks MBj i and MBj i 1 in JVT image data S shown in will be explained as an example.

The activity calculation circuit receives as an input a quantization scale Qm i of the macro block MBm i and a quantization scale Qm i 1 of the macro block MBm i 1 shown in from the MPEG2 decoding circuit .

The activity calculation circuit receives as an input the quantization scales Qm i and Qm i 1 as arguments of the function f1 shown in the formula 11 below and specifies a quantization scale Qa i . Formula 11 1 1 11 

Also the activity calculation circuit receives as an input the quantization scales Qm i and Qm i 1 as arguments of the function f shown in the formula 12 below and specifies a quantization scale Qa i 1 . Formula 12 1 2 1 12 

The activity calculation circuit calculates an average value aveQa of quantization scales Qa i and Qa i 1 of all block data in the field FI j to which the macro blocks MBj i and MBj i 1 belong based on the formula 13 below.

The activity calculation circuit calculates an activity Nact i by dividing the quantization scale Qa i calculated in the step ST by the average value aveQa calculated in the step ST as shown in the formula 14 below. Formula 14 act ave 14 

Also the activity calculation circuit calculates an activity Nact i 1 by dividing the quantization scale Qa i 1 calculated in the step ST by the average value aveQa calculated in the step ST as shown in the formula 15 below. Formula 15 act 1 1 ave 15 

The activity calculation circuit outputs the activities Nact i and Nact i 1 calculated in the step ST to the rate control circuit .

For example in the above embodiments in the coding apparatus the case of performing field coding by the JVT method was explained as an example but frame coding may be performed.

In this case for example in the step ST shown in the activity calculation circuit calculates an average value aveQa of quantization scales Qa of all block data in the frame data to which the macro block belongs and based thereon an activity Nact is generated.

Also in the above embodiments motion image data was explained as an example of data to be processed in the present invention but data to be processed in the present invention may be still image data or audio data.

