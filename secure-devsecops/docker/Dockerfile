# Use an official, secure Python image
FROM python:3.10-slim

# Set a working directory
WORKDIR /app

# Install system deps
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir gunicorn

# Copy the Flask app code
COPY app/ app/

# Expose the app port
EXPOSE 8080

# Run Gunicorn for production
CMD ["gunicorn", "-b", "0.0.0.0:8080", "main:create_app()"]