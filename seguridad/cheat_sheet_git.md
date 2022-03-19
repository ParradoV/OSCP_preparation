GIT CharSheet

**Configuración Inicial

*git config –global user.name “nombre”

git config –global user.email “correo@electronico.com”

Configurar los colores para la interfaz:

git config –global color.ui

Para ver las configuraciones que tenemos para git tenemos que introducir:

giconfig –list

Iniciar repositorio

git init

Si todo hay ido bien iniciará el repositorio y responderá algo parecido a lo siguiente:

Inicializado repositorio Git vacío en /ruta/al/proyecto/.git/

Clonando repositorio

git clone https://github.com/ruta/al/proyecto.git

Copiamos tanto los archivos como el historial, cambios realizados, etc.

NOTA: git reconoce el proyecto a partir del directorio desde donde estás trabajando, por lo que es importante situarse dentro del proyecto adecuado. Es decir, se convertirá en lo que se conoce como “Directorio de Trabajo”

Trabajando con git:

git add NOMBRE_ARCHIVO → Lo añade a una lista virtual para preparar los archivos. A esta lista virtual la llamaremos “Index”.
NOTA: Podemos cambiar el nombre_archivo por otra cosa, quizás por un directorio. Si ponemos “git add .” se añadirán todos los archivos, incluídos los subdirectorios.

Los archivos eliminados se quitan del Index utilizando “git add -u”.

git commit → es la que envía los archivos señalados por el index a nuestro repositorio, que llamaremos “HEAD”. 
NOTA: Puedes hacer un commit de un archivo concreto que se encuentre en el index utilizando “git commit NOMBRE_DE_ARCHIVO”. 
Es posible añadir un texto con “git commit -m “Texto a enviar””, sin embargo si no lo especificas, en el momento de hacer el commit se debe de abrir el editor de textos que tengas como predeterminado (puedes cambiarlo utilizando “–global core.editor EDITOR”).

git status → proporciona un resumen de cómo están las versiones respecto a la versión del repositorio (respecto a HEAD”). Qué archivos has modificado, qué hay en el index, etc.). Cada vez que no sepas lo que has cambiado conviene utilizarlo.

git remote add → Añade un repositorio remoto con el que trabajar, en nuestro caso github. El comando es “git remote add ALIAS_REPOSITORIO DIRECCIÓN_REPOSITORIO. 

git  remote -v → Nos dice qué repositorios remotos tenemos configurados.
git remote rm “NOMBRE” borra el repositorio remoto.
git remote rename NOMBRE_ANTERIOR NOMBRE_ACTUAL.

Recibiendo los cambios

git pull REPOSOTORIO_REMOTO RAMA → Nos trae la rama “RAMA” del repositorio remoto “REPOSITORIO_REMOTO”.
NOTAS: Si en repositorio remoto no pones ninguno, se entiende que será “origin”. Si en las ramas no ponemos ninguna se entiende que será “MASTER”. Es decir, git pull = git pull origin master.

Si hay archivos que tú has modificado pero el otro repositorio no, te quedarás con los tuyos, Cuando se trate de archivos que tú no has cambiado pero que sí son distintos en el remoto, actualizarás los tuyos a este último.

Enviando los cambios
git push REPOSITORIO_REMOTO RAMA
NOTA: Igual que pasaba antes, los valores por defecto son origin para el repositorio y “master” para la rama, con lo que poniendo “git push” tendremos la misma configuración.

IMPROTANTE: Si alguien ha cambiado algo en el servidor remoto, tendremos que hacer primer un pull, resolver los conflictos si los hubiera y después hacer el push.

Archivo .gitignore

Quizás haya algunos archivos que no nos interese sincronizar dentro de nuestro directorio de trabajo (archivos temporales que generan las herramientas, archivos que se crearon en un momento dado y no queremos seguir, etc.). Si hacemos “git add .” se incluirán todos en el index.

Por eso nos podemos crear un archivo (o varios ) denominados “.gitignore” que nos crearemos este archivo en la raíz de nuestro proyecto.

El contenido, por ejemplo, podría ser:

##Ignoramos todos los archivos que terminen en “.temp”
*.temp

Puede ser mucho más complejo, pero seguramente que sea suficiente con esto.

Solución de problemas

Puede haber un problema cuando tú has cambiado algo en tu repositorio local y también un tercero con el que colaboras ha cambiado algo en el repositorio remoto. Ahí es donde entra la solución de problemas y la gestión de ramas.
