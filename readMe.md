# Express API with MySQL and Redis

This project demonstrates an Express.js API integrated with MySQL and Redis. It includes CRUD operations with caching implemented using Redis.

## Features

- **CRUD Operations**: Create, read, update, and delete user records.
- **Caching**: Utilizes Redis for caching user data to improve performance.
- **Scheduled Tasks**: Updates MySQL with any changes made to the Redis cache every 10 seconds.

## Prerequisites

- Node.js
- Docker and Docker Compose

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/chaloemchai-beer/Learn_Redis_Cache.git
    cd Learn_Redis_Cache
    ```

2. **Install dependencies:**

    ```bash
    npm install
    ```

3. **Configure Docker Compose:**

    Ensure Docker and Docker Compose are installed. You can modify the `docker-compose.yml` file if needed.

4. **Start the services:**

    ```bash
    docker-compose up
    ```

5. **Start the Express server:**

    ```bash
    npm start
    ```

    The server will be running on `http://localhost:8000`.

6. **Build users Database in phpmyadmin:**
    build users table and add column data
## API Endpoints

### Get Users

- **Endpoint:** `/users`
- **Method:** `GET`
- **Description:** Retrieves all users from MySQL.

### Get Users with Cache 1

- **Endpoint:** `/users/cache-1`
- **Method:** `GET`
- **Description:** Retrieves users from Redis cache if available; otherwise, fetches from MySQL and updates the cache.

### Get Users with Cache 2

- **Endpoint:** `/users/cache-2`
- **Method:** `GET`
- **Description:** Similar to `/users/cache-1`, but uses a different cache key.

### Add User

- **Endpoint:** `/users`
- **Method:** `POST`
- **Description:** Adds a new user to MySQL and updates the Redis cache.

### Get Users with Cache 3

- **Endpoint:** `/users/cache-3`
- **Method:** `GET`
- **Description:** Similar to `/users/cache-1`, but uses a different cache key.

### Update User

- **Endpoint:** `/users/:id`
- **Method:** `PUT`
- **Description:** Updates an existing user in MySQL and updates the Redis cache.

## Docker Compose Configuration

- **db**: MySQL service with the `tutorial` database.
- **phpmyadmin**: Provides a web interface to manage MySQL.
- **redis**: Redis caching service.

## Cron Job

A cron job runs every 10 seconds to update MySQL with any changes made to the Redis cache.

## Error Handling

The API handles errors by logging them to the console and returning a 500 status code with an error message.

## License

This project is licensed under the MIT License.

