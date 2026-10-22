# WordPress Deployment Using Docker Compose

## Project Overview
This project deploys a WordPress application and a MySQL database using Docker Compose. Docker Compose manages both containers and allows them to communicate with each other.

## Technologies Used
- Docker
- Docker Compose
- WordPress
- MySQL

## Architecture
- **WordPress:** Runs the web application and exposes port `8002` on the host.
- **MySQL:** Stores WordPress data in a MySQL database.
- **Docker Volume:** The `db_data` volume persists MySQL data.
- **Container Networking:** WordPress connects to MySQL using the service name `db` on port `3306`.

## Project Structure

```text
docker-compose-exer/
├── docker-compose.yml
└── README.md
```

## Prerequisites
- Docker installed
- Docker Compose installed
- Terminal access

## Steps to Deploy

### 1. Clone the Repository

```bash
git clone https://github.com/akshayaajitkumar-crypto/Deploying-Multi-Tier-Application--Docker.git
cd Deploying-Multi-Tier-Application--Docker
```

### 2. Start the Application

```bash
docker compose up -d
```

This starts the WordPress and MySQL containers in the background.

### 3. Check Container Status

```bash
docker compose ps
```

### 4. Access WordPress

Open the following URL in your browser:

http://localhost:8002

### 5. Access the MySQL Database

Connect to MySQL inside the database container:

```bash
docker compose exec db mysql -u wp_user -p
```

Enter the database password when prompted.

Select the WordPress database:

```sql
USE wp_database;
```

List the database tables:

```sql
SHOW TABLES;
```

View WordPress posts:

```sql
SELECT ID, post_title, post_status FROM wp_posts;
```

### 6. View Container Logs

```bash
docker compose logs
```

To view logs for a specific service:

```bash
docker compose logs wordpress
docker compose logs db
```

### 7. Stop the Application

```bash
docker compose down
```

This stops and removes the containers but preserves the named database volume.

To also remove the database volume and its stored data, run:

```bash
docker compose down -v
```

**Warning:** The `-v` option deletes the database volume and its data.

## Key Learn
