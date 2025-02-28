1. Crear una cuenta en github.com
2. Crear un nuevo repositorio
    1. Seleccionar que sea público
    2. Ponerle cualquier nombre
    3. No importa si le ponen descripción o no
    4. Seleccionar que se cree un archivo README
3. Una vez creado el repositorio, conectar con SSH
    1. Dar click en "Code" y luego en "SSH"
    2. Dar click en "add a new publick key"
    3. Ponerle un nombre relacionado con su computadora (ej.: Linux-Daniel)
    4. Abrir el explorador de archivos en una carpeta de su elección
    5. Dar click derecho y seleccionar "Git Bash aquí"
    6. Ingresar el siguiente comando, sustituyendo con su correo: 
        ssh-keygen -t ed25519 -C "your_email@example.com"
    7. Presionan enter en los siguientes tres "prompts" que muestre la terminal
    8. Ingresar el siguiente comando:
        eval "$(ssh-agent -s)"
    9. Y luego ingresar este:
        ssh-add ~/.ssh/id_ed25519
    10. Por último:
        cat ~/.ssh/id_ed25519.pub
    11. Copiar lo que salga en el campo de Github (en el navegador de internet)que dice "Key"
    12. Click en "Add SSH Key"
    13. De vuelta en la consola (Git Bash), ingresa este comando para comprobar que los pasos anteriores se hayan seguido correctamente:
        ssh -T git@github.com
4. Clonar el repositorio
    1. Copiar el enlace que aparece en Code -> SSH en su cuenta de Github, debe ser algo como: 
        git@github.com:usuario/repositorio.git
    2. En la consola, clonar su repositorio:
        git clone git@github.com:usuario/repositorio.git
    3. Entrar a su repositorio 
        cd repositorio


        



 
