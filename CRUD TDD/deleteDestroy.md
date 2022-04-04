## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`

## El metodo withoutExceptionHandling, desactiva la excepción que esta atrapando el test, de esta manera podemos ver los errores de una manera mas comoda, entendible para ir implementando lo que nos hace falta.

`$this->withoutExceptionHandling();`

### Codigo test method DELETE, eliminar un recurso:

```php
    /** @test */
    public function a_post_can_be_destroy()
    {
        $this->withoutExceptionHandling(); //Deshabilitamos los errores

        $post = Post::factory()->create(); //Creamos una elemento

        $response = $this->delete('post/' . $post->id); //Solicitamos la ruta delete POST

        $this->assertCount(0, Post::all()); //Si hay 0 registros en la base de datos significa que ya no hay nada

        $response->assertRedirect('post'); //Redirigimos a nuestra vista de POST
    }
```
