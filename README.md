# Authentication with Microservice model in NodeJS 
Authentication by Microservice model in Nodejs (Typescript)

** Project: Auth and User.
- Auth: Using as a switch for microservice.  Sử dụng để phân nhánh các microservice. Typical here, the main function is create and authorized with a token. 
- User: Find and compare account. In addition, It supply some API test which has authorized token. 
``
    Auth
  /      \
User      Another
``
# Installing:
* Run Auth project:
``sh
$ cd /auth
$ npm i
$ npm run start:dev
``
* Run User project:
``sh
$ cd /user
$ npm i
$ npm run start:dev
``
-------------
# Manual

### Sign in:
- Step 1: Call api: 
*Input:
``
{
URL  :  http:localhost:3000/auth/
Type :  Post
Body: {
      "username": "AAA 1",
      "password": "BBB 1"
      }
}
``
- Step 2: Auth -> User to find a user. Respoinse to Auth
- Step 3: Compare password
- Step 4: Create token for webclient.
*Output:
``
{
   "userId": 1,
   "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImlkIjoxLCJ1c2VybmFtZSI6IkFBQSAxIiwicGFzc3dvcmQiOiJCQkIgMSIsIm5hbWUiOiJOTk4gMSIsImVtYWlsIjoiQUFBQSAxIiwiY3JlYXRlZEF0IjoiMjAyMC0wNy0xNlQwNDoxMzozMi45MTVaIn0sInN1YiI6MSwiaWF0IjoxNTk0ODczMTQwLCJleHAiOjE1OTQ4NzMyMDB9.pqyvzSOEPrs7pWHhNB9sPTHj4sYKRy4-IH_8yIEx0QA"
}
``
### Xác thực token:
- Step1: call API in User project:
Input:
``
{
URL  :  http:localhost:3010/greet/
Type :  Get
Authentication: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImlkIjoxLCJ1c2VybmFtZSI6IkFBQSAxIiwicGFzc3dvcmQiOiJCQkIgMSIsIm5hbWUiOiJOTk4gMSIsImVtYWlsIjoiQUFBQSAxIiwiY3JlYXRlZEF0IjoiMjAyMC0wNy0xNlQwNDoxMzozMi45MTVaIn0sInN1YiI6MSwiaWF0IjoxNTk0ODczMTQwLCJleHAiOjE1OTQ4NzMyMDB9.pqyvzSOEPrs7pWHhNB9sPTHj4sYKRy4-IH_8yIEx0QA"
}
``
- Step 2: User send token to Auth.
- Step 3: Accept authorized token in Auth.
- Step 4: True, Run action of this controller:
Output:
``
"Greetings authenticated user"
``
-------------------------------------------------------------------
## Author
Shandy Nguyen - Master computer Science
