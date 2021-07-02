
# Despliegue en servidor

## Front 

    ``` PUBLIC_URL=http://ec2-52-54-213-161.compute-1.amazonaws.com/ npm run build ```

    Copiar la carpeta build al servidor
    
    ``` scp -r -i ~/Downloads/<nombre-archivo>.pem build ubuntu@52.54.213.161:~/ ```

    En el servidor se ha creado un enlace simbólico dentro de /home/usrapp/front

    Cuando despleguemos copiar la carpeta build al directorio /home/usrapp/yyyymmddfront

    borrar el enlace simbólico y crearlo de nuevo para que apunte a la nueva carperta

    Para crear el enlace simbólico 
        ln -s <nombre-carpeta> front

## Back

    Entrar en el servidor
    Carpeta /home/usrapi/back

    Asegurarse en la rama en la que estas
    Si vamos a desplegar en develop ponerse primero en la rama 
        ``` git checkout develop ```
        ``` git reset --hard HEAD ```
        ``` git pull ```
    



    