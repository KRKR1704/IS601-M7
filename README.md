# QR Code Generator — Quick Run then Setup

## Run the program (quick)

Prerequisites: Python 3.10+ installed or Docker available.

Run locally (Python virtual environment recommended):

```bash
# create and activate venv (optional but recommended)
python3 -m venv venv
source venv/bin/activate

# install dependencies
pip install -r requirements.txt

# run the app (generates a timestamped PNG in qr_codes/)
python main.py --url https://github.com/KRKR1704
```

Run in Docker (no Python install required):

```bash
# build the image
docker build -t qr-code-generator-app .

# run the container and mount local qr_codes to retrieve generated images
docker run --rm -v "$PWD/qr_codes:/app/qr_codes" --name qr-generator qr-code-generator-app --url https://github.com/KRKR1704

# see container logs
docker logs qr-generator
```

Run with docker-compose:

```bash
docker compose up --build
```

Notes:
- Output images are saved to the `qr_codes/` folder.
- The app accepts env vars for defaults: `QR_CODE_DIR`, `FILL_COLOR`, `BACK_COLOR`.

---

## Project Setup (step-by-step)

1. Install Git and Python 3.10+ (OS-specific installers)

2. Clone repository

```bash
git clone <repository-url>
cd <repository-directory>
```

3. Create and activate a virtual environment (recommended)

```bash
python3 -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate.bat # Windows (PowerShell/CMD)
```

4. Install dependencies

```bash
pip install -r requirements.txt
```

5. Run the app

```bash
python main.py --url https://www.example.com
```

6. (Optional) Build and run with Docker

```bash
docker build -t qr-code-generator-app .
docker run --rm -v "$PWD/qr_codes:/app/qr_codes" qr-code-generator-app --url https://www.example.com
```

7. Push to GitHub

```bash
git add .
git commit -m "Dockerized QR Code Generator"
git push origin main
```

---

## CI / Docker Hub notes

- The repo contains a GitHub Actions workflow (`.github/workflows/*`) that can build and push the image to Docker Hub. To enable pushing, set these repository secrets:
  - `DOCKERHUB_USERNAME` — your Docker Hub username
  - `DOCKERHUB_TOKEN` — Docker Hub access token (not your password)

---

# Useful Commands Cheat Sheet

| Action                         | Command                                          |
| ------------------------------- | ------------------------------------------------ |
| Configure Git Global Username  | `git config --global user.name "Your Name"`      |
| Configure Git Global Email     | `git config --global user.email "you@example.com"` |
| Clone Repository                | `git clone <repo-url>`                          |
| Create Virtual Environment     | `python3 -m venv venv`                           |
| Activate Virtual Environment   | `source venv/bin/activate` / `venv\Scripts\activate.bat` |
| Install Python Packages        | `pip install -r requirements.txt`               |
| Build Docker Image              | `docker build -t <image-name> .`                |
| Run Docker Container            | `docker run -it --rm <image-name>`               |
| Push Code to GitHub             | `git add . && git commit -m "message" && git push` |