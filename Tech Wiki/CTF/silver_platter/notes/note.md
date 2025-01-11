# Box Notes

scr1ptkiddy

Scan showed three ports:
22/tcp
80/tcp
8080/tcp

After initial scan i went to the website to see if there was anything going on there. 
I didnt find anything. On the contact page there was this message: `If you'd like to get in touch with us, please reach out to our project manager on Silverpeas. His username is "scr1ptkiddy".`
I feel like silverpeas has something to do with it but im not really getting anywhere with it. I started a ffuf scan and was givin `/assets` & `/images` got 404 on both of those. 
I ran a `ffuf` scan on port `8080` and got `/website` and `/console`. Neither one of these led anywhere. 

What am i missing? 






### Searchsploit

#### Make sure it is up to date
```bash
searchsploit -u

```

#### Search for Specific Product or Software

```Bash
searchsploit acache
```


