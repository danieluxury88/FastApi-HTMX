- Run Command
```
gunicorn -c gunicorn_config.py main:app
or
uvicorn main:app --reload --port=9090
```

## Installation
```
python3 -m venv venv
source venv/bin/activate
pip install requirements.txt
```


## Resume
- This project is a web application built using the FastAPI framework. Here's a breakdown of the technologies and libraries used:

### Technologies and Libraries

1. **FastAPI**:
   - **Description**: FastAPI is a modern, fast (high-performance), web framework for building APIs with Python 3.6+ based on standard Python type hints.
   - **Usage**: The main application is created using FastAPI. It handles routing, request handling, and response generation.
   - **Relevant Code**:
     ```python
     from fastapi import FastAPI, Request, Form
     app = FastAPI()
     ```

2. **Jinja2**:
   - **Description**: Jinja2 is a templating engine for Python. It is used to generate HTML dynamically by combining templates with data.
   - **Usage**: Jinja2 is used to render HTML templates for the web pages.
   - **Relevant Code**:
     ```python
     from fastapi.templating import Jinja2Templates
     templates = Jinja2Templates(directory="templates")
     ```

3. **HTMLResponse**:
   - **Description**: A response class from FastAPI that returns HTML content.
   - **Usage**: Used to specify that the response should be HTML.
   - **Relevant Code**:
     ```python
     from fastapi.responses import HTMLResponse
     ```

### Project Structure

- **main.py**: The main application file where the FastAPI app is defined and routes are set up.
- **requirements.txt**: A file listing the dependencies required for the project.
- **templates/**: Directory containing HTML templates.
  - **items.html**: Template for displaying the list of items.
  - **partials/item.html**: Template for displaying a single item.

### Key Functionalities

1. **Get Items**:
   - **Route**: `GET /`
   - **Description**: Fetches and displays a list of items.
   - **Relevant Code**:
     ```python
     @app.get("/", response_class=HTMLResponse)
     def get_items(request: Request):
         return templates.TemplateResponse("items.html", {"request": request, "items": items})
     ```

2. **Add Item**:
   - **Route**: `POST /add-item`
   - **Description**: Adds a new item to the list and displays it.
   - **Relevant Code**:
     ```python
     @app.post("/add-item")
     def add_item(request: Request, item: str = Form(...)):
         items.append(item)
         return templates.TemplateResponse("partials/item.html", {"request": request, "item": item})
     ```

### Running the Project

To run this project, you would typically use a command like:
```sh
uvicorn main:app --reload
```
This command starts the FastAPI application using Uvicorn, an ASGI server.

### Dependencies

The [`requirements.txt`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fdaniel%2FSites%2FDevTools%2FPythonDev%2Ffastapi-htmx-demo%2Frequirements.txt%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22e0b46eff-3dea-4990-a525-5b2e044cce4e%22%5D "/Users/daniel/Sites/DevTools/PythonDev/fastapi-htmx-demo/requirements.txt") file should list the necessary dependencies, such as:
```
fastapi
jinja2
uvicorn
```

This project leverages FastAPI for building the web application, Jinja2 for templating, and Uvicorn for serving the application. The structure is simple, with routes defined for getting and adding items, and templates used for rendering HTML responses.
