# **Python Requests Module Tutorial**  
*(Making HTTP Requests in Python)*  

The `requests` library is the **most popular** Python library for making HTTP requests. It simplifies working with APIs, web scraping, and handling web data.  

---

## **Table of Contents**  
1. [Installation](#installation)  
2. [Making a GET Request](#making-a-get-request)  
3. [Passing Parameters in URLs](#passing-parameters-in-urls)  
4. [Handling JSON Responses](#handling-json-responses)  
5. [Making POST Requests](#making-post-requests)  
6. [Handling Headers & Authentication](#handling-headers--authentication)  
7. [Handling Cookies & Sessions](#handling-cookies--sessions)  
8. [Error Handling & Timeouts](#error-handling--timeouts)  
9. [Downloading Files](#downloading-files)  
10. [Advanced Usage (Streaming, Proxies)](#advanced-usage-streaming-proxies)  

---

## **1. Installation**  
```bash
pip install requests
```

---

## **2. Making a GET Request**  
```python
import requests

response = requests.get("https://jsonplaceholder.typicode.com/posts/1")
print(response.status_code)  # 200 (Success)
print(response.text)  # Raw response text
```

**Output:**  
```json
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit..."
}
```

---

## **3. Passing Parameters in URLs**  
```python
params = {"userId": 1}
response = requests.get(
    "https://jsonplaceholder.typicode.com/posts",
    params=params
)
print(response.url)  # https://jsonplaceholder.typicode.com/posts?userId=1
```

---

## **4. Handling JSON Responses**  
```python
response = requests.get("https://jsonplaceholder.typicode.com/posts/1")
data = response.json()  # Parse JSON into a Python dict

print(data["title"])  # "sunt aut facere..."
```

---

## **5. Making POST Requests**  
```python
new_post = {
    "title": "Hello World",
    "body": "This is a test post",
    "userId": 1
}

response = requests.post(
    "https://jsonplaceholder.typicode.com/posts",
    json=new_post  # Automatically sets Content-Type: application/json
)

print(response.json())  # Returns the created post with an ID
```

---

## **6. Handling Headers & Authentication**  
### **Custom Headers**  
```python
headers = {
    "User-Agent": "MyApp/1.0",
    "Authorization": "Bearer abc123"
}

response = requests.get(
    "https://api.example.com/data",
    headers=headers
)
```

### **Basic Authentication**  
```python
from requests.auth import HTTPBasicAuth

response = requests.get(
    "https://api.example.com/protected",
    auth=HTTPBasicAuth("username", "password")
)
```

---

## **7. Handling Cookies & Sessions**  
### **Reading Cookies**  
```python
response = requests.get("https://example.com")
print(response.cookies)  # <RequestsCookieJar[...]>

for cookie in response.cookies:
    print(f"{cookie.name}: {cookie.value}")
```

### **Using Sessions (Persistent Cookies)**  
```python
session = requests.Session()

# First request (sets cookies)
session.get("https://example.com/login", auth=("user", "pass"))

# Subsequent requests reuse cookies
response = session.get("https://example.com/dashboard")
print(response.text)
```

---

## **8. Error Handling & Timeouts**  
### **Checking for Errors**  
```python
try:
    response = requests.get("https://example.com", timeout=5)
    response.raise_for_status()  # Raises HTTPError for bad responses (4xx, 5xx)
except requests.exceptions.RequestException as e:
    print(f"Error: {e}")
```

### **Setting Timeouts**  
```python
try:
    response = requests.get("https://example.com", timeout=(3.05, 27))  # (connect, read)
except requests.exceptions.Timeout:
    print("Request timed out!")
```

---

## **9. Downloading Files**  
```python
url = "https://example.com/image.jpg"
response = requests.get(url, stream=True)

with open("image.jpg", "wb") as f:
    for chunk in response.iter_content(chunk_size=8192):
        f.write(chunk)

print("File downloaded!")
```

---

## **10. Advanced Usage**  
### **Streaming Large Responses**  
```python
response = requests.get("https://example.com/large-data", stream=True)

for line in response.iter_lines():
    if line:
        print(line.decode("utf-8"))
```

### **Using Proxies**  
```python
proxies = {
    "http": "http://10.10.1.10:3128",
    "https": "http://10.10.1.10:1080"
}

response = requests.get("http://example.com", proxies=proxies)
```

