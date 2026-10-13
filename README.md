<p align="center"><img src="assets/cover-news.png" alt="Inter-Country Relations from the News" width="100%"></p>

# Analysis of Inter-Country Relations Through News Articles

**YTU Computer Engineering research project** · Advisor: **Prof. Dr. Banu Diri**
📄 Paper: [`paper/Inter-Country_Relations_Article.pdf`](paper/Inter-Country_Relations_Article.pdf)

The project models diplomatic relations between countries **automatically, from international news**, and draws them on an interactive world map.

- **8,949** English-language articles from outlets in **11 countries** (CA, CN, DE, FR, IR, IT, JP, RU, TR, UK, US)
- Time span: **June 2025 to April 2026**, collected from **GDELT** through Google BigQuery
- Output: a **0–100 relation score** for each country pair, checked against the independent **Goldstein event scale**

## Pipeline

<p align="center"><img src="assets/diagram-news.png" alt="Collect → scrape & clean → label & featurise → model → relation matrix" width="100%"></p>

## Results

| Model | Accuracy | F1 |
|---|---:|---:|
| Lexicon-based Bag-of-Words (no ML) | 0.710 | 0.661 |
| Random Forest | 0.829 | 0.655 |
| Logistic Regression | 0.864 | 0.753 |
| **Linear SVM** | **0.874** | **0.791** |

<p align="center"><img src="assets/fig52_karsilastirma.png" width="80%" alt="Model comparison"></p>

### Relation matrix (source → target, 0–100)

<p align="center"><img src="assets/fig56_iliski_matrisi.png" width="72%" alt="Relation matrix"></p>

### Interactive map

The final notebook exports an interactive Plotly world map. You pick a source country and see its attitude toward every other country.

<p align="center"><img src="assets/fig57_harita.png" width="90%" alt="Map view: US-based coverage towards other countries"></p>

### Validation and trends

<table>
<tr>
<td width="50%"><img src="assets/fig58_goldstein.png" alt="Goldstein validation"><br><sub>Model sentiment vs. the Goldstein scale: <b>r = 0.645</b> (n = 110 country pairs, p &lt; 0.001)</sub></td>
<td width="50%"><img src="assets/fig61_kuresel_ton.png" alt="Global tone trend"><br><sub>Average news tone across all pairs, month by month</sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/fig42_ulke_cifti.png" alt="Articles per pair"><br><sub>Number of articles per country pair</sub></td>
<td width="50%"><img src="assets/fig53_confusion.png" alt="Confusion matrix"><br><sub>Confusion matrix of the best model</sub></td>
</tr>
</table>

## Stack

`Python` · `pandas` · `NumPy` · `scikit-learn` (TF-IDF, Logistic Regression, Random Forest, LinearSVC, Ridge) · `spaCy` (NER) · `NLTK` (Hu & Liu opinion lexicon) · `newspaper3k` · `Plotly` · `Google BigQuery / GDELT` · `Google Colab`

---

<sub>Figure labels are in Turkish because they come from the original report. Built by <a href="https://github.com/mtaiea">Mustafa Talha Arı</a>.</sub>
