# Rendering-Hytexila-Dataset
Using computer graphics algorithms as a rendering system, hytexila hyperspectral images were rendered with varying lighting and camera conditions, based on their spectral power distribution and wavelength. The rendered results were compared pixel by pixel with the original RGB image using reflectance data from the images as spectral power distribution.


For the initial experiment we only used one pixel reflectance values of foodchilli and textile
image and assigned these values to the plane geometry created in blender.
The spectral power distribution (SPD) are assigned to the plane geometry as a diffuse lambertian
reflection using the matte material. For checking the effects of the reflectance data we also
used those values as absorption coefficient and index of refraction by utilizing the PBRT
spectrum parameters "eta", "k". Since the matte material have no properties related to
absorption coefficient and index of refraction. We then applied spectral power distribution
data file to the "metal" material in order to see the effects of the SPDs. 


Generating a Rendered hyperspectral images is possible using PBRT but it needs some
backend modification on handling the values of reflectance data while reading the values
of SPDs for each wavelength. We believe that the current PBRT implementation related
to using spectral data works fine for one dimensional wavelength values but it does not
work when the SPDs are used in a stack manner. As a result, to render the HyTexila
dataset we need to add a specific library or code snippet to PBRT that can read multi
dimensional SPD values and apply those SPDs to each pixel in the intended geometry
sequentially.
