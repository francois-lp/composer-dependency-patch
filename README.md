## Composer dependency patch
*Patch of "symfony/var-dumper" in order to change display of dd() function*
<br/>*POC using composer extra patches*

## Installation

__Requirements__
```
    - PHP (>= 8.0.0)
    - Composer (>= 2.1.8)
```

__Project__
```
    $ git clone https://github.com/francois-lp/composer-dependency-patch
    $ cd composer-dependency-patch
    $ composer install
```

## Getting started
```
    Open file index.php in a browser
```

## Notes
__Patching steps__
1. Patch creation *(difference between original file and modified file)*
```shell
    diff -u vendor/symfony/var-dumper/Dumper/HtmlDumper_ORIGINAL.php vendor/symfony/var-dumper/Dumper/HtmlDumper.php > patches/var-dumper.patch
```
2. Patch manual modification *(add prefix letter to files paths and rename modified filename by the original)*
```
    --- a/vendor/symfony/var-dumper/Dumper/HtmlDumper.php	2021-10-24 19:50:48.000000000 +0200
    +++ b/vendor/symfony/var-dumper/Dumper/HtmlDumper.php	2021-10-24 19:50:52.000000000 +0200
```
3. Patch addition into composer.json
```json
    "extra": {
        "patches": {
            "symfony/var-dumper": {
                "Change color of the strings": "patches/var-dumper.patch"
            }
        }
    }
```
4. Patch application
```
    composer update symfony/var-dumper
```

## Links
* [Comment patcher une dépendance composer](https://www.youtube.com/watch?v=FyeUf5SDSCc)
