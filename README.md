# A simple TCP echo server
Runs on Linux and FreeBSD. On Linux you can enable epoll() usage with -DUSE_EPOLL=1 argument to CMake. Otherwise, select() will be used.

# Знакомство с мультиплексированием

Необходимо попробовать клиент-серверное взаимодействие с использованием механизмов мультиплексирования.
Помимо этого нужен Makefile, с помощью которого можно будет собрать клиент и сервер.
Семейство протоколов для использования на выбор: AF_UNIX, AF_INET, AF_INET6.

## Сервер должен:
 * В качестве аргументов принимать адрес, на котором будет ожидать входящих соединений
 * Стартовать, делать bind(2) на заданный адрес и ожидать входящих соединений с использованием одного из механизмов мультиплексирования
 * При получении соединения, добавлять дескриптор в механизм мультиплексирования и ожидать событий и на нем
 * Выполнять на принятых соединениях серверную часть протокола
 * По завершении обработки соединения удалять все события из механизмов мультиплексирования

## Клиент должен:
 * Принимать параметром адрес, к которому стоит подключиться
 * Используя механизмы мультиплексирования подключаться к серверу
 * Используя механизмы мультиплексирования выполнять клиентскую часть протокола
 * Завершаться

Для сильных духом предлагается реализовать код, который будет работать на двух разных ОС, используя на каждой специфичные механизмы мультиплексирования.
Сильность духа будет оцениваться в два балла.
