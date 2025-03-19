 

## **1️⃣ MongoDB ka Basic Introduction**  
✅ **MongoDB kya hai?**  
- Ye ek **NoSQL database** hai jo **JSON-like documents** me data store karta hai.  
- **RDBMS vs MongoDB:** Isme tables nahi hote, balki **Collections aur Documents** hote hain.  

✅ **MongoDB ke Features**  
- **Schema-less database** (tables ki zaroorat nahi)  
- **Horizontally scalable** (large data handle kar sakta hai)  
- **High performance** (fast read/write operations)  

✅ **MongoDB ko Install kaise karein?**  
- **Windows/Linux par MongoDB install** karna seekhein.  
- `mongod` command se server start karein.  
- `mongo` shell ka use karke database access karein.  

---

## **2️⃣ MongoDB ke Basic Commands**  
MongoDB me kaam karne ke liye ye basic commands yaad hone chahiye:  

| **Command**      | **Description** |
|-----------------|----------------|
| `show dbs` | Sabhi databases list karta hai |
| `use myDatabase` | Ek naya ya existing database select karta hai |
| `db.createCollection("users")` | Naya collection banata hai |
| `show collections` | Database ke collections dikhata hai |

---

## **3️⃣ CRUD Operations (Create, Read, Update, Delete)**  

### **(A) Data Insert Karna (Create)**
```json
db.users.insertOne({ name: "Amit", age: 25, city: "Delhi" })
```
```json
db.users.insertMany([
  { name: "Rahul", age: 30, city: "Mumbai" },
  { name: "Neha", age: 22, city: "Pune" }
])
```

### **(B) Data Read Karna (Read)**
```json
db.users.find() // Pura data show karega
```
```json
db.users.find({ city: "Delhi" }) // Sirf Delhi wale users show karega
```

### **(C) Data Update Karna (Update)**
```json
db.users.updateOne({ name: "Amit" }, { $set: { age: 26 } })
```
```json
db.users.updateMany({ city: "Delhi" }, { $set: { city: "New Delhi" } })
```

### **(D) Data Delete Karna (Delete)**
```json
db.users.deleteOne({ name: "Amit" }) // Sirf ek record delete karega
```
```json
db.users.deleteMany({ city: "New Delhi" }) // Jitne bhi records match karenge, delete ho jayenge
```

---

## **4️⃣ Filtering aur Querying Data**  
### **Conditional Queries**
```json
db.users.find({ age: { $gt: 25 } }) // Jinka age 25 se jyada hai
```
```json
db.users.find({ city: { $in: ["Delhi", "Mumbai"] } }) // Sirf Delhi aur Mumbai wale users
```

### **Sorting aur Limiting**
```json
db.users.find().sort({ age: 1 }) // Age ke basis pe ascending order me
```
```json
db.users.find().limit(2) // Sirf 2 records dikhayega
```

---

## **5️⃣ MongoDB Indexing (Basic Concept)**
Index lagane se **queries fast ho jati hain**.  
```json
db.users.createIndex({ name: 1 }) // Name field par index banayega
```
```json
db.users.find({ name: "Rahul" }).explain("executionStats") // Query speed check karne ke liye
```

---

## **6️⃣ MongoDB Aggregation (Basic)**
Agar aapko **data ko process aur transform** karna hai to **Aggregation Pipeline** use hota hai.

```json
db.users.aggregate([
  { $match: { city: "Delhi" } }, // Sirf Delhi wale users select honge
  { $group: { _id: "$city", avgAge: { $avg: "$age" } } } // City-wise average age nikalega
])
```

---

## **7️⃣ Common Beginner-Level Interview Questions**
Agar aap beginner hain, to **ye questions practice karein**:

### **Basic Questions**
1. MongoDB kya hai?  
2. SQL aur NoSQL databases me kya difference hai?  
3. MongoDB me Collections aur Documents kya hote hain?  
4. MongoDB ka schema-less hone ka kya matlab hai?  
5. MongoDB me indexes ka kya use hai?  

### **CRUD Operations Questions**
6. MongoDB me ek naya document kaise insert karte hain?  
7. MongoDB me `find()` aur `findOne()` me kya difference hai?  
8. `updateOne()` aur `updateMany()` me kya antar hai?  
9. MongoDB me data delete kaise kiya jata hai?  
10. Aggregation Pipeline ka basic concept samjhaiye.  

### **Practical Coding Questions**
✅ MongoDB me ek **Student Collection** banaiye jisme `name`, `age`, `marks`, aur `city` fields ho.  
✅ Query likhiye jo **Mumbai ke students ka data** return kare.  
✅ Query likhiye jo **students ko unke marks ke hisaab se sort kare**.  
✅ Query likhiye jo **marks 50 se jyada wale students ka count** nikale.  

---

## **8️⃣ Practice & Hands-on Learning**
### **Practice MongoDB on:**
- **MongoDB Atlas** (Free cloud-based MongoDB)  
- **Local MongoDB setup**  
- **MongoDB University Free Courses**  

### **Mini Project Ideas**
✅ **User Registration System** (User data store & CRUD operations)  
✅ **Product Catalog System** (E-commerce style database)  
✅ **Employee Management System** (Store & query employee details)  

---

## **🎯 Final Tips**
✅ **Daily 1-2 hours practice karein**  
✅ **CRUD operations aur indexing par focus karein**  
✅ **Interview ke liye queries likhne ki practice karein**  
✅ **Basic projects banakar apni MongoDB skills improve karein**  

Agar aapko **koi specific topic ya query practice karni hai**, to mujhe bata sakte hain. 🎯🚀
