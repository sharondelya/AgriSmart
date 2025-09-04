# Security Configuration Guide

## Overview
This document outlines the security measures implemented in the AgriSmart project and provides guidance for secure deployment.

## Environment Variables Setup

### Required Environment Variables
Before deploying or running the application, you must set up the following environment variables:

```bash
# Database Configuration
DB_HOST=your_database_host
DB_PORT=5432
DB_NAME=your_database_name
DB_USER=your_database_user
DB_PASSWORD=your_secure_database_password
DB_SSLMODE=require

# Application Security
SECRET_KEY=your_very_secure_secret_key_here

# Stripe Payment Configuration
STRIPE_PUBLISHABLE_KEY=pk_test_your_publishable_key_here
STRIPE_SECRET_KEY=sk_test_your_secret_key_here

# Admin Configuration (for initial setup)
ADMIN_EMAIL=admin@yourdomain.com
ADMIN_NAME=Admin
ADMIN_PASSWORD=your_secure_admin_password

# Application Environment
APP_ENV=production
DEBUG=false
```

### Setting Up Environment Variables

1. **Copy the example file:**
   ```bash
   cp .env.example .env
   ```

2. **Edit the .env file with your actual values:**
   - Never commit the `.env` file to version control
   - Use strong, unique passwords
   - Generate a secure SECRET_KEY (32+ characters)
   - Use production Stripe keys for live deployment

## Security Features Implemented

### 1. Environment Variable Protection
- All sensitive credentials moved to environment variables
- `.env` file added to `.gitignore`
- Default values provided for development

### 2. Database Security
- SSL mode enforced for database connections
- Parameterized queries to prevent SQL injection
- Password hashing using werkzeug security

### 3. Session Security
- Secure session configuration
- HTTP-only cookies
- Session key prefixing
- Configurable session lifetime

## Deployment Checklist

### Before Public Deployment:
- [ ] Verify `.env` file is not in repository
- [ ] Confirm `.gitignore` includes sensitive files
- [ ] Set strong SECRET_KEY in production
- [ ] Use production database credentials
- [ ] Enable SSL/HTTPS in production
- [ ] Set DEBUG=false in production
- [ ] Change default admin password
- [ ] Review and update Stripe keys for production

### Security Best Practices:
- [ ] Regular security updates for dependencies
- [ ] Monitor for suspicious activities
- [ ] Regular backup of database
- [ ] Use HTTPS for all communications
- [ ] Implement rate limiting for API endpoints
- [ ] Regular security audits

## Files Protected

The following files contain sensitive information and are protected:
- `.env` - Environment variables (gitignored)
- `app.py` - Now uses environment variables
- `Database_initialization.py` - Now uses environment variables

## Emergency Response

If credentials are accidentally exposed:
1. Immediately rotate all affected credentials
2. Update environment variables
3. Check logs for unauthorized access
4. Notify relevant stakeholders
5. Review and strengthen security measures

## Contact

For security concerns or questions, please contact the development team.
