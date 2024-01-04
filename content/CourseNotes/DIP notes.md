---
title: Digital Image Processing Notes
date: 2024-01-04
draft: false
author: HNO3
---
**Table of Contents**

- [[#Chapter 1 Introduction|Chapter 1 Introduction]]
	- [[#Chapter 1 Introduction#Basic Concepts|Basic Concepts]]
	- [[#Chapter 1 Introduction#orientation|orientation]]
- [[#Chapter 2 Vision & Vision Properties|Chapter 2 Vision & Vision Properties]]
	- [[#Chapter 2 Vision & Vision Properties#vision from low level|vision from low level]]
	- [[#Chapter 2 Vision & Vision Properties#vision in high level|vision in high level]]
	- [[#Chapter 2 Vision & Vision Properties#vision properties|vision properties]]
	- [[#Chapter 2 Vision & Vision Properties#color space|color space]]
- [[#Chapter 3 Image Digitalization|Chapter 3 Image Digitalization]]
	- [[#Chapter 3 Image Digitalization#quantization & sampling|quantization & sampling]]
	- [[#Chapter 3 Image Digitalization#quantization|quantization]]
- [[#Chapter 4 Image Transforms|Chapter 4 Image Transforms]]
	- [[#Chapter 4 Image Transforms#Discrete Fourier Transform (DFT2)|Discrete Fourier Transform (DFT2)]]
	- [[#Chapter 4 Image Transforms#Discrete Cosine Transformation (DCT)|Discrete Cosine Transformation (DCT)]]
	- [[#Chapter 4 Image Transforms#DHT|DHT]]
	- [[#Chapter 4 Image Transforms#Karhunen-Loeve Transform (KLT)|Karhunen-Loeve Transform (KLT)]]
	- [[#Chapter 4 Image Transforms#DWT|DWT]]
- [[#Chapter 5 Image Enhancement|Chapter 5 Image Enhancement]]
	- [[#Chapter 5 Image Enhancement#spatial domain filtering|spatial domain filtering]]
	- [[#Chapter 5 Image Enhancement#frequency domain filtering|frequency domain filtering]]
- [[#Chapter 6 Image Restoration|Chapter 6 Image Restoration]]
	- [[#Chapter 6 Image Restoration#image degradation model|image degradation model]]
	- [[#Chapter 6 Image Restoration#restoration in the presence of noise only|restoration in the presence of noise only]]
	- [[#Chapter 6 Image Restoration#inverse filtering|inverse filtering]]
	- [[#Chapter 6 Image Restoration#Wiener filtering / minimum mean square error filtering|Wiener filtering / minimum mean square error filtering]]
	- [[#Chapter 6 Image Restoration#constrained least squares filtering|constrained least squares filtering]]
	- [[#Chapter 6 Image Restoration#geometric image transformation|geometric image transformation]]
- [[#Chapter 7 Image Segmentation|Chapter 7 Image Segmentation]]
	- [[#Chapter 7 Image Segmentation#connectivity|connectivity]]
	- [[#Chapter 7 Image Segmentation#segmentation methods|segmentation methods]]
- [[#Chapter 8 Morphological Image Processing|Chapter 8 Morphological Image Processing]]
	- [[#Chapter 8 Morphological Image Processing#binary morphology|binary morphology]]
	- [[#Chapter 8 Morphological Image Processing#gray-scale morphology|gray-scale morphology]]
- [[#Chapter 9 Image Compression|Chapter 9 Image Compression]]
	- [[#Chapter 9 Image Compression#fundamental concepts|fundamental concepts]]
	- [[#Chapter 9 Image Compression#image data redundancy|image data redundancy]]
	- [[#Chapter 9 Image Compression#model of image compression|model of image compression]]
	- [[#Chapter 9 Image Compression#digital image watermark|digital image watermark]]
- [[#what's going on in past exam|what's going on in past exam]]

## Chapter 1 Introduction

### Basic Concepts

$$ I=f\left(x,y,\lambda,t\right)$$,where
- $I$: illuminance, represents the spatial energy distribution of an image source of radiant enenrgy
- $x$, $y$: coordinates
- $\lambda$: wavelength
- $t$: time

Both spatial coordinates and amplitude of $I$ are *finite* and *discrete*, and it's called digital image. The basic unit is *pixel*, each of which has a particular *location* and *value*

### orientation

- Narrow sense of DIP —— improvement of <font color="#00b050">image quality</font> for human interpretation, <font color="#00b050">processing of image</font> data for storage, transmission, display and representation for machine perception
- Broad sense of DIP —— includes fields where image processing ends and <font color="#00b050">image analysis</font> and <font color="#00b050">image understanding</font> starts (higher levels than narrow sense)

## Chapter 2 Vision & Vision Properties

### vision from low level

- Visual band of electromagnetic spectrum is 350 nm～780 nm
- *retina* translate 2D image into impulses
- *optical nerve* sends impulses into brain to create visual perception
- *receptors*: <font color="#00b050">rods</font> and <font color="#00b050">cones</font>
	- *rod*: thin and long, ~120 million, Scotopic Vision (暗视觉), high sensitivity, achromatic (非彩色的), low acuity (敏度) (spatial acuity), connected to brain in <font color="#00b050">group</font>
	- *cone*: thick and short, 6~7 million, Photopic Vision (明视觉), lower absolute sensitivity, chromatic (彩色的), high acuity, connected to brain <font color="#00b050">single</font>, 3 types.
- trichromatic theory
	- people perceive color can be considered as combination of RGB

### vision in high level

- <font color="#00b050">past experience</font> involves in current perception
- "thinking is part of perception"

### vision properties

- visual phenomena
	- intensity (contrast sensitivity, <font color="#00b050">nonlinear</font> ➡ modulation transfer function ➡ lower sensitivity to high and low spatial frequency, <font color="#00b050">rotationally variant</font>; simultaneous contrast, brightness dependent on intensity of <font color="#00b050">surroundings</font>)
	- wave length (chromatic adaptation, perceived color is dependent on the <font color="#00b050">wavelength composition of surrounding</font> light)
	- color spectrum
	- spatial frequency change
- mach band
	- brightness is <font color="#00b050">not a monotonic function</font> of luminance
	- imperfect response to high-spatial-frequency brightness transitions
- critical fusion frequency
	- fast flickers cannot be distinguished
	- depends on surrounding light
- relative luminous efficiency function
- monochrome vision model
	- color = brightness + chromaticity
	- chromaticity = hue + saturation
	- radiance, lluminance, brightness ➡ energy
	- hue: attribute of light
	- saturation: <font color="#00b050">relative purity</font> or amount of white light mixed with a hue
- color matching-Grassman's axioms
	- any color can be matched by mixture of < 3 color lights
	- color match at one radiance level holds over a wide range of levels
	- luminance of a color mixture is equal to the sum of the luminance of its components
	- RGB / CYM
- colorimetry –trichromatic theory
	- metamerism: $$ I_i(f)=\intop_{\lambda_{\min}}^{\lambda_{\max}}f(\lambda)V_i(\lambda)d\lambda,\quad i=1,2,3$$, if two different light sources with different spectral energy distribution $f(\lambda)$, if their $I$ is the same, then they are same color

### color space

- RGB: cube
- CMY: C = 1 - R, M = 1 - G, Y = 1 - b
- CMYK: $$ C=1.0-R-\boldsymbol{u}K_b\quad\quad M=1.0-\boldsymbol{G}-\boldsymbol{u}K_b\quad\quad Y=1.0-\boldsymbol{B}-\boldsymbol{u}K_b\quad\quad K=\boldsymbol{b}K_b$$, where $K_b = min\{1-R, 1-G, 1-B\}$
- HSI (hue, saturation, intensity): decouple intensity, natural to human /HSV (hue, saturation, value)
	- conversion from RGB to HSI: $H=\begin{cases}\theta&if~B\leq G\\360-\theta&if~B>G\end{cases}$, $\theta=\cos^{-1}\left\{\frac{\frac12(R-G+R-B)}{\sqrt{(R-G)^2+(R-B)(G-B)+\varepsilon}}\right\}$, $S=1-\frac3{R+G+B}[\min(R,G,B)]$, $I=\frac13(R+G+B)$
	- conversion from HSI to RGB: $$ X=I\bigg[1+\frac{S\cos H'}{\cos(60°-H')}\bigg]$$ 
$$ Y=I(1-S)$$ 
$$ Z=3I-(X+Y)$$ $$ H^{\prime}=H\mathrm{~mod~}120\quad\quad H\in[0^{\circ},360^{\circ}]$$ $$ quotient=\begin{cases}0&X,Y,Z&->R,B,G\\1&X,Y,Z&->G,R,B\\2&X,Y,Z&->B,G,R&\end{cases}$$ $$ H\div120=quotient\cdots H^{\prime}$$

## Chapter 3 Image Digitalization

digitalization: two stages, *sampling* + *quantization*
- sampling: $f(x,y)$ (continuous) ➡ $f(m,n)$
- quantization: $f(x,y)$ ➡ $I(x,y)$

representation in this chapter:
- image size: $M\times N$, gray scale $G$, satisfying: $M=2^m,\quad N=2^n,\quad G=2^k$
- bytes required to store this image: $2^{m+n-3}k$

image quality assessment
- *fidelity*: comparison between processed image and original image
- *intelligibility*: information conveyed
- calculation: $$ K=\frac{\int_{-Lx}^{Lx}\int_{-Ly}^{Ly}f(x,y)\hat{f}(x,y)dxdy}{\int_{-Lx}^{Lx}\int_{-Ly}^{Ly}f^2(x,y)dxdy}$$, where $K$ is normalized cross correlation function. then root-mean-square error & mean-square signal-to-noise ratio are often used: $$ e_{rms}=\sqrt{\frac1{MN}\sum_{i=0}^{N-1}\sum_{j=0}^{M-1}\left\{Q[f(i,j)]-Q[\hat{f}(i,j)]\right\}^2}$$, where $Q(f)=K_1\log_b[K_2+K_3f(i,j)]$; and $$ SNR_{rms}^2 = SNR_{ms}=\frac{\sum_{i=0}^{N-1}\sum_{j=0}^{M}\mathcal{Q}\left[\hat{f}(i,j)\right]^2}{\sum_{i=0}^{N-1}\sum_{j=0}^{M-1}\left\{\mathcal{Q}\left[\hat{f}(i,j)\right]-\mathcal{Q}[f(i,j)]\right\}^2}$$

### quantization & sampling

quantization: 
![[DIP notes-20231216-1.png|400]]
less levels of the same color

sampling:
![[DIP notes-20231216-2.png|400]]
less pixels for a image or one pixel has larger area in the original image


#### sampling
![[DIP notes-20231216-3.png|400]]
- signal spectrum has square shape: rectangular sampling is most efficient.
- 2D sampling-reciprocal lattices: sampling periodically with equal intervals in any <font color="#00b050">two directions in space domain</font>, the corresponding spectrum also repeats periodically with equal intervals in two <font color="#00b050">frequency directions</font>
	- $U^TV=2\pi I$
![[DIP notes-20231217-1.png|450]]

sampling efficiency
- density: under the condition of lossless, calculate the number of samples per unit area
	- $S.D.=\dfrac{1}{det(V)}=\dfrac{det(U)}{4\pi^2}$

### quantization
- definition: process between analog samples and discrete-valued samples is called quantization
- $d$: decision level, $r$: reconstruction level, $r_i=Q(d_i)$, then the quantization error is $e=d-Q(d)$, and quantization noise is $\varepsilon^2=E[e^2]$

*scalar quantization*: given number of reconstruction levels $k$, design a quantizer and optimize its loss
- optimal mean square error quantizer, loss function: $\boldsymbol{\varepsilon}^2=\sum_{i=0}^{k-1}\int_{z_i}^{z_{i+1}}(z-q_i)^2p(z)dz$.
- linear quantization: Separate \[z0 ,zk) into k sub-intervals，each of which is of the same length, uniform quantization is the optimal quantization if z is uniformly distributed.

*vector quantization*: also called block quantization or pattern matching quantization: encode values from a vector space into a finite set of values from a discrete <font color="#00b050">subspace of lower dimension</font> (less storage space or <font color="#00b050">compressed</font>), and this is usually done via <font color="#00b050">projection</font> or using <font color="#00b050">codebook</font>.

*halftoning*: used in printing, this process reduce visual reproductions to an image that is printed with only <font color="#00b050">one color</font> of ink, utilizing <font color="#00b050">optic illusion</font> and perceptual <font color="#00b050">grayscale</font>, which will sacrifice <font color="#00b050">resolution</font>

*Dither*: applying noise used to randomize quantization error


## Chapter 4 Image Transforms

### Discrete Fourier Transform (DFT2)

formula: 
DFT:$$ F(u,\nu)=\frac{1}{\sqrt{MN}}\sum_{x=0}^{M-1}\sum_{y=0}^{N-1}f(x,y)e^{-j2\pi(ux/M+vy/N)}$$

IDFT:
$$ f(x,y)=\frac{1}{\sqrt{MN}}\sum_{u=0}^{M-1}\sum_{v=0}^{N-1}F(u,v)e^{j2\pi(ux/M+yy/N)}$$

properties of DFT
- $|F(u, v)|$ has even symmetry about the origin, aka $|F(u,v)| = |F(-u,-v)|$
- conjugate symmetric ($f$ is real function): $F^*(u,v)=F(-u,-v)$, $F(u,v)=F^*(-u,-v)*$
- $F(0,0)$ is the <font color="#00b050">DC component</font>, represents the <font color="#00b050">average value</font> of the image
- <font color="#00b050">translation</font> has no effect on the spectrum of $F(u, v)$
- <font color="#00b050">rotation</font>: if $f$ rotate for $x$ degree, then $F$ will rotate for the same degree
- applying DFT <font color="#00b050">twice</font> = rotate image by 180 degree
- <font color="#00b050">centering</font> the FT: $DFT[f(x,y)(-1)^{x+y}]=F(u-M/2,v-N/2)$
- <font color="#00b050">separability</font>: 2D DFT can be computed by twice 1D DFT

from DFT to DCT: DFT is impractical to implement complex domain, so we just take the real part of transformation kernel ➡ DCT

### Discrete Cosine Transformation (DCT)
- DCT express function or signal in terms of sum of sinusoids with different frequencies and amplitudes
- formula
	- DCT: $$ F(u,v)=C(u)C(v)\sqrt{\frac{2}{MN}}\sum_{x=0}^{M+1}\sum_{y=0}^{N+1}f(x,y)\cos\biggl[\frac{\pi}{M}u\biggl(x+\frac{1}{2}\biggr)\biggr]\mathrm{cos}\biggl[\frac{\pi}{N}v\biggl(y+\frac{1}{2}\biggr)\biggr]$$
	- IDCT: $$ f(x,y)=\sqrt{\frac2{MN}}\sum_{u=0}^{M-1}\sum_{v=0}^{N-1}C(u)C(v)F(u,v)\cos\left[\frac\pi Mu(x+\frac12)\right]\cos\left[\frac\pi Nv(y+\frac12)\right]$$
- properties
	- forward/inverse transformation kernel are the <font color="#00b050">same</font>
	- transformation kernel is <font color="#00b050">separable</font> $F = G\cdot f \cdot G^T$
	- <font color="#00b050">flipping</font> has no effect on the 2D DCT spectrum of an image
- application of DCT
	- lossy compression, keep most of the low frequency components, due to its "energy compaction" property

### DHT

Hadamard Transform: a generalized class of Fourier transforms
- decomposes input signal into a superposition of <font color="#00b050">Walsh functions</font>
	- Walsh matrix: entries of the matrix are either +1 or −1 and its rows as well as columns are <font color="#00b050">orthogonal</font> (dot product is zero)
	- Walsh function: each <font color="#00b050">row</font> of a Walsh matrix correspond to a Walsh function

DHT ([reference video](https://www.youtube.com/watch?v=eWFC8rU1z10))
- formula
	- DHT: $$ H(u,\nu)=\frac1N\sum_{x=0}^{N-1}\sum_{y=0}^{N-1}f(x,y)(-1)^{\sum_{i=0}^{n-1}[b_i(x)b_i(u)+b_i(y)b_i(v)]}$$
	- IDHT: $$ f(x,y)=\frac{1}{N}\sum_{u=0}^{N-1}\sum_{v=0}^{N-1}H(u,\nu)(-1)^{\sum_{i=0}^{n-1}[b_i(x)b_i(u)+b_i(y)b_i(v)]}$$, where image $f$ is $N\times N$, $N = 2^n$, $b_k(z)$ is the value of the $k$th bit of $z$ in binary representation
- calculation: $H = G \cdot f \cdot G$, and $f = G \cdot H \cdot G$
	- $G$ can be calculated by $G_{N} = \dfrac{1}{\sqrt{N}}\begin{bmatrix}H_{N/2}&H_{N/2}\\H_{N/2}&-H_{N/2}\end{bmatrix}$, where $H_2 = \dfrac{1}{\sqrt{2}}\begin{bmatrix}1&1\\1&-1\end{bmatrix}$
- properties
	- forward and inverse transformation kernel of DHT are the same
	- DHT is separable
- ordering schemes of Walsh function
	1. sequency: can be derived from the ordering of the Hadamard matrix by first applying the bit-reversal permutation and then the Gray-code permutation OR: label each row's <font color="#00b050">number of sign changes</font> and <font color="#00b050">re-order</font> the rows in ascending order. eg: $\begin{bmatrix}1&1&1&1&1&1&1&1\\1&-1&1&-1&1&-1&1&-1\\1&1&-1&-1&1&1&-1&-1\\1&-1&-1&1&1&-1&-1&1\\1&-1&-1&1&1&-1&-1&1\\1&1&1&1&-1&-1&-1&-1\\1&-1&1&-1&-1&1&-1&1\\1&1&-1&-1&-1&-1&-1&1\\1&-1&-1&1&-1&1&1&-1\end{bmatrix}$ ➡ $\begin{bmatrix}1&1&1&1&1&1&1&1\\1&1&1&1&-1&-1&-1&-1\\1&1&-1&-1&-1&-1&1&1\\1&1&-1&-1&1&1&-1&-1\\1&-1&-1&1&1&-1&-1&1\\1&-1&-1&1&1&-1&-1&1\\1&-1&-1&1&-1&1&1&-1\\1&-1&1&-1&-1&1&-1&-1\\1&-1&1&-1&1&-1&1&-1\end{bmatrix}$
	2. Hadamard (as shown in previous section)
	3. dyadic

### Karhunen-Loeve Transform (KLT)

KL theorem
- representation of a stochastic process as an infinite linear combination of <font color="#00b050">orthogonal functions</font>, $X_t=\sum_{i=1}^\infty Y_ie_i(t)$
- <font color="#00b050">coefficients</font> in the KL theorem are <font color="#00b050">random variables</font> and the expansion <font color="#00b050">basis</font> depends on the process, allowing it to adapt to process
- <font color="#00b050">orthogonal functions</font> determined by <font color="#00b050">covariance function</font> of the process

empirical version is known as <font color="#00b050">KL Transform</font> (coefficients computed from samples), closely related to principal component analysis (PCA)
- covariance: $$ \begin{aligned}&C_x=\frac1L\sum_{i=1}^L(X_i-m_x)(X_i-m_x)^\mathrm{T}=\frac1L\left[\sum_{i=1}^LX_iX_i^\mathrm{T}\right]-m_xm_x^\mathrm{T}\\&\boldsymbol{m}_x=E\{\boldsymbol{X}\}=\frac1L\sum_{i=1}^LX_i\end{aligned}$$, where $X_i$: $i$ th sample vector, $L$ is the size of sample set
	- image size: $M\times N$, size of $C_x$: $MN \times MN$, size of $m_x$: $MN\times 1$
- diagonalize covariance matrix: $$ C_x\to\{\lambda_i,\vec{u}_i\}\quad\quad P=\begin{bmatrix}\vec{u}_1,...,\vec{u}_i,...\end{bmatrix}^T$$, $Y = P(X-m_x)$, $X = P^TY+m_x$
- arrange eigenvalues in descending order, KL approximation is the one that minimize total mean square error $\varepsilon=\sum_{i=K+1}^{N\times N}\lambda_i$
- pros and cons of KL transform
	- pro: decorrelates the original signal
	- con: computational cost, not suitable for data with a non-Gaussian/non-exponential probability distribution

### DWT

wavelets and wavelet transform: often used to replace conventional Fourier transform
- wavelet: small waves of varying frequencies and limited duration
- wavelet transform vs. FT: both frequency-localized, and wavelet transform have an additional <font color="#00b050">time-localization </font>property

Short-time Fourier Transform (STFT)
- formula: $$ \mathrm{WFT}_{\int}(b,\omega)=\frac1{\sqrt{2\pi}}\int_{R}f(x)W^{*}(x-b)\mathrm{e}^{-\mathrm{j}\omega x}\mathrm{d}x$$, where $W$ is windowing function, and inverse STFT: $$ f(x)=\frac{1}{\sqrt{2\pi}}\iint_{R^2}\mathrm{WFT}_f(b,\omega)W(x-b)\mathrm{e}^{\mathrm{i}ox}\mathrm{d}\omega\mathrm{d}b$$
- STFT has <font color="#00b050">fixed</font> resolution
	- <font color="#00b050">width</font> of the windowing function relates to how the signal is represented
- why DWT: wavelet transform and <font color="#00b050">multiresolution</font> analysis can give good time resolution for high-frequency events and good frequency resolution for low-frequency events, the combination best suited for many real signals

DWT
- image pyramid
	- collection of <font color="#00b050">decreasing resolution</font> images arranged in the shape of a pyramid, used for representing images at more than one resolution
- subband coding
	- An image is <font color="#00b050">decomposed</font> into a set of <font color="#00b050">bandlimited</font> components, called subbands. The subbands can be reassembled to <font color="#00b050">reconstruct</font> the original image without error
- wavelet series: representation of a square-integrable (real or complex-valued) function by a certain orthogonal series generated by a wavelet: $\psi_{a,b}(x)=|a|^{\frac12}\psi{\left(\frac{x-b}a\right)}$, where $\psi$: mother wavelet has a finite-length or fast-decaying oscillating waveform, $a$ and $b$ are scaling and translation parameters
- basic idea: use some small but well known wavelets as <font color="#00b050">probes</font> to compare its similarity with the signal (image). By scaling & translation the detection can have different scales.

## Chapter 5 Image Enhancement

definition: process of manipulating an image so that the result is <font color="#00b050">more suitable</font> than the original for a specific <font color="#00b050">application</font>. These techniques are <font color="#00b050">problem oriented</font>

image enhancement techniques are designed based on <font color="#00b050">heuristic</font> procedures to manipulate an image in order to utilize <font color="#00b050">psychophysical</font> aspects of human visual system

spatial domain processing
- spatial filtering: sharpening / smoothing
	- neighborhood processing techniques (eg. convolution)
	- point processing ($\cdot$)
- intensity transformation: contrast manipulation, thresholding

frequency domain processing
- 2D filter (LPF for smoothing, HPF for sharpening)

### spatial domain filtering
#### histogram (intensity transformation techniques
- definition: <font color="#00b050">estimate</font> of the <font color="#00b050">probability</font> of occurrence of each intensity level in an image
- $$ P(r_k)=\frac{n_k}{MN},\quad k=0,1,...,L-1$$, where $MN$: the total number of pixels, $r_k$: $k$th intensity value, $n_k$: number of pixels with intensity $r_k$, $L$ is number of possible intensity levels
- *histogram equalization*: [geeksforgeeks ref](https://www.geeksforgeeks.org/histogram-equalization-in-digital-image-processing/) <font color="#00b050">mapping</font> original PDF to another whose distribution is more uniform. spread the histogram of the input image, resulting a <font color="#00b050">contrast enhancement</font> $$ s_{k}=T(r_{k})=(L-1)\sum_{i=0}^{k}p_{r}(r_{j})=(L-1)P_{r}^{\prime}(k)=\frac{L-1}{MN}\sum_{i=0}^{k}n_{j}$$
	- ![[DIP notes-20231217-2.png|550]] (这个图公式是不是有点问题...rounding那里不应该加0.5的)
- *histogram modification*
	- histogram specification: uniform histogram is not best choice
	- method used to generate a processed image that has a specified histogram is called histogram specification
	- procedure
		1. histogram equalization
		2. find transformation function for the specified histogram
		3. compute histogram of given image
		4. compute all values of transformation function and store them in a table
		5. convert the histogram of given image to the new image based on the values in the table
	- ![[DIP notes-20231217-3.png|600]]

#### image smoothing

- create an <font color="#00b050">approximating function</font> that attempts to <font color="#00b050">capture important patterns</font> in the data, while <font color="#00b050">leaving out noise</font> or other fine-scale structures/rapid phenomena
- can be done in either spatial domain or frequency domain

smoothing spatial filters
- smoothing linear filters (average filters / LPFs)
	- box filters: $$ h_1=\frac19\begin{bmatrix}1&1&1\\1&1&1\\1&1&1\end{bmatrix}\quad h_2=\frac1{10}\begin{bmatrix}1&1&1\\1&2&1\\1&1&1\end{bmatrix}\quad h_3=\frac1{16}\begin{bmatrix}1&2&1\\2&4&2\\1&2&1\end{bmatrix}$$
- order-statistic(<font color="#00b050">nonlinear</font>) filters --- median filter
	1. sort values of pixels in the m neighborhood pixels
	2. determine their median
	3. assign that value to the corresponding pixel in the filtered image

#### sharpening spatial filters

- Laplacian: $g=f-k\nabla^2f$
- unsharp masking and highboost filtering: $g = f - \bar{f}$, $f' = f+kg$, where $g$ is unsharp mask
- gradient

### frequency domain filtering

- Low frequencies in the transform domain are related to <font color="#00b050">slowly varying intensity</font> components
- High frequencies are caused by <font color="#00b050">sharp transitions</font> in intensity, such as <font color="#00b050">edges</font> and noise
- LPF would <font color="#00b050">blur</font> an image
- HPF would enhance <font color="#00b050">sharp detail</font>, but cause a <font color="#00b050">reduction</font> in <font color="#00b050">contrast</font> in the image

homomorphic filtering
- a generalized technique involving a <font color="#00b050">nonlinear mapping</font> to a different domain in which <font color="#00b050">linear filter</font> techniques are applied, followed by <font color="#00b050">mapping back</font> to the original domain
- simultaneously <font color="#00b050">normalizes the brightness</font> across an image and <font color="#00b050">increases contrast</font>
- Illumination and reflectance combine multiplicatively: $$ \begin{aligned}f(x,y)&=f_i(x,y)\cdot f_r(x,y)\\\\0&<f_i(x,y)<\infty\\\\0&<f_r(x,y)<1\end{aligned}$$
	- $f_i$ and $f_r$ are not separable, but their approximate locations in frequency domain can be located
	- $$ g(x,y)=F^{-1}\{T[F[f(x,y)]]\}$$
## Chapter 6 Image Restoration

goal of restoration: from degraded image to original image

evaluation of restoration: compare the difference between original image and recovered image

traditional vs. modern image restoration
- traditional: stable, linear position invariant, prior knowledge of signal and noise required
- modern: not stable, non-linear, no prior knowledge required

### image degradation model
![[DIP notes-20231217-4.png|450]]
- $G(u,v) = H(u,v)F(u,v) + N(u,v)$
- restoration: given $g$ and some information about $H$ and $n$, and try to obtain an estimate $\hat{f}$ of original image
- property of $H$
	- linear
		- additivity
		- homogeneity: $$ H[k_1f_1(x,y)+k_2f_2(x,y)]=k_1H[f_1(x,y)]+k_2H[f_2(x,y)]$$
	- position invariant: $$ H[f(x-a,y-b)]\quad=\quad g(x-a,y-b)$$

$$ g(x,y)=\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}f(\alpha,\beta)h(x,\alpha,y,\beta)d\alpha d\beta+n(x,y) $$
- simplify: $g=Hf+n$
- $h(x,\alpha,y,\beta)$: impulse response of $H$, referred to as <font color="#00b050">point spread function</font> (PSF)
- size: $f$ is $A\times B$, $h$ is $C\times D$, by zero padding, they are extended to $(A+C-1)\times(B+D-1)$

### restoration in the presence of noise only
- remove <font color="#00b050">periodic noise</font>: can be reduced significant <font color="#00b050">frequency domain</font> filtering, <font color="#00b050">parameters</font> of noise can be estimated by inspection of <font color="#00b050">Fourier spectrum</font> of the image
- noise PDF estimation: <font color="#00b050">intensity values</font> in the noise component may be considered random variables characterized by PDF

### inverse filtering
$$ G(u,v)=H(u,v)F(u,v)+N(u,v)$$  $$ \hat{F}(u,\nu)=F(u,\nu)+\frac{N(u,\nu)}{H(u,\nu)}$$
### Wiener filtering / minimum mean square error filtering
- error measure: $e^2 = E[(f - \hat{f})^2]$
- best estimation: $\hat{F}(u,\nu)=\left[\frac1{H(u,\nu)}\cdot\frac{|H(u,\nu)|^2}{|H(u,\nu)|^2+K}\right]G(u,\nu)$

### constrained least squares filtering
$$ \begin{aligned}\min_{\hat{f}}\left\{\hat{f}^TC^TC\hat{f}\right\}&=\sum_{x=0}^{M-1}\sum_{y=0}^{N-1}\left[\nabla^2\hat{f}(x,y)\right]^2\\\\s.t.\quad\left\|\boldsymbol{g}-\boldsymbol{H}\hat{\boldsymbol{f}}\right\|^2&=\left\|\boldsymbol{n}\right\|^2\end{aligned}$$
solution: $\hat{f}_e=\left(\begin{bmatrix}\dot{h}_e\end{bmatrix}^T\begin{bmatrix}\dot{h}_e\end{bmatrix}+\alpha\begin{bmatrix}\dot{C}_e\end{bmatrix}^T\begin{bmatrix}\dot{C}_e\end{bmatrix}\right)^{-1}\begin{bmatrix}\dot{h}_e\end{bmatrix}^T\mathbf{g}_e$

residual: $r = (g-H\hat{f})$, $\psi(y)=r^Tr=||r||^2$
1. specify initial value of $y$
2. compute $\psi(y)$
3. keep this process until this condition is satisfied: $$ \left\|r\right\|^2=\left\|n\right\|^2\pm a$$, or after $$ \mathrm{increasing~}\gamma\quad\mathrm{if}\quad\left\|r\right\|^2<\left\|n\right\|^2-a$$, return to step 2, or after $$ \text{decreasing }\gamma\quad\mathrm{if}\quad\left\|r\right\|^2>\left\|n\right\|^2+a$$
4. use new value of $\gamma$ to compute $\psi(y)$


$$ \hat{F}=\frac{\boldsymbol{G}}{\boldsymbol{H}}\quad\quad\quad\hat{F}=\left[\frac{H^*}{\mid H\mid^2+\gamma[S_n/S_f]}\right]G\quad\quad\quad\hat{F}=\left[\frac{H^*}{\mid H\mid^2+\gamma\left|P\right|^2}\right]G$$
- observation first
- experimentation
- mathematical modeling

example: blue caused by uniform linear linear motion
$$ g(x,y)=\int_0^Tf[x-x_0(t),y-y_0(t)]dt$$
$$ G(u,v)=F(u,\nu){\int_0^T\exp\{-j2\pi[ux_0(t)+\nu y_0(t)]\}dt} \\ = F(u,v)H(u,v)$$


### geometric image transformation
- Image translation, scaling, rotation
- Generalized linear geometrical transformation
- Affine transformation
- Perspective transformation

geometric image modification
- <font color="#00b050">shear parallel</font> to $x1$ axis: $$ \begin{bmatrix}y_1\\y_2\end{bmatrix}=\begin{bmatrix}1&k_2\\0&1\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}\quad \quad y_1=x_1+k_2x_2$$, ![[DIP notes-20231217-5.png|150]]
- scale parallel to $x1$ axis: $$ \begin{bmatrix}y_1\\y_2\end{bmatrix}=\begin{bmatrix}s_1&0\\0&1\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}\quad\quad\quad\quad\quad\quad\quad\quad y_1=s_1x_1$$, ![[DIP notes-20231217-6.png|150]]
- clockwise rotation: $$ \begin{bmatrix}y_1\\y_2\end{bmatrix}=\begin{bmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}$$
- counter-clockwise rotation: $$ \begin{bmatrix}y_1\\y_2\end{bmatrix}=\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}$$
- translation: $$ \begin{bmatrix}y_1\\y_2\\1\end{bmatrix}=\begin{bmatrix}1&0&b_1\\0&1&b_2\\0&0&1\end{bmatrix}\begin{bmatrix}x_1\\x_2\\1\end{bmatrix} \quad \quad y_1=x_1+b_1, y_2=x_2+b_2$$
- affine transformation: translation+scaling+rotation+reflection+shear+…
	- every linear transformation is affine, not every affine transformation is linear
	- linear transformation followed by a translation$$ \vec{y}=Affine(\vec{x})=A\vec{x}+\vec{b}\quad\quad\quad\quad\vec{y}=M\vec{t}=\left[\begin{array}{cc}A&\vec{b}\end{array}\right]\left[\begin{array}{c}\vec{x}\\1\end{array}\right]$$
	- properties of affine transformations:
		1. [collinearity](https://en.wikipedia.org/wiki/Collinearity "Collinearity") between points: three or more points which lie on the same line (called collinear points) continue to be collinear after the transformation.
		2. [parallelism](https://en.wikipedia.org/wiki/Parallel_(geometry) "Parallel (geometry)"): two or more lines which are parallel, continue to be parallel after the transformation.
		3. [convexity](https://en.wikipedia.org/wiki/Convex_set "Convex set") of sets: a convex set continues to be convex after the transformation. Moreover, the [extreme points](https://en.wikipedia.org/wiki/Extreme_point "Extreme point") of the original set are mapped to the extreme points of the transformed set.
		4. ratios of lengths of parallel line segments stays the same
		5. [barycenters](https://en.wikipedia.org/wiki/Barycenter "Barycenter") of weighted collections of points.


## Chapter 7 Image Segmentation

definition: process of separating or grouping an image into different parts

based on these features:
- color
- edge
- texture

### connectivity

*4-adjacency*: up/down/left/right, $N_4(p)$, if $q$ is in $N_4(p)$, then $p$ and $q$ are 4-adjacent.

*8-adjacency*: diagonal neighbors $N_D(p)$ + 4-adjacent $N_4(p)$

*m-adjacency*: $p$ and $q$ are m-adjacent if 
- $q$ is in $N_4(p)$ OR
- $q$ in $N_D(p)$ and $N_4\left(p\right)\cap N_4\left(q\right)$ has NO pixels whose values are the same used to define adjacency

*path*:

![[DIP notes-20231218-1.png|450]]

- 4-adjacency: no path
- 8-adjacency: 4
- m-adjacency: 7

foreground and background MUST have different definition of connectivity to segment them, or there will be ambiguity.

- $p$ and $q$ are connected in $S$ (a subset of pixels in an image) if there's a path
- $S$ is a <font color="#00b050">connected set</font> or <font color="#00b050">region</font> if there's only one connected component.
- two regions are adjacent if their union is a connected set. if not adjacent: disjoint

view segmentation in connectivity: $R$ represents entire spatial region, then segmentation is a process that partitions $R$ into $N$ subregions that
- $$ \bigcup_{i=1}^NR_i=R$$
- $R_i$ is a connected set
- $R_i \cap R_j = \varnothing$
- $Q(R_i) = TRUE$
- $Q(R_i\cup R_j)=FALSE$ for any adjacent region

### segmentation methods

#### amplitude thresholding

- bilevel luminance thresholding
	- group light objects and dark background into two dominant modes based on a selected threshold $T$
	- $$ g(x,y)=\begin{cases}1&\quad f(x,y)\geq T\\0&\quad f(x,y)<T\end{cases}$$
- basic global thresholding
	- use single threshold over entire image
- multilevel luminance thresholding
- multilevel color component thresholding
	- set threshold for each color
- amplitude (color component) projection

global thresholding vs. variable thresholding
- global: noise and non-uniform illumination will influence the performance of thresholding algorithm
- variable: image partitioning, moving averages

#### region
- region growing
	- seeds
	- similar criteria (like: connectivity)
	- stopping rule

#### clustering
- measure each pixel at coordinate $(i,j)$ with a vector $v_{ij}$
- measurement can be: point gray values, color components, neighborhood features (like moving window mean, standard deviation, mode)
- classification: find a plane/line that separates different classes with maximum margin
	- within cluster scatter matrices: $S_W=\frac1K\sum_{k=1}^K\frac1{M_k}\sum_{x_i\in S_k}(x_i-u_k)(x_i-u_k)^T$, where $u_k$ is the center of the cluster, $S_k$ is the whole set of the cluster, $x_i$ is the object in the cluster
	- between cluster scatter matrices: $S_B=\frac1K\sum_{k=1}^K(u_k-u_0)(u_k-u_0)^T$, $u_0$ is the global center

#### edge detection
- gradient
- kernels
	- Roberts
	- Prewitt
	- Sobel
	- Laplacian
- Hough transform
	- *point-line duality* between xy-plane and pq-plane. ![[DIP notes-20231218-2.png|400]]
		- <font color="#00b050">principle line</font> in image plane can be found by <font color="#00b050">identifying points</font> in parameter space.
	- *point-circle duality* between xy-plane and ab-plane. ![[DIP notes-20231218-3.png|400]]
		- principle <font color="#00b050">circles</font> in image plane can be found by identifying <font color="#00b050">points</font> in parameter space
- Snakes
	- internal forces, image forces, external constraint forces, molding a closed contour to the boundary of an object in an image (draw a larger region encloses the object, then shrink gradually to find the edge of object)
- graph cut
	- graph is used to represent the image, pixels in the image are represented by nodes on the graph, then a Min-Cut/Max-Flow algorithm is used to segment the graph

## Chapter 8 Morphological Image Processing

set theory
- image is a <font color="#00b050">set</font>
- spatial operation basically is set operation

structuring element (SE): small sets used to <font color="#00b050">probe</font> an image under study for properties of interest

more detailed explanation can be found here: [reference](https://homepages.inf.ed.ac.uk/rbf/HIPR2/morops.htm)

### binary morphology

#### erosion & dilation

erosion
- $E=A\Theta B=\left\{\vec{z}\mid B_z\subseteq A\right\}$ or $A\Theta B=\left\{\vec{z}\mid B_z\cap A^C=\emptyset\right\}$, where $B_z$ is the translation of $B$ by vector $z$.
- erosion <font color="#00b050">shrinks</font> (thins) objects in binary image, image details <font color="#00b050">smaller</font> than SE are filtered from the image
```
    1 1 1 1 1 1 1 1 1 1 1 1 1        
    1 1 1 1 1 1 0 1 1 1 1 1 1    
    1 1 1 1 1 1 1 1 1 1 1 1 1    
    1 1 1 1 1 1 1 1 1 1 1 1 1   
    1 1 1 1 1 1 1 1 1 1 1 1 1                
    1 1 1 1 1 1 1 1 1 1 1 1 1               1 1 1
    1 1 1 1 1 1 1 1 1 1 1 1 1               1 1 1
    1 1 1 1 1 1 1 1 1 1 1 1 1               1 1 1
    1 1 1 1 1 1 1 1 1 1 1 1 1        
    1 1 1 1 1 1 1 1 1 1 1 1 1    
    1 1 1 1 1 1 1 1 1 1 1 1 1    
    1 1 1 1 1 1 1 1 1 1 1 1 1   
    1 1 1 1 1 1 1 1 1 1 1 1 1
```
after erosion:
```
    0 0 0 0 0 0 0 0 0 0 0 0 0
    0 1 1 1 1 0 0 0 1 1 1 1 0
    0 1 1 1 1 0 0 0 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 1 1 0 
    0 1 1 1 1 1 1 1 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 1 1 0 
    0 1 1 1 1 1 1 1 1 1 1 1 0 
    0 1 1 1 1 1 1 1 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 1 1 0
    0 0 0 0 0 0 0 0 0 0 0 0 0
```
- only when B is **completely contained** inside A that the pixels values are retained, otherwise it gets deleted or eroded

dilation
- $D=A\oplus B=\left\{\vec{z}\mid\hat{B}_z\cap A\neq\emptyset\right\}$, notice $\hat{B_z}$ is the symmetric ($x,y$ ➡ $-x,-y$)!
- grows or thickens objects in a binary image. Gaps narrower than the SE are bridged
```
	0 0 0 0 0 0 0 0 0 0 0
    0 1 1 1 1 0 0 1 1 1 0   
    0 1 1 1 1 0 0 1 1 1 0  
    0 1 1 1 1 1 1 1 1 1 0
    0 1 1 1 1 1 1 1 1 1 0              1 1 1
    0 1 1 0 0 0 1 1 1 1 0              1 1 1
    0 1 1 0 0 0 1 1 1 1 0              1 1 1
    0 1 1 0 0 0 1 1 1 1 0       
    0 1 1 1 1 1 1 1 0 0 0   
    0 1 1 1 1 1 1 1 0 0 0   
    0 0 0 0 0 0 0 0 0 0 0
```
after dilation:
```
    1 1 1 1 1 1 1 1 1 1 1
    1 1 1 1 1 1 1 1 1 1 1   
    1 1 1 1 1 1 1 1 1 1 1  
    1 1 1 1 1 1 1 1 1 1 1
    1 1 1 1 1 1 1 1 1 1 1
    1 1 1 1 1 1 1 1 1 1 1
    1 1 1 1 0 1 1 1 1 1 1
    1 1 1 1 1 1 1 1 1 1 1       
    1 1 1 1 1 1 1 1 1 1 1   
    1 1 1 1 1 1 1 1 1 0 0   
    1 1 1 1 1 1 1 1 1 0 0
```
- For each pixel in A that has a value of 1, **superimpose** B, with the center of B aligned with the corresponding pixel in A. Each pixel of every superimposed B is <font color="#00b050">included</font> in the dilation of A by B.

#### opening and closing

opening
- $$ A\circ B=(A\Theta B)\oplus B$$
- Opening smooths the contour of an object, breaks narrow isthmuses, and eliminates thin protrusions.![[DIP notes-20231218-6.png|450]]

closing
- $A\bullet B=(A\oplus B)\ominus B$
- tends to smooth sections of contours, fuses narrow breaks and long thin gulfs, eliminates small holes and fills gaps in the contour. ![[DIP notes-20231218-7.png|450]]

properties of opening and closing
- opening
	- $A \circ B$ is a subset of $A$
	- if $C$ is a subset of $D$, then $C \circ B$ is a subset of $D \circ B$
	- $A \circ B \circ B=A \circ B$
- closing
	- $A$ is the subset of $A \bullet B$
	- if $C$ is a subset of $D$, then $C \bullet B$ is a subset of $D \bullet B$
	- $A \bullet B \bullet B=A \bullet B$
#### properties
- commutative: $$ A\oplus B=B\oplus A$$
- associate property: $$ \begin{aligned}(A\oplus B_1)\oplus B_2&=A\oplus(B_1\oplus B_2)\\(A\Theta B_1)\Theta B_2&=A\Theta(B_1\oplus B_2)\end{aligned}$$
- distributed property: $$ \begin{aligned}(A_1\cap A_2)&\Theta B=(A_1\Theta B)\bigcap(A_2\Theta B)\\A&\Theta(B_1\cup B_2)=(A\Theta B_1)\bigcap(A\Theta B_2)\end{aligned}$$
- duality: $$ \begin{aligned}A^C\oplus\hat{B}&=(A\Theta B)^C\\A^C\Theta\hat{B}&=(A\oplus B)^C\end{aligned}$$
- SE decomposition
	- $$ A\Theta(B_1\oplus B_2)=(A\Theta B_1)\Theta B_2$$

#### hit-or-miss transformation
- goal: find the location of certain object
- template matching: $X \textregistered T$, $T = (T_1, T_2)$, where $T_1$ is the foreground and $T_2$ is the background
- match: $T_1$ finds a match in $A$ and $T_2$ finds a match in $A^C$. Hit points are marked as 1 and miss points are marked as 0
- usage
	- erosion: for $\begin{pmatrix}1&1&1\\1&1&1\\1&1&1\end{pmatrix}$, mark hit points as 1 and miss points as 0
	- dilation: for $\begin{pmatrix}0&0&0\\0&0&0\\0&0&0\end{pmatrix}$, mark hit points as 0, and miss points as 1

#### basic morphological algorithms
- boundary extraction: $$ \begin{aligned}Edge(A)&=A-(A\Theta B)\\Edge(A)&=(A\oplus B)-A\end{aligned}$$
- thinning: $A \otimes B = A - A\textregistered B = A \cup (A \textregistered B)^C$
	- the thinning operation is calculated by <font color="#00b050">translating the origin</font> of the SE ($B$) to each possible pixel position, and comparing it with the underlying image pixels ($A$). If the foreground and background pixels in the structuring element <font color="#00b050">exactly match</font> foreground and background pixels in the image, then the image pixel underneath the origin of the structuring element is <font color="#00b050">set to background (zero)</font>. Otherwise it is left unchanged
- thickening:  $A\odot B=A\cup A\textregistered B$
	- calculated by <font color="#00b050">translating the origin</font> of the SE ($B$) to each possible pixel position, and comparing it with the underlying image pixels ($A$). If the foreground and background pixels in the structuring element <font color="#00b050">exactly match</font> foreground and background pixels, then the image pixel underneath the origin of the structuring element is set to <font color="#00b050">foreground (one)</font>. Otherwise it is left unchanged.
- shrinking
	- Erase black pixels such that an object 1) without holes erodes to a <font color="#00b050">single pixel</font> at or near its center of mass, and 2) an object with holes erodes to a <font color="#00b050">connected ring</font> lying midway between each hole and its nearest outer boundary
- skeletonizing
	- skeleton or stick figure representation of an object can be used to describe its structure, also called <font color="#00b050">medial axis transformation</font>, analogy with prairie fire
- hole filling
- convex hull
- pruning

### gray-scale morphology

gray-scale morphology is an extension based on binary image morphology: $OR(a,b) \to max(a,b)$, $AND(a,b) \to min(a,b)$

erosion:
$$ E(z_1,z_2)=(A\Theta B)_z=\min_{z_1+i,z_2+j\in D_A,i,j\in D_B}[A(z_1+i,z_2+j)-B(i,j)]$$

dilation:
$$ D(z_1,z_2)=(A\oplus B)_z=\max_{z_1+i,z_2+j\in D_A,i,j\in D_B}[A(z_1+i,z_2+j)+B(i,j)]$$

opening & closing: same expression, opening is used to <font color="#00b050">remove small, bright details</font>, while closing is used to <font color="#ffc000">attenuate dark features</font>

morphological gradient:
$$ Grad(f)=(f\oplus g)-(f\Theta g)$$

top hat transformation: used for light objects on a dark background
$$ THT(f)=f-(f\circ g)$$

bottom hat transformation: used for dark objects on a light background
$$ BHT(f)=(f\bullet g)-f$$

## Chapter 9 Image Compression

### fundamental concepts

- entropy of single event: $$ I(E)=\log\frac1{P(E)}=-\log P(E)$$
- entropy of zero-memory source: $$ H=-\sum_iP(a_i)\log P(a_i)$$, where $a_i$ is source
- Shannon's first theorem: $$ H=\lim_{n\to\infty}\frac{L_{\mathrm{avg},n}}n$$, as the length of a stream of independent and identically-distributed random variable (i.i.d.) data tends to infinity, it is impossible to compress such data such that the code rate (average number of bits per symbol) is less than the Shannon entropy of the source
- average code length: $R(x) = \sum_iP(x_i)L_i$
- coding efficiency: $\dfrac{H(x)}{R(x)}$
- compression ratio: $$ c=\frac{b_1}{b_2}=\frac{R_{before}(x)}{R_{after}(x)}=\frac{ceil(\log_2(L))}{R_{after}(x)}$$
- signal noise ration (SNR): $$ 10\log\frac{\sigma_x^2}{\sigma_e^2}$$
### image data redundancy
- coding redundancy
- spatial and temporal redundancy
- irrelevant information

### model of image compression
INPUT $f$ ➡ ENCODER {mapper + quantizer + symbol coder} ➡ DECODER {symbol decoder + inverse mapper} ➡ OUTPUT $\hat{f}$

#### Huffman
Huffman's procedure:
1. create source reductions by ordering probabilities of symbols under consideration and combining the lowest probability symbols into a single symbol that replaces them in the next source reduction
2. code each reduced source, starting with the smallest source and working back to the original source
![[DIP notes-20231218-8.png|450]]

> [!NOTE] here is another clearer way [(ref)](https://www.geeksforgeeks.org/huffman-coding-greedy-algo-3/)
> ![[DIP notes-20231226-1.png]]
> combine lowest probability from leaves to root (down to up), then write the code from root (up to down)

- Huffman code is an <font color="#00b050">instantaneous</font> <font color="#0070c0">uniquely</font> <font color="#ffc000">decodable</font> block code
	- block code: each symbol is mapped into a fixed sequence of code symbols
	- instantaneous: each code word can be decoded without referencing succeeding symbols
	- uniquely decodable: any string of code symbol can be decoded in only one way
- pros and cons
	- pros
		- efficient to achieve high compression ratio by assigning shorter code to more frequent symbols
		- prefix-free, no ambiguity when decoding
		- lossless
		- fast and error resilient
	- cons
		- require frequency information in advance
		- may produce complex and large code trees
		- ineffective for data with few symbols (already highly compressed)

#### arithmetic coding

Entire sequence of source symbols is assigned a single arithmetic code word. The <font color="#00b050">code word</font> itself <font color="#00b050">defines an interval</font> of real numbers between 0 and 1. As the <font color="#00b050">number of symbols</font> in the message <font color="#00b050">increases</font>, the <font color="#00b050">interval</font> used to represent it becomes <font color="#00b050">smaller</font> and the number of information units required to represent the interval becomes larger.

![[DIP notes-20231218-9.png|450]]

#### running length coding (RLC)

RLC compresses image by representing runs of <font color="#00b050">identical intensities</font> as run-length pairs, where each run-length pair specifies the <font color="#00b050">start</font> of a new intensity & the <font color="#00b050">number</font> of consecutive pixels that have that intensity (using 57 to represent 57 continuous zeros)

#### other coding methods
- bit-plane
- block transform coding
- predictive coding

### digital image watermark

- one or more items of information inserted into digital images
- visible watermark
	- opaque or semi-transparent sub-image or image is placed on top of another image: $f_w = (1-\alpha)f + \alpha w$, where $\alpha$ controls visibility of watermark
- invisible watermark
	- fragile invisible watermark (LSB watermarked image): $f_w = 4(f/4) + w/64$
		- can't be seen, insert watermark as redundant information, will be destroyed by any modification of the images
	- can also be implemented in transform domain: compute DCT, locate its $K$ largest coefficients by magnitude, then create a watermark by <font color="#00b050">generating</font> $K$-element pseudo-random <font color="#00b050">sequence of numbers</font>, taken from a Gaussian distribution with 0 mean and unit variance, after this embed watermark image from previous step into $K$ largest DCT coefficients using $c_i' = c_i (1 + \alpha w_i)\quad\quad 1\le i \le K$. And at last compute the inverse DCT.


## what's going on in past exam
- [x] neighboring
- [x] filter design (median)
- [x] opening/closing/erosion/dilation
- [x] calculate result of applying filters
- [x] find histogram of image
- [x] histogram equalization
- [x] entropy calculation
- [x] Huffman's encoding
- [x] evaluate compression method with code length, compression ratio, coding efficiency
