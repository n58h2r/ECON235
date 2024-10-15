java c
ECON235
Report Assignment PART 2 (50 marks)
Due date: 5 pm, October 18, 2024. Upload your answers and R script. in the Assessment 2 section on Moodle.
Instructions:  This is an individual assignment. Use the starter R script. form. Moodle to create the dataset for your assigned city (London, Paris or Rome). The answer the questions below and submit your answers along with the full R script. Include your name, student number and tutorial group.
CHECKLIST: your submission must include the following
(1)      Report Part 2 in PDF format (Word files will not be accepted)
(2) R script. with your code (a file with an .R extension which can be run in RStudio)
Submissions that do not satisfy these two conditions will be returned for amendment and will have the late penalty applied on the per day basis.
QuestionsIn this section of the report, you will model the relationship between hotel prices and their distance from the city centre for your selected city. Make sure that 'hotelbookingdata.csv' file is in your Working Directory and then   run the starter R script. to create a dataset for your assigned city.
2.1 Getting started
Note that the starter file uses the following code to create the dataset for subsequent analysis:
city_data <- filter(df, city == 'London', year == 2017  month ==11  weekend ==0) |>
separate(accommodationtype,'@', into = c('garbage','acc_type')) |> separate(distance, ' ', into = c('distance','miles')) |>
select (-garbage, -miles) |>
filter(acc_type == 'Hotel') |>
select(hotel_id, distance, price, neighbourhood, starrating)|>
mutate(distance = as.numeric(distance))|> distinct()
Explain what this code does line-by-line.
In what follows please include all graphs that you produce and discuss into your report.
2.2 (5 marks) Explore the Distribution of the Variables
Begin by creating histograms for both the distance (distance from the city centre) and price (hotel price) variables. Additionally, generate a scatterplot with distance on the x-axis and price on they-axis to visualize the relationship between these two variables. In your analysis, carefully examine the patterns visible in the data. Consider the following:
(i) How do the distributions of distance and price look? Are they normal, skewed, or uniform?
(ii) Are there any outliers or extreme values in either variable?
(iii) Is there any visible relationship between distance and price in the scatterplot? Does it appear linear, non-linear, or are there any clusters?
Based on your observations, discuss the patterns in detail. Describe any peculiarities in the distributions or the scatterplot and highlight any extreme values that may warrant further investigation.
2.3 (10 marks) Addressing Extreme Values
Next, focus on dealing with extreme values (outliers) in the distance and price variables. For any potential outliers you identify, carefully examine the values of other variables in the dataset that could provide context for these observations, such as:
• The hotel’sstar rating
•   The city district or neighbourhood where the hotel is located
To better understand these extreme values, you may need to refer to external sources like Google Maps to verify the hotel’s location. This can help you understand if these extreme values are due to real-world factors   (e.g., hotels located far from the centre but offering luxury services) or data errors. After analysing these factors, decide how to handle the outliers.
Decide if you should:
(a) Remove the extreme values from your dataset?
(b) Transform. the variables or apply specific filters to exclude unrealistic data points?
Clearly state your criteria for handling the extreme values. Justify your approach (e.g., removing hotels with prices above a certain threshold, or restricting distances to within a reasonable range based on the city’s geography). Once you’ve finalized the dataset, recheck the histograms and scatterplot. Ensure that the patterns are now consistent with your expectations and that outliers have been appropriately addressed.
2.4 (6 marks) Linear regression
(a) Non-Parametric Lowess Fit
Begin by fitting a non-parametric Lowess (Locally Weighted Scatterplot Smoothing) curve to model the relationship between price and distance. This method allows you to visually explore the trend without assuming a specific functional form. Plot the Lowess curve on top of the scatterplot from Section 2.2.
After generating the Lowess curve, discuss the observed relationship. Is the trend linear, or does it show non-linear patterns such as curves or plateaus? Does the price drop or increase at certain distances, or is there a consistent trend? Based on the shape of the curve, evaluate whether a linear model seems appropriate for your data.
(b) Fitting a Linear Regression ModelNow, fit a linear regression model to the data to explore the relationship between hotel price (dependent variable) and distance (independent  variable) from the city centre. The equati代 写ECON235 Report Assignment PART 2R
代做程序编程语言on will be of the form.
price =  α  +  β * Distance +  ε
After estimating the model, reproduce the estimated regression line on the scatterplot to compare it with the Lowess curve. This will help you visualize  the differences between the non-parametric fit and the linear model.
Present the regression results in a table format. The table should include: the intercept and slope coefficients, standard errors, t-values, the R- squared value. Interpret the coefficients and comment on their significance.
2.5 (8 marks) Log transformations
(a) Creating Log-Transformed Variables Start by creating two new variables:
• Log-Price: The natural logarithm of the price variable.
• Log-Distance: The natural logarithm of the distance variable.
Produce histograms for both the log-price and log-distance. Comment on their distributions. Are they more normally distributed than the original variables? Are there any extreme values or outliers? Compare the shape of the log-transformed distributions with the original histograms from Section 2.2. Are the transformations useful in making the variables more evenly distributed?
(b) Scatterplots and model choice
Next, create three scatterplots to explore the relationship between price and distance under different specifications:
1. Log-Log Scatterplot: Plot log-price on they-axis and log-distance on the x-axis.
2. Log-Level Scatterplot: Plot log-price on they-axis and distance on the x- axis.
3. Level-Log Scatterplot: Plot price on they-axis and log-distance on the x-axis.
Evaluate which specification makes the most sense for your dataset. Is the relationship more linear in any particular specification? Does one model explain the variation in the data better? Are there any clear outliers or patterns in one scatterplot versus the others?
Based on the analysis, choose your preferred specification. Justify your  decision based on the patterns in the data and the interpretability of the model. For example, if the log-log specification gives a clearer linear relationship, you may prefer that. Alternatively, if distance affects prices in absolute terms, a level-log or log-level specification might be more suitable.
(c) Now, fit a linear regression model based on the specification you selected (log-log, log-level, or level-log). The regression equation will depend on your chosen model. After estimating the model reproduce the estimated regression line on the scatterplot (just like instep 2.4). Present the regression results in a table format, discuss their statistical significance and interpret them. Note that interpretation of the regression coefficients will depend on the model that you have chosen.
2.6 (6 marks) Linear piecewise spline
Now fit the linear piecewise spline model in levels (no logs) with one knot (cutoff point).
To choose the knot first, examine the Lowess fit from Section 2.4(a) to visually identify where the relationship between price and distance seems to change. This point of change will serve as the knot (cutoff) in the spline regression model. For example, you might notice that after a certain distance (say 3 miles from the city centre), the relationship between price and distance becomes less steep or even reverses. This distance would be your knot.
Fit a piecewise linear spline model that divides the relationship into two parts—before and after the knot—allowing for different slopes on each side of the cutoff point. Present the regression results in a table format, discuss  their statistical significance and interpret model coefficients.
2.7 (15 marks) Choosing the best model
Now you’ve estimated three different models:
1. Linear regression: This model assumed a linear relationship between price and distance.2. Your chosen model with log transformations: This could be either a log- log, log-level, or level-log model, which transformed the variables to better fit the relationship.3. Piecewise linear spline model: This model allowed for different slopes before and after a chosen cutoff (knot), providing flexibility in the price-  distance relationship.
Which of these models explains the data better? Justify and explain in detail your choice!
Once you have chosen the best model. Use it to conduct residual analysis to find the best priced hotels in your city.  Save the residuals and the fitted as new variables in your dataset. Use residual analysis to identify the best and worst hotel deals. Include a table of best and worst hotel deals (identified by their ids) in your report.
Produce the scatterplot of data showing the estimated regression line for the best model and five best deals (in green) and five worst deals (in red). All other observations must be of the same uniform. colour.
Finish this part of the report by discussing the results of your analysis. What are its limitations? Which steps would you take to produce a better model   of the relationship between hotel price and distance.







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
