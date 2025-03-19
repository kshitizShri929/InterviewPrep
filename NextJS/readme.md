Aap **Next.js** ki interview preparation ke liye **detailed** questions aur answers chahte hain, to main har **important topic** ko **detail me cover** karunga. Ye guide **beginner to intermediate level** tak aapko **job interview** ke liye prepare karne me madad karegi. 🚀  

---

# **🔥 Next.js Interview Preparation (Beginner to Intermediate)**  
## **📌 Introduction to Next.js**
### **1️⃣ Next.js kya hai?**
✅ **Next.js ek React framework hai** jo **server-side rendering (SSR), static site generation (SSG), hybrid rendering, aur API routes** ko support karta hai.   
✅ Ye **SEO-friendly** aur **performance optimized** websites ke liye use hota hai.  

**📌 Features of Next.js:**  
- **Server-Side Rendering (SSR)**  
- **Static Site Generation (SSG)**  
- **Incremental Static Regeneration (ISR)**  
- **Automatic Code Splitting**  
- **Fast Refresh for Development**  
- **File-based Routing**  
- **Built-in API Routes**  
- **Image Optimization**  

---

## **📌 Difference Between React.js and Next.js**
### **2️⃣ Next.js aur React.js me kya difference hai?**  

| Feature | Next.js | React.js |
|---------|--------|----------|
| Rendering | SSR, SSG, ISR, CSR | CSR (default) |
| SEO | Excellent (SSR, SSG) | Poor (CSR) |
| Routing | File-based Routing | Component-based Routing |
| API Routes | In-built API routes | External API needed |
| Performance | Fast | Moderate |
| Deployment | Server + Static | Client-side only |

✅ **Agar aapko SEO aur performance important hai, to Next.js better option hai.**  

---

## **📌 Routing in Next.js**
### **3️⃣ Next.js me Routing kaise kaam karta hai?**
✅ Next.js me **file-based routing** ka concept use hota hai.   
✅ Jo bhi file **`pages/`** folder me hoti hai, wo automatically ek route ban jati hai.  

**📌 Example:**  
```
/pages/index.js → "/"
/pages/about.js → "/about"
/pages/contact.js → "/contact"
```

---

### **4️⃣ Dynamic Routing in Next.js**  
✅ Dynamic routes ke liye **square brackets `[ ]`** ka use hota hai.  

**Example (`pages/blog/[id].js`):**  
```js
import { useRouter } from 'next/router';

export default function BlogPost() {
    const router = useRouter();
    const { id } = router.query;

    return <h1>Blog Post ID: {id}</h1>;
}
```
👉 Agar user `/blog/123` open karega, to `{id}` ka value `"123"` ho jayega.  

---

## **📌 Data Fetching Methods in Next.js**
Next.js me **3 main data fetching methods** hain:  
1️⃣ **getStaticProps()** (Static Site Generation)  
2️⃣ **getServerSideProps()** (Server-side Rendering)  
3️⃣ **getStaticPaths()** (Dynamic Static Pages)  

### **5️⃣ `getStaticProps()` kya hai?**  
✅ **SSG (Static Site Generation) ke liye use hota hai.**  
✅ Ye page ko **build time** pe data fetch karke **static page** bana deta hai.  

**Example:**  
```js
export async function getStaticProps() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    const posts = await res.json();

    return {
        props: { posts }
    };
}
```

---

### **6️⃣ `getServerSideProps()` kya hai?**  
✅ **SSR (Server-side Rendering) ke liye use hota hai.**  
✅ **Har request ke time par data fetch hota hai.**  

**Example:**  
```js
export async function getServerSideProps() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    const posts = await res.json();

    return {
        props: { posts }
    };
}
```

---

### **7️⃣ `getStaticPaths()` kya hai?**  
✅ **Agar aapko dynamic static pages banani hain to `getStaticPaths()` use hota hai.**  

**Example:**  
```js
export async function getStaticPaths() {
    return {
        paths: [
            { params: { id: '1' } },
            { params: { id: '2' } }
        ],
        fallback: false
    };
}
```

---

## **📌 API Routes in Next.js**
### **8️⃣ Next.js me API Routes kya hote hain?**  
✅ **API routes Next.js me backend logic likhne ka tarika hai.**  
✅ Ye **Node.js ke backend code** ko handle karta hai.  

**Example (`pages/api/hello.js`):**  
```js
export default function handler(req, res) {
    res.status(200).json({ message: 'Hello from API!' });
}
```

**Frontend API call:**  
```js
fetch('/api/hello')
    .then(response => response.json())
    .then(data => console.log(data));
```

---

## **📌 Image Optimization in Next.js**
### **9️⃣ Next.js me Image Optimization kaise hoti hai?**  
✅ **Next.js ka built-in `next/image` component image optimization ke liye use hota hai.**  

**Example:**  
```js
import Image from 'next/image';

export default function Home() {
    return (
        <Image 
            src="/vercel.svg"
            width={200}
            height={100}
            alt="Vercel Logo"
        />
    );
}
```

---

## **📌 Middleware in Next.js**
### **🔟 Next.js me Middleware kya hota hai?**  
✅ **Middleware ek function hota hai jo request aur response ke beech me execute hota hai.**  
✅ **Next.js 12 se Middleware ka support aaya hai.**  

**Example (`middleware.js`):**  
```js
import { NextResponse } from 'next/server';

export function middleware(req) {
    if (!req.cookies.auth) {
        return NextResponse.redirect('/login');
    }
}
```

---

## **📌 Deployment of Next.js**
### **1️⃣1️⃣ Next.js ko kaise deploy karein?**
✅ **Next.js ko Vercel, Netlify, ya custom server pr deploy kar sakte hain.**  
✅ **Commands:**  
```bash
npm run build
npm start
```

---

# **🔥 Next.js Interview Questions (Beginner to Intermediate)**
| # | Question | Answer |
|---|---------|---------|
| 1 | Next.js kya hai? | Ek React framework jo SSR, SSG, ISR ko support karta hai. |
| 2 | Next.js aur React.js me kya difference hai? | Next.js SSR aur SSG support karta hai, React.js sirf CSR karta hai. |
| 3 | `getStaticProps()` ka use kya hai? | Ye SSG ke liye use hota hai aur build-time pe data fetch karta hai. |
| 4 | `getServerSideProps()` ka use kya hai? | Ye SSR ke liye use hota hai aur har request pe data fetch karta hai. |
| 5 | Next.js me API Routes kaise kaam karte hain? | API Routes `pages/api/` folder me backend endpoints banane ke liye use hote hain. |
| 6 | Next.js me Image Optimization kaise hoti hai? | `next/image` component ka use karke. |
| 7 | Next.js me Middleware ka kya role hai? | Request ko modify karne ya authentication ke liye use hota hai. |
| 8 | Next.js ko kaise deploy karein? | `npm run build` aur `npm start` ya Vercel pr deploy karein. |

---

## **🔥 Final Preparation Tips**
✅ **Next.js ka documentation padhein**  
✅ **Ek chhoti si Next.js project banayein aur API routes aur SSR ka use karein**  
✅ **Static aur dynamic routes implement karein**  
✅ **Interview ke liye practice karein**  

Agar aapko kisi aur topic pe **aur detail chahiye** to bata sakte hain! 🚀🔥
