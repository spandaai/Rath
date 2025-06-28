FROM python:3.10.7

WORKDIR /prediction

# First install system dependencies if needed
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements first to leverage Docker cache
COPY requirements.txt .

# Install Python dependencies with specific versions
RUN pip install --upgrade pip && \
    pip install --no-cache-dir \
    numpy==1.23.5 \
    scipy==1.10.1 \
    pandas==2.0.3 \
    scikit-learn==1.3.0 \
    xgboost==1.7.6 \
    Flask==2.3.2 \
    Flask_Cors==4.0.0 \
    gevent==22.10.2

# Copy the rest of the application
COPY . .

CMD python3 -u /prediction/main.py