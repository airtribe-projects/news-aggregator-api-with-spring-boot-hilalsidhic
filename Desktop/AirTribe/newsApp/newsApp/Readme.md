
# 📰 News App — Spring Boot Project

This is a simple **News Aggregator REST API** built with **Spring Boot**.  
It demonstrates **JWT-based authentication**, user registration, news preferences, and fetching news articles from **external APIs**.  
You can also **mark news as read or favorite** and store articles in a cache (**Redis**).

---

## 📌 Features

✅ User registration & login (Spring Security + JWT)  
✅ In-memory database (**H2**) to store users and preferences  
✅ RESTful APIs:
- `POST /api/register` — Register a new user
- `POST /api/login` — Log in and get JWT token
- `GET /api/preferences` — Get news preferences
- `PUT /api/preferences` — Update news preferences
- `GET /api/news` — Fetch news based on preferences (uses external APIs)
- `POST /api/news/{id}/read` — Mark article as read
- `POST /api/news/{id}/favorite` — Mark article as favorite
- `GET /api/news/read` — Get read articles
- `GET /api/news/favorites` — Get favorite articles
- `GET /api/news/search/{keyword}` — Search news by keyword

✅ Proper exception handling  
✅ Input validation  
✅ Caching layer (**Redis**) to reduce external API calls

---

## ⚙️ Tech Stack

- **Spring Boot**
- **Spring Security**
- **JWT**
- **H2 Database**
- **Redis** (for caching)
- **WebClient** or `RestTemplate` for external API calls
- **Lombok**
- **Postman** for API testing

---

## 🚀 How to Run

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/news-app.git
cd news-app
```

---

### 2️⃣ Start Redis Server

> **Important:** If you are using the caching feature, make sure **Redis** is running locally on `localhost:6379`.

**Mac/Linux:**

```bash
redis-server
```

**Windows:**  
Use **WSL**, **Docker**, or the Redis MSI installer.  
Example using Docker:

```bash
docker run -p 6379:6379 redis
```

---

### 3️⃣ Run the Spring Boot Application

```bash
./mvnw spring-boot:run
```

or run `NewsAppApplication` directly from your IDE (**IntelliJ**, **VSCode**, etc.).

---

## 🔑 How to Use

1️⃣ **Register a user**

```http
POST /api/register
```

**Body:**
```json
{
  "username": "yourname",
  "password": "yourpassword",
  "email": "your@email.com"
}
```

2️⃣ **Login**

```http
POST /api/login
```

**Body:**
```json
{
  "username": "yourname",
  "password": "yourpassword"
}
```

This returns a **JWT token**.

3️⃣ **Use JWT for all secured endpoints**

Add HTTP header:
```
Authorization: Bearer YOUR_TOKEN
```

4️⃣ **Test all other endpoints**

Example:

```bash
curl -H "Authorization: Bearer YOUR_TOKEN" http://localhost:8080/api/news
```

---

## ⚡️ Notes

- **External news APIs** (like NewsAPI, GNews, NewsCatcher) require an **API key** — configure these in your `application.properties`.
- News articles are cached in **Redis** to reduce external API calls.
- ✅ You can mark articles as **read** or **favorite**.
- ⚙️ **Pending:** Periodic background job to refresh cached news articles is not yet implemented.
- ✅ Exception handling & input validation are included.

---

## 🧪 API Testing

Use **Postman** or `curl`:
- Register → Login → Copy JWT → Call other endpoints with the `Authorization` header.

---

## ⚙️ application.properties Example

```properties
# JWT secret
jwt.secret=YOUR_SECRET

# External API keys
newsapi.apikey=YOUR_NEWSAPI_KEY

# Redis config
spring.redis.host=localhost
spring.redis.port=6379
```

---

## 📝 Pending

- [ ] **Background scheduler** to periodically update cached articles.

---

## 📌 Contact

For any questions or help, feel free to reach out!
hilalsidhic21@gmail.com
---

**Happy Coding! 🚀**
