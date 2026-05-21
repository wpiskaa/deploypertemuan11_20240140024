# deploypertemuan11_20240140024

Praktikum Software Deployment — Pertemuan 11  
**Spring Boot + Spring Security + PostgreSQL + Docker**

---

## 📋 Deskripsi Project

Aplikasi web sederhana berbasis **Spring Boot** yang mengimplementasikan:
- **Spring Security** untuk autentikasi (login/logout)
- **Spring Data JPA** dengan **PostgreSQL** sebagai database
- **Thymeleaf** sebagai template engine
- **Docker & Docker Compose** untuk containerisasi dan deployment

Fitur utama:
- ✅ Registrasi pengguna (username, password, nama, alamat)
- ✅ Login & logout dengan Spring Security
- ✅ Halaman Home yang menampilkan profil pengguna yang sedang login
- ✅ Password di-encode menggunakan BCrypt

---

## 🗂️ Struktur Folder

```
src/main/java/com/deploy/pertemuan11/
├── controller/
│   ├── AuthController.java
│   └── HomeController.java
├── model/
│   ├── dto/
│   │   └── RegisterRequest.java
│   ├── Profile.java
│   └── User.java
├── repository/
│   ├── ProfileRepository.java
│   └── UserRepository.java
├── security/
│   └── SecurityConfig.java
├── service/
│   └── AuthService.java
└── Pertemuan11Application.java
```

---

## 🐳 Docker Compose

Isi file `docker-compose.yml`:

```yaml
version: '3.8'

services:
  db:
    image: postgres:14
    container_name: db_mahasiswa
    restart: always
    environment:
      POSTGRES_DB: praktikum_db
      POSTGRES_USER: praktikum_user
      POSTGRES_PASSWORD: 12345
    ports:
      - "5434:5432"
    volumes:
      - db_data:/var/lib/postgresql/data

  app:
    build: .
    container_name: pertemuan11
    ports:
      - "8000:8080"
    depends_on:
      - db
    environment:
      SPRING_DATASOURCE_URL: jdbc:postgresql://db:5432/praktikum_db
      SPRING_DATASOURCE_USERNAME: praktikum_user
      SPRING_DATASOURCE_PASSWORD: 12345

volumes:
  db_data:
```

---

## 🚀 Cara Menjalankan dengan Docker

```bash
# 1. Clone repo
git clone https://github.com/wpiskaa/deploypertemuan11_20240140024.git
cd deploypertemuan11_20240140024

# 2. Jalankan Docker Compose
docker-compose up --build -d

# 3. Akses aplikasi di browser
# http://localhost:8000
```

---

## 📸 Screenshot

### 🖥️ Running App di WSL

![Running App WSL](screenshots/running_wsl.png)

---

### 📄 Isi docker-compose.yml

![Docker Compose](screenshots/docker_compose.png)

---

### 📊 Data pada Tabel Database

#### Tabel `users`
![Tabel Users](screenshots/tabel_users.png)

#### Tabel `profile`
![Tabel Profile](screenshots/tabel_profile.png)

---

### 🌐 Tampilan Halaman Web

#### Halaman Register
![Register Page](screenshots/register.png)

#### Halaman Login
![Login Page](screenshots/login.png)

#### Halaman Home
![Home Page](screenshots/home.png)

---

## 🛠️ Tech Stack

| Teknologi | Versi |
|-----------|-------|
| Java | 21 |
| Spring Boot | 4.0.6 |
| Spring Security | 6.x |
| Spring Data JPA | 3.x |
| Thymeleaf | 3.x |
| PostgreSQL | 14 |
| Docker | Latest |
| Lombok | Latest |
| Maven | 3.9.x |

---

## 👤 Identitas

| | |
|---|---|
| **Nama** | Hafizz Kurniawan |
| **NIM** | 20240140024 |
| **Mata Kuliah** | Software Deployment |
| **Pertemuan** | 11 |
