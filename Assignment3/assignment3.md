![cover](picture/cover.png)

[toc]

### 1. Introduction and overview

#### 1.1 Intention

The intention behind this document is to unveil an intricate blueprint of the Smart Library. The document will encompass the updated employment of use cases, refined architecture tailored to the platform's requirements, and realization of use cases and class design. Furthermore, it will expound upon the distinctive architectural styles and pivotal design choices that have been implemented.

#### 1.2 Advances in System Design

In the preceding assignment, we partitioned the intelligent library system into five subsystems and revealed the deployment of use cases, architecture diagrams, class diagrams, and interaction diagrams of the system.

Building upon our prior endeavor, we have accomplished the tasks of analysis and design, which encompassed the enhancement of the use case model, architectural fine-tuning, design model, as well as the identification of architectural styles and critical design choices. The principal enhancements made to our system are outlined as follows:

- **Use Case Model Enhancement:** We have refined the use case model by integrating supplementary realizations and design mechanisms. This serves to present a more comprehensive depiction of the system's functionality and user interactions.

- **Architectural Fine-Tuning:** We have crafted a platform-specific architecture with an improved overarching structure. This architecture guarantees the system's scalability, modularity, and maintainability.

- **Subsystems and Interfaces:** Each subsystem is equipped with well-defined interfaces that foster seamless communication and collaboration between disparate components.

- **Interface Specification:** We have furnished specifications for the system's interactions with external entities such as the public information website, third-party messaging system, and map services. These specifications ensure the seamless integration and exchange of data between the system and external entities.

- **Use Case Realizations:** We have incorporated five exemplars of use case realizations, thereby exhibiting the system's behavior in diverse scenarios. These realizations integrate design mechanisms and leverage the refined architecture to enhance efficiency and user experience.

- **Detailed Class Design:** We have formulated and documented over 20 comprehensive classes that encapsulate the system's data and behavior. These classes adhere to object-oriented principles and significantly contribute to the overall robustness and extensibility of the system.

In addition to the aforementioned enhancements, we have also conscientiously contemplated various architectural styles and made crucial design choices intending to optimize the system's performance and efficacy. These choices have been thoroughly evaluated and aligned with the project's requirements and constraints.

### 2. Updated use case model



#### 2.4 Updated System: Venue Management System

**Update:** 

Deleted some redundant steps in the basic flow of UC07.

| **USE CASE**          | Enter Open Spaces                                            |
| --------------------- | ------------------------------------------------------------ |
| **ID**                | UC07                                                         |
| **Specification**     | This use case happens when a user wanted to enter the library building in order to borrow and return books, and use the facilities like tables and study rooms. There is no limitation unless the total number of people inside reaches the threshold. |
| **Actors**            | **User**                                                     |
| **Pre-Condition**     | User's account must be valid                                 |
| **Basic Flow**        | 1. User verifies his or her identity at the panel attached to the turnstile.<br/> 1.1 If the user has a library card, he or she could swipe the card.<br/> 1.2 The user could also enter his or her account number on the panel to get verification.  <br/>3. The user is allowed to enter the open space. |
| **Alternative Flows** | a. The user is not able to go through the verification process:<br/> a.1. If the user enters an invalid account number, he or she is allowed to renter the account number.<br/> a.2. If the user’s card can’t be recognized, he or she should turn to a librarian for help.<br/>b. When the total number of people inside the building reaches the threshold, no more user is allowed in. |
| **Post-Condition**    | After successfully entering the open spaces, users could see the books on the bookshelves, use public PCs to log in to the system and borrow books, use the tables and check in to a study room. |

**Update:** 

Specify the actor of this use case.

| **USE CASE**          | Book a Study Room                                            |
| --------------------- | ------------------------------------------------------------ |
| **ID**                | UC08                                                         |
| **Specification**     | In this use case, teachers and students will see information about the study rooms on the system interface. Users could book a study room by choosing a spare room, a time spot to enter the room and the duration. Users could only use the study room after booking one. |
| **Actors**            | **Teacher/Student**                                          |
| **Pre-Condition**     | The user must have a valid account and log in to the system and jump to the booking webpage. |
| **Basic Flow**        | 1. Users click the booking button.<br/>2. Check whether the user is authorized to use a study room(public users are not allowed to use study rooms).<br/>3. Users browse the information of all the available periods of study rooms.<br/>4. Users choose a spare study room.<br/>5. Users choose an available period.<br/>6. Users confirm the booking information.<br/>7. Users get a temporary password to enter the booked study room. |
| **Alternative Flows** | a. There are no vacant rooms: users could not choose rooms and will be directed to leave this page.<br/>b. The room chosen has no vacancy: users could not choose a time(step 5)<br/>c. The user is not authorized to use the study room: The user will be informed when clicking the booking button and could not enter step 3. |
| **Post-Condition**    | Users could check in to the study room at due time.          |

### 3. Architecture Refinement

#### 3.1 Platform-dependent architecture



#### 3.2 Subsystems and interfaces

##### 3.2.1 Account Management System

| ORDER NUM | REST API                                                         | INTERFACE INTRODUCTION                                                 |
| --------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 01        | GET /api/users/?userName=username & userPassword = userpassword/ | This interface is used to login the user account.                      |
| 02        | POST /api/users/                                                 | This interface is used to register user accounts.                      |
| 03        | DELETE /api/users/                                               | This interface is used to delete the user account.                     |
| 04        | PUT /api/users/?userName=username/                               | This interface is used for users to modify account information.        |

##### 3.2.2 Book Management System

| Order num | rest api                                                         | interface introduction                                                 |
| --------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 05        | POST /api/users/suggestions                                      | This interface is used to send suggestions from users to administrator |
| 06        | GET /api/users/suggestions                                       | This interface is used to get suggestions                              |
| 07        | PUT /api/users/knowledgeGraph                                    | This interface is used to update the knowledge graph                   |
| 08        | PUT /api/library/inventory?bookid=id&inventory=number/           | This interface is used to update the inventory of some books           |

##### 3.2.4 Venue Management System

| Order num | rest api                               | interface introduction                                       |
| --------- | -------------------------------------- | ------------------------------------------------------------ |
| xx        | POST /api/venue/id                     | This interface accepts the id of a user, indicating the user has enter the venue, and return whether the operation is successful. |
| xx        | GET /api/venue/authorization/id        | This interface returns one user's authorization of entering a certain venue. |
| xx        | GET /api/venue/studyroom/info          | This interface returns the information like room numbers and timetable of study rooms. |
| xx        | POST /api/venue/studyroom/room_id      | This interface accepts the room number(id of a room) and if the room has vacancy, returns the timetable and the registration table of the room, else returns a denial message. |
| xx        | POST /api/venue/studyroom/time/room_id | This interface accepts a time period and change the room's registration table, and return whether the operation is successful. |
| xx        | POST /api/venue/studyroom/password     | This interface accepts the password of a study room, and return whether the operation is successful. |

##### 3.2.5 Reader Communication System

| Order num | rest api                                                         | interface introduction                                                 |
| --------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------- |
| xx        | GET /api/forum/post                                              | This interface is used to get all the posts in the forum               |
| xx        | POST /api/forum/post                                             | This interface is used to send a new post to the database              |
| xx        | POST /api/forum/post/id/reply                                    | This interface is used to add a new reply under a specific post        |
| xx        | DELETE /api/forum/post/id                                        | This interface is used to delete a specific post                       |
| xx        | DELETE /api/forum/post/id/reply                                  | This interface is used to delete a specific reply to a specific post   |

#### 3.3 Interface specification



#### 3.4 Example of interfaces



### 4. Design model

#### 4.1 Implemented use cases

##### 4.1.1 Users Login

![Login](picture/AccountManagementSystem/Login.png)

All users of the system need to log in when entering the system.

We use Spring MVC in the system to process login requests, and use the REST API to send information commands to the database that stores user account information, and use sa-token for account login authentication.

When the user enters the system, he first enters the account login interface of the system. After the user fills in his user name, password and verification code on this interface, he clicks the "Login" button. Login Interface first judges the correctness of the verification code. If the verification code is wrong, then Directly refuse to log in, login fails and prompts that the verification code is wrong; otherwise, if the verification code is correct, the information will be converted into JSON format and sent to Spring MVC, Spring MVC sends a query request to the database through the REST API. The database queries the tuple that matches the user name and password in the account information table and returns the query result. If it is not found, it means that the login information is incorrect, the login request is rejected, and the login fails. And it prompts that the user name or password is wrong; if it is correct, call StpUtil.login(id) to log in, and then get the login token information from sa-token through StpUtil.getTokenInfo(), send and save the token information to the front end, and the login is successful. This use case ends.

Some of the corresponding classes are represented in the class diagram below:

![AMSClass](picture/AccountManagementSystem/AMSMain.png)

##### 4.1.2 Update Book Inventory

![](/picture/BookManagementSystem/UpdateBookInventory.png)

When the administrator enters the system, he can view the update suggestions submitted by the user, or directly update the book inventory, when updating the inventory, you need to choose one of the three to buy new books, increase, and decrease, after the selection, the front-end interface will package the data into a json file through AJAX and send it to the backend, and then call the relevant interface, access the database and update the information to achieve the request, and finally return the result to the front-end and display.

Some of the corresponding classes are represented in the class diagram below:

![](/picture/BookManagementSystem/ClassDiagram1.png)

##### 4.1.4 Book a Study Room

![VMSRealization](C:\Users\Jack Ding\Desktop\Assignment3save\picture\VenueManagementSystem\BookStudyRoomRealization.png)

Booking a study room is a crucial use case for users who wish to reserve a study room for a specific time period. The process of booking a study room is depicted in sequence diagram above.

Based on our system design, we employ AJAX for seamless data interaction. Additionally, we leverage the Spring MVC framework, as utilized in our previous use case realization, to handle requests and perform validation processes. The approved booking details will be submitted to the database through a REST API.

The user begins by browsing the available study rooms and their corresponding time periods. The system presents the information of all the available time slots for study rooms, allowing the user to view the room availability.

Once the user selects a vacant study room, they proceed to choose an available time slot for booking. This selection is made from the displayed options, indicating the time period during which the user intends to use the room.

Upon making the selection, the user confirms the booking information. This includes the chosen study room, the selected time period, and any other relevant details required for the booking process.

The system validates the user's booking request. Spring MVC is responsible for examining the correctness of the input format, ensuring it meets the required semantic level criteria. The pending validation code is utilized to verify the user's authenticity and deter robot users. Any booking input with an illegal format or an incorrect validation code will be rejected by the system.

After successful validation, the booking details are posted to the content database using the REST API's POST command. The database processes the request and returns the result in JSON format, indicating that the booking has been successfully stored in the database. In the event of an error during the operation, an empty JSON response will be returned and subsequently handled by error processing methods.

Finally, the system refreshes the webpage to display the study room booking with the newly added information. The user can now view their confirmed booking details, including the room number, chosen time period, and any other relevant information.

The corresponding subsystems and interfaces are represented in the class diagram provided below.

![VMSClass](picture/VenueManagementSystem/BookingClass.png)

##### 4.1.5 Create Posts

![CreatePosts](picture/ReaderCommunicationSystem/CreatePosts.png)

The use case "Create Posts" serves the purpose of generating new posts. The process for this use case is illustrated in the sequence diagram above.

We employ AJAX for data interaction in conjunction with the Spring MVC framework, which handles the validation process. Once the content is approved, it is submitted to the database via the REST API.

To initiate the post creation, the user activates the "Create a Post" button, prompting the system to transition to the post-creation page. Subsequently, the user inputs the desired post content along with a captcha for bot verification. Upon clicking the submit button, the relevant data is generated and transmitted to Spring MVC using AJAX techniques.

During the validation process, Spring MVC checks the content's format. Concurrently, we utilize Google reCAPTCHA (<https://mvnrepository.com/artifact/com.github.penggle/kaptcha>) to handle the captcha and prevent automated bot usage. Any content with an invalid format or an incorrect captcha will be rejected.

Upon successful validation, the post content is dispatched to the database interface via a POST command facilitated by the REST API. The interface inserts the data into the database and returns the corresponding result.

Finally, the system refreshes the webpage, displaying the newly created post if the operation was successful, or an error message if it failed.

Some of the corresponding classes are represented in the class diagram below:

![DetailedClassDiagram](picture/ReaderCommunicationSystem/DetailedClassDiagram.png)

#### 4.2 Detailed class design

### 5. Architectural styles and critical design decisions

#### 5.1 Architectural styles

After analyzing the requirements of our intelligent library system, we believe that the system does not have high requirements for maintainability and expandability, because for a given library system, the number of users it can serve and the range of services it can provide are limited and will not continue to grow, and the functionality of the system will not change much, and there is no need to design additional interfaces for subsequent expansion; We focus more on the responsiveness and reliability of the system. From the user's point of view, users always want to keep their waiting time as short as possible, and no one wants the server to be down while they are receiving the service. Since the microservices architecture is more focused on the scalability and maintainability of the system, we chose the client-server architecture, which is more in line with our system requirements, as the main architecture.

`Client-Server Architecture`(CSA) is a common distributed computing architecture for building web applications and systems. In this architecture, the system is divided into two main components: the client and the server.

1. `Client`: The client is the front-end part of the system, usually a software application or user interface that runs on the user's device. The client is responsible for providing an interactive interface to the user, receiving user input and sending it to the server. It is also responsible for processing the data returned by the server and presenting the results to the user; it can be a desktop application, a mobile application, a Web browser, etc.
2. `Server`: The server is the back-end part of the system, responsible for processing requests sent by clients and providing corresponding services. The server usually runs on a dedicated hardware device or cloud server, which can handle requests from multiple clients and execute the corresponding business logic and data processing according to the type of requests, it can be an application server, database server, file server, etc.

The client and server communicate over the network, using standard communication protocols to transfer data. This front- and back-end separated architecture allows the client and server to be developed, deployed and maintained independently, improving the flexibility and scalability of the system. It also enables distributed computing, allowing the load to be distributed to multiple servers, improving system performance and scalability; it also supports cross-platform and cross-device access, enabling users to access and use the system through different devices and platforms.

Also, to make our system development, design, and maintenance easier, we have adopted a layered architecture model to aid in the design.

Our layered architecture diagram is as follows:

![LayerBlock](../Assignment2/picture/ArchitecturalAnalysis/layerBlock.png)

The detailed logic layer is implemented as follows:![SystemLevelDiagram](../Assignment2/picture/ArchitecturalAnalysis/systemLevelDiagram.png)

In this layered architecture, each layer is built on top of its next layer and provides a set of clearly defined interfaces and functions. The Application Layer accepts requests from the Presentation Layer and calls the core methods of the Domain Layer to process various requests, while the Domain Layer has direct access to the bottom Data Access Layer, which effectively protects the data from being exposed to other layers.

#### 5.2 Design pattern

In our various subsystems, we use the following design patterns:

1. `Singleton Pattern`: For all users, the same intelligent library system is shared, so it is necessary to ensure that only one library use case exists. This can be achieved by defining a static variable of type `static` in the class, and when it is time to shut down the system, the instance can be saved by a serialization operation to allow the next time the system is started to work again from where it ended last time.
2. `Factory Pattern`: As it is necessary to use different pictures to fill different labels when displaying the interface, in order to avoid using specific class instantiation operations in the client code, we encapsulate the instantiated picture class as a picture factory, and different picture classes can implement the interface in different ways.
3. `Observer Pattern`: The data in the interface is updated in real time, and also displays different data according to the user's operation. We need to add monitoring (observer) for each component (observed) that may be updated to ensure that the data is true. Each observer only needs to pay attention to its own bound observer and does not need to care about the state changes of other components, which can achieve loose coupling between objects and further enhance the maintainability and flexibility of the system.
4. `MVC pattern`: Its basic idea is to achieve loose coupling and maintainability of the code by separating different aspects of the application. The model is responsible for handling data and business logic, the view is responsible for presenting data, and the controller is responsible for coordinating user input and model operations. It provides a clear code structure, making the code easy to understand and maintain; it achieves modularity and reusability, allowing the model, view and controller to be modified and extended independently; it also supports multiple views for the same model, providing flexible user interface customization capabilities.

#### 5.2 Critical design decisions

In order to ensure a good user experience and high code maintainability, our system adopts the development method of front-end and back-end separation.

In order to ensure security, the system uses an authority authentication framework. Since the system only provides services for students and teachers of one school and some off-campus users, the scope of use is not large, so a simple and lightweight authority authentication framework sa-token was chosen.

### 6. Contributions
