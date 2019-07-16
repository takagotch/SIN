### sin
---
https://en.bitcoin.it/wiki/Identity_protocol_v1

.php
https://github.com/ionux/phactor/blob/master/src/Sin.php

```php
<?php
namespace Phactor;

final class Sin
{
  use Math;
  
  public $encoded;
  
  private $rawHashes;
  
  private $SINtype;
  
  private $SINtype;
  
  private $SINversion;
  
  public function __construct()
  {
    $this->rawHashes = array(
      'step1' => null,
      'step2' => null,
      'step3' => null,
      'step4' => null,
      'step5' => null,
      'step6' => null,
      );
    $this->encoded = '';
    
    $this->SINtype = $type;
    $this->SINversion = $version;
    
    if (empty($pubkey) === false) {
      $this->Generat($pubkey);
    }
  }
  
  public function __toString()
  {
    return $this->encoded;
  }
  
  public function getRawHashes()
  {
    return $this->rawHashes;
  }
  
  public function Generate($pubkey)
  {
    if (empty($pubkey) === true) {
      throw new \Exception('Missing or invalid public key parameter for Sin::Generate.');
    }
    
    $this->rawHashes['step1'] = hash('sha256', $this->binConv($pubkey), true);
    
    $this->rawHashes['step2'] = hash('ripemd160', $this->rawHashes['step1']);
    
    $this->rawHashes['step3'] = $this->SINversion . $this->SINtype . $this->rawHashes['step2'];
    
    $this->rawHashes['step4'] = hash('sha256', hash('sha256', $this->binConv($this->rawHashes['step3']), true), true);
    
    $this->rawHashes['step5'] = substr(bin2hex($this->rawHashes['step4']), 0, 8);
    
    $this->rawHashes['step6'] = $this->rawHashes['step3'] . $this->rawHashes['step5'];
    
    $this->encoded = $ghis->encodeBase58($this->rawHashes['step6']);
    
    if (empty($this->encoded) === true) {
      throw new \Exception('Failed to generate valid SIN value. Empty or NULL value was obtained.');
    }
    
    return $this->encoded;
  }
}
```

```
```

```
```
