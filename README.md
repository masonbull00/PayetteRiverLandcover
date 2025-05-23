These are the codes for classifying landcover in the Payette River Watershed, and to calculate Burn Severity for the Rapid Research Project. 
These codes are set-up to run and export data, but are not nearly as in depth comment-wise as the codes in my other repositories.


The classification process for the Payette watershed is identical to the Nellie Juan. I used the same codes to run the classification in both watersheds with the exception of Landsat 7. 
There are sufficient images in the Payette for Scan Line Correction, so there is Landsat imagery from all years that Landsat 7 is active. 
Additionally, we decided to mask out historic fires from the watershed. Fires occurred over ~20% of the watershed since the 1980s, and we want to analyze landcover change unrelated to fire interference. 
This did, however, greatly decrease the available area for classification and somewhat skewed landcover distributions for training data. 

We chose the 6 landcover classes in the Payette based largely on unsupervised classification. 
The classes are Rock, Dense Forest (forest with no visible understory), Transitional Forest (forests with visible understory), 
Riparian Shrubs (dark green and ‘fuzzy’ canopies near water), Vegetated Talus (sparse shrubs and young trees on bare talus slopes), and Trees on Talus (trees and shrubs forming semi-dense communities on talus slopes). 
We found that an X-means classifier generally produced 6 landcover classes, and we compared those classes with high resolution imagery and historic imagery from the region. 
We found that landcover is determined principally by vegetation density and is not necessarily distinct species or plant types. Because landcover is not extremely distinct, it makes the classification exceedingly difficult. 
Classification accuracy in the Payette is usually somewhere in the mid-70s or just cresting 80%. This watershed would greatly benefit from field visits to see how landcover is distributed in the field to improve training data. 

I never created training data for Landsat 7 sensors around 1999-2002. I only used training data for whichever year was closest to the image I was classifying. The training data for Landsats 5 and 8 are very similar.
Post-processing for the Payette watershed is also identical to the Nellie Juan. The same codes do the same thing for the Payette and Nellie Juan. 
However, the Payette watershed has many more images so the codes take substantially longer to run and some axes need to be edited to fit all of the years of imagery. 
I never completely finished post-processing for the Payette. I created a change matrix and all of the landcover change rasters and then related those changes to topography. 

The next step is to analyze how NDVI changed over time in the Payette and see if changes accelerated over time. 
I would recommend that whoever takes this up next reevaluates the training data to see if they can improve it by either removing or adding classes, or bolstering the existing data. 
There is a chance that I overfit the model with too much data. However, when decreasing the amount of training data there is no marked increase in accuracy.

Here is the link to my classification codes on GEE. You should have reader access to copy code:
Landsat 8 Fire Masked: https://code.earthengine.google.com/e40a22cb0679c94b2f65584b2f40bef3
Landsat 7 Fire Masked: https://code.earthengine.google.com/3e8d7af3bd4e81626cf0437d002fa88f
Landsat 5 Fire Masked: https://code.earthengine.google.com/bc9d71690a94543c7273d37fba4b3132

This is the code that I used to test various amounts of training data and its effect on accuracy for a single year of Landsat 8 imagery: 
https://code.earthengine.google.com/1460cf698a1e98c45b8a9c57c0feeba4

Here is the training data that I created, again with reader access:
Landsat 8: https://code.earthengine.google.com/?asset=projects/ee-masonbull/assets/Payette/PayetteNewClasses7_8_26_2024
Landsat 5: https://code.earthengine.google.com/?asset=projects/ee-masonbull/assets/Payette/PayetteNewClasses7_8_26_2024

And for posterity, the historic fires, waterbodies, and watershed outline:
Fires: https://code.earthengine.google.com/?asset=projects/ee-masonbull/assets/Payette/PayetteFires
Water bodies: https://code.earthengine.google.com/?asset=projects/ee-masonbull/assets/Payette/PayetteWater
Outline: https://code.earthengine.google.com/?asset=projects/ee-masonbull/assets/Payette/PayetteWatershed
