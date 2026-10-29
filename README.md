# ecommerce_customer_segmentation_case_study
Project Overview
This machine learning case study segments e-commerce customers based on their purchasing behaviour. It uses RFM analysis, K-Means, and DBSCAN, then visualizes the resulting segments with PCA and t-SNE. The final step turns the customer groups into practical marketing personas.
Objectives
- Explore and check the customer dataset.
- Build customer-level RFM features: Recency, Frequency, and Monetary value.
- Transform and standardize the features before clustering.
- Select a K-Means cluster count using the elbow method and sampled silhouette scores.
- Compare K-Means with DBSCAN, including DBSCAN noise points and parameter sensitivity.
- Visualize clusters with PCA and t-SNE.
- Create customer personas and suggested marketing actions.
Files
- MLE_Case_Study.ipynb — the Jupyter notebook containing the analysis and code.
- E-commerce_Customer_Segmentation_2026.csv — the input dataset expected by the notebook. Add this dataset separately; it is not embedded in the notebook.
Dataset note: This notebook expects a customer-level CSV with 50,000 customers and columns such as customer_id, days_since_last_purchase, total_purchases, and total_spent_usd. It also uses fields such as dataset_year, satisfaction_score, preferred_category_1, shopping_channel, and loyalty_tier for data checks and persona interpretation. It does not directly use the transaction-level online_retail_II.xlsx workbook unless you adapt the notebook and rebuild the required columns.

Techniques Used
RFM Analysis
- Recency: Days since the customer's most recent purchase. Lower is more recent.
- Frequency: Number of purchases. Higher generally indicates more frequent shopping.
- Monetary: Total customer spending. Higher indicates greater spending.
Clustering
- K-Means: Creates a selected number of customer groups. The notebook compares candidate values of K and uses the best sampled silhouette score as a guide.
- DBSCAN: Groups dense regions and marks isolated customers as noise (-1). Its output depends on eps and min_samples.
Dimensionality Reduction
- PCA: Projects the RFM features into two principal components for a 2D view and reports the variance explained.
- t-SNE: Creates a 2D visualization of a customer sample to inspect local grouping patterns. Its axes are not directly interpretable as business measures.
Libraries
- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
Google Colab usually includes these libraries. If running locally, install any missing packages:
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
How to Run in Google Colab
1. Upload MLE_Case_Study.ipynb to Google Colab.
2. Upload E-commerce_Customer_Segmentation_2026.csv to the Colab session, or place it in Google Drive.
3. In the notebook section “2. Load Data”, replace the existing local computer path:
   file_path = r'/Users/farhan/Downloads/E-commerce_Customer_Segmentation_2026.csv'
   df = pd.read_csv(file_path)
   with the Colab upload workflow:
   from google.colab import files
   uploaded = files.upload()
   file_path = next(iter(uploaded))
   df = pd.read_csv(file_path)
4. Run the notebook cells from top to bottom.
5. Review the cluster profiles, visualizations, DBSCAN sensitivity results, and marketing persona table.
Workflow
1. Import libraries.
2. Load and inspect the dataset.
3. Check shape, duplicates, unique customers, missing values, and dataset year.
4. Select the raw RFM measures.
5. Explore RFM distributions.
6. Apply log1p and standard scaling.
7. Compare K-Means cluster counts using inertia and silhouette scores.
8. Fit the final K-Means model and profile each cluster.
9. Visualize K-Means clusters with PCA and t-SNE.
10. Tune and run DBSCAN, inspect noise points, and compare parameter settings.
11. Build marketing personas using cluster-level RFM summaries and customer attributes.
12. Summarize the results and suggested actions.
Marketing Personas
The notebook assigns persona labels based on the median RFM profiles of the K-Means clusters. Suggested labels include:
- Champions — reward loyalty, VIP access, and referral incentives.
- At-Risk Loyal Customers — personalized win-back messages and loyalty reminders.
- High-Value Occasional Customers — premium or complementary product recommendations.
- Active Emerging Customers — discovery content and second-purchase incentives.
- Reactivation Candidates — low-cost reactivation messages.
The actual persona assigned to each cluster depends on the computed profile; cluster numbers do not have a fixed business meaning.
Important Interpretation Notes
- RFM clustering is an unsupervised learning task; classification accuracy is not an appropriate evaluation metric here.
- Scaling is important because Recency, Frequency, and Monetary use different ranges.
- K-Means requires choosing K and can be affected by outliers.
- DBSCAN can identify noise points, but its results may change significantly with eps and min_samples.
- PCA and t-SNE are visualization tools; they do not prove that a marketing strategy will succeed.
- Treat suggested actions as hypotheses and evaluate campaigns using experiments such as A/B tests.
Expected Outputs
- Data quality checks and RFM summary statistics.
- RFM distribution charts.
- Elbow and silhouette plots for K-Means.
- K-Means cluster sizes and profile table.
- PCA and t-SNE visualizations.
- DBSCAN cluster counts, noise percentage, and sensitivity table.
- Marketing persona table with suggested actions.
Conclusion
This project demonstrates how customer transaction behaviour can be summarized with RFM, segmented using K-Means and DBSCAN, visualized with PCA and t-SNE, and translated into actionable marketing ideas. The most useful segmentation is the one that is both statistically reasonable and understandable enough to support a clear business decision.
