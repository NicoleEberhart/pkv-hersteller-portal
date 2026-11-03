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
- **Digitale Patientenrechnung (DiPag):** Rechnungen im PVS erstellen und über den DiPag Fachdienst an Versicherte digital übermitteln. 

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
Die meisten Privatversicherten können die ePA bereits nutzen.
Technisch wird dieselbe ePA wie in der GKV genutzt und die Prozesse sind weitgehend identisch. Der relevanteste Unterschied liegt darin, wie Zugriffsberechtigungen auf die ePA für Leistungserbringereinrichtungen zustande kommen. Dazu gibt es allgemein zwei Wege:

  1. **Initiierung eines Behandlungskontexts über Auslesen der eGK:** Dieser Prozess (bisher mit VSDM++. zukünftig mit PoPP) wird bei gesetzlich Versicherten standardmäßig genutzt. Bei Privatversicherten ist er aufgrund fehlender eGK nicht möglich.
  2. **Einstellung einer Berechtigung über die ePA-App:** Dieser Prozess kann von allen Versicherten genutzt werden. In der GKV dient er vor allem der Anpassung der Berechtigungsdauer. Bei Privatversicherten ist dieses der Standardweg, um eine Berechtigung zu erteilen.
     
Von Seiten des AIS ist entsprechend sicherzustellen, dass Nutzer auf ePAs Privatversicherter zugreifen können, sofern die Versicherten bereits eine Zugriffsberechtigung für die Einrichtung erteilt haben. Zudem muss das System analog zu den Prozessen für gesetzlich Versicherte Feedback geben, wenn die Berechtigung nicht (mehr) besteht.
Die Umsetzung des Online Check-ins ist ebenfalls relevant, damit Versicherte die ebenfalls für den Zugriff notwendige KVNR sicher an das AIS übermitteln können.

### Bezug zur „ePA für alle"
Die Umsetzung erfolgt im Rahmen der „ePA für alle". Maßgeblich ist die jeweils gültige **Spezifikationsversion**; Versionsstände und Fristen daher vor der Implementierung prüfen. Siehe [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)

## Digitale Patientenrechnung (DiPag)

Die DiPag ist die erste Anwendung der TI 2.0 und zielt darauf ab, den gesamten Abrechnungsprozess zwischen Rechnungsersteller, Versicherten und Privater Krankenversicherung medienbruchfrei zu digitalisieren. 

Der DiPag-Fachdienst ist direkt über das Internet erreichbar und nach dem Zero-Trust-Ansatz abgesichert. Für AIS-Hersteller bedeutet das, dass neben der Anbindung an den DiPag-Fachdienst zusätzlich ein ZETA-Client integriert werden muss, siehe: [Implementierungsleitfaden für Clients der Digitalen Patientenrechnung](https://wiki.gematik.de/spaces/RUAAS/pages/800562254/Implementierungsleitfaden+f%C3%BCr+Clients+der+Digitalen+Patientenrechnung)

Auf Seiten der Versicherten ist die DiPag entweder unmittelbar in das ePA-FdV oder in die Service-App der jeweiligen Versicherung mit Einreichungsfunktion integriert. Rechnungen können nur dann an den DiPag-Fachdienst übermittelt werden, wenn der Rechnungsempfänger über ein DiPag-Nutzerkonto verfügt und eine Einwilligung zum digitalen Rechnungsversand vorliegt. Für eine Abfrage des Rechnungsempfängers und seiner Einwilligung am Fachdienst sind die KVNR und das Geburtsdatum erforderlich. 

Die Einwilligung erteilt der Rechnungsempfänger einmalig bei Einrichtung des Nutzerkontos. Eine patientenindividuelle Zustimmung müssen Rechnungsersteller daher nicht gesondert einholen.

Sobald eine Rechnung auf dem DiPag-Fachdienst für den Rechnungsempfänger bereitsteht, wird dieser per E-Mail und – sofern aktiviert – per Push-Nachricht benachrichtigt. Anschließend kann der Rechnungsempfänger die Rechnung als PDF/A-3 mit eingebetteten strukturierten Daten und/oder ein Zugriffstoken herunterladen und beim gewünschten Kostenträger zur Kostenerstattung einreichen. 

Da Leistungserbringer Privatrechnungen häufig nicht selbst stellen, sondern an externe Abrechnungsdienstleister abgeben, sollten bei der Übertragung der Patienten- und Abrechnungsdaten an den Abrechnungsdienstleister zwingend auch die KVNR und das Geburtsdatum des Rechnungsempfängers übermittelt werden. 


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
- **DiPag**
  - [DiPag-Featuredokument](https://gemspec.gematik.de/docs/gemF/gemF_DiPag/latest/)
  - [DiPag-Fachdienst-Spezifikations](https://gemspec.gematik.de/docs/gemSpec/gemSpec_DiPag_FD/latest/)
  - [Implementierungsleitfaden für Clients der Digitalen Patientenrechnung](https://wiki.gematik.de/spaces/RUAAS/pages/800562254/Implementierungsleitfaden+f%C3%BCr+Clients+der+Digitalen+Patientenrechnung)
  - [DiPag FHIR-Profile inkl. FHIR-Implementierungsleiten](https://simplifier.net/DigitalePatientenrechnung/~introduction) 
  - [ZETA Spezifikation](https://gemspec.gematik.de/docs/gemSpec/gemSpec_ZETA/latest/)
  - [ZETA Hauptrepository](https://github.com/gematik/zeta)

## Weiterführende Informationen 
- [Linksammlung](https://github.com/NicoleEberhart/pkv-hersteller-portal/blob/main/docs/links.md) 
-	[Was Leistungsebringer zur ePA wissen müssen](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/was-leistunsgerbringer-zur-elektronischen-patientenakte-epa-wissen-muessen/)
-	[Leistungserbringer ermöglichen mit dem E-Rezept mehr Komfort für Privatversicherte](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/leistungserbringer-schaffen-mit-dem-e-rezept-mehr-komfort-fuer-privatversicherte/)
- [Online Check-in in der Praxis: Entdecken Sie den neuen Service für Ihre Privatversicherten](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/online-check-in-in-der-arztpraxis/)

## Kontakt
Bei Rückfragen zur AIS-Anbindung: ehealth-ti@pkv.de
