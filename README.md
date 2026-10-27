# NHS Data Science & ETL Pipeline

University of York, *DATA: Introduction to Data Science* coursework (2024/25), by Jesly Prosper.

Six raw NHS operational datasets (appointments, billing, insurance, prescriptions, surgery and test records) are designed into a relational schema (ER diagram in Chen's notation), normalised, and loaded into SQLite. The database is then analysed three ways:

| Analysis | Method | Question |
| --- | --- | --- |
| Inferential statistics | Chi-square test of independence | Are age group, gender or hospital associated with appointment no-shows? |
| Supervised learning | Logistic regression (class-weighted) | Can a no-show be predicted from patient and appointment details? |
| Unsupervised learning | K-means clustering | Which groups of patients use services in similar ways? |

The notebook also covers the ethics of these models in an NHS setting and SQL reporting on hospitals, departments and patient preferences.

## Files

| File | Contents |
| --- | --- |
| `DATA Assessment 2024-25.ipynb` | The full analysis |
| `Diagrams.png` | ER diagram |
| `Data coruse work.pdf` | Exported write-up |

## Running it

1. Install Python 3 and: `pip install pandas scikit-learn scipy matplotlib seaborn jupyter`
2. Put the SQLite database `NHSDBB.DB` in this folder. It is not committed because of its size.
3. Open the notebook with `jupyter notebook` and run all cells.

Each analysis cell prints the raw appointment status labels first. If the no-show label in your data is not recognised, add it to the `NO_SHOW` set at the top of that cell.
