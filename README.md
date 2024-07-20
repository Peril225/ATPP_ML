# Report: Airplane Ticket Price Prediction

## Data Preprocessing
Firstly, except for the Price feature, every other feature had dtype as an object that needed to be processed. Features such as Airline, Source, Destination, Total_Stops, and Additional_Info are categorical features while the rest had object type but the values were continuous.

- **Route**: A redundant feature as total stops in the flight were already mentioned under the Total_Stops feature. Therefore, the Route feature was dropped.
- **Date of the Journey, Departure Time, and Arrival Time**: These features had datatype as an object and were converted to datetime for better understanding. The Date of the Journey was split into Journey day and Journey month. Similarly, Departure Time and Arrival Time were split into Hours and Minutes. After conversion, Date of the Journey, Departure Time, and Arrival Time were dropped.
- **Categorical Features Encoding**: Features like Airline, Source, Destination, Total_Stops, and Additional_Info were encoded using one-hot encoding.

## Exploratory Data Analysis

### Univariate Analysis
- Most of the ticket prices range from 1750 to 20,000, with a few prices just below 80,000. The average price is around 9000.
- Jet Airways has bookings above 3500, followed by Indigo and Air India with around 2000 and 1700 bookings respectively. Multiple carriers, SpiceJet, and Vistara have bookings below 1500. The Premium economy of Multiple carriers and Vistara, the Business class of Jet Airways, and Trujet have very few bookings.
- Most bookings had 1 to 2 stops, with only a few having 3-4 stops. Around 3000 bookings had no stops in the journey.
- A large number of bookings did not have any additional information. Some bookings did not include meals or did not have check-in baggage.
- Delhi was a highly preferred source of flights, and Cochin was a highly preferred destination. Chennai and Kolkata were the least preferred source and destination, respectively.

### Bivariate Analysis
- Jet Airways Business class has the highest price among all the airlines.
- Based on source and destination, the usual price range is around 10,000.
- For Business class mentioned as additional info, the price range is very high. One short layover, two long layovers, and red-eye flights have flat lines for box plots.
- Initial days of the month have higher prices (i.e., from 1 to 5). Afterward, the price remains between 8000 and 9000.
- For every month, the price remained above 9000, except in April, when the price dropped below 6000.
- The price is high if the arrival time is 5; otherwise, it remains below 10,000.
- When the departure hour is greater than 2, the price remains above 7000.

## Model Building
This problem is a regression task, which can be solved using a Regression model. Models such as Random Forest Regressor, Decision Tree Regressor, and Linear Regression are used to build and predict airplane ticket prices.

First, a Random Forest Regressor was built with every feature to compute feature importance. Based on feature importance, the features with more significance were utilized to build Linear Regression and Decision Tree Regressor models.

### Important Features:
- Airline_multiple carriers premium economy
- Source_mumbai
- Destination_hyderabad
- Airline_spicejet
- Additional_Info_business class
- Source_banglore
- Source_delhi
- Airline_vistara
- Destination_cochin
- Destination_new delhi
- Airline_indigo
- Airline_air india
- Additional_Info_no info
- Arrival_min
- Airline_multiple carriers
- Departure_min
- Departure_hour
- Arrival_hour
- Total_Stops
- Additional_Info_in-flight meal not included
- Airline_jet airways business
- Journey_month
- Airline_jet airways
- Journey_day
- Duration

## Model Evaluation
| Models                    | MSE          | MAE         | R²          |
|---------------------------|--------------|-------------|-------------|
| Random Forest Regressor   | 2253971.786  | 655.8830281 | 0.895465824 |
| Decision Tree Regressor   | 2676327.985  | 703.3827016 | 0.875877887 |
| Linear Regression         | 6911051.105  | 1804.129564 | 0.67948089  |

Random Forest has the least MSE and MAE among all the models, followed by Decision Tree. The accuracy of the Random Forest is 89%, and 87% for the Decision Tree. However, the Linear Regression model has an accuracy score of only 67% and has high MSE and MAE compared to other models.
