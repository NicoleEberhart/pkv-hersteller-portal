# Für AIS-Hersteller

Dieser Bereich richtet sich an Hersteller von Arztinformationssystemen (AIS) 
und bündelt die Informationen, die für die Anbindung und Umsetzung von
TI-Anwendungen für **Privatversicherte** relevant sind.

## Inhaltsverzeichnis
- [Umsetzungsthemen für AIS](#umsetzungsthemen-für-ais)
- [Online Check-in](#online-check-in)
  - [Sonderfall: Kein Online Check-in vorhanden](#sonderfall-kein-online-check-in-vorhanden)
  - [Testen](#testen)
- [E-Rezept: Workflow 200](#e-rezept-workflow-200)
- [Elektronische Patientenakte](#elektronische-patientenakte)
  - [ePA in der PKV](#epa-in-der-pkv)
  - [Bezug zur „ePA für alle"](#bezug-zur-epa-für-alle)
- [Abgrenzung: PKV-spezifische Themen außerhalb des AIS-Scopes](#abgrenzung-pkv-spezifische-themen-außerhalb-des-ais-scopes)
- [Spezifikationen & Leitfäden](#spezifikationen--leitfäden)
- [Weiterführende Informationen](#weiterführende-informationen)
- [Kontakt](#kontakt)

## Umsetzungsthemen für AIS
- **Online Check-in (OCI):** Anwendung zur sicheren Übernahme der KVNR
  Siehe [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)
- **E-Rezept ausstellen (WF200):** Verordnung im AIS erstellen und
  elektronisch signieren – Prozess analog zur GKV, inkl. Komfortsignatur.
  Siehe [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- **ePA-Zugriff bei Privatversicherten:** Dokumente abrufen und über das
  AIS in die ePA einstellen.
  Siehe [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)

## Online Check-in
Der Online Check-in ist das PKV-Pendant zur elektronischen
Ersatzbescheinigung (eEB) der GKV und dient der einmaligen, digitalen
Übermittlung der Versichertenstammdaten – insbesondere der KVNR – an die
Praxis, da PKV-Versicherte keine eGK vorlegen.
Für AIS-Hersteller besteht die Implementierung im Kern aus zwei Bausteinen:
KIM-Empfang plus automatischer FHIR-Datenübernahme.
Siehe [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)

### Sonderfall: Kein Online Check-in vorhanden
Liegt keine OCI-Nachricht vor (z. B. Patient nutzt die App nicht), muss die
KVNR auf anderem Weg erfasst werden. Der E-Rezept-Prozess (WF200) bleibt
ansonsten unverändert.

### Testen
- [Beispiel-Testdatensätze](https://github.com/pkvjulian/oci_pkv_testdaten)
- Um einen Testdatensatz zu erhalten, senden Sie eine Mail an ehealth-ti@pkv.de

## E-Rezept: Workflow 200
Gegenwärtig bieten bereits mehr als 17 private Krankenversicherer ihren Versicherten die Nutzung des E-Rezepts an. 
Workflow **200** ist **kein neuer Prozess**: Der Prozess funktioniert analog zur GKV und hat lediglich eine andere Workflow-Nummer. Der einzige fachliche Unterschied: **160 = GKV**, **200 = PKV** (Direktzuweisung: **209**).
[Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)

## Elektronische Patientenakte
### ePA in der PKV
Gegenwärtig bieten bereits mehr als 10 private Krankenversicherer ihren Versicherten die Nutzung der ePA an. Weitere Anbieter sind gerade in der Umsetzung.
Technisch wird dieselbe ePA wie in der GKV genutzt und die Prozesse sind weitgehend identisch. Der relevanteste Unterschied liegt darin, wie Zugriffsberechtigungen auf die ePA für Leistungserbringereinrichtungen zustande kommen. Dazu gibt es allgemein zwei Wege:

  1. Initiierung eines Behandlungskontexts über Auslesen der eGK: Dieser Prozess (bisher mit VSDM++. zukünftig mit PoPP) wird bei gesetzlich Versicherten standardmäßig genutzt. Bei Privatversicherten ist er aufgrund fehlender eGK nicht möglich.
  2. Einstellung einer Berechtigung über die ePA-App: Dieser Prozess kann von allen Versicherten genutzt werden. In der GKV dient er vor allem der Anpassung der Berechtigungsdauer. Bei Privatversicherten ist dieses der Standardweg, um eine Berechtigung zu erteilen.
     
Von Seiten des AIS ist entsprechend sicherzustellen, dass Nutzer auf ePAs Privatversicherter zugreifen können, sofern die Versicherten bereits eine Zugriffsberechtigung für die Einrichtung erteilt haben. Zudem muss das System analog zu den Prozessen für gesetzlich Versicherte Feedback geben, wenn die Berechtigung nicht (mehr) besteht.
Die Umsetzung des Online Check-ins ist ebenfalls relevant, damit Versicherte die ebenfalls für den Zugriff notwendige KVNR sicher an das AIS übermitteln können.

### Bezug zur „ePA für alle"
Die Umsetzung erfolgt im Rahmen der „ePA für alle". Maßgeblich ist die jeweils gültige **Spezifikationsversion**; Versionsstände und Fristen daher vor der Implementierung prüfen. Siehe [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)

## Abgrenzung: PKV-spezifische Themen außerhalb des AIS-Scopes
Einige PKV-Besonderheiten betreffen primär den Fachdienst, das Versicherten-Frontend (FdV) und das Apothekenverwaltungssystem, nicht das AIS:
•	**Einwilligung zur Abrechnungsinformation**: Für FlowTypes 200/209 wird der abgebenden Apotheke im Task übermittelt, ob der Versicherte eine Einwilligung zum Speichern von Abrechnungsinformationen erteilt hat – diese Einwilligung erteilt der Versicherte im FdV.
•	**ChargeItem / PKV-Abgabedatensatz**: Die Verwaltung der Abrechnungsinformationen (ChargeItem mit AccessCode, 2D-Code-Token) liegt bei FdV und Apotheke.

## Spezifikationen & Leitfäden
- [PKV-IK-Liste](https://github.com/pkvjulian/PKV-IK-Liste)
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)
- [FHIR-Profile VSDM-Ersatzbescheinigung (Simplifier)](https://simplifier.net/VSDM-Ersatzbescheinigung/~introduction)

## Weiterführende Informationen 
- [Linksammlung](https://github.com/NicoleEberhart/pkv-hersteller-portal/blob/main/docs/links.md) 
-	[Was Leistungsebringer zur ePA wissen müssen](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/was-leistunsgerbringer-zur-elektronischen-patientenakte-epa-wissen-muessen/)
-	[Leistungserbringer ermöglichen mit dem E-Rezept mehr Komfort für Privatversicherte](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/leistungserbringer-schaffen-mit-dem-e-rezept-mehr-komfort-fuer-privatversicherte/)
- [Online Check-in in der Praxis: Entdecken Sie den neuen Service für Ihre Privatversicherten](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/online-check-in-in-der-arztpraxis/)

## Kontakt
Bei Rückfragen zur AIS-Anbindung: ehealth-ti@pkv.de
