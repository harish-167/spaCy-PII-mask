# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container at /app
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Download the spaCy language model
# This bakes the model into the image for faster startup
RUN python -m spacy download en_core_web_lg

# Copy the rest of the application's code into the container at /app
COPY . .

# Make port 5002 available to the world outside this container
EXPOSE 5002

# Define environment variable
ENV FLASK_APP=app.py

# Run app.py when the container launches
CMD ["flask", "run", "--host=0.0.0.0", "--port=5002"]