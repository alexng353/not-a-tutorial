# Docker Setup
```bash
docker pull mongodb #yeah its that easy
```
#### init-mongo.js
```js
db.createUser(
    {
        user:"root",
        pwd:"root",
        roles:[
            {
                role:"readWrite",
                db:"testmongo"
            }
        ]
    }
)
```

#### docker-compose.yaml
```yaml
version: '3'
services:
  database:
    image: 'mongo'
    container_name: 'testmongo'
    environment:
      - MONGO_INITDB_DATABASE=testmongo
      - MONGO_INITDB_ROOT_USERNAME=root
      - MONGO_INITDB_ROOT_PASSWORD=root
    volumes:
      - ./init-mongo.js:/docker-entrypoint-initdb.d/init-mongo.js:ro
      - ./mongo-volume:/data/db
    ports:
      - 27017:27017
      - 27018:27018
      - 27019:27019
```


# Prisma
## Prisma Files
`.env`
```env
DATABASE_URL="mongodb://root:root@localhost:27017/data?authSource=admin"
```
`prisma/schema.prisma`
```prisma
generator client {

	provider = "prisma-client-js"

}

  

datasource db {

	provider = "mongodb"

	url = env("DATABASE_URL")

}
```

## Commands
```bash
npx prisma init
# edit prisma files
npx prisma db pull
npx prisma generate

```