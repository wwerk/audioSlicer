**Sound and Signal 2 MiniProject**
<br />
33655491
<br />
**Audio segmentation and sorting based on similarity using MFCCs**
<br />

[![GitHub Repo](https://badgen.net/badge/icon/GitHub?icon=github&label)](https://github.com/wwerk/audioSlicer/)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wwerk/audioSlicer/blob/main/audioSlicer.ipynb)

[![Watch demo on YouTube: https://youtu.be/ZJwwGVGWXwY](https://img.youtube.com/vi/ZJwwGVGWXwY/0.jpg)](https://youtu.be/ZJwwGVGWXwY)

***How my code works:***
-
<br />

1. Setting of global parameters:
   - number of MFCCs used
   - size of the FFT used in calculating MFCCs
   - length of the frame
   - 0th MFCC toggle
   - onset detection toggle
   - windowing toggle
   - smoothing toggle
   - smoothing window width
   - sigma parameter of the Gauss filter
   - segmentation hop length
2. Loading a file using GUI [[ipyfilechooser]](https://pypi.org/project/ipyfilechooser/) / [[google.colab]](https://neptune.ai/blog/google-colab-dealing-with-files)
3. Segmentation:
- into frames of set width [[librosa]](https://librosa.org/doc/main/generated/librosa.util.frame.html)
- on onset times [[librosa]](https://librosa.org/doc/main/generated/librosa.onset.onset_detect.html)
4. Windowing of signal in each frame using Hamming Function [[numpy]](https://numpy.org/doc/stable/reference/generated/numpy.hamming.html#numpy.hamming)
5. Calculation of MFCCs for each frame without centering [[librosa]](https://librosa.org/doc/main/generated/librosa.feature.mfcc.html)
6. Example frame sorting using MFCC values via as folllows,
   - using a k-d tree structure [[scipy.spatial]](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.KDTree.html):
     - by querying for all the neighbours of frame[0], sorted by distance in ascending order
     - by finding the shortest path that traverses the entire tree starting from frame[0]
   - using correlation clustering represented as hierarchy dendrogram, sorted by distance in ascending order [[scipy.cluster]](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html)
7. Output construction via concatenation of frames in arrangements calculated in step 6., optionally smoothing out signal discontinuities between them using a 1-Dimensional Gaussian filter. [[scipy.ndimage]](https://docs.scipy.org/doc/scipy/reference/generated/scipy.ndimage.gaussian_filter.html)

*All results displayed  are plotted using [matplotlib](https://matplotlib.org/).*
<br />

*This project references online resources which elaborate further on the concepts of audio feature extraction and others, such as [musicinformationretrieval.com](https://musicinformationretrieval.com/i) as well as documentation of [matplotlib](https://matplotlib.org/stable/index.html), [librosa](https://librosa.org/doc/main/index.html) and [scipy](https://docs.scipy.org/doc/) libraries.*





***Points my project illustrates:***
-
<br />

- 

***Achieved result:***
-
<br />

-


***Improvements based on user feedback:***
-
<br />

  - comments clearly explaining what the script does and how
  - fixed default plot sizes and labels for better visualisation
  - GUI browser for adding/upload of the source audio file
  - implented sorting using correlation clustering
  
*Thanks to Ben, Jeremi, Maksym, Otta, Sohyun and others for helping me out with testing and suggestions on how to improve this project.*

Costam