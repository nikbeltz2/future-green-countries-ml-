# Future Green Countries 

## Introduction

FutureGreenCountriesML is an ongoing machine learning project that currently forecasts the renewable energy share of 39 different countries from the years 2023-2035. Renewable energy share is the percent of electricity generation derived from renewable sources which generally includes solar, wind, hydro, geothermal, and biomass. In this project, the "true renewable share" is defined as electricity generation that comes from solar, wind, hydro, geothermal, tide, and solar thermal sources. Thus, the "true renewable share" includes sources that are both renewable and clean, a design choice made to eliminate the controversies revolving around the safety of nuclear energy despite it being a clean but not renewable energy source, and biomass, a renewable but arguably not very clean energy source. The purpose of "green forecasting" is to help us understand where some of the world's major powers stand in regards to achieving coming climate goals. Analyzing the current trajectory of a country's energy transition can impact climate and economic policy, as countries focus on making the world a greener place. It can also highlight the leaders, whose example, infrastructure, and policy can be followed. On the other hand, it reveals the slackers who can realize where and why they are lacking and pivot to the renewable sources that work best for them. 

## Data and Sources

The data used for the project was sourced from the International Energy Agency (IEA) via their excel sheets they provide on various data points. The data points used directly from the IEA include the Total Energy Supply (TES) by source, Total Final Consumption [of energy] (TFC) by source, Total CO2 Emissions and their sources, Electricity Generation by source, Total Electricity Consumption, CO2 Emissions per capita. GDP per capita is the final sourced data point, supplied by the World Bank Group. Of the 39 countries reported on, 32 are the official Member countries of the IEA with legal obligations and rights, 5 are Association countries who cannot vote but cooperate with less strict bounds and there is 1 Accession country, a country in the process of becoming a member. The final country who doesn't cooperate with the IEA at all is Russia, so their data is monitored through independent analysis and monitoring their trade with other countries. Data is taken from the years 2000-2022 for a modernized approach to the model as well as for reliability. A majority of the data are numbers straight from the IEA reports, while any missing points are extrapolated based preceeding and following years as well as supplemented by Our World in Data only if both the IEA and Our World in Data had similar numbers regarding non-missing data. 

## What is a Random Forest in Machine Learning?

Machine learning is the process of feeding a model, like Random Forests, a data set and training the model on that data. Training means that the computer tries to make predictions about data it has not seen, based on the data it has been feed. 

A Random Forest is a collection of decision trees that are formed by "Bootstrapping" data where each decision tree uses a different subset of data points taken from the main data set. These decision trees then make predictions based on certain conditions and these predictions are then each combined into a single point, "aggregating" the data. The "Random" comes from the random selection of data points for each decision tree, so the model is less sensitive to the training data. These different data subsets per tree also allows the trees to not be as correlated to one another, giving varied predictions. Variance is important because it allows for each data point to contribute to the final predicition and no one data point controls all outcomes. Another important feature of variance is that errors that occur across predictions are evened out when the final predictions are averaged together, providing a more stable answer. Random Forest was chosen for these attributes and additionally, because it is a regression machine-learning algorithm, meaning it is specifically used to find correlations between different input variables to predict an outcome. As opposed to other regression algorithms, Random Forest specifically can find correlations between non-linear data points, which is crucial as we consider 39 different countries, each with their own diverse energy profile.

## The Three Models: Linear, Static, Dynamic 

The three models used include a linear model, a static random forest model, and a dynamic random forest model. The linear model acts as a baseline, using the renewable share of each country from 2000-2022 as a slope to forecast what 2023-2035 would look like. In other words past years show that the renewable share grows at some x% and will continue to grow at that rate through 2035. This means the linear model is only influenced by a singular data point, the true renewable share defined above. 

The static model uses the energy data from the year 2022 for each country and predicts the following year's change in renewable share. The the features that predict the renewable share will not change year-to-year, hence a static model, as it continuously uses energy data from 2022 for each consecutive year. This differs from the linear model as it is not an average rate of change, but rather a consistent application of the random forest model. 

The dynamic model uses the same random forest model as the static model, but instead of using 2022 for each year's renewable energy share forecast, an approximation is made year by year via applying the median annual change in each of a country's energy features from 2000-2022. Thus, forecasts will vary each year due to fluctuation in data points, mimicking the actual world much more closely. 

## Model Performance Summary 

We use Mean Squared Error (MSE) and R2 Score to test the accuracy of our training and testing models relative to our actual data set. MSE measures the average squared difference between predicted and actual values, while R2 score measures how well a regression model explains the variance of the predicted variable. Note that variance here differs from model variance described above. Here, variance represents the percent at which the differing renewable share percentages across years are explained by the features of the data. For example, an R2 score of 0.0050 means that the model explains only 50% of why countries' renewable shares changed the way they did across a set of years. 

*insert picture of rf3_results* 

For training MSE, the predicted values and actual values only differ around 0.02%, demonstrating almost a perfect fit.

For training R2, the model explains around 85% of the variance in the training data, so it fits the data well. 

For testing MSE, the predicted and actual values differ by 0.14% showing the model is slightly less accurate when facing new data, though still a good fit.

For testing R2, the model only explains around 6% of the variance in the testing data. This is due to the fact that the testing years are from 2019-2021, thus the data is impacted severely by the effects of COVID-19. The design choice to keep the training and testing years as is instead of shifting the years used to 1995-2017 for example is to add realism as the pandemic was an unfortunate reality that we cannot erase, but it does allow us to prepare better for future happenings and the severity of their impacts. Thus, keeping the model years the same allows for the most modern data to be used, also an important matter as the world continues to change and advance, and attempt to model how the world has responded to a post-COVID world as well as eliminating a false reality of plainly forecasting the period in which we experienced COVID if we shifted to our final testing year to be 2017. 

## Key Findings 

Of the three models, the dynamic model performs the best, as hoped. The dynamic model is strong on a majority of countries, highlighting volatility and its ability to perform under varying data between countries. It also provides a sense of realism as the forecasting line fluctuates, unlike the linear and static forecasts, and the renewable share accelerates in countries such as Korea, Ireland, and Greece, portraying an optimistic view on growth in the near future. The static model follows the dynamic model closely due to the lack of real world factors, such as an influx of money into solar panels, that could shift the dynamic model significantly from the others. The linear model, due to its nature, offers a much slower growth for almost all countries in comparison to the other two models, especially when a country is gaining momentum in terms of renewable share growth. 

<p align="center">
  <img src="./results/new_zealand_forecast_.png">
</p>

<p align= "center">
  <img src="./results/united_states_forecast_.png">
</p>

Where the models fail to be 100% consistent in terms of what we might expect to happen in the real world are the models who have experienced more drops in share percentage than growth. When examining the linear model on countries such as Egypt, Indonesia, and Latvia, the "baseline" that the model offers can be viewed as a worst-case-scenario, thus when considering real world factors, stooping to this threshold is unlikely, meaining that if a country does follow the linear forecast in these examples, they are significantly failing when it comes to energy transition. 

The dynamic model struggles on to perform on Norway, Sweden and Switzerland, though these discrepancies can be explained by the features importance chart which explains what data have the most impact on model forecasting. Because of the design choice to exclude the renewable energy source biofuels from the group that contributes to renewable share, we see a negative trend line in Sweden and Switzerland. As for why the dynamic and static lines differ so much, this is due to the fact that Switzerland experienced major droughts in 2021 and 2022, leaving an outlier in electricity generation from hydro, which happens to be the most important feature in the feature performance chart. This resulted in a trend line was skewed heavily toward predicting greater decreases in hydro output, which doesn't typically happen without permanent plant shutdowns or extreme droughts. Lastly, in Norway, we see an increase in the total energy supply of oil, biofuels, and natural gas, and additionally extremely little flucutation among the renewable energy share of norway, which has hovered between 95% and 99% for 20 years straight. Because Norway has operated close to the maximum renewable threshold for so long, it is unlikely that their renewable share would follow the negative trend line the model predicts without experiencing unanticipated disruptions in policy or infrastructure. The model fails to capture this reality as it exaggerates Norway's decline based on the lack of renewable growth Norway has seen because they are already near the ceiling of renewable energy share. 

## Conclusion 

Overall, the dynamic model proved well in its ability to forecast the renewable energy share of 39 different countries for a period of 13 years. Though not perfect, the outliers are explainable, and it outperforms the baseline linear model on most occasions. The model then serves as a way to inform all, government policy makers, renewable energy investors, and the general public alike, of our current path and spark discussion about the future of renewable energy policy and investment as the world attempts to transition towards a greener and safer future. 

## Instructions 

1. Clone the repository
2. Create and activate the virtual environment: 

   `python -m venv sklearn-env`

   `source sklearn-env/bin/activate`

   Windows Users: 

   `sklearn-env\Scripts\activate`
3. Install dependencies:
   pip install -r requirements.txt
4. Place the IEA data file in the `notebooks` directory
5. Open and run `notebooks/renewable_share_forecast.ipynb` using Run all
   Results and forecast CSVs will be saved in the `results/` folder