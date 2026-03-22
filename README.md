
# Steam Game Analysis

This project explores what makes a Steam game “good” by analyzing review quality, pricing model, and popularity using a Steam dataset collected from the SteamSpy API.

The project focuses on three main questions:

1. How should we define the “best” game on Steam?
2. Do paid games receive better reviews than free games?
3. Are highly rated games also more popular?

---

## Dataset

- **Source**: Kaggle
- **Dataset**: Steam Games Dataset (SteamSpy API)

The dataset includes information such as:

- game name
- positive reviews
- negative reviews
- price
- current concurrent users (CCU)
- playtime statistics

---

## Project Structure

```bash
steam-data-analysis/
├── data/
│   └── steam_games_dataset.csv
├── analysis.ipynb
├── README.md
├── .gitignore
└── .gitattributes
````

---

## Methods

### 1. Positive Ratio

I first calculated a basic review score:

I first calculated a basic review score:

positive ratio = positive reviews / (positive reviews + negative reviews)

This gives a simple measure of review quality, but it may be misleading for games with very few reviews.

### 2. Bayesian-Adjusted Score

To reduce small-sample bias, I used a Bayesian-style adjusted score. This method combines each game’s review performance with the global average review level, making the ranking more reliable.

This helps avoid situations where a little-known game with only a small number of reviews appears unrealistically at the top of the ranking.

### 3. Group Comparisons

I compared different groups of games based on:

* **pricing model**: Free vs Paid
* **popularity level**: grouped by CCU (Low / Medium / High)

---

## Analysis Sections

### 1. Naive Ranking vs Bayesian Ranking

A simple ranking based only on positive ratio tends to favor games with limited review counts.

After applying a Bayesian-adjusted score, the ranking becomes more reliable and highlights games that are both highly rated and supported by a large number of reviews.

### 2. Free vs Paid Games

I compared free and paid games using both average and median values of:

* positive ratio
* Bayesian score

To improve reliability, I filtered out games with very low review counts.

**Finding:** Paid games generally achieved higher ratings than free games, although pricing alone is not the only factor affecting review quality.

### 3. Quality vs Popularity

I grouped games by CCU level and compared their review performance.

**Finding:** Games with higher popularity generally also have higher ratings. However, the improvement becomes much smaller from medium-popularity games to high-popularity games, suggesting that popularity and quality are related but not identical.

---

## Key Findings

* Raw positive ratio alone is not enough to identify the “best” game, because low-review games can be overrated.
* Bayesian-adjusted ranking provides a more reliable way to identify highly recommended games.
* Paid games tend to receive stronger user approval than free games overall.
* More popular games usually have better ratings, but extremely high popularity does not necessarily imply much higher quality.

---

## Tools Used

* Python
* pandas
* Jupyter Notebook
* VS Code

---

## Possible Future Improvements

There are several ways this project could be extended in the future:

* analyze playtime and engagement
* study the effect of discounts on popularity
* build simple recommendation rules based on rating and activity
* add visualizations for clearer comparisons

---

## Author

Jiarui Zhang