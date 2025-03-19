  

---

## **🔹 Basic Express.js Interview Questions**  

### **1️⃣ Express.js kya hai?**
✅ **Express.js ek lightweight aur fast web framework hai jo Node.js ke upar bana hai.**  
✅ Ye **server-side applications** aur **RESTful APIs** banane ke liye use hota hai.  

**Example:**
```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('Hello, Express!');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

---

### **2️⃣ Express.js aur Node.js me kya difference hai?**
| Feature | Node.js | Express.js |
|---------|--------|------------|
| Definition | JavaScript runtime | Node.js ka web framework |
| Purpose | Backend development | REST API aur Web apps banane ke liye |
| Complexity | Low-level (Manually handle HTTP) | High-level (Routing, Middleware provided) |
| Features | File system, streams, networking, event-driven | Routing, Middleware, Error handling |

---

### **3️⃣ Express.js me middleware kya hota hai?**
✅ **Middleware ek function hota hai jo request aur response ke beech execute hota hai.**  

**Example:**
```js
const logger = (req, res, next) => {
    console.log(`${req.method} request on ${req.url}`);
    next();  // Next middleware ko call karega
};

app.use(logger);
```

---

### **4️⃣ Express.js me routing kaise kaam karti hai?**
✅ **Routing ka matlab hai URL endpoints handle karna.**  

**Example:**
```js
app.get('/home', (req, res) => res.send('Welcome to Home!'));
app.post('/login', (req, res) => res.send('Login Successful!'));
app.put('/update', (req, res) => res.send('Update Successful!'));
app.delete('/delete', (req, res) => res.send('Delete Successful!'));
```

---

### **5️⃣ Express Router kya hota hai?**
✅ **Router ka use modular routing system banane ke liye hota hai.**  

**Example:**
```js
const express = require('express');
const router = express.Router();

router.get('/users', (req, res) => res.send('User List'));
router.post('/users', (req, res) => res.send('Create User'));

module.exports = router;
```

---

## **🔹 Intermediate Express.js Questions**  

### **6️⃣ Express.js me CORS ka kya use hai?**
✅ **CORS (Cross-Origin Resource Sharing) allow karta hai ki ek domain ka frontend doosre domain ke backend se communicate kar sake.**  

**Example:**
```js
const cors = require('cors');
app.use(cors());
```

---

### **7️⃣ Express.js me request aur response objects kya hote hain?**
| Feature | `req` (Request Object) | `res` (Response Object) |
|---------|----------------------|------------------------|
| Purpose | Client request ka data store karta hai | Server response send karta hai |
| Methods | `req.body`, `req.params`, `req.query`, `req.headers` | `res.send()`, `res.json()`, `res.status()` |
| Example | `req.query.name` (`/users?name=John`) | `res.json({ message: "Success" })` |

---

### **8️⃣ Express.js me Error Handling kaise hota hai?**
✅ **Error handling ke liye ek special middleware hota hai jo 4 arguments leta hai:**  

**Example:**
```js
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something went wrong!');
});
```

---

### **9️⃣ Express.js me authentication kaise implement karte hain?**
✅ **JWT (JSON Web Token) ya session-based authentication use hoti hai.**  

**Example (JWT Authentication using `jsonwebtoken` package):**
```js
const jwt = require('jsonwebtoken');

app.post('/login', (req, res) => {
    const user = { id: 1, username: 'admin' };
    const token = jwt.sign(user, 'secretKey', { expiresIn: '1h' });
    res.json({ token });
});

const verifyToken = (req, res, next) => {
    const token = req.headers['authorization'];
    if (!token) return res.status(403).send('Token required');
    jwt.verify(token, 'secretKey', (err, decoded) => {
        if (err) return res.status(401).send('Invalid Token');
        req.user = decoded;
        next();
    });
};

app.get('/dashboard', verifyToken, (req, res) => {
    res.send('Protected Route');
});
```

---

### **🔟 Express.js me file uploads kaise handle karte hain?**
✅ **File upload ke liye `multer` package use hota hai.**  

**Example:**
```js
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

app.post('/upload', upload.single('file'), (req, res) => {
    res.send('File uploaded successfully!');
});
```

---

## **🔹 Advanced Express.js Questions**  

### **1️⃣1️⃣ Express.js me rate limiting kaise implement karte hain?**
✅ **Rate limiting brute force attacks ko prevent karta hai.**  
**Example using `express-rate-limit`:**
```js
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
    windowMs: 15 * 60 * 1000, // 15 minutes
    max: 100 // Max 100 requests per window
});

app.use(limiter);
```

---

### **1️⃣2️⃣ Express.js me WebSocket kaise implement karein?**
✅ **WebSocket real-time data transfer ke liye use hota hai.**  

**Example using `socket.io`:**
```js
const http = require('http');
const { Server } = require('socket.io');

const server = http.createServer(app);
const io = new Server(server);

io.on('connection', (socket) => {
    console.log('User connected');
    socket.on('message', (msg) => io.emit('message', msg));
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

---

### **1️⃣3️⃣ Express.js me Session Management kaise implement karein?**
✅ **Session management ke liye `express-session` package use hota hai.**  

**Example:**
```js
const session = require('express-session');

app.use(session({
    secret: 'mySecretKey',
    resave: false,
    saveUninitialized: true,
    cookie: { secure: false }
}));

app.get('/session', (req, res) => {
    req.session.user = "John Doe";
    res.send('Session Set');
});

app.get('/get-session', (req, res) => {
    res.send(req.session.user);
});
```

---

## **🚀 Final Preparation Tips**
✅ **Express.js Documentation padhein**  
✅ **JWT Authentication aur Rate Limiting implement karein**  
✅ **MongoDB ke saath integration karein**  
✅ **Practice ke liye chhoti APIs banayein**  

Agar aapko **kisi topic me aur detail chahiye**, to bata sakte hain. 🚀🔥
