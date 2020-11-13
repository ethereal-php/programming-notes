
To make the terminal send characters immediately to your program without line-buffering,
you need to set the terminal to "non-canonical" mode. This disables any line-editing features,
such as the ability to press <kbd>backspace</kbd> to erase characters, and instead sends characters to the 
input buffer immediately. The easiest way to do this in PHP is to call the Unix utility `stty`.

```php
# lang: php
system("stty -icanon");
echo "\033[6n";
$stdin = fread(STDIN, 16);
var_dump($stdin);
```
