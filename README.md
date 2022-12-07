# Take Home Test: Wallet

## Directions

1. Build a small React application. This is your chance to show us the kind of code you'd write on
the job. Please balance execution speed and code quality. 
1. We will evaluate your submission based on correctness, completeness, readability, and performance.
1. Fork this repository into a private repository. We do not want your answers to be publicly available.
1. When you are complete, notify your point of contact at Forage. The point of contact will share with you the interviewer's github handle. Please share access to your private repo.
1. We will immediately schedule a live code review.

## The Challenge

### Iteration 0

Build a wallet and allow a user to add their cards to that wallet. The wire frames below explain the flow and components we'd like to see in your application. Feel free to get creative and modify the interactions. Also, feel free to implement whatever styling you like.

![mockup](https://user-images.githubusercontent.com/10040882/206077291-eb0628c7-0ae2-4cb5-b2c9-a941280a4bd2.png)



*Extra credit: add your component library to a locally run [Storybook](https://storybook.js.org/).*

### Iteration 1

Hook up your "add a card" component to the server contained in this repository. (See instructions in a section below on how to run the server on your local machine). Save the card(s) to local state. Do not assume the server will store the cards the user adds to their wallet. Moreover, ensure your application can handle errors returned by the server. Invalid parameters in the HTTP request will yield an error response. For example, a card number that is less than 16 characters will produce an error. Make sure to display errors to the user.

**Method:** POST
<br/>
**Endpoint:** /api/payment_methods
<br/>
**URL:** http://localhost:8080
<br/>
**Request body** (content/json): { "type": enum[ "ebt", "credit", "debit"], "number": string }. Example: { "type": "ebt", "number": "1234567890123456" }

### Testing

Tests are required for this coding challenge.

## The Server

We have included a server in the folder `/server`. It contains only one endpoint: to save a payment method (card). We have included this reference video where Victor runs through the setup commands below. [Video: how to run the server & access API documentation](https://share.cleanshot.com/XdnjdM)

### How to run the server

1. Download [docker](https://www.docker.com/products/docker-desktop/). Move onto the next step after docker is available to your command line.
1. Open up your terminal.
1. Change your current directory to `/server`: `cd <path to>/server`
1. Run the command: `docker pull stoplight/prism` to download the application Prism. It will run the mock server on your local computer.
1. Run the command: `docker run -v $PWD/oas.yml:/app/oas.yml -p 8080:8080 stoplight/prism mock -h 0.0.0.0 -p 8080 -d /app/oas.yml ` to run the server. The server is available to your react app at `http://localhost:8080/`.


### Access API documentation

1. Move onto the next step after docker is available to your command line.
1. Open up your terminal.
1. Change your current directory to `/server`: `cd <path to>/server`
1. Run the command: `docker pull swaggerapi/swagger-editor` to download the application Swagger-Editor. It will run the API documentation.
1. Run the command: `docker run -p 8000:8080 -v $(pwd):/tmp -e SWAGGER_FILE=/tmp/oas.yml swaggerapi/swagger-editor` to run the API documentation server. You can access the documentation at `http://localhost:8000/`

