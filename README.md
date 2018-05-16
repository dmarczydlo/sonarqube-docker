# Sonarqube

**[Sonarqube](https://www.sonarqube.org)** (formerly Sonar)is an open source platform developed by SonarSource for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells and security vulnerabilities on 20+ programming languages. SonarQube offers reports on duplicated code, coding standards, unit tests, code coverage, code complexity, comments, bugs, and security vulnerabilities.

# How to run sonar
```
docker-compose -f sonar.yml up --build
```

After that command sonar will be available on ```localhost:9000```

If not up to date run ```localhost:9000/setup```


# Sonar scanner

For scanning your project you can use another docker ```newtmitch/sonar-scanner```

## Example

```dockerfile
docker run --net dockersonarqube_sonarnet -ti -v $(pwd):/root/src --link dockersonarqube_sonarqube_1 newtmitch/sonar-scanner sonar-scanner \
  -Dsonar.host.url=http://sonarqube:9000 \
  -Dsonar.jdbc.url=jdbc:h2:tcp://sonarqube/sonar \
  -Dsonar.projectKey=MyProjectKey \
  -Dsonar.projectName="My Project Name" \
  -Dsonar.projectVersion=1 \
  -Dsonar.projectBaseDir=/root \
  -Dsonar.sources=./src
```

Scanner will be used for project: **nameProject**
