# GDSC.LINK Backend Service

This project build using Spring Boot

## Requirement
To run the application, you need to install this application :
- Intellij IDEA (latest version)
- Redis (7.2.3 or above)
- Docker Desktop (4.26.0 or above)

## Installation
- Clone the git project on your local:
  ```bash
    git clone https://github.com/DeveloperDel/gdsc-link-be.git
  ```
  
- Go to the project directory directly:
  ```bash
    cd gdsc-link-be
  ```
  Note: Also, you need to make sure you're already open the docker desktop
  
- Run this script to create the container in the docker:
  ```bash
    docker-compose -d up
  ```

- Run the container:
  ```bash
    docker container start redis link-shortener-api
  ```
  Note: To check if your container already started, you can check it in the docker desktop or just run this script in your prompt:
  ```bash
    docker container ls
  ```
- Finish, you can test the API in the postman to make sure it works properly. 

## API List
This section outline all the API endpoint in this backend service:
### Base URL
For the base url, it depends on your localhost, usually in http://localhost:8080

### GET /links
Retrieve all the links from database
- **Endpoint:** `/links`
- **Method:** GET
- **Example OK Response:**
```json

{
    "data": [
        "Cloud",
        "CloudVerse"
    ],
    "error": false,
    "message": "Links fetch successfully!",
    "status": "OK"
}
```

### GET `/{id}`
Redirect into the original url
- **Endpoint:** `/{id}`
- **Method:** GET
- **Response:**
The response is in the form of HTML/document


### GET `/link/{id}`
Retrieve spesific link from database.
<br>
Note: `{id}` is the short key after get shortened.
- **Endpoint:** `/link/{id}`
- **Method:** GET
- **Example OK Response:**
```json
{
    "data": "https://example.com/your-long-url-that-you-test",
    "error": false,
    "message": "Long url fetch successfully!",
    "status": "OK"
}
```

### GET `/qr-code/{id}`
Retrieve QR Code from the spesific link.
<br>
Note: `{id}` is the short key after get shortened.
- **Endpoint:** `/qr-code/{id}`
- **Method:** GET
- **Response:**
The response is in the form of media type (png).

### GET `/qr-code/download/{id}`
Download QR Code of a spesific link.
<br>
Note: `{id}` is the short key after get shortened.
- **Endpoint:** `/qr-code/{id}`
- **Method:** GET
- **Response:**
The response is in the form of media type (png).

### POST `/shorten`
Short your long url
- **Endpoint:** `/shorten`
- **Method:** POST
- **Example OK Response:**
```json
{
    "data": {
        "url": "<base-url>/<shortened-key>"
    },
    "error": false,
    "message": "URL has been shortened successfully!",
    "status": "CREATED"
}
```

### PUT `/edit/{url}`
Edit your short url key.
<br>
Note: `{url}` is your old key url that will got edited.
- **Endpoint:** `/edit/{url}`
- **Method:** PUT
- **Example OK Response:**
```json
{
    "data": {
        "url": "<base-url>/<shortened-key>"
    },
    "error": false,
    "message": "Url changed successfully!",
    "status": "CREATED"
}
```

## Contribution
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
<br>
Please make sure to update tests as appropriate.

## License
[Apache License v.2.0](https://www.apache.org/licenses/LICENSE-2.0)
