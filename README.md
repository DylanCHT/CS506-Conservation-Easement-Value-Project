# CS506-Conservation-Easement-Value-Project

## Team Member: Qingyang Xu, Kailun Li, Ziyu Shen, Chenhao Tao


## Introduction

The primary purpose of this project is to explore the impact of the conservation easement on the value of lands in Massachusetts. Conservation easement refers to a legal agreement that places a set of permanent restrictions on a property. Many landowners use land conservation as a “tax hack” to get tax reduction while land trusts are trying to protect more lands. Nowadays, the main predictions works of the easement values are ‘manually’ done by the appraisers. The disadvantage of using this method is that the entire process can be too long, and the final assessment may be affected by the appraisers who may have different standards and opinions on the property. In other words, currently, there is no unbiased way to determine the value of a property, which is designated as a “conservation easement.”12
We want to create models to emulate the appraisal process: determine the price to pay to conserve a land parcel using its size, location, land purpose, and several other topographical information. By training the dataset without easement, we hope to find a suitable model to predict the value and percentage reduction in values of the land after they are protected by easements. In our project, we will run several models, such as linear regression and randomforest regressor, as well as using tools such as cross validation to further tune our model. In the end, we choose to use the RandomForest Regressor. This predictive model can be used in the future to detect any land transactions that may be out of the normal price range, indicating the land owner may be trying to use conservation as a “tax hack.”
<img width="815" alt="Screen Shot 2019-12-30 at 11 39 59 AM" src="https://user-images.githubusercontent.com/43009748/71567395-ad3e8380-2af9-11ea-8f70-cee250f2d3bc.png">

## Methodology

Our goal in this project is to find the impact of easement on the sale price of the land. Because the limited amount of data we have for land with easement, we decided to first create a predictive model for sale price based on the data of land without easement, which contributes to over 90% of the whole dataset. Once we got the predictive model, we would use it to predict the sale price for land with easement. By comparing the difference between the two prices (predicted sale price without easement and the real sale price with easement), we would identify the impact of easement on the sale price of land. 

For predictive models, we were choosing between Linear Regression, RandomForest Regressor, Gradient Boosting Regressor, and DecisionTree Regressor. By comparing the MAE on each regression model, we decided to use RandomForest Regressor since it gave us the lower MAE. 
 
After choosing the model with the lowest MAE which is RandomForest Regressor, we train the model with the variables we chose with parameters n_estimators = 100 and max_depth = 11 (Explained in Model Evaluation). Then, we used our predictive model to predict the sale price of the properties with easement. 

Lastly, we will use the formula below to estimate the impact of easement the sale price of properties: 
Impact of Easement = {(Estimated Sale Price - Real Sale Price) / Real Sale Price}* 100%

## FINDINGS AND RESULTS

<img width="684" alt="Screen Shot 2019-12-30 at 11 41 13 AM" src="https://user-images.githubusercontent.com/43009748/71567344-4f11a080-2af9-11ea-8e0c-897e990d0c39.png">

After obtained and trained an optimal predictive model on the sale price of lands without easements, we used the model to predict the sale price of lands with easement, and found the mean percentage difference of predictive sale price and real sale price. The figure below shows a plot of prediction and true target. As we can see, the points lie around the line y = x, which implies that our prediction is generally accurate.
Result of the prediction of the sale price of land with easement
Using the formula stated in the Methodology section, we found the impact of easement on the sale price of the land to be: Impact of Easement = {(Estimated Sale Price - Real Sale Price) / Real Sale Price}* 100% = 39.20%
The result we got shows that the sale price without easement (estimated) is 39.20% higher than the sale price with easement (real), which meets our assumption before running the model. Easement does have a significant impact on the sale price of lands.
Nowadays, land trusts and conservation organizations are still using manual processes to evaluate the price of easement. We hope that by using our prediction model, the appraisal
 
process would become more transparent, unprejudiced and efficient. With a scientific method, land trusts are able to reduce the cost of hiring appraisers in the easement appraising process. Moreover, by using a scientific model, we will also be able to avoid overpriced appraisal and even tax evasion.

## FURTHER IMPROVEMENTS

Although the final result we got is accordant to what expected, which is the conservation easement has significant negative impact on the sale price of land, however, there are some potential improvements that could have been done if we have more time. Firstly, if we look at the graph in the result part, we can see that when the price is low, the plots are randomly distributed in the graph and are not show a linear relation. This means that in the lower price range, the impact of the conservation easement on the price of land is unclear. In the higher range of price, we can see a clear relation between prediction and true value; this means that our predictive model works well in this price range. There are some possible explanations: firstly, it could be that the sales of land with low prices don’t reflect the true value of that land. In the dataset, we can see that many land sales have prices under $1000, which are not reasonable prices. Those sales may be caused by the owner’s gifting of land, thus don’t reflect the true value. Another possible explanation could be the dataset for land with an easement is too small to reflect the true market reaction to this kind of land. We would further look into this issue and figure out the true reason for this and improve the prediction performance in the lower price range. Another improvement we want to do is to improve the accuracy of our predictive model. Although having an MAE of 0.56 is not bad, we still want to improve it, in order to detect the true impact of the conservation easement. To further improve it, we would utilize more information in the dataset, instead of only using ten columns. We would also test out different combinations of the features and find the one that gives us the lowest MAE.

### Packages Using
pandas, numpy, seaborn, matplotlib, math, sklearn, statistics


### Running
Open the file called "CS 506 Property Value Modeling Project Cleaned .ipynb" using Jupyter Note Book

Click "Run All" in Cell Tab in the top

It will show the final result in the last cell


