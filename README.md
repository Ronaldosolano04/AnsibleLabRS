# Laboratorio Ansible con Docker

## Objetivo de la práctica

Crear un laboratorio con dos servidores Linux (Ubuntu 24.04) utilizando Docker
y administrarlos con Ansible, automatizando tareas como mostrar información del
sistema, crear directorios y archivos, usar loops y condicionales.

## Comandos para iniciar los contenedores

```bash
docker compose up -d
docker ps
```

Instalar Python en cada contenedor:

```bash
docker exec server1 bash -c "apt update && apt install -y python3"
docker exec server2 bash -c "apt update && apt install -y python3"
```

## Comprobar la conexión

```bash
ansible docker -i inventory.ini -m ping
```

## Comando para ejecutar el playbook

```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Tareas que realiza el playbook

- Muestra el nombre del host.
- Muestra el sistema operativo.
- Crea el directorio `/tmp/ansible-demo`.
- Crea el archivo `info.txt` con el nombre del servidor y el sistema operativo.
- Crea mediante un loop los directorios `logs`, `backup` y `config`.
- Muestra un mensaje únicamente cuando el sistema operativo es Ubuntu.

## Captura de la ejecución exitosa

![Ejecución exitosa del playbook](img/ejecucion.png)

## Detener el laboratorio

```bash
docker compose down
```