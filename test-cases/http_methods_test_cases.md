# Test Cases Matrix: Fundamental HTTP Methods

| Test Case ID | Feature / Endpoint | Test Scenario | Request Payload | Expected Status Code | Expected Response |
| :--- | :--- | :--- | :--- | :---: | :--- |
| **TC-HTTP-001** | `GET /products/1` | Fetch existing product details (Positive) | N/A | `200 OK` | Object produk berisi `id: 1` dan atribut lengkap. |
| **TC-HTTP-002** | `GET /products/99999` | Fetch non-existent product ID (Negative) | N/A | `404 Not Found` | Pesan error bahwa produk tidak ditemukan. |
| **TC-HTTP-003** | `POST /products/add` | Add product with valid payload (Positive) | `{"title":"Desk Lamp", "price": 25}` | `201 Created` | Object produk baru yang menyertakan auto-generated `id`. |
| **TC-HTTP-004** | `POST /products/add` | Add product with empty body (Negative) | `{}` / Empty | `400 Bad Request` | Pesan error validasi dari server. |
| **TC-HTTP-005** | `PUT /products/1` | Update product with valid payload (Positive) | `{"title":"Chair", "price": 120}` | `200 OK` | Object produk ID 1 dengan atribut baru. |
| **TC-HTTP-006** | `DELETE /products/1` | Delete product by valid ID (Positive) | N/A | `200 OK` | Object berisi konfirmasi penghapusan (misal `isDeleted: true`). |