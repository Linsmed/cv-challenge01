# Use Python 3.10 image as base
FROM python:3.12-slim

# Set the working directory in the container

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV PYTHONPATH="/app:$PYTHONPATH"

# Install curl and bash
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app
RUN pip install poetry

# Copy the rest of the application code into the container
COPY pyproject.toml poetry.lock /app/

# Install the dependencies using Poetry
RUN poetry config virtualenvs.create true \
    && poetry install --no-dev --no-interaction --no-ansi
COPY . /app
# Make sure the prestart script is executable
RUN chmod +x /app/prestart.sh

# Expose the port the app runs on
EXPOSE 8000

# Run the prestart script and start the server
CMD ["sh", "-c", "poetry run bash /app/prestart.sh && poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload"]