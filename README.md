# Klausur 2023 DHBW HDH

## Klausurbearbeitung

### Aufgabe 4:
Vor der Anwendung muss der Namespace 'philipp-erath' erstellt werden und ein Secret 'regcred'

### Aufgabe 5: 
#### Kubernetes Deployment vs. Kubernetes Pod
Kubernetes Pods entstehen durch Kubernetes Deployments, die diese sozusagen definieren. Deployments sind also eine Art Blaupause. Eine passende Analogie wäre etwa das Verhältnis zwischen Image und Container aus Docker.
Deployments lassen sich einfach skalieren und Verwalten. Durch das Konzept der Replica Sets kann auch ein einfacher RollBack stattfinden. Pods haben diese Möglichkeiten so nicht.

#### Wofür ist ein Kubernetes Service gut
Durch Services können verschiedene Netzwerkzugriffe (sowohl intern als auch extern) auf Pods geregelt und gesteuert werden. Der Service selbst ist eine Abstraktionsebene. Der Anwender muss hierzu nicht wissen, auf welchen exakten Nodes Pods laufen. Dieses Routing wird über Servives geregelt. Sie dienen darüber hinaus als ein Level 4 (TCP) Load Balancer. Dadurch dass sich Pods in Kubernetes dynamisch ändern können, ist ein Service ein wichtiger Mechanismus für die Skalierbarkeit von Clustern.

#### Möglichkeiten, ein Cluster von außen zu erreichen
Im Seminar haben wir anfangs die Möglichkeit von einem einfachen Port-Forwarding kennengelernt. Dies wird allerdings nur für Entwicklungszwecke verwendet.

Nodeport Service: Über einen Nodeport-Service kann über den definierten Nodeport einer jeden Node auf den Service zugegriffen werden, der dann an die passenden Nodes und somit dem korrekten Pod weiterleitet.

Ingress Controller: Über ein Ingress Controller kann über eine einzige IP-Adresse von außen auf das Cluster zugegriffen werden.

(Cloud) Load Balancer: Cloud-Anbieter haben die Möglichkeit über einen Service vom Typ Load Balancer einen Load Balancer zur Verfügung zu stellen, über den dann auch die Kommunikation mit extern geregelt werden kann.

### Zusatzaufgabe:
#### Was ist ein Kubernetes Job?
Ein Job erstellt einen oder mehrere Pods und wiederholt die Ausführung der Pods, bis eine bestimmte Anzahl von ihnen erfolgreich beendet wurde. Während die Pods erfolgreich abgeschlossen werden, verfolgt der Job die erfolgreichen Abschlüsse. Wenn eine bestimmte Anzahl von erfolgreichen Abschlüssen erreicht ist, ist die Aufgabe (d. h. der Job) abgeschlossen. Das Löschen eines Jobs bereinigt die von ihm erstellten Pods. Das Anhalten eines Jobs löscht seine aktiven Pods, bis der Job wieder fortgesetzt wird.

#### 

## Setup

### Klone dieses Repository

1. Klone das Repository
    ```bash
    git clone <TODO repo url>
    cd klausur
    git remote remove origin
    ```
2. Erstelle in der GitHub Organisation ein Repository mit dem Namen **\<vorname>.\<nachname>**
3. Lade den Stand in das Repository hoch
   ```bash
   git remote add origin <url deines Repositories>
   git push -u origin master
   ```
4. Erstelle einen Branch für die Bearbeitung
   > Vergesse am Ende nicht deine Bearbeitung hochzuladen

### Sicherstellen, dass alles geht

Führe folgende Befehle in deinem Repository aus, um sicherzustellen, dass alles geht:

```bash
npm install

npm run dev
```

## Aufgaben (20 Punkte)

1. Installiere: **(3 Punkte)**
   * ESLint
   * Jest
   * Prettier
   > Die Config Dateien brauchen nicht angepasst werden
   
   > Denke auch an die nötigen Typescript dependencies
2. Schreibe ein `Dockerfile`, dass dazu benutzt werden kann, die Seite zur Verfügung zu stellen **(2 Punkte)**
3. Schreibe GitHub Actions für: **(3 Punkte)**
   * Continuous Integration
   * Continuous Delivery (GitHub Packages)
   * Continuous Deployment (GitHub Pages)
4. Definiere alle nötigen Manifeste um das erstellte Image auf einem Kubernetes Cluster zu deployen **(5 Punkte)**
5. Erkläre in eigenen Worten:
   * Welche Vorteile ein Kubernetes Deployment gegenüber einem Kubernetes Pod hat **(2 Punkte)**
   * Wofür ein Kubernetes Service gut ist **(2 Punkte)**
   * Mehrere Wege wie man eine Kubernetes Anwendung von außen erreichen kann **(3 Punkte)**

## Zusatzaufgabe:

Definiere einen Kubernetes Job **(2 Punkte)**