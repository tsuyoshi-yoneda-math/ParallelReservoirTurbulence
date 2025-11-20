Please acknowledge the use of these scripts in any publications which make use of them.

I constructed non-incremental online learning of parallelized Reservoir and the corresponding data-driven filter. The strong point of this learning scheme is that only the most recent 1,000 hours of data are used to train the wind speed model. Compared to long-term learning models, its strength lies in its ability to flexibly adapt to sudden pattern changes.

We predicted wind speed for three hours ahead in the Tokyo region. Online learning + recent 1,000 hours of data, the MAE of 2 m/s for prediction using the filtered data, along with a correlation of 0.83 between the filtered data and original data, is considered a fairly robust result. 

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


