---

title: Systems and methods for adjusting spot color inks
abstract: Systems and methods are provided for printing a spot ink. The spot ink may be prepared before the time of printing. The spot ink may be adjusted by half-toning or supplemental CMYK colors at the time of printing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07639393&OS=07639393&RS=07639393
owner: Xerox Corporation
number: 07639393
owner_city: Norwalk
owner_country: US
publication_date: 20050629
---
Spot color inks are used to achieve a specific color more accurately than process mixtures of cyan magenta yellow black CMYK to avoid the halftone pattern associated with process color printing or to print colors outside the gamut of CMYK. A spot color ink also called spot ink provides a pre mixed color ink that is directly printed instead of a color that is obtained by halftoned levels of CMYK components at the time when the color is being printed. Spot color inks are common in the offset printing trade and are becoming available for digital production color systems. Typically spot color inks are offered in the colors of popular samples based color systems. For example a user may acquire a particular spot ink color by selecting the color from a suite of samples of existing spot ink colors.

Spot color inks are often selected to ensure the accuracy of a specific color. For example the red color of Xerox Corporation s logo is specified as Pantone 032. Many of Xerox s printed collaterals and packaging are printed with offset or flexographic inks specifically formulated to achieve this unique red color.

The standards for color accuracy for spot color inks are becoming higher necessitating tight color tolerances on ink manufacturers and on the vendors of printing systems using spot color inks. There are product acquisition costs associated with meeting those tight color tolerances and market costs for failing to meet those tight color tolerances.

It is difficult to manufacture printing systems and inks that are capable of achieving accurate color matches. This difficulty is multiplied by the large number of spot colors to be made available. For example the number of spot colors available from the most popular vendor is more than 1 000. It is estimated that if a day is required for a manufacturer to print test for color accuracy it may take four work years devoted solely to the validation process.

Using methods that are currently available color differences of 10 E ten times the perceptible color difference or more have been observed resulting in customer dissatisfaction and its associated costs. Accordingly an improved yet inexpensive method for achieving customers high standards for spot color accuracy is needed.

This disclosure discloses exemplary systems and methods for printing a spot color ink also referred to alternatively in this disclosure as spot ink . For example a method of printing a spot ink may include determining whether a difference between an actual color of the spot ink and an intended color is within a tolerance level and if the determined difference is not within the tolerance level adjusting the color of the spot ink.

This and other features and details are described in or are apparent from the following detailed description.

Systems and methods may be provided for adjusting colors of rendered or prepared spot inks by halftone adjustment of the spot colors at time of printing or by adding supplementary CMYK inks at time of printing. Such systems and methods may reduce the need for infeasibly tight ink manufacturing tolerances as well as allow customers to fine tune colors to achieve specific color preferences.

The spot color inks that are to be adjusted at time of printing may be conventionally prepared rendered or otherwise formulated prior to the time of printing. The spot color inks may be prepared to achieve a color match with respective intended colors as close as economically feasible.

Adjustments may be made to the prepared spot color inks at time of printing. The adjustments may be achieved by halftoning dithering or the like. The adjustments may include adding or reducing a shade of a color in an area of interest by adding or removing a color by adding or removing selected pixels of an area so as to achieve a visual result that is the same as if a shade of the color had been added to the whole area. The adjustments may be made to the spot color inks. The adjustments may also be made using supplementary CMYK inks.

The color adjustments may be controlled in a manner similar to those conventionally used to adjust process color simulations of spot colors such as for example direct control of color area coverages. The adjustments may also be controlled to translate perceptual inputs physical color measurements or psychophysical color measurements to device specific changes. The physical color measurements are those that are based on the physical properties of the image for example reflectance. The psychophysical color measurements are those that transform physical measurements into quantities correlating to human visual perception for example CIELAB.

The adjustment may be made in a single step or in a loop of steps to approach a desired result. The adjustment may also be made by first producing a set of adjusted colors with for example different supplementary CMYK inks and combinations before selecting one adjusted color from the set of adjusted colors.

When a spot ink is prepared to be close to a desired color half tone addition or subtraction of colorants may be subtle. Thus the amount of added supplementary colors which may be referred to as noise to uniform tints may be minimized. For example an occasional spot of C M Y or K may be adequate to bias the color in the desired direction.

The half tone based adjustments may provide flexibility to move in most directions in color space for most colors. However there may be constraints with highly chromatic colors because there is no color vector in the direction of higher chroma. Thus a spot ink may be formulated with a recipe that is slightly modified to err on the side of excess chroma. The systems and methods for adjusting spot color inks may then adjust by diminishing the excess chroma by moving the colors toward a neutral axis in the color space. Alternatively or additionally the systems and methods for adjusting spot color inks may reduce the excess chroma by using print engine control of developed mass or ink thickness.

Next in step S a difference between the actual color of the spot ink and a desired color is determined. The determination may be made automatically by a device. The determination may alternatively be made by a visual inspection performed by a user. The method then proceeds to step S.

In step S it is determined whether the difference E is greater than a tolerance level E. If the difference is not greater than the tolerance level there is no need to adjust the color. Accordingly the method goes to step S where the method of color adjustment ends and printing starts.

On the other hand if it is determined at step S that the difference is greater than the tolerance level the method proceeds to step S.

In step S a further determination is made whether to generate adjustment options. If it is determined that adjustment options are not to be generated the method proceeds to step S where an adjustment is made to reduce the difference. Thereafter the method returns to step S.

On the other hand if it is determined at step S that adjustment options are to be generated the method proceeds to step S. In step S adjustment options are generated. For example a set of color adjustments may be generated by a variety of half tone or dithered adjustment to either the spot color ink or supplementary CMYK inks.

It will be appreciated that in fact step S may be an implicit step rather than requiring actual processing or an actual decision. For example if the system is not capable of generating adjustment options then of course step S is unnecessary and the system process would proceed directly to step S. If the system is capable of generating adjustment options then the process may actually proceed directly from step S to step S. If the system is capable of generating adjustment options but does not necessarily always present the options for selection then the determination of whether to generate adjustment options may be based on one or more predetermined criteria such as 1 the magnitude of the difference between E and E 2 the color e.g. adjustment options may be generated for specialty blue colors but not specialty red colors or vice versa or the like.

Next in step S a color adjustment is selected from the adjustment options such as the set of color adjustments. The selection may be automatically performed by a device based on for example a minimum of the differences between each of the adjusted colors and the desired color. The selection may alternatively be made manually by a user with a visual comparison among the adjustment options. Thereafter the method returns to step S. However in some embodiments the method may directly proceed to step S without returning to step S.

The method illustrated in may be implemented in a computer program product that can be executed on a computer. The computer program product may be a computer readable recording medium on which a control program is recorded or it may be a transmittable carrier wave in which the control program is embodied as a data signal.

The input output interface may interface with an input device and an output device . The input device and output device may be connected to the system via links and respectively. The memory may store data made available by the input output interface the adjustor the comparator and the selector . The memory may also store spot color information and tolerance level information.

In operation under the control of controller the input output interface may receive a color in the form of for example electronic information output by a spectrophotometer that has measured a color sample. The color may be compared by the comparator with information representing a desired color. The desired color information may be stored in the memory . The desired color information may also be input from the input device .

Based on the comparison the comparator may determine a difference between the received color and the desired color. The comparator may further compare the determined difference with a tolerance level.

When the difference is greater than the tolerance level the adjustor may make adjustments under the control of controller . The adjustment may be made in a single color direction in the color space toward the desired color. The adjustment may also be made in a form of a set of color adjustments.

When the adjustor makes a set of color adjustments the selector under control of the controller may select one color adjustment from the set of color adjustments. Compared to the other color adjustments in the set of color adjustments the selected color adjustment may have for example the smallest color difference with the desired color.

The set of color adjustments may also be output through output device to a user. For example each of the adjusted colors from the set of color adjustments may be displayed to the user. The user may select a color adjustment based on for example a visual inspection of the set of adjusted colors.

After a color adjustment is made the adjusted color may be output for feedback before a second run of adjustment. The adjustment may also be analyzed to decide whether the adjusted color is within the tolerance level with respect to the desired color before the adjusted color is output. For example the color adjustment may be repeated automatically to achieve a satisfactory tolerance level before being output.

It will be appreciated that various of the above disclosed and other features and functions or alternatives thereof may be desirably combined into many other different systems or applications. Also various presently unforeseen or unanticipated alternatives modifications variations or improvements therein may be subsequently made by those skilled in the art which are also intended to be encompassed by the following claims.

