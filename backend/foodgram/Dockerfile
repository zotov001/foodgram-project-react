FROM python:3.7-slim

WORKDIR /app 

COPY foodgram-project-react/requirements.txt . 

RUN pip3 install -r ./requirements.txt --no-cache-dir 

COPY . .

CMD ["gunicorn", "foodgram.wsgi:application", "--bind", "0:8000" ] 