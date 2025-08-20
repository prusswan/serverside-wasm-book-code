# Use a lightweight Python base image
FROM python:3.9-slim-bullseye
#FROM python:3.9-slim # debian buster EOL

WORKDIR /app

# Install Flask
RUN pip install flask

# Copy the app
COPY app.py .

# Expose port 8000
EXPOSE 8000

# Run the server
CMD ["python", "app.py"]
