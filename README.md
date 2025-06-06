# EM-Cluster-Analysis
This R project utilizes the Expectation-Maximization (EM) algorithm via mclust for model-based clustering. It fits normal distributions to scaled country data, segmenting it into inherent groups. The process reveals underlying data structures by assigning cluster classifications and calculating means.

EM algorithm: we use the normal distribution method.
#we have 4 normal distribution, to describe our data. 
#we can do the same as k means, you can use all the results if you prnt the means 
#for all different clustters

install.packages("mclust")
library(mclust)

countries_data2_5 <- data.frame(read_excel( "C:/Users/anama/Downloads/Data analytics/unit 1/countries_data2.xlsx"))
rownames(countries_data2_5) <- countries_data2_5$country
countries_data2_5 <- countries_data2_5[, -c(1,2)]
scaled_datamclust <- scale(countries_data2_5)
em_result <- Mclust(scaled_datamclust)
summary(em_result)
# view cluster assignments

print(em_result$classification)

#cluster means (scaled)
print(em_result$parameters$mean)
plot(em_result, what = "classification")
cluster_means <- aggregate(scaled_data, by = list(Cluster = em_result$classification), FUN = mean)
print(cluster_means)


![Rplot](https://github.com/user-attachments/assets/548bcfc0-3c3c-40c5-8961-ad89d705cd6d)


What does it mean and why it is important?

🧠 Why is this important?
 1. Uncover Hidden Patterns
You reveal natural groupings of countries — for example, you might find economic, social, or environmental similarities that aren’t obvious at first glance.

2. Better Decision-Making
Businesses or NGOs can target clusters instead of individual countries — e.g., marketing strategies, policy planning, or resource allocation.

 3. More Flexible than k-means
EM allows for different shapes, sizes, and overlaps of clusters, not just equal-sized ones.


 4. Scalable Insight
This method works great on scaled data, and you can generalize the process to customers, products, behaviors — not just countries.


