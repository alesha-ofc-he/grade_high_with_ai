# Advanced LLM Telegram Bot

# Made by Mertay Merekeyev, Alikhan Kassymbekov from group IT-2307 

This Telegram bot is designed for exam preparation, integrating LangChain and Ollama to generate answers, summaries, tasks, and quizzes. The bot includes additional features such as:

- **Document Processing:** Accepts files (PDF, DOCX, TXT, JPEG, PNG) and extracts text from them.
- **Summary Generation:** Creates a brief summary of the material and provides recommendations for better learning.
- **Task Generation:** Generates assignments based on the uploaded material.
- **Quiz Generation:** When selecting the "Quiz" command, the bot generates a quiz session with 10 questions. Once the questions are exhausted, the session ends, and a new batch of questions requires pressing the "Quiz" button again.
- **Answering Questions:** Any text that does not match commands is considered a question about the material, and the bot generates an answer.
- **Memory:** Saves uploaded materials and query history both in RAM (via the `user_data` dictionary) and as files.
- **Callback Functionality:** An inline keyboard for quizzes (with a "Next Quiz" button) allows switching between questions.
- **Filtering:** If prohibited words (e.g., "badword1") are detected, the bot notifies the administrator via Telegram.

## Requirements

- Python 3.9+
- Telegram Bot Token (obtained via [BotFather](https://t.me/BotFather))
- Telegram Admin Chat ID (for notifications)

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/advanced-llm-telegram-bot.git
   cd advanced-llm-telegram-bot
   ```

2. **Create and activate a virtual environment:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # on Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:** Either edit the `main.py` file, replacing the lines with `YOUR_TELEGRAM_BOT_TOKEN` and `YOUR_ADMIN_CHAT_ID` with actual values, or create a `.env` file.

5. **Install Tesseract:**

   - **Ubuntu:**
     ```bash
     sudo apt update && sudo apt install tesseract-ocr
     ```
   - **macOS:**
     ```bash
     brew install tesseract
     ```
   - **Windows:**
     Download and install Tesseract from the [official repository](https://github.com/tesseract-ocr/tesseract).

## Running the Bot

Start the bot with the following command:

```bash
python main.py
```

## How the Bot Works

1. **Start:**
   Send the `/start` command in Telegram. The bot will send instructions and display the main menu (reply keyboard).

2. **Uploading a Document:**
   Send a document (PDF, DOCX, TXT, JPEG, PNG). The bot will extract and save the text.

3. **Summary:**
   Press the **Summary** button – the bot will generate a brief summary of the material along with recommendations, displaying them in parts.

4. **Task:**
   Press the **Task** button – the bot will generate an assignment based on the material.

5. **Quiz:**

   - Press the **Quiz** button – the bot will generate a new quiz session with 10 questions and save them.
   - The first question will be sent as a poll with an inline keyboard.
   - By pressing the **Next Quiz** button, the bot will provide the next question from the saved session.
   - After 10 questions, the quiz session ends.

6. **Asking a Question:**
   Send text that does not match any commands – the bot will treat it as a question and generate an answer using the uploaded material.

7. **Material:**
   Press **Material** – the bot will show instructions for uploading a document.

8. **Stop:**
   Press **Stop** to cancel the current operation.

## Possible Improvements

- Integration with a database for long-term storage of history and materials.
- Expanding LangChain chains functionality for multi-step reasoning.
- Enhancing logging and error handling.
- Allowing switching between a local LLM and a remote API call for speed optimization.

