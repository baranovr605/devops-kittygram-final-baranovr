FROM python:3.13.2-alpine

COPY ./requirements.txt ./requirements.txt

RUN apt update && apt install -y build-essential libpq-dev python3-dev && \
    python -m pip install --upgrade setuptools wheel pip && \
    python -m pip install cython && \
    python -m pip install --upgrade pip && \
    pip install -r requirements.txt 
    

EXPOSE 8000

WORKDIR /app

RUN python manage.py collectstatic --noinput && \
    python manage.py migrate

ENTRYPOINT ["python", "manage.py", "runserver", "0.0.0.0:8000"]
