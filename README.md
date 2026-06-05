Backend Foundations: REST API & JSON Architecture
# 🚀 REST API & JSON Fundamentals

## 📌 Proje Hakkında

Bu proje, API (Application Programming Interface) kavramını, REST mimarisini ve JSON veri formatını öğrenmek amacıyla hazırlanmıştır. Ayrıca Python Flask kullanılarak temel CRUD işlemlerini gerçekleştiren örnek bir REST API uygulaması geliştirilmiştir.

---

## 🏗️ API Nedir?

API (Application Programming Interface), farklı yazılımların birbiriyle iletişim kurmasını sağlayan arayüzdür.

Bir istemci (Client), API aracılığıyla sunucuya (Server) istek gönderir ve sunucudan yanıt alır.

### API İletişim Süreci

1. Client isteği gönderir.
2. API isteği işler.
3. Server veriyi hazırlar.
4. JSON formatında yanıt döndürülür.

---

## 🌐 REST Mimarisi

REST (Representational State Transfer), web servisleri geliştirmek için kullanılan mimari yaklaşımdır.

Örnek endpointler:

```http
/api/users
/api/products
/api/orders
```

REST mimarisinde her kaynak (resource) bir URL ile temsil edilir.

---

## ⚡ HTTP Metotları

| Metot  | Açıklama        |
| ------ | --------------- |
| GET    | Veri Listeleme  |
| POST   | Veri Ekleme     |
| PUT    | Veri Güncelleme |
| DELETE | Veri Silme      |

### GET

```http
GET /api/users
```

### POST

```http
POST /api/users
```

### PUT

```http
PUT /api/users/1
```

### DELETE

```http
DELETE /api/users/1
```

---

## 📦 JSON Nedir?

JSON (JavaScript Object Notation), API'lerde veri taşımak için kullanılan hafif veri formatıdır.

Örnek:

```json
{
  "id": 1,
  "name": "Esma",
  "email": "esma@example.com"
}
```

---

## 🎯 Endpoint Tasarımı

| Endpoint            | Açıklama              |
| ------------------- | --------------------- |
| GET /api/users      | Kullanıcıları Listele |
| GET /api/users/1    | Kullanıcı Detayı      |
| POST /api/users     | Kullanıcı Ekle        |
| PUT /api/users/1    | Kullanıcı Güncelle    |
| DELETE /api/users/1 | Kullanıcı Sil         |

---

## 🔐 API Güvenliği

Temel güvenlik önlemleri:

* HTTPS Kullanımı
* JWT Authentication
* Authorization
* Rate Limiting
* Input Validation

---

## 💻 Flask ile REST API Uygulaması

### Kurulum

```bash
pip install flask
```

### API Kodu

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

users = [
    {"id": 1, "name": "Esma"},
    {"id": 2, "name": "Ahmet"}
]

@app.route('/api/users', methods=['GET'])
def get_users():
    return jsonify(users)

@app.route('/api/users/<int:id>', methods=['GET'])
def get_user(id):
    for user in users:
        if user["id"] == id:
            return jsonify(user)

    return {"error": "User not found"}, 404

@app.route('/api/users', methods=['POST'])
def create_user():
    data = request.json

    new_user = {
        "id": len(users) + 1,
        "name": data["name"]
    }

    users.append(new_user)

    return jsonify(new_user), 201

@app.route('/api/users/<int:id>', methods=['PUT'])
def update_user(id):
    data = request.json

    for user in users:
        if user["id"] == id:
            user["name"] = data["name"]
            return jsonify(user)

    return {"error": "User not found"}, 404

@app.route('/api/users/<int:id>', methods=['DELETE'])
def delete_user(id):
    global users

    users = [user for user in users if user["id"] != id]

    return {"message": "User deleted"}

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 🧪 Test Örnekleri

### GET

```http
GET http://127.0.0.1:5000/api/users
```

### POST

```json
{
  "name": "Mehmet"
}
```

### PUT

```json
{
  "name": "Ali"
}
```

### DELETE

```http
DELETE http://127.0.0.1:5000/api/users/1
```

---

## 📚 Öğrenilen Konular

* API Mantığı
* REST Mimarisi
* HTTP Metotları
* JSON Veri Yapısı
* Endpoint Tasarımı
* Flask Framework
* CRUD İşlemleri
* Backend Temelleri

---

## 👨‍💻 Kullanılan Teknolojiler

* Python
* Flask
* REST API
* JSON
* HTTP Protocol

---

## 📄 Lisans

Bu proje eğitim amaçlı geliştirilmiştir.


📄 Author: Esma Şişman
