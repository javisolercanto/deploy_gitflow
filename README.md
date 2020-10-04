# Práctica GitFlow (Javier Soler Cantó)

## Introducción a Git y GitFlow

### Git

Git es un sistema de control de versiones creado por Linus Torvals. Nos permite llevar un control sobre nuestros proyectos para así poder trabajar con mayor eficiencia y seguridad. Gracias a git podemos llevar un control más exaustivo de los cambios que se realizan en nuestro proyecto y así poder detectar errores con muchas más facilidad, también un aspecto muy importante de git es la conexión que podemos tener con nuestros compañeros de trabajo y la facilidad que nos permite para guardar y recuperar cambios tanto nuestros como de nuestros compañeros.

![Logo de Git](/images/gitlogo.png)

### GitFlow

GitFlow es una metodología que utiliza las ramas como forma de trabajo, con estas ramas evitamos sobrecargar de commits las ramas más principales y así evitar pérdida de información. Principalmente tenemos dos ramas como son la master (producción) y la develop (desarrollo) , de ésta última saldrán todas las ramas donde se trabajará el código mediante features y más tarde con release que será las agrupaciones de éstas que ya se subirán a la rama master. De ésta última saldrán las ramas de hotfix que nos permiten realizar cambios o pequeños arreglos.

## Práctica

### Usuario 1

![Captura de código](/images/img1.png)

Lo primero que haremos será clonar nuestro repositorio vacío de github que hemos creado, con el comando git clone “nombre_carpeta” . Una vez clonado debemos inicializarlo en git flow para poder trabajar con esta extensión, para ello ejecutamos: git flow init , le daremos el nombre que queramos a nuestras ramas o simplemente podemos dejar los nombres que vienen por defecto. 

![Captura de código](/images/img2.png)

Una vez hecho esto debemos crear una nueva feature para poder trabajar, para ello ejecutamos git flow feature start [nombre_feature] . Este comando crea la rama y nos posiciona en ella para poder trabajar. Una vez situado en ella creamos la carpeta src/ y el archivo home.html al que le damos los elementos necesarios.

![Captura de código](/images/img3.png)

Una vez tengamos nuestros cambios guardados y con el commit realizado debemos subirlos al repositorio remoto, en caso de que otro compañero estuviera involucrado en esta feature, debemos realizar un git flow feature publish [nombre_feature] , este comando nos permite  subir esos cambios a remoto. 

![Captura de código](/images/img4.png)

![Captura de código](/images/img5.png)

Una vez tengamos claro que hemos finalizado con esta feauture debemos subirla al repositorio remoto y cerrar esa rama, para ello, ejecutamos git flow feature finish [nombre_feature] , éste comando nos posicionará en la rama develop y combinará nuestros cambios con los existentes en ésta rama develop, una vez realizado este merge eleminará la rama de la feature. Ahora para poder disponer de la rama develop en el remoto debemos subirla, para ello, ejecutamos git push origin develop y ahora disponemos de ésta rama en el remoto.

### Usuario 2

![Captura de código](/images/img6.png)

Para trabajar con el usuario2 clonaremos con git clone el repositorio, una vez lo tengamos en local utilizamos git flow init para poder utilizar la metodología git flow. Una vez lo tengamos listo podemos crear las nuevas features con el comando git flow feature start [nombre_feature] ahora ya podemos posicionarnos en esas nuevas ramas para poder trabajar sobre las nuevas funcionalidades.

![Captura de código](/images/img7.png)

![Captura de código](/images/img8.png)

Ahora ya el usuario2 ha implementado la funcionalidad contenidoHTML por ello como ya ningún usuario tiene que trabajar con ella podemos ejecutar git flow feature finish [nombre_feature] para así poder combinarlo con el código existente de la rama develop. 

![Captura de código](/images/img9.png)

![Captura de código](/images/img10.png)

![Captura de código](/images/img11.png)

Ahora ya el usuario2 ha implementado la funcionalidad atributosHTML por ello como ya ningún usuario tiene que trabajar con ella podemos ejecutar git flow feature finish para así poder combinarlo con el código existente de la rama develop.

![Captura de código](/images/img12.png)

![Captura de código](/images/img13.png)

### Usuario 3

![Captura de código](/images/img14.png)

Con el usuario3 una vez hayamos repetido el anterior proceso de clonar el repositorio remoto y hacer el git flow init para poder trabajar con la metodología git flow, creamos la nueva feature ejecutando git flow feature start [nombre_feature] . Añadimos el nuevo fichero para la nueva funcionalidad y guardamos los cambios con el commit, ahora ejecutamos un git flow feature finish [nombre_feature] para finalizarla y así hacer un merge con develop y borrar ésta rama de feature.

![Captura de código](/images/img15.png)

![Captura de código](/images/img16.png)

Una vez tenemos todos los cambios actualizados en develop podemos proceder a realizar una nueva release, para ello ejecutamos el comando git flow start release [nombre_release] que nos creará y posicionará en una nueva rama por si tenemos que hacer algún cambio leve y de última hora antes de subirlo a producción.

![Captura de código](/images/img17.png)

Para finalizar la release ejecutamos el comando git flow release finish [nombre_release] , este comando fusiona (merge) las ramas develop y master para así poder tener todas las features. Ahora con un simple git push desde master tenemos los cambios en remoto

### Usuario 1

![Captura de código](/images/img18.png)

Para poder mejorar el contenido una vez ha entrado en producción podemos realizar un hotfix con el comando git flow hotfix start [nombre_hotfix] el cual nos creará una rama en la que podremos cambiar o arreglar un bug y poder fusionarlo con git flow hotfix finish [nombre_hotfix] a la rama master de producción. Este comando no es para desarollar si no para arreglar errores o fallos.

![Captura de código](/images/img19.png)
