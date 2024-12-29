# VIX-UVXY-Trading-Opportunities

The VIX, often referred to as the 'fear gauge' measures the market's expectation of future volatility (hence implied volatility) in the S&P 500 index (SPX). It's calculated based on SPX options' implied volatility. The higher the VIX, the more volatility traders expect in the market.
UXVY is a leveraged ETF (this is important to note) that aims to provide twice the daily performance of the VIX. The fact that it's an ETF means that it won't track the VIX perfectly, and the fact that it is leveraged means that it loses its price over time. The latter is no issue as nobody holds these financial instruments long-term. The part about it not tracking the VIX perfectly can be used to trade. Here is something perhaps interesting...
Plotted VIX/UVXY over last 10 years:

![VIX:UVXYratio](https://github.com/user-attachments/assets/098392c1-3f61-4170-abe8-a851759ca59a)

This can show us where price-discrepancies between VIX and UXVY are. Notice recently, on December 17, there was a mismatch between the price ratio of UXVY and the VIX. The VIX spiked and UXVY didn't follow until VIX was eroding into mean-reversion.
The ratio itself is increasing which is due to the fact that the price of UXVY decreases. You can attempt at calculating the rate of change using knowledge of contango and backwardation but I won't go into that right now but perhaps later, as it's not important for what I'm about to illustrate.

We can apply a fast Fourier transform (FFT) on the ratio to try detect repetition in divergence of UXVY vs VIX. This decomposes the 'signal' into its frequency domain, which we can use to compute something called the 'spectral entropy'.
The spectral entropy then tells us how the information-theoretic uncertainty, and hence predictability of the frequencies:
We calculate the spectrum $X(\omega_i)$ of our VIX/UVXY ratio, and then the Power Spectral Density by squaring the amplitude of our signal/ratio and normalizing by the number of bins.
$$P(\omega_i)=\dfrac{1}{N}\left|X(\omega_i) \right|^2$$
This can be viewed as a Probability Density Function, with $p$ defined as
$$p_i=\dfrac{P(\omega_i)}{\sum_iP(\omega_i)}$$
such that we can meaningfully attribute a Shannon entropy as
$$H_{\text{Spectral}} = -\sum_i p_i\ln(p_i)$$
![VIX:UXVY-entropy2024](https://github.com/user-attachments/assets/09fefc48-4754-4b54-9032-c45af89eedc2)
Notice how the same day as the spike in the VIX/UVXY ratio, which indicates a tracking error, the spectral entropy decreased, indicating a greater predictability in frequencies of divergences. This is empirically seen to be a lag of UVXY for certain moves in the VIX. These periods of greater predictability happen somewhat often, and it seems to always take the UXVY fund a while to match the VIX properly again.

![VIX:UXVY-entropy2012-2024](https://github.com/user-attachments/assets/0a1fe70c-4c00-4772-acb5-1fbf1a4ad50b)

