# 🎲 Board Game Recommender

Content-based recommender for ~30,000 board games from BoardGameGeek, with an interactive Streamlit app.

**How it works.** Each game's mechanics and categories (for example *Hand Management*, *Tile Placement*,
*Economic*) are one-hot encoded with scikit-learn's `MultiLabelBinarizer`. Recommendations rank candidates by

```
score = 0.50 × cosine similarity of tags + 0.30 × normalized rating + 0.20 × complexity match
```

Similarities are computed on demand for one game at a time instead of as a full game × game matrix,
which keeps memory use low (the full matrix would take several GB).

**App pages:**
- **Find Similar:** pick a game and get similar games within a complexity tolerance.
- **Conceptual Search:** no starting game needed; pick the mechanics and constraints you want.
- **Compare Games:** similarity score plus radar and tag-weight charts for two games.
- **Statistics:** complexity vs rating correlation and other dataset statistics.

The `Dataset*.py` modules load, check, clean, handle outliers in, and save the raw BoardGameGeek data
before it reaches the recommender.

**Stack:** Python, pandas, NumPy, scikit-learn, Streamlit, Matplotlib, seaborn.

**Run:**
```bash
pip install -r requirements.txt
streamlit run app.py
```

Course project, MSc Data Science (USFQ).
