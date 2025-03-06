![Screenshot 2025-03-06 213829](https://github.com/user-attachments/assets/d65e6511-731c-406b-bb27-bcd105c801ec)# What is client or server?
-> A server is a computer or a system that provides the resources,data,services or programs to other computers,known as clients,over a network.<br>
Example:<br>
Googl<br>
FoodPanda<br>
Fcaebook<br>
Whatsapp<br>
# API : (Application Program Interface), that allows conversation between client and server.
-> In server ,cleint related datas are stored,when we search something in youtube,the srever collected the data and connected with the database and this database fetch our required query.<br>
When we try to log in any website ,the client is connected via internet with the server the help of api,the request go to the server via API,and then the server validate this request and throw this to the database anf fetch this data or the requred data and send the OTP to the client.<br>
# What are Rest API's?
->The representational state transfer architechture perhaps the most popular approach to build API's.REST relies on a client/server approach which separates front and backends of the API.<br>
We can communicate with the client or server easily  with the help of REST api.
### Using HTTP methods for the RESTful services:
1.Get 2.Post(a logging system) 3.Update 4.Put 5.Delete <br>
To communicate with the server we use the HTTP protocols.
### How to create API's : The technologies used to built API's:
-> 1.Node.js 2.LAravel <br>
### PostMan software is used to test the API
# JSON
-> Json stands for Javascript Object Notation,is a lightweight data-interchange format,plain text written in javascript object notation,used to send data between computers and also language indepencdent.
### JSON value must have one data type : A string,number,object,array,boolean,null.
### JSON structure:
JSON data is written as name/value pairs(aka key,value pairs) <br>
Example: "name":"Protiva", <br>
"ID":41, <br>
### JSON Object:
These {} represent json object which container json value it could be string,integer,bool  etc. <br>
Example: { "name":"Protiva","ID":41,};<br>
here's are two parameters name: "name and "ID".
### Nested JSON object:
{ "status": true,<br>
  "message":"Login successful",<br>
  "data":{<br>
           "name":"Shi",<br>
           "age":23,<br>
           },<br>
             }<br>
### JSON Array:
These square bracket [] represents array in programming language or list,similarly json it has same structure to return value.<br>
This simple array which holds string value.<br>
Example: ["Ford","BMW"]<br>
Example in code:<br>
{"status": true,<br>
  "message":"Login successful",<br>
  "data":[<br>
  {<br>
  "id":41,<br>
  "user_id":2,<br>
  "time":"9.12",<br>
  "date":"3/6/2025"<br>
  }<br>
  ],<br>
  }<br>
## JSON place holder is a open source plateform that provide the API's
### When we have to use packages in flutter dart project,then <b>pub.dev website helps to get it.It is the official package repository for Dart and Flutter apps.<br>
To integrate the api we have a prpackage named http,it allows to integrate api in our project.This package uses different pacckages of networking protocols.To add the http package in project go to http/installing/dependencies/copy-http ^0.13.4<br>

<div align="center">
  <img src=![Screenshot 2025-03-06 213829](https://github.com/user-attachments/assets/f6acaa0d-41cb-4759-82ff-1e9e578e2b0f)
>
</div><br>

           

