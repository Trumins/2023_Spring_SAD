### 2.a 

#### Account Management System

| ORDER NUM | REST API                                                     | INTERFACE INTRODUCTION                                       |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 01        | GET /api/users/?userName=username & userPassword = userpassword/ | This interface is used to login the user account.            |
| 02        | POST /api/users/                                             | This interface is used to register user accounts.            |
| 03        | DELETE /api/users/                                           | This interface is used to delete the user account.           |
| 04        | PUT /api/users/?userName=username/                           | This interface is used for users to modify account information. |

### 3.a 

#### Users Login

![Login](.\picture\Login.png)

All users of the system need to log in when entering the system.
We use Spring MVC in the system to process login requests, and use the REST API to send information commands to the database that stores user account information, and use sa-token for account login authentication.
When the user enters the system, he first enters the account login interface of the system. After the user fills in his user name, password and verification code on this interface, he clicks the "Login" button. LoginInterface first judges the correctness of the verification code. If the verification code is wrong, then Directly refuse to log in, login fails and prompts that the verification code is wrong; otherwise, if the verification code is correct, the information will be converted into JSON format and sent to Spring
MVC, Spring MVC sends a query request to the database through the REST API. The database queries the tuple that matches the user name and password in the account information table and returns the query result. If it is not found, it means that the login information is incorrect, the login request is rejected, and the login fails. And it prompts that the user name or password is wrong; if it is correct, call StpUtil.login(id) to log in, and then get the login token information from sa-token through StpUtil.getTokenInfo(), send and save the token information to the front end, and the login is successful. This use case ends.

### 3.b 

#### Account Management System

![](.\picture\AMSMain.png)

### 4

In order to ensure a good user experience and high code maintainability, our system adopts the development method of front-end and back-end separation.

In order to ensure security, the system uses an authority authentication framework. Since the system only provides services for students and teachers of one school and some off-campus users, the scope of use is not large, so a simple and lightweight authority authentication framework sa-token was chosen.