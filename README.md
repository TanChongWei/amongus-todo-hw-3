# PowerX Fundamentals in Developer Tools - Homework 3

This project involves setting up a CI/CD pipeline for an already existing application. The following steps are involved:
- Creation of a Dockerfile for the code base
- Running of tests to ensure that the application is working properly
- Running a Docker build using a docker build action
- Running a security check using snyk against the docker image to check for vulnerabilities
- Pushing the image onto Docker hub using a docker login action and a docker push action
- Deploying the application to Heroku using a Heroku Github action

![image](https://user-images.githubusercontent.com/72724926/141983293-0a79b65a-5d4c-4067-bf73-ad4a2392c7de.png)

Heroku application link:
https://cw-amongus-todo.herokuapp.com/

# Among Us TODOs API

![Among Us banner](docs/img/banner.jpg)

Fake REST API server of tasks from Among Us

## Getting Started

This application is backed by the default data from a json file (default to be `db.json`, however it can be specified through an environment variable).
The underlying server that power the application is [json-server](https://github.com/typicode/json-server)

### Starting the application

Simply `npm start` and the server will be started with the default configurations on port 3000 and db file to be `db.json`

### App-level configurations

- `DB`: path to the json file that will be used as the database
- `PORT`: port that the app will start on

### Testing

- Code linting: `npm run lint`
- Full test suite: `npm test`

## API Reference

Data from the json database file will be loaded every time the app starts and db writes will be made to the same file as well. Hence, a note on if the data is not commited into source, we might see differences between environments.

Listed below are basic usages of the API, more advanced usages can be found [here](https://github.com/typicode/json-server#routes).

### POST /todos

Create a new tasks

```
POST /todos

{
    text: string,
    type: "short" | "long" | "common"
}
```

### GET /todos/:id

Get task by ID

```
GET /todos/:id
```

### GET /todos

Get tasks

```
GET /todos
```

Possible query parameters:

- `q`: full text search
- `_page` and `_limit`: paginate
- any fields from the TODO object: filter using specific fields
- `_start` and `_end`: slice based on TODO ID

### PUT /todos/:id

Replace whole TODO item content

```
PUT /todos/:id

{
    text: string,
    type: "common" | "long" | "short"
}
```

### PATCH /todos/:id

Partial update TODO item

```
PATCH /todos/:id

{
    text?: string,
    type?: "common" | "long" | "short"
}
```

### DELETE /todos/:id

Delete a TODO item

```
DELETE /todos/:id
```

## Contributing

For any requests, bug or comments, please [open an issue](https://github.com/stanleynguyen/amongus-todo/issues) or [submit a pull request](https://github.com/stanleynguyen/amongus-todo/pulls).
