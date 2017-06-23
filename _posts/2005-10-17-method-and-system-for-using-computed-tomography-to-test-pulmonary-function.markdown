---

title: Method and system for using computed tomography to test pulmonary function
abstract: Computed axial tomography images of different respiratory phases of lungs are obtained, where the intensity of the image measures lung density. One image is deformed to the coordinate space of the other image, and the differences between the intensity values of the other image as compared to the mapped image are evaluated as measures of ventilation.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07668357&OS=07668357&RS=07668357
owner: Stanford University
number: 07668357
owner_city: Palo Alto
owner_country: US
publication_date: 20051017
---
This invention was made with government support under Contract Number CA093626 awarded by the National Institutes of Health. The Government has certain rights in the invention.

The present invention generally relates to methods and systems of determining pulmonary function and in particular to methods and systems using computed tomography.

Currently pulmonary ventilation is performed using single photon emission computed tomography SPECT a nuclear medicine imaging procedure which is more expensive and time consuming than computed axial tomography CAT scan or CT . Furthermore the resolution of SPECT is significantly poorer than that of CT. What is needed is a method for measuring lung ventilation that uses CT.

It is therefore an object of the present invention to measure pulmonary function using computed axial tomography CT .

This invention brings together two emerging technologies thoracic four dimensional computed tomography 4DCT and deformable image registration algorithms to devise a new clinical test for lung function. The lung function tests will show the difference in lung density between respiratory phases in different parts of the lung from which regions of small or no density change low ventilation can be identified.

Four dimensional computed tomography 4DCT acquisition methods that explicitly account for respiratory motion have been recently developed in academic and commercial settings. Similarly deformable image registration algorithms are evolving to the point of routine clinical utility. The combination of these two emerging technologies can be used as a pulmonary function test for ventilation by assessing the density differences of the same anatomic areas of the lung from CT scans acquired at different respiratory phases.

Due to the deformation of the lungs caused by respiration the CT scans at different respiratory phases referred to subsequently as inhale and exhale scans cannot be directly compared as the anatomy is in a different location in the two images. and respectively show exhale and inhale images. However deformable image registration algorithms can be applied to deform one respiratory phase to another. This is shown by the image in where the exhale image of is deformed into the inhale image of . This enables calculation of the density differences between the inhale image shown in and the deformed exhale image shown in based on the differences of the intensity values in the images and hence ventilation can be quantified.

For example let the exhale CT scan be given by I x and the inhale scan by I x . A transformation u can be found that maps the coordinate space of I x to I x via u x x . The ventilation can then be quantified by evaluating the difference between the two images I x I u x in the lung region.

Note that the vector displacement fields themselves and variations thereof could also be used to analyze lung function. Furthermore for this method it is prudent to use a deformable image registration algorithm which is not driven by minimizing intensity differences as such algorithms will artificially try to minimize the intensity difference which for this application is the quantity of interest.

A proof of principle example of this method is given in in which the exhale image has been deformed to the inhale image creating the image shown in . A subtraction of the deformed exhale image from the inhale image results in a difference image . A smoothing function is then applied to minimize the effects of CT artifacts and limitations in the image registration process resulting in a smoothed difference image .

While the invention has been described in terms of a single preferred embodiment those skilled in the art will recognize that the invention can be practiced with modification within the spirit and scope of the appended claims.

