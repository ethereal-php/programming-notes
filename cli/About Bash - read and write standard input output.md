# About Bash - read and write standard input output

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

To solve the input echoing issue, we can add `-echo` to the stty arguments to disable input echoing in the terminal.
To reset the terminal to its state before we changed it, we can call `stty -g` to output a list of current terminal
settings which can be passed to stty later to reset the terminal.

```php

```
