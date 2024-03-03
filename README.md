# Note Taker

#### Video Demo: [My Video](https://youtu.be/wfehwoKMKII)

#### Description

**Note Taker** is a web application that allows users to create an account using their email, sign into that account, create notes that are saved to a database, and sign out.

#### Tech Stack

**Note Taker** was made using the following technologies:

- Flask
- Jinja
- Javascript
- Bootstrap
- SQL Alchemy

#### Application Breakdown

**base.html** serves as the main template from which most of the other pages derive. It's a basic layout detailing the design of the navbar. It also contains the logic responsible for rendering the correct links in the navbar depenging on which page the user is as well as what messages to flash on screen in accordance with user actions. This page includes a dynamically changing title tag and a script tag responsible for handling the deletion of notes.

**home.html** This HTML document serves as a landing page for the "Note Taker" web application. Utilizing Bootstrap for styling, the page features a centered layout with a primary blue background. The main content includes a large, bold title ("Note Taker") and links for "Login" and "Sign Up." The design focuses on simplicity and ease of navigation, presenting users with quick access to login or sign-up functionality.

**notes.html** The content section includes a centered heading "Notes" and a list of user-specific notes displayed within a Bootstrap list group. Each note is presented as a list item, showing the note's data with a corresponding close button for deletion. Additionally, the template provides a form allowing users to add new notes, featuring a textarea for input and a submit button labeled "Add Note." The use of Bootstrap classes ensures a visually appealing and responsive layout, contributing to an intuitive user experience in managing and interacting with notes.

**login.html** A page that includes a bordered and rounded form, featuring an aligned heading "Login." The form has two input fields for the user's email address and password, each styled with Bootstrap form-control class for a consistent appearance. A submit button labeled "Login" is provided to initiate the login process. The use of Bootstrap classes ensures a clean and user-friendly layout, aligning with the overall design of the application. Upon submission, this form is expected to trigger a POST request to handle the login functionality on the server side.

**sign-up.html** is a form (same layout as login.html) that allows the user to create an account by filling out a form containing input fields for email, first name, password, and password confirmation. The logic for password verification is handled seperately.

**main.py** Responsible for creating and running the web app.

**\_\_init\_\_.py** This script configures a Flask web application, integrating SQLAlchemy for database operations and Flask-Login for user authentication. It initializes the application with a secret key and SQLite database URI, registers blueprints for modular organization (views and auth), and associates them with respective URL prefixes. The script initializes the database and user loader function, ensuring the creation of the SQLite database if it doesn't exist. Finally, it returns the configured Flask app instance, ready for further development and deployment.

**views.py** This Flask script defines a Blueprint named 'views' with three routes. The '/notes' route requires user authentication and handles both GET and POST requests, allowing users to add notes associated with their account. The '/' route checks if the user is authenticated; if yes, it redirects them to the '/notes' route; otherwise, it renders the 'home.html' template. The '/delete-note' route handles POST requests, deleting a note based on the provided JSON data if it belongs to the authenticated user. Overall, the script manages user authentication, note creation, and deletion while ensuring proper user verification.

**auth.py** This script defines an 'auth' Blueprint handling user authentication. The '/login' route manages user login, validating credentials and redirecting to the 'notes' page upon success. The '/logout' route logs out authenticated users and redirects to the home page. The '/sign-up' route facilitates user registration, performs input validation, creates a new user, logs them in, and redirects to 'notes' upon success. The script utilizes Flask-Login for session management, SQLAlchemy for database operations, and incorporates Werkzeug for secure password hashing. Flash messages provide user feedback for various actions.

**models.py** is responsible for defining the schema of the user and their notes. The 'Note' model represents notes with attributes such as 'id', 'data', 'date', and 'user_id', establishing a relationship with the 'User' model. The 'User' model, inheriting from both 'db.Model' and 'UserMixin' for Flask-Login integration, represents users with attributes including 'id', 'email', 'password', 'first_name', and a relationship with user notes.

**index.js** performs an asynchronous HTTP POST request to the "/delete-note" endpoint on the server. It sends a JSON payload containing the noteId parameter to identify the note to be deleted. After the server processes the request and deletes the corresponding note, the function redirects the user to the root ("/") location by setting window.location.href to "/" after the request is complete. In summary, this function is likely used in a web application to delete a note by making a server request and updating the page accordingly.
