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

                

