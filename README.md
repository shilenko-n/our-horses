# Наши кони

Сборка всего проекта с помощью Docker

Клонируем гитхаб репозиторий рекурсивно с подмодулями
```shell
git clone git@github.com:shilenko-n/our-horses.git --recursive
```

В папке src_main и src_chat копируем .env.example в .env
```shell
cp .env.example .env
```

Собираем проект
```shell
docker-compose up
```

Ключ автоматически сгенерируется

## Схема сервисов проекта

<img width="1200" height="1000" alt="app-map" src="https://github.com/user-attachments/assets/a3efce4e-17d9-4ba9-b491-46de73462b33" />
