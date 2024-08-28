Enabling MongoDB Replica Set Locally
Modify MongoDB Config File
To enable replication, you need to change the replication settings in your MongoDB configuration file (mongod.conf or equivalent).

Add the following lines:

yaml
Copy code
replication:
  replSetName: "myReplicaSet"
Restart MongoDB
After making the changes, restart your MongoDB instance for the new replication settings to take effect.

Initiate Replica Set in Mongo Shell

Open your Mongo shell.

Switch to your desired database (for example, from test to prisma):

bash
Copy code
test> use prisma
switched to db prisma
Initiate the replica set by running the following command:

bash
Copy code
prisma> rs.initiate({
  _id: "myReplicaSet",
  members: [{ _id: 0, host: "127.0.0.1:27017" }]
})
Verify Replica Set Status

Check that the replica set has been initiated correctly. You should see:

bash
Copy code
{ ok: 1 }
If { ok: 1 } is returned, the replica set has been successfully configured, and your issue should be resolved.