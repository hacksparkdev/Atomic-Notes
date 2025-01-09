Godaddy: cor3ytat@icloud.com
# Admin 
```Bash
username: cor3ytat@icloud.com
password: EmmaJane07!!
```

# Setting up access
To give secure access to your CTF team on your Wiki.js server, you'll want to set up proper authentication and user roles. Here are the steps to help you securely configure access:

### 1. **Set Up User Authentication**

#### a. **Enable Authentication**
Wiki.js supports multiple authentication methods, including local authentication (using Wiki.js accounts), OAuth2 (Google, GitHub, etc.), and LDAP. For a CTF team, you may want to use a method that integrates well with your existing infrastructure, such as GitHub OAuth or LDAP if you're already using those.

To set up authentication:
1. Log in to your Wiki.js admin panel (`http://<your-server-ip>:3000`).
2. Go to **Administration** > **Authentication**.
3. Choose your preferred authentication method (Local, OAuth, LDAP, etc.).
4. Configure the method according to the documentation for your chosen system.

#### b. **Local Authentication** (Username and Password)
1. Enable local authentication if you're using Wiki.js accounts.
2. Add users manually or allow them to register themselves (depending on your preferences).
3. Make sure users have strong passwords to prevent unauthorized access.

### 2. **Set Up User Roles and Permissions**

After configuring authentication, you need to set appropriate roles and permissions for your CTF team members. Wiki.js provides flexible role-based access control (RBAC).

1. **Define User Roles:**
    - Go to **Administration** > **Users & Groups**.
    - Create new roles for your CTF team, such as:
      - **Admin**: Full access to the Wiki.
      - **CTF Member**: Limited access to specific pages (e.g., challenges, solutions, tools).
    - Each role can have specific access levels (read, write, delete, etc.).

2. **Assign Permissions:**
    - After creating roles, you can set permissions for each page or section of your Wiki.
    - Go to **Administration** > **Pages** and assign read/write/delete permissions based on the roles you've created.
    - You can also use **Groups** to manage permissions for teams (e.g., CTF team, Admin team).

### 3. **Restrict Access to Specific Pages/Sections**
If you want your CTF team to access only certain pages (e.g., challenge solutions or notes), you'll need to configure page permissions:

1. Create the CTF-specific pages (e.g., `CTF Challenges`, `CTF Solutions`, etc.).
2. Set permissions on these pages so that only members with the appropriate roles can view or edit them.
   - Go to **Administration** > **Pages** > Select the page you want to restrict access to.
   - Set the permissions for different roles (e.g., "CTF Member" can view but not edit).

### 4. **Set Up Secure Access (SSL/TLS)**

To ensure that all traffic to your Wiki.js server is encrypted, you'll need to set up SSL/TLS. If you're running your server on your home network, you can use a free certificate from [Let’s Encrypt](https://letsencrypt.org/) or use a self-signed certificate for internal use.

Here’s how you can set up SSL:
1. **Using Let’s Encrypt**:
   - If your home server has a public domain name, you can use Let’s Encrypt to generate an SSL certificate.
   - Install a web server like **nginx** or **Apache** to reverse proxy your Wiki.js server and handle SSL termination.
   - Use Certbot to request and renew Let’s Encrypt certificates.
   
2. **Using a Self-Signed Certificate**:
   - If you don’t have a public domain, you can generate a self-signed certificate.
   - Install it on your server and configure Wiki.js or a reverse proxy to use SSL.

### 5. **Set Up Two-Factor Authentication (Optional)**

To further secure your Wiki.js server, you can enable two-factor authentication (2FA). This adds an extra layer of security by requiring users to verify their identity using an app (e.g., Google Authenticator) in addition to their password.

1. Go to **Administration** > **Authentication** > **Two-Factor Authentication**.
2. Enable 2FA and configure the authentication method (e.g., using Google Authenticator).
3. Encourage your CTF team members to enable 2FA for their accounts.

### 6. **VPN or Firewall for Additional Security (Optional)**

If you're concerned about external access and only want your CTF team to access the Wiki.js server from trusted networks:
1. **VPN Access**: Set up a VPN server (e.g., OpenVPN, WireGuard) on your home network. Have your CTF team connect to the VPN before accessing the Wiki.js server.
2. **Firewall Configuration**: You can also restrict access by IP address using your router's firewall or by configuring your server's firewall (e.g., using `iptables` or `ufw` on Linux) to only allow access from specific IP ranges.

### 7. **Regular Backups**

To ensure that your data is protected and can be recovered in case of issues, set up a regular backup schedule for your Wiki.js database and files. Wiki.js has built-in backup options for database and content files that you can automate with cron jobs or using tools like `rsync`.

---

### Summary:
1. **Authentication**: Use local accounts, OAuth, or LDAP for secure login.
2. **Roles & Permissions**: Set specific roles (e.g., CTF team) and define page-level permissions.
3. **Secure Access**: Use SSL/TLS encryption (via Let’s Encrypt or self-signed certificate).
4. **Two-Factor Authentication**: Enable 2FA for extra security.
5. **VPN or Firewall**: Secure access by requiring VPN or restricting IP addresses.
6. **Backups**: Regularly back up Wiki.js data to ensure recovery in case of failure.

By following these steps, you can securely give your CTF team access to your Wiki.js server and protect your content from unauthorized access.