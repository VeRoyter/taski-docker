# Создать образ на основе базового слоя,
# который содержит файлы ОС и интерпретатор Python 3.10.
FROM python:3.10

# Переходим в образе в директорию /app: в ней будем хранить код проекта.
WORKDIR /app

# Устанавливаем Gunicorn для продакшена
RUN pip install gunicorn==20.1.0

# Копируем файл зависимостей
COPY requirements.txt .

# Устанавливаем зависимости
RUN pip install -r requirements.txt --no-cache-dir

# Копируем всё содержимое проекта
COPY . .

# При старте контейнера запускаем Gunicorn связывая его с портом 8000
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]