# Für PVS-Hersteller

Dieser Bereich richtet sich an Hersteller von Praxisverwaltungssystemen (PVS)
und bündelt die Informationen, die für die Anbindung und Umsetzung von
TI-Anwendungen für **Privatversicherte** relevant sind.

## Inhaltsverzeichnis
- [Umsetzungsthemen für PVS](#umsetzungsthemen-für-pvs)
- [Online Check-in](#online-check-in)
- [E-Rezept: Workflow 200](#e-rezept-workflow-200)
  - [Die 3 technischen Änderungen gegenüber Workflow 160](#die-3-technischen-änderungen-gegenüber-workflow-160)
- [Elektronische Patientenakte (ePA)](#elektronische-patientenakte-epa)
- [Abgrenzung: PKV-spezifische Themen außerhalb des PVS-Scopes](#abgrenzung-pkv-spezifische-themen-außerhalb-des-pvs-scopes)
- [Spezifikationen & Leitfäden](#spezifikationen--leitfäden)
- [Kontakt](#kontakt)

## Umsetzungsthemen für PVS
- **Online Check-in (OCI):** PVS-Feature zur sicheren Übernahme der KVNR
  (inkl. QR-Code/VZD, KIM-Infrastruktur, SM(C)-B, Konnektor/TI-Anbindung).
  Siehe [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)
- **E-Rezept ausstellen (WF200):** Verordnung im PVS erstellen und
  elektronisch signieren – Prozess analog zur GKV, inkl. Komfortsignatur.
  Siehe [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- **ePA-Zugriff über Freigabe per ePA-App:** Dokumente abrufen und über das
  PVS in die ePA einstellen.
  Siehe [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)

## Online Check-in
Der Online Check-in ist das PKV-Pendant zur elektronischen
Ersatzbescheinigung (eEB) der GKV und dient der einmaligen, digitalen
Übermittlung der Versichertenstammdaten – insbesondere der KVNR – an die
Praxis, da PKV-Versicherte keine eGK mit aktualisierten Stammdaten vorlegen.
Für PVS-Hersteller besteht die Implementierung im Kern aus zwei Bausteinen:
KIM-Empfang plus automatischer FHIR-Datenübernahme.

## E-Rezept: Workflow 200
Workflow **200** ist **kein neuer Prozess**: Er nutzt dasselbe Datenmodell,
Statusmodell und dieselben Schnittstellen wie Workflow **160**. Der einzige
fachliche Unterschied: **160 = GKV**, **200 = PKV** (Direktzuweisung: **209**).

### Die 3 technischen Änderungen gegenüber Workflow 160
1. **FlowType setzen** – bei `POST /Task/$create` den Parameter
   `flowType = "200"` übergeben (Direktzuweisung: `"209"`).
2. **Versicherungstyp setzen** – im Verordnungsdatensatz
   `Coverage.type.coding.code = "PKV"`. Der Fachdienst prüft dies bei
   `$activate` und weist die Operation sonst ab.
3. **KVNR als Identifier** – Versicherten über die PKV-KVNR referenzieren
   (Datenmodell sonst identisch zum GKV-Datensatz).

## Elektronische Patientenakte (ePA)
Das PVS ruft Dokumente aus der ePA ab und stellt strukturierte Daten ein,
sofern der Versicherte die Praxis per ePA-App berechtigt hat.

## Abgrenzung: PKV-spezifische Themen außerhalb des PVS-Scopes
Einige PKV-Besonderheiten betreffen primär den Fachdienst, das
Versicherten-Frontend (FdV) und das Apothekenverwaltungssystem, nicht das PVS:
- **Einwilligung zur Abrechnungsinformation:** Für FlowTypes 200/209 wird der
  abgebenden Apotheke im Task übermittelt, ob der Versicherte eine
  Einwilligung zum Speichern von Abrechnungsinformationen erteilt hat – diese
  Einwilligung erteilt der Versicherte im FdV.
- **ChargeItem / PKV-Abgabedatensatz:** Die Verwaltung der
  Abrechnungsinformationen (ChargeItem mit AccessCode, 2D-Code-Token) liegt
  bei FdV und Apotheke.

## Spezifikationen & Leitfäden
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Implementierungsleitfaden Primärsysteme OCI (gematik)](https://github.com/gematik/spec-VSDM-Ersatzbescheinigung/blob/master/guides/eEB-OCI/Einfuehrung/Index.page.md)
- [FHIR-Profile VSDM-Ersatzbescheinigung (Simplifier)](https://simplifier.net/VSDM-Ersatzbescheinigung/~introduction)

## Kontakt
Bei Rückfragen zur PVS-Anbindung: ehealth-ti@pkv.de
