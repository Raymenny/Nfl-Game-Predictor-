[README-2.md](https://github.com/user-attachments/files/25463080/README-2.md)
# NFL Game Predictor 🏈

A machine learning model I built that predicts NFL game outcomes. Started as a simple win/loss predictor and turned into something way more complex - multiple ML models, a neural network, SHAP explainability, and a REST API you can actually call.

**[Open in Colab](https://colab.research.google.com/github/Raymenny/Nfl-Game-Predictor-/blob/main/colab.ipynb)**

## What is this?

I wanted to build something that actually used real ML, not just a tutorial project. So I grabbed NFL game data going back to 2010, trained a bunch of different models, compared them, and built a predictor you can use to get win probabilities for any matchup. It even tells you how confident it is.

## Main stuff:
- Predicts win probability for any NFL matchup
- Confidence level - HIGH, MEDIUM, or LOW based on how sure the model is
- Backtested on the full 2024 season (~58% accuracy)
- SHAP values that explain *why* the model made each prediction
- REST API so you can call predictions programmatically
- Interactive dropdown to predict matchups without touching any code

## Models I used
Trained four different models and compared them:
- Logistic Regression (~60% accuracy)
- Random Forest (~58.7%)
- XGBoost (~55.4%)
- Neural Network with TensorFlow (~59%)

Logistic Regression ended up being the most accurate which was surprising - sometimes simpler is better.

## Features the model uses
- Rolling averages for offense and defense over the last 3 games
- Win streak tracking
- Home/away advantage
- Points allowed (defensive performance)

## How to run
Just click the Colab badge above and hit **Runtime → Run all**. Takes about 2-3 minutes to train everything. Scroll to the bottom and use the dropdown to predict any matchup.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Raymenny/Nfl-Game-Predictor-/blob/main/colab.ipynb)

## Stuff that was tricky

**Getting the data:** Pro Football Reference blocks scrapers so I had to find a different source. Ended up using nflverse's public dataset on GitHub which had everything I needed going back to 1999.

**NaN issues:** Rolling averages create NaN values for the first few games of each season since there's no history yet. Had to figure out the right way to drop those without messing up the rest of the data.

**Flask in Colab:** Running a REST API inside a Colab notebook isn't straightforward. Had to use threading to run Flask in the background while still being able to make requests to it from the same notebook.

**Model consistency:** Each time the Colab session resets you lose all your variables. Spent a lot of time figuring out the right order to run everything so it doesn't break.

## What I learned

- How to build and compare multiple ML models on the same dataset
- Feature engineering - creating rolling stats and win streaks from raw game data
- SHAP values for model explainability (AY/A turned out to be the most important feature)
- Cross validation for more honest accuracy testing
- Backtesting a model on a held-out season
- Building a REST API with Flask
- Neural networks with TensorFlow/Keras

## Tech stack
Python, Pandas, Scikit-learn, XGBoost, TensorFlow, Flask, SHAP, Matplotlib

## Future ideas
Stuff I might add:
- Elo rating system (like FiveThirtyEight uses)
- Strength of schedule as a feature
- Playoff performance data
- Deploy the API so it's accessible without Colab
- Add more seasons of training data

## Connect
Ivan Munguia
- LinkedIn: [linkedin.com/in/ivan-munguia-283a96271](https://linkedin.com/in/ivan-munguia-283a96271)
- GitHub: [@Raymenny](https://github.com/Raymenny)

Looking for internships in software development! If you're hiring or know someone who is, let me know.
