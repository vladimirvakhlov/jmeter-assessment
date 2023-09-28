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
