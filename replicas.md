# HOW TO GET REPLICA SETS WORKING LMAO
## WHY WE NEED A REPLICA SET
Accessing data is easy because you just read the data
But editing data requires a transaction; this means it either fails or succeeds.
MongoDB is stupid and says that transactions must work on multiple servers, meaning you need a replica to connect them in case one of them fails the others work as backup.

## Primaries and Secondaries and Elections
A primary is basically the main server, that's the one that you connect to. It does all the important things like editing reading etc

If primary fails, the secondaries run an 'election' where they point fingers at each other and say hrmmmmmmm until one of them gets the job as primary. Just like real life

## Instructions to get replica to work:
sshhhhhhhhhhhhhhhhhhhhhhh into the server using

ssh root@107.174.243.68

Follow https://www.sohamkamani.com/docker/mongo-replica-set/ until it says "Use Dockerfile"

Use mongodb://107.174.243.68:30001/data?directConnection=true

## Keyfiles
Regular standalone servers just have a single password, which is totally very safe. However, a problem arises when multiple servers needs the same password. Which I have no clue where the problem is but there is a problem somewhere.

Anyways, you generate a keyfile, which is basically a text file with your unsecure password right inside it. If someone gets that password, you are screwed not because your database is screwed but because someone has literally found out how to access your computer files.

Inside the mongod.conf file, you add in security: keyFile=/path/to/key_file. OR you can just restart mongod and run mongod --keyFile=/path/to/key_file.

DOES NOT WORK BTW THAT'S ALL I KNOW ABT IT I LEARNED ABOUT THAT AT 3 OK SUE ME
