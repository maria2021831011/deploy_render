# Flask Application Deployment on Render

This repository contains a Flask web application deployed using Render.

## Prerequisites

* Python 3.11+
* Git
* GitHub Account
* Render Account

## Local Setup

### Create Virtual Environment

```bash
conda create -n myenv python=3.11 -y
conda activate myenv
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run the Application

```bash
python app.py
```

The application will be available at:

```
http://localhost:5000
```

---

## Project Structure

```text
project/
│
├── app.py
├── requirements.txt
├── Procfile
├── templates/
├── static/
└── README.md
```

---

## Deployment on Render

### Step 1: Push Code to GitHub

```bash
git init
git add .
git commit -m "Initial Commit"
git branch -M main
git remote add origin <repository-url>
git push -u origin main
```

### Step 2: Create a Render Web Service

1. Log in to Render.
2. Click **New +**.
3. Select **Web Service**.
4. Connect your GitHub repository.
5. Choose the repository.

### Step 3: Configure Build Settings

#### Build Command

```bash
pip install -r requirements.txt
```

#### Start Command

```bash
gunicorn app:app
```

> If your Flask application file is named `main.py`, use:

```bash
gunicorn main:app
```

### Step 4: Deploy

Click **Create Web Service** and wait for the deployment to complete.

Render will automatically:

* Clone the repository
* Install dependencies
* Build the application
* Deploy the service

---

## Environment Variables

If your application uses secrets or database credentials, add them in:

**Render Dashboard → Environment Variables**

Example:

```env
SECRET_KEY=your_secret_key
DB_HOST=your_database_host
DB_USER=your_database_user
DB_PASSWORD=your_database_password
```

Access them in Flask:

```python
import os

secret_key = os.getenv("SECRET_KEY")
```

---

## Requirements

Example `requirements.txt`:

```text
Flask
gunicorn
```

Generate automatically:

```bash
pip freeze > requirements.txt
```

---

## Procfile

Create a file named `Procfile` in the project root:

```text
web: gunicorn app:app
```

---

## Live Deployment

After successful deployment, Render provides a URL similar to:

```text
https://your-app-name.onrender.com
```

Visit the URL to access the application.

---

## License

This project is licensed under the MIT License.

