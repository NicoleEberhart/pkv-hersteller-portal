# Für AVS-Hersteller

## Inhaltsverzeichnis
- [PKV-Besonderheiten auf einen Blick](#pkv-besonderheiten-auf-einen-blick)
- [Umsetzungsthemen für AVS](#umsetzungsthemen-für-avs)
- [Spezifikationen & Dokumente](#spezifikationen--dokumente)
- [Weiterführende Informationen](#weiterführende-informationen)
- [Kontakt](#kontakt)

Dieser Bereich richtet sich an Hersteller von Apothekenverwaltungssystemen (AVS) und bündelt die Informationen, die für die PKV-TI-Anwendungen relevant sind.

## PKV-Besonderheiten auf einen Blick
- Online Check In 2.0 identisch zu GKV
- Nach der Bezahlung erhalten Privatversicherte von der Apotheke eine digitale Apothekenrechnung (=Kostenbeleg) , Beispiel: https://github.com/DAV-ABDA/eRezept-Beispiele/blob/main/PKV/PZN_Mehrfachverordnung/PZN_MV_1/PZN_MV1_Kostenbeleg.pdf, sofern sie diesem in der E-Rezept-App zugestimmt haben.

## Umsetzungsthemen für AVS-Hersteller
- [**Online Check-In 2.0** (PoPP)](#online-check-in-2.0): Herstellung eines Behandlungskontextes und damit Zugriff auf E-Rezepte und die ePA inkl. Medikationsliste
- [**Annahme PKV-E-Rezept (WF200)](e-rezept) Umsetzung gemäß Implementierungsleitfaden Primärsysteme.
- [**Digitale Apothekenrechnung (ehemals Kostenbeleg)](digitale-apothekenrechnung): Abrechnung Privatversicherter   gemäß TA DAV PKV. https://www.abda.de/themen/e-health/datenaustausch-pkv/

# Online-Check-In 2.0 
# E-Rezept 
# Digitale Apothekenrechnung

## Spezifikationen & Dokumente
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Technische Anlage PKV-Abgabedaten Apothekenrechnung (TA DAV PKV)](https://www.abda.de/fileadmin/user_upload/assets/ehealth/PKV_Datenauschtausch/TA_DAV_PKV_005_20250603.pdf)](https://www.abda.de/themen/e-health/datenaustausch-pkv/)
- [FHIR-Profile zum E-Abgabedatensatz](https://simplifier.net/erezeptabgabedaten)
- [FHIR-Profile zum PKV Abgabe-und Abrechnungsinformationen](https://simplifier.net/erezept-patientenrechnung/)

### Weiterführende Informationen
- [Linksammlung](https://github.com/NicoleEberhart/pkv-hersteller-portal/blob/main/docs/links.md) 
-	[Was Leistungsebringer zur ePA wissen müssen](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/was-leistunsgerbringer-zur-elektronischen-patientenakte-epa-wissen-muessen/)
-	[Leistungserbringer ermöglichen mit dem E-Rezept mehr Komfort für Privatversicherte](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/leistungserbringer-schaffen-mit-dem-e-rezept-mehr-komfort-fuer-privatversicherte/)
- [Online Check-in in der Praxis: Entdecken Sie den neuen Service für Ihre Privatversicherten](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/online-check-in-in-der-arztpraxis/)

## Kontakt
Bei Rückfragen wenden Sie sich an: ehealth-ti@pkv.de
