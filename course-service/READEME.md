# 🚀 Deployment in GCP

## 🌟 Project Overview
This repository showcases my hands-on assignment for **Enterprise Cloud Architecture**.  
The project demonstrates the deployment of a **Spring Boot application** with **MySQL database integration** using **Google Cloud SQL** services.

---

## 👤 Student Information
- **Name:** Chamud Shakeen  
- **Registration No:** 2301682019  
- **Email:** chamudgamage@gmail.com  

---

## 🎥 Demo Video
📹 [Watch Demo Video](https://drive.google.com/file/d/1fGjNehTjXBr7BEhOPoYd0GpqEhi-R6li/view?usp=sharing)

---

## ⚙️ Google Cloud MySQL Database Configuration Guide

### **Phase 1: Access Google Cloud Console**
- Go to 👉 [Google Cloud Console - SQL](https://console.cloud.google.com/sql)  
- Ensure you’re working in the correct project environment.

---

### **Phase 2: Initialize Cloud SQL Instance**
1. Click **Create Instance** → Select **MySQL**.  
2. Choose **MySQL 8.0** (recommended).  
3. Set **Instance ID** (e.g., `db-mysql`).  
4. Configure **root password** (e.g., `Ijse@1234`).  
5. Select **Region** → `us-central1` (or nearest region).  
6. Availability → **Single zone** (sufficient for development).  

---

### **Phase 3: Configure Public IP Access**
1. Go to your instance → **Connections** tab.  
2. Under **Public IP**, click **Add Network**.  
3. Enter name → `development-access`.  
4. Set IP range → `0.0.0.0/0` ⚠️ *(Development only)*.  
5. Save changes → Note the **Public IP** (e.g., `35.223.236.132`).  

---

### **Phase 4: Create Database in Instance**
1. Connect using Cloud Shell or terminal:

```bash
mysql -h <YOUR_PUBLIC_IP> -P 3306 -u root -p
````

✅ Example:

```bash
mysql -h 35.223.236.132 -P 3306 -u root -p
```

Enter password → (e.g., `Ijse@1234`).

2. Create a new database:

```sql
CREATE DATABASE eca_courses;
```

3. Verify database creation:

```sql
SHOW DATABASES;
```

✔️ You should now see `eca_courses` listed.

---

### **Phase 5: Spring Boot Application Integration**

Update your **`application-gcp.properties`**:

```properties
spring.datasource.url=jdbc:mysql://35.223.236.132:3306/eca_courses?createDatabaseIfNotExist=true
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.username=root
spring.datasource.password=Ijse@1234
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

server.port=8081
```

➡️ Run your Spring Boot app → Connection with Cloud SQL will be established.

---

## 🏁 Getting Started

1. Clone the repository:

```bash
git clone https://github.com/CHAMUD12/eca-gcp-practical.git
```

2. Update **`application-gcp.properties`** with your DB details.
3. Run the Spring Boot application.
4. Open 👉 [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

