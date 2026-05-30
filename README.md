# DataEngineeringProject

A Python-based ETL (Extract, Transform, Load) pipeline framework for structured data engineering workflows.

## Project Overview

This project provides a modular ETL pipeline architecture for ingesting raw data, applying transformations, and loading processed results to a target destination. It is designed to be extended with custom extraction, transformation, and loading logic.

## Features

- Modular ETL architecture with clearly separated concerns
- Environment-based configuration via `.env` file
- Structured data directories for raw and processed data
- Extensible database integration layer

## Project Structure

```
DataEngineeringProject/
├── config/
│   └── .env                  # Environment variables (DATA_PATH, credentials)
├── data/
│   ├── raw/                  # Input/source data
│   └── processed/            # Output/processed data
├── src/
│   ├── db/                   # Database connection and schema modules
│   └── ETL/
│       ├── extract/          # Data extraction logic
│       ├── transform/        # Data transformation logic
│       └── load/             # Data loading logic
├── main.py                   # Application entry point
├── requirements.txt          # Python dependencies
└── .gitignore
```

## Prerequisites

- Python 3.12+
- pip

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Mosshato/DataEngineeringProject.git
   cd DataEngineeringProject
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv .venv

   # Windows (PowerShell)
   .\.venv\Scripts\Activate.ps1

   # Windows (CMD)
   .venv\Scripts\activate.bat

   # macOS / Linux
   source .venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Configuration

Edit `config/.env` and set the required environment variables:

```env
DATA_PATH=/path/to/your/data/directory
```

| Variable    | Description                              | Required |
|-------------|------------------------------------------|----------|
| `DATA_PATH` | Path to the directory containing raw data | Yes      |

> **Note:** The `.env` file is excluded from version control. Never commit secrets or credentials.

## Usage

Run the ETL pipeline:

```bash
python main.py
```

The pipeline will:
1. Read `DATA_PATH` from environment variables
2. **Extract** data from the specified path
3. **Transform** the extracted data
4. **Load** the processed data to the destination

## Architecture

```
data/raw/
    │
    ▼
[ Extract ]  ──  src/ETL/extract/
    │
    ▼
[ Transform ] ── src/ETL/transform/
    │
    ▼
[ Load ]     ──  src/ETL/load/
    │
    ▼
data/processed/
```

Each stage is implemented as an independent module under `src/ETL/`, making it straightforward to swap or extend individual steps without affecting the rest of the pipeline.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m "Add my feature"`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

## License

This project is open source. See the repository for license details.
