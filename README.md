# jmeter-assessment
Test Assessment for Assurity Consulting, written in JMeter.
# Usage
Headless:
```powershell
jmeter.bat -n -t jmeter-test.jmx -l log.jtl -e -o jmeter_report -q custom.properties -q url.properties -q loadprofile.properties
```
UI:
```powershell
jmeter.bat -t jmeter-test.jmx -l log.jtl -e -o jmeter_report -q custom.properties -q url.properties -q loadprofile.properties
```
