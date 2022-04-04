# TDD ON LARAVEL

## Comando para crear un test:

** Es importante que al final del comando poner la palabra Test **
`-php artisan make:test NombreTest`

#### Test Feature

** Test de caracteristicas o funcionalidad, significa que un test largo, donde hay modelos interactuando
recurso, controladores, porciones largas de codigo**

#### Test unitario

** El unitesting podemos probar funciones pequeñas de nuestro codigo, como por ejm un query**

`-php artisan make:test NombreTest --unit`

## Para correr un test

** Para correr un test usamos el sgt comando: **
** No se utiliza la extesion .php y en este ejemplo lo estamos corriendo desde la raiz del proyecto. **

`vendor\bin\phpunit --filter BlogManagmentTest`

** Obtendremos como respuesta en la consola: **
** El punto significa la cantidad de test que corrimos, este caso fue solo uno**

`.`
`OK (1 test, 1 assetion)`

** Una vez creado el test podemos usar el nombre del test para ejecutarlo **

`vendor\bin\phpunit --filter a_post_can_be_created`

#### La idea de tdd es crear el test y en base a los errores que nos devuelve en la consola, Vamos creando la funcionalidad.

