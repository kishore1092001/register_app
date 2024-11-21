# Start with your base image
FROM python:3.9-slim

# Install dependencies, including netcat-openbsd
RUN apt-get update && apt-get install -y netcat-openbsd

# Set up your app
WORKDIR /app
COPY . /app

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the Flask port
EXPOSE 5000

# Command to start the application
CMD ["sh", "-c", "while ! nc -z $MYSQL_HOST 3306; do sleep 1; done && python app.py"]

