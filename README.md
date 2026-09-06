# 🌾 Kisan Dost - AI Agricultural Helpline & Multi-Agent Assistant

**Kisan Dost** is a professional, 24/7 AI-powered agricultural assistant designed specifically for farmers in Punjab, Pakistan. Built using **Streamlit**, **OpenAI/OpenRouter agents**, and **SQLite**, it empowers farmers with real-time agronomic data, weather forecasts, fertilizer calculations, pest diagnosis, market pricing, and government scheme accessibility.

---

## 🚀 Key Features & Capabilities (7 Core Tools)

The application features 7 robust capabilities integrated into specialized multi-agent workflows:

1. **🌦️ Live Weather & Irrigation Advice:** Fetches real-time temperature and humidity using the Open-Meteo free API to provide customized irrigation alerts based on the farmer's district.
2. **🧪 Precision Fertilizer NPK Plan:** Calculates exact requirements and estimated costs in PKR for Urea and DAP fertilizers based on crop type and land size.
3. **🛡️ Pest Doctor & Safe Dosages:** Diagnoses plant diseases and pest infestations (e.g., Whitefly) from symptoms and provides strict pesticide safety limits and dosage guidelines.
4. **📈 Wholesale Mandi Pricing:** Retrieves wholesale market prices and trends for regional crops based on Punjab standards.
5. **💰 Profit & Budget Estimator:** Estimates full-season input costs, expected revenues, and net profit margins per acre.
6. **🏛️ Government Support & Kisan Card:** Connects farmers with government agricultural programs, subsidized fertilizer initiatives, and eligibility details.
7. **🌾 Crop Advisor & Recommendation:** Recommends the best crops based on district, soil type, and seasonal profitability.

---

## 🤖 Core Architectural Highlights & Implementation

### 1. Multi-Agent Architecture & Handoffs
The system uses a sophisticated delegation workflow:
* **Triage Agent:** Acts as the central router that reads the user's prompt, maintains session states, enforces domain restrictions, and dynamically hands off tasks to specialist agents (**Agronomy Specialist**, **Pest Doctor**, and **Market & Finance Specialist**).

### 2. Structured Outputs (Pydantic)
* Replaces loose, unstructured text responses with rigorous **Pydantic models** (`FertilizerPlan`, `WeatherAdvice`, `MandiPriceResponse`, `PestDoctorResponse`, `ProfitPlan`, `CropRecommendation`, `GovtSupportResponse`) ensuring robust type-safety and structured data handling.

### 3. Guardrails & Safety Protocols
* **Domain Guardrails:** Restricts the assistant strictly to agriculture, farming, crops, and rural economic support in Pakistan, gracefully handling and blocking off-topic queries.
* **Pesticide Safety Guardrails:** Ensures chemical treatments, pest controls, and pesticide dosages come with strict safety limits and cautionary intervals.

### 4. Sessions & Context Management
* **SQLite Persistent Storage (`kisan_dost.db`):** Automatically saves and retrieves the active farmer's profile data (Name, District, Land Acres, Primary Crop) across reloads and user interactions, eliminating the need to re-enter information.

### 5. Real APIs & UI/UX Styling
* **Live Open-Meteo Weather API:** Fetches real-time meteorological data dynamically for Pakistani districts without requiring external paid keys.
* **Professional UI/UX:** Styled with custom Streamlit CSS using a professional deep green and agricultural gold palette, responsive multi-column layouts, and interactive progress tracking.

---

## 📊 Datasets & Data Sources
* **Live Meteorological Data:** Open-Meteo free weather API.
* **Agricultural Standards:** Punjab Agriculture Market Information Service (AMIS) metrics for NPK ratios and wholesale market price trends.
* **Local Database:** SQLite embedded file for session state and user profile persistence.

---

## 🔑 API Keys & Environment Configuration
To run and authenticate the AI models, configure your `.env` file:
```env
OPENAI_API_KEY=your_openrouter_or_openai_api_key_here
OPENAI_BASE_URL=[https://openrouter.ai/api/v1](https://openrouter.ai/api/v1)

Project Structure : 

KISAN-DOST/
│
├── venv/                   # Python virtual environment
├── .env                    # Environment variables (API keys and configurations)
├── .gitignore              # Git ignore file
├── pyvenv.cfg              # Virtual environment configuration
├── app.py                  # Main Streamlit user interface application
├── main.py                 # Core agent logic and backend execution handler
├── kisan_dost.db           # SQLite database for persistent farmer profiles
├── requirements.txt        # Project python dependencies
└── README.md               # Project documentation

⚙️ Setup and Installation
Clone the repository and navigate to the project folder.

Install the required dependencies:

Bash
pip install -r requirements.txt
Create your .env file and add your API credentials.

Run the application via Streamlit:

Bash
streamlit run app.py 