# Authentication with Microservice model in NodeJS 
Authentication by Microservice model in Nodejs (Typescript)

Tạo 2 project với chức năng login và sử dụng token:
+ Auth: Hay còn gọi là main router. Sử dụng để phân nhánh các microservice. Điển hình ở đây, Auth có chức năng là xác thực token. 
+ User: xác thực tài khoảng và mật khẩu. Cung cấp thêm 1 số API demo vần các thực token. 
 ----------------------------------------------------
                           Auth
                       /             \
                   User      Another

** Sign in:
- Step 1: Call api: 
Input:
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
- Step 2: Auth sẽ gọi qua project User để tìm user trả kết quả tìm kiếm về cho Auth
- Step 3: Compare password
- Step 4: Tạo token và trả về webclient.
Output:
``
{
    "userId": 1,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImlkIjoxLCJ1c2VybmFtZSI6IkFBQSAxIiwicGFzc3dvcmQiOiJCQkIgMSIsIm5hbWUiOiJOTk4gMSIsImVtYWlsIjoiQUFBQSAxIiwiY3JlYXRlZEF0IjoiMjAyMC0wNy0xNlQwNDoxMzozMi45MTVaIn0sInN1YiI6MSwiaWF0IjoxNTk0ODczMTQwLCJleHAiOjE1OTQ4NzMyMDB9.pqyvzSOEPrs7pWHhNB9sPTHj4sYKRy4-IH_8yIEx0QA"
}
``
** Xác thực token:
- Step1: Gọi API của User để test token:
Input:
``
{
URL  :  http:localhost:3010/greet/
Type :  Get
Authentication: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImlkIjoxLCJ1c2VybmFtZSI6IkFBQSAxIiwicGFzc3dvcmQiOiJCQkIgMSIsIm5hbWUiOiJOTk4gMSIsImVtYWlsIjoiQUFBQSAxIiwiY3JlYXRlZEF0IjoiMjAyMC0wNy0xNlQwNDoxMzozMi45MTVaIn0sInN1YiI6MSwiaWF0IjoxNTk0ODczMTQwLCJleHAiOjE1OTQ4NzMyMDB9.pqyvzSOEPrs7pWHhNB9sPTHj4sYKRy4-IH_8yIEx0QA"
}
``
- Step 2: Từ User gọi về Auth bằng token
- Step 3: Xác thực token ở Auth và trả về kết quả xác thực cho User
- Step 4: Khi xác thực thành công. Thực hiện action của controller:
Output:
``
"Greetings authenticated user"
``
-------------------------------------------------------------------
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
