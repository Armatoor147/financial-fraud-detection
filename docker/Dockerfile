# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy requirements and install dependencies
COPY docker/requirements-docker.txt .
RUN pip install --no-cache-dir -r requirements-docker.txt

# Copy the model and source code
COPY models/fraud_detection_model.pkl models/
COPY src/ .

# Expose the port the app runs on
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]