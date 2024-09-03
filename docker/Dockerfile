FROM python:3.11-slim-buster

# Set the working directory
WORKDIR /app

ENV PYTHONUNBUFFERED=1
ENV PYTHONDONTWRITEBYTECODE 1

RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && apt-get clean


RUN pip3 install -U pip
RUN pip3 install -U poetry

COPY pyproject.toml poetry.lock* /app/

# Project initialization:
RUN poetry config virtualenvs.create false \
    && poetry install --no-interaction --no-ansi

COPY . /app

# Run the application
CMD ["python", "manage.py", "runserver"]