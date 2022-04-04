```php
<?php

namespace Tests\Feature;

use App\Models\Post;
use Illuminate\Foundation\Testing\RefreshDatabase;
use Tests\TestCase;

class BlogManagmentTest extends TestCase
{
    //Este use nos ayuda a ejecutar migraciones antes de ejecutar un test, de esta manera lo hará de forma automatica
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

    /** @test */
    public function un_dato_puede_recuperarse()
    {
        $this->withoutExceptionHandling();

        $posts = Post::factory()->create();


        $response = $this->get('post/' . $posts->id);

        $response->assertOk();

        $post = Post::first();

        $response->assertViewIs('posts.show');

        $response->assertViewHas('post', $post);
    }

    /** @test */
    public function a_post_can_be_created()
    {
        //Desactiva la exepcion que esta atrapando el test
        $this->withoutExceptionHandling();

        $response = $this->post('post', [
            'title' => 'Test title',
            'content' => 'Test content',
        ]);

        $this->assertCount(1, Post::all());

        $post = Post::first();

        $this->assertEquals($post->title, 'Test title');
        $this->assertEquals($post->content, 'Test content');

        $response->assertRedirect('post/' . $post->id);
    }

    /** @test */
    public function a_post_can_be_update()
    {
        //Desactiva la exepcion que esta atrapando el test
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

    /** @test */
    public function a_post_can_be_destroy()
    {
        $this->withoutExceptionHandling(); //Deshabilitamos los errores

        $post = Post::factory()->create(); //Creamos una elemento

        $response = $this->delete('post/' . $post->id); //Solicitamos la ruta delete POST

        $this->assertCount(0, Post::all()); //Si hay 0 registros en la base de datos significa que ya no hay nada

        $response->assertRedirect('post'); //Redirigimos a nuestra vista de POST
    }
}
```
