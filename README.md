# NHS Data Science & ETL Pipeline

University of York, *DATA: Introduction to Data Science* coursework (2024/25), by Jesly Prosper.

Six raw NHS operational datasets (appointments, billing, insurance, prescriptions, surgery and test records) are designed into a relational schema (ER diagram in Chen's notation), normalised to 3NF, and loaded into SQLite: 556,692 appointments, 400,000 patients, 252 hospitals and 3,143 departments. The database is then analysed three ways.

## Results

The data has no `No-Show` status. Appointments are `Completed` (450,595), `Cancelled` (50,235) or `Scheduled` (55,862), so cancellation is used as the missed-appointment outcome.

| Analysis | Method | Finding |
| --- | --- | --- |
| Inferential statistics | Chi-square tests + Cramér's V | 10.0% of appointments were cancelled. Age, gender, weekday, hour, department and hospital are **not** associated with cancellation (all p > 0.2, V < 0.03). |
| Supervised learning | Logistic regression (one-hot, class-weighted) | ROC-AUC 0.50: the available attributes cannot predict cancellations. This is reported as-is rather than tuned into a misleading score. |
| Unsupervised learning | K-means, k chosen by silhouette (k = 3, 0.66) | 2% of patients (6,337) average 13 appointments each and make up about 15% of all appointments, a high-utiliser group suited to care coordination. |

The notebook also covers the ethics of these models in an NHS setting and SQL reporting on hospitals, departments and patient preferences.

## Files

| File | Contents |
| --- | --- |
| `DATA Assessment 2024-25.ipynb` | The full analysis, with outputs |
| `DATA Assessment 2024-25.html` | The same notebook, viewable without Jupyter |
| `Diagrams.png` | ER diagram |
| `Data coruse work.pdf` | Exported write-up |

## Running it

1. Install Python 3 and: `pip install pandas scikit-learn scipy matplotlib seaborn jupyter`
2. Put the SQLite database `NHSDBB.DB` (2.3 GB, not committed because of its size) in this folder.
3. Open the notebook with `jupyter notebook` and run all cells.
