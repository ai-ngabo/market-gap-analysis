## A. Executive Summary

Analysis of 80,707 food products from the Open Food Facts dataset 
revealed a significant market gap in high-protein, low-sugar snack 
products. Only 1,515 products (1.8%) fall into the Optimal health 
tier, confirming a clear Blue Ocean opportunity in the snack aisle. 
Protein Bars & Supplements lead with an average health score of 72.1, 
while Confectionery sits at the bottom at 39.2. The data recommends 
targeting Meat & Fish with products exceeding 20.0g of protein 
and under 3.4g of sugar per 100g.

## B. Project Links

- **Notebook:** [https://colab.research.google.com/drive/1qCGsKBRmwSDZplxDQj3u0BYiC72Ek_va?usp=sharing]
- **Dashboard:** [https://nutrient-sugar-gapgit-fhhqwpnw9ewfwhgxtdm33r.streamlit.app/]
- **Presentation:** [https://docs.google.com/presentation/d/1_8puIhPuS_QlxhpLqq2FcKFQbPs4jJDojfg5KARLeUw/edit?usp=sharing]
- **Demo Video** [https://youtu.be/A_3kyrHVCm0]

## C. Technical Explanation

### Data Cleaning
- Loaded the first 500,000 rows from the Open Food Facts CSV dataset
- Dropped all rows with null values in `product_name`, `sugars_100g`,
  and `proteins_100g` — the three columns critical to the analysis
- Filtered out biologically impossible values by keeping only products
  where all nutrient columns fall within 0–100g per 100g
- Final clean dataset: 80,707 products across 11 named categories

### Category Wrangling
- Parsed the `categories_tags` comma-separated string column
- Mapped keywords to 11 high-level categories using a priority-ordered
  keyword matching function
- Categories created: Protein Bars & Supplements, Confectionery,
  Dairy & Eggs, Cereals & Grains, Beverages, Bakery & Snacks,
  Legumes & Plant Protein, Nuts & Seeds, Fruits & Vegetables,
  Condiments & Seasonings, Meat & Fish
- Products not matching any category were labelled "Other" and
  excluded from the dashboard visualizations

### Candidate's Choice — Nutritional Health Scoring & ML Clustering
Added a composite Health Score (0–100) modeled after WHO dietary
guidelines, rewarding protein and fiber while penalizing sugar and
fat. Combined with KMeans clustering (k=4) to automatically discover
product health tiers from the data:

| Tier | Health Score | Avg Protein | Avg Sugar | Products |
|---|---|---|---|---|
| Tier 1 — Optimal | 81.84 | 16.74g | 8.73g | 1,515 |
| Tier 2 — Good | 58.59 | 20.37g | 4.72g | 12,771 |
| Tier 3 — Moderate | 55.69 | 6.66g | 5.47g | 53,076 |
| Tier 4 — Poor | 34.06 | 4.71g | 45.38g | 13,345 |

**Justification:** As an ML engineer focused on healthcare, this
addition reframes the market gap as a public health framework.
A snack manufacturer can use the health tiers to benchmark any
new product against data-driven nutritional standards before R&D
investment — bridging the gap between commercial opportunity and
genuine population health impact.

---

# Project Brief: The "Sugar Trap" Market Gap Analysis

**Client:** Helix CPG Partners (Strategic Food & Beverage Consultancy)

**Deliverable:** Interactive Dashboard, Code Notebook & Insight Presentation

---
  Prepared by Alain Ishimwe Ngabo @2026
