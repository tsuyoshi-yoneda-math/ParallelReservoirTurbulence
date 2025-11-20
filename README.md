Please acknowledge the use of these scripts in any publications that make use of them.

I developed a non-incremental online learning system using a parallelized reservoir and the corresponding data-driven filter. Unlike long-term learning models, its strength lies in its ability to adapt flexibly to sudden changes in patterns.

For the summary of parallelized reservoir, see

https://github.com/tsuyoshi-yoneda-math/SummaryNoteSlide-ML-Turbulence/blob/main/parallelized-reservoir.pdf

We applied this method to predict wind speed three hours ahead in the Tokyo region. Using online learning with the most recent 1,000 hours of data, the <b>MAE of 2 m/s for predictions based on the filtered data—together with a correlation of 0.83 between the filtered and original data—can be regarded as a fairly robust result.</b>

The following is a comparable result from our study:

William Y.Y. Cheng and W. James Steenburgh, Evaluation of Surface Sensible Weather Forecasts by the WRF and the ETA Models over the Western United States, WRF/MM5 Users' Workshop - June 2005.

https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www2.mmm.ucar.edu/wrf/users/workshops/WS2005/abstracts/Session4/4-Cheng.pdf&ved=2ahUKEwjl_v3xq_qPAxWIr1YBHR9JLEsQFnoECBYQAQ&usg=AOvVaw1NB6Bv5VFOk7oVVpT3cp0j

Although the data are not from the same location or period, the MAE for the 3-hour-ahead wind speed prediction is still comparable. Our conclusion is that our model can quickly respond to sudden local winds and recent weather patterns compared to long-term learning models, the current accuracy is quite promising.

We employ the excellent Ohkubo-Inubushi method (for the Ridge regression) in the latest version. 
For the detail, see Scientific Reports volume 14, Article number: 30918 (2024).

https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.nature.com/articles/s41598-024-81880-3.pdf&ved=2ahUKEwjN7738qvqPAxW6qFYBHe5hJB0QFnoECBYQAQ&usg=AOvVaw2imVztYVPlD_xuZTJibtUG

If you want to know the mathematical structure of the realtime filter, see the following paper:

``Long-term prediction of El Niño-Southern Oscillation using reservoir computing with data-driven realtime filter"

https://pubs.aip.org/aip/cha/article-abstract/35/5/053149/3347294/Long-term-prediction-of-El-Nino-Southern?redirectedFrom=fulltext


