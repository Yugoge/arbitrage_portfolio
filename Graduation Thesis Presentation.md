# Graduation Thesis Presentation

# Model Section

Good [morning/afternoon/evening], everyone. Today, I'll present our refined approach to constructing arbitrage portfolios, building upon the methodology developed by Kim, Korajczyk, and Neuhierl.

Our model starts with the assumption that asset returns \( R \) follow a K-factor model:

$$
R = \alpha 1_T' + B F' + E
$$
Here, \( \alpha \) represents abnormal returns, and \( B \) represents factor loadings. Both \( \alpha \) and \( B \) are linear functions of firm-specific characteristics \( X \):

$$
\alpha = G_\alpha (X) + \Gamma_\alpha 
B = G_\beta (X) + \Gamma_\beta
$$
We treat \( \alpha \) and \( \beta \) as orthogonal components, where \( \alpha \) averages to zero. This allows us to remove the impact of \( \alpha \) by demeaning \( R \), leading to:

$$
R_{JT} \approx (G_\beta (X) + \Gamma_\beta) F' J_T + E_{JT}
$$
Ignoring the error term, we can approximate \( R \) as:

$$
\hat{R} \approx P R_{JT} \approx G_\beta (X) F' J_T
$$
Next, we compute the product \( \hat{R} \hat{R}' \), which is similar to a covariance matrix:

$$
\hat{R} \hat{R}' \approx G_\beta (X) F' J_T F G_\beta' (X)
$$
Using characteristic root decomposition, we estimate \( G_\beta (X) \).

For alpha estimation, we leverage the orthogonality between \( G_\alpha (X) \) and \( G_\beta (X) \). We use two methods:

1. **Method 1:**  
   $$
   G_\beta (X) \perp G_\alpha (X), \quad \hat{\theta} = \arg \min (\hat{R} - X \theta)' (\hat{R} - X \theta)
   $$
   
   
2. **Method 2:**  
   $$
   \bar{R} - G_\alpha (X) \bar{F} = G_\alpha (X) + (\Gamma_\alpha + \Gamma_\beta + \bar{E})
   $$
   

Finally, we calculate the arbitrage portfolio weights \( \omega \) as:

$$
\omega = \frac{1}{N} G_\alpha (X)
$$
This approach helps us isolate and utilize the abnormal returns driven by firm characteristics, constructing a robust arbitrage portfolio.

# Methodology Section

Our study begins with data collection from sources such as iFinD, CRSP, and Compustat, covering March 31, 2016, to January 31, 2024. We focus on firm characteristics that predict stock returns, ensuring a diverse market representation.

For the estimation period, we clean the dataset, addressing missing values and outliers. To estimate factor loadings, we use rolling estimation periods of 3 to 48 months, projecting demeaned returns onto firm characteristics.

In terms of cross-section, we focus on 6,369 US stocks and consider 35 firm-specific characteristics to predict stock returns. The data is standardized using the following transformation: 
$$
\text{Transformed}(x_i) = \frac{\text{Rank}(x_i) + 1}{|g_i| + 1}
$$
To ensure the comparability across different parameters, we implement an investment restriction, limiting our analysis to 2,000 stocks at any given time.  Our margin requirements are 50% for long positions and 150% for short positions. 

Principal Component Analysis (PCA) helps extract primary systematic factors driving stock returns, identifying factor loadings accurately. This robust method ensures our model reflects the relationship between characteristics and systematic risk.

**Tensor projection challenge:**  
$$
(N \times T) \times L, \quad (N \times T) \times 1
$$
We address the tensor projection challenge by managing the dimensionality of our data matrices, ensuring accurate and efficient processing.

Finally, we construct arbitrage portfolios using estimated alpha and factor loading functions. Weights are proportional to estimated alphas, aiming to maximize returns by exploiting mispricing.

# Findings Section

Our findings reveal several key insights:

1. **Estimation Horizons and Investment Periods:**
   - An 18-month estimation horizon with a 3-month investment period generated substantial but volatile returns.
   - A 48-month horizon with a 1-month investment period showed significant alpha, especially with lagged financial characteristics.

2. The heatmap on the left shows the significant characteristics contributing to beta, such as market value and PS TTM, indicating their influence on systematic risk. The heatmap on the right highlights the significant characteristics contributing to alpha, including EPS basic and operating profit to revenue, emphasizing their role in predicting abnormal returns. We conclude that there is significant divergence and between beta factor and alpha factors.
3. **Sector-Specific Performance:**
   - The energy sector showed high returns due to predictable demand and long-term contracts.
   - The REITS sector underperformed, likely due to interest rate sensitivity and regulatory influences.
   - In entertainment and media, beta-driven investments showed limited returns, while alpha-driven investments achieved higher gains.

4. **Practical Considerations:**
   - Accounting for transaction costs and practical investment constraints is crucial for translating theoretical models into actionable strategies.

Overall, our study demonstrates the potential of characteristic-based arbitrage portfolios to generate significant abnormal returns, though ongoing refinement is necessary to account for market dynamics and practical constraints.





Thank you for your attention. I'll be happy to take any questions you might have.