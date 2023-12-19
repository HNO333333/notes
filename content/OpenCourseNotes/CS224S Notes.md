---
title: CS224S Notes
date: 2023-12-19
draft: false
author: HNO3
---
[course syllabus](https://web.stanford.edu/class/cs224s/syllabus/)

>[!info]- why this course:
>of course final year project :(

## Lecture 2 Phonetics

### Acoustic Phonetics

#### observation from waveform of voice
- Each <font color="#00b050">peak</font> corresponds to an <font color="#00b050">opening</font> of the vocal folds
- low frequency of the complex wave is called the <font color="#00b050">fundamental frequency</font> of the wave or F0

#### Source-filter model of speech production
![[CS224S Notes-20231219-1.png|500]]
- Source and filter are independent, so
	- Different vowels can have same pitch
	- The same vowel can have different pitch

#### intonation
- use of suprasegmental phonetic features
	- F0
	- intensity
	- duration

#### pitch & F0
- Pitch is the mental sensation or perceptual correlated of F0
- Relationship between pitch and F0 is <font color="#00b050">not linear</font>
- Mel scale is one model of this F0-pitch mapping

#### prosody (韵律)
3 aspects
- *Prominence*: some syllables/words are more prominent than others
- *Structure*/boundaries: sentences have prosodic structure. Some words group naturally together, while others have a noticeable <font color="#00b050">break</font> or disjuncture between them
- *Tune*: the intonational melody of an utterance

