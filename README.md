# Api-testing-on-postman
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://documenter.getpostman.com/view/41463947/2sB2cd4xxm
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  https://github.com/Kazi-Mostafa-Moymim/Api-testing-on-postman.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Health Check**_

### Request URL: https://practice.expandtesting.com/notes/api
### Request Method: GET
  **Response Body:**
 ```console 
  {
    "success": true,
    "status": 200,
    "message": "Notes API is Running"
}
```
 ## _**2. User Registration **_
### Request URL: https://practice.expandtesting.com/notes/api/users/register
### Request Method: POST
### Request Body:
 ```console 
{
        "name": "Mostafa",
        "email": "Mostafa@noemail.com",
        "password": "test123"
}

```
### Pre-request Script:
 ```console 
{
   var name = pm.variables.replaceIn('{{$randomFirstName}}')
pm.environment.set("name",name)
var email = pm.variables.replaceIn('{{$randomEmail}}')
pm.environment.set("email",email)
var password = pm.variables.replaceIn('{{$randomPassword}}')
pm.environment.set("password",password)
}
```
### Response Body:
 ```console 
User account created successfully
{
  "success": true,
  "status": 201,
  "message": "User account created successfully",
  "data": {
    "id": 6,
    "name": "Ebrahim",
    "email": "ebrahim@noemail.com"
  }
}

Bad Request - Invalid input data
{
  "success": false,
  "status": 400,
  "message": "Invalid input data"
}

```
## _**3. user Profile.**_
### Request URL: https://practice.expandtesting.com/notes/api/users/profile
### Request Method: GET
### Pre-request Script: None
### Header:
 ```console 

        "accept": "application/json",
        "x-auth-token": "c89135e02a92470b886827fd9ccdf45a8e3f6af19fc8483f8e3647575ae7fd21"

```
  **Response Body:**
 ```console 
User profile information retrieved successfully 200

{
  "success": true,
  "status": 200,
  "message": "Profile successful",
  "data": {
    "id": "67bf14125f5a0b0286af9adf",
    "name": "Ebrahim",
    "email": "ebrahim@noemail.com"
  }
}
	
Bad Request 400
{
  "success": false,
  "status": 400,
  "message": "Bad Request"
}
	
Unauthorized Request 401
{
  "success": false,
  "status": 401,
  "message": "Unauthorized Request"
}
	
Internal Error Server 500
{
  "success": false,
  "status": 500,
  "message": "Internal Error Server"
}
```

 ## _**4. Update the Profile Details**_
### Request URL: https://practice.expandtesting.com/notes/api
### Request Method: PUT
### Pre-request Script:
```console 
    headers: {
        "accept": "application/json",
        "x-auth-token": "c89135e02a92470b886827fd9ccdf45a8e3f6af19fc8483f8e3647575ae7fd21"
   }

Body: 
{
        "name": "Ebrahim",
        "phone": "1886644261",
        "company": "Achieve"
}
    
    
```
### Pre-request Script:
 ```console 
var secondName = pm.variables.replaceIn('{{$randomFirstName}}')
pm.environment.set("secondName",secondName)


var company = pm.variables.replaceIn('{{$randomCompanyName}}')
pm.environment.set("company",company)

```

### Response Script:
  **Request Body:** 
 ```console 
  Profile updated successful 200
{
  "success": true,
  "status": 200,
  "message": "Profile updated successful",
  "data": {
    "id": "67bf14125f5a0b0286af9adf",
    "name": "Ebrahim",
    "email": "ebrahim@noemail.com",
    "phone": "1886644261",
    "company": "Achieve"
  }
}
	
Bad Request 400
{
  "success": false,
  "status": 400,
  "message": "Bad Request"
}
	
Unauthorized Request 401
{
  "success": false,
  "status": 401,
  "message": "Unauthorized Request"
}
	
Internal Error Server 500
{
  "success": false,
  "status": 500,
  "message": "Internal Error Server"
}
	 ```
 ## _**4. Log out the Profile**_
### Request URL: https://practice.expandtesting.com/notes/api/users/logout
### Request Method: DELETE
### Pre-request Script:
  **Header:**
 ```console 
  { 
 "accept": "application/json",
        "x-auth-token": "c89135e02a92470b886827fd9ccdf45a8e3f6af19fc8483f8e3647575ae7fd21" }
```
 **Response:**
 ```console 
  { 
 
Successful Request 200
{
  "success": true,
  "status": 200,
  "message": "User has been successfully logged out"
}
	
Bad Request 400
{
  "success": false,
  "status": 400,
  "message": "Bad Request"
}
	
Unauthorized Request 401
{
  "success": false,
  "status": 401,
  "message": "Unauthorized Request"
}
	
Internal Error Server 500
{
  "success": false,
  "status": 500,
  "message": "Internal Error Server"
}```


 ## _**5. Delete the profile**_

### Request URL: https://practice.expandtesting.com/notes/api/users/delete-account
### Request Method: DELETE
### Header:
 ```console
{
        "accept": "application/json",
        "x-auth-token": "c89135e02a92470b886827fd9ccdf45a8e3f6af19fc8483f8e3647575ae7fd21"
   }


```
### Response Body: 
 ```console 
  { 
 
Successful Request 200
{
  "success": true,
  "status": 200,
  "message": "User has been successfully logged out"
}
	
Bad Request 400
{
  "success": false,
  "status": 400,
  "message": "Bad Request"
}
	
Unauthorized Request 401
{
  "success": false,
  "status": 401,
  "message": "Unauthorized Request"
}
	
Internal Error Server 500
{
  "success": false,
  "status": 500,
  "message": "Internal Error Server"
}```



## Run Command:  
- Run Command for Console: 
```console 
newman run KaziMostafaMoymim_01400804185.postman_collection.json -e KaziMostafaMoymim_01400804185.postman_environment.json 
```
- Run Command for Report: 
```console 
newman run KaziMostafaMoymim_01400804185.postman_collection.json -e KaziMostafaMoymim_01400804185.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:
![Newman Report Summary](https://github.com/Kazi-Mostafa-Moymim/Api-testing-on-postman/blob/3de037105c9f956b9b56958ed8d06ae567efe404/Screenshot%202025-04-28%20101741.png)
![Newman Report Summary](https://github.com/Kazi-Mostafa-Moymim/Api-testing-on-postman/blob/3de037105c9f956b9b56958ed8d06ae567efe404/Screenshot%202025-04-28%20101802.png)
![image](https://github.com/Kazi-Mostafa-Moymim/Api-testing-on-postman/blob/3de037105c9f956b9b56958ed8d06ae567efe404/Screenshot%202025-04-28%20101812.png)
![Newman Report Summary](https://github.com/Kazi-Mostafa-Moymim/Api-testing-on-postman/blob/3de037105c9f956b9b56958ed8d06ae567efe404/Screenshot%202025-04-28%20101820.png)
