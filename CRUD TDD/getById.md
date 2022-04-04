## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`

## El metodo withoutExceptionHandling, desactiva la excepción que esta atrapando el test, de esta manera podemos ver los errores de una manera mas comoda, entendible para ir implementando lo que nos hace falta.

`$this->withoutExceptionHandling();`

### Codigo test method GET, retornar solo un dato:

```php
    /** @test */
    public function un_dato_puede_recuperarse()
    {
        $this->withoutExceptionHandling();

        $posts = Post::factory()->create();

        $response = $this->get('post/' . $posts->id);

        $response->assertOk();

        $post = Post::find($posts->id);

        $response->assertViewIs('posts.show');

        $response->assertViewHas('post', $post);
    }
```
