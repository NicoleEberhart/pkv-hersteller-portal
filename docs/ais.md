# Für AIS-Hersteller

Dieser Bereich richtet sich an Hersteller von Arztinformationssystemen (AIS) und bündelt die Informationen, die für die Anbindung und Umsetzung von
TI-Anwendungen für **Privatversicherte** relevant sind.

## Inhaltsverzeichnis
- [Umsetzungsthemen für AIS](#umsetzungsthemen-für-ais)
- [Online Check-in](#online-check-in)
  - [Sonderfall: Kein Online Check-in vorhanden](#sonderfall-kein-online-check-in-vorhanden)
  - [Testen](#testen)
- [E-Rezept: Workflow 200](#e-rezept-workflow-200)
- [Elektronische Patientenakte (ePA)](#elektronische-patientenakte-epa)
  - [ePA in der PKV](#epa-in-der-pkv)
  - [Bezug zur „ePA für alle"](#bezug-zur-epa-für-alle)
- [Digitale Patientenrechnung (DiPag)](#digitale-patientenrechnung-dipag)
- [Abgrenzung: PKV-spezifische Themen außerhalb des AIS-Scopes](#abgrenzung-pkv-spezifische-themen-außerhalb-des-ais-scopes)
- [Spezifikationen & Leitfäden](#spezifikationen--leitfäden)
- [Weiterführende Informationen](#weiterführende-informationen)
- [Kontakt](#kontakt)

## Umsetzungsthemen für AIS
- **Online Check-in (OCI):** Anwendung zur sicheren Übermittlung der Krankenversichertennummer (KVNR) in das AIS, siehe [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)
- **PKV-E-Rezept ausstellen (WF200):** Verordnung im AIS erstellen und elektronisch signieren – Prozess analog zur GKV, inkl. Komfortsignatur, siehe 
  Siehe [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- **ePA-Zugriff bei Privatversicherten:** Der Versicherte erteilt eine ePA-Freigabe über die ePA-App. Der Leistungserbringer kann dann Dokumente abrufen und über das AIS in die ePA einstellen. Analog zur GKV, siehe [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- **Digitale Patientenrechnung (DiPag):** Rechnungen mit strukturierten Daten sicher an den DiPag-Fachdienst übermitteln, siehe [Implementierungsleitfaden für Clients der Digitalen Patientenrechnung](https://wiki.gematik.de/spaces/RUAAS/pages/800562254/Implementierungsleitfaden+f%C3%BCr+Clients+der+Digitalen+Patientenrechnung)
- **PADneXt-Schnittstelle:** Übertragung der KVNR an Abrechnungsdienstleister, damit auch sie die DiPag nutzen können, siehe [PADneXt für GOÄneu - Abrechner - PADline](https://padline.de/padnext-fuer-goaeneu-abrechner/)

## Online Check-in
Der Online Check-in ist das PKV-Pendant zur elektronischen Ersatzbescheinigung (eEB) der GKV und dient der **einmaligen, digitalen Übermittlung der Versichertenstammdaten** – insbesondere der KVNR. 
Für AIS-Hersteller besteht die Implementierung im Kern aus zwei Bausteinen: **KIM-Empfang plus automatische FHIR-Datenübernahme**
Siehe [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)

### Sonderfall: Kein Online Check-in vorhanden
Liegt keine OCI-Nachricht vor (z. B. Patient nutzt die App nicht), muss die KVNR auf anderem Weg erfasst werden. Der E-Rezept-Prozess (WF200) bleibt ansonsten unverändert.

### Weiterentwicklung Online Check-in 2.0 

### Testen
- [Beispiel-Testdatensätze](https://github.com/pkvjulian/oci_pkv_testdaten)
- Um einen Testdatensatz in der RU auf Ihre KIM-Adresse zu erhalten, senden Sie eine Mail an *ehealth-ti@pkv.de*

## E-Rezept: Workflow 200
Die meisten Privaten Krankenversicherungen bieten bereits das E-Rezept an. Der Workflow **200** ist **kein neuer Prozess**: Der Prozess funktioniert analog zum GKV-Prozess (WF 160).  Beide Workflows nutzen dasselbe FHIR-Datenmodell. Die wesentlichen Unterschiede liegen in den nachgelagerten PKV-spezifischen Prozessen (Abrechnungsprozess und Zustimmung zum Erhalt einer digitalen Apothekenrechnung), die lediglich die Apothekensoftware betreffen. 

- Beide Workflows nutzen dasselbe Statusmodell
- Es werden für die Verordnungsdaten die E-Rezept-Profile der KBV verwendet
- Die FHIR-Datenmodelle sind identisch
  
Mehr Infos: [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)

## Elektronische Patientenakte (ePA)
### ePA in der PKV
Die meisten Privatversicherten können die ePA bereits nutzen. Technisch wird dieselbe ePA wie in der GKV genutzt und die Prozesse sind weitgehend identisch. 
Der relevanteste Unterschied liegt darin, wie Zugriffsberechtigungen auf die ePA für Leistungserbringereinrichtungen zustande kommen. Dazu gibt es allgemein zwei Wege:

  1. **Initiierung eines Behandlungskontexts über Auslesen der eGK:** Dieser Prozess (bisher mit VSDM++. zukünftig mit PoPP) wird bei gesetzlich Versicherten standardmäßig genutzt. Bei Privatversicherten ist er aufgrund fehlender eGK nicht möglich.
  2. **Einstellung einer Berechtigung über die ePA-App:** Dieser Prozess kann von allen Versicherten genutzt werden. In der GKV dient er vor allem der Anpassung der Berechtigungsdauer. Bei Privatversicherten ist dieses der Standardweg, um eine Berechtigung zu erteilen.
     
Von Seiten des AIS ist entsprechend sicherzustellen, dass Nutzer auf ePAs Privatversicherter zugreifen können, sofern die Versicherten bereits eine Zugriffsberechtigung für die Einrichtung erteilt haben. Zudem muss das System analog zu den Prozessen für gesetzlich Versicherte Feedback geben, wenn die Berechtigung nicht (mehr) besteht.
Die Umsetzung des Online Check-ins ist ebenfalls relevant, damit Versicherte die ebenfalls für den Zugriff notwendige KVNR sicher an das AIS übermitteln können.

### Bezug zur „ePA für alle"
Die Umsetzung erfolgt im Rahmen der „ePA für alle". Maßgeblich ist die jeweils gültige **Spezifikationsversion**; Versionsstände und Fristen daher vor der Implementierung prüfen. Siehe [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)

## Digitale Patientenrechnung (DiPag)

Die DiPag ist die erste Anwendung der TI 2.0 und zielt darauf ab, den gesamten Abrechnungsprozess zwischen Rechnungsersteller, Versicherten und Privater Krankenversicherung medienbruchfrei zu digitalisieren. 

Der DiPag-Fachdienst ist direkt über das Internet erreichbar und nach dem Zero-Trust-Ansatz abgesichert. Für AIS-Hersteller bedeutet das, dass neben der Anbindung an den DiPag-Fachdienst zusätzlich ein ZETA-Client integriert werden muss, siehe [Implementierungsleitfaden für Clients der Digitalen Patientenrechnung](https://wiki.gematik.de/spaces/RUAAS/pages/800562254/Implementierungsleitfaden+f%C3%BCr+Clients+der+Digitalen+Patientenrechnung)

Auf Seiten der Versicherten ist die DiPag entweder unmittelbar in das ePA-FdV oder in die Service-App der jeweiligen Versicherung mit Einreichungsfunktion integriert. Rechnungen können nur dann an den DiPag-Fachdienst übermittelt werden, wenn der Rechnungsempfänger über ein DiPag-Nutzerkonto verfügt und eine Einwilligung zum digitalen Rechnungsversand vorliegt. Für eine Abfrage des Rechnungsempfängers und seiner Einwilligung am Fachdienst sind die KVNR und das Geburtsdatum erforderlich. 

Die Einwilligung erteilt der Rechnungsempfänger einmalig bei Einrichtung des Nutzerkontos. Eine patientenindividuelle Zustimmung müssen Rechnungsersteller daher nicht gesondert einholen.

Sobald eine Rechnung auf dem DiPag-Fachdienst für den Rechnungsempfänger bereitsteht, wird dieser per E-Mail und – sofern aktiviert – per Push-Nachricht benachrichtigt. Anschließend kann der Rechnungsempfänger die Rechnung als PDF/A-3 mit eingebetteten strukturierten Daten und/oder ein Zugriffstoken herunterladen und beim gewünschten Kostenträger zur Kostenerstattung einreichen. 

Da Leistungserbringer Privatrechnungen häufig nicht selbst stellen, sondern an externe Abrechnungsdienstleister abgeben, sollten bei der Übertragung der Patienten- und Abrechnungsdaten an den Abrechnungsdienstleister zwingend auch die KVNR und das Geburtsdatum des Rechnungsempfängers übermittelt werden. Um diese Übermittlung sicherzustellen ist für AIS-Hersteller außerdem die Umsetzung der PADneXt-Schnittstelle relevant [Schnittstellenbeschreibung PADneXt](https://padline.de/downloads/#vdds). Diese Schnittstelle bereitet sie zugleich optimal auf die bevorstehende GOÄneu-Novelle vor. 


## Abgrenzung: PKV-spezifische Themen außerhalb des AIS-Scopes
Einige PKV-Besonderheiten betreffen primär den Fachdienst, das Versicherten-Frontend (FdV) und das Apothekenverwaltungssystem, nicht das AIS:
•	**Einwilligung zur Abrechnungsinformation**: Für FlowTypes 200/209 wird der abgebenden Apotheke im Task übermittelt, ob der Versicherte eine Einwilligung zum Speichern von Abrechnungsinformationen erteilt hat – diese Einwilligung erteilt der Versicherte im FdV.
•	**ChargeItem / PKV-Abgabedatensatz**: Die Verwaltung der Abrechnungsinformationen (ChargeItem mit AccessCode, 2D-Code-Token) liegt bei FdV und der Apotheke.

## Spezifikationen & Leitfäden
- [PKV-IK-Liste](https://github.com/pkvjulian/PKV-IK-Liste)
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)
- [FHIR-Profile VSDM-Ersatzbescheinigung (Simplifier)](https://simplifier.net/VSDM-Ersatzbescheinigung/~introduction)
- **DiPag**
  - [DiPag-Featuredokument](https://gemspec.gematik.de/docs/gemF/gemF_DiPag/latest/)
  - [DiPag-Fachdienst-Spezifikation](https://gemspec.gematik.de/docs/gemSpec/gemSpec_DiPag_FD/latest/)
  - [Implementierungsleitfaden für Clients der Digitalen Patientenrechnung](https://wiki.gematik.de/spaces/RUAAS/pages/800562254/Implementierungsleitfaden+f%C3%BCr+Clients+der+Digitalen+Patientenrechnung)
  - [DiPag FHIR-Profile inkl. FHIR-Implementierungsleitfaden](https://simplifier.net/DigitalePatientenrechnung/~introduction) 
  - [ZETA Spezifikation](https://gemspec.gematik.de/docs/gemSpec/gemSpec_ZETA/latest/)
  - [ZETA Hauptrepository](https://github.com/gematik/zeta)

## Weiterführende Informationen 
- [Linksammlung](https://github.com/NicoleEberhart/pkv-hersteller-portal/blob/main/docs/links.md) 

## Kontakt
Bei Rückfragen zur AIS-Anbindung: ehealth-ti@pkv.de
