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
