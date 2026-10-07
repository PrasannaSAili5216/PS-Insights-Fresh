


|Deploy Page|
<img width="1918" height="865" alt="deploy page" src="https://github.com/user-attachments/assets/4c5cb817-3890-4fc9-9448-90a446464292" />


# 🔒 Privacy-Safe Cross-Company Data Insights

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red)
![Status](https://img.shields.io/badge/Status-Prototype-green)

> **Sensitive data warning:** The app now generates synthetic data in memory and does not load the customer CSV files. Treat those existing CSVs as sensitive. This repository is not ready for public deployment or pushing to a remote until the data files and Git history have been reviewed and handled under your organization's data-security process.

A synthetic-data prototype exploring cross-company analytics. It is not a production privacy-preserving clean room.

**Use Case:** Financial Fraud Detection (AI for Good)

## 🚀 Key Features

- **Demo matching**: Local set intersections over generated IDs; this is not cryptographic PSI.
- **Demo noise**: Laplace noise helper for prototyping; there is no persistent privacy-budget accounting or production DP release policy.
- **Cortex AI Analyst (Simulated)**: Natural language interface for querying insights.
- **Role-based demo views**: UI selection only; not authentication or server-enforced authorization.

## 🛠️ Tech Stack

- **Frontend**: Streamlit
- **Privacy Logic**: Python (NumPy, Pandas)
- **Testing**: Pytest

## �️ Governance & Data Credential Handling

This workspace contains a governance prototype, not an enforced clean-room security boundary:

- The app uses generated in-memory demo data; do not connect real customer data to this app.
- Matching is local prototype logic and does not provide cryptographic protection.
- Roles in `src/governance.py` demonstrate policy rules but do not authenticate users or enforce tenant isolation.
- The supported roles are `BANK`, `INSURER`, `BROKERAGE`, and `ADMIN`.
- Sensitive credential values must stay in a local secret store or environment variables, not in the repository.

Recommended credential pattern:

- Store real credentials in a local `.env` file or a secure secret manager.
- Keep the repo safe by committing only placeholder values.
- Never store production passwords, tokens, or database connection strings in Git.

Example environment keys for each data source:

```env
BANK_DATA_SOURCE_URL=
BANK_DB_USERNAME=
BANK_DB_PASSWORD=
INSURER_DATA_SOURCE_URL=
INSURER_DB_USERNAME=
INSURER_DB_PASSWORD=
BROKERAGE_DATA_SOURCE_URL=
BROKERAGE_DB_USERNAME=
BROKERAGE_DB_PASSWORD=
```

The project does not ship with real credentials. A secure secret store alone does not make this prototype suitable for processing real customer data.

## �📦 Installation

1. Clone the repository.
2. Install dependencies:
   ```bash
   py -m pip install -r requirements.txt
   ```

## 🏃‍♂️ Running the App

Start the dashboard with automatic port fallback:
```bash
py run_app.py
```

The default URL is `http://localhost:8504`. If port 8504 is already in use, the launcher picks the next available port and prints the URL to open.

## 🧪 Testing

Run unit tests to verify privacy guarantees and fraud logic:
```bash
py -m pytest
```

## 📚 Project Structure

- `src/app.py`: Main dashboard application.
- `src/data_gen.py`: Generates synthetic fraud data.
- `src/fraud_analysis.py`: Demo overlap analysis and simulated analyst responses.
- `src/privacy.py`: Core differential privacy functions.
- `tests/`: Unit and smoke tests.
