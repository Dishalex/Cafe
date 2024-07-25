FROM python:3.9

WORKDIR /app

COPY pyproject.toml poetry.lock /app/
RUN pip install poetry
RUN poetry install

COPY . /app

CMD ["poetry", "run", "uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]
