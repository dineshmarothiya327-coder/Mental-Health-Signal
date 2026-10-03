# Mental Health Signal

A student wellness analytics app that estimates a mental health score from reported habits. The prediction is informational only and is not a clinical assessment.

## Project files

- `index.html`, `style.css`, `script.js` — plain HTML, CSS, and JavaScript frontend.
- `main.py` — FastAPI prediction API.
- `Mental_Health_Model.pkl` — trained scikit-learn model loaded by the API.
- `requirements.txt` — Python dependencies.
- `Student Social Media And Mental Health Impact.csv` and `ML_Project.ipynb` — source data and model exploration.
- `ML Project.html` — project build guide; it is separate from the prediction UI.

## Run locally

Python 3.10 or newer is recommended. From the project directory, create an environment and install dependencies:

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Start the API in one terminal:

```sh
.venv/bin/uvicorn main:app --host 127.0.0.1 --port 8001
```

Start a static server from the project directory in another terminal:

```sh
python3 -m http.server 8000
```

Open <http://localhost:8000/>. The frontend currently posts predictions to `http://127.0.0.1:8001/predict`. The API docs are at <http://127.0.0.1:8001/docs>. Keep the API URL in `script.js` aligned with the port used by Uvicorn.

If you prefer to open `index.html` directly, the frontend currently targets a localhost API; run the backend and serve the page over HTTP for the most reliable browser behavior.

## Prediction input

The API accepts JSON at `POST /predict`. Required fields are `age`, `gender`, `country`, `academic_level`, `most_used_platform`, `purpose_of_use`, `avg_daily_usage_hours`, `daily_unlocks`, `study_hours`, `physical_activity_hours`, `sleep_hours_per_night`, and `stress_level`. Successful responses contain `predicted_mental_health_score`. Input ranges and allowed categories are defined in `main.py`.

## Notes

The serialized model was created with scikit-learn 1.9.0. Using a different scikit-learn version may produce an `InconsistentVersionWarning`; use the version that created the model if you encounter model compatibility issues. The page requires a network connection to load its Google Fonts.
# Mental-Health-Signal
