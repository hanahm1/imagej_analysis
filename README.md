# imagej_analysis

Program: FIJI (a life science verison of ImageJ)

Immunohistochemistry on preserved tissues stains "positive" cells with a specific antibody/color while the "negative" cells are counterstained with another, very different color. In order to analyze positive vs. negative cells, we need to separate the different colors then prepare the pictures for computer analysis. 

The microscope camera used had very dark pictures so all of those pictures went through a backgroud subtraction (12) to lighten up the pictures.

Colour Deconvolution separates the colors. In my case, H DAB (hemotoxylin + antibody chromagen/HRP stain) were the colors I separated. From there, the image thresholds were adjusted to include as many positive cells and as few background as possible. Images were then made binary with watershed (watershed tries to separate cells that may be clumped together). The analysis is then called and the cell counts (for that color) are calculated as well as the area. The results window contains all of the individual cells, their IDs, and their areas. When you have thousands of cells being counted, that's pretty useless (for what I need anyway).  The summary table gives the cell count for that color plus the total area those cells occupy (even the percentage of area they occupy).

Code Issues: This is not a hands off macro, which is unfortunate. There is some sort of background code that wraps all the edited pictures together in one file and re-processes them. This causes a dialogue box to come up and ask if you want to convert the DAB pictures to binary. Click cancel, you already did that and saved the picture. The macro then aborts so you'll need save the summary table by hand. I can't figure out how to disable this automatic feature, if you do, let me know because this is driving me nuts. If I find out, I'll update the master branch and this read me... in case people actually do read this.
