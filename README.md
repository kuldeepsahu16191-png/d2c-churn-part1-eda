# d2c-churn-part1-eda

D2C Customer Churn Intelligence - Part 1: Data Audit, EDA & Business UnderstandingProject OverviewThis repository contains Part 1 of the Capstone Project for the D2C personal-care brand. The primary objective of this phase is to thoroughly audit the raw transactional and master datasets, conduct exploratory data analysis (EDA) to map out customer behavior patterns, establish evidence-backed churn hypotheses, and formulate core business safeguards before launching any retention campaigns.  Repository StructureThis repository is self-contained and independently runnable using the following structure:
├── eda_audit.ipynb             # Core Python notebook containing data loading, cleaning, and EDA
├── data_quality_report.md      # Formal document outlining data anomalies and treatment plans
├── business_memo.md            # Strategic business memo outlining investigative steps
├── requirements.txt            # Python environment dependencies
└── README.md                   # Setup and execution instructions (this file)  
Dataset InventoryThe analysis utilizes the following files from the provided dataset package:  customers.csv - Customer master profile records.orders.csv - Historical transaction data.
support_tickets.csv - Customer support interactions and statuses.web_events_snapshot.csv - Digital app/web platform interactions.churn_labels.csv - Ground-truth target labels for modeling evaluation.intervention_history.csv - Historical record of past marketing retention campaigns.

DATA_DICTIONARY.md - Schema and snapshot date constraints.

🛡️ Data Leakage Guardrail: As instructed, all data points with timestamps occurring after the specified snapshot date have been strictly filtered out and are completely excluded from feature building.  Generated Artifacts & VisualizationsRunning the analysis script exports 6 mandatory, meaningful charts directly into the workspace root folder:  chart1_churn_distribution.png - Breakdown of the target churn label distribution.  chart2_spend_distribution.png - Histogram showing customer lifetime monetary spend patterns.  chart3_tickets_vs_churn.png - Boxplot comparing support ticket frequency across churn cohorts.  chart4_events_vs_churn.png - Boxplot mapping digital platform interaction volume against customer state.  chart5_recency_distribution.png - Histogram of days elapsed since a customer's last order.  chart6_correlation_matrix.png - Comprehensive inter-correlation matrix across all extracted behavioral features.  
