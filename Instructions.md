# Instrucciones para sincronizar un repositorio de Git con Github

1. Crear una cuenta en Github
    1. Entra a [Github](github.com) y sigue los pasos que la página indica
       para crear una cuenta.
2. Crear un nuevo repositorio
    1. Una vez creada la cuenta, busca la opción de crear un nuevo repositorio.
    2. Selecciona que sea público
    2. Elige un nombre cualquiera 
    3. No importa si tiene descripción o no
    4. Selecciona que se cree un archivo README
3. Una vez creado el repositorio, conectar con SSH
    1. En la página principal del repositorio busca el botón verde de "Code" y luego da click en "SSH"
    2. Da click en "add a new public key"
    3. Elige un nombre relacionado con tu computadora (ej.: Linux-Daniel)
    4. Abre el explorador de archivos en una carpeta de tu elección
    5. Da click derecho dentro de la carpeta y selecciona "Git Bash aquí" (si
       no ves la opción, usa shift + click derecho)
    6. Ingresar el siguiente comando, sustituyendo con su correo: 
        `ssh-keygen -t ed25519 -C "your_email@example.com"`
    7. Presionan enter en los siguientes tres "prompts" que muestre la terminal
    8. Ingresar el siguiente comando:
        `eval "$(ssh-agent -s)"`
    9. Y luego ingresar este:
        `ssh-add ~/.ssh/id_ed25519`
    10. Por último:
        `cat ~/.ssh/id_ed25519.pub`
    11. Copiar lo que salga en el campo de Github (en el navegador de internet)que dice "Key"
    12. Click en "Add SSH Key"
    13. De vuelta en la consola (Git Bash), ingresa este comando para comprobar que los pasos anteriores se hayan seguido correctamente:
        `ssh -T git@github.com`
4. Clonar el repositorio de manera local
    1. Copiar el enlace que aparece en Code -> SSH en su cuenta de Github, debe ser algo como: 
        > git@github.com:usuario/repositorio.git
    2. En la consola, clonar su repositorio:
        `git clone git@github.com:usuario/repositorio.git`
    3. Entrar a su repositorio 
        `cd repositorio`
5. Registrar y opciones por defecto para Git
    1. Usar los siguientes comandos (uno por uno) para registrar su correo
       y nombre de usuario:
    `git config --global user.email "su_direccion_de_email@gmail.com"`
    `git config --global user.name "su_username_de_github"`
    2. Usar el siguiente comando para cambiar el nombre de tu branch principal
       a "main" en vez de "master"
    `git config --global init.defaultbranch main`
6. Subir un primer cambio
    1. Usa `git status` para que Git te muestre el estado actual de tu
       repositorio
    2. Crea un nuevo archivo dentro de tu repositorio, puedes hacerlo desde el
       explorador de archivos o directamente en un bloc de notas guardándolo
como "ejemplo.txt" o desde la terminal con el siguiente comando:
    `echo "Hola, Mundo! :)" >> ejemplo.txt`
    3. Una vez creado el archivo, revisa la salida de `git status`
    4. Si tu archivo ya fue reconocido por Git como un archivo nuevo, agrégalo
       al área de staging (es decir, a la lista de cambios que se van a meter
en tu próximo commit, esto se hace con este comando:
    `git add ejemplo.txt`
    5. Crea tu primer commit, usa `git commit -m "aquí va una corta descripción de
       tus cambios`
    6. Usa de nuevo `git status` para confirmar que todo esté en orden y listo para enviarlo al repositorio remoto.
    7. Usa `git push` para llevar tus cambios al repositorio remoto.
7. Ejemplo de subir el reporte de una práctica
    1. Al inciar la creación de mi práctica, crearé un *branch* llamado "practica_n", esto se hace con el comando `git branch practica_n`
    2. En esta nueva branch, voy a ir lleavando el control de mis cambios, de manera que mis cambios no afecten a mi branch principal hasta que yo decida hacer un *merge*, más delante se explicará esto.
    3. Para cambiar a esa branch, se utiliza el comando `git checkout practica_n`. Una *branch* es una línea de tiempo a la cuál se le van agregando commits.
    4. El comando *checkout* nos permite movernos entre distintos commits en nuestro repositorio, donde un *commit* es una "captura" o un "punto de guardado" de nuestro proyecto. Cada commit que yo hago es un punto al que puedo moverme. Cada *branch* o línea temporal tiene un nombre, pero en realidad ese nombre es solo un "apodo" para el último commit en la lína temporal. Si esto no es claro, más adelante se explicará mejor.
    5. Ahora, crearé una nueva carpeta para guardar el código de la práctica. Esto se puede hacer desde el navegador de archivos o desde la consola con el siguiente comando: `mkdir codigo`
    6. De la misma manera, voy a crear una nueva carpeta para guardar el reporte con el comando: `mkdir reporte`
    7. Si uso el comando `git status`, no aparecerá nada en la salida puesto que mis cambios no incluyen archivos. Pero puedo empezar a crear archivos. 
    8. Entraré a la carpeta de código y crearé un nuevo archivo, digamos *practica.cpp*. En el caso de uso normal, uno podría guardar ahí un proyecto de arduino. En mi caso, el archivo lo crearé mediante una serie de comandos: 
        1. Primero entro a la carpeta de código: `cd codigo`
        2. Luego crearé el archivo: `echo "/* Este será un archivo de arduino */" >> practica.cpp`
        3. Por último, regresaré a la carpeta de arriba: `cd ..` 
    9. Si ahora uso el comando `git status`, me mostrará que hay cambios dentro de la carpeta *codigo*. Entonces, puedo agregar todo lo que esté dentro de la carpeta usando el comando `git add codigo`
    10. Crearé un nuevo archivo dentro de la carpeta reporte y lo agregaré de manera similar a como lo hice con el código. 
    11. Una vez agregados los cambios presentes en ambas carpetas, crearé un commit con `git commit -m "Subir reporte y codigo"`
    12. Por último, para tener un respaldo en la nube, le haré un *push*: `git push`. Esto, sin embargo, puede generar un problema ya que no hay ninguna branch llamada *practica_n* registrada en el repositorio remoto (alias: la nube, alias: Github). Al tratar de hacer el push, Git me pide usar este comando: ` git push --set-upstream origin practica_n`, así que lo ingresaré y permitiré que se cree una nueva branch en mi repositorio remoto. 
    13. Después de esto, puedo ir agregando todos mis cambios mediante más commits en la branch *practica_n*
    14. En el navegador de internet puedo ir a mi repositorio de Github y si todo salió bien, veré un mensaje relacionado a que hice *push* a mi branch *practica_n* recientemente. Si ya tengo todo listo, puedo entonces hacer un *merge*, es decir, unir todo lo que hice en una branch (*practica_n*) con mi branch principal. Para esto, hay que dar click en *Compare & pull request*.
    15. En la siguiente página, le pondré un título y una descripción a mi *merge request*, que será básicamente uan justificación de por qué quiero juntar cambios de una branch con otra. 
    16. Si no hay conflictos y después de crear la *pull request*, la siguiente página me debe mostrar el botón "Merge pull request". Presionando esto, se habrán integrado todos los cambios a mi branch principal. 
