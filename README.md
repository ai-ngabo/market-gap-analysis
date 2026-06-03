## A. Executive Summary

Analysis of 80,000+ food products from the Open Food Facts 
dataset revealed a significant market gap in high-protein, 
low-sugar snack products. Only 1,515 products (1.8%) fall 
into the Optimal health tier, confirming the Blue Ocean 
opportunity. Protein Bars & Supplements lead with an average 
health score of 72.1, while Confectionery sits at the bottom 
at 39.2. The data recommends targeting Meat & Fish or Protein 
Bar formats with 17+g protein and under 10g sugar per 100g.

## B. Project Links

- **Notebook:** [https://colab.research.google.com/drive/1qCGsKBRmwSDZplxDQj3u0BYiC72Ek_va?usp=sharing]
- **Dashboard:** [https://drive.google.com/file/d/1bebiwLdK6KMmvAxYU-z9Qm57jcHVl0i3/view?usp=drive_link]
- **Presentation:** [https://docs.google.com/presentation/d/1_8puIhPuS_QlxhpLqq2FcKFQbPs4jJDojfg5KARLeUw/edit?usp=sharing]

## C. Technical Explanation

### Data Cleaning
- Loaded first 500,000 rows from Open Food Facts CSV
- Dropped rows with null values in product_name, 
  sugars_100g, and proteins_100g
- Filtered out biologically impossible values 
  (nutrients outside 0–100g per 100g range)
- Final clean dataset: ~80,700 products

### Category Wrangling
- Parsed categories_tags comma-separated string
- Mapped keywords to 11 high-level categories using 
  priority-ordered keyword matching
- Categories: Protein Bars & Supplements, Confectionery,
  Dairy & Eggs, Cereals & Grains, Beverages, Bakery & Snacks,
  Legumes & Plant Protein, Nuts & Seeds, Fruits & Vegetables,
  Condiments & Seasonings, Meat & Fish

### Candidate's Choice — Nutritional Health Scoring & ML Clustering
Added a composite Health Score (0–100) modeled after WHO 
dietary guidelines rewarding protein and fiber while 
penalizing sugar and fat. Combined with KMeans clustering 
(k=4) to automatically discover product health tiers:

| Tier | Health Score | Protein | Sugar | Count |
|---|---|---|---|---|
| Tier 1 Optimal | 81.84 | 16.74g | 8.73g | 1,515 |
| Tier 2 Good | 58.59 | 20.37g | 4.72g | 12,771 |
| Tier 3 Moderate | 55.69 | 6.66g | 5.47g | 53,076 |
| Tier 4 Poor | 34.06 | 4.71g | 45.38g | 13,345 |

**Justification:** As an ML engineer focused on healthcare, 
this reframes the market gap as a public health framework;
helping manufacturers not just find the commercial opportunity 
but build products that genuinely improve population nutrition, 
bridging snack labelling to clinical nutrition standards.
