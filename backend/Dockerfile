FROM python:3.13.2

COPY ./requirements.txt ./requirements.txt

RUN apt update && apt install python3.6-dev libmysqlclient-dev && \
    python -m pip install --upgrade pip setuptools wheel && \
    pip install -r requirements.txt 
    

EXPOSE 8000

WORKDIR /app

RUN python manage.py collectstatic --noinput && \
    python manage.py migrate

ENTRYPOINT ["python", "manage.py", "runserver", "0.0.0.0:8000"]
