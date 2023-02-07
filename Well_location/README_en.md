Let's say we work for the mining company GlavRosGosNeft. We need to decide where to drill a new well.

We were provided with oil samples in three regions: in each 10,000 fields, where we measured the quality of oil and the volume of its reserves. We will build a machine learning model that will help determine the region where mining will bring the greatest profit. Let's analyze the possible profit and risks using the *Bootstrap.* technique

Steps to choose a location:

- In the selected region, they are looking for deposits, for each, the values of the signs are determined;
- Build a model and estimate the volume of reserves;
- Select the deposits with the highest value estimates. The number of fields depends on the company's budget and the cost of developing one well;
- The profit is equal to the total profit of the selected deposits.

Project conclusions:
1. The linear regression model for the second region proved to be ideal. But the value of the metric R2 is equal to one only in one case, if the MSE is zero. This model predicts all responses perfectly. This never happens - this means that all the predictions on the training data coincided with the validation ones. Those. predictions have zero error. Zero error can only be in the absence of a probable character. Most likely, a strong correlation of f2 features to the stock for this region influenced. Therefore, it is necessary to clarify the correctness of the data for the region. The data will not be used correctly.
2. In each region there is a share of break-even wells, they are of most interest to us. The least break-even wells are in the second region, the average volume of raw materials for the break-even development of new wells is 111.11 thousand bar.
3. The most attractive for the development of deposits is the First region, with a projected profit of 3.32 billion rubles
4. the level of risk is less than critical (2.5%), only the Second region was able to make a profit. Where there is a 95% chance to make a profit of more than 0.43 billion rubles. The risk of becoming unprofitable is only 0.7%
5. If the data of the second region is correct, we select it as the only one that satisfies the conditions of the problem. However, you can pay attention. that the factor f2 has a great influence on the amount of reserves.