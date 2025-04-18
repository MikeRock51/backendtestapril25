<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Expense Management API

## About The Project

This is a multi-tenant expense management API built with Laravel. The API allows companies and their employees to track and manage expenses effectively.

## Tech Stack

- **Framework**: Laravel
- **Database**: PostgreSQL
- **Authentication**: Laravel Sanctum for API token authentication
- **Background Jobs**: Laravel Queue with database driver
- **Email**: Laravel Mail

## Features

- Multi-tenant architecture supporting multiple companies
- User roles and permissions
- Expense tracking and categorization
- Audit logging for all operations
- Weekly expense reports via email
- API for mobile and web clients

## Requirements

- PHP >= 10
- Composer
- PostgreSQL >= 14
- PHP extensions: pdo_pgsql, pgsql

## Installation

1. Clone the repository:
   ```bash
   git clone [repository-url]
   cd backendtestapril25
   ```

2. Install dependencies:
   ```bash
   composer install
   ```

3. Setup environment:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. Configure the database in `.env`:
   ```
   DB_CONNECTION=pgsql
   DB_HOST=127.0.0.1
   DB_PORT=5432
   DB_DATABASE=backendtestapril25
   DB_USERNAME=postgres
   DB_PASSWORD=postgres
   ```

5. Run migrations and seed the database:
   ```bash
   php artisan migrate:fresh --seed
   ```

6. Start the development server:
   ```bash
   php artisan serve
   ```

## API Documentation

### Authentication

```
POST /api/login
POST /api/logout
POST /api/register
```

### Companies

```
GET /api/companies
GET /api/companies/{id}
POST /api/companies
PUT /api/companies/{id}
DELETE /api/companies/{id}
```

### Users

```
GET /api/users
GET /api/users/{id}
POST /api/users
PUT /api/users/{id}
DELETE /api/users/{id}
```

### Expenses

```
GET /api/expenses
GET /api/expenses/{id}
POST /api/expenses
PUT /api/expenses/{id}
DELETE /api/expenses/{id}
```

### Audit Logs

```
GET /api/audit-logs
GET /api/audit-logs/{id}
```

## Background Jobs

The application includes scheduled tasks for:

- Weekly expense reports sent via email to company admins
- Audit log cleanup

To run the scheduler:

```bash
php artisan schedule:run
```

To process queued jobs:

```bash
php artisan queue:work
```

## Testing

Run tests with:

```bash
php artisan test
```

## Development

The project follows the Laravel best practices. Here are some useful commands for development:

```bash
# Clear application cache
php artisan cache:clear

# Create a new migration
php artisan make:migration create_new_table

# Create a new controller
php artisan make:controller NewController

# Create a new model with migration and factory
php artisan make:model NewModel -mf
```

## Deployment

For production deployment:

1. Set appropriate environment variables
2. Optimize the application:
   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

3. Set up a proper web server (Nginx/Apache)
4. Configure a process manager for queue workers
