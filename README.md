MongoDB
---------------------------------------------------------

    https://github.com/avamsykiran/MongoDB_02Aug21_06Aug21_0900100.git


    What is MongoDB?
        NoSQL Database Management System

    Database Management System:
        Data Availablity
        Data Consistency
        Reliability
        Transaction Atomicity and Management

    Database Models
        Flat File Data Models
        Network Data Models
        Hyrarchial Data Models
        Relational Data Models

    Graph Representation of Data         Hyrarchial Data Models
    ------------------------------------------------------------------

            D2H Portal
            -------------
                    Channel
                    Packages
                    Subscriber


                    Subscriber
                        has multiple Packages
                                        has a group of Channels

                    Subscribers: [{
                        subId
                        subName
                        Packages : [{
                            packId:
                            activationDate:
                            validTillDate:
                            channels:{[

                            ]}
                        }]

                    }]


    Hyrarchial Data Model
    ----------------------[ noSQL ]

        MongoDB
        ChacheDB
        ....etc


    Lab Setup
    -----------------

        MongodB Server
        MongodB Client

                https://fastdl.mongodb.org/windows/mongodb-windows-x86_64-5.0.1-signed.msi


    Start Your Server:
                            mongod --dbpath ./data
                            
    Start Your Commad Line Cleint
                            mongo


    MongodB DB structure                        RDBMS DB Structure 
    --------------------------------------------------------------------
    Database                                        Database
        Collection                                      Table
            Docuemnts                                       Record/Row/Tuple
                Fields and Document                                 Attributes/Col/Fields


    MongoDB Commands
    ---------------------------------------------------------------------

    use DATABASE_NAME       create or switch toa database
    db                      show the current database
    show dbs                show all databases ; and a db is not visible unless
                            it has atleast one document.
    db.dropDatabase()       is used to drop a existing database.

    db.createCollection(name)
    show collections
    db.COLLECTION_NAME.drop()

    db.COLLECTION_NAME.insertOne({}})
    db.COLLECTION_NAME.insertMany([{},{},{}])
    db.COLLECTION_NAME.insert({}})
    db.COLLECTION_NAME.insert([{},{},{}])

    db.COLLECTION_NAME.find()
    db.COLLECTION_NAME.find().pretty()
    db.COLLECTIONNAME.findOne({})           Query data by example

    Opertion Cluases

    Operation	            Syntax	
    ============================================================================
    Equality	            {<key>:<value>}	
    Less Than	            {<key>:{$lt:<value>}}
    Less Than Equals	    {<key>:{$lte:<value>}}
    Greater Than	        {<key>:{$gt:<value>}}	
    Greater Than Equals	    {<key>:{$gte:<value>}}	
    Not Equals	            {<key>:{$ne:<value>}}	
    Values in an array	    {<key>:{$in:[<value1>, <value2>,……<valueN>]}}	
    Values not in an array	{<key>:{$nin:<value>}}	

    And                     { $and: [ {<key1>:<value1>}, { <key2>:<value2>} ] }
    Or                      { $or: [ {<key1>:<value1>}, { <key2>:<value2>} ] }
    Not                     { $NOT: [ {key1: value1}, {key2:value2} ] }
