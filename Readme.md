# Customer Management API

A simple Customer Management System API built with FastAPI. This API allows you to create, retrieve, update, and delete customer records using RESTful endpoints. It uses an in-memory data store for demonstration purposes.

---

## Features
- **Add a customer**
- **List all customers**
- **Get a customer by ID**
- **Update customer details**
- **Delete a customer**

---

## Endpoints

### 1. Create Customer
`POST /customers/`
- **Request Body:**
  ```json
  {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "1234567890"
  }
  ```
- **Response:** Returns the created customer object.

### 2. List Customers
`GET /customers/`
- **Response:** Returns a list of all customers.

### 3. Get Customer by ID
`GET /customers/{customer_id}`
- **Response:** Returns the customer object if found.
- **Error:** 404 if customer not found.

### 4. Update Customer
`PUT /customers/{customer_id}`
- **Request Body:** Same as create.
- **Response:** Returns the updated customer object.
- **Error:** 400 if ID mismatch, 404 if customer not found.

### 5. Delete Customer
`DELETE /customers/{customer_id}`
- **Response:** `{ "detail": "Customer deleted" }`
- **Error:** 404 if customer not found.

---

## Example Usage

### Create a Customer
```bash
curl -X POST "http://localhost:8000/customers/" \
     -H "Content-Type: application/json" \
     -d '{"id": 1, "name": "John Doe", "email": "john@example.com", "phone": "1234567890"}'
```

### Get a Customer
```bash
curl "http://localhost:8000/customers/1"
```

### List All Customers
```bash
curl "http://localhost:8000/customers/"
```

### Update a Customer
```bash
curl -X PUT "http://localhost:8000/customers/1" \
     -H "Content-Type: application/json" \
     -d '{"id": 1, "name": "Jane Doe", "email": "jane@example.com", "phone": "9876543210"}'
```

### Delete a Customer
```bash
curl -X DELETE "http://localhost:8000/customers/1"
```

---

## How to Run

1. **Install dependencies:**
   ```bash
   pip install fastapi uvicorn
   ```
2. **Start the server:**
   ```bash
   uvicorn main:app --reload
   ```
3. **Access the API docs:**
   Open [http://localhost:8000/docs](http://localhost:8000/docs) in your browser for interactive documentation.

---

## Notes
- This API uses an in-memory dictionary for storing customers. Data will be lost when the server restarts.
- For production, integrate with a persistent database.

---

## License
MIT
