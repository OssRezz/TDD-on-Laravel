# Comandos Laravel TDD

### Peticiones de rutas

#### get

`$response = $this->get('post');`

#### post

````php
 $response = $this->post('post', [
            'title' => 'Test title',
            'content' => 'Test content',
        ]);
```

### assertOk

`$response->assertOk();` Si la respuesta tiene el codigo de estatus 200

### assertViewIs

`$response->assertViewIs('posts.index');` If the return of the controller has the view index in the folder posts

# Documentacion de testing en laravel:

[Documentacion](https://laravel.com/docs/4.2/testing)
