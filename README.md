> [!NOTE]
> Here's scripts to install and integrate Dependency Check and Sonarqube on Jenkins:

> Dependency check
```if [ ! -f /tmp/dependency-check/bin/dependency-check.sh ]
then
	curl -Lo /tmp/dependency-check.zip https://github.com/jeremylong/DependencyCheck/releases/download/v10.0.3/dependency-check-10.0.3-release.zip
 	unzip /tmp/dependency-check.zip -d /tmp/
fi
	/tmp/dependency-check/bin/dependency-check.sh -s . --disableYarnAudit -project NodeGoat -o . -f ALL
```


> Sonarqube script:
```
if [ ! -f /tmp/sonar-scanner/bin/sonar-scanner ]
then
    curl -Lo /tmp/sonnar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-6.1.0.4477.zip
    unzip /tmp/sonarscanner.zip -d /tmp
fi
/tmp/sonar-scanner/bin/sonar-scanner \
    -Dsonar.projectKey=NodeGoat \
    -Dsonar.sources=. \
    -Dsonar.dependencyCheck.jsonReportPath=dependency-check-report.json \
    -DSonar.dependencyCheck.htmlReportPath=dependency-check-report.html \
    -Dsonar.host.url=http://localhost:9001 \
    -Dsonar.login=<login_key>
```
<p align="center">
  <a href="https://www.jenkins.io">
    <img src="https://img.shields.io/badge/Jenkins-49728B?style=for-the-badge&logo=jenkins&logoColor=white"/>
  </a>
  <a href="https://www.sonarsource.com/products/sonarqube/">
    <img src="https://img.shields.io/badge/Sonarqube-5190cf?style=for-the-badge&logo=sonarqube&logoColor=white"/>
  </a>
</p>
