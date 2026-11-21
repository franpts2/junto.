# junto.

A social platform that connects people through shared music, films, and books.

<p align="left">
  <img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel">
  <img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP">
  <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS">
  <img src="https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E" alt="JavaScript">
</p>

## About

Junto is a full-featured social media platform designed to bring people together through shared cultural interests. The platform combines traditional social networking features with media discovery, allowing users to connect, share, and discuss their favorite movies, books, and music.

## Features

### Authentication & User Management

- Secure authentication (email/password, Google OAuth)
- Password recovery via email
- Customizable user profiles (bio, avatar, favorites)
- Block/unblock system with appeal mechanism
- Privacy controls for connections and visibility

### Social Feed & Interactions

- Personalized timeline (friends & groups)
- Post creation with text and images
- Media reviews (movies, books, music)
- Like and comment system
- Real-time AJAX feed updates
- Content filtering (all/friends-only)

### Messaging System

- Direct messages (private chat)
- Real-time chat updates
- Conversation management (delete, history)
- Mention system (@user tagging)

### Friend Network

- Send/accept/reject friend requests
- Friends list and management
- User search and discovery
- Dedicated friends feed

### Media Library Integration

- Browse/search movies, books, music
- Add media to favorites
- Share reviews and ratings

### Groups & Communities

- Create and manage groups
- Admin/member roles
- Join/invite requests
- Group posts and discussions

### Advanced Search

- Search users, posts, comments, groups
- Full-text and filtered search

### Administration & Moderation

- Admin dashboard
- User moderation (block/unblock, appeals)
- Content reports and review
- Platform analytics

### Notification System

- Friend requests, group invites
- Likes, comments, and message alerts

## How It Works

**Tech Stack**

- Framework: Laravel 12.x (PHP 8.2+)
- Database: PostgreSQL (Dockerized)
- Frontend: TailwindCSS 4.0, Vite
- Authentication: Laravel Sanctum, Google OAuth
- Storage: Local filesystem for uploads
- Development: Docker Compose

**System Architecture**

```
┌─────────────────────────────┐
│   Frontend (Blade + Vite)   │
│   TailwindCSS + JavaScript  │
├─────────────────────────────┤
│   Laravel 12 Backend        │
│   (MVC + Policies)          │
├─────────────────────────────┤
│   PostgreSQL Database       │
│   (Docker Container)        │
└─────────────────────────────┘
```

**Database Schema**

- Users & Authentication: users, password resets, sessions
- Social Network: friend requests, friendships, followers
- Content: posts, reviews, comments, likes
- Groups: groups, memberships, invites, join requests
- Media: movies, books, music, favorites
- Messaging: direct messages
- Notifications: friend requests, group invites, mentions
- Moderation: reports, blocks, unblock appeals
- Security: login attempts, session management

**Key Laravel Features**

- Eloquent ORM (rich relationships)
- Authorization policies
- Form validation
- Middleware (auth, guards)
- Service layer abstraction
- File uploads (images)
- Email notifications

## Quick Start

### Prerequisites

- PHP 8.2+
- Composer 2.2+
- Docker & Docker Compose
- Node.js 18+

### Quick Start

1. **Clone the repository**

2. **Install dependencies**
    ```bash
    composer install
    npm install
    ```
3. **Start PostgreSQL with Docker**
    ```bash
    docker compose up -d
    ```
4. **Configure environment**
    ```bash
    cp .env.example .env
    php artisan key:generate
    ```
    Update `.env` with database credentials:
    ```
    DB_CONNECTION=pgsql
    DB_HOST=localhost
    DB_PORT=5432
    DB_DATABASE=postgres
    DB_USERNAME=postgres
    DB_PASSWORD=password
    ```
5. **Seed the database**
    ```bash
    php artisan db:seed
    ```
6. **Build frontend assets**
    ```bash
    npm run build
    # Or for development with hot reload:
    npm run dev
    ```
7. **Start the development server**
    ```bash
    php artisan serve
    ```

Access the application at http://localhost:8000

#### Docker Quick Run

To run the app with Docker only:

```bash
docker run -d --name lbaw2544 -p 8001:80 gitlab.up.pt:5050/lbaw/lbaw2526/lbaw2544
```

_P.S. only available upon FEUP authentication in Docker_

#### Database Management

pgAdmin 4 is available at http://localhost:4321 to manage the PostgreSQL database.

Connection details:

- Hostname: postgres
- Username: postgres
- Password: password

#### Troubleshooting

**Database connection issues:**

```bash
docker compose down
docker compose up -d
php artisan db:seed
```

**Asset compilation errors:**

```bash
npm ci
npm run build
```

## Test Credentials

You can use the seeded database accounts or create your own.

### Administration Credentials

| Email             | Password |
| ----------------- | -------- |
| admin@example.org | 1234     |

### User Credentials

| Type          | Email             | Password |
| ------------- | ----------------- | -------- |
| basic account | alice@example.org | 1234     |
| basic account | bruno@example.org | 1234     |

## Project Structure

```
junto/
├── app/
│   ├── Helpers/               # Utility helpers
│   ├── Http/
│   │   ├── Controllers/       # Request handlers
│   │   ├── Middleware/        # Request filters
│   ├── Models/                # Eloquent models
│   ├── Policies/              # Authorization rules
│   └── Services/              # Business logic
├── bootstrap/                 # App bootstrap files
├── config/                    # Configuration files
├── database/
│   ├── factories/             # Model factories
│   ├── migrations/            # Database schema
│   ├── seeders/               # Seed classes
│   └── junto-seed.sql         # Initial data
├── docs/
│   └── a7_openapi.yaml        # API specification
├── etc/                       # Docker, nginx, php configs
├── public/                    # Public assets (entry, css, js, images)
├── resources/
│   ├── css/                   # Stylesheets
│   ├── js/                    # JavaScript modules
│   └── views/                 # Blade templates
│       ├── components/        # Reusable UI components (admin, account, dashboard, groups, etc.)
│       ├── errors/            # Error pages (404, etc.)
│       ├── layouts/           # Layout templates (admin, app, auth, base, minimal)
│       ├── pages/             # Main pages (about, home, features, admin, auth, groups, messages, notifications, profile, search)
├── routes/
│   ├── console.php            # CLI routes
│   └── web.php                # Application routes
├── storage/                   # Logs, cache, uploads
├── tests/                     # PHPUnit tests
├── vendor/                    # Composer dependencies
├── videos/                    # Video Demo
├── artisan                    # Laravel CLI
├── composer.json              # Composer dependencies
├── docker-compose.yaml        # Docker services
├── Dockerfile                 # Docker build file
├── package.json               # Node dependencies
├── phpunit.xml                # PHPUnit config
├── README.md                  # Project documentation
├── vite.config.js             # Vite config
└── upload_image.sh            # Image upload script
```

## Video Demo & API Documentation

- **Video Demo:**
    - The project video demonstration is available at [videos/lbaw2544.mp4](videos/lbaw2544.mp4). Open this file to watch the latest demo showcasing the platform's features and user experience.

- **API Documentation & Certificates:**
    - The OpenAPI (Swagger) specification for the platform's API is available in `docs/a7_openapi.yaml`. This file provides a comprehensive description of available API endpoints, request/response formats, and authentication requirements.
    - The `docs/` folder also contains project-related certificates (CSS and HTML reports and also checklists of usability and Accessibility).

## Team & Course

**Team**

This project was developed by:

- [Francisca Portugal](https://github.com/franpts2)
- [Francisco Bandeira](https://github.com/fmbb8)
- [Maria Luiza Vieira](https://github.com/maluviieira)
- [Pedro Lunet](https://github.com/PedroLunet)

**Course**

Developed for the LBAW (Database and Web Applications Laboratory) course at FEUP (Faculty of Engineering, University of Porto).

Course: LBAW 2024/2025  
Project Code: lbaw2544

## License

Coursework submitted at FEUP. Shared for reference; all rights reserved unless stated otherwise.

---

_junto. — culture, together._
