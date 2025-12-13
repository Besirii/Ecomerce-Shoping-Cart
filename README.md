Simple E-commerce Shopping Cart (Laravel)

A simple e-commerce shopping cart application built with Laravel, Livewire, and Tailwind CSS. The project demonstrates core e-commerce functionality while following Laravel best practices.

This project uses Laravel Breeze (Livewire) for authentication and ensures that each shopping cart is persisted per authenticated user using the database (no sessions or local storage).

📌 Features

User authentication (register, login, logout)

Product listing with price and stock

Add products to cart

Update cart item quantities

Remove items from cart

Cart persisted per authenticated user

Low stock email notification (Queue + Job)

Daily sales report email (Scheduled Job / Cron)

🧱 Tech Stack

Backend: Laravel

Frontend: Livewire

Authentication: Laravel Breeze

Styling: Tailwind CSS

Queues: Laravel Queue (Database driver)

Scheduling: Laravel Task Scheduler

Version Control: Git / GitHub

🚀 Installation & Setup
1. Clone the Repository

2. Install Dependencies
   composer install
   npm install && npm run dev
3. Environment Setup
   cp .env.example .env
   php artisan key:generate

Update .env with your database and mail credentials.

4. Database Migration
   php artisan migrate
5. Queue Configuration
   php artisan queue:table
   php artisan migrate

Update .env:

QUEUE_CONNECTION=database

Run the queue worker:

php artisan queue:work
🔐 Authentication

Authentication is handled by Laravel Breeze (Livewire).

Users must be authenticated to access cart features

Each user has exactly one cart

Cart data is always retrieved using auth()->user()

🗄️ Database Structure
Main Tables

users

products

carts

cart_items

orders

order_items

Key Relationships

User → hasOne Cart

Cart → hasMany CartItems

Product → hasMany CartItems

Order → hasMany OrderItems

🧩 Application Flow

User registers or logs in

User browses products

User adds products to their cart

Cart items can be updated or removed

Stock is reduced when items are added

Orders are stored for reporting

📉 Low Stock Notification

When a product’s stock_quantity falls below a defined threshold (e.g. ≤ 5)

A queued job is dispatched

An email notification is sent to a dummy admin user

Technologies Used:

Laravel Jobs

Laravel Queue

Laravel Mail

📊 Daily Sales Report

A scheduled job runs every evening

Collects all orders placed during the day

Sends a summary email to the dummy admin user

Scheduler Setup
* * * * * php /path/to/project/artisan schedule:run >> /dev/null 2>&1
          🎨 Styling

Built with Tailwind CSS

Clean and minimal UI

Responsive by default

🧪 Testing (Optional Enhancement)

You can extend the project by adding:

Feature tests for cart actions

Unit tests for jobs and services

📦 Git Workflow
git add .
git commit -m "Initial e-commerce shopping cart implementation"
📎 Notes

This project is intentionally kept simple

Designed to demonstrate Laravel fundamentals

Easy to extend with checkout, payments, or admin dashboard

✅ Summary

✔ Authenticated user-based cart storage
✔ Livewire-powered frontend
✔ Database-driven cart persistence
✔ Queue-based low stock alerts
✔ Scheduled daily sales report
✔ Laravel best practices followed
