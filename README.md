## Colormap distorsions Panel app ##

The notebook in this repo served two goals:

1. As a playground for continue learning Panel (following the awesome PyData tutorial by James Bednar, [Panel: Dashboards for PyData (Austin 2019)](https://youtu.be/AXpjbJUVeb4))
2. To share an app demonstrating the effect of colormaps on perception (and on the ability to see fault edges on a seismic horizon)

The first version of the app was presented as a lightning talk at the [Transform 2020 virtual conference](https://transform2020.sched.com/) organized by [Software Underground](https://softwareunderground.org/); you can watch a [video recording of the presentation here](https://www.youtube.com/watch?v=rUbvueIF5f8&t=510s).

<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/master/for%20readme/new_gif.gif" width="600">
</p>

### Conda setup ####
To create the conda environment for this tutorial run:

```
conda env create -f environment.yml
```

### To run the notebook interactively with Binder click on the button below ####
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/rakibulinux/Colormap-distorsions-Panel-app/HEAD)

### To launch the app directly from server, use the link below ####
[Launch app](https://mybinder.org/v2/gh/rakibulinux/Colormap-distorsions-Panel-app/master?urlpath=%2Fpanel%2Fnyc_taxi_v3)


### How to use the app ####
If you would like some background, please read [Crameri et al., 2020,  The misuse of colour in science communication. Nat Commun 11, 5444 ](https://www.nature.com/articles/s41467-020-19160-7), and my Society of Exploration Geophysicists tutorial [Evaluate and compare colormaps](https://github.com/seg/tutorials-2014/blob/master/README.md#august-2014).

The idea behind this app is to allow comparing  any from a wide variety of colormaps to a good perceptual benchmark. As such:
1. In the top row, I chose grayscale as reference perceptually uniform colormap. (N.B. not all grayscale colormaps are actually truly, 100% perceptually uniform, when you plot Lightness, but this is a decent approximation).

2. The left column is purely for visual reference of the data with grayscale (top) vs. data with colormap (bottom). (N.B. I plan at some point to add an option to show the deuteranope simulation as an extra).

3. The real comparison is done in the middle column (it should be fairly intuitive) by only showing intensity with monochromatic palette for the grayscale (top) and colormapped (bottom). A perceptual colormap with uniform incremental contrast at bottom would look like the benchmark at top. Below I am showing an example for Viridis:
<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/086b13486cd0fd386d253ec1229067fedd9ea0b3/for%20readme/viridis.png" width="600">
</p>
Notice that the intensity plots are virtually indistinguishable. A perceptual colormap with uniform but lower total intensity contrast (from least to most intense) will still look similar to the reference, but a bit more washed out due to shorter range. As an aside: I use intensity here for simplicity, as it may be a more familiar idea to more users; I will eventually switch to Lightness. Below is an example with one of my colormaps, CubeYF:
<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/master/for%20readme/cube_YF.png" width="600">
</p>

4. The right column uses Sobel edge detection to enhance the visibility of potential artifacts caused by non perceptual colormaps. Additionally, edge detection is typically an interpretation product, so it is a good way to show what to expect, and how artifacts have an effects a real-world workflow. Below is an example with npy_spectral, highlighting scarps (continuous arrow) and plateaus (dashed arrow):
<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/a083b6f9457e418c2e73161acb167503dcc15559/for%20readme/nipy_spectral.png" width="600">
</p>

5. As further evidence, please compare the hillshsade versions with contours:
<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/bc66e63e12aac6ecab98cefb773634df6a42754c/for%20readme/data_hillshade.png" width="500">
</p>
<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/bc66e63e12aac6ecab98cefb773634df6a42754c/for%20readme/gist_rainbow_colormapped_data_hillshade.png" width="500">
</p>

6. The interesting thing to me is that, according to this intensity-based tool, even a perceptual version of the rainbow (cet-rainbow) still has some issues. They are subtle, but they are definitely there, like the thin white strips (caused by yellow hard edges), indicated by yellow arrows and the red with its artificial decrease in intensity (indicated by purple arrow) giving the impression of lows where there should be highs:
<p align="center">
<img src="https://github.com/mycarta/Colormap-distorsions-Panel-app/blob/994fe6cf47625af4e0f816e6bb6dd18557753fb3/for%20readme/cet_rainbow.png" width="600">
</p>

### License ###
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/"> CC BY Creative Commons License</a>, with the exception of the data used (a seismic horizon from the [Penobscot 3D](https://terranubis.com/datainfo/Penobscot) which is covered by a [CC BY-SA Creative Commons License](https://creativecommons.org/licenses/by-sa/3.0/)).

