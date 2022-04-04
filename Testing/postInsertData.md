## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`

## El metodo withoutExceptionHandling, desactiva la excepción que esta atrapando el test, de esta manera podemos ver los errores de una manera mas comoda, entendible para ir implementando lo que nos hace falta.

`$this->withoutExceptionHandling();`

### Codigo test method Post:

```php
    use RefreshDatabase;
    /** @test */
    public function a_post_can_be_created()
    {
        $this->withoutExceptionHandling();

        $response = $this->post('post', [
            'title' => 'Test title',
            'content' => 'Test content',
        ]);

        $response->assertOk(); //Si la respuesta esta bien = 200
        $this->assertCount(1, Post::all());

        $post = Post::first();

        $this->assertEquals($post->title, 'Test title');
        $this->assertEquals($post->content, 'Test content');
    }
```
