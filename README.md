# Домашнее задание к занятию «Очереди RabbitMQ» - Костюк Денис

## Задание 1. Установка RabbitMQ

Используя Vagrant или VirtualBox, создайте виртуальную машину и установите RabbitMQ. Добавьте management plug-in и зайдите в веб-интерфейс.

Итогом выполнения домашнего задания будет приложенный скриншот веб-интерфейса RabbitMQ.

### Решение:

![Скрин1](https://github.com/denniskostyuk/RabbitMQ/blob/main/task_1.png)

## Задание 2. Отправка и получение сообщений

Используя приложенные скрипты, проведите тестовую отправку и получение сообщения. Для отправки сообщений необходимо запустить скрипт producer.py.

Для работы скриптов вам необходимо установить Python версии 3 и библиотеку Pika. Также в скриптах нужно указать IP-адрес машины, на которой запущен RabbitMQ, заменив localhost на нужный IP.

$ pip install pika

Зайдите в веб-интерфейс, найдите очередь под названием hello и сделайте скриншот. После чего запустите второй скрипт consumer.py и сделайте скриншот результата выполнения скрипта

В качестве решения домашнего задания приложите оба скриншота, сделанных на этапе выполнения.

Для закрепления материала можете попробовать модифицировать скрипты, чтобы поменять название очереди и отправляемое сообщение.

### Решение:
Запуск producer.py :
![Скрин2](https://github.com/denniskostyuk/RabbitMQ/blob/main/task_21.png)
Запуск consumer.py :
![Скрин3](https://github.com/denniskostyuk/RabbitMQ/blob/main/task_22.png)
![Скрин4](https://github.com/denniskostyuk/RabbitMQ/blob/main/task_23.png)

Хочу обратить внимание, что файл consumer.py не работал до тех пор, пока я не заменил строку
channel.basic_consume(callback, queue='hello', no_ack=True)
на
channel.basic_consume('hello', callback, auto_ack=True)

## Задание 3. Подготовка HA кластера

В файлах /etc/hosts на 2-х машинах прописаны:
$ cat /etc/hosts
192.168.0.168 test1
192.168.0.148 test2

Машины пингуются.

При вводе на test2 команды rabbitmqctl join_cluster test1 происходит вот такая ошибка:

![Скрин5](https://github.com/denniskostyuk/RabbitMQ/blob/main/task_3.png)

Как решить проблему - не знаю

Статья https://www.rabbitmq.com/cli.html#erlang-cookie не помогла
