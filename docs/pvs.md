# Für PVS-Hersteller

Dieser Bereich richtet sich an Hersteller von Praxisverwaltungssystemen
(PVS, inkl. ZPVS, PsyPVS) und bündelt die Informationen, die für die
Anbindung und Umsetzung von TI-Anwendungen für **Privatversicherte**
relevant sind.

## PKV-Besonderheiten auf einen Blick
- Privatversicherte haben **keine elektronische Gesundheitskarte (eGK)**.
- Für E-Rezept und ePA-Zugriff wird die **Krankenversichertennummer (KVNR)**
  benötigt; sie wird per **Online Check-in (OCI)** ins PVS übermittelt.
- Der **OCI** überträgt nur die KVNR – die **ePA-Berechtigung** erteilen
  Versicherte zusätzlich aktiv per ePA-App.
- Für Privatversicherte ist das E-Rezept **freiwillig**; das klassische
  Privatrezept bleibt jederzeit möglich.

## Umsetzungsthemen für PVS
- **Online Check-in (OCI):** PVS-Feature zur sicheren Übernahme der KVNR
  (inkl. QR-Code/VZD, KIM-Infrastruktur, SM(C)-B, Konnektor/TI-Anbindung).
- **E-Rezept ausstellen:** Verordnung im PVS erstellen und elektronisch
  signieren – Prozess analog zur GKV, inkl. Komfortsignatur.
- **ePA-Anbindung:** Sofern das PVS grundsätzlich ePA-fähig ist, muss
  zusätzlich der Online Check-in für Privatversicherte unterstützt werden.
- **Dokumente in der ePA:** Befunde, Diagnosen, Berichte und strukturierte
  Daten (z. B. Medikationsplan) systemgestützt einstellen.
- **FHIR-Profile:** Verordnungsdatensatz nach den KBV-FHIR-Profilen abbilden
  (u. a. Versicherungsverhältnis „PKV").

## E-Rezept: Workflow 160 vs. Workflow 200
Workflow **200** ist **kein neuer Prozess**: Er nutzt dasselbe Datenmodell,
Statusmodell und dieselben Schnittstellen wie Workflow **160**. Der einzige
fachliche Unterschied: **160 = GKV**, **200 = PKV**.

### Die 3 technischen Änderungen gegenüber Workflow 160
1. **FlowType setzen** – bei `POST /Task/$create` den Parameter
   `flowType = "200"` übergeben (Direktzuweisung: `"209"`).
2. **Versicherungstyp setzen** – im Verordnungsdatensatz
   `Coverage.type.coding.code = "PKV"`. Der Fachdienst prüft dies bei
   `$activate` und weist die Operation sonst ab.
3. **KVNR als Identifier** – Versicherten über die PKV-KVNR referenzieren
   (Datenmodell sonst identisch zum GKV-Datensatz).

### Voraussetzung
- **Online Check-in** muss implementiert sein, um KVNR und
  Versichertenstammdaten bereitzustellen (Bezug zu VSDM 2.0).

## Spezifikationen & Leitfäden
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Anforderungskatalog Verordnungssoftware (BMV-Ä Anlage 23, KBV)](https://www.kbv.de/html/bundesmantelvertrag.php)
- [Technische Anlage E-Rezept inkl. Anlagen und Beispiele (KBV)](https://update.kbv.de/ita-update/DigitaleMuster/ERP/)
- [Fachliches Datenmodell Verordnungsdatensatz / FHIR-Profile (KBV)](https://simplifier.net/erezept)
- [TI-Score zum Umsetzungsstand der Primärsysteme](https://www.ti-score.de/)

## Kontakt
Bei Rückfragen zur PVS-Anbindung: ehealth-ti@pkv.de
