# CryptoClustering

For this challenge, I've used my knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.


## Step 1: Import Data

- Import required libraries and dependencies
- Load the data into a Pandas DataFrame
- Display sample data
- Generate summary statistics
- Plot the data to see what's in your DataFrame





## Step 2: Prepare the Data

- Use the `StandardScaler()` module from scikit-learn to normalize the data from the CSV file.
- Create a DataFrame with the scaled data
- Set the coinid column as index
- Display sample data




## Step 3 : Find the Best Value for k Using the Original Data

For finding the best value for k using the original data, I've used the Elbow Curve method. Steps taken are as follows:

- Create a list with the number of k-values from 1 to 11
- Create a for loop to compute the inertia with each possible value of k and Append the model.inertia_ to the inertia list
- Create a dictionary with the data to plot the Elbow curve
- Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

The Elbow Curve indicates that the best value for k is 4.





## Step 4: Cluster Cryptocurrencies with K-means Using the Original Data

For this step, I've used the K-Means modem to cluster Cryptocurrencies using the original data

- Initialize the K-Means model using the best value for k
- Fit the K-Means model using the scaled data
- Predict the clusters to group the cryptocurrencies using the scaled data
- Print the resulting array of cluster values.
- Add a new column to the DataFrame with the predicted clusters
- Create a scatter plot using hvPlot by:

    - setting `x="price_change_percentage_24h"` and `y="price_change_percentage_7d"`
    - Color the graph points with the labels found using K-Means and 
    - add the crypto name in the `hover_cols` parameter to identify the cryptocurrency represented by each data point.





## Step 5: Optimize Clusters with Principal Component Analysis

Following are the steps for optimizing clusters with Principal Component Analysis

- Create a PCA model instance and set `n_components=3
- Use the PCA model with `fit_transform` to reduce to three principal components
- Retrieve the explained variance to determine how much information can be attributed to each principal component.

    - Approximately 89.5% of the total variance is explained of the 3 PCA variables.

- Create a new DataFrame with the PCA data.
- Set the coinid column as index



## Step 6: Find the Best Value for k Using the PCA Data

I've used the elbow method on the PCA data to find the best value for k using the following steps:

- Create a list with the number of k-values from 1 to 11.
- Create an empty list to store the inertia values.
- Create a for loop to compute the inertia with each possible value of k.
- Create a dictionary with the data to plot the Elbow curve.
- Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

The best value for k when using the PCA data can be identified as 4 as shown in the elbow curve below. This is similar to the best k value found using the original data.




## Step 7: Cluster Cryptocurrencies with K-means Using the PCA Data

To cluster the cryptocurrencies for the best value for k on the PCA data:

- Initialize the K-means model with the best value for k.
- Fit the K-means model using the PCA data.
- Predict the clusters to group the cryptocurrencies using the PCA data.
- Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
- Create a scatter plot using hvPlot:

    - Set the x-axis as "PC1" and the y-axis as "PC2".
    - Color the graph points with the labels found using K-means.
    - Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.




## Step 8: Visualize and Compare the Results

The results are visualized and compared by completing the following steps:

- Create a composite plot by using hvPlot and the plus sign (+) operator to compare the elbow curve created from the original data with the one created from the PCA data.

- Create a composite plot by using hvPlot and the plus (+) operator to compare the cryptocurrency clusters that resulted from using the original data with those that resulted from the PCA data.


**Question:** After visually analyzing the cluster analysis results, what is the impact of using fewer features to cluster the data using K-Means?

  * **Answer:** The elbow curves for both techniques are similar and both indicates that the optimal value for k, the number of clusters is probably 4. However, by visually analyzing the cluster anaysis results, it appears that the impact of using fewer features to cluster the data using K-Means(with PCA), we get a better representation of the data and can indentify the four clusters in a clear manner. Optimizing clusters using PCA data compared to using the original data, provides relatively better visualization and understanding of the data, specially the third cluster as it can be clearly identified as a seperate cluster. 










