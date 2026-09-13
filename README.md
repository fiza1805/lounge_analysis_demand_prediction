## Lounge Demand Prediction & Capacity Planning

A data driven approach to predicting airline lounge demands and determining capacity risks based on historical flight and passenger eligibility data.

## Project Summary

Predicting airline lounge demand based on historical passenger eligibility data

Airline lounge demand can vary according to haul, arrival region, time of day and aircraft capacity.
This project develops a pragmatic, data driven approach to:
1. Determine flight segments based on historical airline data
2. Calculate historical lounge eligibility rates

3. Develop a reusable demand lookup table

4. Forecast estimated lounge demand for a given flight profile
5. Assess capacity utilisation

6. Identify capacity shortfalls

7. Perform demand growth scenario analysis
8. Develop business recommendations
The approach is developed as a historical data decision support framework rather than a live predictive model.
---
## Business Problem
Airport lounge operators need to know if their capacity is sufficient to meet passenger demand.
It may not always be possible to know the passenger demand at a future date.

A pragmatic approach is required to estimate the future demand based on historical patterns and identify any capacity risks.
This project answers exactly that question by leveraging historical lounge eligibility patterns to develop a reusable demand lookup table for different flight segments.
---
## Approach
The approach taken in this project can be broadly summarised as below:
```text
Historical Airline Data
↓
Data Cleaning & Validation
↓
Exploratory Data Analysis
↓
Flight Segmentation
↓
Lounge Eligibility Analysis
↓
Demand Rate Lookup Table
↓
Flight-Level Demand Estimation
↓
Capacity Utilisation Analysis
↓
Future Schedule Planning
↓
Sensitivity & Growth Scenarios
↓
Business Recommendations
```
Wherein, the flights were segmented primarily by haul, arrival region and time of day followed by determining historical lounge eligibility rates and developing a lookup framework.
---
## Dataset
The data used for this project was obtained from the British Airways Summer Schedule Dataset as a part of the Forage Data Science programme.
It consists of 10,000 flight records spanning between April 1st, 2025 and October 30th, 2025.
The relevant variables include:
1. Flight date-time
2. Departure and arrival airports
3. Arrival region
4. Haul
5. Aircraft type
6. First class seats
7. Business class seats
8. Economy seats
9. Tier 1 eligible passengers
10. Tier 2 eligible passengers
11. Tier 3 eligible passengers
Wherein, the notebook first ensures the validity of the date range of the flight records.
---
## Flight Segmentation
The flights were initially grouped together using haul × arrival region × time of day.
There were 16 such operational groups:
```text
SHORT - Europe - Morning
SHORT - Europe - Lunchtime
LONG - North America - Morning
LONG - Asia - Afternoon
LONG - Middle East - Evening
...
```
The most common of which, SHORT-haul Europe Morning had 2,069 flights.
---
## Lounge Demand Rate
For each group, the passenger eligibility was aggregated and converted into percentages.
The lookup table ultimately takes the form of:
```text
Haul
Arrival Region
Time of Day
Tier 1 %
Tier 2 %
Tier 3 %
Lounge Demand Rate
```
This approach essentially allows for estimating lounge demand for any given flight without the need for more granular data.
The lookup table was created by aggregating all flights, seats and eligible passengers for a given group.
---
## Demand Rate Insights
The lounge-demand rate for the following flight segment was the highest found in the data:
SHORT-haul Europe Lunchtime
with the lounge-demand percentage coming at 22.22%
According to the dataset this flight would see a relatively larger demand than the other flight segments.
---
## Flight Level Estimation
With the demand rate lookup framework in place, we can estimate the lounge demand for a given flight.
Using the following example:
| Parameter | Value |
| --------- | ----- |
| Haul | SHORT |
| Arrival Region | Europe |
| Time of Day | Lunchtime |
| Total Seats | 180 |
| Tier 1 Expected Demand | 0.7 |
| Tier 2 Expected Demand | 8.2 |
| Tier 3 Expected Demand | 31.1 |
| Total Expected Demand | 40.0 |
The demand estimate for this flight can be compared to the capacity of the lounge.
---
## Capacity Risk
Assuming that the 180-seat aircraft above has a lounge capacity of 35, the capacity utilisation and risk can be estimated as:
| Parameter | Value |
| --------- | ----- |
| Expected Lounge Demand | 40 |
| Lounge Capacity | 35 |
| Capacity Utilisation | 114.3% |
| Potential Shortfall | 5 |
| Capacity Risk | High Risk |
This provides a useful capacity-planning insight for the airline operator.
---
## Schedule Level Planning
Using the same approach, a capacity-planning estimate can be done for an entire future schedule.
Using this illustrative example, the following estimates were made:
| Parameter | Value |
| --------- | ----- |
| Total Expected Demand | 144.2 |
| Average Capacity Utilisation | 103% |
| Flights Over Capacity | 2 |
| Potential Shortfall | 9.2 |
This provides a useful overview of the demand for the entire future schedule.
---
## Sensitivity Analysis
In addition to the capacity risk for the illustrative flight example in 🛫 Flight Level Estimation, a sensitivity analysis was done to see how the demand growth would impact the capacity requirements.
| Demand Growth | Projected Demand | Capacity 35 | Utilisation | Shortfall |
| ------------: | ---------------: | ----------: | ----------: | --------: |
| 0% | 40 | 35 | 114.3% | 5 |
| 10% | 44 | 35 | 125.7% | 9 |
| 20% | 48 | 35 | 137.1% | 13 |
| 30% | 52 | 35 | 148.6% | 17 |
The analysis demonstrates that demand growth can put a significant strain on the available capacity.
---
## ML Model Comparison
Several supervised machine learning models were tested to see if any could accurately predict lounge demand given the variables.
The models tested were:
1. Linear Regression baseline
2. Random Forest
While the Random Forest had a decent performance:
```text
MAE : 18.18
RMSE : 22.81
R²  : -0.22
```
... the project proceeded to utilise the more accessible lookup table method instead of trying to force a machine learning model to fit the data.
---
## Business Insights
From this analysis the following business insights were made:
1. It can be seen that SHORT-haul Europe flights have the highest lounge demand rate amongst all other flight segments.
2. Particularly, SHORT-haul Europe Lunchtime appears to be a very busy segment.
3. Some segments can exceed the capacity of the available lounges.
4. Demand growth can lead to significant capacity shortfalls.
5. Capacity planning should be done at a flight segment level rather than assuming that all aircraft capacity is suitable for a lounge.
6. A future lookup table can be a valuable asset for an airline planner who does not have access to more granular data.
---
## Tools & Technologies
Python, Pandas, NumPy, Matplotlib, Jupyter Notebook, Excel dataset, Statistical analysis, Data aggregation, Scenario analysis, Simple machine learning.
---
## Future Work
Some of the potential future work that can be done on this project includes:
1. Retraining demand rate lookup table with more recent data
2. Including more variables in the analysis
3. Doing a more granular analysis
4. Building a dashboard for the airport planners
5. Using more advanced forecasting methods
This is only a small insight into what can be done with the right data. This project itself is a very simplistic analysis based on historical data.
---

## Project Author

M Sumaiya

B.Tech – Computer Science & Engineering
Specialisation: Artificial Intelligence & Data Science
