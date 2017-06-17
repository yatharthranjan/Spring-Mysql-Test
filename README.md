# Spring-Mysql-Test
Test and deploy a spring java application with mysql interactions on heroku platform using the ClearDB add-on.

To test run this application, Run the following URLs in your browser:
1. For creating a new user in the database : https://dry-earth-89710.herokuapp.com/demo/add?name=anyName&email=anyEmail
   Note that you can send any name or email as a paramter for get http request.
2. For Displaying all the user in the database in JSON format : https://dry-earth-89710.herokuapp.com/demo/all


This simple application was first created on the loaclhost using Spring and Hibernate with the help of this tutorial : https://spring.io/guides/gs/accessing-data-mysql/

If you do not know how to use spring in java please follow the tutorial on this repository first : https://github.com/yatharthranjan/Spring-Test





After creating all the files or cloning them, follow the following steps to deploy your application on heruko platform-

1. Create a free account on https://heroku.com
2. Install the heroku Command Line Interface (CLI)
3. run the following command on your command shell : $ heroku login
4. Login with your heroku account credentials.
5. next clone this repository and change directory in command prompt to this repository(eg. $ cd Spring-Mysql-Test).
6. run the following command on your command shell : $ heroku create
7. This will create a unique heroku app for you.
8. Now deploy the code using the command: $ git push heroku master
9. So right now you have your application on heruko but it will not work if you try to run it. This is because you need to      create a MySQL database and add those credentials to your app so hibernate can make connections to database using JDBC.
10. For creating database in heruko we will use the ClearDB add-on for heruko.
11. In the command prompt type the following to add ClearDB to your application : $ heroku addons:create cleardb:ignite 
12. You may be asked to enter billing information for the above task. Do this without hesitation since CLearDB is free.
13. Now get the database URL like this : $ heroku config | grep CLEARDB_DATABASE_URL
14. On execution of this command you will see the Database URL which is of the form : 
    mysql://[username]:[password]@[host/db]
15. Now you can access your database under the 'Resources' tab in your heroku app.
16. Now you just need to update the credentials of the database in your application.properties file. In order to do that,       open the application.properties file of the repository with any text editor and update the values as follows - 
          spring.datasource.url = jdbc:mysql://host/db
          spring.datasource.username = username
          spring.datasource.password = password
          
17. Here the host, db, username and password can be identified from the Dtatabase URL generated in step 13 and comparing         with the format given in step 14.
18. Now you are ready to deploy and run the updated version of your application. Run the following commands to add, commit and push the updated version to git and heruko :
          $ git add .
          $ git commit -am "your commit message"
          $ git push heruko master
19. This is it. You now have a full working MySQL database with Spring java backend like a REST API. You can run your app through the URL in your browser : [Your Heruko app name you created]/demo/add?name=anyName&email=anyEmail
and [Your Heruko app name you created]/demo/all
eg. For me the app name is- https://dry-earth-89710.herokuapp.com
