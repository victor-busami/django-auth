generate a better readme,one that is pproperly formated and uses relevant beautiful emojis to strengthen whats been talked about.also,do not remove anything from this readme - i want it to act as a guide of the steps i have taken in building this app 


# 🧠 Mental Health App - Django REST API Backend

A comprehensive Django REST API backend for a mental health application with JWT authentication, custom user management, and PostgreSQL database integration.

## 🚀 Project Setup & Development Journey

### 🏗️ Step 1: Set up a Virtual Environment
Django projects are best kept isolated from your system Python using a virtual environment.
```bash
python -m venv env
.\env\Scripts\Activate.ps1  # Windows PowerShell
```

### 🎯 Step 2: Create Your Django Project
```bash
django-admin startproject core .
```

### 🌐 Step 3: Run the Development Server
Let's test it out!
```bash
python manage.py runserver
```
You should see the Django welcome page! 🎉

### 🚫 Step 4: Disable Django Admin
Streamlined the project by removing unnecessary admin functionality for this API-focused application.

### 🔐 Step 5: Create the Auth App
```bash
python manage.py startapp authapp
```

### 👤 Step 6: Create the Custom User Model
Django comes with a default User model, but we'll make our own to customize it.
- Email-based authentication instead of username
- Custom user manager for proper user creation
- Extended user fields for mental health app requirements

### ⚙️ Step 7: Configure Django to Use the Custom User
This tells Django to use your custom user instead of the default.
```python
AUTH_USER_MODEL = 'authapp.CustomUser'
```

### 🗃️ Step 8: Run Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

✅ Your project is now using a custom user model. Next, we'll structure the authapp with:
- 📝 **serializers**
- 👁️ **views** 
- 🛣️ **URLs**

And then build the REST API endpoints for signup, login, logout, and delete.

### 📁 Step 9: Structure the authapp
Inside the authapp folder, create the following files/folders for better organization:
- `serializers.py` - Data validation and serialization
- `views.py` - API endpoint logic
- `urls.py` - URL routing patterns

### 🔄 Step 10: Create Serializers for User and Auth Actions
In `authapp/serializers.py`:
- `UserSerializer` - User data representation
- `RegisterSerializer` - User registration validation
- `LoginSerializer` - Login credentials validation

### 🎭 Step 11: Create Auth Views
Implemented comprehensive authentication views:
- `RegisterView` - User registration endpoint
- `LoginView` - User login with JWT token generation
- `LogoutView` - Secure logout with token blacklisting
- `DeleteAccountView` - Account deletion functionality

### 🛣️ Step 12: Create URL Routes
Configured URL patterns for all authentication endpoints with proper API versioning.

### 🔧 Step 13: Install Django REST Framework & JWT
```bash
pip install djangorestframework
pip install djangorestframework-simplejwt
```
Added to `INSTALLED_APPS`:
- `rest_framework`
- `rest_framework_simplejwt`
- `rest_framework_simplejwt.token_blacklist`

### 🐘 Step 14: Switch to PostgreSQL
Migrated from SQLite to PostgreSQL for production-ready database management:
```bash
pip install psycopg2-binary
```

### 🚀 Step 15: Run Your Django Server
```bash
python manage.py runserver
```

---

## 🧪 API Testing Guide with Postman

### 📝 1. Register (Signup)
**Method:** `POST`  
**URL:** `http://127.0.0.1:8000/api/auth/signup/`  
**Body (JSON):**
```json
{
  "email": "test@example.com",
  "name": "Test User",
  "password": "password123"
}
```
**✅ Expected Response:**
```json
{
  "email": "test@example.com",
  "name": "Test User",
  "id": 1
}
```

### 🔑 2. Login
**Method:** `POST`  
**URL:** `http://127.0.0.1:8000/api/auth/login/`  
**Body (JSON):**
```json
{
  "email": "test@example.com",
  "password": "password123"
}
```
**✅ Expected Response:**
```json
{
  "user": {
    "id": 1,
    "email": "test@example.com",
    "name": "Test User"
  },
  "tokens": {
    "refresh": "<refresh_token>",
    "access": "<access_token>"
  }
}
```
**📋 Copy both access and refresh tokens — you'll need them below.**

### 🚪 3. Logout
**Method:** `POST`  
**URL:** `http://127.0.0.1:8000/api/auth/logout/`  
**Body (JSON):**
```json
{
  "refresh": "<paste_your_refresh_token_here>"
}
```
**Header:**
```
Authorization: Bearer <access_token>
```
**✅ Expected Response:** Status `205 Reset Content`

### 🗑️ 4. Delete Account
**Method:** `DELETE`  
**URL:** `http://127.0.0.1:8000/api/auth/delete/`  
**Header:**
```
Authorization: Bearer <access_token>
```
**✅ Expected Response:** Status `204 No Content`

---

## 🛠️ Tech Stack

- **🐍 Python 3.13** - Programming language
- **🎯 Django 5.2.3** - Web framework
- **🔧 Django REST Framework** - API development
- **🔐 Simple JWT** - JWT authentication
- **🐘 PostgreSQL** - Production database
- **🌐 Virtual Environment** - Dependency isolation

## 📦 Key Features

- ✅ **Custom User Model** with email authentication
- ✅ **JWT Token Authentication** with refresh/access tokens
- ✅ **Token Blacklisting** for secure logout
- ✅ **PostgreSQL Integration** for scalable data storage
- ✅ **RESTful API Design** following best practices
- ✅ **Comprehensive User Management** (CRUD operations)
- ✅ **Security Best Practices** implemented throughout

## 🚀 Quick Start

1. **Clone and navigate to project:**
   ```bash
   cd c:\Users\busam\Documents\mentalhealth\backend
   ```

2. **Activate virtual environment:**
   ```bash
   .\env\Scripts\Activate.ps1
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run migrations:**
   ```bash
   python manage.py migrate
   ```

5. **Start development server:**
   ```bash
   python manage.py runserver
   ```

6. **Test API endpoints** using the Postman guide above! 🎯

---

**Built with ❤️ for mental health awareness and support**