# FastAPI Book API with CI/CD Pipeline and Nginx Reverse Proxy

This is a FastAPI-based Book Management API that supports CRUD operations for managing books. The project is configured with CI/CD using GitHub Actions and is deployed on Render, with Nginx as a reverse proxy.

## Features

- ✅ Create, Retrieve, Update, and Delete books
- ✅ FastAPI framework with Pydantic models
- ✅ PostgreSQL database (or in-memory storage)
- ✅ CI/CD pipeline using GitHub Actions
- ✅ Automatic deployment on Render
- ✅ Nginx reverse proxy for efficient request handling

## API Endpoints

| Method   | Endpoint                  | Description                     |
|----------|---------------------------|---------------------------------|
| POST     | `/api/v1/books/`          | Add a new book                  |
| GET      | `/api/v1/books/`          | Get all books                   |
| GET      | `/api/v1/books/{book_id}` | Get a specific book by ID       |
| PUT      | `/api/v1/books/{book_id}` | Update book details             |
| DELETE   | `/api/v1/books/{book_id}` | Delete a book                   |

## Installation & Running Locally

1. **Clone the Repository:**
    ```bash
    git clone https://github.com/zuuhair11/Hng12_Backend_S01_Application-with-CI-CD-Pipeline
    cd Hng12_Backend_S01_Application-with-CI-CD-Pipeline
    ```

2. **Create a Virtual Environment & Activate it:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4. **Run the Application:**
    ```bash
    uvicorn main:app --reload
    ```

5. **Access the API:**
    - Open your browser and go to [http://127.0.0.1:8000](http://127.0.0.1:8000).

## Deployment & CI/CD Setup

### Continuous Integration (CI)
- The CI pipeline runs automatically on every pull request to the main branch. It executes unit tests using pytest to ensure code quality.

### Continuous Deployment (CD)
- The CD pipeline deploys the application on Render whenever changes are merged into the main branch.

## Nginx Reverse Proxy Setup

Nginx is configured to route requests to the FastAPI backend efficiently. Below is an example `nginx.conf`:

```txt
server {
    listen 80;
    server_name https://hng12-backend-s01-application-with-ci-cd.onrender.com;

    location / {
        proxy_pass http://localhost:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

## Running Tests

To run tests, use the following command:

```bash
pytest
```

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any inquiries, please contact [your-email@example.com](mailto:your-email@example.com).
