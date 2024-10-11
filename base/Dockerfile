# Use the official Python image from the Docker Hub
FROM python:3.12.4-slim

# Set the working directory in the container
WORKDIR /app

# Install system dependencies if needed 
RUN apt-get update && \
    apt-get install -y --no-install-recommends gcc && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Copy the requirements file into the container
COPY requirements.txt .

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY . .

# Command to run the application
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "base.wsgi:application"]

