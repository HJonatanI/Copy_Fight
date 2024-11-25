# Copy Fight - Diseño Web #

## Parte 1: Configuración del entorno de desarrollo. ##

### Paso 1: Crear una cuenta en GitHub. ###

* Entrar a https://github.com/ y regístrarse. Completar el proceso de verificación.
	* En la página de inicio, entrar en la opción __Sing up__.
	* Ingresar __email__.
	* Ingresar __contraseña__.
	* Ingresar __nombre de usuario__.
	* Aceptar o no propagandas al mail.
	* Confirmación de __“No eres un robot”__.
	* Presionar en __“Create Account”__.
	* Si todo es correcto se enviará un __mail de confirmación__ al __email__ ingresado.

### Paso 2: Crear un repositorio en GitHub. ###

1. Una vez dentro de la cuenta de __GitHub__, presionar en __New__ para crear un nuevo __repositorio__.

2. Completar los siguientes campos:
	* __Repository name__: nombre del repositorio, por ejemplo __Copy_Fight__.
	* __Description__: una breve descripción del __repositorio__.
	* __Public__: para que otros puedan verlo (o __Private__ si se prefiere).
	* Marcar la casilla __Add a README file__ para incluir un archivo __README.md__ en el __repositorio__.
	* Existen dos opciones más que se dejarán en blanco: __Add .gitignore__ y __Choose a license__.

3. Hacer clic en __Create repository__.

### Paso 3: Configurar Git en el ordenador. ###

1. Instalar __Git__:
	* En __Windows__, descargar __Git__ desde https://git-scm.com/ e instalar de forma automática dando a todo __Siguiente__.
	* En __macOS__, se puede instalar __Git__ a través de __Homebrew__:
        ```	
        brew install git
        ```

2. Abrir una __terminal__ (__Git Bash__ en __Windows__ o la __terminal__ en __macOS/Linux__) y configurar __Git__:
    ```
    git config --global user.name "TuNombreDeUsuario"
    git config --global user.email "TuCorreo@ejemplo.com"
    ```
	Colocar el __nombre de usuario__ y el __email__ de __GitHub__.

3. __Clonar__ el __repositorio__:
	* Navegar a la ubicación donde se desea __clonar__ el __repositorio__:
    	```
        cd ruta/donde/guardar/el/proyecto
        ```
	* __Clonar__ el __repositorio__ con el __enlace__ de __GitHub__:
    	```
        git clone https://github.com/TuUsuario/Copy_Fight.git
        ````
	    El __enlace__ se encuentra en el __repositorio__, en la opción __<>Code__ en las pestañas __Local/HTTPS__.
	* Esto creará una __carpeta copy_fight__ con el __repositorio__ descargado.

### Paso 4: Instalar Python y MySQL. ###

* __Python__:
	* Descárgar desde https://www.python.org/downloads/ y seguir los pasos de instalación (No olvidarse de marcar la opción de __PATH__).
	* Verificar la instalación:
        ```	
        python --version
        ```

* __MySQL__:
	* Descargar __MySQL__ desde https://dev.mysql.com/downloads/mysql/ y seguir los pasos (elegir la __instalación completa__).
	* Si se está en __Windows__ es necesario configurar el __PATH__.
	* Crear una __base de datos básica__.
		* Abrir __MySQL__: Abrir una __terminal__ y ejecutar ` mysql -u root -p ` o ` winpty mysql -u root -p ` (se puede reemplazar __root__ por el __usuario__ configurado en la instalación). Esto abrirá la __consola__ de __MySQL__ y pedirá la __contraseña__.
		* Crear la __Base de Datos__: Una vez dentro de __MySQL__, ejecutar el comando para crear una __base de datos__. En este caso, la __base de datos__ se llamará __copy_fight__.
    		```
    		CREATE DATABASE copy_fight;
    		```
		* Crear un __Usuario__ y __Asignar Permisos__ (opcional): Crear un nuevo __usuario__ específicamente para esta __base de datos__.
    		```
            CREATE USER 'tu_usuario'@'localhost' IDENTIFIED BY 'tu_contraseña';
            ```
		* Luego, otorgar __permisos completos__ a este __usuario__ en la __base de datos__:
    		```
            GRANT ALL PRIVILEGES ON bitefight_clone.* TO 'tu_usuario'@'localhost';
    		FLUSH PRIVILEGES;
    		```
		* Verificar la Creación de la __Base de Datos__: Ejecutar el siguiente comando para asegurar de que la __base de datos__ fue creada correctamente:
    	    ```
            SHOW DATABASES;
            ```
		    Deberías verse __copy_fight__ en la __lista__ de __bases de datos__.

### Paso 5: Configurar un entorno virtual. ###

1. Navegar al directorio del __repositorio__:
    ```
    cd Copy_Fight
    ```
2. Crear un __entorno virtual__:
    ```
    python -m venv env
    ```
3. Activar el __entorno virtual__:
	* En __Windows__:
        ```
        .\env\Scripts\activate
        ```
	* En __macOS/Linux__:
        ```
        source env/bin/activate
        ```
	* En __Windows__, __Git Bash__:
        ```    
        source env/Scripts/activate
        ```
4. Para desactivar el __entorno virtual__:
    ```
    deactivate
    ```

### Paso 6: Instalar Django. ###

1. Con el __entorno virtual__ activado, instalar __Django__:
    ```
    pip install django
    ```
2. Verifica la instalación:
    ```
    django-admin --version
    ```
### Paso 7: Instalar Sublime Text y configurarlo. ###

1. Descargar e instalar __Sublime Text__ desde https://www.sublimetext.com/.
	* Si se está en __Windows__ se necesitará configurar el __PATH__.
	* Buscar en la __lupa__ de inicio __“Variables de entorno” del sistema__.
	* En la sección de __“Variables de sistema”__ buscar el __PATH__ y presionar en __Editar__.
	* Seleccionar __Nuevo__ o __Add__ e ingresar la __ruta__ de __Sublime Text__ hasta el directorio donde está el __ejecutable__.
	* Presionar en __Aceptar__.

2. Abrir el __repositorio__ en __Sublime Text__:
	* En la __terminal__:
        ```
        subl .
        ```
	* Alternativamente, abrir __Sublime__ y usar __File > Open Folder__ para seleccionar la carpeta del __repositorio__.

## Parte 2: Crear la estructura básica del proyecto en Django. ##

### Paso 1: Crear un proyecto de Django en el entorno local. ###

1. Asegúrase de que el __entorno virtual__ esté activado:
	```
	.\env\Scripts\activate  # En Windows
	# o
	source env/bin/activate  # En macOS/Linux
	# o
	source env/Scripts/activate  # En Windows con GitBash
	```
2. En la __terminal__, navegar al directorio del __repositorio__ y usar el siguiente comando para crear el __proyecto__ de __Django__:
	```
	django-admin startproject copy_fight .
	```
    El punto (.) al final indica a __Django__ que cree los archivos del proyecto en el directorio actual, en lugar de crear una carpeta adicional.

3. Después de ejecutar el comando, se generarán algunos archivos y carpetas en el proyecto:
	* __copy_fight/__ (directorio del proyecto)
	* **__init__.py**: hace que __Django__ trate este directorio como un __módulo__ de __Python__.
	* __settings.py__: contiene toda la configuración del proyecto __(base de datos, aplicaciones, middleware, etc.)__.
	* __urls.py__: administra todas las __rutas__ o __URLs__ del proyecto.
	* __wsgi.py y asgi.py__: archivos que permiten que el proyecto se __comunique__ con el __servidor web__.
	* __manage.py__: una herramienta para __ejecutar comandos__ de __Django__ (cómo iniciar el servidor, aplicar migraciones, y más).

4. Para verificar que el proyecto se haya creado correctamente, iniciar el servidor de desarrollo de __Django__:
	```
	python manage.py runserver
	```
    Abrir el navegador y visitar http://127.0.0.1:8000/. Se debería ver una __pantalla de bienvenida__ de __Django__ indicando que el proyecto está funcionando.

### Paso 2: Conocer los archivos de configuración y estructura básica de Django. ###

Antes de continuar, es importante entender la función de los archivos principales en la estructura del proyecto:

* __settings.py__: este archivo contiene todas las configuraciones del proyecto, como la configuración de la __base de datos__, __aplicaciones__ instaladas, configuraciones de seguridad y más. Se cambiarán varias configuraciones aquí a medida que avance el proyecto.

* __urls.py__: en este archivo se definen las __URLs__ principales del proyecto. Al añadir más aplicaciones, se podrán organizar las __URLs__ de manera __modular__.

* __manage.py__: este archivo es una __interfaz de línea de comandos__ para interactuar con el proyecto. Se usará para ejecutar el __servidor__, aplicar cambios en la __base de datos__, y realizar otras tareas administrativas.

### Paso 3: Configurar Django para conectar con MySQL. ###

1. Abrir __settings.py__ en el directorio __copy_fight__.

2. Buscar la sección __DATABASES__. Cambiar la configuración predeterminada para conectar a __MySQL__. Reemplazar el contenido de __DATABASES__ con el siguiente código:
	```
	DATABASES = {
		'default': {
	    	'ENGINE': 'django.db.backends.mysql',
	        'NAME': 'nombre_base_datos', # Cambiar este valor con el nombre de la base de datos
	        'USER': 'tu_usuario', # Cambiar este valor con el usuario de MySQL
	        'PASSWORD': 'tu_contraseña', # Cambiar este valor con la contraseña del usuario
	        'HOST': 'localhost', # Dejar 'localhost' si la base de datos está en el ordenador
	        'PORT': '3306', # Puerto predeterminado de MySQL
	    }
	}
	```
3. Instalar el conector de __MySQL__ para __Python__, llamado __mysqlclient__, con el siguiente comando:
	```
	pip install mysqlclient
	```
4. Para comprobar que la conexión a la __base de datos__ esté configurada correctamente, ejecutar:
	```
	python manage.py migrate
	```
    Esto aplicará las __migraciones predeterminadas__ y debería crear las __tablas básicas__ en la __base de datos MySQL__ que se especificó.

### Paso 4: Crear una aplicación en Django para la lógica del juego. ###

__Django__ utiliza __aplicaciones__ para organizar funcionalidades. Se creará una __aplicación__ para gestionar la lógica y el contenido principal del juego, como los usuarios, los personajes, el sistema de combate, etc.

1. En la __terminal__, asegurarse de estar en el directorio del proyecto y ejecutar el siguiente comando para crear una aplicación llamada __game__:
    ```
    python manage.py startapp game
    ```   
2. Después de ejecutar el comando, se verá una nueva carpeta llamada __game__ con los siguientes archivos y directorios:
	* __migrations/__: almacena las __migraciones__ de la __base de datos__ para esta __aplicación__.
	* __admin.py__: registra __modelos__ para gestionarlos en la __interfaz__ de __administración__ de __Django__.
	* __apps.py__: permite a __Django__ reconocer esta __aplicación__ como parte del proyecto.
	* __models.py__: define las tablas de la __base de datos__ en forma de __modelos__.
	* __views.py__: se escriben las __funciones__ que manejan las __solicitudes__ de los __usuarios (vistas__).
	* __tests.py__: se usa para realizar __pruebas automáticas__ a la __aplicación__.
	* __urls.py__: este archivo no está creado por defecto, se añadira más adelante para definir __rutas__ específicas de la __aplicación game__.

3. Ahora se debe informar a __Django__ que la __aplicación game__ forma parte del proyecto. Abrir __settings.py__ y buscar la sección __INSTALLED_APPS__. Añadir __game__ al final de la __lista__:
	```
	INSTALLED_APPS = [
		'django.contrib.admin',
	    'django.contrib.auth',
	    'django.contrib.contenttypes',
	    'django.contrib.sessions',
	    'django.contrib.messages',
	    'django.contrib.staticfiles',
	    'game',  # La aplicación del juego
	]
	```								
    __Django__ permite dividir la funcionalidad del proyecto en __aplicaciones__, y cada __aplicación__ puede tener su propio conjunto de __vistas__, __modelos__ y __rutas__. Para entender el flujo:

4. __Modelos (models.py)__: Aquí se definen los __modelos__ que representan las __tablas__ en la __base de datos__. Por ejemplo, para los personajes de los jugadores, se crea un __modelo Character__.

5. __Vistas (views.py)__: Las __vistas__ procesan las __solicitudes__ y devuelven respuestas. Cada __vista__ puede representar una __página__ del juego, como el perfil del personaje o la interfaz de combate.

6. __URLs (urls.py)__: Cada __aplicación__ puede tener su propio archivo de __URLs__ para organizar sus __rutas__ de manera __modular__ y luego vincularse con el __urls.py__ principal del proyecto.