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
<img width="571" alt="Screenshot 2023-06-05 at 10 12 46 PM" src="https://github.com/eckoecho/Prediction-of-Product-Sales/assets/43970023/d2276846-d735-4c7f-bb74-29410936cc5d">


