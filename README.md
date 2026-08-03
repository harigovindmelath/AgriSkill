# Agriskill

A full-stack Django platform connecting **landowners** who need agricultural help with **skilled professionals** who can provide it — with ML-based matching and real-time features.



## Features

**Two user types, dedicated flows**
- **Landowners** — post help needed, browse matched professionals
- **Skilled Professionals** — list skills, get matched to relevant landowner requests

**Authentication**
- Login by email or mobile number
- Passwords hashed with Django's `pbkdf2_sha256` (via `make_password`/`check_password`)

**ML-Based Matching**
- TF-IDF vectorization of skills/requirements text
- Nearest Neighbors search to recommend the best-matching professionals for a landowner's needs

**Real-Time Features**
- Django Channels + WebSockets (`consumer.py`) for live functionality

**Skill Sharing**
- Users can post text + images to share skills or updates

## Tech Stack

- **Django 5.1** + **Django REST Framework**
- **Django Channels** — WebSocket support
- **scikit-learn** — TF-IDF vectorization, Nearest Neighbors matching
- **NumPy**
- **Redis** — channel layer backend for Channels

## Getting Started

```bash
git clone https://github.com/harigovindmelath/agriskill.git
cd agriskill

pip install -r requirements.txt

# Set environment variables (see Configuration below)

python manage.py migrate
python manage.py runserver
```

### Configuration

Before running, set these as environment variables rather than using the values in `settings.py` directly:
```bash
export DJANGO_SECRET_KEY="generate-a-new-key"
export DJANGO_DEBUG="False"  # True only for local development
```

You'll also need Redis running locally for the real-time features (Django Channels).

## Project Structure

```
Agriskill/          # Main Django app — models, views, matching logic, WebSocket consumer
mysite/              # Django project settings, URLs, WSGI/ASGI config
templates/           # HTML templates
manage.py
requirements.txt
Minor-final.pdf      # Full academic project report
```

## Project Report

See [`Minor-final.pdf`](./Minor-final.pdf) for the complete written project report, including problem statement, design decisions, and evaluation.
