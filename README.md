# Todo App Backend

This is the backend for a Todo application built with FastAPI and SQLAlchemy, using MySQL as the database. I also created a frontend app to use this backend using React, which repo you can access here:

[https://github.com/fathiyul/todo-app-react](https://github.com/fathiyul/todo-app-react)

## Project Structure

```
backend/
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── models.py
│   ├── schemas.py
│   ├── database.py
│   └── crud.py
├── alembic/
│   └── ...
└── requirements.txt
```

- `main.py`: The main FastAPI application
- `models.py`: SQLAlchemy ORM models
- `schemas.py`: Pydantic models for request/response handling
- `database.py`: Database connection and session management
- `crud.py`: CRUD operations for interacting with the database

## Environment Setup

1. Create a `.env` file in the root directory of the project.
2. Add the following environment variables to the `.env` file:
   ```
   DB_USER=your_database_user
   DB_PASSWORD=your_database_password
   DB_HOST=localhost
   DB_NAME=todo_db
   ```
3. Replace `your_database_user` and `your_database_password` with your actual MySQL credentials.
4. Ensure that the `DB_NAME` matches the name of the database you created for this project.

Note: The `.env` file contains sensitive information and should never be committed to version control. It's already included in the `.gitignore` file.

## Setup

1. Clone the repository:
   ```
   git clone <repository-url>
   cd <repository-name>/backend
   ```

2. Create a virtual environment and activate it:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

4. Set up your MySQL database and update the connection string in `app/database.py`:
   ```python
   SQLALCHEMY_DATABASE_URL = "mysql://username:password@localhost/todo_db"
   ```

5. Run the application:
   ```
   uvicorn app.main:app --reload
   ```

The API will be available at `http://localhost:8000`.

## API Endpoints

### Users

- `POST /users/`: Create a new user
  - Request body: `{"username": "string", "password": "string"}`

- `POST /users/login`: User login
  - Request body: `{"username": "string", "password": "string"}`

### Todos

- `GET /todos/{user_id}`: Get all todos for a user

- `POST /todos/{user_id}`: Create a new todo for a user
  - Request body: `{"text": "string", "completed": false}`

- `PUT /todos/{todo_id}`: Update a todo
  - Request body: `{"text": "string", "completed": boolean}`

- `DELETE /todos/{todo_id}`: Delete a todo

## Authentication

This API uses simple username/password authentication. In a production environment, you should implement more secure authentication methods like JWT.

## Database Migrations

This project uses Alembic for database migrations. To create a new migration:

```
alembic revision --autogenerate -m "Description of the change"
```

To apply migrations:

```
alembic upgrade head
```

## Testing

(Add information about how to run tests once you've implemented them)

## Contributing

(Add guidelines for contributing to the project)

## License

(Add license information)
