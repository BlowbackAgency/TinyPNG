# Tinify PHP client for ProcessWire

__Hooks TinyPNG on the fly image compression to ProcessWire__

Get your API key at [TinyPNG Developer page](https://tinypng.com/developers). This module connects to API by [Tinify PHP client](https://tinypng.com/developers/reference/php).

## Usage

### Using manually

This module adds new `$image->tinify()` method to the Pageimage object:

```php
$image = $page->images->first()->tinify();
echo "<img src='{$image->url}' alt='{$image->description}' />";
```

Behind the scenes image is copied and compressed. As a succesful result tiny variation of Pageimage is returned:

```html
<img src='/site/assets/files/1/my_image.-tiny.jpg' alt='My description' />
```

### Automatically on `$image->size()`

Resized variations can be automatically compressed by enabling auto mode at module config page.

```php
$image = $page->images->first()->size(200,200);
echo "<img src='{$image->url}' alt='{$image->description}' />";
```

```html
<img src='/site/assets/files/1/my_image.200x200-tiny.jpg' alt='My description' />
```

## Module config options

Name       | Type   | Default | Description
---------- | ------ | ------- | -----------
`apikey`   | string | ``      | TinyPNG developer API key (required).
`logging`  | int    | `1`     | Log compression data (1=true, 0=false).
`limit`    | int    | `500`   | Monthly compression usage limit (zero or empty for no limit).
`auto`     | int    | `0`     | Auto mode (1=true, 0=false). Compress automatically `$image->size()` resized variations.
`sizes`    | string | ``      | Ignored sizes at auto mode. Separate width/height by colon and sizes by pipe (200,200|960,0|0,320).

## Contribute

Please report any bugs or enhancements as [opening new issue](.issues). If you find this module useful, you can always support our work by making a small [donation](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=WB4BHJ8HS8U8Q). Thanks!

## License

This software is licensed under the MIT License (MIT). [View the license](./LICENSE.md).
