## Reflexion CI/CD Pipeline

***
### Jobs:

#### Lint-Job:
Linting als erster Schritt ist sinnvoll, da so bereits frühzeitig Fehler im Code-Stil oder potenzielle Probleme erkannt werden. Damit werden spätere Fehler im Test vermieden.

#### Test-Job:
Durch die Abhängigkeit (needs: lint) wird garantiert, dass nur bereits sauber geprüfter Code getestet wird. 

#### Deploy-Job:
Der Deploy-Schritt wird nur bei einem Push auf den master-Branch ausgelöst. Somit werden bei PR's zukünftig keine unnötigen Deployprozesse ausgelöst.

### Überlegungen zum Grundaufbau

- Trennung von Jobs: Jeder Job hat eine Klar zugeteilte Aufgabe. So ist es leichter verständlich und übersichtlicher.
- Caching: Durch das Node.js-Caching wird Zeit gespart, was besonders bei häufigen Runs gut ist.
- Einsatz von npm ci

### Kritik und Verbesserungen

- Das Deployment ist aktuell nur eine Simulation. In Zukunft könnte hier ein echter Deployment-Prozess eingebunden werden ( z.B. AWS oder Docker Registry)
- Je nachdem könnte man einen zusätzlichen Build-Job erstellen
- Man könnte eine Analyse und Check von Code Coverage reports einbauen.
- Security checks mit z.B. GHAS
- Man könnte zudem auch die Branch strategie erweitern (andere Prozesse für z.B. Feature branch, etc.)