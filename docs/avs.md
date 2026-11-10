# Für AVS-Hersteller

Dieser Bereich richtet sich an Hersteller von Apothekenverwaltungssystemen (AVS). Er bündelt die Informationen, die für die PKV-Anwendungen der Telematikinfrastruktur (TI) in der Apotheke relevant sind.

> Stand: 10.11.2026 · Die Inhalte dienen der technischen Information. Verbindlich sind die jeweils gültigen Spezifikationen und Vereinbarungen.

## Inhaltsverzeichnis
- [PKV-Besonderheiten auf einen Blick](#pkv-besonderheiten-auf-einen-blick)
- [Umsetzungsthemen für AVS](#umsetzungsthemen-für-avs)
- [Spezifikationen & Dokumente](#spezifikationen--dokumente)
- [Weiterführende Informationen](#weiterführende-informationen)
- [Kontakt](#kontakt)

## PKV-Besonderheiten auf einen Blick
- Privatversicherte haben **keine elektronische Gesundheitskarte (eGK)**. 
- Für das Ausstellen eines E-Rezepts sowie für den ePA-Zugriff wird die **Krankenversichertennummer (KVNR)**  benötigt; sie wird per **Online Check-in (OCI)** via KIM ins AIS übermittelt.
- Der **OCI** überträgt die KVNR und weitere Stammdaten– die **ePA-Berechtigung** erteilen Versicherte zusätzlich aktiv per ePA-App.
- Nach der Bezahlung erhalten Privatversicherte von der Apotheke eine digitale Apothekenrechnung (=Kostenbeleg) , Beispiel: https://github.com/DAV-ABDA/eRezept-Beispiele/blob/main/PKV/PZN_Mehrfachverordnung/PZN_MV_1/PZN_MV1_Kostenbeleg.pdf, sofern sie diesem in der E-Rezept-App zugestimmt haben.

## Umsetzungsthemen für AVS-Hersteller
- [**Online Check-In 2.0** (PoPP)](#online-check-in-20): Herstellung eines Behandlungskontextes und damit Zugriff auf E-Rezepte und die ePA inkl. Medikationsliste
- [**Annahme PKV-E-Rezept (WF200)**](#e-rezept-wf200) Umsetzung gemäß Implementierungsleitfaden Primärsysteme.
- [**Digitale Apothekenrechnung** (ehemals Kostenbeleg)](#digitale-apothekenrechnung): Abrechnung Privatversicherter   gemäß TA DAV PKV. https://www.abda.de/themen/e-health/datenaustausch-pkv/

### Online-Check-In 2.0 
Der Online-Check-in 2.0 stellt über PoPP einen Behandlungskontext her. Damit erhält die Apotheke Zugriff auf E-Rezepte und die ePA inklusive Medikationsliste.

- Ablauf und Anforderungen: Implementierungsleitfäden
- 
### E-Rezept (WF 200)
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)


### Digitale Apothekenrechnung
- [Technische Anlage PKV-Abgabedaten Apothekenrechnung (TA DAV PKV)](https://www.abda.de/fileadmin/user_upload/assets/ehealth/PKV_Datenauschtausch/TA_DAV_PKV_005_20250603.pdf)](https://www.abda.de/themen/e-health/datenaustausch-pkv/)
- - [FHIR-Profile zum E-Abgabedatensatz](https://simplifier.net/erezeptabgabedaten)
- [FHIR-Profile zum PKV Abgabe-und Abrechnungsinformationen](https://simplifier.net/erezept-patientenrechnung/)

## Weitere Spezifikationen & Dokumente
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)


### Weiterführende Informationen
- [Linksammlung](https://github.com/NicoleEberhart/pkv-hersteller-portal/blob/main/docs/links.md) 


## Kontakt
Bei Rückfragen wenden Sie sich an: ehealth-ti@pkv.de
