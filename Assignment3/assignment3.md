![](/picture/cover.png)

[toc]

### 1、Introduction and overview

#### 1.1 Intention

The intention behind this document is to unveil an intricate blueprint of the Smart Library. The document will encompass the updated employment of case scenarios, refined architecture tailored to the platform's requirements, and meticulous realization of case scenarios and class design. Furthermore, it will expound upon the distinctive architectural styles and pivotal design choices that have been implemented.

#### 1.2 Advances in System Design

In the preceding assignment, we partitioned the intelligent library system into five subsystems and revealed the deployment of case scenarios, architecture diagrams, class diagrams, and interaction diagrams of the system.

Building upon our prior endeavor, we have accomplished the tasks of analysis and design, which encompassed the meticulous enhancement of the case scenario model, architectural fine-tuning, design blueprint, as well as the identification of architectural styles and critical design choices. The principal enhancements made to our system are outlined as follows:

- **Case Scenario Model Enhancement:** We have meticulously refined the case scenario model by integrating supplementary realizations and design mechanisms. This serves to present a more comprehensive depiction of the system's functionality and user interactions.

- **Architectural Fine-Tuning:** We have crafted a platform-specific architecture with an improved overarching structure. This architecture guarantees the system's scalability, modularity, and maintainability.

- **Subsystems and Interfaces:** We have successfully pinpointed and compiled a list of the subsystems constituting the system. Each subsystem is equipped with well-defined interfaces that foster seamless communication and collaboration between disparate components.

- **Interface Specification:** We have furnished meticulous specifications for the system's interactions with external entities such as the public information website, third-party messaging system, and map services. These specifications ensure the seamless integration and exchange of data between the system and external entities.

- **Elaborate Case Scenario Realizations:** We have meticulously incorporated five exemplars of elaborate case scenario realizations, thereby exhibiting the system's behavior in diverse scenarios. These realizations integrate design mechanisms and leverage the refined architecture to enhance efficiency and user experience.

- **Detailed Class Design:** We have meticulously formulated and documented over 20 comprehensive classes that encapsulate the system's data and behavior. These classes adhere to object-oriented principles and significantly contribute to the overall robustness and extensibility of the system.

In addition to the aforementioned enhancements, we have also conscientiously contemplated various architectural styles and made crucial design choices intending to optimize the system's performance and efficacy. These choices have been thoroughly evaluated and aligned with the project's requirements and constraints.

### 2、Updated use case model



### 3、 Architecture Refinement

#### 3.1 Platform-dependent architecture



#### 3.2 Subsystems and interfaces

##### 1、Account Management System

| ORDER NUM | REST API                                                     | INTERFACE INTRODUCTION                                       |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 01        | GET /api/users/?userName=username & userPassword = userpassword/ | This interface is used to login the user account.            |
| 02        | POST /api/users/                                             | This interface is used to register user accounts.            |
| 03        | DELETE /api/users/                                           | This interface is used to delete the user account.           |
| 04        | PUT /api/users/?userName=username/                           | This interface is used for users to modify account information. |

##### 2、Book Management System

| Order num | rest api                                               | interface introduction                                       |
| --------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| 05        | POST /api/users/suggestions                            | This interface is used to send suggestions from users to administrator |
| 06        | GET /api/users/suggestions                             | This interface is used to get suggestions                    |
| 07        | PUT /api/users/knowledgeGraph                          | This interface is used to update the knowledge graph         |
| 08        | PUT /api/library/inventory?bookid=id&inventory=number/ | This interface is used to update the inventory of some books |



#### 3.3 Interface specification



#### 3.4 Example of interfaces



### 4、Design model

#### 4.1 Implemented use cases

##### 1、Users Login

![Login](/picture/AccountManagementSystem/Login.png)

All users of the system need to log in when entering the system.
We use Spring MVC in the system to process login requests, and use the REST API to send information commands to the database that stores user account information, and use sa-token for account login authentication.
When the user enters the system, he first enters the account login interface of the system. After the user fills in his user name, password and verification code on this interface, he clicks the "Login" button. LoginInterface first judges the correctness of the verification code. If the verification code is wrong, then Directly refuse to log in, login fails and prompts that the verification code is wrong; otherwise, if the verification code is correct, the information will be converted into JSON format and sent to Spring
MVC, Spring MVC sends a query request to the database through the REST API. The database queries the tuple that matches the user name and password in the account information table and returns the query result. If it is not found, it means that the login information is incorrect, the login request is rejected, and the login fails. And it prompts that the user name or password is wrong; if it is correct, call StpUtil.login(id) to log in, and then get the login token information from sa-token through StpUtil.getTokenInfo(), send and save the token information to the front end, and the login is successful. This use case ends.

![](/picture/AccountManagementSystem/AMSMain.png)

#### 4.2 Detailed class design

### 5、Architectural styles and critical design decisions

#### 5.1 Architectural styles 

After analyzing the requirements of our intelligent library system, we believe that the system does not have high requirements for maintainability and expandability, because for a given library system, the number of users it can serve and the range of services it can provide are limited and will not continue to grow, and the functionality of the system will not change much, and there is no need to design additional interfaces for subsequent expansion; We focus more on the responsiveness and reliability of the system. From the user's point of view, users always want to keep their waiting time as short as possible, and no one wants the server to be down while they are receiving the service. Since the microservices architecture is more focused on the scalability and maintainability of the system, we chose the client-server architecture, which is more in line with our system requirements, as the main architecture.

`Client-Server Architecture `(CSA) is a common distributed computing architecture for building web applications and systems. In this architecture, the system is divided into two main components: the client and the server.

1. `Client`: The client is the front-end part of the system, usually a software application or user interface that runs on the user's device. The client is responsible for providing an interactive interface to the user, receiving user input and sending it to the server. It is also responsible for processing the data returned by the server and presenting the results to the user; it can be a desktop application, a mobile application, a Web browser, etc.
2. `Server`: The server is the back-end part of the system, responsible for processing requests sent by clients and providing corresponding services. The server usually runs on a dedicated hardware device or cloud server, which can handle requests from multiple clients and execute the corresponding business logic and data processing according to the type of requests, it can be an application server, database server, file server, etc.

The client and server communicate over the network, using standard communication protocols to transfer data. This front- and back-end separated architecture allows the client and server to be developed, deployed and maintained independently, improving the flexibility and scalability of the system. It also enables distributed computing, allowing the load to be distributed to multiple servers, improving system performance and scalability; it also supports cross-platform and cross-device access, enabling users to access and use the system through different devices and platforms.

Also, to make our system development, design, and maintenance easier, we have adopted a layered architecture model to aid in the design.

Our layered architecture diagram is as follows:

![](../Assignment2/picture/ArchitecturalAnalysis/layerBlock.png)

The detailed logic layer is implemented as follows:![](../Assignment2/picture/ArchitecturalAnalysis/systemLevelDiagram.png)

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

### 6、Contributions