This is the playbook to configure the MongoDb with Datadog<br>
<b>Prerequrities:</b><br>
-MongoDb server should be configured as follows<br>
-In etc/mongodb.conf  add <br>

replication:<br>
             replSetName: nameOfrepelset <br>

-Restart the monodb by "sudo service mongod restart"<br>
-After restarting the mongodb  <br>
Use this in MongoDb serevr:<br>
>Mongo<br>
>use admin<br>
>db.createUser({"user":"datadog", "pwd": "your passsword", "roles" : [ {role: 'read', db: 'admin' }, {role: 'clusterMonitor', db: 'admin'}, {role: 'read', db: 'local' }]})<br>
>rs.initiate({_id:"nameOfreplset",members:[{"_id":1,"host":"localhost:27017"}]})


-Run  the  playbook "Datadog-mongodb" <br>
 <i>ansible-playbook playbook-name</i><br>
 -restart the datadog:<br>
    <i>sudo /etc/init.d/datadog-agent restart</i><br>
 -check status of data-dog: <br>
     <i>sudo /etc/init.d/datadog-agent info<i><br>

     
