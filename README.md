wkhtml2pdf
==========
Version 1.0 - Laravel 4 - Html to PDF Composer Package

#Usage#

        MODE_DOWNLOAD = 'D';              // Force the client to download PDF file
        MODE_STRING = 'S';                // Returns the PDF file as a string
        MODE_EMBEDDED = 'I';              // When possible, force the client to embed PDF file
        MODE_SAVE = 'F';                  // PDF file is saved on the server. The path+filename is returned.
        
        PDF::url('I', 'http://google.com'); // Generate Pdf from web url

	return PDF::html('I', 'hello'); // Return a PDF in browser generated from laravel view/hello.php
	
	return PDF::html('I', 'hello',array('data' => $data)); // Return a PDF from view/hello.php with added parameters
	
	return PDF::html('D', 'hello',array('message' => 'hello'), 'myFile'); // Return a PDF download dialog named myFile.pdf from view/hello.php with added parameters 

        return PDF::save('hello',array('message' => 'hello'), '../app/storage/pdf/hello.pdf'); // Saving pdf without displaying (Mode is not applicable)
        

## Quick start

### Required setup

In the `require` key of `composer.json` file add the following

    "har2vey/wkhtml2pdf": "dev-master"

Run the Composer update comand

    $ composer update

In your `config/app.php` add `'har2vey\Wkhtml2pdf\Wkhtml2pdfServiceProvider'` to the end of the `$providers` array

    'providers' => array(

        'Illuminate\Foundation\Providers\ArtisanServiceProvider',
        'Illuminate\Auth\AuthServiceProvider',
        ...
        'har2vey\Wkhtml2pdf\Wkhtml2pdfServiceProvider',

    ),

At the end of `config/app.php` add `'PDF'    => 'har2vey\Wkhtml2pdf\Facades\Wkhtml2pdf'` to the `$aliases` array

    'aliases' => array(

        'App'        => 'Illuminate\Support\Facades\App',
        'Artisan'    => 'Illuminate\Support\Facades\Artisan',
        ...
        'PDF'    => 'har2vey\Wkhtml2pdf\Facades\Wkhtml2pdf',

    ),

## Configuration
Please set the driver file according to the current OS, Supported drivers include: mac osx, linux 32, linux 64

	wkhtmltopdf-0.9.9-OS-X.i368 //mac os
	wkhtmltopdf-amd64 //linux 64bit
	wkhtmltopdf-i386 //linux 32bit
    
## Troubleshooting
	**There is a debug flag in config where you can test the output of the drivers.**

	1. Upon encountering permissions issue during execution of the drivers, try updating the ownership and permission of the driver files to solve the issue.
	2. All asset urls must be absolute, relative urls will not work.

