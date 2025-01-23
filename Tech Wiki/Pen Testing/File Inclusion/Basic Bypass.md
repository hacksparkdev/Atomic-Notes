References:[ URL Encoding Reference](https://www.eso.org/~ndelmott/url_encode.html)
Tags: [[File Inclusion]] [[Cybersecurity]] [[Hack The Box]] #BasicBypass

There are some basic basic filter that can be used to stop from using `../` 

```php
$language = str_replace('../', '', $_GET['language']);
```

To bypass this filter we can use `..//` the extra `/` will trick the filter so we can traverse the path.  We could also use `....///`.

Sometime the filter will stop the use of certain character like `.` or `/`. In this case we can use url encoding to hide the characters. To do this we could use `burpsuite`.

![[Pasted image 20250120123836.png|2000x500]]

