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
	* __Repository name__: nombre del repositorio, por ejemplo __copy_fight__.
	* __Description__: una breve descripción del __repositorio__.
	* __Public__: para que otros puedan verlo (o __Private__ si se prefiere).
	* Marcar la casilla __Add a README file__ para incluir un archivo __README.md__ en el __repositorio__.
	* Existen dos opciones más que se dejarán en blanco: __Add .gitignore__ y __Choose a license__.

3. Hacer clic en __Create repository__.

### Paso 3: Configurar Git en el ordenador. ###

1. Instalar __Git__:
	* En __Windows__, descargar __Git__ desde https://git-scm.com/ e instalar de forma automática dando a todo __Siguiente__.
	* En __macOS__, se puede instalar __Git__ a través de __Homebrew__:
	` brew install git `

2. Abrir una __terminal__ (__Git Bash__ en __Windows__ o la __terminal__ en __macOS/Linux__) y configurar __Git__:
	` git config --global user.name "TuNombreDeUsuario" `
	` git config --global user.email "TuCorreo@ejemplo.com" `
	Colocar el __nombre de usuario__ y el __email__ de __GitHub__.

3. __Clonar__ el __repositorio__:
	* Navegar a la ubicación donde se desea __clonar__ el __repositorio__:
	` cd ruta/donde/guardar/el/proyecto `
	* __Clonar__ el __repositorio__ con el __enlace__ de __GitHub__:
	` git clone https://github.com/TuUsuario/Copy_Fight.git `
	El __enlace__ se encuentra en el __repositorio__, en la opción __<>Code__ en las pestañas __Local/HTTPS__.
	* Esto creará una __carpeta copy_fight__ con el __repositorio__ descargado.

### Paso 4: Instalar Python y MySQL. ###
* Python:
	* Descárgar desde https://www.python.org/downloads/ y seguir los pasos de instalación (No olvidarse de marcar la opción de __PATH__).
	* Verificar la instalación:
	` python --version `

* MySQL:
	* Descargar __MySQL__ desde https://dev.mysql.com/downloads/mysql/ y seguir los pasos (elegir la __instalación completa__).
	* Si se está en __Windows__ es necesario configurar el __PATH__.
	* Crear una __base de datos básica__.
		* Abrir __MySQL__: Abrir una __terminal__ y ejecutar ` mysql -u root -p ` o ` winpty mysql -u root -p ` (se puede reemplazar __root__ por el __usuario__ configurado en la instalación). Esto abrirá la __consola__ de __MySQL__ y pedirá la __contraseña__.
		* Crear la __Base de Datos__: Una vez dentro de __MySQL__, ejecutar el comando para crear una __base de datos__. En este caso, la __base de datos__ se llamará __copy_fight__.
		` CREATE DATABASE copy_fight; `
		* Crear un __Usuario__ y __Asignar Permisos__ (opcional): Crear un nuevo __usuario__ específicamente para esta __base de datos__.
		` CREATE USER 'tu_usuario'@'localhost' IDENTIFIED BY 'tu_contraseña'; `
		* Luego, otorgar __permisos completos__ a este __usuario__ en la __base de datos__:
		` GRANT ALL PRIVILEGES ON bitefight_clone.* TO 'tu_usuario'@'localhost'; `
		` FLUSH PRIVILEGES; `
		* Verificar la Creación de la __Base de Datos__: Ejecutar el siguiente comando para asegurar de que la __base de datos__ fue creada correctamente:
		` SHOW DATABASES; `
		Deberías verse __copy_fight__ en la __lista__ de __bases de datos__.

### Paso 5: Configurar un entorno virtual. ###

1. Navegar al directorio del __repositorio__:
	` cd copy_fight `

2. Crear un __entorno virtual__:
   	` python -m venv env `

3. Activar el __entorno virtual__:
	* En __Windows__:
	` .\env\Scripts\activate `
	* En __macOS/Linux__:
	` source env/bin/activate `
	* En __Windows__, __Git Bash__:
	` source env/Scripts/activate `

4. Para desactivar el __entorno virtual__:
	` deactivate `

### Paso 6: Instalar Django. ###

1. Con el __entorno virtual__ activado, instalar __Django__:
	` pip install django `

2. Verifica la instalación:
	` django-admin --version `

### Paso 7: Instalar Sublime Text y configurarlo. ###

1. Descargar e instalar __Sublime Text__ desde https://www.sublimetext.com/.
	* Si se está en __Windows__ se necesitará configurar el __PATH__.
	* Buscar en la __lupa__ de inicio __“Variables de entorno” del sistema__.
	* En la sección de __“Variables de sistema”__ buscar el __PATH__ y presionar en __Editar__.
	* Seleccionar __Nuevo__ o __Add__ e ingresar la __ruta__ de __Sublime Text__ hasta el directorio donde está el ____ejecutable__.
	* Presionar en __Aceptar__.

2. Abrir el __repositorio__ en __Sublime Text__:
	* En la __terminal__:
	` subl . `
	* Alternativamente, abrir __Sublime__ y usar __File > Open Folder__ para seleccionar la carpeta del __repositorio__.
