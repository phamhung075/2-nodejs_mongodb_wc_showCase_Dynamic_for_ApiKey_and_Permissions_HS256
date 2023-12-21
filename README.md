# Node.js MongoDB Showcase with Authentication (HS256)

## Introduction

`nodejs_mongodb_wc_showCase_auth_HS256` is a Node.js application showcasing user authentication and data management using MongoDB. It employs the HS256 algorithm for secure authentication, focusing on API key creation and usage.

## Installation

To set up this project:

1. Clone the repository:
    
    `git clone https://github.com/phamhung075/2-nodejs_mongodb_wc_showCase_Dynamic_for_ApiKey_and_Permissions_HS256.git`
    
2. Change to the project directory:
    
    `cd 2-nodejs_mongodb_wc_showCase_Dynamic_for_ApiKey_and_Permissions_HS256-master`
    
3. Install necessary dependencies:
    
    `npm install`
    

## Usage

### Modules and Services

#### Access Service (`./services/access.service.js`)

Responsible for user authentication, including signup processes. Uses bcrypt for password hashing and crypto for key generation.

#### API Key Service (`./services/apiKey.service.js`)

Manages the creation and validation of API keys, critical for securing access to the application.

#### Authentication and Token Management

- **Auth Utils** (`./auth/authUtils.js`): Utilities for token generation and authentication.
- **KeyToken Service** (`./services/keyToken.service.js`): Manages token creation and validation.
- **KeyToken Model** (`./models/keyToken.model.js`): Schema for storing key tokens.

#### Models

- **Shop Model** (`./models/shop.model.js`): Manages shop data in MongoDB.
- **API Key Model** (`./models/apiKey.model.js`): Schema for API key data.

#### Utilities

- **Lodash Utility** (`./utils/index.js`): Functions for data handling like `getInfoData`.

#### Controllers

- **Access Controller** (`./controllers/access.controller.js`): Manages access routes and authentication logic.
- **Check Auth Middleware** (`./middlewares/checkAuth.js`): Ensures secure access to APIs.

#### Routes

- **Access Routes** (`./routes/access.route.js`): User access and authentication routes.
- **API Key Routes** (`./routes/apiKey.route.js`): Routes for API key management.

### MongoDB Connection

Connect to MongoDB using: `mongodb://localhost:27017`



### Postman Example for SignUp

#### Create API key 

Please uncomment lines 8 to 11 in the `apiKey.service.js` file. 
Then, make a request to http://localhost:3052/v1/api/shop/signup to create an API key, which will be displayed in the Node.js server console.
```
    // //create Api for test
    // const newKey = await apiKeyModel.create({key: crypto.randomBytes(64).toString('hex'), permissions: ['0000']});
    // console.log(newKey);
    // //end Api for test
```


now, we can signup with Apikey
```
@url_dev=http://localhost:3052/v1/api/

### signup
POST {{url_dev}}/shop/signup
Content-Type: application/json
x-api-key: bebded361da96590be34a4b7f9aa3f9db3fc637d27c95428c13d4c0ad2145cdbdb2b2974df95715efaf5335c3c7f6368e86e5f29bb846e54b3250b48fc1d7fe7

{
    "name": "cartepopup",
    "email": "cartepopup4@gmail.com",
    "password": "abc123"
}
```

For more detailed examples, refer to see [README.png](./help02.png).
