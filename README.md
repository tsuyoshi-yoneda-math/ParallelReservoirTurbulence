Please acknowledge the use of these scripts in any publications which make use of them.

I constructed non-incremental online learning of parallelizable Reservoir (simple turbulence model)
and the corresponding realtime filter (based on Bayesian optimization) for the parallel data.

The strong point of this learning scheme is that only the most recent 1,000 hours of data are used to predict the wind speed.  
With this limited training data, online learning can be performed to predict three hours ahead in the Tokyo region. Compared to long-term learning models, its strength lies in its ability to flexibly adapt to sudden pattern changes.

Online learning + recent 1,000 hours of data, the MAE of 2 m/s for prediction using the filtered data, along with a correlation of 0.83 between the filtered data and original data, is considered a fairly robust result. On the other hand, the MAE of 4.05 m/s for the prediction without any use of filter, is poor accuracy.

With long-term learning models, even with a large amount of data, the speed at which they can adapt to the latest patterns may be slower. Considering that the current model can quickly respond to sudden local winds and recent weather patterns compared to long-term learning models, the current accuracy is quite promising.



If you want to know the mathematical structure of the realtime filter, see the following paper:

``Long-term prediction of El Niño-Southern Oscillation using reservoir computing with data-driven realtime filter"

https://pubs.aip.org/aip/cha/article-abstract/35/5/053149/3347294/Long-term-prediction-of-El-Nino-Southern?redirectedFrom=fulltext

The sample time series stored in "tokyo_region_wind_speed_hourly" is the windspeed in Tokyo region from start_date = "2024-01-01" until end_date = "2024-06-30", and "flt_tokyo_region_wind_speed_hourly.csv" is the corresponding filtered data. You can directly download it from download_TokyoRegion_WindSpeed.ipynb.


 
Optimizing the hyperparameters of the realtime-filter: 

As for DataDrivenFilter_for_ParallelData_TYoneda.ipynb, you can set desirable ranges of the hyperparameters

r_1:   Higher end of the passing frequency range
r_2:   Lower end of the passing frequency range
c:     Parameter for the attenuation of weight function
d_1:   Amplitude of the frequency r_1
d_2:   Amplitude of the frequency r_2
width: Length of weighted running average in past time series

The following parameters are related to the reduction of the indefinite factor of the time series.

T_train:   Training length
n_trials:  Number of trials for optuna
max_dim:   Max pattern length
min_dim:   Min pattern length
min_count: Delete patterns if occurrence is fewer than this
n_bins:    Number of partitions of range
min_win_vote_rate: Minimum requirement for win_vote_rate

The filtered time series in csv file is generated.



Optimizing the hyperparameters of the echo state network model:

As for
ParallelReservoirTurbulence_Flted_robust_TYoneda.ipynb
and
ParallelReservoirTurbulence_NOflt_robust_TYoneda.ipynb,
you can set desirable ranges of the hyperparameters

lag:         Delay time
dim:         Dimension of input delay-coordinate vector
N_x:         Dimension of reservoir state vector
beta:        Regularization parameter to avoid over-fitting
density:     Rate of non-zero elements in recurrent connection matrix A
input_scale: Scaling parameter of the input matrix
rho:         maximum Eigenvalue of the matrix A
alpha:       Leaking rate
seed_value:  Seed value to generate random matrices

Make sure that the parameter search space is identical between the "frozen trial" section and the "objective function" section.

The following parameters are related to training and prediction of the time series.

n_trials:    Number of times to test with optuna (generate MAE for this number of times)
T_train:     Training period
T_test:      Forecast period
test_num:    Number of times for one test (to get one autocorrelation)
discard_len: Number of steps not learned at the beginning (not important).
MAX_TRIALS : Repeat the same thing while shifting each one step to produce robust result.

The history of bayesian optimization, "reservoir.csv" is generated.
