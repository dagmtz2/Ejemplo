# Instrucciones para sincronizar un repositorio de Git con Github

1. Crear una cuenta en Github
    1. Entra a [github.com](Github.com) y sigue los pasos que la página indica
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
        git@github.com:usuario/repositorio.git
    2. En la consola, clonar su repositorio:
        git clone git@github.com:usuario/repositorio.git
    3. Entrar a su repositorio 
        cd repositorio
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
    5. Crea tu primer commit, usa `git commit -m "aquí pones una descripción de
       tus cambios`





 
