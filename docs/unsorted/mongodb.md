## Create New Database and User
```javascript
use dbname
db.createUser( { user: "dbuser",
                  pwd: "password",
                  roles: [ { role: "readWrite", db: "dbname" } ]
              } )
```
## User Admin Login String
```bash
mongo --port 27017 -u UserAdmin -p 'pass123' --authenticationDatabase 'admin'
```
