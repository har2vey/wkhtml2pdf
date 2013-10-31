wkhtml2pdf
==========
Version 1.0 - Laravel 4 - Html to PDF Composer Package

#Usage#

		MODE_DOWNLOAD = 'D';              // Force the client to download PDF file
        MODE_STRING = 'S';                // Returns the PDF file as a string
        MODE_EMBEDDED = 'I';              // When possible, force the client to embed PDF file
        MODE_SAVE = 'F';                  // PDF file is saved on the server. The path+filename is returned.

    PDF::url('I', 'http://www.anywebsite.com'); // Generate Pdf from web url

    PDF::html('I', 'hello'); // Return a PDF in browser generated from laravel view/hello.php

    PDF::html('I', 'hello',array('data' => $data)); // Return a PDF from view/hello.php with added parameters

    PDF::html('D', 'hello',array('message' => 'hello'), 'myFile'); // Return a PDF download dialog named myFile.pdf from view/hello.php with added parameters 

    PDF::save('hello',array('message' => 'hello'), '../app/storage/pdf/hello.pdf'); // Saving pdf without output (Mode is not applicable)

## Quick start

### Required setup

In the `require` key of `composer.json` file add the following

    "nitmedia/wkhtml2pdf": "dev-feature"
To use the forked branch add the following in the `repositories` key

	"repositories": [
        {
          "type": "vcs",
          "url": "https://github.com/har2vey/wkhtml2pdf"
        }
    ],

Run the Composer update comand

    $ composer update

In your `config/app.php` add `'Nitmedia\Wkhtml2pdf\Wkhtml2pdfServiceProvider'` to the end of the `$providers` array

    'providers' => array(

        'Illuminate\Foundation\Providers\ArtisanServiceProvider',
        'Illuminate\Auth\AuthServiceProvider',
        ...
        'Nitmedia\Wkhtml2pdf\Wkhtml2pdfServiceProvider',

    ),

At the end of `config/app.php` add `'PDF'    => 'Nitmedia\Wkhtml2pdf\Facades\Wkhtml2pdf'` to the `$aliases` array

    'aliases' => array(

        'App'        => 'Illuminate\Support\Facades\App',
        'Artisan'    => 'Illuminate\Support\Facades\Artisan',
        ...
        'PDF'    => 'Nitmedia\Wkhtml2pdf\Facades\Wkhtml2pdf',

    ),

## Configuration
Please set the driver file accoridng to the current OS, Supported drivers include: mac osx, linux 32, linux 64

    php artisan config:publish nitmedia/wkhtml2pdf
    
### Driver types

	wkhtmltopdf-0.9.9-OS-X.i368
	wkhtmltopdf-amd64
	wkhtmltopdf-i386
    
## Troubleshooting
	**There is a debug flag in config where you can test the output of the drivers.**

	1. Some users have noted a strange permissions issue executing the drivers. Try chmod'ing the driver files to solve the issue.
	2. All asset urls must be absolute, relative urls wont work.


The MIT License (MIT)

Copyright (c) <2013> <Nithin Meppurathu>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
