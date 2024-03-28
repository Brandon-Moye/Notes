# MongoDB

Purpose: document learning while creating Bridge with MongoDB

### Terminology b/n SQL and NoSQL (MongoDB)

| SQL      | NoSQL      |
| -------- | ---------- |
| Cluster  | Cluster    |
| Database | Database   |
| Table    | Collection |
| Row      | Document   |
| Column   | Field      |

### Atlas

- Configure Database Access for Authentication methods and allow anonymous for production
- To view data in a cluster go to: Data Services Tab>Database>Browse Collections>

### Compass

- GUI interface for MonogDB
- easy way to upload new datasets
- Aggregations Tab
  - Plan out pipeline/filters and then export the code in the language of your choosing
  - **filtering** fields is called **$project** where if you set paramters: 1 then it will just return those parameter
- Schema Tab
  - Graphical representation of data

### Realm

_backend with api routes, user auth, graph ql without hosting a server_

_serverless functions to use Realm as the backend API connecting to the Atlas database and supplying data to the application front end_

- Functionalities
  - Functions
    - build out APIs for the app
  - User Auth
    - internal or outside providers
  - Triggers
  - execute f(x)s based on events in the DB, user auth events, or schedules
  - Data Access Control
  - 3rd Party Services
  - GraphQL
- Realm needs to be connected to a Cluster

| Save                | Deploy          |
| ------------------- | --------------- |
| creates a dev draft | makes it public |

- For authenticaion you will probably want to turn on anynomous authentication in Realm

#### Realm - Functions

Basic serverless function that provides an API route to return all of our products:
```
exports = function(arg) {
let collection = context.services.get("mongodb-atlas").db("store").collection("products");
return collection.find({})
}
```
return one specific product:
```
exports = function(arg) {
let collection = context.services.get("mongodb-atlas").db("store").collection("products");
return collection.findOne({_id: BSON.ObjectId(arg)})

//arg is what is passed from the function call, this would be a specific ID
```

#### Realm - SDKs
- install SDK for your app and add the anonymous user function to get it connected
code to connect Realm App ID:
```
import * as Realm from "realm-web"
useEffect(async() => {
  const REALM_APP_ID = "" //get from products bar, put in .env file
  const app = new.Realm.App({id: REALM_APP_ID});
  const credentials = Realm.Credentials.anonymous();
  try {
    const user = await app.logIn(credentials);
    const allProducts = await user.functions.getAllProducts
  }
  //getAllProducts was a servless function written in the Realm exampe
})
```