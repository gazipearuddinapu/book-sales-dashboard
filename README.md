# 📚 Book Sales Dashboard

An end-to-end data analysis project on book sales data across three independent datasets (DATA1, DATA2, DATA3).  
Results are presented in an interactive BI-style dashboard hosted on GitHub Pages.

🔗 **[View Dashboard →](https://YOUR-USERNAME.github.io/book-sales-dashboard/)**

---

## Overview

Each dataset contains three files:
- `users.csv` — customer records (name, email, phone, address)
- `orders.parquet` — purchase transactions (book, quantity, price, timestamp)
- `books.yaml` — book catalogue (title, author, year)

The notebook cleans and analyses all three datasets independently and produces the following metrics for each:

| # | Metric |
|---|--------|
| 1 | **Top 5 days by revenue** |
| 2 | **Number of unique real users** (after identity reconciliation) |
| 3 | **Number of unique author sets** |
| 4 | **Most popular author / author set** (by copies sold) |
| 5 | **Top customer** (all associated user IDs listed) |
| 6 | **Daily revenue line chart** |

---

## Key Findings

| Metric | DATA1 | DATA2 | DATA3 |
|---|---|---|---|
| Unique users | 3,115 | 2,663 | 3,290 |
| Unique author sets | 325 | 293 | 268 |
| Top author(s) | Arlinda Huel | Hershel Treutel, Miss Modesto Denesik, Sen. Trula Bosco | Coy Streich, Keeley Hand, Lela Emard |
| Best buyer ID(s) | [44650] | [54419] | [50855] |
| Peak revenue day | 2024-12-05 ($42,218) | 2025-09-02 ($33,683) | 2025-01-29 ($47,343) |

---

## Notable Data Challenges

- **Messy prices** — formats like `€50¢50`, `22$75¢`, `USD 45.99`; all normalised to USD (`€1 = $1.20`)
- **Messy timestamps** — separators varied (spaces, semicolons, commas); parsed with `dateutil`
- **Duplicate users** — same person may appear with a different address, phone, or name alias; reconciled with Union-Find on shared email or phone
- **Co-authored books** — author field may contain comma-separated names; treated as an unordered set for grouping

---

## Stack

| Layer | Library |
|---|---|
| Data loading | `pandas`, `pyarrow`, `pyyaml` |
| Cleaning & parsing | `re`, `dateutil` |
| Analysis | `pandas` |
| Visualisation (notebook) | `matplotlib` |
| Dashboard | Vanilla HTML / CSS / JS |

---

## Repository Structure

```
.
├── task4_analysis.ipynb        # Main analysis notebook
├── index.html                  # BI dashboard (GitHub Pages)
├── daily_revenue_DATA1.png
├── daily_revenue_DATA2.png
├── daily_revenue_DATA3.png
└── README.md
```

---

## Running the Notebook

```bash
pip install pandas pyarrow pyyaml python-dateutil matplotlib
jupyter notebook task4_analysis.ipynb
```

Place your data under a `data/` directory with the structure:

```
data/
├── DATA1/
│   ├── users.csv
│   ├── orders.parquet
│   └── books.yaml
├── DATA2/
│   └── ...
└── DATA3/
    └── ...
```
