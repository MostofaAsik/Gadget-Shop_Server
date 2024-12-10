
# Simple Server Making Code

# Step_1

## npm init -y     //(then select react and  javascript)

## npm i express cors dotenv mongodb


# Step-2
>> create index.js file (root file)

# index.js

//Basic Requirement

const express = require('express')

const cors = require('cors')

require('dotenv').config()

const { MongoClient, ServerApiVersion } = require('mongodb');

const app = express()

const port = process.env.PORT || 3000


//middleware

app.use(express.json())

app.use(cors())

//mongodb code will appear here


const uri = `mongodb+srv://${process.env.DB_USER}:${process.env.DB_PASS}@cluster0.rvjkksn.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0`;

const client = new MongoClient(uri, {
    serverApi: {
        version: ServerApiVersion.v1,
        strict: true,
        deprecationErrors: true,
    }
});

async function run() {
    try {

        await client.connect();

        //server code will appear here





        // Send a ping to confirm a successful connection
        await client.db("admin").command({ ping: 1 });
        console.log("Pinged your deployment. You successfully connected to MongoDB!");
    } finally {
        // Ensures that the client will close when you finish/error
        // await client.close();
    }
}

run().catch(console.dir);




// Simple Api's

app.get('/', (req, res) => {
    res.send('Gadget Shop Server is Running ')
})

app.listen(port, () => {
    console.log(`Server is runnig on port ${port}`)
})


# Step-3

creating dotenv file ( root file)

# .env

DB_USER=database name (AirTicket)

DB_PASS=database password (HRFvvhGry7NfzcCz)

# Step-4
crating .gitignore file (root file)

# .gitignore

node_modules

.env

.vercel  // if needed
