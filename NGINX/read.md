## 🚀 **NGINX Interview Preparation (Beginner to Intermediate)**  

Agar aap **NGINX ka job interview** dene wale hain, to ye **detailed guide** aapko **best preparation** karne me madad karegi.  

---

# **📌 What is NGINX?**
### **1️⃣ NGINX kya hai?**
✅ **NGINX ek open-source, high-performance web server aur reverse proxy server hai.**  
✅ Ye **HTTP server, load balancer, reverse proxy, aur caching server** ke roop me kaam karta hai.  
✅ **Main features:**  
   - High performance aur scalability.  
   - Load balancing aur reverse proxy support.  
   - SSL/TLS termination.  
   - Static aur dynamic content handling.  
   - Microservices architecture aur container support (Docker, Kubernetes).  

---

# **📌 Key Features of NGINX**
### **2️⃣ NGINX ke Benefits kya hain?**
✅ **1. High Performance** → Apache se fast hai aur zyada traffic handle kar sakta hai.  
✅ **2. Load Balancing** → Multiple servers ke beech traffic distribute karta hai.  
✅ **3. Reverse Proxy** → Backend servers ke liye requests forward karta hai.  
✅ **4. Security** → DDoS protection, SSL termination, aur request filtering.  
✅ **5. Scalability** → Microservices aur containerized applications ke liye best hai.  

---

# **📌 NGINX Architecture**
### **3️⃣ NGINX Architecture kya hai?**
✅ **Components of NGINX:**  
- **Master Process** → Configuration read karta hai aur worker processes ko manage karta hai.  
- **Worker Processes** → Requests handle karte hain aur multiple clients ko serve karte hain.  
- **Event-Driven Model** → Low memory usage aur high performance ke liye.  
- **Reverse Proxy Module** → Backend servers se communication karta hai.  
- **Load Balancer** → Requests ko multiple servers me distribute karta hai.  

---

# **📌 NGINX Installation & Setup**
### **4️⃣ NGINX Install kaise karein?**
✅ **Linux (Ubuntu/Debian) par install karein:**  
```sh
sudo apt update
sudo apt install nginx
```
✅ **Start & Enable Service:**  
```sh
sudo systemctl start nginx
sudo systemctl enable nginx
```
✅ **NGINX Status Check karein:**  
```sh
sudo systemctl status nginx
```
✅ **Windows ke liye:**  
- [NGINX Official Download](https://nginx.org/en/download.html) se package download karein.  
- `.exe` file run karein aur NGINX start karein.  

✅ **Check if NGINX is running:**  
```sh
curl -I http://localhost
```

---

# **📌 Basic NGINX Commands**
### **5️⃣ Important Commands**
📌 **NGINX Restart, Reload & Stop**  
```sh
sudo systemctl restart nginx
sudo systemctl reload nginx
sudo systemctl stop nginx
```
📌 **NGINX Configuration File Check:**  
```sh
sudo nginx -t
```
📌 **NGINX Logs Check:**  
```sh
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log
```

---

# **📌 Basic NGINX Configuration**
### **6️⃣ Default Configuration File Location:**
📌 **NGINX Configuration File:**  
```sh
/etc/nginx/nginx.conf
```
📌 **Example Configuration (`/etc/nginx/sites-available/default`):**
```nginx
server {
    listen 80;
    server_name example.com;
    
    location / {
        root /var/www/html;
        index index.html index.htm;
    }
}
```
✅ **Configuration Apply karne ke liye Restart karein:**  
```sh
sudo systemctl restart nginx
```

---

# **📌 Reverse Proxy Configuration**
### **7️⃣ Reverse Proxy Setup**
✅ **Reverse Proxy ek intermediate server hota hai jo client requests ko backend servers par forward karta hai.**  

📌 **Reverse Proxy Example:**
```nginx
server {
    listen 80;
    server_name mywebsite.com;

    location / {
        proxy_pass http://127.0.0.1:5000;  # Backend Server
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```
👉 **Yeh NGINX request ko `http://127.0.0.1:5000` par forward karega.**  

---

# **📌 Load Balancing in NGINX**
### **8️⃣ Load Balancer Configuration**
✅ **NGINX Load Balancer multiple backend servers ke beech traffic distribute karta hai.**  

📌 **Load Balancing Example:**
```nginx
upstream backend_servers {
    server 192.168.1.101;
    server 192.168.1.102;
}

server {
    listen 80;
    server_name mywebsite.com;

    location / {
        proxy_pass http://backend_servers;
    }
}
```
👉 **Yeh traffic ko `192.168.1.101` aur `192.168.1.102` ke beech distribute karega.**  

✅ **Load Balancing Methods:**  
- **Round Robin (Default)** → Requests ko evenly distribute karta hai.  
- **Least Connections** → Jo server sabse kam load pe hai usko prefer karta hai.  
- **IP Hash** → Client IP ke base par same server ko requests forward karta hai.  

---

# **📌 SSL/TLS Setup in NGINX**
### **9️⃣ HTTPS Enable kaise karein?**
✅ **Let's Encrypt SSL install karein:**  
```sh
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com
```
📌 **SSL Configuration Example:**
```nginx
server {
    listen 443 ssl;
    server_name yourdomain.com;
    
    ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;

    location / {
        root /var/www/html;
        index index.html;
    }
}
```
✅ **SSL Certificate Renewal:**  
```sh
sudo certbot renew --dry-run
```

---

# **📌 Security Best Practices**
### **🔟 NGINX Security Implementations**
✅ **1. Disable Server Tokens:**  
```nginx
server_tokens off;
```
✅ **2. Limit Request Rate:**  
```nginx
limit_req_zone $binary_remote_addr zone=mylimit:10m rate=1r/s;
location / {
    limit_req zone=mylimit burst=5;
}
```
✅ **3. Enable HTTP2:**  
```nginx
listen 443 ssl http2;
```
✅ **4. Protect Against Clickjacking:**  
```nginx
add_header X-Frame-Options DENY;
```

---

# **🔥 NGINX Interview Questions (Beginner to Intermediate)**
| # | Question | Answer |
|---|---------|---------|
| 1 | NGINX kya hai? | NGINX ek high-performance web server, reverse proxy, aur load balancer hai. |
| 2 | Apache vs NGINX ka difference? | NGINX event-driven model use karta hai, jo high performance aur scalability deta hai. Apache process-based model use karta hai. |
| 3 | NGINX reverse proxy kaise kaam karta hai? | Ye client request ko backend servers tak forward karta hai aur response return karta hai. |
| 4 | NGINX Load Balancing kya hai? | Multiple backend servers ke beech traffic distribute karta hai. |
| 5 | NGINX me SSL kaise enable karein? | Let's Encrypt ya manual SSL certificates use karke HTTPS configure kar sakte hain. |
| 6 | NGINX me caching kaise kaam karta hai? | FastCGI caching aur Proxy caching se performance improve hoti hai. |
| 7 | NGINX me `nginx.conf` file ka kya role hai? | Isme server aur request handling configuration hoti hai. |
| 8 | NGINX me DDoS protection kaise implement karein? | Rate limiting aur access control rules configure kar sakte hain. |

---

## **🔥 Final Preparation Tips**
✅ **NGINX ka hands-on practice karein**  
✅ **Reverse proxy aur load balancing concepts samjhein**  
✅ **Security best practices follow karein**  
✅ **Mock interviews aur real-world scenarios solve karein**  

Agar aapko **kisi specific topic par aur detail chahiye** to bata sakte hain! 🚀🔥
