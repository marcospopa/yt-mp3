# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Install system dependencies required for pydub and yt-dlp
# ffmpeg is essential for audio processing
RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    && rm -rf /var/lib/apt/lists/*

# Copy the requirements file into the container at /app
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
# --no-cache-dir ensures we don't store the pip cache, keeping the image size smaller
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application's code into the container at /app
COPY . .

# Make port 5001 available to the world outside this container
EXPOSE 5001

# Define environment variable to ensure python outputs everything straight
# to the container log, making it easier to debug
ENV PYTHONUNBUFFERED 1

# Run app.py when the container launches
# Use gunicorn for a production-ready server in a real-world scenario,
# but for this project, the Flask development server is sufficient.
CMD ["python", "app.py"]