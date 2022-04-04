## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`

## El metodo withoutExceptionHandling, desactiva la excepción que esta atrapando el test, de esta manera podemos ver los errores de una manera mas comoda, entendible para ir implementando lo que nos hace falta.

`$this->withoutExceptionHandling();`

### Codigo test method GET:

```php
    use RefreshDatabase;

    /** @test */
    public function una_lista_de_posts_pueden_ser_recuperados()
    {
        $this->withoutExceptionHandling();

        $posts = Post::factory(3)->create(); //creamos datos de prueba

        $response = $this->get('post'); //Llamo a la ruta post con el metodo get

        $response->assertOk(); //verificamos que la respuesta sea 200

        $posts = Post::all(); //Traemos todos los datos ya creados en el factory de arriba

        $response->assertViewIs('posts.index'); //La  respuesta de la vista es la carpeta posts con el archivo index

        $response->assertViewHas('posts', $posts); //Si la vista tiene el parametro Post, con los datos recien creados
    }
```
