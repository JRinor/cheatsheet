## Cheatsheet Inspection Continue de Code

### Tests automatisés

- **Tests unitaires** :
  - Frameworks : JUnit (Java), pytest (Python), Jest (JavaScript)
  - Commande : `./gradlew test` (Java/Gradle), `npm test` (JavaScript)

- **Tests d'intégration** :
  - Outils : Selenium, Cypress (web), Postman (API)
  - Commande : `./gradlew integrationTest` (Java/Gradle)

- **Tests de performance** :
  - Outils : JMeter, Gatling
  - Commande : `jmeter -n -t test_plan.jmx -l results.jtl`

### Couverture de code

- **Outils** : JaCoCo (Java), coverage.py (Python), Istanbul (JavaScript)

- **Génération de rapport** :
  - Java : `./gradlew jacocoTestReport`
  - Python : `coverage run -m pytest` puis `coverage report`
  - JavaScript : `npm run coverage`

- **Seuils de couverture** :
  - Configurer dans le pipeline CI pour échouer si la couverture est inférieure à un certain pourcentage

### SonarQube

- **Analyse locale** :
  `sonar-scanner -Dsonar.projectKey=my-project`

- **Intégration CI/CD** :
  - Jenkins : Utiliser le plugin SonarQube Scanner
  - GitLab CI : Utiliser l'image `sonar-scanner-cli`

- **Métriques clés** :
  - Bugs
  - Vulnérabilités
  - Code smells
  - Duplication de code
  - Couverture de code

- **Quality Gates** :
  - Configurer dans SonarQube pour définir les critères de qualité
  - Exemple : Échouer si plus de 5 bugs critiques

### Bonnes pratiques

- Exécuter les tests et l'analyse à chaque commit
- Configurer des webhooks pour notifier l'équipe des résultats
- Intégrer les résultats dans les pull requests
- Réviser régulièrement les règles et seuils

### Commandes utiles

- Lancer une analyse SonarQube :
  `mvn sonar:sonar` (Maven)
  `./gradlew sonarqube` (Gradle)

- Vérifier la qualité du code avant de merger :
  `sonar-scanner -Dsonar.analysis.mode=preview`

- Générer un rapport de couverture et l'envoyer à SonarQube :
  `./gradlew jacocoTestReport sonarqube`
