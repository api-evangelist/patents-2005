---

title: Video display control apparatus and video display control method
abstract: Provided are a video display control apparatus and a video display control method. A video display control apparatus, including a data storage storing graphic/control integrated data including control information used to display graphic data to be combined with video data and the video data; and a controller combining the video data and the graphic data referring to the graphic/control integrated data and transmitting the combined data to more than one display device. As described above, the transmission capacity of video data, OSD data, and graphic data for a variety of display devices is reduced, thereby lowering the bus proportion. As a whole, the power consumption required by a system is reduced, thereby realizing to be suitable for a mobile device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07554563&OS=07554563&RS=07554563
owner: Samsung Electronics Co., Ltd.
number: 07554563
owner_city: Suwon-Si
owner_country: KR
publication_date: 20050830
---
This application claims the benefit of Korean Patent Application No. 10 2004 0068478 filed on Aug. 30 2004 in the Korean Intellectual Property Office the disclosure of which is incorporated herein in its entirety by reference.

The present invention relates to a video display control apparatus and a video display control method.

As digital cameras and digital camcorders become more popular their use is remarkably increasing. Video taken by a device such as a digital camera or a digital camcorder can be displayed on a separate video device such as a CRT or on LCD panel of the device which is also used as an interface. In order to provide video data as well as information on the video data the video data and On Screen Display OSD data or the video data and graphic data are combined and then displayed as a user interface that can be manipulated by a user.

An OSD is information that a monitor itself displays on its screen without a separate video signal. When a video signal cable is not properly connected a message such as check the connection is displayed and when various setting operations are performed using a manipulation button on the front of the monitor the operations are displayed on screen. All of this employs the OSD function. OSD is usually used to manipulate a monitor s screen display function.

Image formats express digital color images include a variety of formats such as YUV YIQ etc. in addition to a RGB format used in a color computer graphic or a color television. The RGB format expresses a color image using three components R Red G Green and B Blue . The YUV format expresses a color image using a luminance component Y and two color components U and V. The YIQ format is similar to the YUV format.

If a screen displayed on an LCD panel of a digital camera or a digital camcorder is also transmitted to CRT the OSD information indicating the playback state and the date is displayed however the user interface menu is not displayed.

Conventionally the OSD information or graphic data displayed on these display devices is stored in a separate memory and the stored OSD information and graphic data are read processed separately and displayed on each display device. The graphic data may also be composed of a plurality of graphic layers which are all stored separately and are combined to be displayed on a display device.

The microprocessor supports an OSD that informs users of system information or video information generates OSD data and graphic data and stores them in a memory so as to support an alpha blending function and various graphic layers in order to provide various user interfaces.

The bus master MASTER which is a device that may be a master having authority to control the bus system includes an input unit that receives an input signal from a camera and stores the signal in a system memory.

The memory stores input video data from a camera and layers of graphic data which is combined with the video data and is displayed.

The postprocessor reads data from a certain area of the memory and displays the data on the video display controller which displays data received from the postprocessor on each of the display device .

When an input YUV signal sampled at a rate of 4 2 2 is received from a camera the YUV signal is compressed restored stored or transformed by a video processor and the transformed data or the stored video data is displayed by a video display device. In general video display devices express colors represented by a color coordinate system having three dimensional coordinate axes such as R G B Y cb Cr Y pb Pr etc. The video display device may be a single display device or a plurality of display devices and data may be simultaneously displayed on a plurality of video display devices.

For example when a video display device is composed of a CRT display device requiring SD 720 480 or 720 576 Y cb Cr video received from a camera and of a display device requiring RGB video having a different resolution a color converter that converts the video and a zooming converter that converts an input output resolution are required due to the different color spaces. An alpha blending function is also required to blend the OSD data and graphic layer.

Wherein Img x y denotes an image input to a video display control apparatus 1 alpha x y denotes an alpha blending value which is multiplied by the input image Grp x y denotes graphic data alpha denotes an alpha blending value which is multiplied by the graphic data and Out x y denotes an alpha blended display video.

The memory stores video data graphic data and alpha data for the CRT and graphic data and alpha data for the LCD.

The video data contains an input Y Cb Cr signal received from a camera which is sampled using an interfacing method at a rate of 4 2 2.

The graphic data and alpha data for the CRT indicate graphic data and alpha data which are displayed on the CRT. The size of graphic data and alpha data is 720 480 which is the same as the video data. The graphic data and alpha data for the LCD indicate graphic data and alpha data which are displayed on the LCD. The size of graphic data and alpha data is 480 240. Each graphic data is generally sampled at 4 4 4 and an alpha value is generally expressed as a level of 16 or 256.

The postprocessor includes a YCbCr2RGB a 1 alpha blender an alpha blender an alpha blender an adder an RGB2YCbCr a scalar and an adder .

The YCbCr2RGB converts a YcbCr signal of the video data read from the memory into RGB for alpha blending. The 1 alpha blender performs alpha blending by multiplying 1 alpha by the video data converted into a RGB format. The alpha blender performs alpha blending for the graphic data for the CRT by multiplying the alpha data by the graphic data which are read from the memory . The alpha blender performs alpha blending for the graphic data for the LCD by multiplying the alpha data by the graphic data which are read from the memory . The adder adds the alpha blended video data and the alpha blended graphic data and outputs them to the RGB2YCbCr . The RGB2YCbCr converts the received data in a RGB format into an YCbCr format. The scalar changes the resolution of the alpha blended video data to correspond to the size of the LCD. The adder adds the alpha blended video data whose resolution is changed and the alpha blended graphic data and outputs them to the LCD controller .

The NTSC encoder outputs data received from the RGB2YCbCr to the CRT and the CRT displays the received data. The LCD controller outputs the data received from the adder to the LCD and the LCD displays the received data.

Meanwhile as most multimedia devices tend to require a high compressibility and various data transformations the data bus proportion maintains considerably high. As the portability of multimedia devices increases the clock signal of a system is decreased by decreasing various methods to reduce operation of the inside of the system and the bus proportion.

However the bus proportion of a video display control apparatus among a plurality of masters on bus is rather considerably high due to various types of data. A graphic handling is to read each layer from the memory and directly add it in hardware which also results in increasing the bus proportion.

Additional aspects and or advantages of the invention will be set forth in part in the description which follows and in part will be apparent from the description or may be learned by practice of the invention.

The present invention provides a video display control apparatus and a video display control method that reduce a data transmission to lower the amount of bus data in a video display control system having more than one display device.

According to an aspect of the present invention there is provided a video display control apparatus including a data storage storing a graphic control integrated data including graphic data to be combined with video data and the control information used to display the video data and a controller combining the video data and the graphic data referring to the graphic control integrated data and transmitting the combined data to more than one display device.

The controller may include a parser analyzing the graphic control integrated data and extracting an alpha information on the graphic data information on a display device on which the graphic data is displayed and a color data of the graphic data more than one alpha blender receiving the color data based on the information on a display device and alpha blending the color data using an alpha value based on the extracted alpha information and an adder combining the alpha blended graphic data displayed from the alpha blender and the video data.

The controller may further include a format converter converting the output data from the adder to correspond to a color format of the display device and a scalar converting the output data from the format converter to be corresponding to a resolution of the display device.

The controller may include a parser analyzing information on each line included in the graphic control integrated data a run length decoder run length decoding line data of the graphic control integrated data in order to extract alpha information on the graphic data information on a display device on which the graphic data is displayed and color data of the graphic data from the graphic control integrated data more than one alpha blender receiving the graphic data based on the information on a display device and alpha blending the color data using an alpha value based on the extracted alpha information and an adder combining the alpha blended graphic data displayed from the alpha blender and the video data.

The controller may further include a format converter converting the output data from the adder to correspond to a color format of the display device and a scalar converting the output data from the format converter to correspond to a resolution of the display device.

The line information may include at least one item of information with respect to each line indicating whether OSD data exists whether run length encoding is performed whether a bitmap table is used and whether it is the same as an upper line.

According to another aspect of the present invention there is provided a video display control method including storing graphic control integrated data including graphic data to be combined with video data and the control information used to display the video data combining the video data and the graphic data referring to the graphic control integrated data and transmitting the combined data to more than one display device.

The combining may include analyzing the graphic control integrated data and extracting alpha information on the graphic data information on a display device on which the graphic data is displayed and color data of the graphic data receiving the color data based on the information on a display device and alpha blending the color data using an alpha value based on the extracted alpha information and combining the alpha blended graphic data and the video data.

The combining may further include converting the combined data to a color format of the display device and converting the data whose format is converted to a resolution of the display device.

The combining may include analyzing information on each line included in the graphic control integrated data run length decoding line data of the graphic control integrated data in order to extract alpha information on the graphic data information on a display device on which the graphic data is displayed and color data of the graphic data from the graphic control integrated data receiving the graphic data based on the information on a display device and alpha blending the color data using an alpha value based on the extracted alpha information and combining the alpha blended graphic data and the video data.

The combining may further include converting the combined data to a format of the display device and converting the data whose format is converted to a resolution of the display device.

The line information may include at least one information with respect to each line indicating whether an OSD data exists whether a run length encoding is performed whether a bitmap table is used and whether it is the same as an upper line.

The combining may include reading and storing the graphic control integrated data line by line and run length decoding If a present line is determined to be identical to a just previously decoded line data by the information indicating whether it is the same as the upper line included in the line information the line data just previously decoded.

Reference will now be made in detail to the embodiments of the present invention examples of which are illustrated in the accompanying drawings wherein like reference numerals refer to the like elements throughout. The embodiments are described below to explain the present invention by referring to the figures.

In the apparatus shown in the graphic data generator generates graphic control integrated data and stores it in the memory and the postprocessor reads the graphic control integrated data stored in the memory combines it with video data and displays the combined data on the respective display devices.

First the graphic data generator generates the graphic control integrated data in which information on OSD data graphic layers alpha information display devices are integrated and stores it in the memory according to an embodiment of the present invention. The memory stores the video data and the graphic control integrated data .

The video data can be data which is stored by an encoding process not shown from a camera or camcorder and has a size of for example 720 480.

The graphic control integrated data integrates graphic layers includes final graphic data to be displayed on a display device and includes additional alpha information and information on other display devices. The configuration of the graphic control integrated data stored in the memory is illustrated in .

Referring to the graphic control integrated data includes a line information layer and a line data layer . The line information layer is uncompressed data which contains information on each line. The line data layer is pixel data contained in each line which may be compressed by run length encoding etc. The specific data content of the line information layer is illustrated in and the specific content of the line data layer is illustrated in . These will be described in detail later.

The specific configuration of the graphic data generator is illustrated in . Referring to the graphic data generator includes a line information extractor a line data extractor a run length encoder and a line information and line data combiner . If each constituent of the graphic data generator is made up of by a process using API Application Programming Interface through software various and splendid graphic interfaces which cannot be expressed in a method using an existing OSD chip are expressed. Since every graphic layer and OSD information are formed on a single of layer a plurality of layers are combined into a single of layer in the existing hardware which definitely decreases bus proportion. The method of generating data in a process is sufficiently applied under the condition that a frequency of changing a graphic related video is 3 to 5 frames for a second.

The line information extractor receives input data on every layer e.g. layer layer and layer to be used for the graphic data and extracts line information on the graphic data in which all the layers are combined. The combined graphic layers which are composed of pixels horizontally and lines perpendicularly extract information on each line. For every line from the combined graphic layers the line information extractor determines whether OSD data exists whether it is appropriate to perform run length encoding whether a bitmap table is used and whether a line has the same data as that of an upper line extracts information thereon and generates the line information layer as shown in .

Referring to the line information layer has information on each line of data including the combined graphic layers. If the data including the combined graphic layers are composed of n lines the line information layer has n lines information. The respective line information includes information on whether OSD data exists information on whether a RLE Run Length Encoding is performed information on whether a bitmap table is used and whether it is the same as an upper line .

Information on whether OSD data exists is used when OSD data does not exist in a line and instead of the line being processed a next line is processed. Information on whether run length encoding is performed is used for performing the run length encoding when the run length encoding is more effective as data contained in the line is determined and thus the same data is very redundant. Information on whether a bitmap table is used is whether to regard each pixel data as an index of the bitmap table or whether to use the actual color value as it is. Information on whether it is the same as an upper line is used to employ the previous line data without reading the present line from a memory again in a decoding if the present line is made up of the same data as that of a previous line.

The line data extractor receives input data and alpha information on every layer i.e. layer layer and layer to be used for the graphic data and extracts line data therefrom. The line data includes information on pixels contained in each line. The information on each pixel includes pixel data i.e. a color value an alpha value to be applied to the pixel and information on which display device the pixel data is displayed. Since the OSD data and graphic layer data are integrated for use according to an embodiment of the present invention with respect to each pixel there is information indicating to which display device the pixel data is transmitted. For example as shown in the playback state date and user interface menu of the graphic data are all displayed on the LCD however the OSD information indicating the playback state and data is displayed only on the CRT. Accordingly each pixel includes information on a display device to which the pixel is transmitted so that the data indicating the playback state and the data is displayed on both a CRT and an LCD and the user interface menu is displayed on the LCD only.

An example of line data generated by the line data extractor is illustrated in . Referring to the line data includes alpha and mode information a partitioner color information and a partitioner .

The alpha and mode information includes information on an alpha value which is applied to each pixel and on a display device on which each pixel is displayed. The partitioner is an identifier to identify the alpha and mode information and the color information . The color information which is information to express the color of each pixel is comprised of a luminance signal and a color difference signal.

Each of the pixels has the alpha and mode information and color information. Referring to the alpha and mode information contains alpha and mode information on pixel 0 alpha and mode information on pixel 1 . . . and alpha and mode information on pixel M 1. If a bitmap table holds color information of each pixel the color information contains a bitmap index on pixel 0 a bitmap index on pixel 1 . . . and a bitmap index for pixel M 1.

The alpha and mode information on each of the pixels contains alpha information and mode information .

The alpha information indicates an alpha value to adjust the transparency of a pixel and the mode information contains information on a display device on which the pixel is displayed and information on whether the pixel is sampled at a rate of 4 4 4.

Referring to the mode information contains information on whether a pixel is displayed on an LCD information on whether a pixel is displayed on a CRT information on whether a pixel is displayed on other devices and information on whether a pixel is sampled at the rate of 4 4 4 . As in the system shown in the same data is not always displayed on more than two display devices such as the CRT and the LCD . For example with respect to a display device including a touch screen or scroll bar the display device has to include information for a menu and button etc. which are not indispensable for other display devices. Hence graphic control integrated data included in a memory contains information considering every condition. However it is required to determine whether a pixel is displayed on every display device. Information on a display device is included in the mode information which is merely an example. If other display devices are employed the corresponding information has to be included in the mode information.

Whether a pixel is sampled at the rate of 4 4 4 intends to handle a 4 4 4 sampling in an alpha blending considering that as an alpha blending operation is handled using quantized pixel information an image quality is reduced in a system which is expressed as 4 2 2 as shown in .

The run length encoder receives output line data from the line data extractor and performs run length encoding on every line. With regard to a line whose run length encoding is determined not to be performed in the line information extractor run length encoding is not performed on the line according to the information and the line is displayed on the line information and line data combiner .

Referring to line data includes alpha and mode information a partitioner color information and a partitioner .

The alpha and mode information contains run code run code . . . which are run length encoded. Each run code contains a flag indicating a run code a run count indicating a run length and a run value . The run value contains alpha information and mode information .

Each run code contains a flag indicating a run code a run count and a run value . The run value indicates a bitmap index . In line data run length encoding according to an embodiment of the present invention the alpha and mode information and color information are run length encoded separately and are partitioned by a partitioner.

Referring to each flag of run codes is expressed as 255 in an example of alpha and mode information in which the run length is encoded. A first run code indicates consecutive runs of 255 each having a run value of 0 and a second run code indicates consecutive runs of 32 each having a run value of 34.

Since 23 34 33 after the second run code has no flag of 255 they indicate the alpha information and mode information of an individual pixel. A next run code indicates consecutive runs of 255 each having a run value of 0. Since 34 33 after the run code has no flag of 255 they indicate the alpha information and mode information of an individual pixel. In the last six 0s two 0s are to comply with a unit of 32 bit and other four 0s are partitioners to partition the alpha and mode information and color information.

The postprocessor includes a line buffer a parser a run length decoder an alpha blender a 1 alpha blender an adder an alpha blender an adder an YCbCr2RGB and a scalar .

The line buffer reads the graphic control integrated data stored in the memory line by line and stores it. First the line buffer receives the line information of the graphic control integrated data .

The parser reads data stored in the line buffer and separates input data by lines which are run length encoded into their characteristics. First the parser reads line information stored in the line buffer and analyzes it.

Referring to line information includes the information on whether OSD data exists whether a RLE is performed the information on whether a bitmap table is used and the information on whether it is the same as an upper line .

The parser first analyzes the information on whether the OSD data exists in the line information if the OSD data exists controls to read line data corresponding to the line information and store it in the line buffer if the OSD data does not exist analyzes next line information since there is no need to read the line data. The information on whether the OSD data exists makes it possible to remove transmission of line which has no data for transmission thereby lowering the bus proportion.

The parser analyzes the information on whether a RLE is performed if a run length encoding is performed controls line data stored in the line buffer to be decoded by the run length decoder and if a run length encoding is not performed directly extracts detailed data i.e. alpha information mode information and color information included in the line data and transmits it to an alpha blender.

The parser analyzes the information on whether a bitmap table is used if the bitmap is used controls to find an index of a bitmap table not shown and get a color value corresponding to the index to be alpha blended in analyzing the color information of line data.

The parser analyzes whether it is the same as an upper line if the present line has the same data as that of an upper line line just previously decoded and does not read line data from a memory but uses the present line data stored in the line buffer . If the present line is determined to be identical to the upper line owing to the information the parser uses data included in the line buffer as it is without reading line data from the memory thereby lowering the bus proportion. If they are not identical to each other next line data is read from the graphic control integrated data stored in the memory and is stored in the line buffer . The run length decoder simultaneously decodes every stream separated from the parser and extracts or calculates alpha information mode information and color information.

As described referring to the mode information includes information on a display device on which a pixel is displayed. Based on the information on a display device included in the mode information an alpha value and color value are displayed on an alpha blender or an alpha blender . The alpha blender is for a display on the CRT and the alpha blender is for a display on the LCD. The mode information may include information on whether a pixel is to sample at the rate of 4 4 4. In a case where information on whether a pixel is to be sampled at the rate of 4 4 4 is set to use a 4 4 4 sampling an alpha blender is controlled to perform alpha blending using the 4 4 4 sampling thereby preventing an image quality from being decreased.

The alpha blender performs alpha blending by multiplying an alpha value and color value which are received from the run length decoder .

The 1 alpha blender receives input video data which are read from the memory and multiplies 1 alpha the video data by and performs alpha blending.

The adder adds graphic data received from the alpha blender and alpha blended and video data received from the 1 alpha blender and alpha blended and outputs it to the NTSC encoder .

The alpha blender performs the alpha blending by multiplying an alpha value and color value which are received from the run length decoder .

The adder adds graphic data received from the alpha blender and alpha blended and video data received from the 1 alpha blender and alpha blended and outputs it to the YCbCr2RGB .

The YCbCr2RGB converts a TCbCr format received from the adder into a RGB format and outputs it to the scalar . The scalar changes resolution of data received from the YCbCr2RGB to correspond to the LCD display device and outputs the converted data to the LCD controller . The NTSC encoder outputs data received from the adder to the CRT and the CRT displays the received data. The LCD controller outputs the data received from the scalar to the LCD and the LCD displays the received data.

Referring to the line information on graphic control integrated data is read from a memory and stored in a line buffer in Operation . A parser reads the line information stored in the line buffer in Operation . The parser analyzes line information on each line in Operation . Based on the line information analyzed by the parser line data is read from the memory and stored in the line buffer in Operation . Based on the analyzed line information the line data is run length decoded and is combined with video data in Operation .

Based on the analyzed line information a color space is converted and a scale is converted so that the combined data complies with the format of each display device and is displayed in Operation .

It is possible for the present invention to be realized on a computer readable recording medium as a computer readable code. Computer readable recording mediums include every kind of recording device that stores computer system readable data. ROM RAM CD ROM magnetic tape floppy disc optical data storage etc. are used as a computer readable recording medium. The computer readable recording mediums can also be realized in the form of a carrier wave e.g. transmission through Internet . A computer readable recording medium is dispersed in a network connecting computer system resulting in being stored and executed as a computer readable code by a dispersion method. A functional program code and code segments used to implement the present invention can be derived by a skilled computer programmer from the description of the invention contained herein.

While the present invention has been particularly shown and described with reference to exemplary embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the spirit and scope of the invention as defined by the appended claims. The exemplary embodiments should be considered in descriptive sense only and not for purposes of limitation. Therefore the scope of the present invention is defined not by the detailed description of the invention but by the appended claims and all differences within the scope of the present invention will be construed as being included in the present invention.

Data for a video display controller has a good much portion of a general multimedia device compared to other modules and a variety of effects are more increasing in order to support a variety of user environments.

Accordingly as described above the transmission capacity of a video data an OSD data and a graphic data for a variety of display devices is reduced thereby lowering a bus proportion. As a whole the power consumption required by systems is reduced thereby realizing to be suitable for a mobile device.

Although a few embodiments of the present invention have been shown and described it would be appreciated by those skilled in the art that changes may be made in these embodiments without departing from the principles and spirit of the invention the scope of which is defined in the claims and their equivalents.

