# DSA210 TMDb Lead Actor Origin Analysis

This project analyzes whether movies with Western and Non-Western lead actors differ in budget, rating, and popularity using the TMDb 5000 Movies and Credits datasets. The notebook also enriches the dataset with lead actor place-of-birth data from the TMDb API, classifies lead actors into Western and Non-Western origin groups, runs exploratory data analysis, performs normality-aware hypothesis tests, and builds simple rating prediction models.

## Files

- `main.ipynb`: Main analysis notebook.
- `tmdb_5000_movies.csv`: Movie-level TMDb dataset.
- `tmdb_5000_credits.csv`: Cast and crew TMDb dataset.
- `DSA210_Proposal.pdf`: Project proposal.
- `requirements.txt`: Python dependencies.

## Setup

Create and activate a project-local virtual environment:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Install the dependencies inside the virtual environment:

```bash
pip install -r requirements.txt
```

Create a `.env` file in the project root and add your TMDb API key:

```env
API_KEY=your_tmdb_api_key_here
```

Then open and run the notebook:

```bash
jupyter notebook main.ipynb
```

## Notes

The notebook uses the TMDb API to enrich actors with `place_of_birth`. If the API call cells are rerun, they may take time because the notebook queries unique lead actors. The API key is loaded from `.env` with `python-dotenv`; `.env` is ignored by git so the key is not committed.

## Research Focus

The main statistical comparisons are:

- Budget differences between Western and Non-Western lead actor origin groups.
- Rating differences between Western and Non-Western lead actor origin groups.
- Popularity differences between Western and Non-Western lead actor origin groups.

Before each group comparison, the notebook checks normality. If both groups appear normally distributed, it uses Welch's independent samples t-test. If normality is violated, it uses the Mann-Whitney U test as a non-parametric alternative.
