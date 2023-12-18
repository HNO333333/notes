---
title: Digital Image Processing Notes
date: 2023-12-17
draft: false
author: HNO3
---
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
#### histogram (intensity transformation techniques)
- definition: <font color="#00b050">estimate</font> of the <font color="#00b050">probability</font> of occurrence of each intensity level in an image
- $$ P(r_k)=\frac{n_k}{MN},\quad k=0,1,...,L-1$$, where $MN$: the total number of pixels, $r_k$: $k$th intensity value, $n_k$: number of pixels with intensity $r_k$
- *histogram equalization*: <font color="#00b050">mapping</font> original PDF to another whose distribution is more uniform. spread the histogram of the input image, resulting a <font color="#00b050">contrast enhancement</font> $$ s_{k}=T(r_{k})=(L-1)\sum_{i=0}^{k}p_{r}(r_{j})=(L-1)P_{r}^{\prime}(k)=\frac{L-1}{MN}\sum_{i=0}^{k}n_{j}$$
	- ![[DIP notes-20231217-2.png|450]]
- *histogram modification*
	- histogram specification: uniform histogram is not best choice
	- method used to generate a processed image that has a specified histogram is called histogram specification
	- procedure
		1. histogram equalization
		2. find transformation function for the specified histogram
		3. compute histogram of given image
		4. compute all values of transformation function and store them in a table
		5. convert the histogram of given image to the new image based on the values in the table
	- ![[DIP notes-20231217-3.png|400]]

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

