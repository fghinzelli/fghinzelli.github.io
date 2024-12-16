## Prisma
Prisma is a Javascript ORM to create and management databases on node applications.]

## Installation
```bash
npm install prisma
```
## Initialization
```bash
# Create a prisma folder with a file named *schema.prisma* and a .env file
npx prisma init
```
## Create models

```javascript
model User {
  id Int @id @default(autoincrement())
  name String
  username String @unique
  avatar String
  Post Post[]
}

model Post {
  id Int @id @default(autoincrement())
  cover String
  title String
  slug String @unique
  body String
  markdown String
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  authorId Int
  author User @relation(fields: [authorId], references: [id])
}
```

## Generate migrations
Before, edit file .env with the user/password of the database
```bash
npx prisma migrate dev --name init
```

## Generate client
It's necessary to generate the client every time the database is changed
```bash
npx prisma generate
```
