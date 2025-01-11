Tags: [[Burpsuite]] [[Command Injection]] [[Cybersecurity]] [[Penetration Testing]]

### Intercepting packets with Burpsuite

1. Start Burpsuite
2. Click the proxy tab at the top of the page![[Screenshot From 2024-12-18 16-12-12.png]]
3. On the blue button bellow click intercept on.
4. Click the open Browser Orange button
5. When you type in the IP or the URL you want to get to. it will stall. You can click the forward button to move the request along. 

### Injecting a Command
We can inject a  command into a web page using  Burpsuite.
1. We first run the request. 
2. Then we can catch the requ[e]([[]()]())st with Burpsuite. You can use `ctrl + r ` to send the request to the repeater. ![[Screenshot From 2024-12-18 16-29-03.png]]
3. Now we can inject our command where we want. ![[Screenshot From 2024-12-18 16-30-58.png]]
4. Here we used the pipe command `%7c` which only shows the second command.
5. As we can see the command rand and printed `www-data`

### OR || Operator
We can use the or operator to get just our command. The `OR` operator will only run the second command if the first one fails. If we remove the IP address here, It will only run the second command. Which would be the `whoami`.

![[Screenshot From 2024-12-18 16-45-13.png]]

Here we can see that it worked. 

