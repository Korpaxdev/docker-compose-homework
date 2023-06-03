FROM python:alpine

EXPOSE 8000

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD python manage.py collectstatic --no-input \
    && python manage.py migrate \
    && python manage.py loaddata ./fixtures/*.json \
    && gunicorn stocks_products.wsgi:application --bind 0.0.0.0:8000



