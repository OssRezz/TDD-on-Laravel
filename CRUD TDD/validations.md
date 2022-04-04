## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`


### Codigo test method GET, retornar solo un dato:

```php
    /** @test */
    public function a_title_is_required()
    {
        // $this->withoutExceptionHandling();

        $response = $this->post('post', [
            'title' => '',
            'content' => 'Esto es un contenido',
        ]);

        $response->assertSessionHasErrors(['title']);F
    }

    /** @test */
    public function a_content_is_required()
    {
        //Deshabilitamos el catch para que nos atrape el error
        // $this->withoutExceptionHandling();

        $response = $this->post('post', [
            'title' => 'Esto es un titulo',
            'content' => '',
        ]);

        $response->assertSessionHasErrors(['content']);
    }
```
