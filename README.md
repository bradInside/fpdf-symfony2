FPDF for use with Symfony2
==========================

[![Latest Stable Version](https://poser.pugx.org/royopa/fpdf-symfony2/v/stable.svg)](https://packagist.org/packages/royopa/fpdf-symfony2) [![Total Downloads](https://poser.pugx.org/royopa/fpdf-symfony2/downloads.svg)](https://packagist.org/packages/royopa/fpdf-symfony2) [![Latest Unstable Version](https://poser.pugx.org/royopa/fpdf-symfony2/v/unstable.svg)](https://packagist.org/packages/royopa/fpdf-symfony2) [![License](https://poser.pugx.org/royopa/fpdf-symfony2/license.svg)](https://packagist.org/packages/royopa/fpdf-symfony2)

Uses FPDF 1.7, tested in Symfony 2.5+

## Instalation and Usage 

Package available on [Composer](https://packagist.org/packages/royopa/fpdf-symfony2).

If you're using Composer to manage dependencies, you can use

    $ composer require "royopa/fpdf-symfony2": "dev-master"

Or

You can include the following in your composer.json file:

```json
{
    "require": {
        "royopa/fpdf-symfony2": "dev-master"
    }
}
```

Setup
-----

And those to `app/autoload.php`:

```php
$classMap = array(
    'FPDF_' => __DIR__.'/../vendor/royopa/fpdf-symfony2/lib/FPDF/FPDF.php',
    'FPDI_' => __DIR__.'/../vendor/royopa/fpdf-symfony2/lib/FPDF/FPDI.php'
);
$loader->addClassMap($classMap);    
```

Usage
-----
```php
class WelcomeController extends Controller
{
    public function indexAction()
    {
        $pdf  = new \FPDF_FPDF();
        $pdi  = new \FPDF_FPDI();

        $pdf->AddPage();
        $pdf->SetFont('Arial','B',16);
        $pdf->Cell(40,10,'Hello World!');
        $pdf->Output();
    }
}

```

FPDF
-----
FPDF is a PHP class which allows to generate PDF files with pure PHP, that is to say without using the PDFlib library. FPDF is a open source project: you may use it for any kind of usage and modify it to suit your needs.

- http://www.fpdf.org/

On the fpdf homepage you will find links to the documentation, forums and so on.



Example
-------

See my `app/autoload.php`:

```php
<?php

use Doctrine\Common\Annotations\AnnotationRegistry;
use Composer\Autoload\ClassLoader;

/**
 * @var ClassLoader $loader
 */
$loader = require __DIR__.'/../vendor/autoload.php';

AnnotationRegistry::registerLoader(array($loader, 'loadClass'));

$classMap = array(
    'FPDF_' => __DIR__.'/../vendor/royopa/fpdf-symfony2/lib/FPDF/FPDF.php',
    'FPDI_' => __DIR__.'/../vendor/royopa/fpdf-symfony2/lib/FPDF/FPDI.php'
);
$loader->addClassMap($classMap);

return $loader;

```

And My Controller:

```php
<?php

namespace Acme\DemoBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;

class WelcomeController extends Controller
{
    public function indexAction()
    {
        $pdf  = new \FPDF_FPDF();
        $pdi  = new \FPDF_FPDI();

        //my code...
    }
}

```
