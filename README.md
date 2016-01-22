# Recetas Git Flow

Guías para las tareas más comunes en git-flow.

## Tabla de Contenido

* [Git Flow en un nuevo repositorio](#git-flow-en-un-nuevo-repositorio)
* [Git Flow en un repositorio ya existente](#git-flow-en-un-repositorio-ya-existente)
* [Git Flow en un repositorio recién clonado](#git-flow-en-un-repositorio-recién-clonado)
* [Git Flow en un repositorio recién clonado y con git flow ya trabajado](#git-flow-en-un-repositorio-recién-clonado-y-con-git-flow-ya-trabajado)
* [Realizar un release](#realizar-un-release)
* [Realizar un hotfix](#realizar-un-hotfix)
* [Realizar un feature](#realizar-un-feature)


## Git Flow en un nuevo repositorio

Para iniciar **git flow** en un nuevo repositorio seguimos los siguientes pasos:

Con la terminal en el directorio de nuestro repositorio.

1. Iniciamos el repositorio de la manera habitual.
```
$ git init
```

2. Una vez iniciado el repositorio, iniciamos git flow.
```
$ git flow init
```

3. La terminal nos pedirá las configuraciones a utilizar (nombre del branch maestro, desarrollo, prefijo branch feature, etc.). La sugerencia aquí es dejar los valores por defecto, por lo que sólo será necesario presionar enter.
![git-flow-config-prompt](/img/git-flow-config-prompt.png)

¡Listo! Ya tenemos nuestro repositorio con git flow.

## Git Flow en un repositorio ya existente

Para iniciar git flow en un repositorio ya existen, es decir, con `git init` ya ejecutado, seguimos los siguientes pasos:

Con la terminal en el directorio de nuestro repositorio.

1. Ejecutamos el siguiente comando para inicializar git flow.
```
$ git flow init
```

2. La terminal nos pedirá las configuraciones a utilizar (nombre del branch maestro, desarrollo, prefijo branch feautre, etc.). La sugerencia aquí es dejar los valores por defecto, por lo que sólo será necesario presionar enter.

¡Listo! Ya tenemos nuestro repositorio con git flow.

## Git Flow en un repositorio recién clonado

Para iniciar git flow en un repositorio recién clonado seguimos los siguientes pasos:

Con la terminal en el directorio de nuestro repositorio.

1. Ejecutamos el siguiente comando para inicializar git flow.
```
$ git flow init
```

2. La terminal nos pedirá las configuraciones a utilizar (nombre del branch maestro, desarrollo, prefijo branch feautre, etc.). La sugerencia aquí es dejar los valores por defecto, por lo que sólo será necesario presionar enter.

¡Listo! Ya tenemos nuestro repositorio con git flow.


## Git Flow en un repositorio recién clonado y con git flow ya trabajado

Para iniciar git flow en un repositorio recién clocado y en el cual ya se había estado trabajando con git flow, seguimos los siguientes pasos:

Con la terminal en el directorio de nuestro repositorio.

1. Ejecutamos el siguiente comando para consultar todas las ramas del repositorio (remotas y locales).
```
$ git branch -a
```

2. Buscamos la rama con el nombre que comienza con el prefijo **remotes/origin/nombre-rama-develop** y el nombre de la rama correspondiente a develop (en caso de usar los valores por defector en la configuración de git flow este nombre seria **develop**.

3. Copiamos todo el nombre **remotes/origin/nombre-rama-develop** y ejecutamos el comando.
```
$ git checkout remotes/origin/nombre-rama-develop
```
Este comando nos moverá a la referencia de la rama remota de desarrollo.

4. Creamos una rama local con referencia a la rama de desarrollo del repositorio remoto.
```
$ git checkout -b develop
```
Este comando creara la rama local develop y nos moverás a ella.

5. Ejecutamos el siguiente comando para inicializar git flow.
```
$ git flow init
```

6. La terminal nos pedirá las configuraciones a utilizar (nombre del branch maestro, desarrollo, prefijo branch feautre, etc.). La sugerencia aquí es dejar los valores por defector, por lo que sólo será necesario presionar enter.

¡Listo! Ya tenemos nuestro repositorio con git flow.


## Realizar un release

Para realizar un release, seguimos los siguientes pasos:

Con la terminal en el directorio de nuestro repositorio y nuestra area de trabajo limpia.

1. Nos movemos a la rama local develop
```
$ git checkout develop
```

2. Bajamos los cambios del repositorio remoto de la rama develop
```
$ git pull origin develop
```

3. Nos movemos a la rama local master
```
$ git checkout master
```

4. Bajamos los cambios del repositorio remoto de la rama master
```
$ git pull origin master
```

5. Bajamos los tags de la repositorio remoto de la rama master
```
$ git fetch --tags
```

6. Consultamos los tags ya utilizados
```
$ git tag
```

7. Iniciamos el release
```
$ git flow release start *tag-de-versión-siguiente*
```

8. De ser necesario realizamos los cambios para el release

9. Cerramos el release
```
$ git flow release finish *tag-de-versión-siguiente*
```

10. Nos movemos a la rama local master
```
$ git checkout master
```

11. Subimos los cambios y tags a la rama remota master
```
$ git push origin master --tags
```

12. Nos movemos a la rama local develop
```
$ git checkout develop
```

13. Subimos los cambios a la rama remota develop
```
$ git push origin develop
```

¡Listo! Hemos completado el Release.


## Realizar un hotfix

Para realizar un hotfix, seguimos los siguientes pasos:

Con la terminal, en el directorio de nuestro repositorio y nuestra area de trabajo limpia.

1. Nos movemos a la rama local develop
```
$ git checkout develop
```

2. Bajamos los cambios del repositorio remoto de la rama develop
```
$ git pull origin develop
```

3. Nos movemos a la rama local master
```
$ git checkout master
```

4. Bajamos los cambios del repositorio remoto de la rama master
```
$ git pull origin master
```

5. Bajamos los tags de la repositorio remoto de la rama master
```
$ git fetch --tags
```

6. Consultamos los tags ya utilizados
```
$ git tag
```

7. Iniciamos el hotfix
```
$ git flow hotfix start *tag-de-versión-siguiente*
```

8. Realizamos los cambios para solucionar el problema

9. Hacemos commit de nuestros cambios
```
$ git add .
$ git commit
```

10. Cerramos el hotfix
```
$ git flow hotfix finish *tag-de-versión-siguiente*
```

10. Nos movemos a la rama local master
```
$ git checkout master
```

11. Subimos los cambios y tags a la rama remota master
```
$ git push origin master --tags
```

12. Nos movemos a la rama local develop
```
$ git checkout develop
```

13. Subimos los cambios a la rama remota develop
```
$ git push origin develop
```

¡Listo! Hemos completado el Hotfix.


## Realizar un feature

Para realizar un feature seguimos los siguientes pasos:

Con la terminal en el directorio de nuestro repositorio y nuestra área de trabajo limpia.

1. Nos movemos a la rama local develop (si no estamos en ella)
```
$ git checkout develop
```

2. Bajamos los cambios del repositorio remoto de la rama develop
```
$ git pull origin develop
```

3. Iniciamos el feature
```
$ git flow feature start *nombre-del-feature*
```
Recuerda que el *nombre-del-feature* puede ser el que nosotros elijamos.

4. Realizamos los cambios para nuestro feature

5. Hacemos commit de nuestros cambios
```
$ git add .
$ git commit
```

6. Cerramos el feature
```
$ git flow feature finish *nombre-del-feature*
```

7. Subimos al repositorio remoto en la rama develop
```
$ git push origin develop
```

¡Listo! Hemos competado el feature.