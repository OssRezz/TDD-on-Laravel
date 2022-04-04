## use RefreshDatabase nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica

`use RefreshDatabase;`

## Es importante poner el comentario de @test de esta manera php sabrá que es un test

`/** @test */`

## El metodo withoutExceptionHandling, desactiva la exepcion que esta atrapando el test, de esta manera podemos ver los errores.

`$this->withoutExceptionHandling();`

### Codigo test:

`/** @test */`

`public function a_post_can_be_created()`  
`{`

`$this->withoutExceptionHandling();`

` $response = $this->post('post', [`  
` 'title' => 'Test title',`  
` 'content' => 'Test content',`  
` ]);`

` $response->assertOk(); //Si la respuesta esta bien`  
` $this->assertCount(1, Post::all());`

` $post = Post::first();`

` $this->assertEquals($post->title, 'Test title');`  
` $this->assertEquals($post->content, 'Test content');`  
`}`