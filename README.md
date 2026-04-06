# Future Green Countries 

## Introduction
FutureGreenCountriesML is an ongoing machine learning project that currently forecasts the renewable energy share of 39 different countries from the years 2023-2035. Renewable energy share is the percent of electricity generation derived from renewable sources which generally includes solar, wind, hydro, geothermal, and biomass. In this project, the "true renewable share" is defined as electricity generation that comes from solar, wind, hydro, geothermal, tide, and solar thermal sources. Thus, the "true renewable share" includes sources that are both renewable and clean, a design choice made to eliminate the controversies revolving around the safety of nuclear energy despite it being a clean but not renewable energy source, and biomass, a renewable but arguably not very clean energy source. The purpose of "green forecasting" is help us understand where some of the world's major powers stand in regards to achieving coming climate goals. Analyzing the current trajectory of a country's energy transition can impact climate and economic policy, as countries focus on making the world a greener place. It can also highlight the leaders, who's example, infrastrucutre, and policy can be followed, while slackers can realize where and why they are lacking and pivot to renewable sources that work best for them. 

## Data and Sources

The data used for the project was sourced from the International Energy Agency (IEA) via their excel sheets they provide on various data points. The data points used directy from the IEA include the Total Energy Supply (TES) by source, Total Final Consumption [of energy] (TFC) by source, Total CO2 Emissions and their sources, Electricity Generation by source, Total Electricity Consumption, C02 Emissions per capita. GDP per capita is the final sourced data point, supplied by the World Bank Group. Of the 39 countries reported on, 32 are the official Memeber countries of the IEA with legal obligations and rights, 5 are Association countries who cannot vote but and cooperate with less strict bounds and there is 1 Accession country, a country in the process of becoming a member. The final country who doesn't cooperate with the IEA at all is Russia, so their data is monitored through independent analysis and monitoring their trade with other countries. Data is taken from the years 2000-2022 for a modernized approach to the model as well as for reliability. A majority of the data are numbers straight from the IEA reports, while any missing points are extrapolated based pre and proceeding years as well as supplemented by Our World in Data only if both the IEA and Our World in Data had similar numbers regarding non-missing data. 

# What is a Random Forest in Machine Learning?

Machine learning is a ... 

## The Three Models: Linear, Static, Dynamic 

The three models used include a linear model, a static random forest model, and a dynamic random forest model. The linear model acts as a baseline, using the renewable share of each country from 2000-2022 as a slope to forecast what 2023-2035 would like. In other words passed years show that the renewable share grows at some x% and will continue to grow at that rate through 2035. This means the linear model is only influenced by a singular data point, the true renewable share defined above. 
The static model uses the energy data from the year 2022 for each country and predicts the following year's change in renewable share. The renewable share will not change year-to-year, hence a static model, as it continously uses energy data from 2022 for each consecutive year. This differs from the linear model as it is not an average rate of change, but rather a consistent application of the random forest model. 
The dynamic model uses the same random forest model as the static model, but instead of using 2022 for each year's renewable energy share forecast, an approximation is made year by year via applying the median annual change in each of a country's energy features from 2000-2022. Thus, forecasts will vary each year due to fluctuation in data points, mimicing the actual world much more closely. 

## Model Performance Summary 

## Key Findings 

## Instructions 