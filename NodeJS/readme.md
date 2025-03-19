
## **🔹 Basic Node.js Interview Questions**  

### **1️⃣ Node.js kya hai?**  
✅ **Node.js ek JavaScript runtime hai jo Chrome ke V8 engine par based hai.**  
✅ Ye **asynchronous, event-driven, aur non-blocking I/O model** ko follow karta hai.  

**Example:**
```js
console.log('Hello, Node.js!');
```

---

### **2️⃣ Node.js ka architecture kaise kaam karta hai?**  
✅ **Node.js ek "Single Threaded Event Loop" architecture follow karta hai, jo asynchronous requests ko efficiently handle karta hai.**  

🔹 **Architecture Flow:**  
1. Client request karta hai.  
2. Event loop request ko handle karta hai.  
3. Request agar I/O operation se related ho, to Node.js usko background me handle karta hai.  
4. Jab response ready hota hai, to event loop usko return kar deta hai.  

---

### **3️⃣ Node.js synchronous aur asynchronous programming me kya difference hai?**  
| Feature | Synchronous | Asynchronous |
|---------|------------|--------------|
| Execution | Blocking | Non-blocking |
| Performance | Slow | Fast |
| Example | `fs.readFileSync()` | `fs.readFile()` |

**Example (Synchronous):**
```js
const fs = require('fs');
const data = fs.readFileSync('file.txt', 'utf8');
console.log(data);
```

**Example (Asynchronous):**
```js
fs.readFile('file.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
});
```

---

### **4️⃣ Node.js me event-driven programming kya hoti hai?**  
✅ **Node.js event-driven programming ka use karta hai jisme event listeners asynchronous events ko handle karte hain.**  

**Example using `events` module:**
```js
const EventEmitter = require('events');
const event = new EventEmitter();

event.on('greet', () => console.log('Hello, World!'));
event.emit('greet');
```

---

## **🔹 Intermediate Node.js Questions**  

### **5️⃣ Node.js me Streams kya hote hain?**  
✅ **Streams ek efficient data handling technique hai jo large files ya continuous data ko handle karne me madad karti hai.**  
✅ Streams **4 types** ke hote hain:  
1. **Readable Streams** – Data ko read karna  
2. **Writable Streams** – Data ko write karna  
3. **Duplex Streams** – Read aur Write dono  
4. **Transform Streams** – Data modify karna  

**Example (Readable Stream):**
```js
const fs = require('fs');
const readStream = fs.createReadStream('file.txt', 'utf8');
readStream.on('data', chunk => console.log(chunk));
```

---

### **6️⃣ Node.js me middleware kya hota hai?**  
✅ **Middleware ek function hota hai jo request-response cycle ke beech me execute hota hai.**  
✅ Ye **Express.js** me use hota hai.  

**Example:**
```js
app.use((req, res, next) => {
    console.log('Middleware executed');
    next();
});
```

---

### **7️⃣ Node.js me process aur thread me kya difference hai?**  
| Feature | Process | Thread |
|---------|--------|--------|
| Definition | Ek executing program | Ek lightweight process |
| Memory Usage | High | Low |
| Execution | Independent | Part of process |

---

### **8️⃣ Node.js me `fs` module kya hai?**  
✅ **`fs` (File System) module files ko read, write, delete aur modify karne ke liye use hota hai.**  

**Example:**
```js
const fs = require('fs');

fs.writeFile('test.txt', 'Hello, World!', (err) => {
    if (err) throw err;
    console.log('File created!');
});
```

---

### **9️⃣ Node.js me child process kya hota hai?**  
✅ **Child processes Node.js ke andar ek alag process create karne ke liye use hote hain.**  

**Example using `child_process` module:**
```js
const { exec } = require('child_process');
exec('ls', (err, stdout) => console.log(stdout));
```

---

### **🔟 Node.js me Cluster module kya hai?**  
✅ **Cluster module multiple processes create karke multi-core systems ka full utilization karta hai.**  

**Example:**
```js
const cluster = require('cluster');
const http = require('http');
const numCPUs = require('os').cpus().length;

if (cluster.isMaster) {
    for (let i = 0; i < numCPUs; i++) {
        cluster.fork();
    }
} else {
    http.createServer((req, res) => {
        res.writeHead(200);
        res.end('Hello from Cluster!');
    }).listen(8000);
}
```

---

## **🔹 Advanced Node.js Questions**  

### **1️⃣1️⃣ Node.js me JWT authentication kaise implement karein?**
✅ **JWT (JSON Web Token) secure authentication ke liye use hota hai.**  

**Example using `jsonwebtoken`:**
```js
const jwt = require('jsonwebtoken');

app.post('/login', (req, res) => {
    const user = { id: 1, username: 'admin' };
    const token = jwt.sign(user, 'secretKey', { expiresIn: '1h' });
    res.json({ token });
});
```

---

### **1️⃣2️⃣ Node.js me rate limiting kaise implement karein?**
✅ **Rate limiting DDoS attacks aur brute force prevention ke liye use hoti hai.**  

**Example using `express-rate-limit`:**
```js
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
    windowMs: 15 * 60 * 1000, 
    max: 100 
});

app.use(limiter);
```

---

### **1️⃣3️⃣ Node.js me WebSocket kaise implement karein?**
✅ **WebSocket real-time data communication ke liye use hota hai.**  

**Example using `socket.io`:**
```js
const http = require('http');
const { Server } = require('socket.io');

const server = http.createServer();
const io = new Server(server);

io.on('connection', (socket) => {
    console.log('User connected');
    socket.on('message', (msg) => io.emit('message', msg));
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

---

## **🚀 Final Preparation Tips**
✅ **Node.js Documentation padhein**  
✅ **JWT Authentication aur Rate Limiting implement karein**  
✅ **MongoDB ke saath integration karein**  
✅ **Practice ke liye chhoti APIs banayein**  

Agar aapko **kisi topic me aur detail chahiye**, to bata sakte hain. 🚀🔥
