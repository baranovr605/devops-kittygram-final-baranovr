FROM python:3.13.2

COPY ./requirements.txt ./requirements.txt

RUN apt update && apt install build-essential libpq-dev python3-dev -y && \
    python -m pip install --upgrade pip setuptools wheel && \
    python -m pip install cython && \
    pip install -r requirements.txt 
    

EXPOSE 8000

WORKDIR /app

COPY . .

RUN python manage.py collectstatic --noinput && \
    python manage.py migrate

ENTRYPOINT ["python", "manage.py", "runserver", "0.0.0.0:8000"]
