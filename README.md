# Bienvenido a la librería de encuestas de django

A continuación vamos a explicar cómo instalar el proyecto

1. Descarga el código con el siguiente comando:

```
git clone https://github.com/aliciapj/django_polls.git
```

2. Entramos en la carpeta descargada `django_polls` y creamos el entorno virtual con el comando:
```
cd django_polls
python3 -m venv .venv
```

3. Activamos el entorno virtual
```
source .venv/bin/activate
```

4. Instalamos las librerías necesarias que se encuentran en el fichero `requirements.txt`
```
pip install -r requirements.txt
```

5. Ejecutamos las migraciones
```
python manage.py migrate
```

6. Cargamos los datos iniciales:
```
python manage.py loaddata fixtures/polls_data.json
```

7. Configurar localhost como ip permitida para django. Editar el fichero `django_polls/settings.py`. Añadir la ip local a la variable `ALLOWED_HOSTS` (en la línea 28) de forma que quede así:
```
ALLOWED_HOSTS = ['192.168.33.10', '127.0.0.1', 'localhost']
```

8. Arrancamos el servidor
```
python manage.py runserver
```

## Cómo instalar el proyecto en una máquina remota con Fabric

1. Instala la librería de Fabric desde el repositorio de PIP
```
pip install fabric
```

2. Comprueba la ip del servidor remoto y las credenciales en las línea 11-15 del script `fabfile.py`
```python
@task
def development(ctx):
    ctx.user = 'vagrant'
    ctx.host = '192.168.33.10'
    ctx.connect_kwargs = {"password": "vagrant"}
```

3. Ejecuta el script con el siguiente comando
```
fab development deploy
```

## Cómo instalar el proyecto en una máquina remota con Fabric

1. Instala la librería de Fabric desde el repositorio de PIP
```
pip install fabric
```

2. Comprueba la ip del servidor remoto y las credenciales en las línea 11-15 del script `fabfile.py`
```python
@task
def development(ctx):
    ctx.user = 'vagrant'
    ctx.host = '192.168.33.10'
    ctx.connect_kwargs = {"password": "vagrant"}
```

3. Ejecuta el script con el siguiente comando
```
fab development deploy
```

## Cómo aprovisionar una máquina y desplegar el proyecto con Ansible

1. Instala Ansible en el sistema operativo  
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

2. Instala la librería de Ansible desde el repositorio de PIP
```
pip install ansible
```

3. Comprueba la configuración de variables del fichero `ansible/vars.yml` y ajusta las que necesites

4. Ejecuta el script con el siguiente comando
```
cd ansible  # solo si estas en otra carpeta en la terminal
ansible-playbook -i hosts provision.yml --user=vagrant --ask-pass
```