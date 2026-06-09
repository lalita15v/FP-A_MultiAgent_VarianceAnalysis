

# FP&A Multi‑Agent Variance Analysis Pipeline

A LangGraph‑powered, multi‑agent FP&A automation system that performs end‑to‑end financial analysis, KPI computation, variance reporting, and CFO‑style commentary generation.

This project simulates a real FP&A workflow using:
- Multi‑agent reasoning (CFO agent, Reviewer agent)
- Automated KPI + variance engine
- Commentary generation
- Excel + text output exports
- Clean CLI interface
- Modular LangGraph node architecture

---

## 1. Project Overview

This system takes raw financial data (Actuals + Budget), applies filters such as:
- Region  
- Year  
- Quarter  
- Custom periods  

…and produces:
- Revenue, Expenses, Profit, Margin  
- Variance vs Budget  
- Prior‑year comparisons  
- CFO‑style commentary  
- Reviewed commentary  
- Exported Excel files  
- Exported text commentary  
- Optional charts and board‑pack outputs

The pipeline is fully automated and runs end‑to‑end from a single command.

---

## 2. How to Run

From the project root:

python main.py --region APAC --year 2024 --quarter Q1 --periods Jan,Feb


Supported arguments:
- `--region` (e.g., APAC, EMEA, AMER)
- `--year` (e.g., 2023, 2024)
- `--quarter` (Q1, Q2, Q3, Q4)
- `--periods` (comma‑separated months)

Example:

python main.py --region EMEA --year 2023



---

## 3. Project Architecture

FP&A_MultiAgent_VarianceAnalysis/
│
├── main.py
├── graph_fpna.py
├── dashboard.py
├── pdf_generator.py
├── generate_tb_data.py
├── tempfile2.py
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── financials.csv
│   └── TB_Data.txt
│
├── output/
│   ├── commentary.txt
│   ├── kpis.xlsx
│   ├── variance_table.xlsx
│   ├── board_pack.pdf
│   └── variance_output.xlsx
│
├── charts/
│   ├── gl_drivers.png
│   ├── regions.png
│   ├── waterfall.png
│   └── yoy.png
│
├── exports/
│   ├── excel/
│   ├── powerbi/
│   └── streamlit/
│
├── notebooks/
│   └── placeholder02.txt
│
├── src/
│   ├── agents/
│   │   ├── init.py
│   │   ├── cfo_commentary.py
│   │   ├── hitl.py
│   │   └── reviewer.py
│   │
│   ├── nodes/
│   │   ├── init.py
│   │   ├── commentary_node.py
│   │   ├── export_node.py
│   │   ├── kpi_node.py
│   │   ├── load_data_node.py
│   │   └── review_node.py
│   │
│   └── utils/
│       ├── init.py
│       ├── config.py
│       └── state.py
│
└── venv/



---

## 4. LangGraph Node Architecture

### **load_data_node.py**
Loads financial data from `/data/financials.csv` into the pipeline state.

### **kpi_node.py**
Applies filters and computes:
- Revenue  
- Expenses  
- Profit  
- Margin  
- Variance vs Budget  
- Prior‑year comparisons  

### **commentary_node.py**
Generates CFO‑style narrative commentary based on KPI results.

### **review_node.py**
Reviewer agent refines and validates the commentary.

### **export_node.py**
Exports:
- KPIs → Excel  
- Variance table → Excel  
- Commentary → text file  

---

## 5. Outputs

All outputs are saved to:

/output/



Files include:
- `kpis.xlsx`  
- `variance_table.xlsx`  
- `commentary.txt`  
- `board_pack.pdf`  
- `variance_output.xlsx`  

---

## 6. Data Requirements

The system expects a CSV with columns:

- Year  
- Month  
- Region  
- Data Type (Actual / Budget)  
- Account Node  
- Amount  

Example rows:

2024, Jan, APAC, Actual, Income, 128080
2024, Jan, APAC, Budget, Income, 120000



---

## 7. Example Run Output

[INFO] Starting LangGraph FP&A pipeline...
[INFO] Loading financial data...
[INFO] Computing KPIs and variances...
[INFO] Applying region filter: APAC
[INFO] Applying year filter: 2024
[INFO] Filtered rows: 84
[INFO] Generating CFO commentary...
[INFO] Reviewing commentary...
[INFO] Exporting outputs...
[INFO] FP&A pipeline completed.



---

## 8. Future Enhancements (Optional)

- Forecasting module  
- Scenario analysis  
- Streamlit dashboard  
- n8n automation  
- LangGraph Cloud deployment  

---

## 9. License

MIT License (or add your preferred license)