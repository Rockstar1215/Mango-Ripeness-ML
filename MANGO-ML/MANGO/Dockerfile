FROM python:3.11

WORKDIR /app

# Install system dependencies for OpenCV
RUN apt-get update && apt-get install -y libgl1-mesa-glx

# Create and activate a virtual environment
RUN python -m venv venv
ENV PATH="/app/venv/bin:$PATH"

ADD app.py .
COPY Ripe /app/MANGO/Ripe
COPY Early_Ripe /app/MANGO/Early_Ripe
COPY Partially_Ripe /app/MANGO/Partially_Ripe
COPY over_ripe /app/MANGO/over_ripe
COPY not_mango /app/MANGO/not_mango
COPY Unripe /app/MANGO/Unripe
COPY templates /app/templates
# Install dependencies
RUN pip install --upgrade pip
RUN pip install Flask Werkzeug numpy opencv-python scikit-learn joblib python-dotenv 

# Copy the application files

# Set the command to run both Python scripts sequentially
CMD ["bash", "-c", "python app.py & python main.py"]
