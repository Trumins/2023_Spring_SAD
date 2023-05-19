# heading

## 1. Project Goals

## 2. Architechure Analysis

架构分析：以高级架构、子系统的形式介绍项目，并详细说明在当前阶段之前所做的体系结构决策。您应该至少包括一个系统级图表，例如，系统的分层体系结构。您还应该为系统级关系图提供文本描述。

## 3. Process and Current Status

In the previous assignment, we divided the smart library system into 5 subsystems and gave their use case models and use case analysis in detail. In this assignment, we first give the architecture diagram of the whole system and the specific analysis of the architecture, and then design the components at each level based on this architecture. In this process, we also designed the class and sequence diagrams for each subsystem and explained them all. During the analysis, we also found the poorly designed elements in the use case module of the previous assignment and made improvements. Currently, we have completed the architectural analysis of the whole system and the class and sequence analysis of each subsystem.

## 4. Changes in Use Case Models

### 4.1 Book Management System

In the last assignment, in terms of the knowledge graph, I only considered the librarian's modifications to it. For this assignment , I found that users also have the need to use the knowledge graph, so I added the function to use the knowledge graph to the use case model.

The updated use case diagram is as follows.

![](../Assignment2/picture/BookManagementSystem/newBookManagementSystemModel.png)

### 4.5 Reader Communication System

In the last assignment, I grouped the use cases “Reply to Posts” and “Create Posts” under the general term “Share Thoughts”. However, I realized that this was not appropriate because these two use cases are quite different from each other. Moreover, this would also increase the complexity. Therefore, I removed the use case “Share Thoughts”.

The updated use case diagram is as follows.

![RCS_newUCD](../Assignment2/picture/ReaderCommunicationSystem/RCS_newUCD.png)

## 5. Description of Class Diagram and Sequence Diagram

### 5.1 Book Management System

#### 5.1.1 Class Diagram

![](../Assignment2/picture/BookManagementSystem/BookManagementSystem.png)

#### 5.1.2 Sequence Diagram

##### 5.1.2.1. User Give Suggestions

This sequence diagram shows what happens after a user submits a suggestion. The page sends the suggestion as a request to the backend, which receives it, returns a success message, and gives feedback in the user interface.

![](../Assignment2/picture/BookManagementSystem/UserGiveSuggestions.png)

##### 5.1.2.2. Librarian Get Suggestions

The process of administrator viewing suggestions is similar to the process of user sending suggestions, except that the request sent by the interface changes from a suggestion to a get request, and the data returned by the backend changes from success information to the content of the suggestion

![](../Assignment2/picture/BookManagementSystem/LibrarianGetSuggestions.png)

##### 5.1.2.3. Manage Inventory

This sequence diagram shows the process by which a librarian receives a suggestion and then changes the book inventory based on the suggestion. The librarian first selects one from adding books and reducing books (adding books includes adding existing books and acquiring new books). If adding books is selected, the books are added and the newly added books are classified, tagged, indexed, etc., and then the information of the book inventory is updated; if reducing books is selected, the books are directly reduced and the book information is updated.

![](../Assignment2/picture/BookManagementSystem/ManageInventory.png)

##### 5.1.2.4. Librarian Change Knowledge Graph

This sequence diagram shows the various operations of the librarian on the knowledge graph. The librarian can delete, add, or update the knowledge graph, and all three processes are similar: the interface first sends a request to the backend, which receives the request and processes it logically, then returns the result to the interface and displays it.

![](../Assignment2/picture/BookManagementSystem/LibrarianChangeKG.png)

##### 5.1.2.5. User Use Knowledge Graph

The process of using knowledge graphs by users is similar to that of librarians. Users can choose to view the current knowledge graph, use the knowledge graph to compare different books, analyze users' reading preferences based on their reading records and get recommended books, and other operations. All these operations are the process that the page initiates the request, the back-end processes it and returns the result and displays it.

![](../Assignment2/picture/BookManagementSystem/UserUseKG.png)

### 5.5 Reader Communication System

#### 5.5.1 Class Diagram

![RCS_ClassDiagram](../Assignment2/picture/ReaderCommunicationSystem/RCS_ClassDiagram.png)

#### 5.5.2 Interaction Diagram

##### 5.5.2.1 Search for Readers

This communication diagram shows the patterns of collaborations what happens after a user submits a suggestion.

![RCS_SearchforReaders](../Assignment2/picture/ReaderCommunicationSystem/RCS_SearchforReaders.png)

## References

Application Architecture Guide（<https://developer.android.google.cn/jetpack/guide?hl=zh-cn>）This webpage introduces the common application architectures for Android application development, introducing developers to a series of common architectural principles, recommended application architectures, common best practices, and some real-life application examples. It introduces developers to a series of common architectural principles, recommended application architectures, common best practices, and some real-life application examples. The layered architecture and the interface display part used in this project are designed according to this design guideline

## Contributions
