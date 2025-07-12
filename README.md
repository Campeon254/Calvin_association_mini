# Calvin_association_mini
A short project demonstrating Association Rules

## Association Rules on Simulated Shopping Data

### Objective
The purpose on this mini-project is to simulate basic transactional data for a grocery store and apply association rule learning `(Apriori Algorithm)` to discover common shopping patterns. This helps in identifying combinations of products that frequently occur together. This is valuable for decision making in product placement, marketing, and sales strategies.

---

### Task:
#### a) Simulating Transaction  Data
* Created 20 fake transactions using random.
* Each transaction consists of 2 to 5 items selected from a pool of 8 unique items:
    ['Milk', 'Bread', 'Beer', 'Diaper', 'Eggs', 'Butter', 'Coffee', 'Cereal', 'Salt']

* The code that created the simulated data:  
![Simulated data code](screenshots/image.png)

* Sample output:  
![Simulated data sample output](screenshots/image-1.png)

---

#### b) Converting data to a One-Hot Encoded data
To achieve this, we used `pandas.get_dammies()` to one-hot encode the transactions.
* The code used to encode the categorical variables:
```python
# One-Hot Encoding using pandas
encoded_df = pd.get_dummies(df)
```

* Sample output:  
![One-hot encoded transactions](screenshots/image-3.png)

The output takes the categorical variables and converts them to numerical variables in preparation for the apriori algorithm

---

#### c) Analyzing with Apriori
We applied the Apriori algorithm using the mlxtend library.

We set the minimum support to 30%, meaning that the itemsets must appear in at least 30% of the transactions to be considered frequent.

``` python
# Applying Apriori Algorithm
frequent_itemsets = apriori(encoded_df, min_support=0.3, use_colnames=True)
```
* Sample output:  
![Apriori algorithm sample output](screenshots/image-4.png)

---

#### d) Generating Association Rule
Finally, we used `association_rules` functions to generate rules based on:
    * **Metric:** Confidence
    * **Minimum Threshold:** 70%

```python
# Generating Association Rules
rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=0.7)
```
In our case, we did not have an association between the products: 
![Apriori rules output screenshot](screenshots/image-5.png)

**Assuming there was an output**

{Bread} => {Beer}

Confidence: 0.75

*Real-life interpretation:*
Customers who purchase Bread are 75% likely to also purchase Beer. This implies a strong association between these items. 

*A grocery store could take advantage of this insight by:*
* Placing Bread and Beer close together on shelves.
* Creating bundle offers or discounts for buying both.

Such strategies can improve the customer shopping experience and increase overall sales.

---

### Setup Instructions

**1) Clone this repository.**
```bash
git clone https://github.com/Campeon254/Calvin_association_mini
cd Calvin_association_mini
```

**2) Install libraries.**
```python
pip install random mlxtend pandas
```

**3) Run the Jupyter file.**
```bash
python Association.ipynb
```
---

### License
This project is licensed under the MIT license - see [LICENSE](https://github.com/Campeon254/Calvin_association_mini/blob/b3d57ed2e84cab2cb1b767821ea06c62379d36c6/LICENSE) for details

