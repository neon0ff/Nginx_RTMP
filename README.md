# Nginx_RTMP
### Для начала обновим пакеты и установим Nginx и модуль RTMP к нему
```bash
sudo apt update
```
```bash
sudo apt install nginx
```
```bash
sudo apt install libnginx-mod-rtmp
```
```bash
sudo systemctl start nginx
```
```bash
sudo systemctl enable nginx
```
### Открываем конфигурационный файл и добавляем в конец следующие 
```bash
rtmp {
        server {
                listen 1935;
                chunk_size 4096;
                allow publish 127.0.0.1;
                allow publish ваш ip откуда будет идти трансляция;
                deny publish all;

                application live {
                        live on;
                        record off;
                }
        }
}
```
### Открываем порты
```bash
sudo ufw allow 1935/tcp
```

# Настройка OBS
### В настройках трансляции OBS, Сервис выбираем настраиваемый, 
### а в Серврер <code>rtmp://ip сервера RTMP/live</code>
### Ключ прописывать не надо

# VLC
### В VLC прописываем <code> rtmp://ip сервера RTMP/live </code>
