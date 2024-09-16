## Cheatsheet Inspection Continue de Code

### Tests automatisés

- **Tests unitaires** :
  - Frameworks : JUnit (Java), pytest (Python), Jest (JavaScript), NUnit (.NET)
  - Commandes :
    - Java/Gradle : `./gradlew test`
    - JavaScript : `npm test`
    - Python : `pytest`
    - .NET : `dotnet test`

- **Tests d'intégration** :
  - Outils : Selenium, Cypress (web), Postman (API), RestAssured (Java)
  - Commandes :
    - Java/Gradle : `./gradlew integrationTest`
    - Cypress : `npx cypress run`

- **Tests de performance** :
  - Outils : JMeter, Gatling, k6
  - Commandes :
    - JMeter : `jmeter -n -t test_plan.jmx -l results.jtl`
    - k6 : `k6 run script.js`

### Couverture de code

- **Outils** : JaCoCo (Java), coverage.py (Python), Istanbul (JavaScript), Coverlet (.NET)

- **Génération de rapport** :
  - Java : `./gradlew jacocoTestReport`
  - Python : `coverage run -m pytest && coverage report`
  - JavaScript : `npm run coverage`
  - .NET : `dotnet test /p:CollectCoverage=true`

- **Seuils de couverture** :
  - Exemple de configuration dans `.gitlab-ci.yml` :
    ```yaml
    coverage:
      script:
        - ./gradlew jacocoTestReport
      coverage: '/Total.*?([0-9]{1,3})%/'
    ```

### Analyse statique de code

- **SonarQube** :
  - Analyse locale : `sonar-scanner -Dsonar.projectKey=my-project`
  - Intégration CI/CD :
    - Jenkins : Utiliser le plugin SonarQube Scanner
    - GitLab CI :
      ```yaml
      sonarqube:
        image: 
          name: sonarsource/sonar-scanner-cli:latest
        script:
          - sonar-scanner
      ```

- **Autres outils** :
  - ESLint (JavaScript) : `eslint .`
  - Pylint (Python) : `pylint **/*.py`
  - Checkstyle (Java) : `./gradlew checkstyleMain`

### Métriques clés

- Bugs et vulnérabilités
- Code smells et dette technique
- Duplication de code
- Complexité cyclomatique
- Couverture de code

### Quality Gates

- Configurer dans SonarQube ou directement dans le pipeline CI
- Exemple de configuration SonarQube :
  ```json
  {
    "Bugs": {"op": "GT", "error": 0},
    "Vulnerabilities": {"op": "GT", "error": 0},
    "Code Smells": {"op": "GT", "warning": 50},
    "Coverage": {"op": "LT", "error": 80}
  }
  ```

### Bonnes pratiques

- Exécuter les tests et l'analyse à chaque commit
- Configurer des webhooks pour notifier l'équipe (Slack, MS Teams)
- Intégrer les résultats dans les pull requests/merge requests
- Réviser régulièrement les règles et seuils
- Implémenter des revues de code automatisées

### Commandes et scripts utiles

- Lancer une analyse SonarQube complète :
  ```bash
  mvn clean verify sonar:sonar \
    -Dsonar.projectKey=my:project \
    -Dsonar.host.url=http://localhost:9000 \
    -Dsonar.login=myAuthToken
  ```

- Script pour vérifier la qualité avant de merger :
  ```bash
  #!/bin/bash
  ./gradlew test
  ./gradlew sonarqube
  quality_gate_status=$(curl -s "http://localhost:9000/api/qualitygates/project_status?projectKey=my:project" | jq -r '.projectStatus.status')
  if [ "$quality_gate_status" != "OK" ]; then
    echo "Quality Gate failed!"
    exit 1
  fi
  ```

- Générer un rapport de couverture et l'envoyer à SonarQube :
  ```bash
  ./gradlew jacocoTestReport
  ./gradlew sonarqube \
    -Dsonar.coverage.jacoco.xmlReportPaths=build/reports/jacoco/test/jacocoTestReport.xml
  ```