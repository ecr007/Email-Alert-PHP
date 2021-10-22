# Email Alert PHP

```php
/**
 * 
 * Funcion para reportar errores via correo electronico.
 * 
 * @param String $subject
 * @param String $message
 * @param String $prioridad [error, warning, debug, info]
 * @return Void
 */
function sendAlert($subject,$message,$prioridad)
{
  $emails = [];

  $message = wordwrap($message, 70, "\r\n");

  if (ENV == 'local' ) {
    $logger = new Katzgrau\KLogger\Logger(PATH_ROOT.DS.'logs');
    $logger->debug($subject.' '.$prioridad.' '.$message.'; File => '.__FILE__.' Line => '.__LINE__);
  }else{
    @mail(implode(",", $emails), $subject.' Lv:'.$prioridad, $message);
  }
}
```
