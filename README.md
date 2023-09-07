# Django REST Framework User Authentication and Testing API with MongoDB
<img width="948" alt="userauth" src="https://github.com/Hk669/Django-Userauth/assets/96101829/32457fe6-eb92-46f5-ad0f-3c21657bc8a0">


### This Django REST Framework (DRF) project provides user authentication endpoints for login and signup, along with an example protected endpoint for testing authentication. This README will guide you through the project structure, installation, API usage, and testing.

## Table of Contents

1. [Installation and Setup](#installation-and-setup)
2. [API Endpoints](#api-endpoints)
    - [User Login](#1-user-login)
    - [User Signup](#2-user-signup)
    - [Test Authentication](#3-test-authentication)
3. [Usage](#usage)
    - [User Login](#user-login)
    - [User Signup](#user-signup)
    - [Test Authentication](#test-authentication)
4. [Project Structure](#project-structure)
5. [Database](#database)
5. [Additional Notes](#additional-notes)

## Installation and Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/Hk669/django-userauth.git
   ```

2. Navigate to the project directory:

   ```bash
   cd userauth
   ```

3. Create a virtual environment and activate it:

   ```bash
   conda create --name myenv
   conda activate myenv
   ```

4. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

5. Apply database migrations:

   ```bash
   python manage.py migrate
   ```

6. Create a superuser account (admin) to manage the Django admin panel:

   ```bash
   python manage.py createsuperuser
   ```

7. Start the development server:

   ```bash
   python manage.py runserver
   ```

## API Endpoints

### 1. User Login

- **Endpoint:** `/login/`
- **HTTP Method:** POST
- **Description:** Allows users to log in by providing their username and password. Upon successful login, a token is generated and returned along with user information.

### 2. User Signup

- **Endpoint:** `/signup/`
- **HTTP Method:** POST
- **Description:** Allows users to sign up by providing their user details, including username, password, and email. After successful registration, a token is generated, and user information is returned.

### 3. Test Authentication

- **Endpoint:** `/test_token/`
- **HTTP Method:** GET
- **Description:** An example protected endpoint that requires authentication. Users must include their token in the request headers to access this endpoint.

## Usage

### User Login

To log in, make a POST request to `/login/` with the following JSON payload:

```json
{
  "username": "your_username",
  "password": "your_password"
}
```

Upon successful login, you will receive a response with a token and user information.

### User Signup

To sign up, make a POST request to `/signup/` with the following JSON payload:

```json
{
  "username": "new_username",
  "password": "new_password",
  "email": "new_email@example.com"
}
```

After successful registration, you will receive a response with a token and user information.

### Test Authentication

To access the protected `/test_token/` endpoint, you need to include an `Authorization` header with the token obtained during login or signup. Make a GET request to `/test_token/` with the `Authorization` header as follows:

```
Authorization: Token YOUR_TOKEN_HERE
```

If the token is valid, you will receive a response indicating that the authentication test passed.

## Project Structure

- `userauth/`: The project's main directory containing the authentication-related code.
  - `views.py`: Contains the API views for login, signup, and the protected test endpoint.
  - `serializers.py`: Defines serializers for user data.
  - `settings.py`: Django project settings, including configuration for authentication and DRF.
  - `urls.py` : Maps to the fuction for user activities 
- `.env`: Store credentials
- `test.rest` : To make the API requests from IDE
- `manage.py`: Django management script.

## Database

- MongoDB is used as the database for this project. Ensure it is installed and running locally. Configure your database connection settings in the project's settings.

```
DATABASES = {
    'default' : {
        'ENGINE' : 'djongo',
        'NAME' : os.environ.get('MONGODB_NAME'),
        "CLIENT" : {
            'host' : os.environ.get('MONGODB_HOST'),
            'username' : os.environ.get('MONGODB_USER'),
            'password' : os.environ.get('MONGODB_PASSWORD'),
        }
    }
}

```

## Additional Notes

- This project uses token-based authentication provided by the Django REST Framework.
- Passwords are securely hashed using Django's built-in password hashing mechanism.
- Protect your authentication tokens as they grant access to protected resources.
- Customize this project according to your specific requirements and security considerations.

Feel free to explore and enhance this authentication API for your Django-based projects.
