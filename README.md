## DevOps Project for Beginners

[![Image](https://github.com/yankils/Simple-DevOps-Project/blob/master/Devops_course.PNG "DevOps Project - CI/CD with Jenkins Ansible Docker Kubernetes ")](https://www.udemy.com/course/valaxy-devops/?referralCode=8147A5CF4C8C7D9E253F)

### Voraussetzungen

- **Java:** Die Beispielanwendung erfordert eine installierte Java-Laufzeitumgebung (JDK 7 oder neuer).
- **Maven:** Zum Bauen des Multi-Modul-Projekts wird Maven benötigt.

### Build

Das gesamte Projekt kann mit Maven gebaut werden:

```bash
mvn clean package
```

Dadurch entsteht unter `webapp/target` ein WAR-Archiv. Das Web-Modul lässt sich wahlweise direkt mit Jetty starten oder in einen Tomcat deployen:

```bash
# Start mit Jetty
mvn -pl webapp jetty:run

# Oder das WAR in einen vorhandenen Tomcat kopieren
cp webapp/target/webapp.war $CATALINA_BASE/webapps/
```

### Docker & Kubernetes

Die bereitgestellte `Dockerfile` erzeugt ein Tomcat-Image, in das das gebaute WAR kopiert wird. Die Dateien `regapp-deploy.yml` und `regapp-service.yml` sind Beispielmanifeste für Kubernetes und können nach dem Build mit `kubectl apply -f` ausgerollt werden.
