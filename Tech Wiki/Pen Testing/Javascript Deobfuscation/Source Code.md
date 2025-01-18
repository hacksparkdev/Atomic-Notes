Tags: [[Javascript]] [[Penetration Test]] [[Hack The Box]] [[Cybersecurity]]

Websites are ran in the backgrounds with `html` `css` & `Javascript`  To check a websites source code we can use `crlt + u ` This will bring up the source. 

![[Pasted image 20250116165947.png]]

Here we can see the html of a page. Most website will have `CSS` as well as Javascript linked to an external page. This site has the `CSS` internally. 

## What is obfuscation

- Obfuscation is a technique used to make a script more difficult to read by humans but allows it to function the same from a technical point of view, though performance may be slower. This is usually achieved automatically by using an obfuscation tool, which takes code as an input, and attempts to re-write the code in a way that is much more difficult to read, depending on its design.

- For example, code obfuscation often turn the code into a dictionary of all of the words and symbols used within the code and then attempt to rebuild the original code during execution by referring to each word and symbol from the dictionary. The following is an example of a simple JavaScript code being obfuscated:

We can use a website like [Javascript-minifier](https://www.toptal.com/developers/javascript-minifier) To minify our code before we obfuscate it.  We can use a tool from [Beautify Tools](https://beautifytools.com/javascript-obfuscator.php) To obfuscate our tools. To further obfuscate our code we can base 64 encode it with [obfuscator.io](https://obfuscator.io/#code)

![[Pasted image 20250116173839.png]]

### Code to Obfuscate

![[Pasted image 20250116173919.png]]

### Obfuscated Code

![[Pasted image 20250116173945.png]]

### Deobfuscate Code

We can use the browser to minify code. If we bring up the code in `Firefox` and use the debugger we will get a minified version of the code. We can then use this code in a tool like [beau
tifer](https://beautifier.io/) to make the code more readable. We caunpacka;lsdkfjadsfsdfsdffunasdlkfjdsfsdlkfsdf;lasdkjfasdf;lkasdjfas;dlfkjasd;lfkjasddsfsadfasdfasfasdfasdfasdfanpacker](https://matthewfl.com/unPacker.html) to deobfuscate the code even more to get the original code. 

Sometimes developer will build their own tool to obfuscate. This way would be much more difficult to Deobfuscate.

![[Pasted image 20250116175115.png]]

### Curl Post Request

```bash
curl http://IP-address:PORT -X POST
```


# Boxes to pawn for this 

![[Pasted image 20250116190929.png]]