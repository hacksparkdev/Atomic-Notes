Tags: [[File Inclusion]] [[Hack The Box]] [[Cybersecurity]] [[Penetration Testing]]

File inclusion happens when you have access to local server files from a function in the code the vulnerabilities happen to programming languages that have templating frameworks like. `php`, `NodeJS`, `Java`. 
When making a request to access a file by the templating agent we can intercept and use it to gain access to other files. Some of the functions we can use to read files some we can use to read and write. Here is a list of functions we can use and if we can read or write the files. 

|**Function**|**Read Content**|**Execute**|**Remote URL**|
|---|:-:|:-:|:-:|
|**PHP**||||
|`include()`/`include_once()`|✅|✅|✅|
|`require()`/`require_once()`|✅|✅|❌|
|`file_get_contents()`|✅|❌|✅|
|`fopen()`/`file()`|✅|❌|❌|
|**NodeJS**||||
|`fs.readFile()`|✅|❌|❌|
|`fs.sendFile()`|✅|❌|❌|
|`res.render()`|✅|✅|❌|
|**Java**||||
|`include`|✅|❌|❌|
|`import`|✅|✅|✅|
|**.NET**||||
|`@Html.Partial()`|✅|❌|❌|
|`@Html.RemotePartial()`|✅|❌|✅|
|`Response.WriteFile()`|✅|❌|❌|
|`include`|✅|✅|✅|
