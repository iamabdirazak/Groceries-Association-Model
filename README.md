# Groceries Association Model

## Overview

This project implements an association rule mining pipeline on a groceries dataset. The goal is to extract frequent itemsets and generate association rules that reveal relationships between purchased items. These insights can be used for product recommendation and market basket analysis.

The dataset contains transaction data representing items purchased together. The code processes the data, cleans and filters items, mines frequent itemsets using the Apriori algorithm, generates association rules, evaluates them, and provides visualization and recommendation functions.

---

## Features

- Flexible loading and parsing of transaction data in different CSV formats
- Data cleaning and normalization of item names
- Filtering low-frequency items and removing sparse transactions
- Apriori algorithm implementation for frequent itemset mining
- Association rule generation with support, confidence, and lift metrics
- Evaluation of rules on a train/test split
- Recommendation function based on mined rules
- Visualizations: scatter plots, network graphs, and lift heatmaps
- Export of frequent itemsets and association rules to CSV

---

## Data Loading & Preprocessing

- Supports single-column CSV where each row is a comma-separated list of items (one transaction per row).
- Supports multi-column CSV with transaction IDs, customer IDs, and item description columns.
- Normalizes item names (lowercase, strip, replace special characters).
- Removes rare items (appear fewer than 3 times) and transactions with fewer than 2 items.
- Final cleaned transaction list is used for mining.

---

## Mining Frequent Itemsets

- Implements Apriori algorithm with configurable minimum support (default 1%).
- Extracts frequent itemsets of increasing size until no more meet support threshold.

---

## Generating Association Rules

- Rules generated from frequent itemsets with configurable minimum confidence (default 20%).
- Calculates support, confidence, and lift for each rule.
- Rules are sorted by lift to highlight strong associations.

---

## Evaluation

- Data split into train/test sets (80%/20%).
- Rules mined on training data.
- Precision of top-1 predicted consequent evaluated on test data.

---

## Recommendations

- Function to recommend items based on basket contents using mined rules.
- Recommendations scored by lift, confidence, and support product.

---

## Visualizations

- Scatter plot of rules showing support vs confidence, colored by lift.
- Network graph of top association rules (requires `networkx`).
- Pairwise lift heatmap for top frequent items.

---

## Usage

1. Place your groceries CSV dataset in `data/groceries.csv`.
2. Run the preprocessing and mining script to parse transactions, clean data, and mine frequent itemsets.
3. Generate association rules and evaluate their performance.
4. Use `recommend_for_basket(basket, rules)` to get product recommendations.
5. Visualize rules and item relationships with provided plots.
6. Export frequent itemsets and rules to CSV files for further analysis.

---

## Outputs

- `frequent_itemsets.csv` — list of frequent itemsets with support values.
- `association_rules.csv` — all generated association rules.
- `top_association_rules.csv` — top 50 rules sorted by lift.

---

## Requirements

- Python 3.x
- pandas
- matplotlib
- networkx (optional, for network graph visualization)
- numpy

---

## Example

```python
basket = ["whole milk", "brown bread"]
recommendations = recommend_for_basket(basket, rules)
print("Recommendations:", recommendations)

---

## Author
-
Abdirazak Mubarak

## Date
-
Aug 12, 2025
```
