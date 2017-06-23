---

title: Covert OFDM transmission using cyclic prefix
abstract: Methods for secure OFDM communications include changing the length of OFDM symbols in a pseudo-random fashion by appending a totally random signal to some of the OFDM symbols. An adaptive cyclic prefix is provided for covert and spectrally efficient communication. A developed PN based random data addition provides further security by removing the chance of combining synchronization information over several OFDM symbols.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08149685&OS=08149685&RS=08149685
owner: University of South Florida
number: 08149685
owner_city: Tampa
owner_country: US
publication_date: 20050902
---
This disclosure is a non provisional patent application based upon provisional patent application 60 522 235 filed Sep. 3 2004 by the same inventors and bearing the same title.

This work has been supported by Raytheon Inc. grant CHARTFIELD STRING USF01 TPA 22000 210600 000000 0000000 210610060.

This invention relates generally to security measures for wireless transmissions. More particularly it relates to methods for preventing synchronization to a transmitted signal by an unauthorized user.

Orthogonal frequency division multiplexing OFDM systems exhibit immunity to multipath distortion. In OFDM the linear convolution of a transmitted signal with a channel impulse response CIR is converted to circular convolution by cyclically extending the transmitted OFDM symbols. The transmitted data symbols are recovered using a simple one tap equalizer in the frequency domain. The redundancy introduced by cyclic prefix CP can be used for channel estimation and synchronization as well. However. CP may be undesirable for covert applications because unauthorized users may explore the periodicity introduced by the CP to synchronize to the transmitted signal.

To remove the distortion due to multipath the length of the CP should be larger than the maximum excess delay of the channel. When the length of the CP is smaller than the maximum excess delay previously transmitted OFDM symbols interfere with a current OFDM symbol as indicated in prior art . This type of interference is known as inter symbol interference ISI or interblock interference IBI and the performance degradation due to ISI is investigated in equations 1 and 2 below. The power spectral density of the interference is derived in terms of the CIR and the CP length in equation 1 . Assuming there are only post cursors from the preceding symbol the signal to noise ratio SNR of the received signal at each subcarrier position can be written as 

Where H k is the channel frequency response CFR at kth subcarrier N is the fast Fourier transform FFT size h is the nth tap of CIR and L is the length of the CIR.

As indicated by equation 1 the degradation depends on the ratio between the tail power of the CIR and total power of CIR as indicated in prior art which shows BER degradation as a function of guard interval length in a noiseless environment. The length of the power delay profile PDP is denoted 20 and it is assumed to be exponentially decaying. Calculating the SNR in each sub carrier and calculating the average BER provides theoretical results. As shows insufficient CP length causes irreducible error floor in OFDM.

The redundancy introduced by the CP can be used to estimate time and frequency offsets. Synchronization algorithms based on the maximum likelihood ML equation 3 minimum mean square error MMSE equation 4 and the maximum correlation MC equation 5 criteria use the periodicity introduced by the cyclic prefix to estimate the timing and frequency offsets.

The ML method is illustrated in where only one OFDM symbol is shown. The synchronization metric obtained by one OFDM symbol can be written as

where r n is the received signal Nis the length of CP and Nis the length of the useful data part. Using 2 the timing position can be found as max 3 

These estimates should be averaged over different OFDM symbols to obtain reliable estimates. Adding the correlation metrics from different symbols and dividing by the number of symbols provides the needed average. As the number of available OFDM symbols increase the estimates become more accurate. The resulting synchronization metric and the final metric obtained by averaging are shown in prior art where the effect of averaging is depicted.

The respective lengths of the OFDM symbol and CP can be estimated blindly by exhaustive searching. This knowledge gives undesired or unauthorized users the ability to synchronize to the transmitted signal. prior art shows the magnitude of the synchronization metric as a function of different CP and OFDM symbol sizes. As indicated in the peak occurs when the hypothesized lengths are equal to the correct lengths.

The periodicity inherently introduced by the usage of CP can be explored by undesired users to synchronize to the transmitted signal.

Accordingly what is needed in the art is a technique that prevents unauthorized synchronization while maintaining the advantages of the CP.

However in view of the prior art considered as a whole at the time the present invention was made it was not obvious to those of ordinary skill in this art how the needed additional security could be provided.

The novel methods maintain the advantages of the cyclic prefix but prevent unauthorized exploitation of the cyclic prefix CP for synchronization. By allowing use of the CP the novel methods provide secure data transmission by lowering coding requirements thus providing high data transmission rates and decreased power consumption.

In a preferred embodiment the size of the CP is changed adaptively depending upon channel conditions and random signals are appended to some of the orthogonal frequency division multiplexing OFDM symbols in a pseudo random manner to scramble the correlation peaks in the time domain.

When the correlation peaks are scrambled in time unauthorized users who are not privy to the scrambling pattern cannot combine the synchronization information with the different symbols. The novel method therefore prevents unauthorized detection of the transmitted signal even if an unauthorized user achieves an initial synchronization.

The present invention makes wireless transmission more secure so that undesired users cannot probe transmitted information. This is especially important for military defense applications. Moreover commercial wireless system providers may incorporate this invention for the prevention of theft of service or for increasing user privacy.

More particularly the novel method for preventing unauthorized exploitation of a cyclic prefix for synchronization while maintaining the advantages of the cyclic prefix includes the step of

changing the length of OFDM symbols in a pseudo random fashion by appending a random signal to at least one of the OFDM symbols. The invention further includes the steps of providing extra scrambling of the correlation peaks by changing the size of the random signal depending on a PN sequence reducing bandwidth loss due to transmission of the random signal by using a known PN sequence using the known PN sequence in an authorized receiver for synchronization increasing the immunity to the multipath by changing the length of the CP in each OFDM symbol according to a PN sequence thereby scrambling the correlation peaks combining the adaptive cyclic prefix with channel coding making the cyclic prefix smaller than a maximum excess delay of the channel compensating for a performance loss by providing additional coding power providing additional coding power by using very tight coding and changing the FFT IFFT sizes of each OFDM symbol based on a PN sequence thereby providing two types of security by making synchronization and demodulation of a received signal difficult for unauthorized users.

Insufficient CP causes performance degradation and enables undesired users to synchronize to the transmitted signal as the length of the CP gets larger. Therefore the present invention changes the length of the CP adaptively depending upon channel conditions. The length of the CP should be just enough to prevent ISI. By using a small CP the present invention prevents synchronization of undesired users to the transmitted signal.

This adaptation requires knowledge of the maximum excess delay of the wireless channel that can be estimated using CFR 6 or channel frequency correlation CFC 7 . The length of the CP can be constant over a burst and the length information can be conveyed to the receiver by signaling. Changing the length of the CP adaptively also provides efficient channel utilization since the overall CP time is minimized.

In practical applications extraction of the synchronization parameters by using the CP with only one OFDM symbol is difficult if not impossible because the CP is perturbed by multipath components and additive noise. Moreover the presence of frequency offset decreases the correlation between the repeated parts. To overcome this problem averaging over a number of OFDM symbols is performed. shows the noisy correlation outputs from different OFDM symbols and the resulting synchronization metric that is obtained by averaging said correlations. The instantaneous correlations are noisy and the resulting metric obtained by averaging has a peak around the correct timing point which is zero.

Averaging over different OFDM symbols can be done if the length of each OFDM symbol is precisely known.

The present invention changes the length of OFDM symbols in a pseudo random fashion by appending a totally random signal to some of the OFDM symbols. An integrated circuit having a processor generates the totally random signal and appends it to more than one OFDM symbol of a plurality of OFDM symbols in a frame so that the OFDM symbols in said plurality of OFDM symbols in said frame do not have a common length and so that correlation peaks are scrambled. The resulting frame structure and correlation peaks in a noiseless static channel is illustrated in where the length of the CP is N the length of the data is N and the length of the appended random signal is R. Using this method the correlation peaks are scrambled in time. This prevents undesired users from using the CP for synchronization since they cannot combine the information from different symbols as is possible with prior art systems. Even if an initial synchronization is obtained for the arriving frame the receiver needs to know the exact start positions of the individual OFDM symbols. This is possible if the positions and lengths of the added random signals are known. An authorized user on the other hand can extract the transmitted information since the way the OFDM symbols are scrambled is known. The novel method prevents an unauthorized user from estimating the length of the CP and useful data by executive search method see as well.

A pseudo noise PN based preamble is used for synchronization. Since only an authorized user knows the transmitted signal unauthorized users cannot synchronize to the transmitted signal. Furthermore the receiver can use the knowledge of scrambling pattern and the redundancy contained in the CP to obtain synchronization information by combining the correlation outputs from each OFDM symbol. Authorized users combine the synchronization information from the preamble and from the CP using an appropriate technique.

The decision on whether to append a random signal to a specific OFDM symbol or not can be made by using the transmitted preamble sequence or by using the spreading and or scrambling codes of users in MC CDMA. If none of those are available the transmitter must select some specific codes and convey the required information to the receiver.

1. Provide extra scrambling of the correlation peaks by changing the size of the random signal depending on a PN sequence.

2. Reduce the bandwidth loss due to the transmission of the random signal by using a known PN sequence Instead of a totally random signal. The known PN sequence is used in an authorized receiver for synchronization.

3. Increase the immunity to the multipath by changing the length of the CP in each OFDM symbol according to a PN sequence thereby scrambling the correlation peaks.

4. Combine the adaptive cyclic prefix with channel coding. The cyclic prefix does not have to be the same as the maximum excess delay of the channel. It can be smaller but not larger for security purposes . If it is smaller the performance loss must be compensated for by additional coding power. In the limiting case no CP is used and the 1 51 is compensated by using very tight coding.

5. Change the FFT IFFT sizes of each OFDM symbol based on a PN sequence. This provides two types of security by making synchronization and demodulation of received signal difficult for unauthorized users.

It will thus be seen that the advantages set forth above and those made apparent from the foregoing description are efficiently attained and since certain changes may be made in the above construction without departing from the scope of the invention it is intended that all matters contained in the foregoing description or shown in the accompanying drawings shall be interpreted as illustrative and not in a limiting sense.

It is also to be understood that the following claims are intended to cover all of the generic and specific features of the invention herein described and all statements of the scope of the invention that as a matter of language might be said to fall therebetween. Now that the invention has been described 

