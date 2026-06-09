# Für PVS-Hersteller

Dieser Bereich richtet sich an Hersteller von Praxisverwaltungssystemen und bündelt die Informationen, die für die Anbindung und Umsetzung von TI-Anwendungen für **Privatversicherte** relevant sind.

## Umsetzungsthemen für PVS
- **Online Check-in (OCI):** PVS-Feature zur sicheren Übernahme der KVNR (inkl. QR-Code/VZD, KIM-Infrastruktur, SM(C)-B, Konnektor/TI-Anbindung).
- **E-Rezept ausstellen (WF200):** Verordnung im PVS erstellen und elektronisch   signieren – Prozess analog zur GKV, inkl. Komfortsignatur.
- **ePA Zugriff über Freigabe ePA-App:** Dokumente abrufen und in die ePA einstellen über das PVS. 

# Online Check-in
Der Online Check-in ist das PKV-Pendant zur elektronischen Ersatzbescheinigung (eEB) der GKV und dient der einmaligen, digitalen Übermittlung der Versichertenstammdaten – insbesondere der KVNR – an die Praxis, da PKV-Versicherte keine eGK mit aktualisierten Stammdaten vorlegen . Für PVS-Hersteller besteht die Implementierung im Kern aus zwei Bausteinen: KIM-Empfang plus automatischer FHIR-Datenübernahme.

# E-Rezept: Workflow 160 vs. Workflow 200
Workflow **200** ist **kein neuer Prozess**: Er nutzt dasselbe Datenmodell, Statusmodell und dieselben Schnittstellen wie Workflow **160**. Der einzige fachliche Unterschied: **160 = GKV**, **200 = PKV**.

### Die 3 technischen Änderungen bei der Implementierung gegenüber Workflow 160
1. **FlowType setzen** – bei `POST /Task/$create` den Parameter    `flowType = "200"` übergeben (Direktzuweisung: `"209"`).
2. **Versicherungstyp setzen** – im Verordnungsdatensatz `Coverage.type.coding.code = "PKV"`. Der Fachdienst prüft dies bei
   `$activate` und weist die Operation sonst ab.
3. **KVNR als Identifier** – Versicherten über die PKV-KVNR referenzieren    (Datenmodell sonst identisch zum GKV-Datensatz).



# Elektronische Patientenakte 

## Abgrenzung: PKV-spezifische Themen außerhalb des PVS-Scopes
Einige PKV-Besonderheiten betreffen primär den Fachdienst, das Versicherten-Frontend (FdV) und das Apothekenverwaltungssystem, nicht das PVS:
- Einwilligung zur Abrechnungsinformation: Für FlowTypes 200/209 wird der abgebenden Apotheke im Task die Info übermittelt, ob der     Versicherte eine Einwilligung zum Speichern von Abrechnungsinformationen erteilt hat – diese Einwilligung erteilt der Versicherte im FdV .
- ChargeItem / PKV-Abgabedatensatz: Die Verwaltung der Abrechnungsinformationen (ChargeItem mit AccessCode, 2D-Code-Token) liegt bei FdV und Apotheke .


## Spezifikationen & Leitfäden
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Anforderungskatalog Verordnungssoftware (BMV-Ä Anlage 23, KBV)](https://www.kbv.de/html/bundesmantelvertrag.php)
- [Technische Anlage E-Rezept inkl. Anlagen und Beispiele (KBV)](https://update.kbv.de/ita-update/DigitaleMuster/ERP/)
- [Fachliches Datenmodell Verordnungsdatensatz / FHIR-Profile (KBV)](https://simplifier.net/erezept)
- [TI-Score zum Umsetzungsstand der Primärsysteme](https://www.ti-score.de/)

## Kontakt
Bei Rückfragen zur PVS-Anbindung: ehealth-ti@pkv.de
