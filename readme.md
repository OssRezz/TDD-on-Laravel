# TEST DRIVEN DEVELOPMENT ON LARAVEL

## Comando para crear un test:

-Es importante que al final del comando poner la palabra Test  
`-php artisan make:test NombreTest`

#### Test Feature

-Test de caracteristicas o funcionalidad, significa que un test largo, donde hay modelos interactuando
recurso, controladores, porciones largas de codigo.

#### Test unitario

-El unitesting podemos probar funciones pequeñas de nuestro codigo, como por ejm una query

`-php artisan make:test NombreTest --unit`

## Para correr todos los test

-Para correr todos los test de una clase usamos el sgt comando:  
No se utiliza la extension .php y en este ejemplo lo estamos corriendo desde la raiz del proyecto.

`vendor\bin\phpunit --filter BlogManagmentTest`

-Obtendremos como respuesta en la consola:  
El punto significa la cantidad de test que corrimos, este caso fueron 3, ... 3 test

```diff
...                                                                 3 / 3 (100%)

Time: 00:00.561, Memory: 30.00 MB

+OK (3 tests, 11 assertions)
```

## Para correr un solo test

-Una vez creado el archivo y clase del test podemos usar el nombre de la funcion para ejecutarlo

`vendor\bin\phpunit --filter a_post_can_be_created`

## TDD

### La idea de tdd es crear el test y en base a los errores que nos devuelve en la consola, Vamos creando la funcionalidad.

### En este caso nos dira que no existe el modelo, la ruta, la migracion, la tabla, la base de datos, el controlador, la funcion del contralador etc...

### 1) Escribimos la prueba

### 2) Ejecutamos

```diff
-Si sale en rojo, corregimos el error.
```

### 3) Implementamos funcionalidad

### 4) Ejecutamos

```diff
-Si sale en rojo, repetimos todos los pasos anteriores

+Si sale en verde pasamos al seguiente paso que es refactorizar
```

### 5) Refactorizacion de codigo

### Documentacion de testing en laravel:

[Documentacion about testing](https://laravel.com/docs/9.x/testing)  
[http documentacion testing](https://laravel.com/docs/9.x/http-tests)
