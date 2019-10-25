<h2> How to install </h4>

`composer require skytrex/ci-dompdf 0.0.4`
<br>
-<b>versioning is depends on the release </b>
<hr>
<h2> How to use this with Codeigniter 3 </h4>

<h4>1. Create a pdf.php file in folder <b> application/libraries/pdf.php </b> </h4> 

```
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

<h4>2. Add pdf.php to your <b> application/autoload </b> and add file to your helper </h4>

```

$autoload['libraries'] = array('pdf');

$autoload['helper'] = array('file');

```

<h4>3. Change <b>composer autoload</b> in <b>config.php</b> to below. </h4>

```

$config['composer_autoload'] = FCPATH .'vendor/autoload.php';

```

<h4>4. Enjoy!! </h4>
