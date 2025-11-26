
# 🧹 Automated Job Market ETL Pipeline

**"Because cleaning data manually is boring."**

This project is a Python-based **ETL (Extract, Transform, Load)** pipeline. It simulates fetching raw job postings, cleaning the messy data (inconsistent salaries, dates, text), and loading it into a structured SQL database for analysis.

---

## 🚀 How it Works

The pipeline performs three automated steps:

1.  **EXTRACT (API/Simulation):** Fetches raw job data. Includes a fail-safe simulation mode to generate realistic test data without burning API credits.
2.  **TRANSFORM (Pandas):**
    * **Salaries:** Converts strings like `"$85k"` or `"120,000"` into pure integers (`85000`, `120000`).
    * **Dates:** Standardizes various date formats into `YYYY-MM-DD`.
    * **Logic:** Auto-tags roles as **"Senior"**, **"Mid"**, or **"Entry"** based on keywords in the job title.
3.  **LOAD (SQLite):** Saves the clean data into a local `linkedin_jobs.db` database.

---

## 📊 The "Before vs. After" Transformation

Here is what the script actually does to the data:

| Feature | ❌ Raw Input (Messy) | ✅ Pipeline Output (Clean) |
| :--- | :--- | :--- |
| **Salary** | `"$85k - $90k"` | `85000.0` (Float) |
| **Date** | `"Oct 3rd, 2023"` | `"2023-10-03"` (ISO Format) |
| **Title** | `"senior data ANALYST"` | `"Senior Data Analyst"` |
| **Level** | *(Column didn't exist)* | `"Senior"` (Derived) |

---

## 🛠️ Tech Stack

* **Python 3.x**
* **Pandas** (Data Cleaning & Manipulation)
* **SQLite3** (Database Storage)
* **Requests** (API Handling)

---

## 💻 How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/job-etl-pipeline.git](https://github.com/your-username/job-etl-pipeline.git)
    ```

2.  **Install required libraries:**
    ```bash
    pip install pandas requests
    ```

3.  **Run the script:**
    ```bash
    python main.py
    ```

4.  **Check the output:**
    The script will print a preview of the clean data and create a file named `linkedin_jobs.db`.

---

## 📈 Future Improvements
* Connect to a live Visualization tool (PowerBI/Tableau).
* Automate the script to run daily using Airflow or Cron.
* Add email alerts if data extraction fails.

---

*Created by [Your Name]*
