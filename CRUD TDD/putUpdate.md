## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`

## El metodo withoutExceptionHandling, desactiva la excepción que esta atrapando el test, de esta manera podemos ver los errores de una manera mas comoda, entendible para ir implementando lo que nos hace falta.

`$this->withoutExceptionHandling();`

### Codigo test method PUT, actualizar un recurso:

```php
    /** @test */
    public function a_post_can_be_update()
    {
        $this->withoutExceptionHandling();

        $post = Post::factory()->create();

        $response = $this->put('post/' . $post->id, [
            'title' => 'Test title',
            'content' => 'Test content',
        ]);

        $this->assertCount(1, Post::all());

        $post = $post->fresh();

        $this->assertEquals($post->title, 'Test title');
        $this->assertEquals($post->content, 'Test content');

        $response->assertRedirect('post/' . $post->id);
    }
```
