# SEB-Task

Short recap regarding https://data.gov.lv/dati/lv/dataset/gada-parskatu-finansu-dati

As there were not much space for time-series analysis I focused on analyzing company financial structure and identifying potential company profiles.

Why this matters:

PCA analysis develop clusters with similar financial structures (in our example), which are dynamic and only exist stable in a relation to other given data. This is useful for a further market dynamic assessment as 'changes in type of company segment' or transitions between company segments over time. Additionally, it could be used as a predictive feature for freshly added company to the dataset. its proximity to existing clusters provides early insight into potential future behavior.

For example, a company may appear healthy today (positive profits and sufficient liquidity) but closely resemble structurally weaker firms — such as those with high leverage, heavy dependence on short-term liabilities, and thin operating margins. Even if current performance is strong, such a structure increases vulnerability to shocks, making the company more likely to experience future financial distress.

The Test

Merged financial statements into one dataset

Converted raw numbers into ratios and shares to remove size effects (normalized by turnover, bs as share of total cap)

Kept only informative, scale-free features (cost structure, profitability, leverage, asset mix) ; compared with ratios

Filtered out reports with too much missing data and capped extreme values

Used PCA to compress financial information into a few key dimensions

Applied clustering (K Mean, tried others, but no significant difference, better data clearing and preparation would make the difference) to group companies with similar financial profiles

Got ‘profiles’ for companies

Result (metrics could be seen after running the code)

Clusters 0 and 5 represent financially stable firms with strong liquidity or collateral and are generally safer from a bank’s perspective Clusters 1 and 2 show elevated risk due to high leverage, inventory or receivables exposure, and sensitivity to operational or demand shocks Cluster 3 consists of distressed, loss-making companies with weak debt service capacity and a high probability of default Cluster 4 contains abnormal or unreliable reporters whose financial ratios are distorted and unsuitable for automated credit assessment

I also run correlational map. Most of the columns are not indpendent and therefore strongly linearly related. Attempt to use data from PCA cluster was no better, should have been starting point but contains to much noise, but data sould be carefully cleaned by hand beforehand. Forest would also require more supervised approach, and therefore data cleaning (idially, creating actual mathematical realtion between related values like COGS & expanses for example. dbscan returned noisier data compared to PCA.
