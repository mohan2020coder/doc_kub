FROM python:3.11-alpine
WORKDIR /app
COPY . .
RUN pip install Flask redis
CMD ["python", "app.py"]