## Lab Report 2

## Part 1

### Code

![image](images/code1rep2.png)

![image](images/code2rep2.png)

### Server

![image](images/hello.jpeg)

![image](images/how.jpeg)

- The method called in the screenshots is ```handleRequest```.
- The argument of ```handleRequest ``` is ```url``` which is a member of the ```URI``` class, and initially, the value is  ```localhost:2500/```, then it becomes ```localhost:2500/add-message?s=Hello```, and finally it becomes ```localhost:2500/add-message?s=How%20are%20you```.
- The relevant fields of the class are:
  - path: This is called by ```getPath()```, and remains unchanged in the screenshots because even though the url is changed, it extracts the same Path as the previous part. Its value is `/add-message`.
  - query: This is called by  ```getQuery()```, and this value is changed in the screenshots. Initally it's value is ```s=Hello```, and it changes to ```s=How%20are%20you```.
 

## Part 2

### Path to the private key.

![image](images/privkey.jpeg)

### Path to the public key.

![image](images/pubkey.jpeg)

### Logging into ieng6 account without password.

![image](images/term2.jpeg)


## Part 3
I learned a lot in the 2nd and 3rd lab. Some things include how to access remote servers from the terminal of our laptops. I believe that this would be incredibly helpful in internships where we may have to connect to remote server. I even learnt how to host a server on the internet and how online requests are processed. I even learnt multiple terminal commands like `mkdir` and `scp`.

