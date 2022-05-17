# node-express-typescript
### Simple application structure of node express typescript

### Project setup steps : 

#### step 1 : mkdir node-express-typescript
#### step 2 : cd node-express-typescript
#### step 3 : npm init // creating package.json
#### step 4 : npm i typescript
#### step 5 : npx tsc --init // creating tsconfig.json
#### step 6 : npm i body-parser cross-env dotenv express helmet rimraf // add project dependencies 
#### step 7 : npm i @types/body-parser @types/express @types/node
#### step 8 : npm i --save-dev concurrently nodemon
#### step 9 : Update the below scripts in package.json file
           "scripts": {
              "build": "rimraf dist && tsc",
              "start": "cross-env NODE_ENV=development concurrently \"tsc --watch\" \"nodemon -q dist/index.js\"",
              "prestart": "npm run build",
              "test": "echo \"Error: no test specified\" && exit 1"
            },

#### step 10 : Creating the index.ts file and adding the below code sinnpets
            import express, { Express, Request, Response } from 'express';
            import bodyParser from 'body-parser';
            import helmet from 'helmet';
            import dotenv from 'dotenv';

            dotenv.config();

            const PORT = process.env.PORT || 3000;
            const app: Express = express();

            app.use(helmet());
            app.use(bodyParser.json());
            app.use(bodyParser.urlencoded({ extended: true }));

            app.get('/', (req: Request, res: Response) => {
              res.send('<h1>Hello from the TypeScript world!</h1>');
            });

            app.listen(PORT, () => console.log(`Running on port : ${PORT}`));


#### Step 11 : npm run start
#### Hit the http://localhost:3000/ in browser. 
