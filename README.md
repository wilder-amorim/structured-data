# Structured Data @ElePHPant

[![Maintainer](http://img.shields.io/badge/maintainer-@wilderamorim-blue.svg?style=flat-square)](https://twitter.com/WilderAmorim)
[![Maintainer](http://img.shields.io/badge/maintainer-@sergiodanilojr-blue.svg?style=flat-square)](https://twitter.com/sergiodanilojr)
[![Source Code](http://img.shields.io/badge/source-wilderamorim/structured-data-blue.svg?style=flat-square)](https://github.com/wilderamorim/structured-data)
[![PHP from Packagist](https://img.shields.io/packagist/php-v/elephpant/structured-data.svg?style=flat-square)](https://packagist.org/packages/elephpant/structured-data)
[![Latest Version](https://img.shields.io/github/release/wilderamorim/structured-data.svg?style=flat-square)](https://github.com/wilderamorim/structured-data/releases)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)
[![Build](https://img.shields.io/scrutinizer/build/g/wilderamorim/structured-data.svg?style=flat-square)](https://scrutinizer-ci.com/g/wilderamorim/structured-data)
[![Quality Score](https://img.shields.io/scrutinizer/g/wilderamorim/structured-data.svg?style=flat-square)](https://scrutinizer-ci.com/g/wilderamorim/structured-data)
[![Total Downloads](https://img.shields.io/packagist/dt/elephpant/structured-data.svg?style=flat-square)](https://packagist.org/packages/elephpant/structured-data)

###### Structured Data (schema.org) is a set of extensible schemas makes it easier for webmasters and developers to embed  structured data on their web pages for use by search engines and other applications.

Dados estruturados (schema.org) é um conjunto de esquemas extensíveis que facilita para webmasters e desenvolvedores incorporar dados estruturados em suas páginas da web para serem usados por mecanismos de pesquisa e outros aplicativos.

### Highlights

- Simple installation (Instalação simples)
- Composer ready and PSR-2 compliant (Pronto para o composer e compatível com PSR-2)

## Installation

Structured Data is available via Composer:

```bash
"elephpant/structured-data": "dev-master"
```

or run

```bash
composer require elephpant/structured-data:dev-master
```

## Documentation

###### For details on how to use, see a sample folder in the component directory. In it you will have an example of use for each class. It works like this:

Para mais detalhes sobre como usar, veja uma pasta de exemplo no diretório do componente. Nela terá um exemplo de uso para cada classe. Ele funciona assim:

#### Start Web Page:

```php
<?php
require __DIR__ . "/../vendor/autoload.php";
use ElePHPant\StructuredData\WebPage;

$webPage = new WebPage();
$webPage->start(
    'Wayne Enterprises, Inc.',
    'Wayne Enterprises is a big, growing multinational company',
    'https://www.yourdomain.com/wayne-enterprises.jpg',
    'https://www.dccomics.com',
    'en-US'
);
$webPage->isPartOf(
    'https://www.yourdomain.com/logo.png',
    'https://www.yourdomain.com/logo.png'
);
$webPage->about(
    'https://www.yourdomain.com/logo.png'
);
$webPage->creator(
    'https://www.yourdomain.com/logo.png',
    'Gotham City',
    'DC',
    '12345-678',
    '1007 Mountain Drive',
    'Bruce Wayne',
    'https://gravatar.com/avatar', [
        'https://www.facebook.com/zuck',
        'https://www.instagram.com/zuck'
    ]
);
```

#### BlogPosting:

```php
<?php
require __DIR__ . "/../vendor/autoload.php";
use ElePHPant\StructuredData\BlogPosting;

/**
 * SINGLE POST EXAMPLE
 */
$post = new \stdClass();
$post->title = "It's not who I am underneath but what I do that defines me.";
$post->slug = "it-s-not-who-i-am-underneath-but-what-i-do-that-defines-me";
$post->subtitle = "Bruce Wayne, eccentric billionaire. No guns, no killing. Swear to me! I'm Batman";
$post->content = "<h3>I'm Batman</h3><p>Bats frighten me.</p><p>It's time my enemies shared my dread.</p>";
$post->post_date = "2020-12-30";
$post->post_modified = "2020-12-31";
$post->cover = "images/2020/12/it-s-not-who-i-am-underneath-but-what-i-do-that-defines-me.jpg";

/**
 * Schema: BlogPosting
 * @link https://schema.org/BlogPosting
 */
$blogPosting = new BlogPosting($webPage);
$blogPosting->start($post->title, $post->subtitle, $post->content, $post->post_date, $post->post_modified);
$blogPosting->image("https://www.yourdomain.com/storage/{$post->cover}");
$blogPosting->mainEntityOfPage("https://www.yourdomain.com/blog/{$post->slug}");
$blogPosting->publisher('https://www.yourdomain.com/logo.png');
$blogPosting->author('Bruce Wayne', 'https://gravatar.com/avatar', [
    'https://www.facebook.com/zuck',
    'https://www.instagram.com/zuck'
]);
```

##### Render JSON:

```php
<?php echo $blogPosting->render(); // {"@context":"http://schema.org","@type": ...
```

##### Render JSON-LD auto script tag:

```php
<?php echo $blogPosting->render(true); // <script type="application/ld+json">{"@context":"http://schema.org","@type": ... </script>
```

##### Render JSON manually script tag:

```html
<script type="application/ld+json">
    <?= $blogPosting->render(); ?> // {"@context":"http://schema.org","@type": ...
</script>
```

##### Debug:

```php
<?php $blogPosting->debug();
```

## Contributing

Please see [CONTRIBUTING](https://github.com/wilderamorim/structured-data/blob/master/CONTRIBUTING.md) for details.

## Support

###### Security: If you discover any security related issues, please email agencia@uebi.com.br instead of using the issue tracker.

Se você descobrir algum problema relacionado à segurança, envie um e-mail para agencia@uebi.com.br em vez de usar o rastreador de problemas.

Thank you

## Credits

- [Wilder Amorim](https://github.com/wilderamorim) (Developer)
- [Sérgio Danilo Jr.](https://github.com/sergiodanilojr) (Developer)
- [Agência Uebi](https://www.uebi.com.br) (Team)
- [All Contributors](https://github.com/wilderamorim/structured-data/contributors) (This Rock)

## License

The MIT License (MIT). Please see [License File](https://github.com/wilderamorim/structured-data/blob/master/LICENSE) for more information.