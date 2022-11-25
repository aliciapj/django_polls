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

7. Arrancamos el servidor
```
python manage.py runserver
```
