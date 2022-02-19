# Указывает Docker использовать официальный образ python 3 с dockerhub в качестве базового образа
FROM python:3.8.12
# Устанавливает переменную окружения, которая гарантирует, что вывод из python будет отправлен прямо в терминал без предварительной буферизации
ENV PYTHONUNBUFFERED 1
ENV TZ=Europe/Moscow
# Устанавливает рабочий каталог контейнера — "app"
WORKDIR /webapp
# Копирует все файлы из нашего локального проекта в контейнер
COPY ./src /webapp
# Запускает команду pip install для всех библиотек, перечисленных в requirements.txt
RUN && pip install -r /requirements/main.txt --no-cache-dir \
    && pip install -r /requirements/poetry.txt --no-cache-dir \
    && pip install -r /requirements/test.txt --no-cache-dir


RUN groupadd -r django \
    && useradd -r -u 1500 -g django django \
    && mkdir -p /webapp/logs \
    && chown -R django /webapp

USER 1500