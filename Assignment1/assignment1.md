---
typora-root-url: picture
---

<center><font size=5 color=#008b8b>Content</font></center>

[TOC]

## 1.Introduction

### 1.1 Development background

The university library provides a large number of book resources for students and teachers, which is an important space for learning and exchanging ideas. Therefore, it is very necessary to establish an efficient and reliable library information management system. At the same time, human society is experiencing a new round of technological and industrial revolutions led by artificial intelligence, big data, and other technologies. At present, these emerging technologies are not fully applied in the field of library management. Based on the concept of Smart +, we believe that the library management system should provide more convenient and efficient information and knowledge services for schools and society by transforming it into intelligent systems. Through software engineering and big data technologies, we plan to develop an intelligent university library management system.

### 1.2 Functions of the System

- The system can realize the management of book resources and support the classification, cataloguing, labeling, indexing, input, modification, deletion, and other functions of the collection of books.

- The system can manage the borrowing information and support readers' borrowing, returning, renewing, and other businesses.

- The system supports the management of reader information and the operation of user account registration, login, and password modification. In addition, readers can be divided into teachers, students, and the public for separate management, providing different permissions for different types of readers.

- The system supports a variety of terminals, enabling users to handle services online through various terminals.

- The system supports the management of venue resources and users' reservations of venues.

- The system supports the reader communication function, which can analyze readers' reading preferences according to their borrowing records, and help readers find other readers with the same interests to communicate according to their reading preferences. 

### 1.3 Target users

- Students: Students of the university can inquire, borrow and renew books on the system, and deal with violations. They can make reservations for seats. They can log on to the forum to express views and communicate with people who have similar reading interests.

- Teachers: similar to the authority of students in the university. But the authority to query and borrow books and periodicals is higher.

- Public users: Public users can search books on the system. They can read books and periodicals in the reading room but can not take books and periodicals out of the library. Can reserve the library reading room seats.

- Librarian: Manage all the library books borrowing and returning through this system. Check out the information and borrowing status of the books. Manage the borrowing rights of various users.

- Administrator: Review forum posts in the system and deal with illegal users. 

### 1.4 Originalities of the System

1. Forum functions and readership. In the future, the system will improve the forum function, and establish their own readership circle for different reader groups. In the forum, users can have academic exchanges but also can put forward corresponding suggestions and opinions for the improvement of the library management system. In the reader circle, readers with the same reading hobby can make friends and exchange their reading insights.

2. The application of big data. Big data technology is used to collect users' daily bibliographic journal query, action location track, reading period, and other information, so as to understand the knowledge needs and reading habits of each user. In order, according to these analysis results, the system can timely complete and update the books and periodicals that are the most concerned by user groups and that has been the most frequently retrieved and borrowed, and push the latest knowledge information in each professional field required by users according to the personalized needs of users. 

## 2. Glossary of Terms

| terms                           | definition                                                                                                                                                                                                                                                                                                            |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **User**                        | All the people who could use the Smart University Library Management System.                                                                                                                                                                                                                                          |
| **Teacher**                     | The person teaching classes at the university.                                                                                                                                                                                                                                                                        |
| **Student**                     | The person enrolled in classes at the university.                                                                                                                                                                                                                                                                     |
| **Public user**                 | The system users are other than the students and teachers. Could be someone from the community near the University and so on. The system is open to society.                                                                                                                                                          |
| **Account**                     | A representation of a user's identity in a system in which a user can access certain contents of the system only after logging in to his or her account.                                                                                                                                                              |
| **Administrator**               | A person who has permission to create and delete accounts or change the book information in the system. Administrators execute the decrease or increase of books in this system.                                                                                                                                      |
| **Suggestion**                  | A piece of advice that is carried out by the users, will bring a more convenient experience to users if the advice is adopted.                                                                                                                                                                                        |
| **Book Diagram**                | A diagram that stores all the information of all the books in the library, including the name, index, category, entry time, and the borrowing authority of different users of each book.                                                                                                                              |
| **Forum**                       | An online discussion platform where users can post messages and reply to other users’ messages.                                                                                                                                                                                                                       |
| **Post**                        | A message that a user submits to the forum. A post can include text, images, videos, or other types of content.                                                                                                                                                                                                       |
| **Bookmark**                    | Mark a post so that it can be easily accessed later.                                                                                                                                                                                                                                                                  |
| **Open Space**                  | Space in the library building could be accessed by anyone with a SULMS(Smart University Library Management System) account. The open spaces have facilities including public PCs, tables and desks, bookshelves, study rooms, etc.                                                                                    |
| **Study Room**                  | A room that could be used exclusively by one or a few users for studying purposes. Only teachers and students can use a study room. One must book a spare room before using it. If the user fails to arrive on time, he or she will be punished.                                                                      |
| **Retrieve password**           | When a user forgets his or her account password, he or she can retrieve his or her password by entering his or her username and verifying the bound email address.                                                                                                                                                    |
| **Borrow books:**               | Users with authority to borrow books stocked in the library.                                                                                                                                                                                                                                                          |
| **Return books:**               | Users return the books they have borrowed from the library.                                                                                                                                                                                                                                                           |
| **Search books:**               | The user enters the information of the book he wants to query, and the system displays the corresponding book.                                                                                                                                                                                                        |
| **Renew books:**                | The user continues to borrow the books they are borrowing or pay fines for exceeding the borrowing period.                                                                                                                                                                                                            |
| **Check the borrowing record:** | The user or the librarian queries the user's borrowing records. The borrowing record includes the books that users have already borrowed and the books that they are borrowing, as well as the borrowing time of each book. Based on this, the librarian can determine whether the user exceeds the borrowing period. |
| **Manage the borrowing right:** | The librarian can manage the user's borrowing rights. Students, teachers, and public users have different permissions. In addition, the librarian can cancel the permission of the users who fail to return the books many times according to the regulations.                                                        |
|                                 |                                                                                                                                                                                                                                                                                                                       |

## 3. Use case modeling

### 3.1 Book Managment System

### 3.2 Account Management System

**Use Case Diagram**

![](/User account management system.png)

**Concise Text Descriptions** 

Login account: This use case allows the user to log in to the account by entering the correct username, password, and verification code.

Exit account: This use case allows the user to log out of the account from the system, after which the user needs to log in again in order to access the system.

Change password: This use case allows the user to change the login password of his/her account. After the change, the user must use the changed login password to log in to the account again.

Modifying user information: This use case allows the user to modify some of the personal information saved in the system, such as the mobile phone number and bound email address.

Retrieve password: This use case allows users to retrieve their login password if they forget their login password by entering the account name and then using email authentication.

Email authentication: This use case is used to verify the user's email when retrieving the password. The system sends a verification email to the email box bound to the user. The user can complete the verification by clicking the verification link in the email, and the password can be retrieved after the verification is completed.

Register account: This use case allows public users to register new accounts on their own, after registration of public users can login the account access to the system.

Bind email address: This use case is used for mailbox authentication when a user binds an email. The system sends a verification email to the email box that the user wants to bind. The user can complete the verification by clicking the verification link in the email. After the verification is completed, the binding can be completed.

Cancel account: This use case allows public users to cancel their account, which will be permanently deleted and then unable to log in to the account.

Create account: This use case allows the account administrator to create an account for the newly enrolled teachers and students. The account user name is the user's student ID or job ID, the password is the default value, and the personal information is the personal information saved in the student information management system or the faculty information management system.

Delete account: This use case allows the account administrator to delete the account for students and faculty who have left the university. After deleting the account, the account will not be used to log in to the system.

**Detailed Specification for Use Case**

Use Case:Login account

| **USE CASE**          | **Login account**                                            |
| --------------------- | ------------------------------------------------------------ |
| **ID**                | UC01                                                         |
| **Specification**     | This use case allows the user to log  in to the account by entering the correct username, password, and  verification code. |
| **Actors**            | **Users**                                                    |
| **Pre-Condition**     | The user already has his own account  in the system.         |
| **Basic Flow**        | When the user enters the  login page, the use case begins;  1. The user enters the  username, password, and verification code in the input box, and then clicks  "Login";  2. The system confirms that  the verification code entered by the user is correct;  3. The system determines  that the username and password entered by the user match;  4. The user logs in to the  account successfully, and the use case ends. |
| **Alternative Flows** | a. At any point in the login process,  the user may exit the page. In this case, the login fails and the use case  ends;  3a. If the system confirms that the  verification code entered by the user is incorrect, a message "Verification Code error" is displayed. The login  fails and the use case ends;  4a. If the system confirms that the  password entered by the user is incorrect, the system displays a message  indicating "Incorrect username or Password". The login fails and  the use case ends. |
| **Post-Condition**    | After successful login,  users can log out of the account, change the login password, or modify their  information. |

![](/Login_account.png)

Use Case:Register account

| **USE CASE**          | **Register account**                                         |
| --------------------- | ------------------------------------------------------------ |
| **ID**                | UC07                                                         |
| **Specification**     | This use case allows public users to  register new accounts on their own. |
| **Actors**            | **Public  users**                                            |
| **Pre-Condition**     | Public users access the system for the  first time and do not have their own accounts. |
| **Basic Flow**        | The use case begins when  the public user goes to the login page and clicks "Register";  1. The public user enters  the username wants to register in the input box and clicks "Next";  2. The system confirms that  the entered user name has not been used;  3. The public user enters  the password and the confirm password in the input box, and clicks “Next”;  4. The system confirms that  the password entered by the user is the same as the confirmed password;  5. The public user enters  the email address wants to bind and clicks "Verify";  6. The system sends a  verification email to the email address entered by the user, and the public  user clicks the verification link in the verification email to pass the  verification within 48 hours;  7. The account is  successfully registered, and the use case ends. |
| **Alternative Flows** | a. If the public user exits the page  at any of the first 5 steps, registration fails and the use case ends;  2a. If the system confirms that the  username entered by the public user has been used, the system displays a  prompt "The username has been used" and returns to step 1;  4a. If the system finds that the  password entered by the public user is different from the confirmed password,  the system displays the message "Confirm password is different from the  password" and returns to step 3;  6a. If the public user does not  receive the verification email, they can modify the email address and click  " Reverify " or directly click " Reverify". Then the  system will resend the verification email, and the previous verification  email will become invalid;  6b. If the public user does not  complete the authentication within 48 hours of the validity period of the  verification email, the account registration fails and the use case ends. |
| **Post-Condition**    | After successfully  registering an account, the public user can log in to the system through the  account. |

![](/Register_account.png)

### 3.3 Book Borrowing Management System

### 3.4填上各位的内容

### 3.5

## 4.Supplementary Specification

### 4.1 Objectives

### 4.2 Performance

### 4.3 Reliability

### 4.4 Security

### 4.5 Maintainability

### 4.6 Comprehensibility

### 4.7 Design constraints

## 5. References

[1] Martin Fowler. UML Distilled: A Brief Guide to the Standard Object Modeling Language (3rd Edition)[M]. Boston: Addison-Wesley Professional.

This book not only introduces the key aspects of UML, but also clearly demonstrates the role UML plays in the development process. By reading this book we can learn how to draw UML.

[2] Yanfang Xie. The Design and Implementation of University Library Management System[D]. Shanghai Jiaotong University,2011.

This article analyzes the present situation and the deficiency of library management systems at home and abroad, as well as the development trend of library management systems under the condition of the continuous information development of library business work. It also introduces the university library management system designed and developed by itself, including the development technology used in the system, the system demand analysis, the system design and implementation, and the system test and analysis.

[3]  Li Lin. Design of Digital Library Management System[J]. New Technology and New Products of China, 2021, No.438(08):30-32.DOI:10.13612/j.cnki.cntp.2021.08.010.

This article analyzes the current situation and limitations of the digital library management system, and designs a digital library management system combining the relevant technologies of big data and cloud storage, which has functions such as intelligent query, literature association, data statistics, big data user analysis, literature synchronous upload and cloud progress.

## 6.Contributions

## 7. Agile Methods
