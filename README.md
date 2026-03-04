# Praktikum 1 - User Management REST API

Aplikasi REST API sederhana untuk manajemen data pengguna menggunakan Spring Boot, Spring Data JPA, MySQL, Lombok, MapStruct, dan Validation.

---

## Endpoint API

### Base URL
```
http://localhost:8080/api/users
```

---

### 1. Create User (Tambah User)

**Endpoint:**
```
POST /api/users
```

**Request Header:**
```
Content-Type: application/json
```

**Request Body:**
```json
{
  "name": "Asroni",
  "age": 69
}
```

**Response Body (Success - 201 Created):**
```json
{
  "status": "success",
  "data": {
    "id": "0c55bd6d-7683-4f9a-98d1-aafb2d53c315",
    "name": "Asroni",
    "age": 69
  }
}
```

**Response Body (Failed - 400 Bad Request - Field kosong):**
```json
{
  "status": "error",
  "message": "name: must not be blank, age: must be greater than 0"
}
```

**Response Body (Failed - 400 Bad Request - Tipe data salah):**
```json
{
  "status": "error",
  "message": "age: must be a number"
}
```

---

### 2. Get All Users (Ambil Semua User)

**Endpoint:**
```
GET /api/users
```

**Request Body:**
```
-
```

**Response Body (Success - 200 OK):**
```json
{
  "status": "success",
  "data": [
    {
      "id": "0c55bd6d-7683-4f9a-98d1-aafb2d53c315",
      "name": "Asroni",
      "age": 69
    },
    {
      "id": "661f9511-f30c-52e5-b827-557766551111",
      "name": "Hana Miyamoto",
      "age": 22
    }
  ]
}
```

**Response Body (Failed - 200 OK - Data kosong):**
```json
{
  "status": "success",
  "data": []
}
```

---

### 3. Get User By ID (Ambil User Berdasarkan ID)

**Endpoint:**
```
GET /api/users/{id}
```

**Contoh:**
```
GET /api/users/0c55bd6d-7683-4f9a-98d1-aafb2d53c315
```

**Request Body:**
```
-
```

**Response Body (Success - 200 OK):**
```json
{
  "status": "success",
  "data": {
      "id": "0c55bd6d-7683-4f9a-98d1-aafb2d53c315",
      "name": "Asroni",
      "age": 69
  }
}
```

**Response Body (Failed - 404 Not Found - ID tidak ditemukan):**
```json
{
  "status": "error",
  "message": "user not found"
}
```

**Response Body (Failed - 400 Bad Request - ID tidak valid):**
```json
{
  "status": "error",
  "message": "invalid id format"
}
```

---

### 4. Update User (Perbarui Data User)

**Endpoint:**
```
PUT /api/users/{id}
```

**Contoh:**
```
PUT /api/users/0c55bd6d-7683-4f9a-98d1-aafb2d53c315
```

**Request Header:**
```
Content-Type: application/json
```

**Request Body:**
```json
{
  "name": "Asrooney",
  "age": 69
}
```

**Response Body (Success - 200 OK):**
```json
{
  "status": "success",
  "data": {
      "id": "0c55bd6d-7683-4f9a-98d1-aafb2d53c315",
      "name": "Asrooney",
      "age": 69
  }
}
```

**Response Body (Failed - 404 Not Found - ID tidak ditemukan):**
```json
{
  "status": "error",
  "message": "user not found"
}
```

**Response Body (Failed - 400 Bad Request - Field kosong):**
```json
{
  "status": "error",
  "message": "name: must not be blank, age: must be greater than 0"
}
```

**Response Body (Failed - 400 Bad Request - Tipe data salah):**
```json
{
  "status": "error",
  "message": "age: must be a number"
}
```

---

### 5. Delete User (Hapus User)

**Endpoint:**
```
DELETE /api/users/{id}
```

**Contoh:**
```
DELETE /api/users/661f9511-f30c-52e5-b827-557766551111
```

**Request Body:**
```
-
```

**Response Body (Success - 200 OK):**
```json
{
  "status": "success delete user with id 661f9511-f30c-52e5-b827-557766551111"
}
```

**Response Body (Failed - 404 Not Found - ID tidak ditemukan):**
```json
{
  "status": "error",
  "message": "user not found"
}
```

**Response Body (Failed - 400 Bad Request - ID tidak valid):**
```json
{
  "status": "error",
  "message": "invalid id format"
}
```

---

## Ringkasan Endpoint

| Method | Endpoint | Deskripsi |
|--------|----------|-----------|
| POST | /api/users | Tambah user baru |
| GET | /api/users | Ambil semua user |
| GET | /api/users/{id} | Ambil user by ID |
| PUT | /api/users/{id} | Update user by ID |
| DELETE | /api/users/{id} | Hapus user by ID |



<img width="1919" height="1034" alt="image" src="https://github.com/user-attachments/assets/09bc4d2e-dc0d-4dfb-b8e7-33a0b0309a44" />
