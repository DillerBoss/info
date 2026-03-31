Test
Test after SSH
"Инструкции Dockerfile"
1. From - базовый слой (alpine:tag, ubuntu:tag)
2. RUN - для запуска команда в процессе сборки (лучше сразом несколько, чтобы не делать лишние слои)
3. COPY и ADD - <локальный путь> <путь в контейнере> (ADD позволяет скачать файл прямо в контейнер)
4. СMD & ENTRYPOINT - определяем, что запускать 
4.1 СMD - команда по умолчанию ( CMD "echo", "Hello from CMD"] при запуске docker run my-image -> Hello from CMD, но если передать другую команду docker run my-image echo "Override", будет Override
4.2 ENRYPOINT - основной процесс(будет всегда запускаться) (ENTRYPOINT ["echo", "Hello from ENTRYPOINT"] при запуске docker run my-image -> Hello from ENTRYPOINT, docker run my-image "Override" -> Hello from ENTRYPOINT Override
5. ENV - переменные окружения (<ключ> <значение>) При запуске можно переопределить флагом -e
6. EXPOSE - завление о порте (<port>) нужен флаг -p при docker run
Дополнительно
WORKDIR /app: переключает рабочую директорию. Все последующие RUN/CMD/ENTRYPOINT выполняются в /app
USER node: меняет пользователя, от которого будут выполняться команды (безопасность: не оставаться root)
VOLUME /data: указывает, что /data является точкой монтирования тома (volumes)
