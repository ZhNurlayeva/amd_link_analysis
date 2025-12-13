# amd_link_analysis
# PageRank-Based Book Recommendation Networks  
### Amazon Books Review Dataset

**Author:** Zhanat Nurlayeva
**Programme:** Master in Data Science for Economics  
**Course:** Algorithms for Massive Data  
**University:** Università degli Studi di Milano  
**Academic Year:** 2024–2025  

---

## Project Overview

This project applies **link analysis techniques** to the Amazon Books Reviews dataset to study how books are connected through shared readership.  
Books are modeled as nodes in a graph, with edges representing **co-review relationships** between titles reviewed by the same users.

The objective is to identify **structurally influential books** using **PageRank** and to compare network-based importance with traditional popularity indicators such as review counts and ratings.

---

## Dataset

- **Source:** Amazon Books Reviews dataset (Kaggle, CC0 license)  
- **Nodes:** Books  
- **Edges:** Shared reviewers (co-review graph)  
- **Preprocessing:**  
  - Canonicalisation and deduplication of book titles  
  - Removal of isolated nodes  
  - Analysis restricted to the **Largest Connected Component (LCC)**  

---

## Methodology

### Graph Construction
- Books are connected if they share a minimum number of reviewers.
- **LSH-based candidate generation** is used to avoid \(O(n^2)\) comparisons.
- Final edges are added only after **exact reviewer overlap verification**.

### Centrality Measures
The following metrics are computed:
- **PageRank** (prestige / global influence)
- **Degree centrality** (connectivity)
- **Closeness centrality** (reachability)
- **Betweenness centrality** (bridge roles)

Each metric captures a different dimension of influence in the network.

### Temporal PageRank
A **temporal extension of PageRank** is implemented using exponential decay on review timestamps, assigning more weight to recent activity.  
This allows separation between:
- **Timeless structural hubs**, and  
- **Books with current momentum**.

### Community Detection
- Communities are detected using **Louvain clustering**.
- Each community is labelled by its **dominant genre**.
- PageRank mass distribution across communities is analysed.

---

## Results

- PageRank is strongly correlated with degree, confirming its structural nature.
- Correlation with review count is weak, and with ratings is negligible.
- Network importance differs from popularity and perceived quality.
- Temporal PageRank highlights recent trends invisible to static rankings.

---

## Limitations

- Analysis is limited to the Largest Connected Component.
- Edge weights are binary and do not capture connection strength.
- Temporal dynamics are modelled in aggregate.
- Some title deduplication errors may persist.

---

## Conclusion

Link analysis provides a richer perspective on book influence than traditional metrics alone.  
By modelling books as nodes connected through shared readership, the project identifies influential titles that act as connectors between reader communities and reveals how a small subset of books shapes global navigation behaviour.

---

## Repository Structure

