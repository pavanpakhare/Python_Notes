# **FastAPI Tutorial: Building High-Performance APIs in Python**

FastAPI is a modern, fast (high-performance), web framework for building APIs with Python 3.7+ based on standard Python type hints. It's one of the fastest Python frameworks available, on par with NodeJS and Go.

## **Table of Contents**
1. [Why FastAPI?](#why-fastapi)
2. [Installation & Setup](#installation--setup)
3. [Creating Your First API](#creating-your-first-api)
4. [Path Parameters](#path-parameters)
5. [Query Parameters](#query-parameters)
6. [Request Body](#request-body)
7. [Response Model](#response-model)
8. [Error Handling](#error-handling)
9. [Dependency Injection](#dependency-injection)
10. [Database Integration (SQLAlchemy)](#database-integration-sqlalchemy)
11. [Authentication (JWT)](#authentication-jwt)
12. [Deployment](#deployment)

---

## **1. Why FastAPI?**
✅ **Blazing fast** (Starlette & Pydantic under the hood)  
✅ **Automatic docs** (Swagger & ReDoc)  
✅ **Type hints** for better code completion & validation  
✅ **Async support** (ASGI compatible)  
✅ **Production-ready** with minimal boilerplate  

---

## **2. Installation & Setup**
```bash
pip install fastapi uvicorn[standard]
```

Create `main.py`:
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}
```

Run the server:
```bash
uvicorn main:app --reload
```
- Open `http://localhost:8000`  
- Interactive docs at `http://localhost:8000/docs`  

---

## **3. Creating Your First API**
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```
- Try it: `http://localhost:8000/items/5?q=test`

---

## **4. Path Parameters**
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id}
```
- **Type conversion**: FastAPI automatically converts `user_id` to an `int`.

---

## **5. Query Parameters**
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/")
def read_items(skip: int = 0, limit: int = 10):
    return {"skip": skip, "limit": limit}
```
- Try it: `http://localhost:8000/items/?skip=5&limit=20`

---

## **6. Request Body**
```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float
    is_offer: bool = None

@app.post("/items/")
def create_item(item: Item):
    return {"item_name": item.name, "item_price": item.price}
```
- Test in Swagger UI (`/docs`) or with `curl`:
```bash
curl -X POST "http://localhost:8000/items/" -H "Content-Type: application/json" -d '{"name":"Foo","price":45.2}'
```

---

## **7. Response Model**
```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):
    username: str
    email: str

@app.post("/users/", response_model=User)
def create_user(user: User):
    return user
```
- Ensures the output matches the `User` model.

---

## **8. Error Handling**
```python
from fastapi import FastAPI, HTTPException

app = FastAPI()

@app.get("/items/{item_id}")
def read_item(item_id: int):
    if item_id == 0:
        raise HTTPException(status_code=404, detail="Item not found")
    return {"item_id": item_id}
```

---

## **9. Dependency Injection**
```python
from fastapi import FastAPI, Depends

app = FastAPI()

def common_params(q: str = None, skip: int = 0, limit: int = 100):
    return {"q": q, "skip": skip, "limit": limit}

@app.get("/items/")
def read_items(commons: dict = Depends(common_params)):
    return commons
```
- Reusable logic (e.g., authentication, DB sessions).

---

## **10. Database Integration (SQLAlchemy)**
```python
from fastapi import FastAPI, Depends
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker, Session

SQLALCHEMY_DATABASE_URL = "sqlite:///./test.db"
engine = create_engine(SQLALCHEMY_DATABASE_URL)
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
Base = declarative_base()

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True, index=True)
    name = Column(String)

Base.metadata.create_all(bind=engine)

app = FastAPI()

def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()

@app.post("/users/")
def create_user(name: str, db: Session = Depends(get_db)):
    db_user = User(name=name)
    db.add(db_user)
    db.commit()
    return {"name": name}
```

---

## **11. Authentication (JWT)**
```python
from fastapi import FastAPI, Depends, HTTPException
from fastapi.security import OAuth2PasswordBearer

app = FastAPI()
oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/protected/")
def protected_route(token: str = Depends(oauth2_scheme)):
    if token != "secret-token":
        raise HTTPException(status_code=401, detail="Unauthorized")
    return {"message": "Access granted"}
```

---

## **12. Deployment**
### **Using Uvicorn in Production**
```bash
uvicorn main:app --host 0.0.0.0 --port 80
```

### **Docker Deployment**
```dockerfile
FROM tiangolo/uvicorn-gunicorn-fastapi:python3.9

COPY ./app /app
```

### **Deploy to Cloud (AWS, GCP, Azure)**
- Use **Docker** or **serverless** (AWS Lambda + API Gateway).

---

## **Next Steps**
- **WebSockets**: Real-time communication.  
- **Background Tasks**: Send emails, process data async.  
- **Testing**: Use `TestClient` for API tests.  
- **Middleware**: CORS, logging, rate-limiting.  

