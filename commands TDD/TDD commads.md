# Comandos Laravel TDD

### Peticiones de rutas

#### get

`$response = $this->get('post');`

#### post

```php
 $response = $this->post('post', [
            'title' => 'Test title',
            'content' => 'Test content',
        ]);
```

### assertOk

`$response->assertOk();` Si la respuesta tiene el codigo de estatus 200

### assertStatus

`$response->assertStatus(200);` Si la respuesta tiene el codigo de estatus 200

### assertViewIs

`$response->assertViewIs('posts.index');` If the return of the controller has the view index in the folder posts

### assertViewHas

If the view has posts parameter in the return.

```php
$posts = Post::factory(3)->create();
$posts = Post::all();
$response->assertViewHas('posts', $posts);
```

### assertRedirect

`$response->assertRedirect('post/' . $post->id);` Nos redirige a una vista

### assertSessionHasErrors

Si la sesion tiene un error, va a devolver true. Esto nos sirve para validar errores.

```php
        $response = $this->post('post', [
            'title' => 'Esto es un titulo',
            'content' => '',
        ]);

        $response->assertSessionHasErrors(['content']);
```
