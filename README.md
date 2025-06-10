# 🌤️ Weather & Air Quality ETL Pipeline

---

## 🔎 Project Overview

This project implements an end-to-end **ETL (Extract, Transform, Load)** pipeline to collect, process, and store weather and air quality data for any city and timeframe. It integrates two powerful APIs — VisualCrossing for weather and AirVisual for air quality —  
to deliver clean, enriched datasets stored in PostgreSQL for analysis and reporting.

---

## ⚙️ ETL Pipeline Breakdown

| Step           | Description                                              | Icon             |
|----------------|----------------------------------------------------------|------------------|
| **1. Extract** | Retrieve weather & air quality data from external APIs.  | 📡               |
|                | - Weather (temperature, humidity, wind speed) via VisualCrossing | 🌤️       |
|                | - Air Quality (PM2.5, PM10, AQI) via AirVisual           | 🌫️               |
| **2. Transform** | Clean missing or inconsistent data.                      | 🧹               |
|                | Convert temperature from Kelvin to Celsius                | 🌡️               |
|                | Join weather and air quality datasets by city and date   | 🔗               |
|                | Engineer new features like "Feels Like" temperature and AQI categories | ➕      |
| **3. Load**    | Insert processed data into PostgreSQL tables: weather, air_quality, and combined_data | 🐘  |
| **4. Analyze** | Use the Jupyter notebook for exploratory data analysis and visualization | 📊        |

---

## 📁 Project Structure

```

weather\_air\_quality\_etl/
├── src/
│   ├── extract.py        # API data extraction scripts
│   ├── transform.py      # Data cleaning and feature engineering
│   ├── load.py           # Database insertion logic
│   ├── config.py         # API keys and database credentials management
│   └── utils.py          # Helper functions for ETL
├── sql/
│   └── schema.sql        # SQL schema for database tables
├── notebooks/
│   └── analysis.ipynb    # Jupyter notebook for data exploration
├── requirements.txt      # Python dependencies
├── README.md             # This documentation file
├── LICENSE               # MIT License
└── run\_etl.sh            # Script to run ETL steps sequentially

```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- PostgreSQL database server with user access
- API keys for:
  - [VisualCrossing](https://www.visualcrossing.com/)
  - [AirVisual](https://www.iqair.com/)

### Setup Instructions

1. **Clone the repository**

   ```bash
   git clone https://github.com/username/Weather_Quality_ETL_pipeline.git

2. **Create and activate a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate       # Linux/macOS
   venv\Scripts\activate          # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**

   Create a `.env` file in the project root with your credentials:

   ```ini
   VISUALCROSSING_API_KEY=your_visualcrossing_api_key
   AIRVISUAL_API_KEY=your_airvisual_api_key
   DATABASE_URL=postgresql://username:password@host:port/dbname
   ```

5. **Set up the PostgreSQL database schema**

   ```bash
   psql -U <username> -d <dbname> -f sql/schema.sql
   ```

6. **Run the ETL pipeline**

   You can run the steps individually:

   ```bash
   python src/extract.py
   python src/transform.py
   python src/load.py
   ```

   Or run the entire pipeline at once using the shell script:

   ```bash
   chmod +x run_etl.sh
   ./run_etl.sh
   ```

7. **Explore the data**

   Launch the Jupyter notebook for analysis:

   ```bash
   jupyter notebook notebooks/analysis.ipynb
   ```

---

## 📊 Features & Benefits

* **Comprehensive Data:** Combines weather and air quality data for richer insights
* **Robust Cleaning:** Handles missing values and unit conversions seamlessly
* **Feature Engineering:** Adds "Feels Like" temperature and AQI health categories
* **Scalable Storage:** Structured PostgreSQL tables for efficient querying
* **Analysis Ready:** Includes notebook for exploratory data analysis and visualization

---

## 🛠️ Technologies Used

| Component        | Technology / Library                                         |
| ---------------- | ------------------------------------------------------------ |
| Programming      | Python 3.7+                                                  |
| Database         | PostgreSQL                                                   |
| Weather API      | [VisualCrossing](https://www.visualcrossing.com)             |
| Air Quality API  | [AirVisual](https://www.iqair.com)                           |
| Python Libraries | `requests`, `pandas`, `SQLAlchemy`, `numpy`, `python-dotenv` |
