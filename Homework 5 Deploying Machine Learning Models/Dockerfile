FROM agrigorev/zoomcamp-model:2025

WORKDIR /app

# Install system-level build tools so numpy can compile
RUN apt-get update && apt-get install -y build-essential && rm -rf /var/lib/apt/lists/*

# Copy dependencies
COPY requirements.txt .

# Install Python dependencies
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

# Copy your FastAPI app and model
COPY app.py .
COPY pipeline_v1.bin .

EXPOSE 8000

# Run FastAPI app
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
