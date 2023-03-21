# Flask Task Manager App
This is a Flask-based task manager app that allows users to create, read, update, and delete tasks and categories. The app also allows users to view tasks by category.

  Link Link: https://kc-task-manager.herokuapp.com/add_task


## Technology Stack
This app is built using the following technologies:

- Flask: Python-based web framework
- SQLAlchemy: SQL toolkit and ORM for Python
- JavaScript (JS): programming language that allows for dynamic updates to webpages
- CSS: styling language for HTML webpages
- HTML: markup language for creating webpages
- GitHub: web-based version control system for software development
- ElephantSQL: cloud-based PostgreSQL database hosting service
- Heroku: cloud platform that allows for deployment of web applications


## Features
The Flask Task Manager App has the following features:

- User authentication and authorization
- CRUD operations for tasks and categories
- Task filtering by category
- Materialize CSS for a clean, responsive UI
- Font Awesome icons for additional visual appeal


## Project Structure
The app is structured as follows:

- `run.py`: the main Python file that initializes the Flask app and runs it
- `taskmanager` folder:
  - `__init__.py`: initializes the Flask Blueprint and the SQLAlchemy database
  - `models.py`: defines the Task and Category SQLAlchemy models
  - `routes.py`: contains the app's URL routes and their corresponding view functions
  - `static folder`: contains the JS and CSS files used for styling and interactivity
  - `templates folder`: contains the Jinja2 HTML templates that generate the app's webpages


## `routes.py`

 The Flask application has a home route (`@app.route("/")`) that retrieves all the tasks in the database and renders them in the `tasks.html` template using `render_template`. The `categories` route (`@app.route("/categories")`) retrieves all the categories in the database and renders them in the `categories.html` template using `render_template`.

The `add_category` route (`@app.route("/add_category", methods=["GET", "POST"])`) allows the user to add a new category by rendering the `add_category.html` template. If the request method is "POST", the function retrieves the category name from the submitted form, creates a new `Category` object with the retrieved name, adds the category to the database session, and commits the changes to the database. The function then redirects the user to the `categories` route.

The `edit_category` route (`@app.route("/edit_category/<int:category_id>", methods=["GET", "POST"])`) allows the user to edit an existing category by rendering the `edit_category.html` template. If the request method is "POST", the function retrieves the new category name from the submitted form, updates the `Category` object with the retrieved name, and commits the changes to the database. The function then redirects the user to the `categories` route.

The `delete_category` route (`@app.route("/delete_category/<int:category_id>")`) allows the user to delete an existing category. The function retrieves the category to be deleted from the database session, deletes the category, and commits the changes to the database. The function then redirects the user to the `categories` route.

The `add_task` route (`@app.route("/add_task", methods=["GET", "POST"])`) allows the user to add a new task by rendering the `add_task.html` template. If the request method is "POST", the function retrieves the task name, task description, is_urgent status, due date, and category id from the submitted form, creates a new `Task` object with the retrieved data, adds the task to the database session, and commits the changes to the database. The function then redirects the user to the `home` route.

The `edit_task` route (`@app.route("/edit_task/<int:task_id>", methods=["GET", "POST"])`) allows the user to edit an existing task by rendering the `edit_task.html` template. If the request method is "POST", the function retrieves the new task name, task description, is_urgent status, due date, and category id from the submitted form, updates the `Task` object with the retrieved data, and commits the changes to the database. The function then renders the `edit_task.html` template with the updated task data and categories.

The `delete_task` route (`@app.route("/delete_task/<int:task_id>")`) allows the user to delete an existing task. The function retrieves the task to be deleted from the database session, deletes the task, and commits the changes to the database. The function then redirects the user to the `home` route.


## `models.py`

 The `models.py` file defines the database schema for the `Category` and `Task` models. The `Category` model includes an `id` field, a `category_name` field that is unique and cannot be null, and a `tasks` field that represents a one-to-many relationship with the `Task` model. The `Task` model includes an `id` field, a `task_name` field that is unique and cannot be null, a `task_description` field that cannot be null, an `is_urgent` field, which is a Boolean value indicating whether the task is urgent or not, a `due_date` field representing the due date of the task, and a `category_id` field that represents a many-to-one relationship with the `Category` model.

In addition to defining the fields for each model, the `models.py` file also includes the `repr` method for each model, which returns a string representation of the model object. This is useful for debugging and logging purposes, as well as for displaying model objects in templates.

Overall, the `models.py` file is essential for defining the structure of the database and the relationships between the `Category` and `Task` models. The file also provides a way to interact with the database through the Flask-SQLAlchemy ORM (Object-Relational Mapping), which allows for easy manipulation of database records using Python objects.


## Usage
To use this app, follow these steps:

1. Clone the repository from GitHub to your local machine.
2. Create a virtual environment and activate it.
3. Install the dependencies from the `requirements.txt` file using pip.
4. Create a PostgreSQL database on ElephantSQL.
5. Create a file named `.env` in the root directory of the project and add the following environment variables:
  - `DATABASE_URL`: the URL to connect to the ElephantSQL database
  - `SECRET_KEY`: a secret key used by Flask for security
6. Run the app using the command python run.py in the terminal.


## Deployment
This app can be deployed to Heroku by following these steps:

1. Create a Heroku account and install the Heroku CLI.
2. Create a new app on Heroku.
3. Connect the app to the GitHub repository.
4. Set the environment variables `DATABASE_URL` and `SECRET_KEY` using the Heroku CLI.
5. Deploy the app from the GitHub repository using the Heroku CLI.


## Contributing
Contributions to this app are welcome. To contribute, follow these steps:

1. Fork the repository.
2. Create a new branch with your changes.
3. Test your changes locally.
4. Push your changes to your fork.
5. Create a pull request with a description of your changes.


## License
This app is licensed under the MIT License.

## Credits
- The app was created by following a Code Institute Walk Through Module as part of their Full Stack Developer Dimploma Course. 

- Please note that the README file was generated using an AI language model, ChatGPT(3.5), which has certain limitations and may contain inaccuracies. This tool was used to document the project for future reference. 
