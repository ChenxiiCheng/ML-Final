Data process

As we know, the data acquired online usually have many null values,  so it's necessary to preprocess the data so that the final prediction will have a better performance. Measures are as listed:

1. Eliminate  the whole data row if there is any null value exist,
2. Replace the null value with the mean value of a certain feature.

Analyse 
Since there are more than 10k samples in the original data, it would not hurt the whole integrality if the incomplete data is less than 5%,  however, if there are too many samples to be eliminated, then the second measure will be better for it can suit the major part of data except for some outliers and it won't cause problems for reducing the sample size.

We selected the first one because of its perfect data integrality.


However, after the preliminary data process, a problem still exists. Some of the samples with extreme feature values, are too rare in the graph to consider as the training sample, but still affect the whole prediction, so it is necessary to eliminate these outliers and then to train these sample. The specific removal method is shown below.


![1557527862772](C:\Users\wzsca\AppData\Roaming\Typora\typora-user-images\1557527862772.png)

As the price is most significant, we detected some outliers in 'Price',  remove them, and then train the data again and again until we find the best outlier_step, which decides the range of removal.
After removing these outliers, we obtained a better prediction, with 4% improvement, compared with the first beginning. 





Besides, there are so many features we need to consider, which may not be that relevant, so we thought it should have a better performance if we remove certain less relevant features, and pay more attention to those main influential features.
Then we tried to remove the last 2 features,'sqft_lot' and 'condition' according to the heatmap. To our surprise, even though it has low relation to the price, after removing these 2 features, we didn't get what we want, the final R2_score is a little bit lower than before. So we kept our old way.



![1557529787305](C:\Users\wzsca\AppData\Roaming\Typora\typora-user-images\1557529787305.png)



Cost performance evaluation

One of the meaning to do this project, since people all would like to buy a cost-effective house, it 's necessary to evaluate the house price according to the model, then we built a CP function,
as long as input the basic features, then compare the predicted price with the actual price, it will tell you the cost performance 
with a specific value. In the future, with more data acquired and modify the model, we would get a more accurate evaluation.

![1557529004517](C:\Users\wzsca\AppData\Roaming\Typora\typora-user-images\1557529004517.png)





