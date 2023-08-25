# ![ds git](https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/412d74b9-43e6-4d64-9ba5-e705326cb6a7)
**Prediction of Product Sales**
----
## **Inspecting Outlet Features to Predict Sales**
---
**Author**: Echo Diaz

Our goal of this is to help retailers understand the properties of products and outlets that play crucial roles in increasing sales. Our target is to increase Item Sales per Outlet. To do so, I inspect features that contribute to outlet sales.

---
**Data Source**:
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
### **Exploratory Data Analysis (EDA)**
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
### **Explanatory Data Analysis**
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
# **Recommendations**

## For those who own or manage outlets:

My analysis indicates the need for quick, low-effort foods. Adding more ready-made or on-the-go foods increase outlet sales.

Futhermore, higher Item MRP increase outlet sales. Stock each outlet with higher MRP and sales will increase.

## Model Performance: 

The Decision Tree has the better overall regression metrics (MAE, MSE, RSME), I fine-tune the model by adjusting the hyperparamater of `max_depth`.  Deploy this model to have future predictions.
---
# **Limitations & Next Steps**

This model could be improved by diving further into grouping Item Types and inspecting different Outlet Size and Outlet Identifiers.

--
### Coefficients Interpreted
![plot_linreg_coefficients](https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/f05de8b1-97fc-4970-9f1b-f6348fc00f78)

* If the `outlet_identifier_OUT027` feature increases by 1 unit it will increase the outlet sales by at 675. This outlet seems to have a significant positive impact on sales, possibly due to factors like its location, size, marketing strategies, or product assortment.
* If we increase the `outlet-location-type-tier3` feature by 1 unit it increases outlet sales 675. This could imply that products sold in locations categorized as "Tier 3" have a positive impact on sales, possibly due to factors like demographics, local preferences, or economic conditions.=
* If we decrease the `outlet-type_grocery_store` by 1 unit it decreases the outlet sales by 856.  This might indicate that "Grocery Store" outlets have a negative impact on sales, possibly due to factors like limited product variety, lower foot traffic, or pricing strategies.



### Feature Importance Interpreted
![plot_rf_important_features](https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/453c844c-8ed0-4fc9-a5fa-699199a5aa69)

 Higher importance values means a feature has a stronger impact on this RegressionForest's predictions.
* The item's MRP (maximum retail price) has the strongest impact (.467) on the prediction of sales.
* Outlet Type Grocery Store has the 2nd strongest impact on the prediction of sales with .192.
* An item's visibility has the 3rd strongest impact on prediction of sales with .121.
* Outlet 027 has a significant impact on the prediction of sales with .043.
* Supermarket Type3 has a significant impact on the prediction of sales with .033.

#### Summary Bar Plot - bar version
![summary_plot_rf_feature_importance](https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/d579e4c6-0828-47d8-b275-99b436623fab)

Your comparison of most important features found by shap vs feature importance:
As you can see from the plots above, RandomForestRegressor and Shap's top features have overlapping results, agreeing on the importance of `Item_MRP` and `Outlet_Type_Grocery Store`.  `Item_Visibility` is in RandomForestRegressor's top features while Shap's model picked `Outlet_Identifier_OUT027`. The difference could be explained by the randomization used in the Shap model. 

### Summary Dot Plot -  Top 3 Important Features Interpreted 
![summary_dot_rf_feature_importance](https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/a915202d-0a6b-4b14-9f0c-52a3cd028701)

* `item_mrp` The red dots indicate a high positive SHAP value and suggests that as the Maximum Retail Price of an item increases, the RegressionForest's predictions of outlet sales also increase.
* `outlet-type_grocery_store` A high negative SHAP value for this feature indicates that when products are sold in "Grocery Store" type outlets, the model predicts lower sales. Products sold in grocery store outlets have a negative impact on sales, possibly due to factors like limited product variety or lower foot traffic in such outlets.
* `outlet-identifier-OUT027` A high positive SHAP value for this feature indicates that products sold in the outlet with identifier "OUT027" are associated with significantly higher predictions of sales. Sales are substantially increased when OUT027's products are sold. This outlet seems to have a unique and positive impact on sales, possibly due to various factors like location, popularity, or effective marketing.

---
# **For Further Information**
For any additional questions, please contact:

Echo Diaz (Data Scientist)
eckoecho@gmail.com
