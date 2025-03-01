# Use official Python image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the requirements file
COPY requirements.txt .

# Install dependencies
RUN apt update && apt install -y build-essential python3-dev libffi-dev

RUN pip3 install --no-cache-dir -r requirements.txt

# Copy the rest of the app files
COPY . .

# Set environment variables (can be overridden at runtime)
ENV REDIS_HOST=redis
ENV REDIS_PORT=6379
ENV REDIS_CHANNEL=log_channel

# Command to run the application
CMD ["python3", "main.py"]
