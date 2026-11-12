# AI Life Certificate Assistance System 🤖

An educational demonstration web application built with Streamlit, SQLite, and Google Gemini AI. This system simulates the process of submitting, verifying, and managing pensioner life certificates. It features automated local verification, AI-powered rejection explanations, and email/WhatsApp notification capabilities.

## 🌟 Features

* **Interactive Dashboard**: View total pensioners, submissions, and recent certificate activities.
* **Submission & Verification**: Submit a life certificate using a PPO Number, Bank Account, and IFSC code.
* **Automated Email Notifications**: Sends a real email to the pensioner if their certificate is rejected (via Gmail SMTP).
* **WhatsApp Message Generation**: Generates a pre-formatted WhatsApp message preview (and optional clickable link) for easy communication.
* **AI Rejection Explanation**: Uses Google Gemini to analyze rejection reasons and explain them to the pensioner in natural language.
* **AI Pension Chatbot**: A dedicated chatbot powered by Gemini to answer general pension and life certificate questions.
* **Record Management**: View submission history and securely check registered pensioner records.

## 🛠️ Technology Stack

* **Frontend & UI:** [Streamlit](https://streamlit.io/)
* **Database:** SQLite (built-in Python library)
* **Data Handling:** Pandas
* **AI Integration:** Google Generative AI SDK (Gemini)
* **Email Service:** Python `smtplib` and `email.message`
* **Environment Management:** `python-dotenv`

## 📋 Prerequisites

Before running the application, ensure you have the following ready:

* Python 3.8 or higher
* A Google Gemini API Key
* A Gmail account with **2-Step Verification** enabled and an **App Password** generated.

## 🚀 Setup & Installation

**1. Clone or Download the Repository**
Ensure all project files (`app.py`, `database.py`, `verification_service.py`, `email_serv.py`, `requirements.txt`, etc.) are in the same directory.

**2. Install Dependencies**
Open your terminal or command prompt in the project directory and install the required packages using the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

**3. Configure Environment Variables**
Create a new file named exactly `.env` in the root directory of your project. Add the following credentials to the file (do not use quotes or spaces around the `=` sign):

```text
GOOGLE_API_KEY=your_gemini_api_key_here
SENDER_EMAIL=your_email@gmail.com
SENDER_APP_PASSWORD=your_16_letter_google_app_password
```

*(Note: Do not use your standard Gmail password. You must generate a 16-character App Password from your Google Account Security settings).*

**4. Initialize the Database**
To create the SQLite database and populate it with dummy pensioner records, run:

```bash
python seed_data.py
```

*(Depending on your project structure, this might also be handled by running `database.py` directly).*

**5. Run the Application**
Launch the Streamlit app by running:

```bash
streamlit run app.py
```

The application will open automatically in your default web browser at `http://localhost:8501`.

## 💡 How to Test the Email Feature

To test the automated rejection emails:
1. Navigate to **Submit / Resubmit Certificate**.
2. Enter a valid registered PPO (e.g., `PPO202400456`).
3. Enter an *incorrect* bank account number or IFSC code.
4. Click **Submit/Resubmit Life Certificate**.
5. The system will reject the submission and display a **Send email notification** button. Click it to dispatch the email using your `.env` credentials.

## ⚠️ Disclaimer

This is strictly an **educational demonstration**. It is not an official government or banking portal. Local demo verification checks do not constitute official pension approval. Ensure you do not store real, sensitive PII (Personally Identifiable Information) in the local database.