# 🥗 MacroSnap

**MacroSnap** is an AI-powered nutrition tracking assistant that helps users quickly understand the calories and macronutrients in their meals.

Instead of manually searching for nutritional information or maintaining a food diary, users can simply **upload a photo of their meal or describe what they are eating**. MacroSnap uses **Google Gemini** to identify the meal and provide estimated calories, protein, carbohydrates, and fat.

Users can also send a **summary of all meals discussed during the session directly to their WhatsApp** using Twilio.

## ✨ Features

### 📸 Analyze Meal Photos

Upload a JPG, JPEG, or PNG photo of your meal.

MacroSnap uses Google Gemini's vision capabilities to analyze the image and provide:

* What the meal appears to be
* Estimated calories
* Estimated protein
* Estimated carbohydrates
* Estimated fat

### 💬 Describe Food Using Text

Users don't need a photo.

They can simply type what they are eating, for example:

```text
2 chapatis with chicken curry and a bowl of rice
```

MacroSnap analyzes the description and provides an estimated nutritional breakdown.

### 🤖 AI Nutrition Assistant

MacroSnap uses Google Gemini as a conversational nutrition assistant.

It remembers the meals discussed during the current chat session, allowing the user to ask questions and add multiple meals.

The AI is specifically instructed to focus on:

* Food
* Nutrition
* Meals
* Fitness-related questions

### 📊 Track Multiple Meals

Users can discuss multiple meals during the same session.

For example:

```text
Breakfast → 2 eggs and toast

Lunch → Chicken biryani

Snack → Banana

Dinner → Chapati and chicken curry
```

MacroSnap can then combine the meals into a single summary.

### 📱 WhatsApp Daily Summary

The **Send to WhatsApp** feature generates a summary of the meals discussed during the session.

The summary includes:

* Each meal
* Estimated calories for each meal
* Total calories
* Total protein
* Total carbohydrates
* Total fat

The summary is then sent to the user's WhatsApp number using **Twilio WhatsApp messaging**.

### 👤 Simple Onboarding

When the application starts, the user enters:

* Name
* WhatsApp number with country code

Example:

```text
Name: Fawaz
WhatsApp: +91XXXXXXXXXX
```

The application then creates a personalized MacroSnap chat session.

## 🔄 How MacroSnap Works

```text
        User
          │
          ▼
  Enter Name & WhatsApp
          │
          ▼
     MacroSnap App
       (Streamlit)
          │
          ▼
  Upload Meal Photo
       OR
  Describe Meal
          │
          ▼
    Google Gemini
          │
          ▼
  Meal Identification
          │
          ▼
 Calories + Protein
 Carbohydrates + Fat
          │
          ▼
   Continue Adding
       Meals
          │
          ▼
 "Send to WhatsApp"
          │
          ▼
   Generate Summary
          │
          ▼
       Twilio
          │
          ▼
    📱 WhatsApp
```

## 🛠️ Technology Stack

| Technology           | Purpose                                 |
| -------------------- | --------------------------------------- |
| **Python**           | Application development                 |
| **Streamlit**        | Web application interface               |
| **Google Gemini**    | AI-powered meal and nutrition analysis  |
| **Google GenAI SDK** | Communication with Gemini               |
| **Twilio**           | WhatsApp messaging                      |
| **Git & GitHub**     | Version control and source code hosting |

## 📁 Project Structure

```text
MacroSnap/
│
├── .streamlit/
│   └── secrets.toml
│
├── app.py
├── prompts.py
├── requirements.txt
├── .gitignore
└── README.md
```

### `app.py`

Contains the main Streamlit application, Gemini integration, chat interface, meal image processing, and Twilio WhatsApp functionality.

### `prompts.py`

Contains the AI instructions used by MacroSnap, including:

* Nutrition assistant system prompt
* Welcome message
* WhatsApp summary prompt

### `requirements.txt`

Contains the Python dependencies required by the application.

## 📦 Requirements

The project uses:

```text
google-genai
streamlit
twilio
```

You also need:

* Python 3.10 or later
* Google Gemini API key
* Twilio account
* Twilio WhatsApp configuration

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/fawazfaisalvp2003-ui/macrosnap.git
cd macrosnap
```

### 2. Create a virtual environment

On Windows:

```powershell
python -m venv venv
```

### 3. Activate the virtual environment

```powershell
.\venv\Scripts\Activate.ps1
```

If PowerShell prevents activation, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then:

```powershell
.\venv\Scripts\Activate.ps1
```

### 4. Install dependencies

```powershell
pip install -r requirements.txt
```

## 🔐 Configuration

MacroSnap requires Google Gemini and Twilio credentials.

Create:

```text
.streamlit/secrets.toml
```

Add the required credentials:

```toml
GEMINI_API_KEY = "your_gemini_api_key"

TWILIO_ACCOUNT_SID = "your_twilio_account_sid"
TWILIO_AUTH_TOKEN = "your_twilio_auth_token"
TWILIO_WHATSAPP_FROM = "your_twilio_whatsapp_sender"
TWILIO_CONTENT_SID = "your_twilio_content_sid"
```

**Never commit `secrets.toml` to GitHub.**

The `.gitignore` file should contain:

```text
.streamlit/secrets.toml
venv/
__pycache__/
*.pyc
```

## ▶️ Run the Application

After activating the virtual environment:

```powershell
python -m streamlit run app.py
```

The application will normally open at:

```text
http://localhost:8501
```

## 📱 WhatsApp Integration

MacroSnap uses Twilio to send the nutrition summary to the user's WhatsApp number.

When the user clicks:

```text
📤 Send to WhatsApp
```

MacroSnap:

1. Collects the meals discussed in the conversation.
2. Asks Gemini to create a combined nutrition summary.
3. Calculates a running summary of calories and macros based on the AI's estimates.
4. Formats the result for WhatsApp.
5. Sends the message using Twilio.

## 🧠 AI Nutrition Analysis

For each meal, MacroSnap asks Gemini to provide:

1. The meal or food identified.
2. Estimated calories.
3. Estimated protein.
4. Estimated carbohydrates.
5. Estimated fat.

Nutrition values are **estimates**, particularly when they are calculated from a photograph. Actual nutritional values can vary depending on ingredients, portion sizes, preparation methods, and other factors.

## 🔒 Security

Never publish API keys, authentication tokens, or other credentials in the GitHub repository.

Store credentials in:

```text
.streamlit/secrets.toml
```

and keep that file excluded using `.gitignore`.

## 🌐 Deployment

MacroSnap can be deployed using **Streamlit Community Cloud**.

When deploying, configure the required secrets in the deployment settings rather than uploading `secrets.toml` to GitHub.

The Streamlit entry point is:

```text
app.py
```

## 🔗 Repository

GitHub:

https://github.com/fawazfaisalvp2003-ui/macrosnap

## 👨‍💻 Author

**Fawaz Faisal**

MacroSnap was developed as an AI-powered nutrition assistant combining computer vision, conversational AI, and WhatsApp messaging into a simple user experience.
