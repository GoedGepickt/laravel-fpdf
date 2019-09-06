# Laravel 6 package for Fpdf

[![Latest Stable Version](https://poser.pugx.org/codedge/laravel-fpdf/v/stable?format=flat-square)](https://packagist.org/packages/codedge/laravel-fpdf)
[![Total Downloads](https://poser.pugx.org/codedge/laravel-fpdf/downloads?format=flat-square)](https://packagist.org/packages/codedge/laravel-fpdf)
[![StyleCI](https://styleci.io/repos/59506451/shield)](https://styleci.io/repos/59506451)
[![License](https://poser.pugx.org/codedge/laravel-fpdf/license?format=flat-square)](https://packagist.org/packages/codedge/laravel-fpdf)

This repository implements a simple [ServiceProvider](https://laravel.com/docs/master/providers)
that creates a singleton instance of the Fpdf PDF library - easily accessible via a [Facade](https://laravel.com/docs/master/facades) in [Laravel 6](http://laravel.com).  

See [FPDF homepage](http://www.fpdf.org/) for more information about the usage.

## Installation using [Composer](https://getcomposer.org/)
```sh
$ composer require GoedGepickt/laravel-fpdf
```

## Usage

### Laravel >= 6.0
Enjoy the auto discovery feature. 

## Configuration (optional)
Run   
`php artisan vendor:publish --provider="Codedge\Fpdf\FpdfServiceProvider" --tag=config`  
to publish the configuration file to `config/fpdf.php`.  
  
Open this file and enter the correct page settings, if you do not want the defaults.

## Basic example

If you want to use the facade you can see a basic example here:

```php
// app/Http/routes.php | app/routes/web.php

Route::get('/', function () {

    Fpdf::AddPage();
    Fpdf::SetFont('Courier', 'B', 18);
    Fpdf::Cell(50, 25, 'Hello World!');
    Fpdf::Output();

});
```

Of course you can also inject the singleton instance via dependency injection. See an example here:

```php
// app/Http/routes.php | app/routes/web.php

Route::get('/', function (Codedge\Fpdf\Fpdf\Fpdf $fpdf) {

    $fpdf->AddPage();
    $fpdf->SetFont('Courier', 'B', 18);
    $fpdf->Cell(50, 25, 'Hello World!');
    $fpdf->Output();

});
```
