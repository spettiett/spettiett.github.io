---
layout: post
title:      "Time Series: Converting Transformed Data to Original Scale"
date:       2019-12-01 14:51:21 +0000
permalink:  time_series_converting_transformed_data_to_original_scale
---


So, you just worked through several Stationarity Assumptions to properly 
transform your original dataset in preparation for time series modeling.  
To make a time series stationary, you may have performed the following:

**To Remove Trend:  **

	If your data has a strong trend (positive or negative) you can consider using the following to reduce the trend.  These transformations may be: log, square root, cube root, and/or smoothing  	using a rolling average/moving average or exponentially weighted 	moving average, etc. 

**To Remove Seasonality and Trend:**

	If your data shows both a strong trend and seasonality, then you may 
	consider using differencing,  etc.

**Note:** With some data you may need to use a combination of these 
transformations.  In order to satisfy the Stationarity assumptions.

Once you have performed the transformation(s) and re-test using a statisticaltest like Dickey-Fuller test and confirm that your p-value is less than .05, then you are ready to continue modeling the transformed data. 

However, after the modeling process and it is time to forecast your data you will want to perform the forecasting on the original scale. So, we need to **un-transform** your data.

So, the following examples show you how to work backwards from log, 
differencing and/or rolling average to get to the original scale.

________________




**EXAMPLE** | The monthly median home price in a specific zip code (2008-2018). 

**Original Dataset**

> ts_77478.head()

time

2008-04-01    218900.0

2008-05-01    217000.0

2008-06-01    215400.0

2008-07-01    214800.0

2008-08-01    215200.0

 
**Convert Log back to Original Scale**

> LogDataexp = np.exp(np.log(ts_77478))
> LogDataexp.head()

 time
2008-04-01    218900.0

2008-05-01    217000.0

2008-06-01    215400.0

2008-07-01    214800.0

2008-08-01    215200.0


**Convert Log + Diff(1) back to Original Scale**

> logData = np.log(ts_77478)

> logDiff = logData.diff(1)
> logDiffcumsum = logDiff.cumsum()
> logAftercumsum = np.exp(logData).add(logDiffcumsum, fill_value=0)

> OriginalData  = logAftercumsum

> OriginalData.head()

time
2008-04-01    218900.000000

2008-05-01    216999.991282

2008-06-01    215399.983882

2008-07-01    214799.981092

2008-08-01    215199.982953


**Convert Subtract Rolling Mean + Log + Diff (1) back to Original Scale**
> log_data = np.log(ts_77478)
> rolmean = log_data.rolling(window = 12).mean()
> log_data_minus_rolmean = log_data - rolmean
> diff_log_data_minus_rolmean = log_data_minus_rolmean.diff(periods=1)

 
> diff_log_data_minus_rolmean.head(24)

time
2008-04-01         NaN

2008-05-01         NaN

2008-06-01         NaN

2008-07-01         NaN

2008-08-01         NaN

2008-09-01         NaN

2008-10-01         NaN

2008-11-01         NaN

2008-12-01         NaN

2009-01-01         NaN

2009-02-01         NaN

2009-03-01         NaN

2009-04-01    0.002516

2009-05-01    0.000176

2009-06-01   -0.001116

2009-07-01   -0.000766

2009-08-01   -0.001726

2009-09-01   -0.001683

2009-10-01   -0.001199

2009-11-01    0.000159

2009-12-01    0.001108

2010-01-01    0.000386

2010-02-01   -0.001478

2010-03-01   -0.002793

 
> rolmeancumsum = diff_log_data_minus_rolmean.cumsum()
> rolmeanlogAftercumsum = np.exp(logData).add(rolmeancumsum, fill_value=0)
> rolmeanlogAftercumsum.head()

time
2008-04-01    218900.000000

2008-05-01    217000.000000

2008-06-01    215400.000000

2008-07-01    214800.000000

2008-08-01    215200.000000


 


