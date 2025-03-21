# What is client or server?
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
### We can make fake API's in -> webhook.site
### To find the structure of API's response ->jsonviewer.stack.hu
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
 ![Screenshot 2025-03-06 213829](https://github.com/user-attachments/assets/f6acaa0d-41cb-4759-82ff-1e9e578e2b0f)

## api code figure from jsonplaceholder site :
![image](https://github.com/user-attachments/assets/cc8dbc29-eb8b-4f63-8efa-12acf16934c9)
## In this case we see there is no name of the array
#### For this purpose we have to make our own Model to identify this array in our flutter project.Also when we copy the api code from postMan to the jsonToDart  file ,it provide only the object not array. For this we want a Future function and also declare and initialization the list.

The getPhotos function is a Future function in Flutter that retrieves a list of photos from the JSONPlaceholder API (https://jsonplaceholder.typicode.com/photos). It fetches the data, decodes the JSON response, converts it into a list of Photos objects, and returns the list.
## To hit the API the the code: 

### 1.List photosList = []; 
Creates an empty list photosList to store photo data
### 2.Future<List> getPhotos() async {
Defines an asynchronous function (getPhotos) that returns a Future<List>, meaning it will perform an operation that takes time and return a list when completed.
### 3.final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/photos'));
Makes an HTTP GET request to fetch data from the given API.
await waits for the response before moving to the next line.
### 4.var data = jsonDecode(response.body.toString());
Converts the API response (JSON format) into a Dart object (a list of maps).
### 5.if (response.statusCode == 200) {
Checks if the API call was successful (statusCode == 200 means success).
### 6.for (Map i in data) {
Iterates over each JSON object (photo entry) in the list.
### 7.Photos photos = Photos(
  #### title: i['title'], 
  #### url: i['url'], 
 #### id: i['id'], 
 #### thumbnailUrl: i['thumbnailUrl']
### );
Creates a Photos object from the JSON data.
Extracts title, URL, ID, and thumbnail URL for each photo.
### 8.photosList.add(photos);
Adds the photo object to the photosList.
### 9.return photosList;
Returns the list of photos after processing all items.
### 10.} else {
####  return photosList;
### }
If the API request fails, it returns the empty photosList.

### Summary
🔹 Fetches data from an API ✅<br>
🔹 Decodes JSON into Dart objects ✅<br>
🔹 Stores objects in a list ✅<br>
🔹 Returns the list for UI display ✅<br>

## Now we have to generate Future.builder function in the body of code:
# Why Do We Use FutureBuilder?
FutureBuilder is used in Flutter to handle asynchronous operations, such as fetching data from an API. It automatically rebuilds the widget based on the state of the Future (loading, success, or error). This avoids manually managing states like "loading" and "data received" and makes UI updates smoother.
### Note for Students 📌
FutureBuilder simplifies API data handling by automatically updating UI when the data arrives.<br>
It prevents crashes when data is still loading (instead of accessing null values).<br>
Use snapshot.hasData to check if data is available before using snapshot.data!.<br>
This approach ensures a smooth user experience with dynamic and scalable lists.<br>

### FutureBuilder(
  #### future: getPhotos(),
Calls the getPhotos() function, which fetches data from an API.<br>
The FutureBuilder waits for the result and rebuilds when data is available.

### builder: (context, AsyncSnapshot<List<Photos>> snapshot){
The builder receives an AsyncSnapshot, which represents the state of the future (loading, success, or error).<br>
It provides access to the data when available.

### return ListView.builder(
 #### itemCount: photosList.length,
 #### itemBuilder: (context,index){
Uses ListView.builder to dynamically create a list of photo items.<br>
itemCount is set to photosList.length to match the number of fetched items.

### return ListTile(
####  leading: CircleAvatar(
    backgroundImage: NetworkImage(snapshot.data![index].url.toString()),
###  ),
leading CircleAvatar: Displays a large profile image from the url.<br>
Uses NetworkImage to fetch and display the image from the web.

### subtitle: Text(snapshot.data![index].title.toString()),
### title: Text('Note the id: '+snapshot.data![index].id.toString()),
Title: Shows the photo's title as a subtitle.<br>
ID: Displays the photo’s unique identifier.

### Final Summary 🚀
🔹 Fetches API Data Using FutureBuilder ✅<br>
🔹 Manages Asynchronous States Automatically ✅<br>
🔹 Displays Data in a ListView Dynamically ✅<br>
🔹 Optimized for Performance in Flutter ✅



 # Flutter get API call with Null Safety: (Plugins make the Model)
### 1. Go to the website -> jsonplaceholder ->Go Routes ->Get /Posts->copy the URL ->Check this URL in PostMan.
### 2. Go to the Flutter project -> go pubspec.yaml and pubget http: ^0.13.4 -> and import http package (import 'package:http/http.dart' as http;)
### 3. When we install plugins in flutter project ,it's not working untill there's exist a name of api's object or array.So there's a problem to create a exact model we want.For this go to the lib of flutter project and create a directory named-> Models.
### 4. Again go to the Models -> New ->Json To Dart -> create class name (PostsModel) -> if our project show null safety then click this ->now copy paste the api code from the PostsMan and generate it.
### 5. We see that there's only the object is created in PostsModel, for this there is no array or list exist,that's why we have to initialize the array or list in our code.And make a custom list:
Go to the home page ->
write the code of Future function under class:
### .......................

## 1.Flutter get API call with Null Safety: (Plugins make the Model)

##### class _HomScreenState extends State<HomScreen> {
 ##### List<PostsModel> postList = [];

#####  Future<List<PostsModel>> getPostApi() async {
    final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/posts'));
    var data = jsonDecode(response.body.toString());
    if (response.statusCode == 200) {
     for (Map i in data) {
        postList.add(PostsModel.fromJson(i));
      }
      return postList;
    } else {
      return postList;
    }
#####  }
#####  @override
#####  Widget build(BuildContext context) {
    return Scaffold();
#####  }
#####  }
#### ....................


![Screenshot 2025-03-15 114819](https://github.com/user-attachments/assets/7c1bbea0-dcf7-40f3-956d-dfaea3940e58)

#### For this our API is hit in our flutter project ^
### 6.Now we have to show this API:
Write the code under body:
#### ......................
#####   @override
 ##### Widget build(BuildContext context) {
#####  return Scaffold(
    appBar: AppBar(
      title: Text("Api Course"),
    ), // AppBar
    body: Column(
      children: [
        Expanded(
          child: FutureBuilder(
            future: getPostApi(),
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return Text("Loading...");
              } else {
                return ListView.builder(
                  itemCount: postList.length,
                  itemBuilder: (context, index) {
                    return Text(postList[index].title.toString());
                  },
                );
              }
            },
          ), // FutureBuilder
        ), // Expanded
      ],
    ), // Column
#####  ); // Scaffold
#####   }
#### ...........................


![Screenshot 2025-03-15 121046](https://github.com/user-attachments/assets/206ac7d3-35ff-4d56-8a1e-1ff2fc19ec27)


![Screenshot 2025-03-15 121852](https://github.com/user-attachments/assets/0fa40300-ec56-4f4e-8f42-d982294cfd58)

## To arrange more suitable form write this in reuturn :
##### return Card(
                        child: Padding(
                          padding: const EdgeInsets.all(8.0),
                          child: Column(
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: [
                              Text(
                                snapshot.data![index].title,
                                style: const TextStyle(
                                  fontSize: 18,
                                  fontWeight: FontWeight.bold,
                                ),
                              ),
                              const SizedBox(height: 5),
                              Text(
                                snapshot.data![index].body,
                                style: const TextStyle(fontSize: 16),
                              ),
                            ],
                          ),
                        ),
                      );


                      
# Or ->
![Screenshot 2025-03-15 121923](https://github.com/user-attachments/assets/0f503ad9-57ec-499b-9a8d-9e97809858e1)


![Screenshot 2025-03-15 122317](https://github.com/user-attachments/assets/93b3b215-2306-445a-8140-359a08fba1c4)


## 2. Flutter get API with null safety: (If plugins faild to create a Model)
###### import 'package:flutter/material.dart';
###### import 'dart:convert';
###### import 'package:http/http.dart' as http;

###### class ExampleTwo extends StatefulWidget {
######   ExampleTwo({super.key});



######  @override
######  State<ExampleTwo> createState() => _ExampleTwoState();
###### }

###### class _ExampleTwoState extends State<ExampleTwo> {


######  List<Photos> photosList=[];

######  Future<List<Photos>> getPhotos() async{
    final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/photos'));
    var data = jsonDecode(response.body.toString());
    if(response.statusCode==200){
      for(Map i in data){
        Photos photos=Photos(title: i['title'], url: i['url'],id:i['id'],thumbnailUrl:i['thumbnailUrl']);
        photosList.add(photos);
      }
      return photosList;
    }
    else{
      return photosList;
    }
 ###### }


######  @override
######  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Photos Api'),
        backgroundColor: Colors.blueAccent,
      ),
      body: Column(
        children: [
          Expanded (child:
          FutureBuilder(
              future: getPhotos(),
              builder: (context, AsyncSnapshot<List<Photos>> snapshot){
                return ListView.builder(
                    itemCount: photosList.length,
                    itemBuilder: (context,index){
                      return ListTile(
                        leading: CircleAvatar(
                          backgroundImage: NetworkImage(snapshot.data![index].url.toString()),
                        ),
                        trailing: CircleAvatar(backgroundImage: NetworkImage(snapshot.data![index].thumbnailUrl.toString(),
                          // Ensures the image covers the available space
                        ) ),

                        subtitle: Text(snapshot.data![index].title.toString()),
                        title: Text('Note the id: '+snapshot.data![index].id.toString()),
                      );
                    });
              }),)

        ],
      ),
    );
######  }
###### }


###### class Photos{
######  String title, url,thumbnailUrl ;
######  int id;
######  Photos({required this.title,required this.url,required this.thumbnailUrl,required this.id});
###### }

https://github.com/user-attachments/assets/579886b6-4713-45b0-9d50-5b51b84636f8


## 3.Flutter get API call with Null Safety: (Plugins make the Model) ->Complex Nested Object

###### import 'package:flutter/material.dart';
###### import 'dart:convert';
###### import 'package:http/http.dart' as http;
###### import 'package:untitled/Models/UserModel.dart';

###### class ExampleThree extends StatefulWidget {
 ######  ExampleThree({Key?key}): super(key: key);

######  @override
######  State<ExampleThree> createState() => _ExampleThreeState();
###### }

###### class _ExampleThreeState extends State<ExampleThree> {

 ###### List<UserModel> userList=[];

######  Future<List<UserModel>> getUserApi() async{
    final response =await http.get(Uri.parse('https://jsonplaceholder.typicode.com/users'));

     var data = jsonDecode(response.body.toString());
    if(response.statusCode==200){
      for(Map i in data){
        print(i['name']);
          userList.add(UserModel.fromJson(i as Map<String, dynamic>));
      }
      return userList;
    }
    else {
      return userList;
    }
######  }


######  @override
######  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          Expanded(
              child:
          FutureBuilder(future: getUserApi(),
              builder: (context,AsyncSnapshot<List<UserModel>> snapshot){
              if(!snapshot.hasData){
                return CircularProgressIndicator();
              }
              else{
                return ListView.builder(
                    itemCount: userList.length,
                    itemBuilder: (context,index){

                      return Card(
                        child: Padding(padding: EdgeInsets.all(8.0),
                        child: Column(
                          mainAxisAlignment: MainAxisAlignment.spaceBetween,
                          children: [
                            ReusbaleRow(title: 'Name', value: snapshot.data![index].name.toString()),
                            ReusbaleRow(title: 'UserName', value: snapshot.data![index].username.toString()),
                            ReusbaleRow(title: 'Email', value: snapshot.data![index].email.toString()),
                            ReusbaleRow(title: 'Address', value: snapshot.data![index].address!.city.toString()+
                                snapshot.data![index].address!.geo!.lat.toString() +
                                snapshot.data![index].address!.geo!.lng.toString()),
                          ],
                        ),)
                      );
                    }
                );
              }
              }),
          )
        ],
      ),
    );
######  }
###### }

###### class ReusbaleRow extends StatelessWidget {
######  String title,value;
######   ReusbaleRow({Key?key,required this.title,required this.value}): super(key: key);

######  @override
######  Widget build(BuildContext context) {
    return Padding(padding: EdgeInsets.all(8.0),
    child: Row(
      mainAxisAlignment: MainAxisAlignment.spaceBetween,
      children: [
        Text(title),
        Text(value),
      ],
    ),
    );
######  }
###### }



https://github.com/user-attachments/assets/a4e4b945-9c1b-4dbc-970b-dd12f2b7354d

## 4.Building List with Complex Very JSON Data || Flutter Get API Call with null safety
....................
###### class _ExampleFour extends State<ExampleFour> {
 ###### Future<ProductsModel> getProductsApi () async {

    //create your own api
    final response = await http.get(Uri.parse('https://webhook.site/d24f9761-dfba-4759-bcda-f42f3dd539b7'));
    var data = jsonDecode(response.body.toString());
    if(response.statusCode == 200){
      return ProductsModel.fromJson(data);
    }else {
      return ProductsModel.fromJson(data);

    }
######  }

######  @override
######  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        centerTitle: true,
        title: Text('Api Course'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          children: [
            Expanded(
              child: FutureBuilder<ProductsModel>(
                future: getProductsApi (),
                builder: (context , snapshot){
                  if(snapshot.hasData){
                    return ListView.builder(
                        itemCount: snapshot.data!.data!.length,
                        itemBuilder: (context, index){
                          return Column(
                            mainAxisAlignment: MainAxisAlignment.start,
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: [
                              ListTile(
                                title: Text(snapshot.data!.data![index].shop!.name.toString()),
                                subtitle: Text(snapshot.data!.data![index].shop!.shopemail.toString()),
                                leading: CircleAvatar(
                                  backgroundImage: NetworkImage(snapshot.data!.data![index].shop!.image.toString()),
                                ),
                              ),
                              Container(
                                height: MediaQuery.of(context).size.height *.3,
                                width: MediaQuery.of(context).size.width * 1,
                                child: ListView.builder(
                                    scrollDirection: Axis.horizontal,
                                    itemCount: snapshot.data!.data![index].images!.length,
                                    itemBuilder: (context, position){
                                      return Padding(
                                        padding: const EdgeInsets.only(right: 10),
                                        child: Container(
                                          height: MediaQuery.of(context).size.height *.25,
                                          width: MediaQuery.of(context).size.width * .5,
                                          decoration: BoxDecoration(
                                              borderRadius: BorderRadius.circular(10),
                                              image: DecorationImage(
                                                  fit: BoxFit.cover,
                                                  image: NetworkImage(snapshot.data!.data![index].images![position].url.toString())
                                              )
                                          ),
                                        ),
                                      );
                                    }),
                              ),
                              Icon(snapshot.data!.data![index].inWishlist! == false ? Icons.favorite : Icons.favorite_outline)
                            ],
                          );
                        });
                  }else {
                    return Text('Loading');
                  }
                },
              ),
            )
          ],
        ),
      ),
    );
######  }
###### }
![image](https://github.com/user-attachments/assets/6959c641-6900-4736-ae93-30ca1562eab7)

## For more explanation check it -> https://github.com/Protiva-Bose/Dart.Api/blob/main/Dart.Api


