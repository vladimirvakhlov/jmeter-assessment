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
# MongoDB Settings
Use the following settings in custom.properties to connect to mongodb
```properties
#---------------------------------------------------------------------------
# Optional MongoDB connection
#---------------------------------------------------------------------------
#
mongodb.address=localhost
mongodb.port=27017
mongodb.dbname=logs_jmeter
mongodb.name=name
mongodb.password=pass
```
Use the following settings in loadprofile.properties to push results into mongodb:
```properties
#Collection to upload results to mongodb
mongodb.collection=test_collection2
```
Note that if one of mongodb.address, mongodb.port, mongodb.dbname or mongodb.collection is absent, the entire attempt to write to mongodb will be skipped.

When running, JMeter will check if specified collection exists in MongoDB, and if not, it will create one.
