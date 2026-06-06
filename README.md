# Team Portfolio & Project Request System

## Overview

This project is a simple demonstration web application built with Flask that showcases a team portfolio and allows potential clients to submit project requests through a contact form.

When a user submits a project request:

1. The request is validated using Flask-WTF.
2. The information is stored in a SQLite database.
3. A Telegram bot periodically checks for new submissions.
4. New requests are automatically forwarded to a Telegram group for the team to review and start working on the project.

This project demonstrates the integration of:

* Flask web framework
* SQLite database
* Flask-WTF form validation
* Telegram Bot API
* Scheduled background tasks

---

## Features

* Team introduction website
* Contact / project submission form
* Input validation and sanitization
* SQLite database storage
* CSRF protection
* Automatic Telegram notifications
* Background scheduler for message delivery


---

## Technologies Used

* Python 3
* Flask
* Flask-WTF
* WTForms
* SQLite3
* python-telegram-bot
* Schedule

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/project-name.git
cd project-name
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate the environment:

**Windows**

```bash
venv\Scripts\activate
```

**Linux / macOS**

```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Configuration

Create a `config.py` file and add:

```python
APP_SECRET_KEY = "your_secret_key"

BOT_TOKEN = "your_telegram_bot_token"

CHAT_ID = "your_group_chat_id"

DB_FILE_PATH = "database.db"

DEBUG = True
```

---

## Running the Application

Start the Flask application:

```bash
python app.py
```

Start the Telegram notification service:

```bash
python telegram_bot.py
```

Open:

```text
http://127.0.0.1:5000
```

---

## Database Schema

The application stores contact requests in a SQLite table:

```sql
CREATE TABLE contacts (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL,
    phone TEXT NOT NULL,
    message TEXT NOT NULL,
    sent INTEGER
);
```

---

## Workflow

1. Visitor opens the website.
2. Visitor submits project information.
3. Data is validated.
4. Request is stored in SQLite.
5. Telegram scheduler checks for unsent requests every 30 seconds.
6. Request is sent to the Telegram group.
7. Record is marked as sent.

---

## Security Features

* CSRF protection using Flask-WTF
* Input validation
* Parameterized SQL queries to prevent SQL injection
* Form field length restrictions
* Email validation
* Phone number validation

---

## Limitations

This project is intended for educational and demonstration purposes.

Current limitations include:

* SQLite is not ideal for high-traffic production environments.
* Telegram messages are sent through polling every 30 seconds.
* No user authentication system.
* No admin dashboard.
* No file upload support.
* Error logging is minimal.
* Messages may be lost if the bot service is stopped unexpectedly.
* Uses local database storage only.

---

## Possible Improvements

* Replace SQLite with PostgreSQL or MySQL.
* Use a task queue such as Celery.
* Send Telegram notifications instantly after form submission.
* Add email notifications.
* Create an admin dashboard.
* Add project status tracking.
* Implement Docker support.
* Deploy using Gunicorn and Nginx.
* Add automated testing.

---

## Educational Purpose

This project was developed as a mini-project to demonstrate how a web application can collect customer project requests, store them in a database, and notify a team automatically through Telegram.

---

## License

This project is available under the MIT License.

---

<img width="1512" height="718" alt="Screenshot 2025-11-20 at 19 40 25" src="https://github.com/user-attachments/assets/cb018fd8-feb2-40d0-b593-c5f47ecb3294" />
