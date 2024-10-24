This block of code extracts the year, month and the extension of a filename. This is useful when for instance you have a lot of files mixed in one folder (images and videos taken over many years), and you want to organize them in their specific `./year/month/` folder. This regular expression applies for any image/video filename having the year, month and day as part of the filename (for example: `...20210117....jpg`).

The `preg_match` function returns 1 if the pattern matches the given filename, and the results of the regex search are saved in the variable `$matches`.

```php
<?php

$img_filename = 'IMG_20210117_211140121.jpg';

$pattern = '/[A-Za-z0-9\-\_]*(20\d{2})(\d{2})\d{2}[A-Za-z0-9\-\_\(\)\~]*\.(jpg|jpeg|png|gif|3gp|mp4)$/';

if (preg_match($pattern, $img_filename, $matches)) {
    print_r($matches);
}

/* Output:
-------------------------------------
Array
(
    [0] => IMG_20210117_211140121.jpg
    [1] => 2021
    [2] => 01
    [3] => jpg
)
-------------------------------------
*/
```

And this is an example with a video filename:

```php
<?php

$vid_filename = 'VID_20191004_201304730.mp4';

$pattern = '/[A-Za-z0-9\-\_]*(20\d{2})(\d{2})\d{2}[A-Za-z0-9\-\_\(\)\~]*\.(jpg|jpeg|png|gif|3gp|mp4)$/';

if (preg_match($pattern, $vid_filename, $matches)) {
    print_r($matches);
}

/* Output:
-------------------------------------
Array
(
    [0] => VID_20191004_201304730.mp4
    [1] => 2013
    [2] => 04
    [3] => mp4
)
-------------------------------------
*/
```