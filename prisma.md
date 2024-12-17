## Prisma 
[Docs](https://www.prisma.io/docs/getting-started)

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

## Seed
Create a new file seed.js like this:

```javascript
const { PrismaClient } = require("@prisma/client");
const prisma = new PrismaClient();

async function main() {
  const author = {
    name: "Ana Beatriz",
    username: "anabeatriz_dev",
    avatar:
      "https://raw.githubusercontent.com/viniciosneves/code-connect-assets/main/authors/anabeatriz_dev.png",
  };
  const ana = await prisma.user.upsert({
    where: { username: author.username },
    update: {},
    create: author,
  });

  const posts = [
  ];
  posts.forEach(async (post) => {
    await prisma.post.upsert({
        where: { slug: post.slug },
        update: {},
        create: post,
      });
  })

  console.log('Author created', ana)
}
main()
  .then(async () => {
    await prisma.$disconnect();
  })
  .catch(async (e) => {
    console.error(e);
    await prisma.$disconnect();
    process.exit(1);
  });
```
Then add a new command to package.json:

```javascript
  },
  "prisma": {
    "seed": "node prisma/seed.js"
  },
  "dependencies": {
```
To execute, run ```npm run prisma seed```
