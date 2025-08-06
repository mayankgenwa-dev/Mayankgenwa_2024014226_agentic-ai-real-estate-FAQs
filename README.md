# 🧠 Agentic AI Real Estate Assistant (n8n Workflow)

This project builds an Agentic AI using [n8n](https://n8n.io) to answer real estate FAQs related to **New Jersey**, leveraging multiple local and national datasets.

## 📌 Objective

To create a powerful, location-specific AI assistant that can respond to user questions about the **New Jersey real estate market**, including:

- Property pricing trends
- Local school ratings
- Demographics
- Mortgage rates
- Zoning laws
- Tax data and more

---

## 📂 Data Sources Used

| Type                      | Source |
|---------------------------|--------|
| 🏡 Real Estate Listings   | [Kaggle USA Real Estate](https://www.kaggle.com/datasets/ahmedshahriarsakib/usa-real-estate-dataset) |
| 📈 Zillow Housing Trends  | [Kaggle Zillow Prices](https://www.kaggle.com/datasets/paultimothymooney/zillow-house-price-data) |
| 🧾 Property Records        | [NJ Open Data](https://data.nj.gov/) |
| 💸 Mortgage Rates          | [Federal Reserve Interest Rates (Kaggle)](https://www.kaggle.com/datasets/federalreserve/interest-rates) |
| 👨‍👩‍👧 Demographics           | [US Census](https://data.census.gov/) |
| 🏫 School Info             | [GreatSchools API / NJ Education Data] |
| 🧾 Local Laws              | NJ.gov / Municipal Ordinances |

---

## 🔧 Workflow Architecture (n8n)

### 🛠️ Step-by-step Workflow (No Webhook Required)

1. **Start Node**
   - Trigger manually or via a scheduler

2. **Google Drive Node (Read Multiple CSVs)**
   - Load property pricing data from a folder (NJ-specific)
   - Use **Search / List** + **Download** operations

3. **Extract File (Binary → JSON)**
   - Convert CSVs to JSON using **'Extract File'** or **'Move Binary Data'**

4. **Merge & Transform Data (Code Node)**
   - Combine multiple datasets into a single object using JavaScript

5. **Gemini Node**
   - Send the combined data and user query to Gemini 2.5 flash
   - Prompt it to answer real estate questions contextually

6. **Respond or Save Result**
   - You can send the response to Email, Google Sheets, Telegram, etc.

---

## 🧪 How to Run

1. Install & start n8n via Docker:
   
   docker run -it -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
