**1º**<br>
Para empezar con la práctica primero tenemos que crear varias carpetas `bind9-docker` y dentro de ella lanzaremos varios comandos `sudo mkdir -p /var/log`, `mkdir -p /var/lib/bind`, `mkdir -p /var/cache/bind`, `mkdir -p /var/run`.<br>
Estas carpetas son necesarias para que se pueda ejecutar correctamente el docker-compose.<br><br>

**2º**<br>
Vamos a crear un archivo con el comando `touch docker-compose.yml` y dentro vamos a meter este texto que es una configuración.<br><br>

version: '3.8' <br>
services: <br>
  bind9: <br>
    image: internetsystemsconsortium/bind9:9.18 <br>
    container_name: bind9 <br>
    ports: <br>
      - "8053:53/tcp"<br>
      - "8053:53/udp"<br>
    volumes:  <br>
      - ./named.conf.options:/etc/bind/named.conf.options<br>
      - ./zones:/etc/bind/zones<br>
      - ./logs:/var/log/bind<br>
    restart: unless-stopped<br><br>

**3**<br>
Ejecutamos el archivo con docker-compose up -d.<br><br>

**4**<br>
Ahora subimos todo a Git con los comandos por orden:<br>
1º `git init`.<br>
2º `git add docker-compose.yml`.<br>
3º `git commit`.<br>
4º `git remote add origin https://github.com/cnovoaarias2001/docker-compose.git`.<br>
5º `git push -u origin master`.<br>