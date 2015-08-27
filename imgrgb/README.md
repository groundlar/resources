imgrgb Results Dump
==================

The movies show the evolution of the algorithm for high-definition renders.

HSB_center_sq.mp4 begins with an array of colors sorted first by Hue, then by Saturation, and finally Brightness (uses HSB color space). The placement algorithm also uses a linear adjustment to coerce pixels _towards_ the seed pixel, resulting in a more centralized or "circular" growth pattern.

In contrast, RBG_disperse_sq.mp4 first sorts the colors according to (R / (G+B)), then by (G / B) in the event of equal primary values (uses RGB color space).The placement algorithm also uses a linear adjustment to coerce pixels _away from_ the seed pixel, resulting in a more "filamentous" growth pattern.

Both videos also use a squared penalty for empty neighbors to coerce subsequent pixels towards areas of higher "pixel density" -- that is, the next pixel favors having previously-placed neighbors.


The static images follow the following naming convention:

|imgrgb|Color Distance Metric|Sorting Function|Dimensions|Seed|Additional Weights|
|:------|:---------------------:|:----------------:|:----------:|:----:|------------------:|
|imgrgb|  avgSqNhbr  |colorComp1_2_0|1023-511|s109103113|.png|
|imgrgb|  avgSqNhbr  |hueComparator|1727-1023|s109103113|-neglin.png|

So for the two images:
imgrgb_avgSqNhbr_colorComp1_2_0_1023-511s109103113.png
imgrgb_avgSqNhbr_hueComparator_1727-1023s109103113-neglin.png


The first would sort the colors by B -> R -> G, while the second would sort first by hue, then saturation, then brightness. The images use the same seed, but vary in size (1023x511 vs 1727x1023). The second image coerces pixels towards previously filled pixels by introducing a negative linear term in the placement algorithm (penalizing empty pixels).

You can see the differences below:

![][noweighting-color]

![][weighting-hue]

[noweighting-color]:https://github.com/skycook/resources/blob/master/imgrgb/imgrgb_avgSqNhbr_colorComp1_2_0_1023-511s109103113.png
[weighting-hue]:https://github.com/skycook/resources/blob/master/imgrgb/imgrgb_avgSqNhbr_hueComparator_1727-1023s109103113-neglin.png





