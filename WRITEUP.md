**Sound and Signal 2 MiniProject**
<br />
33655491
<br />
**Audio segmentation and similarity sorting using MFCCs**
<br />

[![GitHub Repo](https://badgen.net/badge/icon/GitHub?icon=github&label)](https://github.com/wwerk/audioSlicer/)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wwerk/audioSlicer/blob/main/audioSlicer.ipynb)

[![Watch demo on YouTube: https://youtu.be/yyklh6AH8J8](https://img.youtube.com/vi/yyklh6AH8J8/0.jpg)](https://youtu.be/yyklh6AH8J8)
<br />
[Watch demo on YouTube](https://youtu.be/yyklh6AH8J8)

***How this script works:***
-
<br />

1. Setting of global parameters:
- number of MFCCs used,
- size of the FFT used in calculating MFCCs,
- length of the frame,
- 0th MFCC toggle,
- onset detection toggle,
- windowing toggle,
- smoothing toggle,
- smoothing window width,
- sigma parameter of the Gauss filter,
- segmentation hop length.
2. Loading a file using GUI. [[ipyfilechooser]](https://pypi.org/project/ipyfilechooser/) / [[google.colab]](https://neptune.ai/blog/google-colab-dealing-with-files)
3. Segmentation:
- into frames of set width, [[librosa]](https://librosa.org/doc/main/generated/librosa.util.frame.html)
- on onset times. [[librosa]](https://librosa.org/doc/main/generated/librosa.onset.onset_detect.html)
4. Windowing of signal in each frame using Hamming Function. [[numpy]](https://numpy.org/doc/stable/reference/generated/numpy.hamming.html#numpy.hamming)
5. Calculation of MFCCs for each frame without centering [[librosa]](https://librosa.org/doc/main/generated/librosa.feature.mfcc.html)
6. Example frame sorting using MFCC values via as folllows,
- using a k-d tree structure: [[scipy.spatial]](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.KDTree.html)
   - by querying for all the neighbours of frame[0], sorted by distance in ascending order,
   - by finding the shortest path that traverses the entire tree starting from frame[0],
 - using correlation clustering represented as hierarchy dendrogram, sorted by distance in ascending order. [[scipy.cluster]](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html)
7. Output construction via concatenation of frames in arrangements calculated in step 6., optionally smoothing out signal discontinuities between them using a 1-Dimensional Gaussian filter. [[scipy.ndimage]](https://docs.scipy.org/doc/scipy/reference/generated/scipy.ndimage.gaussian_filter.html)

*All results displayed  are plotted using [matplotlib](https://matplotlib.org/).*
<br />

*This project references online resources which elaborate further on the concepts of audio feature extraction and math-based workflows in Python, such as [musicinformationretrieval.com](https://musicinformationretrieval.com/i) as well as documentation of [matplotlib](https://matplotlib.org/stable/index.html), [numpy](https://numpy.org/doc/stable/), [librosa](https://librosa.org/doc/main/index.html) and [scipy](https://docs.scipy.org/doc/) libraries.*





***Points this project illustrates:***
-
<br />

- Potential technical use cases that take advantage of extracted audio features, that is:
  - capability to compare audio fragments in a perceptually-accurate manner (thanks to the use of MFCCs),
  - flexibly scalable deconstruction that is capable of representing the vocabulary of timbres contained within a single sound, phrase or longer piece of audio and connections between them,
  - simple and straightforward preparation of samples out of raw input material, samplepack creation/curation.
- Potential artistic use cases, such as:
  - an interesting method of sound representation, underlied by an analytical principle that is none the less audible,
  - capability to traverse sound in a novel manner, at chosen scale,
  -  a deterministic, universal method of arrangement that can be applied to any source material. This could potentially lead towards creating 'empty' works, merely describing the organisation of sound with no actual audible content until some input is given.


***Achieved result:***
-
<br />

- Script shows great performance with short audio files (under one minute length) and still performs fairly well with longer input material.
- Output can be very interesting both from musical and analytical point of view.
- Plotted graphs visualise the segmentation and make differences between the three ways of frame sorting apparent, but do it well only in case of shorter files/bigger frame sizes. When long input/small frame size is used, the graph displaying the separators tends to be incomprehensive.
- MFCCs seem to add an extra frame compared to the length of the analysed input, also, in second and third example of frame organisation, the mfcc of the first frame of the output looks different than expected.
- Concatenation works rather well and clicks are filtered out, unless very small frame size is used.
- Project could be extended further by:
  - implementing a more computationally efficient way of the shortest path search, if possible,
  - adding the calculation of MFCCs step by step with plotted results for each, as this could make the notebook more informative,
  - in depth comparison of differences between MFCCs and less processed spectral information, such as the result of a FFT. This could be done both in the context of computation time and alignment with human perception,
  - implementing a full GUI, which could improve the user experience and make it a very useful tool,
  - using Principal Component Analysis of extracted features to improve the data interpretability, as well as extend the creative use potential (ie. CataRT synthesis),
  - using a beat/tempo tracking instead of simple onset detection, to improve the musical quality of the output,
  - implementing sequential component analysis to find sequences underlying the input data instead of current segmentation methods.
  


***Improvements based on user feedback:***
-
<br />

  - Comments clearly explaining what the script does and how.
  - Fixed default plot sizes and labels for better visualisation.
  - GUI browser for adding/upload of the source audio file.
  - Implented sorting using correlation clustering.
  
*Thanks to Ben, Jeremi, Maksym, Otta, Sohyun and others for the help with testing and suggestions on how to improve this project.*