# Pasos Git

## Ramas

   - Main -> Donde tenemos el código que está en producción. Esta rama solo se cambia cuando estamos muy muy seguros que ya está todo bien.
   - Develop -> Es la rama donde vamos a probar los cambios que vayamos haciendo antes de subir a Main
   
   He pensado que podemos generar ramas Main de las épicas trabajar sobre esas todos y una vez que esté una funcionalidad completa pasarla a Develop y de ahí a Main

   Pongo un ejemplo:
        - Vamos a empezar a trabajar con el login 
            - Podemos generar la rama FRONT-1000-Main que va a partir de develop
                     
                ``` fetch --all   (en develop para conseguir todas las ramas) ```
                ``` git checkout FRONT-1000-Main  (para situaros en esta rama) ```
            
            - Desde aqui vamos a sacar cada uno nuestra rama de trabajo. 
            - Para nombrar nuestra rama:
                - Ponemos nuestras iniciales por ejemplo EG
                - Ponemos el nombre de la tarea que viene en trello por ejemplo FRONT-1000-Montar_servidor (es importante que no haya espacios en blanco)

                El nombre de la rama quedaría EG-FRONT-1000-Montar_servidor
                De esta forma todos sabemos a primer vista quién ha hecho la tarea, qué tarea es y podriamos localizarza de forma rápida en el tablero.

## Flujo de trabajo

    - Realizamos todas las tareas en nuestra rama.
    - La dinámica ya la conocéis, pero lo pongo aqui. 
        
        ``` git add <nombre-archivo> ```
        ``` git commit -m "FRONT-1000: WIP <comentario-en-ingles>" ``` 
        
        FRONT-1000 -> El código de la tarea
        WIP -> WORK IN PROGRESS se pone solo si la tarea no se ha terminado 

    - Cuando terminemos nuestra tarea hacemos el último commit
    - Cambiamos a la rama Master 
        
        ``` git checkout FRONT-1000-Main ```
        ``` git reset --hard HEAD ```
        ``` git pull ```

        Con esto lo que hacemos es bajarnos los cambios que haya de otros compañeros que ya estén arriba mergeados en esta rama.
        Creo que es mejor hacer un merge de esta rama sobre la nuestra para poder resolver los conflictos de forma local, es mucho mejor.
        
            ``` git checkout <nuestra-rama> ```
            ``` git merge <rama-epica> ```
        
        Cuando hacemos merge puede que haya conflictos y nos lo indica git. Si eso pasa y lo suyo es hablar con la persona que haya hecho los cambios para poder solucionar los conflictos. 
        Si os parece las primeras veces hasta que veamos todos cómo se hace me podéis preguntar y lo hacemos juntos para ver la dinámica.

    - Una vez tenemos nuestra rama lista hay que hacer push para subirlo a github
        
        ``` git push ```
        
        Si es la primera vez os indicará que teneis que usar un comando más completo para crear la rama en github. 
        Copiais lo que os sugiere y lanzais esa instrucción

    - Cuando finalice el push ya tendremos la rama en github



## En github

    - No situamos en el repo sobre el que hemos hecho el push
    - Buscamos nuestra rama en Branches
    - Justo al lado vamos va ver un botón para crear el pull request
    - Hacemos click sobre él
    - Dentro de ahí podemos revisar los cambios que hemos hecho para comprobar que nos hemos olviado algún comentario no deseado o algo que se nos haya escapado.
    - Tened cuidado de qué rama vamos a partir y a qué rama vamos a hacer el PR, en principio la haremos sobre la Main. 
    - Una vez está todo listo
    - Pulsamos el botón para crear el pull request

    - Hay una opción Pull requests que es dónde se quedan todos los PR pendientes de revisión. 
    - Con otro compañero revisamos el PR 
    - Cuando esté todo OK hacemos el merge 
    - Ya habriamos terminado
    - Volvemos a empezar

    


