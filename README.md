# ![ds git](https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/412d74b9-43e6-4d64-9ba5-e705326cb6a7)
Prediction of Product Sales
----
## Inspecting Outlet Features to Predict Sales
---
**Author**: Echo Diaz

Our goal of this is to help retailers understand the properties of products and outlets that play crucial roles in increasing sales. Our target is to increase Item Sales per Outlet. To do so, I inspect features that contribute to outlet sales.

---
Data Source:
[sales_predictions_2023.csv](https://drive.google.com/file/d/1syH81TVrbBsdymLT_jl2JIf6IjPXtSQw/view)
---

**Data Dictionary:**
| Variable Name | Description |
| --- | --- |
| **Item_Identifier** | Unique product ID |
| **Item_Weight** | Weight of product |
|**Item_Fat_Content**| Whether the product is low fat or regular|
|**Item_Visibility**|	The percentage of total display area of all products in a store allocated to the particular product|
|**Item_Type**| The category to which the product belongs|
|**Item_MRP**| Maximum Retail Price (list price) of the product|
|**Outlet_Identifier**| Unique store ID|
|**Outlet_Establishment_Year**| The year in which store was established|
|**Outlet_Size**| The size of the store in terms of ground area covered|
|**Outlet_Location_Type**| The type of area in which the store is located|
|**Outlet_Type**| Whether the outlet is a grocery store or some sort of supermarket|
|**Item_Outlet_Sales**| Sales of the product in the particular store. This is the target variable to be predicted.|

---
## To prepare this data, the data was cleaned, and the following processes were performed:
### Exploratory Data Analysis (EDA)
```
- During the exploratory data analysis, a mixture of scatterplots, barplots, boxplots, and histograms were visualized for each datatype column. 
- Boxplots and barplots were visualized for each categorical column. 
- Scatterplots and boxplots were visualized for numerical columns.
- This gave a good baseline for all of the numeric and categorical columns for univariate EDA.
```
<img width="573" alt="Screenshot 2023-06-05 at 10 20 10 PM" src="https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/39d69c41-7621-409b-8cd7-555c00d38321">

<img width="522" alt="Screenshot 2023-06-05 at 10 20 18 PM" src="https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/1b92742f-a658-4f60-a2ef-d2cbff5adb00">


This histogram and boxplot shows the number of outlets and their respective Outlet Sales. The majority of Outlet Sales fall around $2,000.

---
### Explanatory Data Analysis
<img width="606" alt="Screenshot 2023-06-06 at 9 15 35 PM" src="https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/bfa6238d-97a5-476c-8922-fc2a6a706886">

```
- To visualize the data for explantory purposes, the scatterplot shows a positive trendline to Item MRP.
- The scatterplot was chosen to show how Item MRP effects Outlet Sales. 
- Finally, we see higher Item MRP increases Outlet Sales. 
```

<img width="598" alt="Screenshot 2023-06-06 at 9 16 16 PM" src="https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/7d4679ff-8b21-4c5c-9938-aae3cc909130">

This shows the quantity of items per food category. We see that the top counts of food categories include:
1. Fruits and Vegetables
2. Snack Foods
3. Household
4. Frozen Foods

---
# Recommendation

## For those who own or manage outlets:

My analysis indicates the need for fast and low effort foods. Adding more ready-made or on-the-go foods increase outlet sales.

Futhermore, higher Item MRP increase outlet sales. Stock each outlet with higher MRP and sales will increase.

## Model Performance: 

The Decision Tree has the better overall regression metrics (MAE, MSE, RSME), I fine-tune the model by adjusting the hyperparamater of `max_depth`.  Deploy this model to have future predictions.
