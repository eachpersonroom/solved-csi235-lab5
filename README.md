Download Link: https://assignmentchef.com/product/solved-csi235-lab5
<br>
<strong>Creating a database link, synonym, and programming distributed database system.  </strong>

If you skipped the <strong>Prologue 1 </strong>section in a specification of <strong>Laboratory 5</strong> then it is recommended to read it and to perform the actions described there now.

Implement SQL script solution1.sql that performs the following actions while connected to the “host server”.

<ul>

 <li>Create a database link from the “host server” to the “remote server”.</li>

 <li>Create a synonym names of the relational tables located at the “remote server”.</li>

 <li>Copy information about all orders and the contents of all orders submitted before 1 March 1992 from the “host server” to the “remote server”.</li>

 <li>Delete from the “host server” all orders and the contents of all orders submitted before 1 March 1992.</li>

 <li>Implement the following queries as SELECT</li>

 <li>Find the total number of orders recorded in both the “host server” and the “remote server”.</li>

 <li>Find all order keys and all prices of all orders in both “host server” and the “remote server” where a price is greater than 150000. Sort the results in the ascending order of order keys.</li>

 <li>Find all order keys of all nonempty orders, i.e. the orders that include at least one item. List the order keys together with the total number of items included in each order. Sort the results in the descending order of the total number of items included in each order. Sort all orders with the same total number of items in the ascending order of order keys. Use both “host server” and “remote server”.</li>

 <li>Find the part keys of all parts included in at least one order located in the “host server” and in at least one order located in the “remote server”.</li>

</ul>




<ul>

 <li>Drop the synonyms and a database links.</li>

</ul>




When ready, process SQL script solution1.sql and create a report from processing of the script in a file solution1.lst.




Your report must include a listing of all SQL statements processed. To achieve that put the following SQLcl commands:




SPOOL solution1

SET ECHO ON

SET FEEDBACK ON

SET LINESIZE 200

SET PAGESIZE 400




at the beginning of SQL script and




SPOOL OFF




at the end of SQL script.




<h1>Deliverables</h1>

A file solution1.lst with a report from the implementation of a script solution1.sql that creates the database links, synonyms, and processes the distributed databases.  A report must have no errors and it must list all SQL statements processed.

<u>                                                                                                                                                </u>

<h2>Prologue 2</h2>

Install VirtualBox on your systems. If you do not remember how you did it in CSIT115 then it is explained in




<u>https://documents.uow.edu.au/~jrg/115/cookbook/e1-1frame.html</u>

<strong> </strong>

how to do it.




Download from Moodle ova image of a virtual machine with Ubuntu and MongoDB. The image is available in a section OTHER RESOURCES. You should get a file:




Ubuntu18.04-64bits-MongoDB-4.2.2-08-JAN-2020.ova




Start VirtualBox and import ova image of a virtual machine with Ubuntu and

MongoDB. You should get a new virtual machine Ubuntu18.04-64bitsMongoDB-4.2.2-08-JAN-2020.




Start a virtual machine Ubuntu18.04-64bits-MongoDB-4.2.2-08-JAN-2020.

A password to login as CSCI235 user is:

csci235

When logged in, start Terminal program (3rd icon from bottom in a column of icons on the left hand size of a screen).

To start MongoDB server, process the following command in Terminal window.

mongod –dbpath data –port 4000

When MongoDB server is ready then among the other messages you should get a message:

… waiting for connection on port 4000

in a large number of messaged displayed by a starting server.

Minimize Terminal window. Do not close the window, from now, it is used as a console window by MongoDB server.

Open another Terminal window and to start MongDB command line interface, process the following command.

mongo –port 4000

For a good start, process a command help.

<strong> </strong>

<h1>Task 2</h1>

<strong>Transformation of data stored in the relational tables into data stored in BSON collection. </strong>

If you skipped the <strong>Prologue 2 </strong>section in a specification of <strong>Laboratory 5</strong> then it is recommended to read it and to perform the actions described there now.

An objective of this task is to implement PL/SQL program (anonymous block or stred procedure or stored function), that lists the contents of the relational tables REGION and NATION as a sequence of invocations of db.task2.insert(…) method. Such sequence invocations can be later used to load data into a collection of BSON documents task2. Note, that … must be replaced with the correctly formatted data such that processing of db.task2.insert(…) methods will successfully insert the documents into a collection task2.

As an example, download and unzip the files customer.zip, part.zip, and supplier.zip available on Moodle in a section SAMPLE DATABASES. You should get the files customer.js, part.js, and supplier.js. The files contains invocations db.tpchr.insert(…) methods that insert into a collection tpchr the transformed data from the relational tables CUSTOMER, ORDERS, PART, and SUPPLIER. Your PL/SQL implementation supposed to generate a sequence of invocations of db.task2.insert(…) methods that can be used to load data from the relational tables REGION and NATION into a collection of BSON documents task2.

A PL/SQL implementation technique is up to you. You can implement an anonymous PL/SQL block or stored PL/SQL procedure or stored PL/SQL function. You can reuse the outcomes of Assignment 1, Task 4.

Please note, that the contents of the relational tables REGION and NATION must be transformed into <u>nested BSON documents</u>. A solution that re-implements relational tables as the separate BSON documents scores no marks.

Save your implementation in a file solution2.sql.

When ready, process SQL script solution2.sql and save a report from processing in a file solution2-1.lst.

Your report must include a listing of all PL/SQL statements processed. To achieve that put the following SQLcl commands:

SPOOL solution2-1

SET ECHO ON

SET FEEDBACK ON

SET LINESIZE 100

SET PAGESIZE 200

SET SERVEROUTPUT ON




at the beginning of SQL script and




SPOOL OFF




at the end of SQL script.

To verify the correctness of your transformation copy the generated invocations of db.task2.insert(…) methods into a file solution2.js and use load method to create and load the contents of a collection task2 on MongDB server.

Next use the methods:

db.task2.count(); db.task2.find().pretty();

to list the total number of documents in a collection task2 and to list the contents of collection task2 in a pretty format.

When ready, copy the contents of Terminal window with the results from counting and listing of the document in task2 collection and paste it into a file solution2-

2.lst.

<h1>Deliverables</h1>

A file solution2-1.lst with a report from processing of SQL script solution2.sql. A report must list all SQL and PL/SQL statements processed and all error messages. A file solution2-2.lst with a report from processing of the methods db.task2.count() and db.task2.find().pretty().

<u>                                                                                                                                                </u>


