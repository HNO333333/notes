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
	- conversion from HSI to RGB: $$ X=I\bigg[1+\frac{S\cos H'}{\cos(60°-H')}\bigg]$$$$ Y=I(1-S)$$$$ Z=3I-(X+Y)$$ $$ H^{\prime}=H\mathrm{~mod~}120\quad\quad H\in[0^{\circ},360^{\circ}]$$ $$ quotient=\begin{cases}0&X,Y,Z&->R,B,G\\1&X,Y,Z&->G,R,B\\2&X,Y,Z&->B,G,R&\end{cases}$$ $$ H\div120=quotient\cdots H^{\prime}$$

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

