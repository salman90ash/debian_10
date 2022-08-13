# Настройка Debian_10


## Создаем пользователя

Добавить пользователя

```
adduser www
```

Добавление пользователя в группу sudo

    usermod -aG sudo www

Смена пользователя

    su - www


## Настройка системы
Обновление репозитория

```
sudo apt-get update
```

Настраиваем локали, выбираем (ждем пробел) ru_RU.UTF-8 UTF-8

```
sudo localedef ru_RU.UTF-8 -i ru_RU -fUTF-8 ; \
export LANGUAGE=ru_RU.UTF-8 ; \
export LANG=ru_RU.UTF-8 ; \
export LC_ALL=ru_RU.UTF-8 ; \
sudo locale-gen ru_RU.UTF-8 ; \
sudo dpkg-reconfigure locales
```

Установка минимально необходимого софта
```
sudo apt-get install -y vim mosh tmux htop git curl wget unzip zip gcc build-essential make
```

### Настройка SSH
Создаем папку .ssh
```
mkdir ~/.ssh
```

Устанавливаем права 700 на папку
```
chmod 0700 ~/.ssh
```

Создаем файл authorized_keys
```
touch ~/.ssh/authorized_keys
```

Устанавливаем права 700 на authorized_keys
```
chmod 0644 ~/.ssh/authorized_keys
```

```
sudo vim /etc/ssh/sshd_config
```

Выставляем в конфиге
```
AllowUsers www
PermitRootLogin no
PasswordAuthentication no
```

Перезагружаем SSH сервер
```
sudo service ssh restart ; \
exit
```

Подключаемся по mosh
```
mosh www@62.113.109.163
```
