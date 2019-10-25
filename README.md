# ci-dompdf
[![Latest Stable Version](https://poser.pugx.org/skytrex/ci-dompdf/v/stable)](https://packagist.org/packages/skytrex/ci-dompdf)
[![Total Downloads](https://poser.pugx.org/skytrex/ci-dompdf/downloads)](https://packagist.org/packages/skytrex/ci-dompdf)
[![Latest Unstable Version](https://poser.pugx.org/skytrex/ci-dompdf/v/unstable)](https://packagist.org/packages/skytrex/ci-dompdf)
[![License](https://poser.pugx.org/skytrex/ci-dompdf/license)](https://packagist.org/packages/skytrex/ci-dompdf)
## How to install 

    composer require skytrex/ci-dompdf 0.0.4

**versioning is depends on the release**

------
## How to use this with Codeigniter 3.
------

#### 1. Create a pdf.php file in folder **application/libraries/pdf.php**.

```php
<?php
defined('BASEPATH') OR exit('No direct script access allowed');

require_once("./vendor/skytrex/ci-dompdf/autoload.inc.php");

use Dompdf\Dompdf;

class pdf {

  public function generate($html, $filename='', $stream=TRUE, $paper = 'A4', $orientation = "portrait")
  {
    $dompdf = new DOMPDF();
    $dompdf->loadHtml($html);
    $dompdf->setPaper($paper, $orientation);
    $dompdf->render();
    if ($stream) {
        $dompdf->stream($filename.".pdf", array("Attachment" => 0));
    } else {
        return $dompdf->output();
    }
  }
}
```

#### 2. Add pdf.php to your **application/autoload** and add file to your helper.

```php
$autoload['libraries'] = array('pdf');

$autoload['helper'] = array('file');
```

#### 3. Change **composer autoload** in <b>config.php</b> to below.

```php
$config['composer_autoload'] = FCPATH .'vendor/autoload.php';
```

#### 4. Enjoy!!
