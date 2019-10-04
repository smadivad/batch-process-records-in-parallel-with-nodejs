# Run a batch process records in parallel with nodejs

Hi! One easy way to run a batch process in parallel with **nodejs**.

## Objective
Let's assume there are **1,000,000** rows in a **postgreSQL** table need to be processed using **nodejs**. 
Each row has a **is_processed** field to indicate if it has been **processed** or not, there is also a field called **evenbatch**, it has to be set with the number or slot of batch in where is processed.


## Requirements

 - Node & npm installed (in this project run **node: v10.15.1** & **npm: 6.11.2**)
 - PostgreSQL server (used **10.7** version)
 - GIT or GITHUB

## Installation

**Clone** this repository

    git clone https://github.com/irenteria0617/batch-process-records-in-parallel-with-nodejs.git

Move to **root folder** and run:

    npm install
Create a table test in your database, run this script:

    CREATE TABLE public.test (
      id SERIAL NOT NULL,
      is_processed INTEGER DEFAULT 0 NOT NULL,
      eventbatch INTEGER,
      last_update TIMESTAMP WITHOUT TIME ZONE DEFAULT CURRENT_TIMESTAMP NOT NULL,
      PRIMARY KEY(id)
    ) 
    WITH (oids = false);
Now, lets insert **1,000,000** rows for process in our batch in the database running the follow script :

    INSERT INTO test(id) SELECT * FROM generate_series(1, 1000000);

## Demo
This image is of my project running and processing 10,000 rows. Creating **batchsize** of 1,000 rows.
![enter image description here](https://res.cloudinary.com/dn5xwgf9p/image/upload/v1570209964/preview_github/previewbatchnodejs_ggvt4u.png)
