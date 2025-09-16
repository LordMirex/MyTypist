# MyTypist Application Setup Guide

This guide will help you set up the MyTypist document automation platform from scratch, including database tables, Redis, and all necessary infrastructure.

## 📋 Prerequisites

- **Python 3.11+** (Required for modern async features)
- **PostgreSQL 12+** (Primary database)
- **Redis 6+** (Caching and background tasks)
- **Git** (Version control)

## 🚀 Quick Setup (Replit Environment)

### 1. **Database Setup**
```bash
# Replit automatically provides PostgreSQL
# Check if DATABASE_URL is available
echo $DATABASE_URL
```

### 2. **Install Dependencies**
```bash
# Install all required packages

pip install -r pyproject.toml
```

### 3. **Initialize Database Tables**
```bash
# Run all migrations to create tables
alembic upgrade head
```

### 4. **Start Services**
```bash
# Start Redis (background)
redis-server redis.conf &

# Start Celery worker (background tasks)
celery -A app.tasks.celery worker --loglevel=info &

# Start FastAPI application
python main.py
```

---

## 🔧 Detailed Setup Instructions

### **Step 1: Environment Configuration**

Create or verify environment variables:

```bash
# Database Configuration (Auto-configured in Replit)
DATABASE_URL=postgresql://user:password@host:port/database

# Redis Configuration
REDIS_HOST=localhost
REDIS_PORT=6000
REDIS_URL=redis://localhost:6000

# Security Keys (REQUIRED)
SECRET_KEY=your-32-character-secret-key-here
JWT_SECRET_KEY=your-jwt-secret-key-32-chars-min

# Application Settings
DEBUG=true
APP_NAME=MyTypist
APP_VERSION=1.0.0

# External Services (Optional for basic setup)
SENDGRID_API_KEY=your-sendgrid-key
FLUTTERWAVE_SECRET_KEY=your-flutterwave-key
```

### **Step 2: Database Setup & Migrations**

#### **2.1 Initialize Alembic (First time only)**
```bash
# Alembic is already configured, but to reset:
alembic init alembic  # Only if starting fresh
```

#### **2.2 Create All Database Tables**
The application includes comprehensive migrations for all tables:

```bash
# View migration history
alembic history --verbose

# Run all migrations (creates all tables)
alembic upgrade head
```

#### **2.3 Database Tables Created**
The migrations will create these core tables:

**Core Tables:**
- `users` - User accounts and authentication
- `templates` - Document templates with metadata
- `documents` - Generated documents and processing history
- `audit_logs` - Security and compliance logging

**Feature Tables:**
- `document_shares` - Document sharing and access control
- `referral_programs` & `referral_tracking` - Referral system
- `notifications` - User notifications
- `visits` - Analytics and tracking

**Payment & Business:**
- `payments` - Transaction records
- `subscriptions` - User subscriptions

#### **2.4 Verify Database Setup**
```python
# Test database connection
python -c "
from database import engine, SessionLocal
from sqlalchemy import text
db = SessionLocal()
result = db.execute(text('SELECT table_name FROM information_schema.tables WHERE table_schema = \\'public\\''))
tables = [row[0] for row in result]
print('Created tables:', tables)
db.close()
"
```

### **Step 3: Redis Setup**

#### **3.1 Start Redis Server**
```bash
# Using the provided configuration
redis-server redis.conf

# Or default Redis
redis-server --port 6000 --daemonize yes
```

#### **3.2 Verify Redis Connection**
```bash
# Test Redis connectivity
redis-cli -p 6000 ping
# Should return: PONG
```

### **Step 4: Background Task Setup (Celery)**

#### **4.1 Start Celery Worker**
```bash
# Start Celery worker for background tasks
celery -A app.tasks.celery worker --loglevel=info

# For development with auto-reload
celery -A app.tasks.celery worker --loglevel=info --reload
```

#### **4.2 Verify Celery**
```python
# Test Celery connection
python -c "
from app.tasks.celery import app
result = app.control.ping()
print('Celery workers:', result)
"
```

### **Step 5: Application Startup**

#### **5.1 Development Mode**
```bash
# Start FastAPI with auto-reload
python main.py

# Or using uvicorn directly
uvicorn main:app --host 0.0.0.0 --port 5000 --reload
```

#### **5.2 Production Mode**
```bash
# Using Gunicorn for production
gunicorn -c gunicorn.conf.py main:app

# Or direct configuration
gunicorn --bind 0.0.0.0:5000 --workers 4 --worker-class uvicorn.workers.UvicornWorker main:app
```

---

## 🔍 Verification & Testing

### **Test Database Connection**
```bash
# Run database tests
python -c "
from database import SessionLocal
from app.models.user import User
db = SessionLocal()
print('Database connection:', 'SUCCESS' if db else 'FAILED')
print('User table exists:', bool(db.query(User).first() or True))
db.close()
"
```

### **Test API Endpoints**
```bash
# Test health endpoint
curl http://localhost:5000/health

# Test API documentation
# Visit: http://localhost:5000/api/docs
```

### **Run Test Suite**
```bash
# Run all tests
python run_tests.py

# Or using pytest directly
pytest app/tests/ -v
```

---

## 📂 Directory Structure

```
mytypist/
├── alembic/                    # Database migrations
│   ├── versions/              # Migration files
│   ├── env.py                 # Alembic configuration
│   └── alembic.ini           # Alembic settings
├── app/
│   ├── models/               # SQLAlchemy models
│   ├── routes/               # API endpoints
│   ├── services/             # Business logic
│   ├── tasks/                # Celery background tasks
│   ├── middleware/           # FastAPI middleware
│   └── utils/                # Utility functions
├── storage/                  # File storage
│   ├── documents/            # Generated documents
│   └── templates/            # Template files
├── main.py                   # FastAPI application entry point
├── database.py               # Database configuration
├── config.py                 # Application settings
├── gunicorn.conf.py          # Production server config
└── pyproject.toml            # Dependencies
```

---

## 🔧 Troubleshooting

### **Database Issues**
```bash
# Reset database (DANGER: Loses all data)
alembic downgrade base
alembic upgrade head

# Check migration status
alembic current
alembic history
```

### **Redis Issues**
```bash
# Check Redis status
redis-cli -p 6000 info

# Restart Redis
pkill redis-server
redis-server redis.conf
```

### **Permission Issues**
```bash
# Fix storage permissions
chmod -R 755 storage/
mkdir -p storage/documents storage/templates
```

### **Port Conflicts**
```bash
# Check what's using port 5000
lsof -i :5000

# Use different port
export PORT=8000
python main.py
```

---

## 🌐 Production Deployment

### **Environment Variables for Production**
```bash
# Security (REQUIRED)
export DEBUG=false
export SECRET_KEY="production-secret-key-32-chars-minimum"
export JWT_SECRET_KEY="production-jwt-key-32-chars-minimum"

# Database (Use production PostgreSQL)
export DATABASE_URL="postgresql://user:pass@host:port/dbname"

# Redis (Use production Redis)
export REDIS_URL="redis://host:port"

# External Services
export SENDGRID_API_KEY="your-production-sendgrid-key"
export FLUTTERWAVE_SECRET_KEY="your-production-flutterwave-key"
```

### **Production Startup**
```bash
# Run migrations
alembic upgrade head

# Start services
gunicorn -c gunicorn.conf.py main:app
```

---

## 📊 Database Schema Overview

### **Core Tables:**
- **users**: Authentication and user management
- **templates**: Document templates with placeholders
- **documents**: Generated documents and metadata
- **audit_logs**: Security and compliance tracking

### **Feature Tables:**
- **document_shares**: Secure document sharing
- **notifications**: User notification system
- **referral_programs**: Marketing and referrals
- **payments**: Transaction processing

### **Indexes & Performance:**
- Automatic indexing on foreign keys
- Performance indexes on frequently queried fields
- Connection pooling for high concurrency

---

## ✅ Quick Verification Checklist

- [ ] **Database**: `alembic upgrade head` completes successfully
- [ ] **Redis**: `redis-cli -p 6000 ping` returns PONG
- [ ] **Celery**: Worker starts without errors
- [ ] **API**: `curl http://localhost:5000/health` returns 200
- [ ] **Storage**: `storage/` directories exist with correct permissions
- [ ] **Tests**: `python run_tests.py` passes

---

## 🆘 Support

If you encounter issues:

1. **Check logs**: Application logs contain detailed error information
2. **Verify environment**: Ensure all environment variables are set
3. **Test connections**: Database and Redis connectivity
4. **Review migrations**: Check if all database tables exist
5. **Port availability**: Ensure ports 5000, 6000 are available

---

**🎉 Your MyTypist application should now be running successfully!**

Access the API documentation at: `http://localhost:5000/api/docs`
