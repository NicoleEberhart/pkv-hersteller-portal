# Hersteller-Portal AVS & PVS
Zentrale Informations- und Dokumentationsplattform des PKV-Verbands für Hersteller im Umfeld Telematikinfrastruktur (TI). Bündelt technische Spezifikationen, Schnittstellen, Anbindungswege und Kontaktinformationen für die Umsetzung digitaler Anwendungen für Privatversicherte.

> Stand: 08.06.2026 ·  Kontakt: ehealth-ti@pkv.de

---

## Inhaltsverzeichnis
- [Über dieses Portal](#über-dieses-portal)
- [Für AVS-Hersteller](#für-avs-hersteller)
- [Für PVS-Hersteller](#für-pvs-hersteller)
- [Spezifikationen & Dokumente](#spezifikationen--dokumente)
- [Wichtige Links](#wichtige-links)
- [Kontakt & Support](#kontakt--support)
- [Änderungshistorie](#änderungshistorie)

---

## Über dieses Portal
Dieses Portal wird vom PKV-Verband bereitgestellt und richtet sich an Hersteller von Apotheken- und Praxisverwaltungssystemen. Ziel ist ein schneller, transparenter Zugang zu Spezifikationen, Schnittstellen und Ansprechpartnern.

# Für AVS-Hersteller
Dieser Bereich richtet sich an Hersteller von Apothekenverwaltungssystemen (AVS) und bündelt die Informationen, die für die Anbindung und Umsetzung von TI-Anwendungen für **Privatversicherte** relevant sind.
→ [Zum AVS-Bereich](docs/avs.md)

## PKV-Besonderheiten auf einen Blick
- Privatversicherte haben **keine elektronische Gesundheitskarte (eGK)** –  TI-Anwendungen werden über ePA- und E-Rezept-App genutzt.
- Für den ePA-Zugriff wird die **KVNR** benötigt; zusätzlich berechtigt der Versicherte die Apotheke **aktiv per ePA-App**.
- 
## Umsetzungsthemen für AVS
- **ePA-Zugriff in der Apotheke:** Zugriff über Rezeptabruf, Einlesen der  eGK oder Befugnis eines Stammkunden per ePA-App.
- **Elektronische Medikationliste:** 
- **Annahme PKV-E-Rezept (WF200):** Umsetzung gemäß Implementierungsleitfaden Primärsysteme.
- **Apothekenrechnung (ehemals Kostenbeleg):** Abrechnung Privatversicherter gemäß TA DAV PKV.


## Spezifikationen & Dokumente
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Technische Anlage Apothekenrechnung (TA DAV PKV)](https://www.abda.de/fileadmin/user_upload/assets/ehealth/PKV_Datenauschtausch/TA_DAV_PKV_005_20250603.pdf)

# Für PVS-Hersteller
Dieser Bereich richtet sich an Hersteller von Praxisverwaltungssystemen und bündelt die Informationen, die für die Anbindung und Umsetzung von TI-Anwendungen für **Privatversicherte**
relevant sind.→ [Zum PVS-Bereich](docs/pvs.md)

## PKV-Besonderheiten auf einen Blick
- Privatversicherte haben **keine elektronische Gesundheitskarte (eGK)**. 
- Für E-Rezept und ePA-Zugriff wird die **Krankenversichertennummer (KVNR)**  benötigt; sie wird per **Online Check-in (OCI)** ins PVS übermittelt.
- Der **OCI** überträgt nur die KVNR – die **ePA-Berechtigung** erteilen Versicherte zusätzlich aktiv per ePA-App.
- Für Privatversicherte ist das E-Rezept **freiwillig**; das klassische Privatrezept bleibt jederzeit möglich.

  ## Umsetzungsthemen für PVS
- **Online Check-in (OCI):** PVS-Feature zur sicheren Übernahme der KVNR
  (inkl. QR-Code/VZD, KIM-Infrastruktur, SM(C)-B, Konnektor/TI-Anbindung).
- **E-Rezept ausstellen:** Verordnung im PVS erstellen und elektronisch
  signieren – Prozess analog zur GKV, inkl. Komfortsignatur.
- **Workflow 200 (WF200):** PKV-spezifischer E-Rezept-Workflow für
  Privatversicherte – als eigenständiger Umsetzungsschwerpunkt zu beachten.
- **ePA-Anbindung:** Sofern das PVS grundsätzlich ePA-fähig ist, muss
  zusätzlich der Online Check-in für Privatversicherte unterstützt werden.
- **Dokumente in der ePA:** Befunde, Diagnosen, Berichte und strukturierte
  Daten (z. B. Medikationsplan) systemgestützt einstellen.
- **FHIR-Profile:** Verordnungsdatensatz nach den KBV-FHIR-Profilen
  abbilden (u. a. Versicherungsverhältnis „PKV").

## Spezifikationen & Leitfäden
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Anforderungskatalog Verordnungssoftware (BMV-Ä Anlage 23, KBV)](https://www.kbv.de/html/bundesmantelvertrag.php)
- [Technische Anlage E-Rezept inkl. Anlagen und Beispiele (KBV)](https://update.kbv.de/ita-update/DigitaleMuster/ERP/)
- [Fachliches Datenmodell Verordnungsdatensatz / FHIR-Profile (KBV)](https://simplifier.net/erezept)
- [TI-Score zum Umsetzungsstand der Primärsysteme](https://www.ti-score.de/)

# Wichtige Links
→ [Gesammelte Linksammlung](docs/links.md)

# Kontakt & Support
→ [Ansprechpartner](docs/kontakt.md)
