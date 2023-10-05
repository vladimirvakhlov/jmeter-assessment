# jmeter-assessment
Test Assessment for Assurity Consulting, written in JMeter.
# Usage
Headless:
```powershell
jmeter.bat -n -t jmeter-test.jmx -f -l log.jtl -e -o jmeter_report -q custom.properties -q url.properties -q loadprofile.properties
```
UI:
```powershell
jmeter.bat -t jmeter-test.jmx -f -l log.jtl -e -o jmeter_report -q custom.properties -q url.properties -q loadprofile.properties
```
Note that -f forces to remove log result file from working directory before running test.
# Pre-requisites
- You have to use ``mongo-java-driver-3.9.0.jar`` for that, so copy the file from the bundled ``apache-jmeter-5.6.2`` or use the entire bundled jmeter.
- Ensure that you have a connection to the MongoDB
  - In our case we use Amazon DocumentDB, which is closed for access from outside of Amazon network and you have to create a network tunnel to that using another ec2 instance.
  - Example of the tunnel commandline:
    ```
    ssh -i "mykey.pem" -L 27017:super-uber-docdb.ccnsv7yrewjt.ap-southeast-2.docdb.amazonaws.com:27017 ec2-user@ec-2-amazon-host.com
    ```
    where
    ``mykey.pem`` is the key to access ec2 instance;
    
    first port is the local port request to which will be forwarded;
    
    super-uber-docdb... is the server name and port to which request will be forwarded.;
    
    if the command is successful, then whenever you send request to ``localhost:27017`` it will be forwarded to ``super-uber-docdb.ccnsv7yrewjt.ap-southeast-2.docdb.amazonaws.com:27017`` using ``ec-2-amazon-host.com``
# MongoDB Settings
Use the following settings in custom.properties to connect to mongodb
```properties
#---------------------------------------------------------------------------
# Optional MongoDB connection
#---------------------------------------------------------------------------
#
mongodb.address=localhost
mongodb.port=27017
mongodb.dbname=test_mongo
mongodb.name=[name]
mongodb.password=[password]
```
Use the following settings in loadprofile.properties to push results into mongodb:
```properties
#Collection to upload results to mongodb
mongodb.collection=test_collection2
```
Note that if one of mongodb.address, mongodb.port, mongodb.dbname or mongodb.collection is absent, the entire attempt to write to mongodb will be skipped.

When running, JMeter will check if specified collection exists in MongoDB, and if not, it will create one.
