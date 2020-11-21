# Disease-Forecasting-A-COVID-19-Case-Study

This year, Coronavirus has dominated the news, especially in India.
It was all that people were talking about for the first 3-4 months.
I remember during the initial phases of the lockdown, people often had these questions. 
Questions like where did the virus come from? Who does it affect the most? Which areas in India are worst hit by the pandemic? And finally, where do we see ourselves for a few weeks/months from now? 
In order to answer these questions I took up this project.

Daily Cases


To start off with my analysis, I observed the daily increase in India's number of cases for the first six months. 
There were four lockdown phases during the beginning of the virus outbreak. The first phase lasted almost a month, starting from the third week of March till April 21st. All non-essential services were shut down in this period by the government. The second phase was a continuation of the first and continued till the end of April. The third phase began with easing some of the lockdown restrictions and spanned May's first 15 days. 
And the last stage, after which all restrictions were lifted, lasted till the end of May. 
For each lockdown the number of new confirmed cases is higher at the end of lockdown as compared to the begining of Lockdown . 
Even after 4 Lockdowns the number of cases have increased significantly. This might be due to increased testing of People. So question is, was Lockdown successful ?. 
One might think that government has done good job with its limited amount of Resources and situation could be worse if there was no Lockdown. 
Others might think that government should have taken action early in the month of February and could have handled the situation better like South Korea, or New Zealand who shut down all kinds of re-entry into their counttries at the right time.
The number of daily deaths is increasing significantly over the months. Currently the number of deaths are increasing with 350+ daily . One thing to notice about above graph is on 17 th June , India has reported 2003 Deaths. I wonder whats the reason behind the number of deaths to be high on that particular day.
Inference: As the number of daily new cases has increased so as the number of recovered cases . On 26 th June India had the most recovered cases over these months.

Gender and Age - Distribution

This contained the personal information of all the people who contracted the virus from 30th of January till the 7th of July.

Upon close inspection of the patient data (pulled from Kaggle), I make the following observations
   1.  Of the 168148 patients in the database, 95694 of them had missing entries in the age-bracket column, so I obviously removed them.
       Patients from the age-bracket 28-32 had the highest number of confirmed cases since they tend to move out more.However, patients in the age group 57-67 had a higher fraction of deceased patients, suggesting that they are more vulnerable to the virus and their safety is of utmost priority.
   2.  Of the 168148 patients in the database, 96417 of the entries had no records of any gender.Upon discarding them,
       It was found that Males(66.5%) are more likely to contract the virus than males (33.5%)
   3.  Maximum transmissions were local, which means that community transmission has begun and India has moved on to stage 4.


StateWise Analysis

On inspecting the spread of the virus state-wise, I make the following observations : 

1. Maharashtra has the most no of cases by a large margin accounting for over 21% of the cases, along with a mortality rate of 3% (the highest) and a 
recovery rate of 72% which is good but not that impressive compared to other states.

2. Delhi has the highest recovery rate of almost 89%.

3. Gujarat accounts for roughly 2.6% of Covid Cases in the country but still has the highest mortality rate of 3.11% surpassing Maharashtra. Safety measure need to be prioritized here.

4. Andhra which is the second most infected state has a mortality rate under 1% proving to be the most efficient state during the lockdown.


Finally towards the most interesting part of the project - the forecasting. By how much do we expect the no of cases to increase and how accuarate are these predictions.
Normally we look at standard regression models 
PROPHET FORECASTING

Forecasting is often employed in many organizations such as supply chain management, sales and economics not just in the weather industry.Prophet package was first developed by Facebook's Core Data Science team as an open source tool for forecasting. 
Automated forecasting can be inflexible as it fails incorporating an analysts domain knowledge.
Prophet begins by modeling a time series using the analysts specified parameters, producing forecasts and then evaluating them. 
Using Prophet method to forecast the trends in the next 6 months by following certain trends.Non-linear.First fit the model based on pr_data.
Make a future dataframe and set period = 180. Call predict to make predictions on the future dataframe and store it in forecast. 
yhat- uncertainity interval along with it's lower and upper bounds. trends - long-term increase or decrease in the data. weekly - weekly trends.

This is one of the most attractive features of Prophet. 
It essentially does all of the model selection work for you and gives you a result that works well without much user input required. 
In this case we didn’t have to specify anything at all, just give it some data and we get a model.

The intuition behind Prophet forecasting is to divide our timeseries model into three main model components : trend,seasonality,and holidays

1. Trend : Trend is a linear or logistic growth curve used for modelling the trend or the non-periodic changes in the data.The linear fitting exercise ensures that it is least affected by spikes/missing data.

2. Seasonality : Any periodic changes in the data. For instance in this case, if we want to look into the weekly seasonality of the Covid cases,whether or not there is
a pattern in the spikes There are more cases than usual on a Sunday for example when people tend to go out more than there are on a Tuesday.

3. Holiday : This model takes care of any special occurences/outliers/irregularities in the dataset. These have to be annualy added into the model in form of a dataset.
However, in our case there is no holiday or recurring event . Thus, this is of no concern.

We achieved a MAPE of 4.34 % on the India dataset dated till 27/10/20. Increased rise in the no of cases on Saturday and Sunday.

The point estimate forecasts are in the “yhat” column, but note how many columns got added. 
In addition to the forecast itself we also have point estimates for each of the components, as well as upper and lower bounds for each of these projections. 
That’s a lot of detail provided out-of-the-box just by calling a single function!

limitation is the lack of ability to incorporate additional information into the model.
One can imagine variables that could be used along with the time series to further improve the forecast 
We can’t do anything like this with Prophet directly.

ARIMA FORECASTING

This acronym is descriptive, capturing the key aspects of the model itself. Briefly, they are:

AR: Autoregression. A model that uses the dependent relationship between an observation and some number of lagged observations.
I: Integrated. The use of differencing of raw observations (e.g. subtracting an observation from an observation at the previous time step) in order to make the time series stationary.
MA: Moving Average. A model that uses the dependency between an observation and a residual error from a moving average model applied to lagged observations.

Stationary Time Series : A stationary time series is one whose properties do not depend on the time at which the series is observed.  
Thus, time series with trends, or with seasonality, are not stationary — the trend and seasonality will affect the value of the time series at different times.

