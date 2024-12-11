# Домашнее задание к лекции «Docker»

## Задание 1

[Nginx](./nginx)

Заменена страница приветствия Nginx.
Команда docker image build . --tag=my_image_nginx:1.0 собирает образ с изменённой страницей привествия.
Команда COPY в докерфайле скопирует html шаблон в указанную папку контейнера nginx.
Команда docker run -d --name my_container_nginx my_image_nginx:1.0 запускает контейнер на основании созданного образа.
Команда docker exec -it my_container_nginx bash позволяет зайти в запущенный контейнер,
команда curl localhost:80 получить изменённую страницу приветствия.

Альтернативно также вижу ещё следующий варинант / подход к решению задачи:
Провалиться в стандартный контейнер nginx командой docker exec -it container_name bash. 
Перейти в директорию etc/nginx/conf.d, где с помощью nano (apt-get install nano) отредактировать конфигурацию default.conf, 
изменив путь location/имя index.html/создать свой html шаблон. 
Далее командой docker commit имя контейнера имя образа:тег записать образ с новым приветствием.

## Задание 2

[Smart home](./Smart_home)

Создан контейнер для REST API сервера проекта из курса по Django [Умный дом](https://github.com/dazarin/Smart_home).

Создание образа:
```bash
docker image build . --tag=smart_home_test_image:1.0
```

Создание и запуск контейнера:
```base
docker run -p 8000:8000 --name=smart_home_test_container smart_home_image:1.0
```