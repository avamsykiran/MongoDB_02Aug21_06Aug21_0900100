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

    use DATABASE_NAME               create or switch toa database
    db                              show the current database
    show dbs                        show all databases ; and a db is not visible unless
                                    it has atleast one document.
    db.dropDatabase()               is used to drop a existing database.

    db.createCollection(name)       is used to create a collection
    show collections                is used to list all the collections in the current db
    db.COLLECTION_NAME.drop()       is used to delete a collection completly

    db.COLLECTION_NAME.insertOne({}})               one record will be inserted
    db.COLLECTION_NAME.insert({}})
    db.COLLECTION_NAME.insertMany([{},{},{}])       bulk insertions
    db.COLLECTION_NAME.insert([{},{},{}])

    
    db.COLLECTION_NAME.update({"key":"value"}, {$set{"key":"newValue"}})                updates first matching record
    db.COLLECTION_NAME.findOneAndUpdate({"key":"value"}, {$set{"key":"newValue"}})
    db.COLLECTION_NAME.updateOne({"key":"value"}, {$set{"key":"newValue"}})
    db.COLLECTION_NAME.update({"key":"value"}, {$set{"key":"newValue"}},{multi:true})    updates all matching records
    db.COLLECTION_NAME.updateMany({"key":"value"}, {$set{"key":"newValue"})

    db.COLLECTION_NAME.save({_id:idValue,NEW_DATA})                                     replaces the entire record

    db.COLLECTION_NAME.remove({})                               remove all documents
    db.COLLECTION_NAME.remove({key:value})                      remove all matching documents
    db.COLLECTION_NAME.remove({key:value},1)                    remove first matching document
    db.COLLECTION_NAME.remove({key:value},{justOne:1})          remove first matching document

    db.COLLECTION_NAME.find()
    db.COLLECTION_NAME.find().pretty()
    db.COLLECTION_NAME.find({})                     find by example 
    db.COLLECTION_NAME.find({},{KEY:0/1})           projection of needed fields only
    db.COLLECTIONNAME.findOne({})                   retrive only first matching deocuemnt
    db.COLLECTION_NAME.find().limit(NUMBER)         limiting
    db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)
    db.COLLECTION_NAME.find().sort({KEY:1/0/-1})

    
    Opertion Cluases

        Operation	            Syntax	
        ============================================================================
        Equality	            {<key>:<value>}	
        Less Than	            {<key>:{$lt:<value>}}
        Less Than Equals	    {<key>:{$lte:<value>}}
        Greater Than	        {<key>:{$gt:<value>}}	
        Greater Than Equals	    {<key>:{$gte:<value>}}	
        Not Equals	            {<key>:{$ne:<value>}}	
        Values in an array	    {<key>:{$in:[<value1>, <value2>,??????<valueN>]}}	
        Values not in an array	{<key>:{$nin:<value>}}	

        And                     { $and: [ {<key1>:<value1>}, { <key2>:<value2>} ] }
        Or                      { $or: [ {<key1>:<value1>}, { <key2>:<value2>} ] }
        Not                     { $NOT: [ {key1: value1}, {key2:value2} ] }

    db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)

        Operation	            Syntax	
        ============================================================================
        $sum	                db.mycol.aggregate([{$group : {_id : "$grpcol", sumCol : {$sum : "$col"}}}])
        $avg	                db.mycol.aggregate([{$group : {_id : "$grpCol", avgCol : {$avg : "$col"}}}])
        $min	                db.mycol.aggregate([{$group : {_id : "$grpCol", minCol : {$min : "$col"}}}])
        $max	                db.mycol.aggregate([{$group : {_id : "$grpCol", maxCol : {$max : "$col"}}}])
        

    //lets create a bulky collection to learn retrivals

    db.goods.insert([
        {_id:1,title:"Rice",unit:"25kg Bag",rate:2500,category:"CERALS"},
        {_id:2,title:"Palm Oil",unit:"1 Kg Packet",rate:500,category:"OIL"},
        {_id:3,title:"Olive Oil",unit:"1 Kg Packet",rate:5100,category:"OIL"},
        {_id:4,title:"Urd Dal",unit:"1 Kg Packet",rate:56,category:"PULSES"},
        {_id:5,title:"Channa Dal",unit:"1 Kg Packet",rate:67,category:"PULSES"},
        {_id:6,title:"Groudn Nuts",unit:"1 Kg Packet",rate:80,category:"PULSES"},
        {_id:7,title:"Wheat Flour",unit:"1 Kg Packet",rate:120,category:"FLOURS"},
        {_id:8,title:"Horlicks",unit:"1 Kg Bottle",rate:560,category:"BEVERAGES"},
        {_id:9,title:"Boost",unit:"1 Kg Bottle",rate:760,category:"BEVERAGES"},
        {_id:10,title:"Coke",unit:"600ml Can",rate:100,category:"BEVERAGES"},
        {_id:11,title:"Pepsi",unit:"600ml Can",rate:100,category:"BEVERAGES"},
        {_id:12,title:"Coke",unit:"1.5ltr Bottle",rate:100,category:"BEVERAGES"},
        {_id:13,title:"Pepsi",unit:"1.5ltr Bottle",rate:100,category:"BEVERAGES"},
        {_id:14,title:"Boat Mango",unit:"250ml Pack",rate:500,category:"BEVERAGES"},
        {_id:15,title:"Boat Multi Fruit",unit:"250ml Pack",rate:500,category:"BEVERAGES"},
        {_id:16,title:"Glucose",unit:"500g Pack",rate:500,category:"BEVERAGES"},
        {_id:17,title:"Vermicelli",unit:"500g Packet",rate:450,category:"OTHERS"},
        {_id:18,title:"Popcorn",unit:"50g Packet",rate:110,category:"OTHERS"},
        {_id:19,title:"Gulab Jamun Mix",unit:"500g Packet",rate:220,category:"OTHERS"},
        {_id:20,title:"Curd",unit:"500g Packet",rate:45,category:"OTHERS"}
    ])

    db.goods.find().skip(db.goods.count()-5)
    db.goods.find({$and: [{rate:{$gt:100}},{category:"BEVERAGES"}] })
    db.goods.find({$and: [{rate:{$gt:600}},{$or:[{category:"BEVERAGES"},{category:"OIL"}]}] })
    db.goods.find({$and: [{rate:{$gt:600}},{$or:[{category:"BEVERAGES"},{category:"OIL"}]}] },{title:1,rate:1,_id:0})
    db.goods.find().sort({category:1,rate:1})
    db.goods.aggregate([{$group : {_id : "$category", totalRate : {$sum : "$rate"}}}])
    db.goods.aggregate([{$group : {_id : "$category", avgRate : {$avg : "$rate"}}}])
    db.goods.aggregate([{$group : {_id : "$category", minRate : {$min : "$rate"}}}])
    db.goods.aggregate([{$group : {_id : "$category", maxRate : {$max : "$rate"}}}])
    db.goods.aggregate([{$group : {_id : "$category", maxRate : {$max : "$rate"}}},{$sort:{maxRate:1}}])

    Mongo DB Data Types
    -------------------------------------------------------------
    string 
    int 
    boolean 
    fouble 
    arrays 
    object
    Date 
    Object ID 
    Binary data
    Code             This datatype is used to store JavaScript code into the document.


    Collection Schema Validation
    ------------------------------------------------------------------------

    db.createCollection("students", {
       validator: {
            $jsonSchema: {
                bsonType: "object",
                required: [ "name", "year", "major", "address" ],
                properties: {
                    name: {
                        bsonType: "string",
                        description: "must be a string and is required"
                    },
                    year: {
                        bsonType: "int",
                        minimum: 2017,
                        maximum: 3017,
                        description: "must be an integer in [ 2017, 3017 ] and is required"
                    },
                    major: {
                        enum: [ "Math", "English", "Computer Science", "History", null ],
                        description: "can only be one of the enum values and is required"
                    },
                    gpa: {
                        bsonType: "double",
                        description: "must be a double if the field exists"
                    },
                    address: {
                        bsonType: "object",
                        required: [ "city" ],
                        properties: {
                            street: {
                                bsonType: "string",
                                description: "must be a string if the field exists"
                            },
                            city: {
                                bsonType: "string",
                                description: "must be a string and is required"
                            }
                        }
                    }
                }
            }
        }
    })

    Validating an exiting collection
    --------------------------------------------------------------------------------------------

    db.runCommand({
        collMod: "goods",
        validator: {
            $jsonSchema: {
                bsonType: "object",
                required: [ "title", "unit", "rate", "category" ],
                properties: {
                    title: {
                        bsonType: "string",
                        description: "must be a string and is required"
                    },
                    unit: {
                        bsonType: "string",
                        description: "must be a string and is required"
                    },
                    category: {
                        enum: [ "CERALS", "PULSES", "OIL", "Beverages", "OTHERS","FLOURS" ],
                        description: "can only be one of the enum values and is required"
                    },
                    rate: {
                        bsonType: "double",
                        description: "must be a double and is required"
                    }
                }
            }
        }
    })

    MongoDB with Java
    -----------------------------------------------------------------------
        https://www.mongodb.com/blog/post/getting-started-with-mongodb-and-java-part-i

    MongoDB with Python
    -----------------------------------------------------------------------
        https://www.mongodb.com/languages/python

    What is MongoDB Atlas
    -----------------------------------------------------------------------

        MongoDB Atlas is a fully-managed cloud database developed by the same people that build MongoDB. Atlas handles all the complexity of deploying, managing, and healing your deployments on the cloud service provider of your choice (AWS, Azure, and GCP).

    MongoDB Stitch
    -----------------------------------------------------------------------
            Autorization and authentication on MongoDB clouds.USed sclae or scale down
            the manogdb managed instances.

    MongoDB Ops Manager
    -----------------------------------------------------------------------

            Crating aor dropping mongodb instances for better scalalbility.
            it can alsoe be used to bakcup and restore your mongodb instances.

    
