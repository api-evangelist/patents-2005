---

title: Method and construction for space-time codes for AM-PSK constellations
abstract: Space-time codes are developed for multi-radii AM-PSK constellations. Further, a “super-unified” space-time code construction is developed that incorporates multi-radii AM-PSK codes with the Lu-Kumar unified codes. The multi-radii space-time codes achieve the rate-diversity tradeoff—that is, the codes transmits information at the maximum rate possible for the given signaling constellation and the achieved transmit diversity level.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07471742&OS=07471742&RS=07471742
owner: The Johns Hopkins University
number: 07471742
owner_city: Baltimore
owner_country: US
publication_date: 20050330
---
This application is based on and claims the benefit of prior filed Provisional U.S. Application No. 60 557 589 filed on Mar. 30 2004 the entire contents of which are incorporated herein by reference.

This invention was made with Government support under Grant No. CCR 0325781 awarded by the National Science Foundation. The Government has certain rights in the invention.

The invention relates generally to PSK modulated space time codes and more particularly to the method and construction of space time codes for AM PSK constellations.

Recent advances in coding theory include space time codes which provide diversity in multiple input multiple output MIMO antenna systems over fading channels with channel coding across a small number of transmit antennas. For wireless communication systems a number of challenges arise from the harsh RF propagation environment characterized by channel fading and co channel interference CCI . Channel fading can be attributed to diffuse and specular multipath while CCI arises from reuse of radio resources. Interleaved coded modulation on the transmit side of the system and multiple antennas on the receive side are standard methods used in wireless communication systems to combat time varying fading and to mitigate interference. Both are examples of diversity techniques.

Simple transmit diversity schemes in which for example a delayed replica of the transmitted signal is retransmitted through a second spatially independent antenna and the two signals are coherently combined at the receiver by a channel equalizer have also been considered within the wireless communications industry as a method to combat multipath fading. From a coding perspective such transmit diversity schemes amount to repetition codes and encourage consideration of more sophisticated code designs. Information theoretic studies have demonstrated that the capacity of multi antenna systems significantly exceeds that of conventional single antenna systems for fading channels. The challenge of designing channel codes for high capacity multi antenna systems has led to the development of space time codes in which coding is performed across the spatial dimension e.g antenna channels as well as time.

Space time codes are designed for MIMO communication systems that employ multiple transmit antennas to achieve spatial diversity. The modulated code words are often presented as complex values M T matrices in which the m t th entry srepresents the discrete baseband signal transmitted from the m th transmit antenna at time t. The initial work on space time codes by Guey et al. and Tarokh et al. showed that the transmit diversity achieved by a space time code is equal to the minimum rank among the set of matrices produced as differences between distinct modulated code words. There is a tradeoff between achievable transmission rate and achievable transmit diversity level for space time codes. Full rank space time codes can achieve transmission rates no greater than one symbol per transmission interval. For rank d space time codes the maximum transmission rate is M d 1 symbols per transmission interval. Equivalently the size of an M T rank d space time code cannot exceed q where q is the size of the signaling constellation. Codes meeting this upper limit are referred to as maximal.

In U.S. Pat. No. 6 678 263 Hammons and El Gamal developed the so called binary rank criteria that allowed for the first time the algebraic design of space time codes achieving maximal spatial diversity of all orders. The binary rank criteria for BPSK and QPSK modulated space time codes are based on the observation that the difference between two modulated code words will be of full rank as a matrix over the complex field C whenever a certain binary projection of the difference matrix is of full rank over the binary field GF 2 . From the binary rank criteria Hammons and El Gamal developed the general Stacking Construction for full diversity space time codes examples of which include block codes derived from Galois fields rings and rate 1 M convolutional codes of optimal d. The binary rank criteria showed that the algebraically designed full rank BPSK modulated space time codes could be lifted to full rank QPSK modulated space time codes. In particular Hammons and El Gamal showed that if the linear binary codes A and B produce full rank space time codes when BPSK modulated then the quaternary code C A 2B produces a full rank space time code under QPSK modulation. They referred to this construction as the Dyadic Construction.

Building on the Hammons El Gamal framework Liu et al. showed how the same techniques could be extended to 4 QAM constellations. Thereafter Lu and Kumar developed a generalization of that framework applicable to both the 4 QAM and the general 2 PSK cases. They showed that the Dyadic Construction extends to 2 PSK modulation in the natural way i.e. if the linear binary codes A A . . . Aproduce full rank space time codes under BPSK modulation then the 2 ary code

Dual radii AM PSK constellations offer potential significant advantages over conventional PSK constellations. For example Belzer et al. show that the 8 ary AM PSK constellation consisting of two PQSK rings in a star configuration provides significantly higher capacity on partially coherent AWGN Rayleigh and Rician fading channels. However nothing in the prior art teaches the development of general space time code constructions for AM PSK constellations or the unification of such constructions with the Lu Kumar space time codes for PSK and QAM constellations. Accordingly it would be desirable to be able to utilize space time code constructions for AM PSK constellations especially such codes that are optimal with respect to the rate diversity tradeoff.

In accordance with the present invention space time codes are developed for multi radii AM PSK constellations. Further a super unified space time code construction is developed that incorporates multi radii AM PSK codes with the Lu Kumar unified codes. The multi radii space time codes achieve the rate diversity tradeoff that is the codes transmits information at the maximum rate possible for the given signaling constellation and the achieved transmit diversity level.

Throughout the drawing figures like reference numerals will be understood to refer to like parts and components.

Referring to by way of an example a conventional digital cellular Direct Sequence Code Division Multiple Access DSCDMA base station to mobile station or forward link is shown using a conventional convolutional encoder and Viterbi decoder. also illustrates the mobile station to base station or reverse link.

At the transmit end the system in comprises a data segmentation and framing module where user information bits are assembled into fixed length frames from transmit data blocks . The N bits per frame are input to the base station s convolutional encoder of rate r which produces N r code symbols at the input of the channel interleaver . The channel interleaver performs pseudo random shuffling of code symbols and outputs the re arranged symbols to the spread spectrum modulator . The spread spectrum modulator uses a user specific transmit PN code generator to produce a spread spectrum signal which is carried on a RF carrier to the transmitter where a high power amplifier coupled to the transmit antenna radiates the signal to the base station. The techniques of spread spectrum modulation and RF transmission are well known art to one familiar with spread spectrum communications systems.

The signal received at the mobile station antenna is amplified in the RF receiver and demodulated by the spread spectrum demodulator which uses the same PN code generator as used by the base station transmitter to de spread the signal. The demodulated symbols are de interleaved by the channel de interleaver and input to the Viterbi decoder . The decoded information bits are reconstructed using data block reconstruction into receive data blocks and forwarded to the data terminal equipment at the receive end.

With reference to a digital cellular base station to mobile station link is shown to illustrate the implementation of space time encoding and decoding in accordance with an embodiment of the present invention. While CDMA system is used as an example one familiar with the art would consider the present invention applicable to other types of wireless systems which can employ other types of multiple access methods such as frequency division multiple access FDMA time division multiple access TDMA and hybrid methods.

Transmit data blocks from the data terminal equipment are segmented and framed into fixed frame length and applied to the mobile s channel space time encoder . The output from a channel encoder is fed to the space time formatter which determines the parsing allocation and presentation order of the coded symbols to the various transmit antennas . The spatial formatter output is applied to the spread spectrum modulator which uses a user specific PN code generator to create spread spectrum signals carried on a RF carrier via base RF transmitter to the mobile station transmitter. The transmitter with high power amplifier coupled to the Transmit antenna radiates the signals via separate transmit antennas to the mobile station.

The signal received at one or more mobile station antenna s is amplified in the mobile RF receiver and demodulated in a phase shift keying demodulator which uses the same PN code generator as used by the base station transmitter to de spread the signal. The demodulated symbols are processed at space time decoder by the space time de formatter and input to the channel decoder . The decoded information bits are reconstructed into receive data blocks and forwarded to the data terminal equipment at the receive end. Depending on the space time code used the de formatter and the decoder can be grouped in a single maximum likelihood receiver.

With continued reference to the source generates k information symbols from a discrete alphabet X on the path which are encoded by an error control code C by the space time encoder . The space time encoder produces code words of length N over the symbol alphabet Y. The encoded symbols are mapped by the modulators and so on onto constellation points from a discrete complex valued signaling constellation for transmission across the channel. The modulated radio frequency signals for all of the L transmit antennas and so on are transmitted at the same time to the receiver space time demodulator . The space time channel decoder decodes the signals to the received data path . As shown the receiver provides M receive antennas to collect the incoming transmissions. The received baseband signals are subsequently decoded by the space time decoder .

The present invention is concerned primarily with the design of space time codes rather than the signal processing required to decode them. In most cases the decoding employs known signal processing for maximum likelihood detection.

In the following discussion notation is established and certain key ideas of the Lu Kumar approach upon which the novel space time code constructions of the present invention are built are explained. Following the discussion of the Lu Kumar approach new constructions of space time codes for dual radii and multi radii AM PSK constellations in accordance with the present invention are described. In addition the novel AM PSK constructions of the present invention are extended to produce a generalized AM PSK code construction framework that includes the unified Lu Kumar construction.

Let C be a code of length MT with M T over the discrete alphabet . The codewords of C are presented as M T matrices in which the m t th entry a represents the information symbol that is modulated and transmitted from the m th transmit antenna at transmission interval t. If all of the modulated code word matrices have rank at least d over C then the space time code is called an M T rank d code. In the special case that all of the modulated code words are of full rank M the space time code is called an M T full rank code.

There is a tradeoff between achievable transmission rate and achievable transmit diversity level for space time codes. Full rank space time codes can achieve transmission rates no greater than one symbol per transmission interval. For rank d space time codes the maximum transmission rate is M d 1 symbols per transmission interval. Equivalently the size of an M T rank d space time code cannot exceed q where q is the size of the signaling constellation . Codes meeting this upper limit are referred to as maximal.

The work of Lu and Kumar established a general mathematical framework for the method of algebraic space time code design initiated by Hammons and El Gamal in which the rank of modulated code words over the field C is inferred from the rank of their projections as matrices over the binary field F. The Lu Kumar framework makes use of the ring Z of algebraic integers associated with a primitive complex root of unity .

The 2 PSK constellation consists of the points s a Z 0 1 2 . . . 2 1 where is a complex primitive 2 th root of unity. The connection between modulated space time codes with entries from Z C and binary codes over the field F 0 1 is through the isomorphism Z 1 F. The function Z F denotes the corresponding projection modulo 1 . The set of M T matrices over an alphabet is denoted by . When A a is a matrix with integer entries is written for the matrix whose i j th entry is . For matrices A and B the matrix A B is their Hermitian i.e. componentwise product.

The following propositions present the core technical facts underlying the Lu Kumar approach to space time code design over Z . The first two results highlight key elementary properties of the ring Z . The following two results are the Lu Kumar generalization of the Hammons El Gamal binary rank criteria.

Proposition 1 Let be a complex primitive 2 th root of unity. Let s where m and n are integers. Then 1 s in Z . Furthermore 

On the right hand side of this equation there are n m terms each projecting to 1 modulo 1 . Hence mod1 .

Proposition 3 Let C be complex M T matrix M T with entries from Z . If the binary projection C is of full rank over F then C is of full rank over the field of complex numbers C.

Proof Suppose C is singular over C. Then all M M submatrices of C have zero determinants. Since the determinant calculations may be regarded as taking place in the subfield Q C where Q is the set of rational numbers then C is also singular as a matrix over Q . Therefore there exists a nonzero vector y Q for which yC 0 in Q . From y one may derive a vector x Z such that i xC 0 in Z and ii not all components of x are divisible by 1 . Then x C 0 in F establishes that C is singular.

Corollary 4 Let C be complex M T matrix M T with entries from Z . If the binary projection C is of rank d over F then C is of rank at least d over C.

Proof If C has rank less than d then every d T submatrix of C is singular. By the previous argument every d T submatrix of C is also singular over F.

The following are novel codes for multi radii PSK constellations in accordance with the present invention.

The novel space time code construction of the present invention is a generalization of the basic dyadic construction for 2 PSK. A first version of this construction gives optimal M T space time codes of full rank.

In order to establish the claim that S achieves diversity M it suffices to show that the difference between any pair of distinct modulated code words is of full rank over C. Let S r and S r be distinct code words in S and let S S S .

By choice of the code A the matrix A A is of full rank over F. Hence by proposition 3 S is of full rank over C.

By Propositions 1 and 2 the terms in parentheses are scalars in Z or matrices with entries in Z . Since 0 mod 1 we have from Proposition 1

By the choice of the matrix C C is of full rank over F. Hence by Proposition 3 S is of full rank over C which completes the proof.

Implicit in statement and proof of Theorem 5 is the fact the construction is not degenerate Code words of S depend uniquely on choice of component code words and the two PSK rings do not intersect non trivially. The underlying signaling constellation associated with the dual radii construction is the set of complex numbers .

The parameterization of by a c is considered non degenerate if the mapping a c s is 1 1. Less precisely it can be said that the constellation supporting the space time code S is non degenerate if its implied parameterization is non degenerate.

In Theorem 5 the choice of radius r guarantees the non degeneracy of the underlying dual radii 2 PSK constellation. With its two rings of 2 PSK this constellation is capable of conveying at most K 1 bits per channel use. The new construction therefore achieves the rate diversity tradeoff i.e. the dual radii 2 PSK codes transmit information at the highest rate consistent with the achieved diversity level.

The full rank construction is readily modified to provide space time codes of rank d that also achieve the rate diversity tradeoff.

Theorem 6 Dual Radii Construction II In the Dual Radii Construction let binary code A and the binary codes Cbe maximal M T rank d codes with d M T. Then the modulated space time code S achieves transmit diversity d and transmission rate R K 1 M d 1 bits per channel use.

Now let S S S where S r and S r are distinct code words in S. Depending on whether C C or C C one of the congruences of equations 3 and 6 still holds. By Corollary 4 S is therefore of rank at least d over C. Since S achieves the maximum transmission rate for a space time code having transmit diversity d it can be concluded that S achieves transmit diversity exactly d.

The following is a novel variation on the Dual Radii Construction in which the choice of the 2 ary matrix C also determines the binary matrix A. In this case the underlying constellation is non degenerate but of smaller size than in the previous construction. These codes also achieve the rate diversity tradeoff.

Proof That the achieved transmit diversity is at least d follows the same argument as before. Unlike the prior construction however with this choice for A the underlying constellation consists of two rings of 2 PSK instead of 2 PSK. Hence the achieved transmission rate is the maximum possible for a diversity d space time code over this constellation. Consequently the achieved transmit diversity must be exactly d.

Remark. In Corollary 7 the mapping may be replaced by an arbitrary mapping C F. In this case S still achieves transmit diversity at least d. Whether or not S achieves the rate diversity tradeoff depends on the choice of .

The dual radii 2 PSK construction can be extended to provide novel space time codes for multi radii AM PSK constellations.

Proof When the underlying constellation is non degenerate it consists of 2rings of 2 PSK so the transmission rate achieved by S is clear. Therefore it suffices to show that S achieves diversity at least d.

Note that in Z whenever i j so the fraction on the right in 14 is an algebraic integer. To show that S is of rank at least d over C there are two cases to consider.

Observing that all of the partial products and are congruent to 1 mod 1 and all but the first of the coefficients

Case 2. C C . Equations 2 and 13 differ only in the choice of the matrix D. In the proofs of Theorems 5 and 6 for this case the argument that S is of rank at least d over C does not depend on D.

Remark. As a special case of Theorem 8 we may take Z such that 0 mod 1 and set r 2 1 for i 1 2 . . . L. Representative examples of the constellations supporting this construction are given below.

The Special A construction may be generalized in many different ways for the multi radii constellations. The following version is representative.

Proof If non degenerate the underlying constellation consists of 2rings of 2points and S achieves the rate diversity tradeoff.

Remark. In corollary 9 we may take A C where the . . . C Fare arbitrary functions. In this case S still achieves transmit diversity at least d. Whether or not S achieves the rate diversity tradeoff depends on the choice of the . One may also consider hybrids of Theorem 8 and Corollary 9 in which some of the Aare derived from the matrix C and others are freely chosen from a maximal rank d binary code.

Examples. In the new dual radii and multi radii space time code constructions the underlying AM PSK constellations are determined by the algebraic integers used as the basis for the signaling. are constellation diagrams for representative 8 ary 16 ary 32 ary and 64 ary cases. When the constellation is normalized to unit average energy the Euclidean distance between the closest constellation points can be used as a convenient figure of merit to judge the relative efficiency of the constellation. provides a list of representative AM PSK constellations corresponding to the constellation diagrams of . In the case of the multi radii constructions the examples are for the special case . . . for which r 2 1. Improvements in the normalized minimum distance should be expected if the are chosen without restriction.

For comparison with these representative AM PSK examples the normalized minimum distances for 2 PSK are as follows 1.4142 for QPSK 0.7654 for 8 PSK 0.3902 for 16 PSK 0.1960 for 32 PSK and 0.0981 for 64 PSK. For 4 QAM the corresponding normalized minimum distances are 1.4142 for 4 QAM QPSK 0.6325 for 16 QAM and 0.3086 for 64 QAM. One sees that for the moderate and intermediate constellation sizes the new AM PSK space time codes fill a useful gap not covered by the Lu Kumar unified construction.

The Lu Kumar unified space time code construction generalizes the basic 2 PSK dyadic construction to produce space time codes for 2 PAM 4 QAM and other exotic higher order constellations by proper choice of design parameters. Remarkably these codes achieve the rate diversity tradeoff. The Lu Kumar unified construction may be extended to an even more general construction that includes the novel multi radii 2 PSK codes of the present invention plus their generalization to other constellations . In general the space time codes produced by the novel super unified construction of the present invention also achieve the rate diversity tradeoff. For ease of presentation the unification results are described in two parts. First the simpler dual radii case is discussed followed by a discussion of the general multi radii case.

Let be a non zero complex number and be a complex primitive 2 th root of unity. Choose non zero 2Z and Z such that in Z and 1 0 mod 1 . Set r 2 1. Then the modulated space time code defined by

The terms in parentheses on the right hand side are either scalars in Z or matrices with entries in Z . The two rightmost summands are congruent to 0 mod 1 . Hence 

Remark. When r 1 the resulting construction is the Lu Kumar unified construction. By proper choice of parameters the Lu Kumar unified construction provides space time codes that achieve the rate diversity tradeoff for 2 PAM 4 QAM and 2 PSK constellations specifically for PAM one chooses the parameters 2 K 1 U m 1 1 for QAM one chooses 2 K 2 U m 1 i i and for PSK one chooses 2 K m U 1 1 e. The dual radii 2 PSK codes arise from the super unified construction by taking r 1 along with the indicated PSK selecting parameters in the Lu Kumar construction.

Let C C . . . C A be a function that maps U tuples of non binary codeword matrices to binary M T matrices the range A being arbitrary.

Let be a non zero complex number and be a complex primitive 2 th root of unity. Choose non zero 2Z and Z such that in Z and 0 mod 1 . Set r 2 1. Then the modulated space time code defined by

Theorem 12 Let A A . . . Abe maximal M T rank d binary codes with M T. Let K and U be positive integers and let C 0 u

Let be a non zero complex number and be a complex primitive 2 th root of unity. Choose non zero 2Z and . . . Z such that 0 mod 1 for all i 1 2 . . . L. Furthermore we require that in Z and 0 mod 1 . Set

Proof The main points of the proof are briefly sketched. Following the partial product notation introduced in the proof of Theorem 8 let

When the argument is the same as case 1 in the proof of Theorem 8 with the indicated changes in the initial partial products.

When the argument is the same as in the proof of Theorem 10 except that the matrix D in 18 is now given by 14 .

Remark. As a corollary to Theorem 12 there is again the Special A construction in which one or more of the binary matrices Aare derived as functions of the nonbinary matrices C. The statement of this result is clear from the prior examples Corollaries 7 9 and 11 so is omitted for brevity.

Using the ring Z of algebraic integers as the basis for signaling and exploiting the isomorphism Z 1 F Lu and Kumar developed a broadly applicable generalization of the Hammons El Gamal method of algebraic space time code design in which the rank of modulated code words over the field C is inferred from the rank of their projections as matrices over the binary field F. The Lu Kumar unified space time code construction extended the Hammons El Gamal dyadic construction for QPSK modulated space time codes to provide codes achieving the rate diversity tradeoff for all 2 PSK and 4 QAM signaling constellations. Applicant herein has used the Lu Kumar framework to design novel space time codes that achieve the rate diversity tradeoff for multi radii AM PSK constellations which fill a useful gap not covered by the Lu Kumar unified construction. Applicant has also developed a novel super unified space time code construction that unites both the Lu Kumar unified codes and the new multi radii AM PSK codes in a single novel framework providing optimal space time codes.

The AM PSK constellations consisting of two or more rings of PSK modulation are of interest to communication systems requiring higher spectral efficiency than typical PSK modulated systems and less stringent transmitter receiver linearity requirements than typical QAM modulated systems. One major aspect of the present invention provides optimal space time code constructions that can be used with these modulation formats by MIMO communications systems to achieve higher transmission rates and greater reliability over wireless channels Another major aspect of the present invention provides a generalized AM PSK code construction that is also optimal with respect to the rate diversity tradeoff and provides through choice of parameters optimal codes for PAM PSK QAM and multi radii PSK modulation formats. This generalized construction enables a flexible MIMO communication system that can adapt its choice of modulation to meet system demands and channel capabilities while still providing optimal space time coding.

